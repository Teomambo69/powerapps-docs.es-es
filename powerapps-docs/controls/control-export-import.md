---
title: 'Control Exportar y control Importar: referencia | Microsoft Docs'
description: "Información sobre el control Exportar y el control Importar, que incluye propiedades y ejemplos"
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
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 2bc1eddc09fde255fbc1f7a7899ba2f416374e0c
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="export-control-and-import-control-in-powerapps"></a>Control Exportar y control Importar en PowerApps
Controles para exportar datos a un archivo local y luego importarlos en otra aplicación de PowerApps.

## <a name="description"></a>Descripción
Si desea crear más de una aplicación que utiliza los mismos datos, pero no quiere compartir esos datos fuera de esas aplicaciones, puede exportarlos e importarlos mediante un control **Exportar** y un control **Importar**. Cuando se exportan datos, se crea un archivo comprimido que se puede copiar en otra máquina y leer en cualquier programa que no sea PowerApps.

## <a name="warning"></a>Advertencia
Al habilitar esta funcionalidad en la aplicación, puede exponerla a vulnerabilidades de seguridad y pérdida de datos.  Se recomienda aconsejar a los usuarios que importen solo los archivos reconocidos y de confianza y que exporten únicamente los datos que no sean confidenciales.

## <a name="key-properties"></a>Propiedades principales
**Data**: el nombre de una colección que quiere exportar a un archivo local.

* La propiedad **Data** está disponible para un control **Exportar** pero no para un control **Importar**.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

## <a name="additional-properties"></a>Propiedades adicionales
**[Align](properties-text.md)**: la ubicación del texto respecto al centro horizontal de su control.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**[Padding](properties-size-location.md)**: la distancia entre el texto de un botón Exportar o Importar y los bordes de ese botón.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[RadiusBottomLeft](properties-size-location.md)**: el grado al que se redondea la esquina inferior izquierda de un control.

**[RadiusBottomRight](properties-size-location.md)**: el grado al que se redondea la esquina inferior derecha de un control.

**[RadiusTopLeft](properties-size-location.md)**: el grado al que se redondea la esquina superior izquierda de un control.

**[RadiusTopRight](properties-size-location.md)**: el grado al que se redondea la esquina superior derecha de un control.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[Text](properties-core.md)**: texto que aparece en un control o que el usuario escribe en un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[VerticalAlign](properties-text.md)**: la ubicación del texto en un control respecto al centro vertical de ese control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo
1. Agregue un control **[Botón](control-button.md)** y establezca su propiedad **[OnSelect](properties-core.md)** en esta fórmula:
   <br>**ClearCollect(Products, {Name:"Europa", Price:"10.99"}, {Name:"Ganymede", Price:"12.49"}, {Name:"Callisto", Price:"11.79"})**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
   
    ¿Desea más información sobre la función **[ClearCollect](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
2. Presione F5, haga clic o pulse el control **[Botón](control-button.md)** y luego presione Esc.
3. Agregue un control **Exportar** y establezca su propiedad **Data** en **Productos**.
4. Presione F5, haga clic o pulse el control **Exportar** y luego especifique el nombre del archivo en el que desea exportar los datos.
5. Haga clic o pulse **Guardar** y luego presione Esc para volver al área de trabajo predeterminada.
6. En una aplicación nueva o existente, agregue un control **Importar**, asígnele el nombre **MyData** y establezca su propiedad **[OnSelect](properties-core.md)** en esta fórmula:<br>
   **Collect(ImportedProducts, MyData.Data)**
7. Presione F5, haga clic o pulse **MyData**, haga clic o pulse el archivo exportado y luego haga clic o pulse **Abrir**.
8. Presione Esc, haga clic o pulse **Colecciones** en el menú **Archivo** y confirme que la aplicación actual tiene los datos que ha exportado.

