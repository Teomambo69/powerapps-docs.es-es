---
title: formContext.ui.FormSelector (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Aprenda a trabajar con procesos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuiformselector-client-api-reference"></a>formContext.ui.FormSelector (referencia de la API de cliente)



La propiedad **formContext.ui.formSelector** le permite trabajar con los elementos de formulario donde un elemento de formulario representa un formulario que está disponible para un usuario porque está asociado con un rol de seguridad al que el usuario también está asociado. A menudo habrá solo un formulario. Cuando hay más de un formulario disponible, los métodos para un elemento del formulario se pueden usar para cambiar el formulario que el usuario está visualizando.

Los elementos del formulario están disponibles a través de cualquiera de las siguientes:

- Recopilación **formselector.items**: una recopilación de todos los elementos de formulario accesibles al usuario actual. Sólo los formularios que comparten una asociación con uno de los roles de seguridad del usuario están disponibles en esta colección. Ejemplo:
 
    `formItem = formContext.ui.formSelector.items.get(arg);`

    Consulte [Recopilaciones](collections.md)) para obtener información sobre los métodos de recopilación.
 
    >[!NOTE]
    >Esta recopilación no está disponible para los clientes de móviles de Dynamics 365 (teléfonos y tabletas).

- Método **formselector.getCurrentItem**: devuelve una referencia al formulario mostrado actualmente. Si solo hay un formulario disponible, este método devolverá el valor **nulo**. Ejemplo:
 
    `formItem = formContext.ui.formSelector.getCurrentItem();`       

## <a name="form-item-methods"></a>Métodos de elementos de formulario

Después de recuperar un elemento de formulario de una de las formas anteriores, utilice los siguientes métodos para trabajar con el elemento de formulario. 

|Nombre|Descripción|
|--|--|
|[getId](formcontext-ui-formselector/getId.md)|[!INCLUDE[formcontext-ui-formselector/includes/getId-description.md](formcontext-ui-formselector/includes/getId-description.md)]|
|[getLabel](formcontext-ui-formselector/getLabel.md)|[!INCLUDE[formcontext-ui-formselector/includes/getLabel-description.md](formcontext-ui-formselector/includes/getLabel-description.md)]|
|[navigate](formcontext-ui-formselector/navigate.md)|[!INCLUDE[formcontext-ui-formselector/includes/navigate-description.md](formcontext-ui-formselector/includes/navigate-description.md)]|


