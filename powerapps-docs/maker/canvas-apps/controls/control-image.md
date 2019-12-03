---
title: 'Control Imagen: referencia | Microsoft Docs'
description: Información sobre el control Imagen, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02c9e680582b6d51a613fd8089709401f1e80b32
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679762"
ms.PowerAppsDecimalTransform: true
---
# <a name="image-control-in-powerapps"></a>Control Imagen en PowerApps
Un control que muestra una imagen desde, por ejemplo, un archivo local o un origen de datos.

## <a name="description"></a>Descripción
Si agrega uno o varios controles **Imagen** controles a la aplicación, puede mostrar imágenes individuales que no forman parte de un conjunto de datos, o puede incorporar imágenes desde registros de orígenes de datos.

## <a name="key-properties"></a>Propiedades principales
**[Imagen](properties-visual.md)** : el nombre de la imagen que aparece en un control de imagen, audio o micrófono.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla.

**ApplyEXIFOrientation**: si se aplica automáticamente la orientación especificada en los datos EXIF insertados en la imagen.

**AutoDisableOnSelect**: deshabilita automáticamente el control mientras se ejecuta el comportamiento AlSeleccionar.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**CalculateOriginalDimensions**: habilita las propiedades **AltoOriginal** y **AnchoOriginal**.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)** : el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)** : el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**FlipHorizontal**: si la imagen se voltea horizontalmente antes de mostrarla.

**FlipVertical**: si la imagen se voltea verticalmente antes de mostrarla.

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[PosiciónDeLaImagen](properties-visual.md)** : posición (**Rellenar**, **Ajustar**, **Estirar**, **Icono** o **Centrar**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.

**ImageRotation**: cómo girar la imagen antes de mostrarla.  Los valores pueden ser: no, 90 grados a la derecha, 90 grados a la izquierda y 180 grados a la derecha.

**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**AltoOriginal**: la altura original de una imagen, habilitada con la propiedad **CalculateOriginalDimensions**.

**AnchoOriginal**: el ancho original de una imagen, habilitada con la propiedad **CalculateOriginalDimensions**.

**[RellenoInferior](properties-size-location.md)** : distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)** : distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)** : distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)** : distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[RadiusBottomLeft](properties-size-location.md)** : el grado al que se redondea la esquina inferior izquierda de un control.

**[RadiusBottomRight](properties-size-location.md)** : el grado al que se redondea la esquina inferior derecha de un control.

**[RadiusTopLeft](properties-size-location.md)** : el grado al que se redondea la esquina superior izquierda de un control.

**[RadiusTopRight](properties-size-location.md)** : el grado al que se redondea la esquina superior derecha de un control.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**Transparencia**: el grado en el los controles permanecen visibles detrás de una imagen.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Quitar**( *DataSource*; EsteElemento)](../functions/function-remove-removeif.md)

## <a name="examples"></a>Ejemplos
### <a name="show-an-image-from-a-local-file"></a>Mostrar una imagen desde un archivo local
1. En el menú **Archivo**, pulse o haga clic en **Multimedia** y, después, en **Examinar**.
2. Pulse o haga clic en el archivo de imagen que desea agregar, pulse o haga clic en **Abrir**, y, a continuación, presione Esc para volver al área de trabajo predeterminada.
3. Agregue un control **Imagen** y en su propiedad **Image** escriba el nombre del archivo que agregó.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?

    El control **Imagen** muestra la imagen que ha especificado.

### <a name="show-a-set-of-images-from-a-data-source"></a>Mostrar un conjunto de imágenes desde un origen de datos
1. Descargue este [archivo de Excel](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx)y guárdelo en el dispositivo local.
2. En Power apps Studio, cree o abra una aplicación y, a continuación, haga clic o pulse en **Agregar origen de datos** en el panel derecho.

    Si **Agregar origen de datos** no aparece en el panel de la derecha, pulse o haga clic en la barra de navegación izquierda de una pantalla.
3. Pulse o haga clic en **Agregar datos estáticos a la aplicación**, pulse o haga clic en el archivo de Excel que descargó y, a continuación en **Abrir**.
4. Seleccione la casilla **Flooring Estimates** y a continuación, pulse o haga clic en **Conectar**.
5. Agregue un control **Galería** con imágenes y establezca su propiedad **[Artículos](properties-core.md)** en **FlooringEstimates**.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?

    El control **Galería** muestra imágenes de productos de moqueta, parquet y mosaico basados en vínculos en el archivo de Excel que ha descargado.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
* Si el gráfico se utiliza como botón, se aplican los [requisitos estándar de contraste de color](../accessible-apps-color.md).
* Considere la posibilidad de comprobar si hay problemas de contraste en la imagen, si no es simplemente decorativa.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente si el gráfico se usa como botón o no solo como decoración.
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar vacía o la cadena **""** vacía si el gráfico es exclusivamente decorativo. De esta forma, los lectores de pantalla omiten el gráfico.
* La propiedad **[AccessibleLabel](properties-accessibility.md)** puede estar vacía o la cadena **""** vacía si el gráfico proporciona información redundante.
  * Por ejemplo, un control **Imagen** de engranajes con su propiedad **[AccessibleLabel](properties-accessibility.md)**  establecida en **Configuración**. Esta imagen no se utiliza como botón. Se encuentra junto a una **[etiqueta](control-text-box.md)** que también dice **Configuración**. Los lectores de pantalla leerán la imagen como **Configuración** y, nuevamente, la etiqueta como **Configuración**. No es necesario tanto detalle. En este caso, el control **Imagen** no necesita una propiedad **[AccessibleLabel](properties-accessibility.md)** .

    > [!IMPORTANT]
    > Los lectores de pantalla siempre leerán los controles **Imagen** cuya propiedad **[TabIndex](properties-accessibility.md)** sea cero o superior, incluso si la propiedad **[AccessibleLabel](properties-accessibility.md)** está vacía. El motivo es que se representan como botones. Si no se proporciona ninguna propiedad **[AccessibleLabel](properties-accessibility.md)** , los lectores de pantalla simplemente leerán el gráfico como un **botón**.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* **[TabIndex](properties-accessibility.md)** debe ser cero o mayor si el gráfico se utiliza como botón. De esta forma, los usuarios de teclado pueden navegar hasta él.
* Los indicadores de foco deben ser claramente visibles si el gráfico se usa como botón. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.

    > [!NOTE]
  > Cuando **[TabIndex](properties-accessibility.md)**  es cero o mayor, el control **Imagen** se representa como un botón. No hay ningún cambio en la apariencia visual, pero los lectores de pantalla identifican correctamente la imagen como un botón. Cuando **[TabIndex](properties-accessibility.md)** es menor que cero, el control **Imagen** se identifica como una imagen.
