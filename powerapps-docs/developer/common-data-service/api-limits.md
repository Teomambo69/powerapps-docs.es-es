---
title: Límites de la API (Common Data Service) | Microsoft Docs
description: Comprenda los límites de las solicitudes de la API.
ms.custom: ''
ms.date: 03/21/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: bsimons
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d6b332b1e71a8d440c02cc79f7566eec59533cce
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753084"
---
# <a name="api-limits"></a>Límites de la API

Se limita el número de solicitudes de API realizadas por cada usuario, por instancia de organización, en una ventana deslizante de cinco minutos. Asimismo, limitamos el número de solicitudes simultáneas que pueden producirse en un momento dado.  Cuando se supere uno de estos límites, la plataforma generará una excepción.

El límite le ayudará a asegurarse de que los usuarios que ejecuten aplicaciones no puedan interferir unos con otros basándose en limitaciones de recursos. Los límites no afectarán a los usuarios normales de la plataforma. Solo podrán verse afectadas las aplicaciones que realicen un gran número de solicitudes de API. El límite le ayudará a proporcionar cierto grado de protección contra aumentos aleatorios e inesperados en los volúmenes de solicitudes que ponen en peligro las características de disponibilidad y rendimiento de la plataforma Common Data Service.

Dado que los complementos y las actividades de flujo de trabajo personalizadas se ejecutan en el servidor independientemente de un usuario que ha iniciado sesión, las llamadas de la API realizadas desde el código del complemento no contará para este límite de solicitudes de API externas.

Si su aplicación tiene el potencial para superar el límite, tenga en cuenta la guía que se proporciona en la sección [¿Qué debo hacer si mi aplicación supera el límite?](#what-should-i-do-if-my-application-exceeds-the-limit) siguiente.

## <a name="what-happens-when-the-limit-is-exceeded"></a>¿Qué ocurre cuando se supera el límite?

Cuando se supera el límite, todas las solicitudes al mismo usuario devolverán respuestas de error.

Si utiliza los conjuntos de .NET SDK, la plataforma responderá con un error de WCF `FaultException<OrganizationServiceFault>`.  

| Código de error | Mensaje |
|------------|-------------------------------------|
|`-2147015902`|`Number of requests exceeded the limit of 4000, measured over time window of 300 seconds.`|
|`-2147015903`|`Combined execution time of incoming requests exceeded limit of 1,200,000 milliseconds over time window of 300 seconds. Decrease number of concurrent requests or reduce the duration of requests and try again later.`|
|`-2147015898`|`Number of concurrent requests exceeded the limit of X`|

Si usa solicitudes HTTP, la respuesta incluirá los mismos mensajes, pero con:<br />
`StatusCode` : `429`

Todas las solicitudes devolverán estas respuestas de error hasta que el volumen de solicitudes de la API caiga por debajo del límite. Si obtiene estas respuestas, la aplicación debería dejar de enviar solicitudes de API hasta que el volumen de solicitudes esté por debajo del límite.

## <a name="what-should-i-do-if-my-application-exceeds-the-limit"></a>¿Qué debería hacer si mi aplicación supera el límite?

Cuando la aplicación supera el límite, la respuesta de error desde el servidor puede especificar el período de tiempo que debe esperar antes de enviar más solicitudes. El objeto de respuesta es algo diferente si está usando conjuntos SDK o solicitudes HTTP.

Para obtener información sobre recomendaciones, vea [Control de errores transitorios de mejores prácticas de Azure Architecture](/azure/architecture/best-practices/transient-faults)

[El Polly Project](https://www.thepollyproject.org/) es una biblioteca que incluye capacidades para trabajar con errores transitorios mediante directivas de ejecución.

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

[Usar la API web de Common Data Service](webapi/overview.md)<br />
[Utilizar el Servicio de organización de Common Data Service](org-service/overview.md)<br />
[Ejecute las operaciones por lotes mediante API web](webapi/execute-batch-operations-using-web-api.md)<br />
[Usar ExecuteMultiple para mejorar el rendimiento de la carga masiva de datos](org-service/execute-multiple-requests.md)
