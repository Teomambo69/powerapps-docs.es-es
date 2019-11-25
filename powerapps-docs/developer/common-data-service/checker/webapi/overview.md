---
title: Usar la API web del comprobador de PowerApps | Microsoft Docs
description: La API web del comprobador de PowerApps proporciona una experiencia de desarrollo que puede usarse en una gran variedad de lenguajes de programación, plataformas, y dispositivos.
ms.custom: ''
ms.date: 06/3/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 0d5f7579-304a-4d28-ba73-df30722205eb
caps.latest.revision: 1
author: mhuguet
ms.author: mhuguet
ms.reviewer: pehecke
manager: maustinjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 495a5e976ae3ef9579e96023e65be5bee85f5c01
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753036"
---
# <a name="use-the-powerapps-checker-web-api"></a>Usar la API web del comprobador de PowerApps

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

La API web del comprobador de PowerApps proporciona un mecanismo para ejecutar comprobaciones de análisis estático con personalizaciones y extensiones de la plataforma Common Data Service. Está disponible para que fabricantes y desarrolladores realicen comprobaciones de análisis estático de sus soluciones con un conjunto de reglas de prácticas recomendadas para identificar rápidamente patrones problemáticos. El servicio proporciona la lógica para la [característica del comprobador de soluciones](../../../../maker/common-data-service/use-powerapps-checker.md) en el [portal del fabricante de PowerApps](https://make.powerapps.com) y se incluye como parte de la automatización para [solicitudes enviadas a AppSource](../../publish-app-appsource.md). La interacción directamente con el servicio de esta manera permite el análisis de soluciones que se incluyen como parte de entornos locales (todas las versiones admitidas) y en línea.

 > [!IMPORTANT]
 >
 > - La API web para el comprobador de PowerApps es una característica de vista previa.
 > - [!INCLUDE[cc_preview_features_definition](../../../../includes/cc-preview-features-definition.md)]

<a name="bkmk_altApproaches"></a>

## <a name="alternative-approaches"></a>Enfoques alternativos

Antes de leer los detalles de cómo interactuar en el nivel más bajo con las API web, considere aprovechar el módulo PowerShell, Microsoft.PowerApps.Checker.PowerShell, en su lugar. Es una herramienta completamente compatible disponible en la [Galería de PowerShell](https://www.powershellgallery.com). La restricción actual es que requiere Windows PowerShell. Si no puede satisfacer este requisito, la interacción directamente con las API probablemente será la mejor opción.

<a name="bkmk_getStarted"></a>

## <a name="getting-started"></a>Introducción

Cabe dejar constancia que los análisis de soluciones pueden producir procesos de ejecución larga. Pueden llevar normalmente desde sesenta segundos hasta cinco minutos en función de diversos factores, como número, tamaño, y complejidad de personalizaciones y código. El flujo de análisis tiene varias fases y es asincrónico empezando por iniciar un trabajo de análisis con la API de estado que se usa para consultar la finalización de trabajos. Un flujo de ejemplo para un análisis es el siguiente: 

1. Obtener un símbolo de OAuth
2. Carga de llamada (para cada archivo en paralelo)
3. Análisis de llamada (inicia el trabajo de análisis)
4. Estado de llamada hasta terminada (bucle con una pausa entre llamadas hasta que se señala el final o se llega a los umbrales)
5. Descargar los resultados del URI de SAS proporcionado

Algunas variaciones:

- Incluir una búsqueda del conjunto de reglas o de las reglas como paso previo. Sin embargo, sería un poco más rápido pasar en un identificador de conjunto de reglas configurado o codificado de forma rígida. Se recomienda usar un conjunto de reglas que cubra sus necesidades.
- Puede optar por no usar el mecanismo de carga (vea la carga para limitaciones).

Deberá determinar lo siguiente:

- [¿Qué geografía?](#determine-a-geography)
- [¿Qué versión?](#versioning)
- [¿Qué conjuntos de reglas y reglas?](#rulesets-and-rules)
- [¿Qué es el identificador de inquilino?](#find-your-tenant-id)

Consulte los temas siguientes para documentación sobre las API individuales:

[Recuperar la lista de conjuntos de reglas](retrieve-rulesets.md)<br />
[Recuperar la lista de reglas](retrieve-rules.md)<br />
[Cargar un archivo](upload-file.md)<br />
[Invocar análisis](analyze.md)<br />
[Comprobar estado de análisis](check-status.md)<br />

<a name="bkmk_geo"></a>

## <a name="determine-a-geography"></a>Determinar una geografía

Cuando se interactúa con el servicio del comprobador de PowerApps, los archivos se almacenan temporalmente en Azure junto con informes que se generan. Mediante el uso de una API específica de la geografía puede controlar dónde se almacenan los datos. Se recomienda usar la misma geografía para cada llamada de API en el ciclo de vida de análisis. Cada geografía puede tener una versión diferente en cualquier momento determinado en el tiempo debido a nuestro método seguro de implementación de varias etapas y al hacer se asegura compatibilidad completa de la versión. También puede reducir el tiempo de ejecución ya que los datos no tendrán que viajar tan lejos en algunos casos. Las siguientes son las geografías disponibles:

|Centro de datos de Azure|Nombre|Zona geográfica|URI base|
|---|---|---|---|
|Pública|Vista previa|Estados Unidos|unitedstatesfirstrelease.api.advisor.powerapps.com|
|Pública|Producción|Estados Unidos|unitedstates.api.advisor.powerapps.com|
|Pública|Producción|Europa|europe.api.advisor.powerapps.com|
|Pública|Producción|Asia|asia.api.advisor.powerapps.com|
|Pública|Producción|Australia|australia.api.advisor.powerapps.com|
|Pública|Producción|Japón|japan.api.advisor.powerapps.com|
|Pública|Producción|India|india.api.advisor.powerapps.com|
|Pública|Producción|Canadá|canada.api.advisor.powerapps.com|
|Pública|Producción|Sudamérica|southamerica.api.advisor.powerapps.com|
|Pública|Producción|Reino Unido|unitedkingdom.api.advisor.powerapps.com|

> [!NOTE]
>  Puede optar por usar la geografía de vista previa para incorporar antes las últimas características y cambios. Sin embargo, tenga en cuenta que la vista previa usa solo las regiones de Azure de Estados Unidos.

<a name="bkmk_versioning"></a>

## <a name="versioning"></a>Control de versiones

Aunque no es necesario, se recomienda incluir el parámetro de cadena de consulta de la versión de API con la versión de la API deseada. La versión actual de la API es 1.0. Por ejemplo, a continuación encontrará una solicitud HTTP de conjunto de reglas que especifica para usar la versión 1.0 de la API:

`https://unitedstatesfirstrelease.api.advisor.powerapps.com/api/ruleset?api-version=1.0`

Si no se proporciona, se usará de forma predeterminada la última versión de la API. Se recomienda utilizar un número de versión explícito ya que la versión se incrementará si se introducen cambios importantes. Si el número de versión se especifica en una solicitud, se mantendrá el soporte de compatibilidad con versiones anteriores en versiones posteriores (numéricamente mayores).

<a name="bkmk_rules"></a>

## <a name="rulesets-and-rules"></a>Conjuntos de reglas y reglas

l comprobador de PowerApps requiere una lista de reglas cuando se ejecuta. Estas reglas se pueden proporcionar en forma de reglas individuales o agrupaciones de reglas, denominadas *conjuntos de reglas*. Un conjunto de reglas es una forma cómoda de especificar un grupo de reglas en lugar de especificar cada regla individualmente. Por ejemplo, la característica del comprobador de soluciones usa un conjunto de reglas llamado *Comprobador de soluciones*. Cuando se agregan o se quitan reglas, el servicio incluirá estos cambios automáticamente sin requerir ningún cambio por parte de la aplicación que consume. Si requiere que la lista de reglas no cambie automáticamente como se describe anteriormente, pueden especificar reglas de forma individual.
Los conjuntos de reglas pueden tener runa o varias reglas sin límite. Una regla puede no estar en ningún conjunto de reglas o en varios. Puede obtener una lista de todos los conjuntos de reglas llamando a la API de la siguiente manera: `[Geographical URL]/api/ruleset`. Esta extremo esté abierto y no requiere autenticación.

### <a name="solution-checker-ruleset"></a>Conjunto de reglas del comprobador de soluciones

El conjunto de reglas del comprobador de soluciones contiene un conjunto de reglas que repercuten que tienen posibilidades limitadas de falsos positivos. Si ejecuta análisis con una solución existente, se recomienda que comience con este conjunto de reglas. Este es el conjunto de reglas usado por la [característica del comprobador de soluciones](../../../../maker/common-data-service/use-powerapps-checker.md).

### <a name="appsource-certification-ruleset"></a>Conjunto de reglas de certificación de AppSource

Cuando se publican aplicaciones en AppSource, debe certificar su aplicación. [Las aplicaciones publicadas en AppSource](../../publish-app-appsource.md) son necesarias para cumplir un estándar de alta calidad. El conjunto de reglas de certificación de AppSource contiene las reglas que forman parte del conjunto de reglas del comprobador de soluciones, además de reglas adicionales para garantizar que solo aplicaciones de alta calidad se publican en el almacén. Algunas reglas de certificación de AppSource son más propensas a falsos positivos y pueden requerir atención adicional para su resolución.

<a name="bkmk_tenant"></a>

## <a name="find-your-tenant-id"></a>Buscar el identificador de inquilino

El identificador del inquilino es necesario para interactuar con las API que requieren un símbolo. Consulte [este artículo](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id) para los detalles sobre cómo obtener el identificador de inquilinos. También puede usar los comandos de PowerShell para recuperar el identificador de inquilinos. El siguiente ejemplo aprovecha los cmdlets en el [módulo de AzureAD](https://docs.microsoft.com/powershell/module/azuread/?view=azureadps-2.0).

```powershell
# Login to AAD as your user
Connect-AzureAD

# Establish your tenant ID
$tenantId = (Get-AzureADTenantDetail).ObjectId
```

El identificador de inquilinos es el valor de la propiedad `ObjectId` que se devuelve de `Get-AzureADTenantDetail`. También puede verlo después de iniciar sesión utilizando el cmdlet Connect-AzureAD en la salida de cmdlet. En este caso, se llamará `TenantId`.

<a name="bkmk_auth"></a>

## <a name="authentication-and-authorization"></a>Autenticación y autorización

 La consulta de reglas y conjuntos de reglas no requiere un símbolo OAuth, pero todas las demás API requieren el símbolo. Las API admiten detección de autorización llamando a cualquiera de las API que requieren un símbolo. La respuesta será un código de estado HTTP no autorizado de 401 con un encabezado de WWW-Authenticate, el URI de autorización y el ID de recursos. También debe proporcionar el identificador de inquilinos en el encabezado `x-ms-tenant-id`. Consulte [Autenticación y autorización del Comprobador de PowerApps](/powershell/powerapps/overview#powerapps-checker-authentication-and-authorization) para obtener más información. A continuación se proporciona un ejemplo del encabezado de respuesta devuelto de una solicitud API:

```http
WWW-Authenticate →Bearer authorization_uri="https://login.microsoftonline.com/0082fff7-33c5-44c9-920c-c2009943fd1e", resource_id="https://api.advisor.powerapps.com/"
```

Cuando tenga esta información, puede elegir usar la Azure Active Directory Authentication Library (ADAL) o algún otro mecanismo para adquirir el símbolo. A continuación se proporciona un ejemplo de cómo se realiza esto mediante C# y la [biblioteca ADAL, versión 4.5.1](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/4.5.1):

```c#
// Call the status URI as it is the most appropriate to use with a GET.
// The GUID here is just random, but needs to be there.
Uri queryUri = new Uri($"{targetServiceUrl}/api/status/4799049A-E623-4B2A-818A-3A674E106DE5");
AuthenticationParameters authParams = null;

using (var client = new HttpClient())
{
    var request = new HttpRequestMessage(HttpMethod.Get, queryUri);
    request.Headers.Add("x-ms-tenant-id", tenantId.ToString());

    // NOTE - It is highly recommended to use async/await
    using (var response = client.SendAsync(request).GetAwaiter().GetResult())
    {
        if (response.StatusCode == System.Net.HttpStatusCode.Unauthorized)
        {
            // NOTE - It is highly recommended to use async/await
            authParams = AuthenticationParameters.CreateFromUnauthorizedResponseAsync(response).GetAwaiter().GetResult();
        }
        else
        {
            throw new Exception($"Unable to connect to the service for authorization information. {response.ReasonPhrase}");
        }
    }
}
```

Una vez que ha adquirido el símbolo, se aconseja que proporcione el mismo símbolo a las llamadas posteriores en el ciclo de vida de la solicitud. Sin embargo, las solicitudes adicionales garantizarán probablemente que se adquiera un nuevo símbolo por razones de seguridad.

<a name="bkmk_transport"></a>

## <a name="transport-security"></a>Seguridad de transporte
Para el conseguir el mejor cifrado de su clase, el servicio del comprobador sólo admite comunicaciones usando Seguridad de la capa de transporte (TLS) 1.2 y superior. Para obtener instrucciones sobre las prácticas recomendadas de .NET en relación con TLS, consulte [Prácticas recomendadas de Seguridad de la capa de transporte (TLS) con .NET Framework](https://docs.microsoft.com/dotnet/framework/network-programming/tls).

<a name="bkmk_report"></a>

## <a name="report-format"></a>Formato de informe

El resultado del análisis de soluciones es un archivo zip que contiene uno o varios informes en formato estandarizado JSON. El formato de informe se basa en resultados de análisis estáticos denominado Static Analysis Results Interchange Format (SARIF). Hay herramientas disponibles para ver e interactuar con documentos SARIF. Consulte este [sitio web](https://sarifweb.azurewebsites.net/) para detalles. El servicio se basa en la versión dos de la [norma OASIS](https://docs.oasis-open.org/sarif/sarif/v2.0/sarif-v2.0.html).


### <a name="see-also"></a>Vea también

[Recuperar la lista de conjuntos de reglas](retrieve-rulesets.md)<br />
[Recuperar la lista de reglas](retrieve-rules.md)<br />
[Cargar un archivo](upload-file.md)<br />
[Invocar análisis](analyze.md)<br />
[Comprobar estado de análisis](check-status.md)<br />