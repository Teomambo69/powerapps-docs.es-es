---
title: Contexto de formulario de API de cliente en aplicaciones basadas en modelos| MicrosoftDocs
ms.date: 04/10/2019
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: 0cf94e8d-801a-451f-98c3-130e912f963b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e40c21bb1e26ebefca3ea8d71fb1d02dad1700b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749628"
---
# <a name="client-api-form-context"></a>Contexto de formulario de la API del cliente



El contexto del formulario de cliente API (**formContext**) proporciona una referencia al formulario o a un elemento en el formulario, como por ejemplo, un control de vista rápida o una fila de una cuadrícula editable, en el que se ejecuta el código actual.

Anteriormente, el objeto **Xrm.Page** global se usaba para representan un formulario o un elemento en el formulario. Con la versión más reciente, el objeto **Xrm.Page** está [obsoleto](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated), y ahora debe utilizar el método [getFormContext](reference/executioncontext/getFormContext.md) del objeto de contexto de ejecución pasado para devolver referencia al formulario adecuado o a un elemento en el formulario. 

> [!IMPORTANT]
> *Obsoleta* significa que se va a quitar una característica o una funcionalidad en una versión futura de aplicaciones basadas en modelos, la característica o funcionalidad continuará funcionando y estará completamente admite hasta que se quite oficialmente. Se realizará un anuncio público aquí en la documentación, en el blog oficial, y en muchos otros lugares al menos seis meses antes de la eliminación.<br/><br/>El uso del objeto **Xrm.Page** como acceso estático al contexto principal de formulario *todavía* se admite para mantener compatibilidad con versiones anteriores de scripts existentes y no se eliminará tan pronto como algunos otros métodos API de cliente que aparecen en la sección [Obsolescencia de API de cliente](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) . Se recomienda usar el nuevo objeto **formContext** en lugar del objeto **Xrm.Page** en el código dirigido a la versión 9.0 o posterior donde sea posible. Además, usar el objeto **formContext** permite crear controladores de eventos comunes que pueden funcionar en un formulario o en una cuadrícula editable en función de dónde sea llamado. Más información: [getFormContext (referencia de la API de cliente)](reference/executioncontext/getFormContext.md).<br><br>Obtener el objeto **formContext** para las funciones de JavaScript para acciones de la cinta es diferente de cómo obtenerlo en secuencias de comandos de formulario. Más información: [Formulario y cuadrícula en las acciones de la cinta](../pass-data-page-parameter-ribbon-actions.md#form-and-grid-context-in-ribbon-actions).

## <a name="using-the-formcontext-object-instead-of-the-xrmpage-object"></a>Uso del objeto formContext en lugar del objeto Xrm.Page 

Es muy fácil convertir un código existente con **Xrm.Page** para usar el nuevo objeto **formContext**. Por ejemplo, considere el siguiente script que utiliza el objeto **Xrm.Page**:

```JavaScript
function displayName()
{
    var firstName = Xrm.Page.getAttribute("firstname").getValue();
    var lastName = Xrm.Page.getAttribute("lastname").getValue();
    console.log(firstName + " " + lastName);
}
```

Presentamos el script actualizado que utiliza lo pasado en el contexto de ejecución para recuperar el objeto **formContext** en lugar de utilizar el objeto **Xrm.Page** estático:

```JavaScript
function displayName(executionContext)
{
    var formContext = executionContext.getFormContext(); // get formContext

    // use formContext instead of Xrm.Page  
    var firstName = formContext.getAttribute("firstname").getValue(); 
    var lastName = formContext.getAttribute("lastname").getValue();
    console.log(firstName + " " + lastName);
}
```

>[!IMPORTANT]
>Recuerde seleccionar la opción **pasar el contexto de ejecución como primer parámetro** en el diálogo **propiedades de controlador** al definir los controladores de eventos para usar el objeto **formContext**. Más información: [Contexto de ejecución de la API del cliente](clientapi-execution-context.md)

## <a name="formcontext-object-model"></a>Modelo de objetos formContext

Utilice los objetos **data** y **ui** del objeto **formContext** para manipular mediante programación los elementos de la interfaz de usuario y los datos de aplicaciones basadas en modelos.

![Modelo de objetos formContext](../media/ClientAPI-formContextModel.png)

### <a name="data-object"></a>objeto de datos

Proporciona acceso a los datos de entidad y los métodos para administrar los datos en el formulario así como en el control de flujo de proceso de negocio. Contiene los siguientes objetos:

| **Objeto**  | **Descripción**|
|-----------------|----------------|
|entidad|Proporciona métodos para recuperar información específica del registro que se muestra en la página, el método y una recopilación de todos los atributos incluidos en el formulario.|
|proceso|Proporciona métodos para recuperar propiedades de un flujo de proceso de negocio.|

También proporciona una recopilación de **atributos** para obtener acceso a un control no vinculado a la entidad. Consulte la sección **Recopilaciones en el modelo de objetos formContext** más adelante en este tema.

Más información: [formContext.data](reference/formContext-data.md) 

### <a name="ui-object"></a>objeto ui

Proporciona métodos para recuperar información acerca de la interfaz de usuario, además de recopilaciones para varios subcomponentes del formulario o la cuadrícula. Contiene los siguientes objetos:

| **Objeto**  | **Descripción**|
|-----------------|----------------|
|formSelector|Proporciona una recopilación de elementos que proporciona funciones para consultar los formularios disponibles para el usuario actual. Use el método navigate para cerrar el formulario actual y abrir otro diferente.|
|navegación|No contiene ningún método. Proporciona acceso a elementos de navegación a través de la recopilación de elementos. Para obtener más información, vea la siguiente sección sobre recopilaciones.|
|proceso|Proporciona métodos para interactuar con el control del flujo de proceso de negocio en un formulario.|

Más información: [formContext.ui](reference/formContext-ui.md)

## <a name="collections-in-the-formcontext-object-model"></a>Recopilaciones en el modelo de objeto formContext

La siguiente tabla describe las recopilaciones en el modelo de objetos **Xrm**. Para obtener información sobre los métodos disponibles para recopilaciones en general, vea [Recopilaciones (referencia de la API de cliente)](reference/collections.md).

| **Recopilación**  | **Descripción**|
|-----------------|----------------|
| [atributos](reference/attributes.md)  | Dos objetos contienen una recopilación de atributos:<br/><br/>- La recopilación **formContext.data.attributes** proporciona acceso a atributos no vinculados a entidad.<br/><br/>- La recopilación **formContext.data.entity.attributes** proporciona acceso a cada atributo de entidad que esté disponible en el formulario. Solo los atributos que correspondan a los campos que se agregan al formulario están disponibles.| 
| [controles](reference/controls.md)  | Tres objetos contienen una recopilación de controles:<br/><br/> - **formContext.ui.controls**: proporciona acceso a cada control presente en el formulario.<br/><br/>- **formContext.data.entity.attribute.controls**: dado que un atributo puede tener más de un control en el formulario, esta recopilación proporciona acceso a cada uno de ellos. Esta recopilación contendrá solo un elemento a menos que se agreguen varios controles para el atributo al formulario.<br/><br/>- **formContext.ui.tabs.sections.controls**: esta recopilación solo contiene los controles que se encuentran en la sección.|
|**formContext.data.process.**[stages](reference/formContext-data-process/process/getStages.md) y **formContext.data.process**.[steps](reference/formContext-data-process/stage/getSteps.md)| Proporciona acceso a una recopilación de etapas y pasos en un flujo de proceso de negocio. También permiten agregar o quitar elementos de la recopilación.|
|**formContext.ui.formselector.**[items](reference/formContext-ui-formselector.md)|Cuando se proporcionan varios formularios para una entidad, puede asociarlos con roles de seguridad. Cuando los roles de seguridad asociados a un usuario les permiten ver más de un formulario, la recopilación **formContext.ui.formSelector.items** proporciona acceso a cada definición del formulario disponible para ese usuario.|
|**formContext.ui.navigation.**[items](reference/formContext-ui-navigation.md)|La recopilación **formContext.ui.navigation.items** proporciona acceso a elementos de navegación que se definen mediante el área de navegación del editor de formularios. Los usuarios pueden desplazarse a ellos mediante la barra de comandos.|
| **formContext.ui.**[quickForms](reference/formContext-ui-quickForms.md) | Proporciona métodos para obtener acceso a todos los controles de vista rápida y los controles que los componen en los formularios de Customer Engagement.| La recopilación **Xrm.Page.ui.tabs** proporciona acceso a cada una de estas pestañas.|
| **formContext.ui.**[tabs](reference/formContext-ui-tabs.md) | Puede organizar cada formulario mediante una o varias pestañas. Esta recopilación proporciona acceso a cada una de estas pestañas.|
| **formContext.ui.tabs.**[sections](reference/formContext-ui-sections.md) | Puede organizar cada pestaña de formulario usando una o varias secciones. La recopilación **sections** de la pestaña proporciona acceso a cada una de estas secciones.|


  
### <a name="related-topics"></a>Temas relacionados

[Método getFormContext](reference/executioncontext/getFormContext.md)<br/>
[Método getGlobalContext](reference/xrm-utility/getGlobalContext.md)<br/>
[Métodos del contexto de ejecución](reference/execution-context.md) 

 

