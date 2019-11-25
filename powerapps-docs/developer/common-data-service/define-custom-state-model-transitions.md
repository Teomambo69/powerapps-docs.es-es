---
title: Definir transiciones de modelo de estado personalizadas (Common Data Service) | Microsoft Docs
description: Obtenga más información sobre la definición de las transiciones de modelos de estado personalizados para la entidad Incidente (caso) o entidades personalizadas.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: a7172755f75a2d39ff1ad2b0bf7dcbfb88bdf72d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752992"
---
# <a name="define-custom-state-model-transitions"></a>Definir transiciones de modelo de estado personalizadas

Puede especificar transiciones de estado personalizadas para la entidad `Incident` (**Caso**) o entidades personalizadas. La propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsStateModelAware> es `true` para entidades que soportan transiciones de modelo de estado.  
  
 Las transiciones de estado personalizadas son un nivel opcional de filtración para definir qué transiciones de estado son válidas para un registro en un estado determinado. En particular, cuando dispone de un amplio número de combinaciones para estados válidos y valores de estado, definir una lista limitada de opciones puede facilitar a los usuarios la selección del estado correcto de un registro.  

<a name="BKMK_StateModel"></a>
   
## <a name="what-is-the-state-model"></a>¿Cuál es el modelo de estado?  
 Las entidades que admiten el concepto de estado tienen un par de atributos que capturan estos datos, tal y como se muestra en esta tabla.  
  
|Nombre lógico|Nombre para mostrar|Descripción|  
|------------------|------------------|-----------------|  
|`statecode`|**Estado**|Representa el estado del registro. Para las entidades personalizadas este es **Activo** o **Inactivo**. La entidad Incident (case) utiliza **Activo**, **Resuelto** y **Cancelado**. No puede agregar más opciones de estado, pero puede cambiar las etiquetas de opciones.|  
|`statuscode`|**Razón para el estado**|Representa un estado que está vinculado a un estado específico. Cada estado debe tener al menos un estado posible. Puede agregar opciones adicionales de estado y cambiar las etiquetas de las opciones existentes.|  
  
 Los metadatos de los atributos definen qué valores de estado son válidos para un estado determinado. Por ejemplo, para la entidad `Incident` (**Caso**), se muestran las opciones de estado y de estado predeterminado en la tabla siguiente.  
  
|Est.|Estado|  
|-----------|------------|  
|`Label`: **Activo**<br /><br /> `Value`: 0|`Label`: **En curso**<br /><br /> `Value`: 1<br /><br /> `State`: 0|  
|`Label`: **Activo**<br /><br /> `Value`: 0|`Label`: **En espera**<br /><br /> `Value`: 2<br /><br /> `State`: 0|  
|`Label`: **Activo**<br /><br /> `Value`: 0|`Label`: **Esperando detalles**<br /><br /> `Value`: 3<br /><br /> `State`: 0|  
|`Label`: **Activo**<br /><br /> `Value`: 0|Etiqueta: **Investigación**<br /><br /> `Value`: 4<br /><br /> `State`: 0|  
|`Label`: **Resuelto**<br /><br /> `Value`: 1|`Label`: **Problema resuelto**<br /><br /> `Value`: 5<br /><br /> `State`: 1|  
|`Label`: **Resuelto**<br /><br /> `Value`: 1|Etiqueta: **Información proporcionada**<br /><br /> `Value`: 1000<br /><br /> `State`: 1|  
|Etiqueta: **Cancelado**<br /><br /> `Value`: 2|`Label`: **Cancelado**<br /><br /> `Value`: 6<br /><br /> `State`: 2|  
|Etiqueta: **Cancelado**<br /><br /> `Value`: 2|`Label`: **Combinado**<br /><br /> `Value`: 2000<br /><br /> `State`: 2|  
  
 Estos datos se almacenan en la clase <xref:Microsoft.Xrm.Sdk.Metadata.StatusOptionMetadata>, que representa las opciones de la clase <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata>.  
  
Para ver los metadatos de las entidades de su organización, instale la solución Explorador de metadatos que se describe en [Exploración de los metadatos de su organización](browse-your-metadata.md). También puede examinar la documentación de referencia para las entidades en la [Referencia de entidad](/reference/about-entity-reference.md).
  
<a name="BKMK_DetectValidStatusTransitions"></a>   

## <a name="detect-valid-status-transitions"></a>Detectar transiciones de estado válidas  
 Puede modificar el atributo `statuscode` para definir qué otras opciones de estado representan transiciones válidas a partir del estado actual. Para obtener instrucciones, consulte el tema del Manual de personalización: [Definir las transiciones de razón para el estado](https://go.microsoft.com/fwlink/p/?LinkId=393657)  
  
 Cuando se apliquen transacciones de estado personalizadas a una entidad, la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.EnforceStateTransitions> la propiedad será `true`. Además, cada<xref:Microsoft.Xrm.Sdk.Metadata.StatusOptionMetadata> uno en el<xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata.Options> la colección tendrá una nueva<xref:Microsoft.Xrm.Sdk.Metadata.StatusOptionMetadata.TransitionData> propiedad. Esta propiedad contendrá un valor de cadena que representa un documento XML. Este documento contiene la definición de las transiciones permitidas. Por ejemplo, la opción predeterminada del atributo `Incident` (**Caso**) `StatusCode` puede presentar el valor `TransitionData` siguiente.  
  
```xml  
<allowedtransitions xmlns="https://schemas.microsoft.com/crm/2009/WebServices">  
<allowedtransition sourcestatusid="1" tostatusid="6" />  
<allowedtransition sourcestatusid="1" tostatusid="1000" />   
<allowedtransition sourcestatusid="1" tostatusid="2000" />  
<allowedtransition sourcestatusid="1" tostatusid="5" />  
</allowedtransitions>  
```  
  
> [!NOTE]
>  Cuando se recuperan estos datos en código no administrado del servicio web, por ejemplo, cuando se utiliza JavaScript, se omitirá y aparecerá como el siguiente ejemplo.  
  
```xml  
<allowedtransitions xmlns="https://schemas.microsoft.com/crm/2009/WebServices">  
<allowedtransition sourcestatusid="1" tostatusid="6">  
<allowedtransition sourcestatusid="1" tostatusid="1000">  
<allowedtransition sourcestatusid="1" tostatusid="2000">  
<allowedtransition sourcestatusid="1" tostatusid="5">  
</allowedtransitions>  
```  
  
 Cuando estos datos están presentes y la propiedad `EnforceStateTransitions` de la entidad es `true`, las instancias de incidentes solamente pueden cambiarse a uno de los valores de `statuscode` permitidos. Puede usar<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> para ajustar `statuscode`<xref:Microsoft.Xrm.Sdk.OptionSetValue> a cualquiera de los valores permitidos que no representan un cambio en el estado. Para cambiar el estado, use <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest> ajustando los valores de las propiedades <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest.State> y <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest.Status> o la propiedad <xref:Microsoft.Crm.Sdk.Messages.CloseIncidentRequest.Status> del ajuste <xref:Microsoft.Crm.Sdk.Messages.CloseIncidentRequest> en uno de los valores permitidos para el valor de `statuscode` actual. El intentar establecer un valor no válido genera un error.  
  
### <a name="see-also"></a>Vea también  
 [Ejemplo: recuperar transiciones de estado válidas](org-service/samples/retrieve-valid-status-transitions.md)   
 [Estado y razón para el estado de los registros](/dynamics365/customer-engagement/developer/introduction-entities#bkmk_RecordStateandStatus)   
 [Recuperar y detectar cambios en metadatos](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata)   
 [Definir transiciones de razón para el estado](https://go.microsoft.com/fwlink/p/?LinkId=393657)
