---
title: formContext.ui (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Aprenda a trabajar con procesos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f93e0e21-f911-4681-81b0-82ccf98ee28b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextui-client-api-reference"></a>formContext.ui (referencia de la API de cliente)



Proporciona propiedades y métodos para recuperar información acerca de la interfaz de usuario (IU), así como recopilaciones para varios subcomponentes del formulario.

![Modelo de objetos de la IU de formContext](../../media/ClientAPI-formContext-ui-Model.png)

## <a name="properties"></a>Propiedades

|Nombre|Descripción|
|--|--|
|Controles|Recopilación de todos los controles de la página. Vea [Recopilaciones](collections.md) para obtener información sobre las recopilaciones y los [Controles](controls.md) para obtener información sobre los objetos de control en la recopilación.|
|formSelector|Use el método formSelector.getCurrentItem para obtener información sobre el formulario en uso actualmente. Utilice la colección formSelector.items para obtener información sobre todos los formularios disponibles para el usuario. **formSelector** no está disponible para Microsoft Dynamics 365 para tabletas.|
|navegación|Una colección de todos los elementos de navegación de la página. Vea [Recopilaciones](collections.md) para obtener información sobre los métodos de recopilación y el [elemento formContext.ui.navigation](formContext-ui-navigation.md) para obtener información sobre los elementos de la recopilación. **navigation** no está disponible para Microsoft Dynamics 365 para tabletas.|
|proceso|Proporciona objetos y métodos para interactuar con el control del flujo de proceso de negocio en un formulario.<br/>Más información: [formContext.ui.process](formContext-ui-process.md)|
|quickForms|Una recopilación de todos los controles de vista rápida de un formulario que utilizan el nuevo motor de representación de formularios (también denominado "formularios turbo").<br/>Más información: [quickForms de formContext.ui](formContext-ui-quickforms.md)|
|tabs|Una colección de todas las pestañas de la página.<br/>Vea [Recopilaciones](collections.md) para obtener información sobre los métodos de recopilación y la [pestaña formContext.ui](formContext-ui-tabs.md) para obtener información sobre los elementos de la recopilación.|


## <a name="methods"></a>Métodos 

|Nombre|Descripción|
|--|--|
|[addOnLoad](formContext-ui/addOnload.md)|[!INCLUDE[formContext-ui/includes/addOnLoad-description.md](formContext-ui/includes/addOnLoad-description.md)]|
|[clearFormNotification](formContext-ui/clearFormNotification.md)|[!INCLUDE[formContext-ui/includes/clearFormNotification-description.md](formContext-ui/includes/clearFormNotification-description.md)]|
|[cerrar](formContext-ui/close.md)|[!INCLUDE[formContext-ui/includes/close-description.md](formContext-ui/includes/close-description.md)]|
|[getFormType](formContext-ui/getFormType.md)|[!INCLUDE[formContext-ui/includes/getFormType-description.md](formContext-ui/includes/getFormType-description.md)]|
|[getViewPortHeight](formContext-ui/getViewPortHeight.md)|[!INCLUDE[formContext-ui/includes/getViewPortHeight-description.md](formContext-ui/includes/getViewPortHeight-description.md)]|
|[getViewPortWidth](formContext-ui/getViewPortWidth.md)|[!INCLUDE[formContext-ui/includes/getViewPortWidth-description.md](formContext-ui/includes/getViewPortWidth-description.md)]|
|[refreshRibbon](formContext-ui/refreshRibbon.md)|[!INCLUDE[formContext-ui/includes/refreshRibbon-description.md](formContext-ui/includes/refreshRibbon-description.md)]|
|[removeOnLoad](formContext-ui/removeOnLoad.md)|[!INCLUDE[formContext-ui/includes/removeOnLoad-description.md](formContext-ui/includes/removeOnLoad-description.md)]|
|[setFormEntityName](formContext-ui/setFormEntityName.md)|[!INCLUDE[formContext-ui/includes/setFormEntityName-description.md](formContext-ui/includes/setFormEntityName-description.md)]|
|[setFormNotification](formContext-ui/setFormNotification.md)|[!INCLUDE[formContext-ui/includes/setFormNotification-description.md](formContext-ui/includes/setFormNotification-description.md)]|



### <a name="related-topics"></a>Temas relacionados

[formContext](../clientapi-form-context.md)




