---
title: Establecer KeepAlive en false para interactuar con hosts externos en un complemento | MicrosoftDocs
description: La propiedad KeepAlive establecida en true en el encabezado de solicitud HTTP o que no se haya definido explícitamente en false puede prolongar el tiempo de ejecución de los complementos.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-keepalive-to-false-when-interacting-with-external-hosts-in-a-plug-in"></a>Establecer KeepAlive en false para interactuar con hosts externos en un complemento

**Categoría**: rendimiento

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Si un complemento hace solicitudes web externas e intenta usar `KeepAlive` en una conexión cerrada, el complemento no podrá en definitiva ejecutar la solicitud web. Sin embargo, si se registra el complemento:

- Los usuarios pueden experimentar de forma sincrónica:

    - Aplicaciones basadas en modelos que dejan de responder
    - Interacciones lentas con el cliente
    - El explorador deja de responder

- De forma asincrónica, las ejecuciones de complementos pueden prolongarse durante más tiempo antes de dar error. 

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

1. En HTTP 1.1, todas las conexiones se consideran persistentes (`KeepAlive` es true) a menos que se declaren al contrario. Debido al hecho de que los complementos se ejecutan de forma aislada, el servicio de espacio aislado traduce en ellos creando ejecuciones muy cortas que por lo general no se benefician de `KeepAlive`. Para evitar problemas al establecer la conexión con los servicios externos, se recomienda deshabilitar `KeepAlive` en los complementos. Si el servicio externo específico se beneficiaría de usar sesiones persistentes por razones de rendimiento, envíe `KeepAlive` activamente en un intervalo de la mitad de tiempo de espera inactivo (30 segundos) para evitar que se cierre la conexión.

Los ejemplos siguientes muestran cómo definir `KeepAlive` explícitamente en false según el método que use para establecer conexiones a un servicio externo:

- `HttpWebRequest` 
    ```csharp
    HttpWebRequest req = WebRequest.Create("https://www.contoso.com/api/stuff") as HttpWebRequest;
    
    if (req != null)
    {
        req.KeepAlive = false;
        HttpWebResponse response = (HttpWebResponse)req.GetResponse();
    }
    ```

-  `WebClient` 
    ```csharp
    private string RequestString(Uri location)
    {
        using (var client = new MyWebClient())
        {
            return client.DownloadString(location);
        }
    }

    internal class MyWebClient : WebClient
    {
        // Overrides the GetWebRequest method and sets keep alive to false
        protected override WebRequest GetWebRequest(Uri address)
        {
            HttpWebRequest req = (HttpWebRequest)base.GetWebRequest(address);
            req.KeepAlive = false;

            return req;
        }
    }
    ```

- Instancia de `WCF ClientBase< T >` 
    ```csharp
    OrganizationServiceClient client = null;
    
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        client = new OrganizationServiceClient(binding, address);
    
        WhoAmIResponse response = client.Execute(new WhoAmIRequest()) as WhoAmIResponse;
    }
    catch (Exception ex)
    {
        client.Abort();
    }
    finally
    {
        client.Close();
    }
    ```

- Método estático `WCF ChannelFactory< TChannel >` 
    ```csharp
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        channel = ChannelFactory<IRequestChannel>.CreateChannel(binding, address);
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
    }
    finally
    {
        channel.Close();
    }
    ```

- Instancia de `WCF ChannelFactory< TChannel >` 
    ```csharp
    ChannelFactory<IRequestChannel> factory = null;
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        factory = new ChannelFactory<IRequestChannel>(binding, address);
        channel = factory.CreateChannel();
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
        factory.Abort();
    }
    finally
    {
        channel.Close();
        factory.Close();
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

Para reemplazar el valor de `KeepAlive` predeterminado para las interacciones que no sean de WCF, el método debe centrarse en usar HttpWebRequest para realizar las interacciones con el servidor web, pero primero hay establecer la propiedad `KeepAlive` en false.

Los ejemplos siguientes muestran cómo el patrón problemático según el método que use para establecer conexiones a un servicio externo:

> [!WARNING]
> Estos patrones deben evitarse.

- `HttpWebRequest`

    ```csharp
    WebRequest request = WebRequest.Create("https://www.contoso.com/api/stuff");
    //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    HttpWebResponse response = (HttpWebResponse)request.GetResponse();
    response.Close();
    ```

- `WebClient`

    ```csharp
    using (var client = new WebClient())
    {
        string url = "https://www.contoso.com/api/stuff";
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
        string result = client.DownloadString(url);
    }
    ```

- Instancia de `WCF ClientBase< T >`

    ```csharp
    OrganizationServiceClient client = null;
    
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
        client = new OrganizationServiceClient(binding, address);
    
        WhoAmIResponse response = client.Execute(new WhoAmIRequest()) as WhoAmIResponse;
    }
    catch (Exception ex)
    {
        client.Abort();
    }
    finally
    {
        client.Close();
    }
    ```

- Método estático `WCF ChannelFactory< TChannel >`

    ```csharp
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    
        channel = ChannelFactory<IRequestChannel>.CreateChannel(binding, address);
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
    }
    finally
    {
        channel.Close();
    }
    ```

- Instancia de `WCF ChannelFactory< TChannel >`

    ```csharp
    ChannelFactory<IRequestChannel> factory = null;
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    
        factory = new ChannelFactory<IRequestChannel>(binding, address);
        channel = factory.CreateChannel();
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
        factory.Abort();
    }
    finally
    {
        channel.Close();
        factory.Close();
    }
    ```

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Los complementos que interactúan con los servicios externos pueden experimentar tiempos de ejecución anormalmente superiores. El problema se debe a la ([propiedad KeepAlive](https://msdn.microsoft.com/library/system.net.httpwebrequest.keepalive.aspx)) de las solicitudes HTTP emitidas a servidores web externos. Si la propiedad `KeepAlive` se establece en true o no se define en absoluto (el comportamiento predeterminado es true), el cliente de espacio aislado en el servidor puede continuar intentando y usando una sesión persistente aunque la sesión haya expirado debido a la configuración del dispositivo de red. La causa del tiempo de ejecución extendido se debe a la red que reintenta la solicitud hasta que la conexión se restablezca finalmente.

> [!IMPORTANT]
> Esto afecta a todo el código que inicia solicitudes HTTP para un servidor web mediante [System.Net.WebClient](https://msdn.microsoft.com/library/system.net.webclient.aspx), [System.Net.WebRequest](https://msdn.microsoft.com/library/system.net.webrequest.aspx) or [System.Net.HttpWebRequest](https://msdn.microsoft.com/library/system.net.httpwebrequest.aspx), así como comunicaciones de cliente de Windows Communications Foundation (WCF) mediante un transporte HTTP que se enlaza directa o indirectamente a través de [ChannelFactory\<TChannel>](https://docs.microsoft.com/dotnet/api/system.servicemodel.channelfactory-1) o [ClientBase\<T>](https://docs.microsoft.com/dotnet/api/system.servicemodel.clientbase-1).

Este comportamiento es transparente para los usuarios finales y el registro es tradicional ya que la ejecución se debe a retrasos de red.  Si el complemento se registró como un evento sincrónico, los usuarios podrían experimentar problemas de rendimiento intermitentes durante aquella operaciones registradas que podrían producir ausencia de respuesta de aplicaciones basadas en modelos.  Si el complemento se registra de forma asincrónica, el problema solo se observaría revisando los tiempos de ejecución del complemento y observando que la ejecución tomar más tiempo del normal o esperado.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Ejemplo: acceso web desde un complemento de espacio aislado](../../org-service/samples/web-access-plugin.md)<br />
[Equilibrio de cargas (WCF)](https://msdn.microsoft.com/library/ms730128.aspx)<br />
[Propiedad HttpTransportBindingElement.KeepAliveEnabled](https://msdn.microsoft.com/library/system.servicemodel.channels.httptransportbindingelement.keepaliveenabled.aspx)<br />
[Propiedad HttpWebRequest.KeepAlive](https://msdn.microsoft.com/library/system.net.httpwebrequest.keepalive.aspx)<br />
