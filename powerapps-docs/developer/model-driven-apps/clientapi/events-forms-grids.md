---
title: Eventos en formularios y cuadrículas en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9fb38429-55ef-45ce-a3a3-e649e1be89d0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ab767999bd518bdae7852f7692d62272b809bcd8
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749627"
---
# <a name="events-in-forms-and-grids-in-model-driven-apps"></a>Eventos en formularios y cuadrículas en aplicaciones basadas en modelos



Todo el código del lado cliente es iniciado por eventos. En las aplicaciones basadas en modelos, asocia una función específica a una biblioteca de JavaScript ([Recurso web del script](../script-jscript-web-resources.md)) para que se ejecute cuando se produzca un evento. Esta función se denomina *controlador de eventos*. Cada controlador de eventos especifica una sola función dentro de una biblioteca de JavaScript y los parámetros que pueden pasarse a la función.

Puede asociar controladores de eventos a solo algunos eventos mediante la interfaz de usuario. Para los eventos que no están disponibles para asociarlos a través de la interfaz de usuario, la API de cliente proporciona métodos que pueden usarse para vincular los controladores de eventos a dichos eventos. 

## <a name="add-or-remove-event-handler-function-to-event-using-ui"></a>Agregar o quitar funciones de controlador de eventos a eventos mediante la interfaz de usuario

Utilice la sección **Controladores de eventos** del cuadro de diálogo **Propiedades del formulario** para asociar el script a un evento para formularios y campos.

![Sección del controlador de eventos en las propiedades del formulario](../media/Form-EventHandlers.png)

## <a name="add-or-remove-event-handler-function-to-event-using-code"></a>Agregar o quitar funciones de controlador de eventos a eventos mediante el código

Use los siguientes métodos para agregar y quitar el controlador de eventos para los eventos que no se pueden asociar mediante la interfaz de usuario:

|Eventos |Controlador de eventos|
|-------|-------|
|Atributo [OnChange](reference/events/attribute-onchange.md) | Métodos [addOnChange](reference/attributes/addonchange.md) y [removeOnChange](reference/attributes/removeOnchange.md)|
|Formulario [OnLoad](reference/events/form-onload.md)| Métodos formContext.ui [addOnLoad](reference/formcontext-ui/addonload.md) y [removeOnLoad](reference/formcontext-ui/removeonload.md)|
|Datos de formulario [OnLoad](reference/events/form-data-onload.md)| Métodos formContext.data [addOnLoad](reference/formcontext-data/addonload.md) y [removeOnLoad](reference/formcontext-data/removeonload.md)|
|Formulario [OnSave](reference/events/form-onsave.md)| Métodos [addOnSave](reference/formcontext-data-entity/addonsave.md) y [removeOnSave](reference/formcontext-data-entity/removeonsave.md)|
|Control de búsqueda [PreSearch](reference/events/presearch.md)| Métodos [addPreSearch](reference/controls/addpresearch.md) y [removePreSearch](reference/controls/removepresearch.md)|
|Control kbsearch [OnResultOpened](reference/events/onresultopened.md)|Métodos [addOnResultOpened](reference/controls/addOnResultOpened.md) y [removeOnResultOpened](reference/controls/removeOnResultOpened.md)|
|Control kbsearch [OnSelection](reference/events/onselection.md)|Métodos [addOnSelection](reference/controls/addOnSelection.md) y [removeOnSelection](reference/controls/removeOnSelection.md)|
|Control kbsearch [PostSearch](reference/events/postsearch.md)|Métodos [addOnPostSearch](reference/controls/addOnPostSearch.md) y [removeOnPostSearch](reference/controls/removeOnPostSearch.md)|

>[!IMPORTANT]
>El contexto de ejecución se pasa automáticamente como el primer parámetro a las funciones definidas con el código. Más información: [Contexto de ejecución de la API del cliente](clientapi-execution-context.md) 

## <a name="form-event-pipeline"></a>Canalización de eventos de formulario
Puede definir hasta 50 controladores de eventos para cada evento. Cada controlador de eventos se ejecuta en el orden en que se muestra en la sección **Controladores de eventos** de la ficha **Eventos** del cuadro de diálogo **Propiedades del formulario**.

Use los métodos [setSharedVariable](reference/executioncontext/setSharedVariable.md) y [getSharedVariable](reference/executioncontext/getSharedVariable.md) para pasar una variable común entre los controladores de eventos (funciones). Use el método [getDepth](reference/executioncontext/getDepth.md) del contexto de ejecución para conocer la secuencia en que se ejecuta un controlador de eventos en relación con otros controladores de eventos. 

### <a name="related-topics"></a>Temas relacionados

[Comprender el modelo de objetos de la API de cliente](understand-clientapi-object-model.md)<br/>
[Contexto de ejecución de la API de cliente](clientapi-execution-context.md)<br/>
[Eventos (referencia de la API de cliente)](reference/events.md)<br/>

