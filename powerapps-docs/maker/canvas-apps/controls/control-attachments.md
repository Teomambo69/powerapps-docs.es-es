---
title: 'Control Datos adjuntos: referencia | Microsoft Docs'
description: Información sobre el control Datos adjuntos, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/23/2018
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5279f9368cdd832e84fba13faf8643cd7392d70b
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650803"
---
# <a name="attachments-control-in-powerapps"></a>Control Datos adjuntos en PowerApps
Un control que permite a los usuarios descargar archivos en su dispositivo, así como cargar y eliminar archivos de una lista de SharePoint o una entidad Common Data Service.

## <a name="limitations"></a>Límite
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
1. Cree una aplicación de datos usando una lista de SharePoint como origen de datos. Como alternativa, puede agregar un formulario a la aplicación y establecer una lista de SharePoint como su origen de datos.

2. Seleccione el control **Formulario** en la vista de árbol del lado izquierdo.

3. Haga clic en **Datos** en la pestaña Propiedades en el panel de opciones de la derecha.

4. En **Campos**, habilite el campo **Datos adjuntos**.

    El campo de datos adjuntos asociado a la lista de SharePoint aparecerá en el formulario.

[Aprenda a agregar y configurar un control].(../add-configure-controls.md)


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
