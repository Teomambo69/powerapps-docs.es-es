---
title: 'Control Datos adjuntos: referencia | Microsoft Docs'
description: "Información sobre el control Datos adjuntos, con propiedades y ejemplos"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/29/2017
ms.author: fikaradz
ms.openlocfilehash: b58e99e4775ed5c18d3498864c6e652e814ddf19
ms.sourcegitcommit: c76ec82db5d261be1fb7fdeeec3e119cdfada57f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="attachments-control-in-powerapps"></a>Control Datos adjuntos en PowerApps
Un control que permite a los usuarios descargar archivos en su dispositivo, así como cargar y eliminar archivos de una lista de SharePoint.

## <a name="limitations"></a>Limitaciones
El control de datos adjuntos tiene las siguientes limitaciones temporales:
1. La carga de los datos adjuntos solo funciona con orígenes de datos de la lista de SharePoint.  La compatibilidad con otros orígenes de datos se introducirá de forma incremental, se empezará con CDS.

1. La carga y eliminación de una funcionalidad solo funcionan dentro de un formulario.  El control de datos adjuntos parecerá que está deshabilitado en modo de edición, pero no dentro de los formularios.   Tenga en cuenta que con el fin de guardar las incorporaciones y eliminaciones de archivos en el back-end, el usuario final debe guardar el formulario.

1. No se pueden cargar archivos con un tamaño superior a 10 MB.  

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
**AccessibleLabel**: la etiqueta anunciada por los lectores de pantalla.

**AddAttachmentText**: el texto de la etiqueta del vínculo que se usa para agregar nuevos datos adjuntos.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite agregar y eliminar archivos (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**MaxAttachmentsText**: el texto que reemplaza al vínculo de "Adjuntar archivo" cuando el control contiene el número máximo de archivos permitidos.

**NoAttachmentsText**: texto informativo que se muestra al usuario cuando no hay archivos adjuntos.

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

¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
