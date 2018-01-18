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
ms.openlocfilehash: 2fd5db380eead5403d4cc7d927da5a24aa24abc9
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="attachments-control-in-powerapps"></a>Control Datos adjuntos en PowerApps
Un control que permite a los usuarios descargar archivos en su dispositivo.  Pronto estará disponible la funcionalidad de carga.

## <a name="description"></a>Descripción
Un control **Datos adjuntos** le permite abrir archivos almacenados en un origen de datos.

## <a name="key-properties"></a>Propiedades principales
**[Items](properties-core.md)** : el origen de donde se describen los archivos que se pueden descargar.

**MaxAttachments**: el número máximo de archivos que acepta el control.

**OnAttach**: cómo responde la aplicación cuando el usuario agrega nuevos datos adjuntos.

**OnRemove**: cómo responde la aplicación cuando el usuario elimina datos adjuntos existentes.

**[OnSelect](properties-core.md)**: cómo responde la aplicación cuando el usuario hace clic en unos datos adjuntos.

## <a name="additional-properties"></a>Propiedades adicionales
**AddAttachmentText**: el texto de la etiqueta del botón que se usa para agregar nuevos datos adjuntos.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**NoAttachmentsText**: texto informativo que se muestra al usuario cuando no hay datos adjuntos para mostrar.

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
