---
title: 'Control Datos adjuntos: referencia | Microsoft Docs'
description: Información sobre el control Datos adjuntos, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 03/09/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 35e4107934134a229817deb258bacf5e36c9dbb6
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "78970982"
---
# <a name="attachments-control-in-power-apps"></a>Control de datos adjuntos en Power apps
Un control que permite a los usuarios descargar archivos en su dispositivo, así como cargar y eliminar archivos de una lista de SharePoint o una entidad Common Data Service.

## <a name="limitations"></a>Limitaciones
El control de datos adjuntos presenta estas limitaciones:
1. Los datos adjuntos son compatibles con las listas de SharePoint y Common Data Service entidades.

1. La funcionalidad de carga y eliminación solo funciona dentro de un formulario. El control de datos adjuntos aparece deshabilitado cuando está en modo de edición y no dentro de un formulario. Para guardar las adiciones y eliminaciones de archivos, el usuario de la aplicación debe guardar el formulario. Debido a esta limitación, el control de datos adjuntos no está disponible en la pestaña **Insertar** , pero aparece en el formulario cuando el campo de formulario de datos adjuntos está habilitado en un formulario de SharePoint o de Common Data Service.

1. Solo puede cargar archivos si son de 10 MB o más pequeños.  

## <a name="description"></a>Descripción
Un control de **datos adjuntos** le permite abrir, agregar y eliminar archivos de una lista de SharePoint o una entidad Common Data Service.

## <a name="key-properties"></a>Propiedades principales
**[Items](properties-core.md)** : el origen de donde se describen los archivos que se pueden descargar.

**MaxAttachments**: el número máximo de archivos que acepta el control.

**MaxAttachmentSize**: el tamaño de archivo máximo permitido, en MB, de cada elemento adjunto nuevo.  Actualmente, el límite se encuentra en 10 MB.

**OnAttach**: cómo responde la aplicación cuando el usuario agrega nuevos datos adjuntos.

**OnRemove**: cómo responde la aplicación cuando el usuario elimina datos adjuntos existentes.

**[OnSelect](properties-core.md)** : cómo responde la aplicación cuando el usuario hace clic en unos datos adjuntos.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla. Debe describir el fin de los datos adjuntos.

**AddAttachmentText**: el texto de la etiqueta del vínculo que se usa para agregar nuevos datos adjuntos.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite agregar y eliminar archivos (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**MaxAttachmentsText**: el texto que reemplaza al vínculo de "Adjuntar archivo" cuando el control contiene el número máximo de archivos permitidos.

**NoAttachmentsText**: texto informativo que se muestra al usuario cuando no hay archivos adjuntos.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Visible](properties-core.md)** : indica si un control está visible u oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).


## <a name="example"></a>Ejemplo
1. Agregue un formulario a la aplicación y establezca una lista de SharePoint como origen de datos.

2. Seleccione el control **Mostrar formulario** en la vista de árbol del lado izquierdo. También puede usar **Editar formulario** en su lugar.

3. Seleccione **origen de datos** en la pestaña propiedades en el panel de opciones de la derecha y, a continuación, seleccione la lista de SharePoint a la que se conectó.

4. Seleccione **Editar campos** en la sección de *campos* y seleccione **Agregar campo**. 

5. Seleccione el campo **datos adjuntos** y seleccione **Agregar**.

    El campo de datos adjuntos asociado a la lista de SharePoint aparecerá en el formulario.

[Obtener información sobre cómo agregar y configurar un control](../add-configure-controls.md)


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **ItemColor** y **ItemFill**
* **ItemHoverColor** y **ItemHoverFill**
* **ItemPressedColor** y **ItemPressedFill**
* **AddedItemColor** y **AddedItemFill**
* **RemovedItemColor** y **RemovedItemFill**
* **ItemErrorColor** y **ItemErrorFill**
* **AddAttachmentColor** y **Fill**
* **MaxAttachmentsColor** y **Fill**
* **NoAttachmentsColor** y **Fill**

Y esto, además de los [requisitos estándar de contraste de color](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
Las siguientes propiedades deben estar presentes:
* **[AccessibleLabel](properties-accessibility.md)**
* **AddAttachmentsText**
* **MaxAttachmentsText**
* **NoAttachmentsText**

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
