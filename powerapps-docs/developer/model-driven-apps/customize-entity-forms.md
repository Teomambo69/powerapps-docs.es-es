---
title: Personalización de los formularios de la entidad (aplicaciones basadas en modelos) | Microsoft Docs
description: Los formularios ofrecen la interfaz de usuario (UI) que los usuarios usan para crear, ver, o editar registros de la entidad. Use el diseñador de formulario en las herramientas de personalización para crear y modificar formularios de entidad. Este tema le confiere la información necesaria para crear o editar formularios mediante programación.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: e6a25bbe-e484-cfe9-9ad9-20ac6f19336a
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f81937377d647aae58f189236c1d656d6ab988e5
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "3126507"
---
# <a name="customize-entity-forms"></a>Personalizar los formularios de entidad

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/customize-entity-forms -->

Los formularios ofrecen la interfaz de usuario (UI) que los usuarios usan para crear, ver, o editar registros de la entidad. Use el diseñador de formulario en las herramientas de personalización para crear y modificar formularios de entidad. Más información: [Crear y diseñar formularios](../../maker/model-driven-apps/create-design-forms.md) para obtener información acerca de las tareas relacionadas con el trabajo con formularios en la aplicación.  

 Este tema le confiere la información necesaria para crear o editar formularios mediante programación.  

<a name="BKMK_AccessingFormDefinitions"></a>   

## <a name="access-form-definitions"></a>Definiciones de formulario de acceso  
 Los formularios de entidad se almacenan en la entidad `SystemForm` junto con paneles y visualizaciones. Hay dos formas para inspeccionar las definiciones de formularios para una entidad:  

-   Incluya la entidad en una solución no administrada y exporte la solución.  

-   Consulte la entidad `SystemForm`  

<a name="BKMK_ViewingFormXml"></a>   

### <a name="view-formxml-from-an-exported-entity"></a>Ver FormXML desde una entidad exportada  
 Sólo las definiciones de los formularios de entidad del sistema que se hayan personalizado se incluyen en la solución administrada exportada. Para ver la definición de un formulario de entidad del sistema, debe cambiarlo de alguna forma, o crear un nuevo formulario guardando el formulario existente con un nuevo nombre.  

 Tras exportar la solución, extraiga el contenido y vea el archivo customizations.xml. Encontrará la definición de los formularios en `ImportExportXml` > `Entities` > `Entity` > `FormXml`. En el nodo de `<FormXml>`, verá que cada tipo de formulario se agrupa en un elemento de `<forms>` con el atributo de `type` especificando el tipo de formulario.  

<a name="BKMK_FormProperties"></a>   
## <a name="form-properties"></a>Propiedades del formulario  
 La siguiente tabla describe atributos clave de la entidad `SystemForm` y los datos correspondientes incluidos en los elementos XML exportados con la solución.  


|  Propiedad de SystemForm  |                 Elemento de FormXML                 |                                                                                                              Descripción                                                                                                              |
|-----------------------|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   `AncestorFormId`    |                  `<ancestor>`                   |                      Identificador único del formulario primario. Esto se establece cuando crea un formulario nuevo mediante **Guardar como** para un formulario existente o mediante <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest>.                      |
|    `CanBeDeleted`     |                `<CanBeDeleted>`                 |                                    Información que especifica si se puede eliminar este componente. Esta propiedad administrada se aplica únicamente si el formulario se creó con la importación de una solución administrada.                                    |
|     `Description`     |                `<Descriptions>`                 | `Description` es una cadena y `<Descriptions>` contiene las etiquetas localizadas para la descripción del formulario.<br /><br /> Las etiquetas localizadas se pueden recuperar mediante <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest>. |
| `FormActivationState` |             `<FormActivationState>`             |                                  Especifica el estado del formulario.<br /><br /> Solo los formularios de tipo "principal" se pueden desactivar.<br /><br /> Valores válidos:<br /><br /> -   0: Inactivo<br />-   1: Activo                                  |
|       `FormId`        |                   `<formid>`                    |                                                                                                     Identificador único del formulario                                                                                                     |
|  `FormPresentation`   |              `<FormPresentation>`               |                                     Especifica si este formulario está en el diseño actualizado de la interfaz de usuario en Common Data Service.                                      |
|       `FormXml`       |                    `<form>`                     |                                                                                                Representación XML del diseño de formularios.                                                                                                 |
|  `IntroducedVersion`  |              `<IntroducedVersion>`              |                                                                                          Versión de la solución en la que se agregó el formulario.                                                                                          |
|     `IsAIRMerged`     |                       N/D                       |                                           Especifica si este formulario se combina con el diseño actualizado de la interfaz de usuario en Common Data Service.                                           |
|   `IsCustomizable`    |               `<IsCustomizable>`                |                            Información que especifica si se puede personalizar este componente.<br /><br /> Esta propiedad administrada se aplica únicamente si el formulario se creó con la importación de una solución administrada.                            |
|      `IsDefault`      |                       N/A                       |                                                                          Información que especifica si el formulario o el panel es el predeterminado del sistema.                                                                          |
|        `Name`         |               `<LocalizedNames>`                |       `Name` es una cadena y `<LocalizedNames>` contiene las etiquetas localizadas para el nombre del formulario.<br /><br /> Las etiquetas localizadas se pueden recuperar mediante <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest>.       |
|   `ObjectTypeCode`    | El formulario es un elemento secundario del elemento de `Entity`. |                                                                                        El valor de `ObjectTypeCode` es el nombre lógico de la entidad.                                                                                         |
|        `Type`         |       Atributo de `type` del elemento de la `<forms>`        |                                                       Los valores válidos para los formularios son:<br /><br /> -   2: `main`<br />-   5: `mobile`<br />-   6: `quick`<br />-   7: `quickCreate`                                                        |

<a name="BKMK_CreateAndEditForms"></a>   

## <a name="create-and-edit-forms"></a>Crear y editar formularios  

 Solo puede crear nuevos formularios para una entidad donde <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>. <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateForms> lo permite.  

 Puede crear formularios nuevos con <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> o <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest>. Cuando usa <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest> o **Guardar como** en el editor de formularios, tenga en cuenta que no hay datos heredados entre los formularios. Por lo tanto, los cambios en el formulario base no se aplican automáticamente a los formularios creados a partir de él.  

 Editar las definiciones del formulario desde una solución administrada exportada y después reimportar la solución es un método compatible para editar formularios de entidad. Al editar manualmente los formularios recomendamos usar un editor XML que permita la validación de esquema. Más información: [Editar el archivo XML de personalizaciones con la validación de esquema](edit-customizations-xml-file-schema-validation.md).  

## <a name="open-main-form-in-a-dialog-using-client-api"></a>Abra el formulario principal en un cuadro de diálogo utilizando la API del cliente

Para abrir el formulario principal en un cuadro de diálogo utilizando la API del cliente, debe invocar la llamada utilizando el método [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto). El método de API [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto) le permite abrir el cuadro de diálogo con varias opciones, incluido el tamaño y la posición.

> [!IMPORTANT]
> - El formulario principal abierto en un cuadro de diálogo con la API del cliente todavía está en la vista previa.
> - Las vistas previas de características no se han diseñado para un uso de producción y pueden tener una funcionalidad restringida. Estas características están disponibles antes del lanzamiento oficial para que los clientes puedan tener un acceso anticipado y proporcionar comentarios.


> [!NOTE]
> El método [Xrm.Navigation.openForm](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/openform) no es compatible para abrir un formulario principal como cuadro de diálogo.

## <a name="examples"></a>Ejemplos

### <a name="open-a-new-record"></a>Abrir un nuevo registro

En este ejemplo, el cuadro de diálogo abre un nuevo formulario de cuenta para crear un nuevo registro. El cuadro de diálogo aparece en el centro utilizando hasta el 50 % de la ventana disponible como cuadro modal encima del formulario desde el que se invocó o se llamó.

```JavaScript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2}, {target: 2, position: 1, width: {value: 50, unit:"%"}});
```
> [!div class="mx-imgBorder"]
> ![Abrir un nuevo registro](media/open-new-record-mfd.png "Abrir un nuevo registro")

### <a name="open-an-existing-record"></a>Abrir un registro existente

En este ejemplo, el cuadro de diálogo abre un registro de cuenta existente utilizando el valor de Id. de entidad de cuenta sobre el formulario de contacto. Reemplace el id. de la entidad por cualquier valor de id. del registro que desee abrir en el cuadro de diálogo.

```JavaScript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2, entityId:"xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"}, {target: 2, position: 1, width: {value: 80, unit:"%"}});
```
> [!div class="mx-imgBorder"]
> ![Abrir un registro existente](media/open-existing-record-mfd.png "Abrir un registro existente")

### <a name="open-a-new-record-on-the-side-pane"></a>Abrir un nuevo registro en el panel lateral.

En este ejemplo, el cuadro de diálogo abre un nuevo registro en la esquina derecha de la ventana. Esto se puede lograr mediante el uso de las opciones de píxeles.

```JavaScript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2}, {target: 2, position: 2, width: {value: 500, unit:"px"}});
```
> [!div class="mx-imgBorder"]
> ![Abra un registro existente en el panel lateral](media/open-record-side-pane-mfd.png "Abrir un registro existente en el panel lateral")

### <a name="open-main-form-in-a-dialog-with-callback-method"></a>Abrir formulario principal en un diálogo con el método de devolución de llamada

Este ejemplo muestra cómo se invoca un cuadro de diálogo de formulario principal con un método de devolución de llamada después de guardar un registro y cerrar el cuadro de diálogo.

```Javascript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2},{target: 2, position: 2, width: {value: 80, unit:"%"}}).then(
    function (retVal) {
        console.log(retVal.savedEntityReference[0].id + ", " + retVal.savedEntityReference[0].name)
    },
    function (error) {
        console.log(error);
    });
```

### <a name="see-also"></a>Vea también  

 [Crear y diseñar formularios](../../maker/model-driven-apps/create-design-forms.md)   
 [Entidad SystemForm](../common-data-service/reference/entities/systemform.md)  
 [Esquema XML de formulario](form-xml-schema.md)<br/>
 [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto)
