---
title: Editar una entidad en PowerApps | MicrosoftDocs
description: Obtenga información sobre las formas diferentes en que se puede editar una entidad
ms.custom: ''
ms.date: 05/15/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 8b00780c-74f0-4e3a-b570-b9289d0d5383
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="edit-an-entity"></a>Editar una entidad

Puede modificar cualquier entidad personalizada que cree. Las entidades estándar o las entidades personalizadas administradas pueden tener limitaciones sobre los cambios que puede realizar.  
  
> [!NOTE]
> Las entidades**estándar** son entidades comunes que se incluyen con el entorno y que no son entidades del **Sistema** o **Personalizadas**. Las *entidades personalizadas administradas* son entidades que se han agregado al sistema importando una solución administrada. El grado con que puede modificar estas entidades depende de las propiedades administradas establecidas para cada entidad. Las propiedades que no puede modificar estarán deshabilitadas. 

Hay dos formas de editar una entidad mediante un diseñador:

|Diseñador|Descripción|
|--|--|
|[Portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes.|

En el portal de PowerApps y en el explorador de soluciones puede realizar lo siguiente:

- **Editar campos de la entidad**. Más información: [Crear y editar campos para Common Data Service](create-edit-fields.md)
  
- **Editar relaciones entre entidades**. Más información: [Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)

- **Claves**. [Definir claves alternativas para hacer referencia a registros](define-alternate-keys-reference-records.md)
  
También puede realizar cambios en los registros que admiten la entidad:  

- **Reglas de negocio**. Más información: [Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

- **Vistas**. Más información: [Crear o editar una vista](../model-driven-apps/create-edit-views.md)
  
- **Formularios**. Más información: [Crear y diseñar formularios](../model-driven-apps/create-design-forms.md)

- **Paneles**. Más información: [Crear o editar paneles](../model-driven-apps/create-edit-dashboards.md)

- **Gráficos**. [Creación o edición de un gráfico del sistema](../model-driven-apps/create-edit-system-chart.md)

## <a name="edit-using-powerapps-portal-designer"></a>Editar usando el diseñador del portal de PowerApps

En el diseñador del portal de PowerApps solo hay tres propiedades de la entidad que se pueden editar:
 - Nombre para mostrar
 - Nombre para mostrar plural
 - Descripción

En el diseñador, seleccione la entidad que desea editar y haga clic en ella para abrir el diseñador de entidades. Para modificar las propiedades de la entidad, haga clic en el comando **Configuración** para ver el formulario **Editar entidad** como se muestra a continuación:

![Editar propiedades de entidad](media/edit-entity-properties-powerapps-portal-designer.png)

> [!NOTE]
>  El nombre de muchas entidades estándar también se puede usar en otro texto de la aplicación. Para buscar y cambiar el texto donde se ha usado este nombre, consulte [Editar mensajes de entidades estándar](edit-system-entity-messages.md)

Para cualquier otro cambio en las opciones de entidades, debe editar la entidad usando el explorador de soluciones.

## <a name="edit-using-solution-explorer"></a>Editar usando el explorador de soluciones

Al editar una entidad usando el explorador de soluciones, necesita buscar la solución no administrada a la que desea agregarla.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
<a name="BKMK_ChangeEntityName"></a> 
  
## <a name="change-the-name-of-an-entity"></a>Cambiar el nombre de una entidad  

Use las propiedades **Nombre para mostrar** y **Nombre en plural** para cambiar el nombre de la entidad de la aplicación. 

> [!NOTE]
>  El nombre de muchas entidades estándar también se puede usar en otro texto de la aplicación. Para buscar y cambiar el texto donde se ha usado este nombre, consulte [Editar mensajes de entidades estándar](edit-system-entity-messages.md)
  
<a name="BKMK_ChangeEntityIcon"></a>   

###  <a name="change-the-icons-used-for-custom-entities"></a>Cambiar los iconos usados para entidades personalizadas  

De forma predeterminada, todas las entidades personalizadas en la aplicación web tienen los mismos iconos. Puede crear recursos web de imagen para los iconos que desea para las entidades personalizadas. Más información:  [Cambiar iconos para entidades personalizadas](../model-driven-apps/change-custom-entity-icons.md).  
  
<a name="BKMK_EnableOptions"></a>  
 
###  <a name="entity-options-that-can-only-be-enabled"></a>Opciones de la entidad que solo pueden estar habilitadas  

La siguiente tabla enumera las opciones que puede habilitar para una entidad, pero después de habilitar estos elementos, estos no se pueden deshabilitar:  

[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)] 
  
<a name="BKMK_EnableDisableOptions"></a>  
 
###  <a name="enable-or-disable-entity-options"></a>Habilitar o deshabilitar las opciones de la entidad  

La siguiente tabla enumera las opciones de la entidad que puede habilitar o deshabilitar en cualquier momento.  

[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)] 

### <a name="see-also"></a>Vea también

[Crear una entidad](create-edit-entities.md)<br />
[Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)
