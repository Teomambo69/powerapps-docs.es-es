---
title: Registrar un webhook (Common Data Service) | Microsoft Docs
description: En este tema se describirá cómo registrar un webhook mediante la herramienta de registro de complementos
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 27bf02f8b050e9638b281f74018c9e914364fa94
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "3005101"
---
# <a name="register-a-webhook"></a>Registrar un webhook

Utilice la herramienta de registro de complementos para registrar un webhook. Para obtener la herramienta de registro de complementos, consulte [Descargar herramientas de NuGet](download-tools-nuget.md). 

En la herramienta de registro de complementos puede seleccionar una nueva opción **Registrar nuevo webhook**.

![Muestra la opción de menú para registrar un nuevo webhook. El método abreviado de teclado es Ctrl+W](media/register-new-web-hook.PNG)

Al registrar un webhook debe proporcionar tres elementos de información:


|Elemento  |Descripción  |
|---------|---------|
|**Nombre**|Un nombre único que describa el webhook.|
|**URL de extremo**|La URL para publicar información de contexto de ejecución.|
|**Autenticación**|Una de las tres opciones de autenticación. Para cualquier tipo de autenticación, debe proporcionar las claves que identificarán la solicitud como legítima.|

## <a name="authentication-options"></a>Opciones de autenticación

La opción y los valores correctos de autenticación de registro de webhook que se van a utilizar dependen de lo que se espere del extremo.  El propietario del extremo debe indicarle qué utilizar. Para usar webhooks con Common Data Service, el extremo debe permitir una de las tres opciones de autenticación que se describen a continuación:


|Tipo  |Descripción  |
|---------|---------|
|**HttpHeader**|Incluye uno o varios pares de valores clave en el encabezado de la solicitud http.<br />Ejemplo: <br />`Key1: Value1`<br />`Key2: Value2`|
|**WebhookKey**|Incluye una cadena de consulta mediante `code` como clave y un valor requerido para el punto de conexión. Al registrar el webhook mediante la herramienta de registro de complementos, escriba solo el valor.<br />Ejemplo: <br />`?code=00000000-0000-0000-0000-000000000001`|
|**HttpQueryString**|Incluye uno o varios pares de valor clave como parámetros de cadena de consulta.<br />Ejemplo: <br />`?Key1=Value1&Key2=Value2`|

> [!NOTE]
> La opción **WebhookKey** es útil con [funciones de Azure](https://azure.microsoft.com/services/functions/) porque se espera que la cadena de consulta de autenticación tenga un nombre de clave de `code`.

Cualquier solicitud para el extremo configurado debe fallar cuando no coinciden las opciones de autenticación pasadas en la solicitud. Esto es responsabilidad del extremo.

<a name="query-webhook-registrations"></a>

## <a name="query-webhook-registrations"></a>Consultar registros webhook

Los registros webhook se almacenan en la [Entidad ServiceEndpoint](reference/entities/serviceendpoint.md) y tienen un valor [Contrato](reference/entities/serviceendpoint.md#BKMK_Contract) de `8`.

Puede encontrar detalles sobre los webhooks registrados consultando la entidad **ServiceEndpoint**.

**API web:**

`GET [organization URI]/api/data/v9.0/serviceendpoints?$filter=contract eq 8&$select= serviceendpointid,name,authtype,url`

Para obtener más información, consulte [Consultar datos mediante la API web](webapi/query-data-web-api.md)

**FetchXml:**

```xml
<fetch>
  <entity name="serviceendpoint" >
    <attribute name="serviceendpointid" />
    <attribute name="name" />
    <attribute name="authtype" />
    <attribute name="url" />
    <filter>
      <condition attribute="contract" operator="eq" value="8" />
    </filter>
  </entity>
</fetch> 
```

Más información: [Uso de FetchXML con FetchExpression](org-service/entity-operations-query-data.md#use-fetchxml-with-fetchexpression)

La información detallada sobre el conjunto de valores de autenticación se encuentra en la propiedad [AuthValue](reference/entities/serviceendpoint.md#BKMK_AuthValue) y no se puede recuperar.

## <a name="register-a-step-for-a-webhook"></a>Registrar un paso para un webhook

Registrar un paso para un webhook es similar a registrar un paso para un complemento. La diferencia principal es que no se puede especificar ninguna información de configuración. 

Al igual que un complemento, especifique el mensaje y la información sobre las entidades cuando corresponda. También puede especificar en qué lugar de la canalización del evento se ejecutará el webhook, el modo de ejecución y si se eliminará algún **AsyncOperation** cuando la operación tenga éxito. 

![Diálogo de registro de complemento para registrar un nuevo paso de webhook](media/Plugin-registration-register-webhook-step.PNG)

La información sobre la **Nombre del paso** y la **Descripción** se rellenará automáticamente en función de las opciones que elija, pero puede cambiarlas. Si no establece algunos **Atributos de filtro** para un mensaje que los admita, se le pedirá que lo haga como las prácticas recomendadas de rendimiento.

### <a name="execution-mode-and-debugging-your-web-hook-registration"></a>El modo de ejecución y depuración del registro de su webhook

Su elección al registrar el webhook cambia la experiencia que tendrá al depurar si las cosas no funcionan.

#### <a name="asynchronous-mode"></a>Modo asincrónico
Cuando utilice un modo de ejecución asincrónica, se creará un trabajo de operación asincrónica para capturar el éxito o fracaso de la operación. Si elimina la operación asincrónica cuando tiene éxito ahorrará espacio en la base de datos. 

Cualquier error que se produzca se registrará en los trabajos del sistema. En la aplicación web puede ir a **Configuración > Sistema > Trabajos del sistema** para revisar el estado de cualquier webhoook. Habrá un valor **Razón para el estado** de **Erróneo**. Abra la entidad de trabajo del sistema erróneo para encontrar detalles que describan la razón por la que falló el trabajo.

<a name="query-failed-asynchronous-jobs-for-a-given-step"></a>

#### <a name="query-failed-asynchronous-jobs-for-a-given-step"></a>Consultar trabajos asincrónicos que dan error para un paso determinado

Cuando conozca el **sdkmessageprocessingstepid** de un paso determinado, puede consultar la [Entidad AsynchronousOperations](reference/entities/asyncoperation.md) para cualquier error. Puede usar el valor [OwningExtensionId](reference/entities/asyncoperation.md#BKMK_OwningExtensionId) para filtrar los resultados para un paso registrado específico. Los siguientes ejemplos utilizan *&lt;stepid&gt;* para el **sdkmessageprocessingstepid** del paso.

> [!TIP]
> Para obtener el **sdkmessageprocessingstepid** de un paso dado, consulte [Consultar pasos registrados para un webhook](#query-steps-registered-for-a-webhook) a continuación.

**API web:**

`GET [organization URI]/api/data/v9.0/asyncoperations?$orderby=completedon desc&$filter=statuscode eq 31 and _owningextensionid_value eq @stepid&$select=name,friendlymessage,errorcode,message,completedon?@stepid=<stepid>`

Para obtener más información, consulte [Consultar datos mediante la API web](webapi/query-data-web-api.md)

**FetchXML:**

```xml
<fetch>
  <entity name="asyncoperation" >
    <attribute name="name" />
        <attribute name="friendlymessage" />
    <attribute name="errorcode" />
    <attribute name="message" />
    <attribute name="completedon" />     
    <filter>
      <condition attribute="owningextensionid" operator="eq" value="<stepid>" />
    </filter>
    <order attribute="completedon" descending="true" />
  </entity>
</fetch>
```

Más información: [Uso de FetchXML con FetchExpression](org-service/entity-operations-query-data.md#use-fetchxml-with-fetchexpression)

#### <a name="synchronous-mode"></a>Modo sincrónico

[!INCLUDE [synchronous-webhook-error](includes/synchronous-webhook-error.md)]

> [!NOTE]
> Debe usar el modo sincrónico cuando sea importante que la operación desencadenada por el webhook se produzca de inmediato o si desea que toda la transacción falle salvo que el servicio reciba la carga de webhook. Un registro simple de paso de webhook proporciona opciones limitadas para administrar errores, pero también puede llamar webhooks mediante actividades de flujo de trabajo de complementos si necesita más control. Más información: [Llamar un webhook de la actividad de un flujo de trabajo o del complemento](use-webhooks.md#invoke-a-webhook-from-a-plugin-or-workflow-activity).

## <a name="query-steps-registered-for-a-webhook"></a>Pasos de consulta registrados para un webhook

Los datos para webhooks registrados se encuentran en la [Entidad SdkMessageProcessingStep](reference/entities/sdkmessageprocessingstep.md).

Puede consultar los pasos registrados para un webhook específico cuando conozca el serviceendpointid para el webhook. Consulte [Consultar registros webhook](#query-webhook-registrations) para obtener el identificador de un webhook registrado en una consulta.

**Api web:**

Puede usar esta consulta de API web en la que *&lt;id&gt;* es el [ServiceEndpointId](reference/entities/serviceendpoint.md#BKMK_ServiceEndpointId) del webhook:

```http
GET [organization URI]/api/data/v9.0/serviceendpoints(@id)/serviceendpoint_sdkmessageprocessingstep?$select=sdkmessageprocessingstepid,name,description,asyncautodelete,filteringattributes,mode,stage?@id=<id>
```

Para obtener más información sobre el paso registrado, puede usar esta consulta de API web en la que *&lt;stepid&gt;* es el [SdkMessageProcessingStepId](reference/entities/sdkmessageprocessingstep.md#BKMK_SdkMessageProcessingStepId) para el paso:

```http
GET [organization URI]/api/data/v9.0/sdkmessageprocessingsteps(@id)?$select=name,description,filteringattributes,asyncautodelete,mode,stage&$expand=plugintypeid($select=friendlyname),eventhandler_serviceendpoint($select=name),sdkmessagefilterid($select=primaryobjecttypecode),sdkmessageid($select=name)?@id=<stepid>
```

**FetchXML:**

Puede usar este FetchXML para obtener la misma información en una consulta en la que *&lt;serviceendpointid&gt;* es el id. del webhook:

```xml
<fetch>
  <entity name="sdkmessageprocessingstep" >
    <attribute name="name" />
    <attribute name="filteringattributes" />
    <attribute name="stage" />
    <attribute name="asyncautodeletename" />
    <attribute name="description" />
    <attribute name="mode" />
    <link-entity name="serviceendpoint" from="serviceendpointid" to="eventhandler" link-type="inner" alias="endpnt" >
      <attribute name="name" />
      <filter>
        <condition attribute="serviceendpointid" operator="eq" value="<serviceendpointid>" />
      </filter>
    </link-entity>
    <link-entity name="sdkmessagefilter" from="sdkmessagefilterid" to="sdkmessagefilterid" link-type="inner" alias="fltr" >
      <attribute name="primaryobjecttypecode" />
    </link-entity>
    <link-entity name="sdkmessage" from="sdkmessageid" to="sdkmessageid" link-type="inner" alias="msg" >
      <attribute name="name" />
    </link-entity>
  </entity>
</fetch>
```

## <a name="next-steps"></a>Pasos siguientes

[Probar el registro de webhook con un sitio de registro de solicitud](test-webhook-registration.md)<br />
[Utilice webhooks para crear controladores externos para eventos de servidor](use-webhooks.md)

