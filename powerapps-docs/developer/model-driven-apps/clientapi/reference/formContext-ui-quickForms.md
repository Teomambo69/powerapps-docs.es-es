---
title: formContext.ui.quickForms (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Aprenda a trabajar con procesos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a04043de-3497-433a-ae73-4101806dd931
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuiquickforms-client-api-reference"></a>formContext.ui.quickForms (referencia de la API de cliente)



Proporciona métodos para obtener acceso a todos los controles de vista rápida y sus controles constituyentes en los formularios de aplicaciones basadas en modelos cuando se usa el nuevo motor de representación de formularios (también denominados "formularios turbo"). Un control de vista rápida es un formulario de vista rápida agregado a un formulario principal en aplicaciones basadas en modelos que le permite ver información sobre un registro de entidad relacionado en el formulario principal. Los datos de los controles constituyentes de un control de vista rápida no se pueden editar.

La recopilación **quickForms** proporciona acceso a todos los controles de vista rápida de un formulario y admite todos los métodos estándares de las recopilaciones. Consulte [Recopilaciones](collections.md)) para obtener información sobre los métodos de recopilación. 

Puede recuperar un control de vista rápida en la colección **quickForms** mediante el método [get](collections/get.md) especificando el valor de índice (entero) o el nombre (cadena) del control de vista rápida como argumento:

`quickViewControl = formContext.ui.quickForms.get(arg)`


## <a name="quick-form-control-methods"></a>Métodos de control de formulario rápido

|Nombre|Descripción|
|--|--|
|[getControl](formcontext-ui-quickForms/getControlType.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getControl-description.md](formcontext-ui-quickForms/includes/getControl-description.md)]|
|[getControlType](formcontext-ui-quickForms/getControlType.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getControlType-description.md](formcontext-ui-quickForms/includes/getControlType-description.md)]|
|[getDisabled](formcontext-ui-quickForms/getDisabled.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getDisabled-description.md](formcontext-ui-quickForms/includes/getDisabled-description.md)]|
|[getLabel](formcontext-ui-quickForms/getLabel.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getLabel-description.md](formcontext-ui-quickForms/includes/getLabel-description.md)]|
|[getName](formcontext-ui-quickForms/getName.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getName-description.md](formcontext-ui-quickForms/includes/getName-description.md)]|
|[getParent](formcontext-ui-quickForms/getParent.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getParent-description.md](formcontext-ui-quickForms/includes/getParent-description.md)]|
|[getVisible](formcontext-ui-quickForms/getVisible.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getVisible-description.md](formcontext-ui-quickForms/includes/getVisible-description.md)]|
|[isLoaded](formcontext-ui-quickForms/isLoaded.md)|[!INCLUDE[formcontext-ui-quickForms/includes/isLoaded-description.md](formcontext-ui-quickForms/includes/isLoaded-description.md)]|
|[actualizar](formcontext-ui-quickForms/refresh.md)|[!INCLUDE[formcontext-ui-quickForms/includes/refresh-description.md](formcontext-ui-quickForms/includes/refresh-description.md)]|
|[setDisabled](formcontext-ui-quickForms/setDisabled.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setDisabled-description.md](formcontext-ui-quickForms/includes/setDisabled-description.md)]|
|[setFocus](formcontext-ui-quickForms/setFocus.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setFocus-description.md](formcontext-ui-quickForms/includes/setFocus-description.md)]|
|[setLabel](formcontext-ui-quickForms/setLabel.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setLabel-description.md](formcontext-ui-quickForms/includes/setLabel-description.md)]|
|[setVisible](formcontext-ui-quickForms/setVisible.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setVisible-description.md](formcontext-ui-quickForms/includes/setVisible-description.md)]|


### <a name="related-topics"></a>Temas relacionados

[formContext.ui](formContext-ui.md)