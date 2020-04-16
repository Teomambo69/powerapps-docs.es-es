---
title: Entidades de reglas de duplicados (Common Data Service) | Microsoft Docs
description: Estas entidades contienen datos que definen las reglas de detección de duplicados.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 359c8580b0257fc382958a3ef303abc5c0bb8c59
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156240"
---
# <a name="duplicate-rule-entities"></a>Entidades de reglas de duplicados

Para obtener información sobre cómo configurar reglas de duplicados en la aplicación, vea [Guía del administrador: Configurar reglas de detección de duplicados para mantener limpios los datos](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).

Las reglas de detección de duplicados se definen mediante las entidades siguientes:

- [DuplicateRule](reference/entities/duplicaterule.md): para detectar duplicados en el sistema, cree una *regla de detección de duplicados* para un tipo de entidad específica. Puede crear múltiples reglas de detección para el mismo tipo de entidad. Sin embargo, puede publicar un máximo de cinco reglas de detección de duplicados por tipo de entidad a la vez.  
- [DuplicateRuleCondition](reference/entities/duplicaterulecondition.md): una regla puede tener una o más *condiciones de la regla de detección* de duplicados representadas por la entidad de condición de regla de duplicados. El sistema combina las condiciones como en la operación lógica `AND`. Una regla de detección de duplicados especifica un tipo de entidad base y un tipo de entidad coincidente. Una condición de regla de duplicados especifica el nombre de un atributo base y el nombre de un atributo coincidente. Por ejemplo, especifique una cuenta como la entidad base y un contacto como la entidad coincidente para comparar apellidos y direcciones. Los criterios de coincidencia constan de operadores como coinciden exactamente, primer número n de caracteres o último número n de caracteres. 


Estas dos entidades están relacionadas mediante la relación [DuplicateRule_DuplicateRuleConditions](/reference/entities/duplicaterule.md#BKMK_DuplicateRule_DuplicateRuleConditions).

Trabajos de detección de duplicados contrastando códigos de correspondencia generados de registros existentes con cada nuevo registro creado. Estos códigos de correspondencia se crean con la creación de cada nuevo registro. Por lo tanto, hay posibilidad de que se creen uno o más registros duplicados si se procesan en el mismo momento. Además de detectar duplicados según se crean, debe programar trabajos de detección de duplicados para comprobar si hay otros posibles registros duplicados.
 
 Las reglas de detección de duplicados son para todo el sistema. Debe publicarlas antes de ejecutar un trabajo de detección de duplicados para detectar duplicados de datos en masa o recuperar duplicados de un registro de entidad específico. Para publicar una regla de detección de duplicados, use el mensaje `PublishDuplicateRule` (<xref href="Microsoft.Dynamics.CRM.PublishDuplicateRule?text=PublishDuplicateRule Action" /> o <xref:Microsoft.Crm.Sdk.Messages.PublishDuplicateRuleRequest>). La publicación de reglas de duplicados es una operación asincrónica que se ejecuta en segundo plano.

Los siguientes atributos programables en estas entidades controlan el comportamiento de las reglas de detección de duplicados.

## <a name="duplicaterule"></a>DuplicateRule

|Atributo|Descripción|
|-|-|
|[BaseEntityName](/reference/entities/duplicaterule.md#BKMK_BaseEntityName)| Tipo de registro del registro que se está evaluando en busca de duplicados posibles.|
|[Descripción](/reference/entities/duplicaterule.md#BKMK_Description)|Descripción de la regla de detección de duplicados.|
|[DuplicateRuleId](/reference/entities/duplicaterule.md#BKMK_DuplicateRuleId)|Identificador único de la regla de detección de duplicados.|
|[ExcludeInactiveRecords](/reference/entities/duplicaterule.md#BKMK_ExcludeInactiveRecords)|Determina si se deben marcar los registros inactivos como duplicados.<br /> **Nota**: <br />El valor predeterminado es `false`. Establézcalo en `true` si no desea que los registros inactivos se marquen como duplicados, aunque se cumplan los criterios de la regla de detección de duplicados. <br /> Más información: [Estados inactivos](#inactive-states)|
|[IsCaseSensitive](/reference/entities/duplicaterule.md#BKMK_IsCaseSensitive)|Indica si el operador distingue mayúsculas de minúsculas.|
|[MatchingEntityName](/reference/entities/duplicaterule.md#BKMK_MatchingEntityName)|Tipo de registro de los registros que se están evaluando como duplicados posibles.|
|[Nombre](/reference/entities/duplicaterule.md#BKMK_Name)|Nombre de la regla de detección de duplicados.|
|[OwnerId](/reference/entities/duplicaterule.md#BKMK_OwnerId)|Identificador único del usuario o equipo propietario de la regla de detección de duplicados.|
|[OwnerIdType](/reference/entities/duplicaterule.md#BKMK_OwnerIdType)|Si el propietario es un usuario o un equipo.|
|[Código de estado](/reference/entities/duplicaterule.md#BKMK_StatusCode)|Razón para el estado de la regla de detección de duplicados.|

### <a name="inactive-states"></a>Estados inactivos

La mayoría de las entidades del sistema y todas las entidades personalizadas tienen dos opciones del atributo `StateCode`:

- `Value`: 0 `InvariantName`: `Active`
- `Value`: 1 `InvariantName`: `Inactive`

Puede cambiar la etiqueta de la opción, pero el valor de `InvariantName` no.

Algunas entidades del sistema tendrán más de un estado activo o inactivo. La tabla siguiente muestra algunos ejemplos de entidades con más de un estado activo o inactivo.

|Entidad StateCode |Estado(s) activo(s)|Estado(s) inactivo(s)|  
|--|--|--|  
|[Appointment.StateCode](/reference/entities/appointment.md#BKMK_StateCode)|`Open`, `Scheduled`|`Completed`, `Canceled`|  
|[CampaignActivity.StateCode](/reference/entities/CampaignActivity.md#BKMK_StateCode)|`Open`|`Closed`, `Canceled`|  
|[CampaignResponse.StateCode](/reference/entities/CampaignResponse.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Contract.StateCode](/reference/entities/Contract.md#BKMK_StateCode)|`Draft`, `Invoiced`, `On Hold`|`Canceled`, `Expired`|  
|[ContractDetail.StateCode](/reference/entities/ContractDetail.md#BKMK_StateCode)|`Existing`, `Renewed`|`Canceled`, `Expired`|  
|[Email.StateCode](/reference/entities/Email.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Fax.StateCode](/reference/entities/Fax.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Incident.StateCode](/reference/entities/Incident.md#BKMK_StateCode)|`Active`|`Resolved`, `Canceled`, `Closed`|  
|[Invoice.StateCode](/reference/entities/Invoice.md#BKMK_StateCode)|`Active`|`Closed`, `Paid`, `Canceled`|  
|[KbArticle.StateCode](/reference/entities/KbArticle.md#BKMK_StateCode)|`Draft`, `Unapproved`, `Published`|N/D|  
|[Lead.StateCode](/reference/entities/Lead.md#BKMK_StateCode)|`Open`|`Qualified`, `Disqualified`|  
|[Letter.StateCode](/reference/entities/Letter.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Opportunity.StateCode](/reference/entities/Opportunity.md#BKMK_StateCode)|`Open`|`Won`, `Lost`|  
|[PhoneCall.StateCode](/reference/entities/PhoneCall.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Quote.StateCode](/reference/entities/Quote.md#BKMK_StateCode)|`Draft`, `Active`|`Won`, `Closed`|  
|[SalesOrder.StateCode](/reference/entities/SalesOrder.md#BKMK_StateCode)|`Active`, `Submitted`, `Invoiced`|`Canceled`, `Fulfilled`|  
|[ServiceAppointment.StateCode](/reference/entities/ServiceAppointment.md#BKMK_StateCode)|`Open`, `Scheduled`|`Closed`, `Canceled`|  
|[Task.StateCode](/reference/entities/Task.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  

 Por ejemplo, si establece el atributo `ExcludeInactiveRecords` en `true`, solo los pedidos de venta `Active`, `Submitted` y `Invoiced` se tendrán en cuenta para la búsqueda de coincidencias durante la detección de duplicados. 


> [!NOTE]
> Puede revisar las opciones de `StateCode` disponibles para una entidad con el Explorador de metadatos que se describe en [Examinar los metadatos de la organización](browse-your-metadata.md).
>
> Para recuperar las opciones de `StateCode` para una entidad puede usar la siguiente consulta a la API web mediante la sustitución del `LogicalName` de la entidad por la `appointment` utilizada a continuación:
> ```HTTP
> GET [organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='appointment')/Attributes(LogicalName='statecode')/Microsoft.Dynamics.CRM.StateAttributeMetadata/OptionSet?$select=Options
> ```

## <a name="duplicaterule-special-messages"></a>Mensajes especiales de DuplicateRule

[DuplicateRule](/reference/entities/duplicaterule.md) es una entidad propiedad del usuario y permite ejecutar las operaciones normales para crear, recuperar, actualizar, asignar y eliminar, así como las operaciones para controlar el acceso. Más información: [Mensajes de DuplicateRule](/reference//reference/entities/duplicaterule.md#messages).

También puede usar los siguientes mensajes especiales:

|Mensaje|Operación de la API web|Ensamblado del SDK|
|-|-|-|
|CompoundUpdateDuplicateDetectionRule|<xref href="Microsoft.Dynamics.CRM.CompoundUpdateDuplicateDetectionRule?text=CompoundUpdateDuplicateDetectionRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.CompoundUpdateDuplicateDetectionRuleRequest>|
|PublishDuplicateRule|<xref href="Microsoft.Dynamics.CRM.PublishDuplicateRule?text=PublishDuplicateRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.PublishDuplicateRuleRequest>|
|PublishXml|<xref href="Microsoft.Dynamics.CRM.PublishXml?text=PublishXml Action" />|<xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>|
|UnpublishDuplicateRule|<xref href="Microsoft.Dynamics.CRM.UnpublishDuplicateRule?text=UnpublishDuplicateRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.UnpublishDuplicateRuleRequest>|


## <a name="duplicaterulecondition"></a>DuplicateRuleCondition

|Atributo|Descripción|
|-|-|
|[BaseAttributeName](/reference/entities/duplicaterulecondition.md#BKMK_BaseAttributeName)|Campo que se está comparando.|
|[DuplicateRuleConditionId](/reference/entities/duplicaterulecondition.md#BKMK_DuplicateRuleConditionId)|Identificador único de la condición.|
|[IgnoreBlankValues](/reference/entities/duplicaterulecondition.md#BKMK_IgnoreBlankValues)|Determina si los valores en blanco se deben considerar como valores no duplicados. <br /> **Nota**: <br />El valor predeterminado de este atributo es `false`. Debe establecerlo en `true` si no desea que la regla de detección de duplicados considere los valores `null` como iguales. <br /> **Importante**: <br /> Para una regla de detección de duplicados con una condición, si establece el valor del atributo en `false`, el sistema lo trata como un valor `true`. |
|[MatchingAttributeName](/reference/entities/duplicaterulecondition.md#BKMK_MatchingAttributeName)|Campo que se está comparando con el campo base.|
|[OperatorCode](/reference/entities/duplicaterulecondition.md#BKMK_OperatorCode)|Operador para esta condición de regla.<br /> **Importante**: <br />Si establece el atributo `OperatorCode` en `ExactMatch`, no establezca ningún valor para el atributo `OperatorParam`|
|[OperatorParam](/reference/entities/duplicaterulecondition.md#BKMK_OperatorParam)|Valor del parámetro de N si el operador es Mismos caracteres iniciales o Mismos caracteres finales.<br /> **Importante**: <br />No puede establecer `OperatorParam` en cero durante las operaciones de creación o actualización.|
|[RegardingObjectId](/reference/entities/duplicaterulecondition.md#BKMK_RegardingObjectId)|Identificador único del objeto al que está asociada la condición.|

## <a name="duplicaterulecondition-special-messages"></a>Mensajes especiales de DuplicateRuleCondition

[DuplicateRuleCondition](/reference/entities/duplicaterulecondition.md) es una entidad secundaria a `DuplicateRule`. El acceso para recuperar o modificar estas entidades depende del acceso a la `DuplicateRule` con la que están asociadas. Más información: [Mensajes de DuplicateRuleCondition](/reference/entities/duplicaterulecondition.md#messages).

También puede usar los siguientes mensajes especiales:

|Mensaje|Operación de la API web|Ensamblado del SDK|
|-|-|-|
|CompoundUpdateDuplicateDetectionRule|<xref href="Microsoft.Dynamics.CRM.CompoundUpdateDuplicateDetectionRule?text=CompoundUpdateDuplicateDetectionRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.CompoundUpdateDuplicateDetectionRuleRequest>|


### <a name="see-also"></a>Vea también
<xref href="Microsoft.Dynamics.CRM.duplicaterule?text=duplicaterule EntityType" /><br/><xref href="Microsoft.Dynamics.CRM.duplicaterulecondition?text=duplicaterulecondition EntityType" /><br/><a href="detect-duplicate-data-with-code.md" data-raw-source="[Detect duplicate data](detect-duplicate-data-with-code.md)">Detectar datos duplicados</a><br />
<a href="enable-disable-duplicate-detection.md" data-raw-source="[Enable and disable duplicate detection](enable-disable-duplicate-detection.md)">Habilitar y deshabilitar la detección de duplicados</a><br />
<a href="run-duplicate-detection.md" data-raw-source="[Run duplicate detection](run-duplicate-detection.md)">Ejecutar detección de duplicados</a><br />
<a href="duplicate-detection-messages.md" data-raw-source="[Duplicate detection messages](duplicate-detection-messages.md)">Mensajes de detección de duplicados</a><br />
<a href="org-service/samples/enable-duplicate-detection-and-retrieve-duplicates.md" data-raw-source="[Sample: Enable duplicate detection and retrieve duplicates](org-service/samples/enable-duplicate-detection-and-retrieve-duplicates.md)">Ejemplo: habilitar la detección de duplicados y recuperar los duplicados</a><br />
<a href="org-service/samples/use-duplicate-detection-when-creating-and-updating-records.md" data-raw-source="[Sample: Use duplicate detection when creating and updating records](org-service/samples/use-duplicate-detection-when-creating-and-updating-records.md)">Ejemplo: Uso de detección de duplicados para crear y actualizar registros</a><br />
<a href="/dynamics365/customer-engagement/developer/org-service/sample-detect-multiple-duplicate-records" data-raw-source="[Sample: Detect multiple duplicate records](org-service/samples/detect-multiple-duplicate-records.md)">Ejemplo: detectar varios registros duplicados</a><br />