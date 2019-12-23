---
title: Componer solicitudes HTTP y administrar errores (Common Data Service)| Microsoft Docs
description: Obtenga información sobre los métodos y encabezados de HTTP que forman parte de las solicitudes HTTP que interactúan con la API web y cómo identificar y controlar errores devueltos en la respuesta.
ms.custom: ''
ms.date: 11/05/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 64a39182-25de-4d31-951c-852025a75811
caps.latest.revision: 13
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 405e27d3461f78a2452de1c8b19d99d4d827d879
ms.sourcegitcommit: abeedb952afc5e09ae4c158611e4813b63cb49b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2019
ms.locfileid: "2854678"
---
# <a name="compose-http-requests-and-handle-errors"></a>Componer solicitudes HTTP y administrar errores

La interacción con la API web se realiza creando y enviando solicitudes HTTP. Debe saber cómo establecer los encabezados HTTP apropiados y administrar los errores incluidos en la respuesta.  

<a name="bkmk_url_versions"></a>

## <a name="web-api-url-and-versions"></a>Dirección URL y versiones de API web

Para acceder a la API web, debe crear una dirección URL con los componentes de la tabla siguiente.

|Parte|Descripción|
|--|--|
|Protocolo| `https://`|
|Nombre de entorno|El nombre único que se aplica al entorno. Si el nombre de su empresa es *Contoso*, entonces puede ser `contoso`.|
|Región|El entorno normalmente estará disponible en un centro de datos que tenga cercano geográficamente.<br />Norteamérica: `crm`<br />Sudamérica: `crm2`<br />Canadá: `crm3`<br />Europa, Oriente Medio y África (EMEA): `crm4`<br />Área Asia Pacífico (APAC): `crm5`<br />Oceanía: `crm6`<br />Japón: `crm7`<br />India: `crm8`<br />Norteamérica 2: `crm9`<br />Reino Unido: `crm11`<br />Francia: `crm12`<br />Más valores se agregarán a lo largo del tiempo a medida que se abran nuevas regiones del centro de datos.|
|URL base|`dynamics.com.`|
|Ruta de la API web|La ruta a la API web es `/api/data/`.|
|Versión|   La versión se expresa de esta manera: `v[Major_version].[Minor_version][PatchVersion]/`. La versión válida para esta publicación es `v9.0`.|
|Recurso|El nombre, la función o la acción de entidad que desea usar.|


La dirección URL que use se conformará con estas partes: protocolo + Nombre de entorno + región + dirección URL base + ruta de la API web + versión + recurso.

<a name="version_compatiblity"></a>

###   <a name="version-compatibility"></a>Compatibilidad de versiones

Esta versión incorpora funciones que no están disponibles en las versiones anteriores. Las versiones secundarias posteriores pueden proporcionar capacidades adicionales que no se aplicarán a las versiones secundarias anteriores. El código redactado para v9.0 seguirá funcionando en futuras versiones cuando haga referencia a v9.0 en la dirección URL que use.

A medida que se lancen nuevas versiones, es posible que entren en conflicto con las versiones anteriores. Esto es necesario para ir mejorando el servicio. La mayoría de las veces, las funciones permanecen igual entre las versiones, pero no debería suponer que lo harán.

> [!NOTE]
> A diferencia de las versiones v8.x de menor importancia, las nuevas funciones u otros cambios que se agreguen a las versiones futuras no se aplicarán a las versiones anteriores.
> Deberá prestar atención a la versión del servicio que usa y probar el código si cambia la versión utilizada.

<a name="bkmk_methods"></a>

## <a name="http-methods"></a>Métodos HTTP

 Las solicitudes HTTP pueden aplicar una variedad de métodos diferentes. Cuando use la API web, utilizará únicamente los métodos descritos en la tabla siguiente.  
  
|Método|Uso|  
|------------|-----------|  
|GET|Use para recuperar datos, incluida la llamada a funciones. El código de estado esperado para una recuperación correcta es 200 OK.|  
|POST|Use para crear entidades o llamar a acciones.|  
|PATCH|Use para actualizar entidades o realizar operaciones de upsert.|  
|DELETE|Use para eliminar entidades o propiedades individuales de entidades.|  
|PUT|Use en situaciones limitadas para actualizar propiedades individuales de entidades. Este método no se recomienda para actualizar la mayoría de las entidades. Lo utilizará para actualizar entidades de modelo.|  
  
<a name="bkmk_headers"></a>

## <a name="http-headers"></a>Encabezados de HTTP

Aunque el protocolo OData permite los formatos JSON y ATOM, la API web solo admite JSON. Por tanto, se pueden aplicar los siguientes encabezados.  
  
Cada solicitud debe incluir el valor del encabezado Accept de `application/json`, aunque no se espere ningún cuerpo de la respuesta. Los errores devueltos en la respuesta se devolverán como JSON. Pese a que su código debería funcionar aunque este encabezado no esté incluido, se recomienda incluirlo como procedimiento recomendado  
  
La versión de OData actual es la 4.0, pero las versiones futuras pueden permitir nuevas funciones. Para asegurarse de que no haya ambigüedades sobre la versión de OData que será aplicada al código en ese momento del futuro, debe incluir siempre una instrucción explícito de la versión actual de OData y la versión máxima para aplicar en el código. Usar encabezados OData-Version y OData-MaxVersion establecidos en un valor de 4.0.  
 
Las consultas que expanden propiedades de navegación valorada como colección pueden devolver datos en caché para las propiedades que no reflejan cambios recientes. Incluya el encabezado `If-None-Match: null` en el cuerpo de la solicitud para reemplazar la memoria caché del explorador de la solicitud de la API web. Para obtener más información, consulte [Protocolo de transferencia de hipertexto (HTTP/1.1): Solicitudes condicionales 3.2: If-None-Match](https://tools.ietf.org/html/rfc7232#section-3.2).
 
Todos los encabezados HTTP deben incluir al menos los siguientes encabezados.  
  
```
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0
If-None-Match: null
```  
  
Cada solicitud que incluya datos de JSON en el cuerpo de la solicitud debe incluir un encabezado Content-Type con un valor de `application/json`.  
  
```  
Content-Type: application/json  
```  
  
Puede usar encabezados adicionales para habilitar funcionalidades específicas.  
  
-   Para devolver datos al crear operaciones (POST) o actualizar operaciones (PATCH) para entidades, incluya la preferencia `return=representation`. Cuando esta preferencia se aplica a una solicitud de POST, una respuesta correcta tendrá el estado 201 (Creados). Para una solicitud PATCH, una respuesta correcta tendrá un estado 200 (OK). Sin esta preferencia aplicada, ambas operaciones devolverán el estado 204 (sin contenido) para reflejar que no se devuelve ningún dato en el cuerpo de la respuesta de forma predeterminada.  
  
-   Para devolver los valores con formato con una consulta, incluya la preferencia odata.include anotaciones establecida en Microsoft.Dynamics.CRM.formattedvalue con el encabezado [Prefer](https://tools.ietf.org/html/rfc7240). Más información:[Incluir valores con formato](query-data-web-api.md#bkmk_includeFormattedValues).  
  
-   También puede usar el encabezado Prefer con la opción odata.maxpagesize para especificar el número de páginas desea devolver. Más información:[Especifique el número de entidades para devolver a una página](query-data-web-api.md#bkmk_specifyNumber)  
  
-   Para suplantar a otro usuario cuando el autor de la llamada tiene privilegios para ello, agregue el encabezado MSCRMCallerID con el valor systemuserid del usuario que desea suplantar. Más información:[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md).  
  
-   Para aplicar simultaneidad optimista, puede aplicar el encabezado [If-Match](https://tools.ietf.org/html/rfc7232#section-3.1) con un valor Etag. Más información:[Aplicar simultaneidad optimista](perform-conditional-operations-using-web-api.md#bkmk_Applyoptimisticconcurrency).  
  
-   Para controlar si una operación de upsert debe crear o actualizar realmente una entidad, también puede usar los encabezados If-Match e [If-None-Match](https://tools.ietf.org/html/rfc7232#section-3.2). Más información:[Aplicar Upsert a una entidad](update-delete-entities-using-web-api.md#bkmk_upsert).  
  
-   Al ejecutar operaciones por lotes, deberá aplicar distintos encabezados en la solicitud y con cada parte enviada en el cuerpo. Más información:[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)  
  
<a name="bkmk_statusCodes"></a>

## <a name="identify-status-codes"></a>Identificar códigos de estado

 Tanto si la solicitud http es correcta como si no, la respuesta incluirá un código de estado. Los códigos de estado devueltos por la API web de Common Data Service incluyen lo siguiente.  
  
|Código|Descripción|Escriba|  
|----------|-----------------|----------|  
|200 OK|Esto se produce cuando la operación devuelva datos en el cuerpo de la respuesta.|Correcto|  
|201 Creados|Cuente con esto cuando la operación POST de la entidad se realice correctamente y haya especificado la preferencia `return=representation` en su solicitud.|Correcto|  
|204 Sin contenido|Esto se produce cuando la operación sea correcta pero no devuelva datos en el cuerpo de la respuesta.|Correcto|  
|304 Sin modificar|Esto se produce al comprobar si se ha modificado una entidad desde la última vez que se recuperó. Más información:[Recuperaciones condicionales](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged).|Redirección|  
|403 Prohibido|Esto se produce para los siguientes tipos de errores:<br /><br /> -   AccessDenied<br />-   AttributePermissionReadIsMissing<br />-   AttributePermissionUpdateIsMissingDuringUpdate<br />-   AttributePrivilegeCreateIsMissing<br />-   CannotActOnBehalfOfAnotherUser<br />-   CannotAddOrActonBehalfAnotherUserPrivilege<br />-   CrmSecurityError<br />-   InvalidAccessRights<br />-   PrincipalPrivilegeDenied<br />-   PrivilegeCreateIsDisabledForOrganization<br />-   PrivilegeDenied<br />-   unManagedinvalidprincipal<br />-   unManagedinvalidprivilegeedepth|Error de cliente|  
|401 No autorizado|Esto se produce para los siguientes tipos de errores:<br /><br /> -   BadAuthTicket<br />-   ExpiredAuthTicket<br />-   InsufficientAuthTicket<br />-   InvalidAuthTicket<br />-   InvalidUserAuth<br />-   MissingCrmAuthenticationToken<br />-   MissingCrmAuthenticationTokenOrganizationName<br />-   RequestIsNotAuthenticated<br />-   TamperedAuthTicket<br />-   UnauthorizedAccess<br />-   UnManagedInvalidSecurityPrincipal|Error de cliente|  
|413 La carga es demasiado grande|Espero esto cuando la solicitud sea demasiado larga.|Error de cliente|  
|400 BadRequest|Esto se produce cuando un argumento no sea válido.|Error de cliente|  
|404 No encontrado|Esto se produce cuando no exista el recurso.|Error de cliente|  
|405 Método no permitido|Este error se produce porque el método y las combinaciones de recursos no son correctas. Por ejemplo, no puede utilizar DELETE o PATCH en una colección de entidades.<br /><br /> Esto se produce para los siguientes tipos de errores:<br /><br /> -   CannotDeleteDueToAssociation<br />-   InvalidOperation<br />-   NotSupported|Error de cliente|  
|412 Error de condición previa|Esto se produce para los siguientes tipos de errores:<br /><br /> -   ConcurrencyVersionMismatch<br />-   DuplicateRecord|Error de cliente|
|429 Demasiadas solicitudes|Espere esto cuando se superan los límites de la API. Más información: [Límites de API de protección de servicios](../api-limits.md)|Error de cliente|  
|501 No implementado|Esto se produce cuando alguna operación solicitada no se implementa.|Error de servidor|  
|503 Servicio no disponible|Esto se produce cuando el servicio de la API web no está disponible.|Error de servidor|  
  
<a name="bkmk_parseErrors"></a>

## <a name="parse-errors-from-the-response"></a>Errores de análisis de la respuesta

 Los detalles sobre errores se incluyen como JSON en la respuesta. Los errores tendrán este formato.  
  
```json  
{  
 "error":{  
  "code": "<This code is not related to the http status code and is frequently empty>",  
  "message": "<A message describing the error>",  
  "innererror": {  
   "message": "<A message describing the error, this is frequently the same as the outer message>",  
   "type": "Microsoft.Crm.CrmHttpException",  
   "stacktrace": "<Details from the server about where the error occurred>"  
  }  
 }  
}  
```  
  
### <a name="see-also"></a>Vea también  

[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)
