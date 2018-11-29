---
title: Límites de API (Common Data Service para aplicaciones) | Microsoft Docs
description: Comprenda los límites de las solicitudes de la API.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: MicroSri
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="api-limits"></a>Límites de la API

A partir del 19 de marzo de 2018 se limitará el número de solicitudes de API realizadas por cada usuario, por instancia de organización, en un intervalo de cinco minutos. Cuando se supera este límite, se produce una excepción generada por la plataforma.

El límite le ayudará a asegurarse de que los usuarios que ejecuten aplicaciones que planteen demandas muy grandes a los servidores no afecten a otros usuarios. El límite no afectará a los usuarios normales de la plataforma. Solo se verán afectadas las aplicaciones que realicen un gran número de solicitudes de API. Según los análisis de datos de telemetría, este límite está dentro de los límites de la mayoría de aplicaciones que realizan un gran número de solicitudes de API. El límite le ayudará a proporcionar cierto grado de protección contra aumentos aleatorios e inesperados en los volúmenes de solicitudes que ponen en peligro las características de disponibilidad y rendimiento de la plataforma de Common Data Service para aplicaciones.

Si su aplicación tiene el potencial para superar el límite, tenga en cuenta la guía que se proporciona en la sección [¿Qué debo hacer si mi aplicación supera el límite?](#what-should-i-do-if-my-application-exceeds-the-limit) siguiente.

## <a name="what-is-the-limit"></a>¿Cuál es el límite?

A cada usuario se le permitirán hasta 60.000 solicitudes de API, por instancia de organización, en un intervalo deslizante de cinco minutos.

## <a name="what-happens-when-the-limit-is-exceeded"></a>¿Qué ocurre cuando se supera el límite?

Cuando se supera el límite, las solicitudes devolverán respuestas de error.

Si utiliza los conjuntos de .NET SDK, la plataforma responderá con un error de WCF de `FaultException<OrganizationServiceFault>` con el código de error `-2147015902` y el mensaje `Number of requests exceeded the limit of 60000, measured over time window of 300 seconds.`

Si usa solicitudes HTTP, la respuesta incluye estas propiedades:<br />
`StatusCode` : `429`<br />
`Message` : `Number of requests exceeded the limit of 60000, measured over time window of 300 seconds.`

Todas las solicitudes devolverán estas respuestas de error hasta que el volumen de solicitudes de la API caiga por debajo del límite. Si obtiene estas respuestas, la aplicación debería dejar de enviar solicitudes de API hasta que el volumen de solicitudes esté por debajo del límite.

## <a name="how-is-this-limit-calculated"></a>¿Cómo se calcula este límite?

Dentro de una instancia de la organización, las solicitudes de API realizadas por cada uno de los usuarios con licencia (incluida la identidad con licencia que se usa para ejecutar la automatización) se miden con respecto a este límite. La plataforma medirá el número de solicitudes API realizadas en cinco minutos, que siguen deslizándose durante un período definido. Durante cada intervalo de medición, al final de cinco minutos, se cuenta el número de solicitudes de la API por el usuario. En la siguiente imagen, tres usuarios realizan solicitudes de llamada API durante un período de seis minutos.  

![api-limit-implementation](media/api-limit-implementation-1.png)

|Intervalo|Descripción|
|--|--|
|A|Al final de cinco minutos, el número total de solicitudes de API del usuario 1 es 6K, el usuario 2 es 3K y el usuario 3 es de 10K.|
|B|En 5 + X minutos, y si X es un sector constante de tiempo (por ejemplo, unos segundos), que es la constante del intervalo deslizante, la plataforma mide el total de cada uno de estos usuarios que aún está activo. Según el diagrama anterior, esto sería usuario 1 = 7 K, usuario 2 es 6 K y el usuario 3 es 25 K. Todos los números acumulativos están aún por debajo del límite de 60.000, por lo que no se espera ningún cambio en el comportamiento de estos usuarios.|
|C|A medida que pasa el tiempo y llega a a 5 + 2 X, el usuario 3 realiza alrededor de 40 K solicitudes de API, mientras que el usuario 1 y el 2 realizan 8 K y 9 K llamadas respectivamente. Como consecuencia el usuario 3 llega a 75 K solicitudes de API dentro de cinco minutos, lo que hace que se denieguen 5 K (65 K-60 K = 5 K) de estas solicitudes.|

> [!NOTE]
> Las solicitudes que realizan varias solicitudes de API como <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> o <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest> con los conjuntos de .NET SDK o `$batch` con la API de la Web, cuentan como una sola solicitud para calcular este límite. No obstante, estas solicitudes de API deben seguir las [limitaciones de tiempo de ejecución](org-service/execute-multiple-requests.md#limitations) para esos tipos de operaciones.

## <a name="what-should-i-do-if-my-application-exceeds-the-limit"></a>¿Qué debería hacer si mi aplicación supera el límite?

Cuando la aplicación supera el límite, la respuesta de error desde el servidor especifica el período de tiempo que debe esperar antes de enviar más solicitudes. El objeto de respuesta es algo diferente si está usando conjuntos SDK o solicitudes HTTP.

Para obtener información sobre recomendaciones, vea [Control de errores transitorios de mejores prácticas de Azure Architecture](/azure/architecture/best-practices/transient-faults)

[El Polly Project](http://www.thepollyproject.org/) es una biblioteca que incluye capacidades para trabajar con errores transitorios mediante directivas de ejecución.

### <a name="http-requests"></a>Solicitudes HTTP

Si está usando solicitudes HTTP, puede buscar el encabezado HTTP `Retry-After` que se incluye en la respuesta de error. Contendrá un valor en segundos que indica cuánto tiempo debe esperar antes de realizar una solicitud de seguimiento. Más información [reintentar después de documentos web de MDN](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After)

### <a name="sdk-assemblies"></a>Ensamblados SDK

Si está usando los conjuntos SDK, puede buscar el retardo `Retry-After` en la propiedad <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> usando la tecla `"Retry-After"`. El valor devuelto es un objeto [TimeSpan](/dotnet/api/system.timespan).

### <a name="net-sdk-assembly-example"></a>Ejemplo de conjunto de .NET SDK

El ejemplo siguiente utiliza la [clase de reintento](#retry-class) que se describe a continuación para recuperar un cuenta mediante el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> . Si la solicitud da error porque se ha superado un límite de la API, la clase `Retry` esperará según un intervalo especificado por el servidor y lo intentará de nuevo.

```csharp
var qe = new QueryExpression("account") { TopCount = 1 };
EntityCollection result = Retry.Do(() => service.RetrieveMultiple(qe));
```

#### <a name="retry-class"></a>Clase de reintento

La clase `Retry` muestra cómo reintentar las solicitudes que dan un error con errores transitorios basándose en códigos de error <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault> conocidos. La clase `Retry` espera antes de volver a intentar. Si el error especifica un intervalo entre reintentos, espere según el retraso especificado por el servidor. O bien utilice el retroceso exponencial para calcular el retardo según el número de reintentos efectuados.

```csharp
using System;
using System.ServiceModel;
using System.Threading;

public class Retry
{
    private const int RateLimitExceededErrorCode = -2147015902;

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
        if (ex.Detail.ErrorCode == RateLimitExceededErrorCode)
        {
            return true;
        }

        return false;
    }
}

```



### <a name="see-also"></a>Vea también

[Usar la API web de CDS for Apps](webapi/overview.md)<br />
[Usar el servicio de organización de CDS for Apps](org-service/overview.md)<br />
[Ejecute las operaciones por lotes mediante API web](webapi/execute-batch-operations-using-web-api.md)<br />
[Usar ExecuteMultiple para mejorar el rendimiento de la carga masiva de datos](org-service/execute-multiple-requests.md)