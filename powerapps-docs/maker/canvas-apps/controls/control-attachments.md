---
title: 'Control Datos adjuntos: referencia | Microsoft Docs'
description: Información sobre el control Datos adjuntos, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/23/2018
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ad52396eda0c8db46dd38cb7176524df5feb7416
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834667"
---
# <a name="attachments-control-in-powerapps"></a>Control Datos adjuntos en PowerApps
Un control que permite a los usuarios descargar archivos en su dispositivo, así como cargar y eliminar archivos de una lista de SharePoint.

## <a name="limitations"></a>Limitaciones
El control de datos adjuntos tiene las siguientes limitaciones temporales:
1. Internet Explorer admite la descarga de datos adjuntos solo dentro de los formularios de lista personalizada de SharePoint.

1. La carga de los datos adjuntos solo funciona con orígenes de datos de la lista de SharePoint.  La compatibilidad con otros orígenes de datos se introducirá de forma incremental, se empezará con CDS.

1. La carga y eliminación de una funcionalidad solo funcionan dentro de un formulario.  El control de datos adjuntos parecerá que está deshabilitado en modo de edición, pero no dentro de los formularios.   Tenga en cuenta que con el fin de guardar las incorporaciones y eliminaciones de archivos en el back-end, el usuario final debe guardar el formulario.

1. No se pueden cargar archivos con un tamaño superior a 10 MB.  

1. Actualmente, los dispositivos iOS solo pueden cargar archivos de documentos y cuentas de almacenamiento en la nube. Para adjuntar fotografías o vídeos, use el explorador web en el dispositivo iOS para ejecutar la aplicación.

## <a name="description"></a>Descripción
Un control de **datos adjuntos** permite abrir los archivos almacenados en un origen de datos, así como agregar y eliminar archivos de una lista de SharePoint.

## <a name="key-properties"></a>Propiedades principales
**[Items](properties-core.md)** : el origen de donde se describen los archivos que se pueden descargar.

**MaxAttachments**: el número máximo de archivos que acepta el control.

**MaxAttachmentSize**: el tamaño de archivo máximo permitido, en MB, de cada elemento adjunto nuevo.  Actualmente, el límite se encuentra en 10 MB.

**OnAttach**: cómo responde la aplicación cuando el usuario agrega nuevos datos adjuntos.

**OnRemove**: cómo responde la aplicación cuando el usuario elimina datos adjuntos existentes.

**[OnSelect](properties-core.md)**: cómo responde la aplicación cuando el usuario hace clic en unos datos adjuntos.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla. Debe describir el fin de los datos adjuntos.

**AddAttachmentText**: el texto de la etiqueta del vínculo que se usa para agregar nuevos datos adjuntos.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite agregar y eliminar archivos (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**MaxAttachmentsText**: el texto que reemplaza al vínculo de "Adjuntar archivo" cuando el control contiene el número máximo de archivos permitidos.

**NoAttachmentsText**: texto informativo que se muestra al usuario cuando no hay archivos adjuntos.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Visible](properties-core.md)** : indica si un control está visible u oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).


## <a name="example"></a>Ejemplo
1. Cree una aplicación de datos usando una lista de SharePoint como origen de datos.  Otra alternativa es agregar un formulario a la aplicación y establecer una lista de SharePoint como su origen de datos.

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
