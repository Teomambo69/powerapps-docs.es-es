---
title: Límites de la API de protección de servicios (Common Data Service) | Microsoft Docs
description: Conozca los límites de protección de servicios de las solicitudes de la API.
ms.custom: ''
ms.date: 04/20/2020
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
ms.openlocfilehash: 9f349a913056fe2a964db537b62774eccabdc21e
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275796"
---
# <a name="service-protection-api-limits"></a>Límites de la API de protección de servicio

Para garantizar una disponibilidad y un rendimiento consistentes para todos, aplicamos algunos límites sobre cómo se utilizan las API. Estos límites están diseñados para detectar cuándo las aplicaciones del cliente demandan recursos del servidor de forma extraordinaria.

Los límites no afectarán a los usuarios normales de clientes interactivos. Solo las aplicaciones cliente que realizan solicitudes API extraordinarias deberían verse afectadas. Los límites le proporcionan cierto grado de protección contra aumentos aleatorios e inesperados en los volúmenes de solicitudes que ponen en peligro las características de disponibilidad y rendimiento de la plataforma Common Data Service.

Cuando una aplicación cliente realiza solicitudes demasiado exigentes, Common Data Service sigue el patrón común para los servicios en línea. Devolvemos un error que indica que se han realizado demasiadas solicitudes.

- Con la API web, devolvemos un error [429 de demasiadas solicitudes](https://developer.mozilla.org/docs/Web/HTTP/Status/429).
- Con el servicio de organización, obtendrá un error [OrganizationServiceFault](/dotnet/api/microsoft.xrm.sdk.organizationservicefault) con uno de los tres códigos de error específicos. Más información: [Errores de límite de API de protección de servicio devueltos](#service-protection-api-limit-errors-returned)


## <a name="impact-on-client-applications"></a>Impacto en las aplicaciones cliente

Es responsabilidad de las aplicaciones cliente administrar los errores de límite de API de protección del servicio. Exactamente cómo administrar este error depende de la naturaleza de la aplicación. 

### <a name="interactive-client-applications"></a>Aplicaciones cliente interactivas

Los límites de protección del servicio son lo suficientemente altos como para que sea raro que una persona que utiliza una aplicación cliente interactiva los encuentre durante el uso normal. Sin embargo, es posible que aparezcan si la aplicación cliente permite operaciones masivas. Los desarrolladores de aplicaciones cliente deben ser conscientes de cómo se aplican los límites de API de protección del servicio y diseñar la interfaz de usuario para reducir la posibilidad de que los usuarios envíen solicitudes extremadamente exigentes al servidor. Pero aún así deben esperar que puedan ocurrir errores de límite de API de protección de servicio y estar preparados para manejarlos.

Los desarrolladores de aplicaciones cliente no deberían simplemente lanzar el error para mostrar el mensaje al usuario. El mensaje de error no está destinado a usuarios finales. Ver [Reintentar operaciones](#retry-operations) para estrategias específicas.

### <a name="data-integration-applications"></a>Aplicaciones de integración de datos

Las aplicaciones diseñadas para cargar datos en CDS o realizar actualizaciones masivas también deben poder administrar los errores de límite de API de protección del servicio. Estas aplicaciones priorizan el rendimiento para que puedan completar su trabajo en el mínimo tiempo posible. Estas aplicaciones deben tener una estrategia para volver a intentar las operaciones. Existen varias estrategias que se pueden aplicar para obtener el máximo rendimiento. Más información: [Cómo maximizar el rendimiento](#how-to-maximize-throughput).

### <a name="portal-applications"></a>Aplicaciones de portal

Las aplicaciones de portal generalmente envían solicitudes de usuarios anónimos a través de una cuenta principal de servicio único. Debido a que los límites de la API de protección del servicio se basan en cada usuario, las aplicaciones de portal pueden alcanzar los límites de la API de protección del servicio en función de la cantidad de tráfico que experimente el portal. Al igual que las aplicaciones cliente interactivas, no se espera que los errores de límite de la API de protección del servicio se muestren al usuario final del portal. Se espera que la interfaz de usuario deshabilite más solicitudes y muestre un mensaje de que el servidor está ocupado. El mensaje puede incluir la hora en que la aplicación puede comenzar a aceptar nuevas solicitudes.

## <a name="impact-on-plug-ins-and-custom-workflow-activities"></a>Impacto en complementos y actividades de flujo de trabajo personalizadas

Los complementos y las actividades de flujo de trabajo personalizadas aplican la lógica empresarial activada por las solicitudes entrantes. Los límites de protección del servicio no se aplican a complementos y actividades de flujo de trabajo personalizadas. Los complementos y las actividades de flujo de trabajo personalizadas se cargan y se ejecutan dentro del servicio de espacio aislado. Las operaciones de Common Data Service invocadas en el servicio de espacio aislado no utilizan los puntos de conexión de API públicos.

Si su aplicación realiza operaciones que desencadenan una lógica personalizada, la cantidad de solicitudes enviadas por complementos o actividades de flujo de trabajo personalizadas no se contarán para los límites de la API de protección del servicio. Sin embargo, el tiempo de cálculo adicional que suponen estas operaciones se agregará a la solicitud inicial que las activó. Este tiempo de cálculo es parte de los límites de la API de protección del servicio. Más información: [Cómo se aplican los límites de API de protección del servicio](#how-service-protection-api-limits-are-enforced)

## <a name="retry-operations"></a>Reintentar operaciones

Cuando se produce un error de límite de API de protección del servicio, proporcionará un valor que indica la duración antes de que se puedan procesar las nuevas solicitudes del usuario.

- Cuando se devuelve un error 429 de la API web, la respuesta incluirá un [Retry-After](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After) con el número de segundos.
- Con el servicio de organización, se devuelve un valor [TimeSpan](/dotnet/api/system.timespan) en <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> Recopilación con la clave `Retry-After`.

### <a name="interactive-application-re-try"></a>Reintentar aplicación interactiva 

Si el cliente es una aplicación interactiva, debe mostrar un mensaje de que el servidor está ocupado mientras reintenta la solicitud que realizó el usuario. Es posible que desee proporcionar una opción para que el usuario cancele la operación. No permita que los usuarios envíen más solicitudes hasta que se complete la solicitud anterior que envió.

### <a name="non-interactive-application-re-try"></a>Reintentar aplicación no interactiva

Si el cliente no es interactivo, la práctica común es simplemente esperar a que pase el tiempo antes de enviar la solicitud nuevamente. Esto se hace comúnmente al pausar la ejecución del subproceso actual usando [Thread.Sleep](/dotnet/api/system.threading.thread.sleep) o métodos equivalentes.



## <a name="how-service-protection-api-limits-are-enforced"></a>Cómo se aplican los límites de API de protección del servicio

Los límites de la API de protección del servicio se evalúan en una ventana deslizante de 5 minutos (300 segundos). Si se excede alguno de los límites dentro de los 300 segundos anteriores, se devolverá un error de límite de API de protección del servicio en solicitudes posteriores para proteger el servicio hasta que finalice el tiempo de Retry-After.

Los límites de la API de protección del servicio se evalúan por usuario. Cada usuario autenticado está limitado de forma independiente. Solo las cuentas de los usuarios que están haciendo demandas extraordinarias serán limitadas. Otros usuarios no se verán afectados.

Los límites de la API de protección del servicio se aplican en base a tres facetas:

- El número de solicitudes enviadas por un usuario.
- Se requería el tiempo de ejecución combinado para procesar las solicitudes enviadas por un usuario.
- El número de solicitudes simultáneas enviadas por un usuario.

Si el único límite fuera el número de solicitudes enviadas por un usuario, sería posible omitirlo. Las otras facetas se agregaron para contrarrestar estos intentos. Por ejemplo:

- Puede enviar menos solicitudes si las agrupa en operaciones por lotes.
  - El límite de tiempo de ejecución combinado contrarrestará esto.
- En lugar de enviar solicitudes de forma individual en sucesión, puede enviar una gran cantidad de solicitudes simultáneas dentro de la ventana deslizante de 5 minutos antes de que se apliquen los límites de la API de protección del servicio.
  - El límite de solicitud simultánea contrarrestará esto.

Cada servidor web disponible para su entorno impondrá estos límites de forma independiente. La mayoría de los entornos tendrán más de un servidor web. Los entornos de prueba solo tienen asignado un único servidor web. La cantidad real de servidores web que están disponibles para su entorno depende de múltiples factores que forman parte del servicio administrado que brindamos. Uno de los factores es cuántas licencias de usuario ha comprado.

La siguiente tabla describe los límites de API de protección del servicio predeterminados impuestos *por servidor web* dentro de la ventana deslizante de 5 minutos.

|Medida|Descripción|Límite por servidor web|
|--|--|--|
|Número de solicitudes|El número acumulado de solicitudes realizadas por el usuario|6000|
|Tiempo de ejecución|El tiempo de ejecución combinado de todas las solicitudes realizadas por el usuario| 20 minutos (1200 segundos)|
|Número de solicitudes simultáneas|El número de solicitudes simultáneas realizadas por el usuario|52|

> [!IMPORTANT]
> Estos límites están sujetos a cambios y pueden variar entre diferentes entornos. Estos números representan valores predeterminados y se proporcionan para darle una idea de qué valores puede esperar.

### <a name="the-retry-after-duration"></a>La duración de Retry-After

La duración de `Retry-After` dependerá de la naturaleza de las operaciones que se hayan enviado en el período de 5 minutos anterior. Cuanto más exigentes sean las solicitudes, más tiempo tardará en recuperarse el servidor.

Hoy, debido a la forma en que se evalúan los límites, puede esperar superar el número de solicitudes y los límites de tiempo de ejecución durante un período de 5 minutos antes de que los límites de la API de protección del servicio entren en vigor. Sin embargo, exceder el número de solicitudes concurrentes devolverá inmediatamente un error. Si la aplicación continúa enviando solicitudes tan exigentes, la duración se extenderá para minimizar el impacto en los recursos compartidos. Esto hará que el período de duración del reintento individual sea más largo, lo que significa que su aplicación verá períodos más largos de inactividad mientras espera. Este comportamiento puede cambiar en el futuro.

Cuando sea posible, recomendamos tratar de lograr una tasa constante comenzando con un menor número de solicitudes y aumentando gradualmente hasta que comience a alcanzar los límites de la API de protección del servicio. Después de eso, deje que el servidor le diga cuántas solicitudes puede manejar en un período de 5 minutos. Limitar número máximo de solicitudes dentro de este período de 5 minutos e ir aumentado gradualmente mantendrá baja la duración de Retry-After, optimizando su rendimiento total y minimizando los picos de recursos del servidor.

## <a name="service-protection-api-limit-errors-returned"></a>Errores de límite de API de protección del servicio devueltos

Esta sección describe los tres tipos de errores de límite de API de protección del servicio que se pueden devolver, así como los factores que causan estos errores y las posibles estrategias de mitigación.

- El **Código de error** es el valor de error numérico devuelto por el servicio de la organización <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails>.
- El **Código hexadecimal** es el valor de error hexadecimal devuelto por la API web.

### <a name="number-of-requests"></a>Número de solicitudes

Este límite cuenta el número total de solicitudes durante el período anterior de 300 segundos.

| Código de error | Código hexadecimal | Mensaje |
|------------|------------|-------------------------------------|
|`-2147015902`|`0x80072322`|`Number of requests exceeded the limit of 6000 over time window of 300 seconds.`|

No se espera que un usuario típico de una aplicación interactiva pueda enviar 1200 solicitudes por minuto para superar este límite, a menos que la aplicación permita a los usuarios realizar operaciones masivas.

Por ejemplo, si una vista de lista permite la selección de 250 registros a la vez y permite que un usuario realice alguna operación en todos estos registros, el usuario necesitaría realizar esta operación 24 veces en un lapso de 300 segundos. El usuario necesitaría completar la operación en cada lista en 12,5 segundos.

Si su aplicación proporciona esta función, debe considerar algunas de las siguientes estrategias:

- Disminuyendo el número total de registros que se pueden seleccionar en una lista. Si el número de elementos que se muestran en una lista se reduce a 50, el usuario necesitaría realizar esta operación 120 veces en 300 segundos. El usuario tendría que completar la operación en cada lista en 2,5 segundos.
- Combine las operaciones seleccionadas en un lote. Un lote puede contener hasta 1000 operaciones y evitará el límite de la cantidad de solicitudes. Sin embargo, deberá estar preparado para el límite del tiempo de ejecución.

### <a name="execution-time"></a>Tiempo de ejecución

Este límite rastrea el tiempo de ejecución combinado de las solicitudes entrantes durante el período anterior de 300 segundos.

| Código de error | Código hexadecimal | Mensaje |
|------------|------------|-------------------------------------|
|`-2147015903`|`0x80072321`|`Combined execution time of incoming requests exceeded limit of 1,200,000  milliseconds over time window of 300 seconds. Decrease number of concurrent requests or reduce the duration of requests and try again later.`|

Algunas operaciones requieren más recursos que otras. Las operaciones por lotes, la importación de soluciones y las consultas altamente complejas pueden ser muy exigentes. Estas operaciones también pueden realizarse simultáneamente en solicitudes concurrentes. Por lo tanto, dentro de la ventana de 5 minutos es posible solicitar operaciones que requerirán más de 20 minutos de tiempo de cálculo combinado.

Este límite se puede encontrar cuando se utilizan estrategias que utilizan operaciones por lotes y solicitudes simultáneas para evitar el límite de número de solicitudes.

### <a name="concurrent-requests"></a>Solicitudes simultáneas

Este límite rastrea el número total de solicitudes simultáneas durante el período anterior de 300 segundos.

| Código de error | Código hexadecimal | Mensaje |
|------------|------------|-------------------------------------|
|`-2147015898`|`0x80072326`|`Number of concurrent requests exceeded the limit of 52.`|

Las aplicaciones del cliente no se limitan a enviar solicitudes individualmente en sucesión. El cliente puede aplicar patrones de programación paralela o varios métodos para enviar múltiples solicitudes simultáneamente. El servidor puede detectar cuando responde a múltiples solicitudes del mismo usuario simultáneamente. Si se supera este número de solicitudes simultáneas, se generará este error.

Enviar solicitudes simultáneas puede ser una parte clave de una estrategia para maximizar el rendimiento, pero es importante mantenerlo bajo control.

Cuando usas [Programación en paralelo en .NET](/dotnet/standard/parallel-programming/), el grado predeterminado de paralelismo depende del número de núcleos de CPU en el servidor que ejecutan el código. No debe superar los 52. La [propiedad ParallelOptions.MaxDegreeOfParallelism](/dotnet/api/system.threading.tasks.paralleloptions.maxdegreeofparallelism) se puede configurar para definir un número máximo de tareas concurrentes.

## <a name="how-to-maximize-throughput"></a>Cómo maximizar el rendimiento

Cuando tiene una aplicación que debe priorizar el rendimiento para mover la mayor cantidad de datos en el período más corto, existen algunas estrategias que puede aplicar.

### <a name="let-the-server-tell-you-how-much-it-can-handle"></a>Deje que el servidor le diga cuánto puede asumir.

No intente calcular cuántas solicitudes enviar a la vez. Cada entorno puede ser diferente. Aumente gradualmente la tasa de envío de solicitudes hasta que comience a alcanzar los límites y luego depende del valor `Retry-After` del límite de API de protección del servicio para indicarle cuándo enviar más. Este valor mantendrá su rendimiento total en el nivel más alto posible.

### <a name="use-multiple-threads"></a>Usar varios subprocesos

El límite superior en el número de subprocesos simultáneas es algo que su aplicación puede usar para tener una mejora significativa en el rendimiento. Esto es cierto si sus operaciones individuales son relativamente rápidas. Dependiendo de la naturaleza de los datos que está procesando, es posible que deba ajustar el número de subprocesos para obtener un rendimiento óptimo.

Más información:

- [Usar la biblioteca paralela de tareas con la API web](#use-task-parallel-library-with-web-api)
- [Usar la biblioteca paralela de tareas con CrmServiceClient](#use-task-parallel-library-with-crmserviceclient)

### <a name="avoid-batching"></a>Evitar el procesamiento por lotes

En el servicio de la organización, el sentido común es emplear <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> para agrupar múltiples operaciones. La principal ventaja que proporciona es que reduce la cantidad total de carga útil SOAP XML que debe enviarse por cable. Esto proporciona alguna ventaja de rendimiento cuando la latencia de la red es un problema.

En el pasado, las operaciones ExecuteMultiple se limitaban a solo 2 a la vez debido al impacto en el rendimiento que esto podría tener. Este ya no es el caso, porque los límites de API de protección de servicio han hecho que ese límite sea redundante.

La mayoría de los escenarios serán más rápidos enviando solicitudes individuales con un alto grado de paralelismo. Si cree que el tamaño del lote puede mejorar el rendimiento, es mejor comenzar con un tamaño de lote pequeño de 10 y aumentar la simultaneidad hasta que comience a obtener errores de límite de API de protección del servicio que tendrá que volver a intentar.

Cuando se usa la API web, la carga útil JSON más pequeña enviada por cable para solicitudes individuales significa que la latencia de la red no es un problema. La cantidad total de carga útil que se envía usando $batch es mayor que el envío de solicitudes individuales. Solo use $batch si desea administrar transacciones usando conjuntos de cambios. Más información: [Ejecutar operaciones por lotes mediante la API web](webapi/execute-batch-operations-using-web-api.md)

> [!NOTE]
> Las operaciones por lotes no son una estrategia válida para eludir los límites de derechos. Los límites de API de protección del servicio y los límites de derechos se evalúan por separado. Los límites de derechos se basan en operaciones CRUD y se acumulan en función de si se incluyen o no en una operación por lotes. Más información: [Limitaciones de derechos](../../maker/common-data-service/api-limits-overview.md#entitlement-limits)

### <a name="remove-the-affinity-cookie"></a>Eliminar la cookie de afinidad

Cuando realiza una conexión a un servicio en Azure, se devuelve una cookie con la respuesta y todas sus solicitudes posteriores intentarán enrutarse al mismo servidor a menos que la administración de capacidad lo obligue a ir a otro servidor. Si elimina esta cookie, cada solicitud que envíe se enrutará a cualquiera de los servidores elegibles. Esto aumenta el rendimiento porque se aplican límites por servidor. Esto simplemente le permite usar más servidores si están disponibles.

> [!NOTE]
> Esta estrategia solo debe ser utilizada por aplicaciones que buscan optimizar el rendimiento. Las aplicaciones cliente interactivas se benefician de la cookie de afinidad porque permite reutilizar los datos almacenados en caché que de lo contrario tendrían que volver a crearse, lo que llevaría a un rendimiento más deficiente.

El siguiente código muestra cómo deshabilitar las cookies al inicializar un HttpClient con la API web, suponiendo que esté utilizando un HttpMessageHandler personalizado para administrar la autenticación. Más información: [Ejemplo que demuestra un DelegatingHandler](authenticate-oauth.md#example-demonstrating-a-delegatinghandler)

```csharp
HttpMessageHandler messageHandler = new OAuthMessageHandler(
    config,
    new HttpClientHandler() { UseCookies = false }
    );
HttpClient httpClient = new HttpClient(messageHandler)
```

Si está utilizando CrmServiceClient, agregue lo siguiente al nodo AppSettings en el archivo App.config.

```xml
<add key="PreferConnectionAffinity" value="false" /> 
```

### <a name="optimize-your-connection"></a>Optimizar la conexión

Puede esperar un mayor rendimiento optimizando la conexión. El código de muestra compatible con .NET usa esta configuración:

```csharp
//Change max connections from .NET to a remote service default: 2
System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
//Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4 
System.Threading.ThreadPool.SetMinThreads(100, 100);
//Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server 
System.Net.ServicePointManager.Expect100Continue = false;
//Can decreas overall transmission overhead but can cause delay in data packet arrival
System.Net.ServicePointManager.UseNagleAlgorithm = false;
```
Más información: [Administrar conexiones](/dotnet/framework/network-programming/managing-connections)

## <a name="strategies-to-manage-service-protection-api-limits"></a>Estrategias para administrar los límites de API de protección del servicio

Esta sección describe formas en que puede diseñar sus clientes y sistemas para evitar errores de límite de API de protección del servicio. También puede considerar cómo administra sus licencias para reducir el impacto.

### <a name="update-your-client-application"></a>Actualizar la aplicación cliente

Los límites de API de protección de servicio se han aplicado a CDS desde 2018, pero hay muchas aplicaciones cliente escritas antes de que existieran estos límites. Estos clientes no esperaban estos errores y no pueden administrar los errores correctamente. Debe actualizar estas aplicaciones y aplicar los patrones descritos en las secciones [Usar el servicio de la organización](#using-the-organization-service) o [Usar la API web](#using-the-web-api) a continuación.

### <a name="move-towards-real-time-integration"></a>Avanzar hacia la integración en tiempo real

Recuerde que el punto principal de los límites de la API de protección del servicio es suavizar el impacto de las solicitudes altamente exigentes que se producen en un corto período de tiempo. Si sus procesos comerciales actuales dependen de grandes trabajos periódicos durante la noche, semanales o mensuales que intentan procesar grandes cantidades de datos en un corto período de tiempo, considere cómo podría habilitar una estrategia de integración de datos en tiempo real. Si puede alejarse de los procesos que requieren operaciones altamente exigentes, puede reducir el impacto que tendrán los límites de protección del servicio.

## <a name="using-the-web-api"></a>Uso de la API web

Si está utilizando la API web con una biblioteca de cliente, es posible que admita el comportamiento de reintento esperado para los errores 429. Consulte con el editor de la biblioteca cliente.

Si ha escrito su propia biblioteca, puede incluir comportamientos que sean similares a los incluidos en este código de muestra para un asistente [ejemplo de clase CDSWebApiService (C#) de API web](webapi/samples/cdswebapiservice.md).

```csharp
private async Task<HttpResponseMessage> SendAsync(
    HttpRequestMessage request,
    HttpCompletionOption httpCompletionOption = HttpCompletionOption.ResponseHeadersRead,
    int retryCount = 0)
{
    HttpResponseMessage response;
    try
    {
        //The request is cloned so it can be sent again.
        response = await httpClient.SendAsync(request.Clone(), httpCompletionOption);
    }
    catch (Exception)
    {
        throw;
    }

    if (!response.IsSuccessStatusCode)
    {
        if ((int)response.StatusCode != 429)
        {
            //Not a service protection limit error
            throw ParseError(response);
        }
        else
        {
            // Give up re-trying if exceeding the maxRetries
            if (++retryCount >= config.MaxRetries)
            {
                throw ParseError(response);
            }

            int seconds;
            //Try to use the Retry-After header value if it is returned.
            if (response.Headers.Contains("Retry-After"))
            {
                seconds = int.Parse(response.Headers.GetValues("Retry-After").FirstOrDefault());
            }
            else
            {
                //Otherwise, use an exponential backoff strategy
                seconds = (int)Math.Pow(2, retryCount);
            }
            Thread.Sleep(TimeSpan.FromSeconds(seconds));

            return await SendAsync(request, httpCompletionOption, retryCount);
        }
    }
    else
    {
        return response;
    }
}
```

Quizás también quieras usa [Polly](https://github.com/App-vNext/Polly), una biblioteca de resistencia de .NET y control de errores transitorios que permite a los desarrolladores expresar políticas como Retry, Circuit Breaker, Timeout, Bulkhead Isolation y Fallback de manera fluida y segura.

### <a name="http-response-headers"></a>Encabezados de la respuesta HTTP

Si está utilizando solicitudes HTTP con la web API, puede seguir los valores límite restantes con los siguientes encabezados de respuesta HTTP:

|Encabezado  |Descripción del valor  |
|---------|---------|
|`x-ms-ratelimit-burst-remaining-xrm-requests`|El número restante de solicitudes para esta conexión|
|`x-ms-ratelimit-time-remaining-xrm-requests`|La duración combinada restante de todas las conexiones que usan la misma cuenta de usuario|

No debe depender de estos valores para controlar la cantidad de solicitudes que envía. Están destinados a fines de depuración. Si está eliminando la cookie de afinidad, estos valores se restablecen cuando se conecta a un servidor diferente.

### <a name="use-task-parallel-library-with-web-api"></a>Usar la biblioteca paralela de tareas con la API web

Para lograr un rendimiento óptimo, debe usar varios subprocesos. La Biblioteca de tareas paralelas (TPL) hace que los desarrolladores sean más productivos al simplificar el proceso de agregar paralelismo y concurrencia a las aplicaciones.

Vea estos ejemplos usando el [ejemplo de la clase CDSWebApiService (C#) de la API web](webapi/samples/cdswebapiservice.md):

- [Ejemplo de operaciones en paralelo CDSWebApiService (C#) de la API web](webapi/samples/cdswebapiservice-parallel-operations.md)
- [Ejemplo de operaciones asincrónicas CDSWebApiService (C#) de la API web](webapi/samples/cdswebapiservice-async-parallel-operations.md)


## <a name="using-the-organization-service"></a>Usar el servicio de la organización

Si usa el servicio de la organización, se recomienda que use <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. Esta clase implementa los métodos <xref:Microsoft.Xrm.Sdk.IOrganizationService> y puede administrar cualquier error de límite de API de protección de servicio que se devuelve. 

Desde la versión 9.0.2.16 de Xrm.Tooling.Connector, se pausará automáticamente y volverá a enviar la solicitud después del período de duración de Retry-After.

Si su aplicación está utilizando actualmente el nivel bajo <xref:Microsoft.Xrm.Sdk.Client>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> o bien las clases <xref:Microsoft.Xrm.Sdk.WebServiceClient>.<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> . Debería poder reemplazarlos con la clase CrmServiceClient. <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> está en desuso.

Más información:

- [Crear aplicaciones cliente de Windows mediante las herramientas XRM](/xrm-tooling/build-windows-client-applications-xrm-tools).
- [Obsolescencia del tipo de autenticación de Office365 y clase OrganizationServiceProxy para conectarse a Common Data Service](/power-platform/important-changes-coming#deprecation-of-office365-authentication-type-and-organizationserviceproxy-class-for-connecting-to-common-data-service)

### <a name="use-task-parallel-library-with-crmserviceclient"></a>Usar la biblioteca paralela de tareas con CrmServiceClient

Para lograr un rendimiento óptimo, debe usar varios subprocesos. La Biblioteca de tareas paralelas (TPL) hace que los desarrolladores sean más productivos al simplificar el proceso de agregar paralelismo y concurrencia a las aplicaciones.

Se puede usar TPL con <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> porque CrmServiceClient incluye un método <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.Clone> que permite administrar múltiples instancias del cliente con TPL. Por ejemplo, vea [Ejemplo: Biblioteca paralela de tareas con CrmServiceClient](xrm-tooling/sample-tpl-crmserviceclient.md).

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

Esta sección incluye preguntas frecuentes. Si tiene preguntas que no se responden, publíquelas usando el botón **Comentarios** en la parte inferior de esta página para enviar comentarios sobre esta página.

### <a name="im-using-an-etl-application-i-licensed-how-do-i-get-optimum-throughput"></a>Estoy usando una aplicación ETL que autoricé. ¿Cómo obtengo un rendimiento óptimo?

Trabaje con el proveedor de la aplicación ETL para conocer qué configuraciones se aplican. Asegúrese de estar utilizando una versión del producto que admita el comportamiento Retry-After.

### <a name="see-also"></a>Vea también

[Administrar Power Platform / Licencias y gestión de licencias / Límites de solicitudes y asignaciones](/power-platform/admin/api-request-limits-allocations)<br />
[Información general sobre límites de la API Common Data Service](../../maker/common-data-service/api-limits-overview.md)<br />
[Usar la API web de Common Data Service](webapi/overview.md)<br />
[Utilizar el Servicio de organización de Common Data Service](org-service/overview.md)
