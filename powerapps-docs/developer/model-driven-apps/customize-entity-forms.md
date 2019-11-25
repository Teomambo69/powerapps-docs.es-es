---
title: Personalización de los formularios de la entidad (aplicaciones basadas en modelos) | Microsoft Docs
description: Los formularios ofrecen la interfaz de usuario (UI) que los usuarios usan para crear, ver, o editar registros de la entidad. Use el diseñador de formulario en las herramientas de personalización para crear y modificar formularios de entidad. Este tema le confiere la información necesaria para crear o editar formularios mediante programación.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: e6a25bbe-e484-cfe9-9ad9-20ac6f19336a
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d108949576e682e88a140f62426d4351cb3ef82c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749620"
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

### <a name="see-also"></a>Vea también  
 [Crear y diseñar formularios](../../maker/model-driven-apps/create-design-forms.md)   
 [Entidad SystemForm](../common-data-service/reference/entities/systemform.md)  
 [Esquema XML de formulario](form-xml-schema.md)