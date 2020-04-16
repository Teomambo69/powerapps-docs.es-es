---
title: Definir las reglas de visualización de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: 'Obtenga información sobre cómo definir las reglas específicas a supervisar cuando se muestran los elementos de la cinta de opciones al configurar los elementos de la cinta de opciones. '
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 70e5687f-4d0e-3d43-03f3-10e5aa5b0713
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 190659fb75b6cb6e89b1952178ff4eb0301f47b7
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115660"
---
# <a name="define-ribbon-display-rules"></a>Defina las reglas de la visualización de la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-display-rules -->

Al configurar los elementos de la cinta de opciones se pueden definir las reglas específicas para supervisar cuándo se mostrarán los elementos de la cinta de opciones.  

-   Use el elemento /`RuleDefinitions`/DisplayRules/`<DisplayRule>` para definir las reglas que controlan cuándo debe mostrarse el elemento de la cinta de opciones.  

-   Use el elemento /CommandDefinitions/`CommandDefinition`/DisplayRules/`<DisplayRule>` para asociar reglas de visualización específicas a una definición de comando.  

## <a name="control-when-ribbon-elements-are-displayed"></a>Controlar cuándo se muestran los elementos de la cinta de opciones  
 Al definir las reglas de visualización en las definiciones de reglas, se puede usar la misma regla de visualización para muchas definiciones de comando. Cuando más de una regla de visualización está definida para una definición de comando, todas las reglas de visualización deben evaluarse como true para que se muestre el elemento de la cinta de opciones.  

 Todas las reglas de visualización proporcionan un atributo opcional para especificar si el valor predeterminado de la regla es true o false, y un atributo `InvertResult` opcional para habilitar la devolución de un resultado negativo cuando el elemento que se está probando devuelve true.  

 El elemento `/RuleDefinitions/DisplayRules/DisplayRule` admite los siguientes tipos de reglas:  

 `<CommandClientTypeRule>`  
[!INCLUDE[ribbon_element_CommandClientTypeRule](../../includes/ribbon-element-commandclienttyperule.md)]

 Los valores `Type` corresponden a lo siguiente:  


|   Value   |                                                                               Presentación                                                                               |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Modern`  |                                       La barra de comandos se muestra mediante Microsoft Dynamics 365 for tablets.                                       |
| `Refresh` |                                                      La barra de comandos se muestra mediante la interfaz de usuario actualizada.                                                      |
| `Legacy`  | La cinta de opciones se muestra en los formularios de entidades que no se actualizaron o en una vista de lista en Dynamics 365 for Outlook. |

 `<CrmClientTypeRule>`  
 Permite la definición de reglas según el tipo de cliente usado. Las opciones de `Type` son las siguientes:  

- Web  

- Outlook  

  `<CrmOfflineAccessStateRule>`  
  Use este criterio para mostrar un elemento de la cinta de opciones en función de si Dynamics 365 for Microsoft Office Outlook con acceso sin conexión está actualmente sin conexión.  

  `<CrmOutlookClientTypeRule>`  
  Use esta regla si desea mostrar un botón para el tipo específico de Dynamics 365 for Outlook. Las opciones de `Type` son las siguientes:  

- CrmForOutlook  

- CrmForOutlookOfflineAccess  

  `<CrmOutlookClientVersionRule>`  
  [!INCLUDE[ribbon_element_CrmOutlookClientVersionRule](../../includes/ribbon-element-crmoutlookclientversionrule.md)]

  Los valores válidos son:  

- 2003  

- 2007  

- 2010  

  `<EntityPrivilegeRule>`  
  Use este tipo de regla para mostrar elementos de la cinta de opciones cuando un usuario tiene privilegios específicos de una entidad. Debe especificar el nivel de privilegio y el privilegio específico que desea comprobar.  

  `<EntityPropertyRule>`  
  Permite la definición de reglas según los valores booleanos de las propiedades de entidad específicas. Las opciones de `PropertyName` son las siguientes:  

- DuplicateDetectionEnabled  

- GridFiltersEnabled  

- HasStateCode  

- IsConnectionsEnabled  

- MailMergeEnabled  

- WorksWithQueue  

- HasActivities  

- IsActivity  

- HasNotes  

  `<EntityRule>`  
  Las reglas de la entidad permiten la evaluación de la entidad actual. Esto resulta útil al definir acciones personalizadas que se aplican a la plantilla de la entidad en lugar de a las entidades específicas. Por ejemplo, es posible que desee agregar un elemento de la cinta de opciones en todas las entidades excepto en algunas entidades específicas. Es más fácil definir la acción personalizada de la plantilla de la entidad que se aplica a todas las entidades y después usar una regla de la entidad para filtrar aquellas que se deben excluir.  

  Las reglas de la entidad también incluyen un atributo de contexto opcional para especificar si se muestra la entidad en el formulario o en una lista (HomePageGrid). El atributo opcional `AppliesTo` se puede establecer en `PrimaryEntity` o en `SelectedEntity` para distinguir si se muestra la entidad en una subcuadrícula.  

  `<FormEntityContextRule>`  
  [!INCLUDE[ribbon_element_FormEntityContextRule](../../includes/ribbon-element-formentitycontextrule.md)]

  `<FormStateRule`  
  Use la regla de estado de formulario para determinar el tipo actual de formulario que se muestra en un registro. Las opciones de `State` son las siguientes:  

- Crear  

- Existente  

- Solo lectura  

- Deshabilitada  

- BulkEdit  

  `<FormTypeRule>`  
  [!INCLUDE[ribbon_element_FormTypeRule](../../includes/ribbon-element-formtyperule.md)]

  Los valores `Type` corresponden a lo siguiente:  

|Value|Presentación|  
|-----------|------------------|  
|`Main`|Un formulario de entidad que se muestra en la aplicación.|  
|`Preview`|El formulario de vista previa de una entidad mostrada como elemento de expansión en la cuadrícula.|  
|`AppointmentBook`|Se usa con la cita, el equipamiento, serviceappointment y las entidades de systemuser para la interfaz de usuario Programación de servicios.|  
|`Dashboard`|El formulario define un panel.|  
|`Quick`|Formulario de vista rápida.|  
|`QuickCreate`|Formulario de creación rápida.|  

 `<HideForTabletExperienceRule>`  
 [!INCLUDE[ribbon_element_HideForTabletExperienceRule](../../includes/ribbon-element-hidefortabletexperiencerule.md)]

 `<MiscellaneousPrivilegeRule>`  
 Use este tipo de regla para comprobar los privilegios que no se aplican a una entidad específica, como ExportToExcel, MailMerge o GoOffline.  

 `<OrganizationSettingRule>`  
 Use esta opción para mostrar un elemento de la cinta de opciones solo si la configuración específica de la organización está habilitada. Las opciones de configuración son las siguientes:  

- IsSharepointEnabled  

- IsSOPIntegrationEnabled  

- IsFiscalCalendarDefined  

  `<OrRule>`Esta regla le permite reemplazar el valor de comparación predeterminado AND para varios tipos de reglas de visualización. Use el elemento `OrRule` para definir varias combinaciones posibles válidas para comprobar.  

  `<OutlookRenderTypeRule>`  
  Use esta opción para mostrar un elemento de la cinta de opciones si la cinta se muestra en [!INCLUDE[pn_MS_Outlook_Short](../../includes/pn-ms-outlook-short.md)] de forma específica. Las opciones de `Type` son las siguientes:  

- Web  

- Outlook  

  `<OutlookVersionRule>`  
  Use esto para mostrar un elemento de la cinta de opciones de una versión determinada de Outlook. Las opciones de `Version` son las siguientes:  

- 2003  

- 2007  

- 2010  

  `<PageRule>`  
  Este tipo de regla compruebe la dirección URL de la página que se muestra. Devuelve true si coincide la dirección.  

  `<RelationshipTypeRule>` Este tipo de regla se aplica a los registros seleccionados en una cuadrícula. Le permite determinar el tipo de relación, de la siguiente manera:  

- OneToMany  

- ManyToMany  

- NoRelationship  

  `<SkuRule>`  
  Use este tipo de regla para mostrar un elemento de la cinta de opciones para una versión de SKU determinada de Common Data Service, de la siguiente manera:  

- OnPremise  

- Online  

- Spla  

  `<ValueRule>`  
  Use esta regla para comprobar el valor de un campo específico en el registro que se muestra en el formulario.  

> [!NOTE]
>  Para los comandos definidos para la subcuadrícula en formularios con la experiencia de usuario actualizada, no se pueden usar las reglas de valor dentro de reglas de visualización. Use este elemento en un `<EnableRule>` para ocultar un elemento.  

### <a name="see-also"></a>Vea también  
 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Definir reglas de habilitación de la cinta de opciones](define-ribbon-enable-rules.md)   
 [Definir las acciones de la cinta de opciones](define-ribbon-actions.md)
