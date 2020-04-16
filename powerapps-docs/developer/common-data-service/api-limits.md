---
title: Límites de la API de protección de servicios (Common Data Service) | Microsoft Docs
description: Conozca los límites de protección de servicios de las solicitudes de la API.
ms.custom: ''
ms.date: 11/23/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f46360623cd3cf530f9d6b2a0c7c1aecd3c66c0c
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156484"
---
# <a name="service-protection-api-limits"></a>Límites de la API de protección de servicio

Para garantizar una disponibilidad y un rendimiento consistentes para todos, aplicamos algunos límites sobre cómo se utilizan las API. Limitamos el número de conexiones simultáneas por cuenta de usuario, el número de solicitudes de API por conexión y la cantidad de tiempo de ejecución que se puede usar para cada conexión. Estos se evalúan en una ventana deslizante de cinco minutos. Cuando se supere uno de estos límites, la plataforma generará una excepción.

Los límites de API de protección de servicios ayudan a asegurarse de que los usuarios que ejecuten aplicaciones no puedan interferir unos con otros basándose en limitaciones de recursos. Los límites no afectarán a los usuarios normales de la plataforma. Solo podrán verse afectadas las aplicaciones que realicen un gran número de solicitudes de API. Los límites le proporcionan cierto grado de protección contra aumentos aleatorios e inesperados en los volúmenes de solicitudes que ponen en peligro las características de disponibilidad y rendimiento de la plataforma Common Data Service.

Dado que los complementos y las actividades de flujo de trabajo personalizadas se ejecutan en el servidor independientemente de un usuario que ha iniciado sesión, las llamadas de la API realizadas desde el código del complemento no contará para los límites de la API de protección de servicios. 

## <a name="limits"></a>Límites

> [!IMPORTANT]
> Estos límites se aplican por servidor web. Cada grupo de escalas tiene varios servidores web que pueden procesar cada solicitud según el equilibrio de carga. Estos números representan un único servidor web y, por lo tanto, el nivel de rendimiento más bajo posible debido a estos límites. Su rendimiento real debería ser mayor.
> 
> Verá diferencias significativas entre los entornos de prueba y los entornos de producción. Los entornos de prueba tienen menos recursos asignados para que puedan encontrar estos límites más fácilmente que los entornos de producción.
> 
> No se concentre demasiado en los números aquí. Lo importante es comprender que las aplicaciones que dependen de operaciones de datos de alto volumen deben diseñarse para responder a las señales que el servidor enviará para indicar cuándo se alcanzan los límites. No intente codificar soluciones basadas en los números aquí. En su lugar, utilice las técnicas descritas a continuación para obtener el mayor rendimiento posible respondiendo a las señales que enviará el servicio.

Los límites de protección del servicio esperan que la aplicación use múltiples hilos para maximizar el rendimiento. Cada hilo representa una conexión separada y cada conexión se evalúa en una ventana deslizante de 5 minutos (300 segundos).

Dentro de esa ventana deslizante de 5 minutos, hay tres aspectos que se miden como se describe en la siguiente tabla:

|Medida|Descripción|Límite por servidor web|
|--|--|--|
|Número de solicitudes|El número real de solicitudes realizadas por conexión.|6000|
|Tiempo de ejecución|La duración combinada de todas las conexiones que usan la misma cuenta de usuario| 20 minutos (1200 segundos)|
|Número de conexiones|El número de conexiones que usan la misma cuenta de usuario|52|

La combinación de **Numero de solicitudes** y **Tiempo de ejecución** explica el hecho de que algunas operaciones requieren más recursos del sistema que otras. Realizar una consulta compleja requiere más recursos del sistema que la creación o actualización de un solo registro.

Si bien las llamadas API realizadas desde el código del complemento no se contarán en el número de solicitudes, el tiempo de ejecución de esas llamadas se aplicará a la llamada de origen.

Algunas operaciones conocidas del sistema de larga duración, como ImportSolution, no tendrán el tiempo de ejecución completo incluido en el cálculo del límite. La contribución de estas llamadas al cálculo del límite se limita a 5 minutos si el tiempo de ejecución real es mayor.

Si su aplicación tiene el potencial para superar estos límites, aplique la guía que se proporciona en la sección [¿Qué debo hacer si mi aplicación supera el límite?](#what-should-i-do-if-my-application-exceeds-the-limit) siguiente.

Dependiendo de la naturaleza de los datos que está procesando, puede ajustar la cantidad de conexiones simultáneas para obtener el máximo rendimiento. Si cada operación es relativamente rápida, use más conexiones.

## <a name="what-happens-when-the-limit-is-exceeded"></a>¿Qué ocurre cuando se supera el límite?

Cuando se supera el límite, todas las solicitudes a la misma conexión devolverán respuestas de error.

Si utiliza los conjuntos de .NET SDK, la plataforma responderá con un error de WCF `FaultException<OrganizationServiceFault>`.  

| Código de error | Mensaje |
|------------|-------------------------------------|
|`-2147015902`|`Number of requests exceeded the limit of 6000, measured over time window of 300 seconds.`|
|`-2147015903`|`Combined execution time of incoming requests exceeded limit of 1,200,000 milliseconds over time window of 300 seconds. Decrease number of concurrent requests or reduce the duration of requests and try again later.`|
|`-2147015898`|`Number of concurrent requests exceeded the limit of 52`|

Si usa solicitudes HTTP con la API web, la respuesta incluirá los mismos mensajes, pero con:<br />
`StatusCode` : `429`

Todas las solicitudes devolverán estas respuestas de error hasta que el volumen de solicitudes de la API caiga por debajo del límite. Si obtiene estas respuestas, la aplicación debería dejar de enviar solicitudes de API hasta que el volumen de solicitudes esté por debajo del límite.

> [!TIP]
> Si está utilizando solicitudes HTTP con la web API, puede seguir los valores límite restantes con los siguientes encabezados de respuesta HTTP:
> 
> |Encabezado  |Descripción del valor  |
> |---------|---------|
> |`x-ms-ratelimit-burst-remaining-xrm-requests` |El número restante de solicitudes para esta conexión|
> |`x-ms-ratelimit-time-remaining-xrm-requests`  |La duración combinada restante de todas las conexiones que usan la misma cuenta de usuario|

## <a name="what-should-i-do-if-my-application-exceeds-the-limit"></a>¿Qué debería hacer si mi aplicación supera el límite?

Cuando la aplicación supera el límite, la respuesta de error desde el servidor puede especificar el período de tiempo que debe esperar antes de enviar más solicitudes. El objeto de respuesta es algo diferente si está usando conjuntos SDK o solicitudes HTTP con la API web.

Para obtener información sobre recomendaciones, vea [Control de errores transitorios de mejores prácticas de Azure Architecture](/azure/architecture/best-practices/transient-faults)

[El Polly Project](https://www.thepollyproject.org/) es una biblioteca que incluye capacidades para trabajar con errores transitorios mediante directivas de ejecución.

### <a name="http-requests-with-the-web-api"></a>Solicitudes HTTP con la API web

Si encuentra un código de error 429, puede buscar el encabezado HTTP `Retry-After` incluido en la respuesta de error. Contendrá un valor en segundos que indica cuánto tiempo debe esperar antes de realizar una solicitud de seguimiento. Más información [reintentar después de documentos web de MDN](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After)

### <a name="sdk-assemblies"></a>Ensamblados SDK

> [!NOTE]
> No necesita aplicar estos patrones cuando:
>
>  - El código se ejecutará en un complemento o actividad de flujo de trabajo personalizado. No es necesario que aplique estos patrones porque los límites de protección del servicio no se aplican en estos casos.
>  - Use el método <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. Estos patrones están integrados en ese cliente. Esta es la clase de proxy recomendada para usar para aplicaciones cliente.
>
> Debe aplicar estos patrones si usa el <xref:Microsoft.Xrm.Sdk.Client>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> o bien <xref:Microsoft.Xrm.Sdk.WebServiceClient>.<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> clases proxy.

Si está usando los ensamblados SDK con las clases de proxy <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> o <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>, puede buscar el valor de retardo de `Retry-After` en la propiedad <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> usando la tecla `"Retry-After"`. El valor devuelto es un objeto [TimeSpan](/dotnet/api/system.timespan).

## <a name="net-sdk-assembly-example"></a>Ejemplo de conjunto de .NET SDK

El ejemplo siguiente utiliza la [clase de reintento](#retry-class) que se describe a continuación para recuperar un cuenta mediante el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> . Si la solicitud da error porque se ha superado un límite de la API, la clase `Retry` esperará según un intervalo especificado por el servidor y lo intentará de nuevo.

```csharp
var qe = new QueryExpression("account") { TopCount = 1 };
EntityCollection result = Retry.Do(() => service.RetrieveMultiple(qe));
```

### <a name="retry-class"></a>Clase de reintento

La clase `Retry` muestra cómo reintentar las solicitudes que dan un error con errores transitorios basándose en códigos de error <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault> conocidos. La clase `Retry` espera antes de volver a intentar. Si el error especifica un intervalo entre reintentos, espere según el retraso especificado por el servidor. O bien utilice el retroceso exponencial para calcular el retardo según el número de reintentos efectuados.

```csharp
using System;
using System.ServiceModel;
using System.Threading;

public class Retry
{
    private const int RateLimitExceededErrorCode = -2147015902;
    private const int TimeLimitExceededErrorCode = -2147015903;
    private const int ConcurrencyLimitExceededErrorCode = -2147015898;

    public static TResult Do<TResult>(Func<TResult> func, int maxRetries = 3)
    {
        int retryCount = 0;

        while (true)
        {
            try
            {
                return func();
            }
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex) 
                when (IsTransientError(ex))
            {
                if (++retryCount >= maxRetries)
                {
                    throw;
                }

                if (ex.Detail.ErrorCode == RateLimitExceededErrorCode)
                {
                    // Use Retry-After delay when specified
                    delay = (TimeSpan)ex.Detail.ErrorDetails["Retry-After"];
                }
                else
                {
                    // else use exponential backoff delay
                    delay = TimeSpan.FromSeconds(Math.Pow(2, retryCount));
                }

                Thread.Sleep(delay);
            }
        }
    }

    private static bool IsTransientError(FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)
    {
        // You can add more transient fault codes to retry here
        if (ex.Detail.ErrorCode == RateLimitExceededErrorCode ||
            ex.Detail.ErrorCode == TimeLimitExceededErrorCode ||
            ex.Detail.ErrorCode == ConcurrencyLimitExceededErrorCode)
        {
            return true;
        }

        return false;
    }
}
```

### <a name="see-also"></a>Vea también

[Administrar Power Platform / Licencias y gestión de licencias / Límites de solicitudes y asignaciones](/power-platform/admin/api-request-limits-allocations)<br />
[Información general sobre límites de la API Common Data Service](../../maker/common-data-service/api-limits-overview.md)<br />
[Usar la API web de Common Data Service](webapi/overview.md)<br />
[Utilizar el Servicio de organización de Common Data Service](org-service/overview.md)
