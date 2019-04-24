---
title: 'Control Pantalla: referencia | Microsoft Docs'
description: Información sobre el control Pantalla, con propiedades y ejemplos
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6fedff6d6ffc34fe390ec6978672d699480a7cb9
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61548740"
---
# <a name="screen-control-in-powerapps"></a>Control Pantalla en PowerApps

Elemento de la interfaz de usuario que contiene uno o más controles de una aplicación.

## <a name="description"></a>Descripción

La mayoría de las aplicaciones tienen varios controles **Pantalla** que contienen controles **[Etiqueta](control-text-box.md)**, **[Botón](control-button.md)** y otros controles que muestran los datos y son compatibles con la navegación. Para obtener información acerca de cómo agregar una pantalla, reorganizan las pantallas y configurar la exploración, revise [agregar una pantalla](../add-screen-context-variables.md).

## <a name="key-properties"></a>Propiedades principales

**[ImagenDeFondo](properties-visual.md)**: nombre de un archivo de imagen que aparece en el fondo de una pantalla.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

## <a name="additional-properties"></a>Propiedades adicionales

**Alto** -el alto de la pantalla. Si la aplicación es la capacidad de respuesta ([**escala para ajustarse a** ](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) es **desactivar**) y el dispositivo en el que se ejecuta la aplicación es menor que esta propiedad, la pantalla puede desplazar verticalmente.

**[PosiciónDeLaImagen](properties-visual.md)**: posición (**Rellenar**, **Ajustar**, **Estirar**, **Icono** o **Centrar**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.

**Nombre** -el nombre de la pantalla.

**AlEstarOculto**: el comportamiento de una aplicación cuando el usuario navega fuera de una pantalla.

**OnStart**: el comportamiento de la aplicación cuando el usuario la abre.

- La fórmula en la que se establece esta propiedad se ejecuta antes de que aparezca la primera pantalla de la aplicación. Llame a la función [**Navegar**](../functions/function-navigate.md) para cambiar qué pantalla aparece en primer lugar cuando se inicia la aplicación.
- No se pueden establecer [variables de contexto](../working-with-variables.md) con la función [**UpdateContext**](../functions/function-updatecontext.md) porque no ha aparecido aún ninguna pantalla. Sin embargo, puede pasar variables de contexto en la función **Navegar** y crear y rellenar una [colección](../working-with-variables.md) mediante el uso de la función [**Recopilar**](../functions/function-clear-collect-clearcollect.md).
- Cuando se actualiza una aplicación, se ejecuta la fórmula en la que se establece esta propiedad cuando la aplicación se carga en PowerApps Studio. Para ver el impacto de cambiar esta propiedad, tiene que guardar, cerrar y volver a cargar la aplicación.
- La propiedad **AlIniciar** es realmente una propiedad de la aplicación, no de la pantalla. Por comodidad a la hora de editar, se ve y se modifica como una propiedad en la primera pantalla de la aplicación. Si se quita la primera pantalla o se reorganizan las pantallas, puede ser difícil encontrar esta propiedad. En este caso, guarde, cierre y vuelva a cargar la aplicación y la propiedad volverá a aparecer como una propiedad de la primera pantalla.

**AlEstarVisible**: el comportamiento de una aplicación cuando el usuario navega a una pantalla.

**Orientación** -la orientación de la pantalla. Si su **ancho** es mayor que su **alto**, será la orientación **Layout.Horizontal**; en caso contrario, será **Layout.Vertical** .

**Tamaño** -un entero positivo que clasifica el tamaño de la pantalla. La clasificación se determina comparando la pantalla **ancho** propiedad a los valores de la [ **App.SizeBreakpoints** ](../functions/signals.md) propiedad. El **ScreenSize** tipo consta de cuatro valores (**pequeño**, **medio**, **grande**, y **ExtraLarge** ) que se corresponden con los enteros del 1 al 4.

**Ancho** -el ancho de la pantalla. Si la aplicación es la capacidad de respuesta ([**escala para ajustarse a** ](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) es **desactivar**) y el dispositivo en el que se ejecuta la aplicación es más estrecho que esta propiedad, la pantalla puede desplazarse horizontalmente.

## <a name="related-functions"></a>Funciones relacionadas

[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Ejemplo

1. Agregue un control **[Radio](control-radio.md)**, asígnele el nombre **ScreenFills** y establezca su propiedad **[Elementos](properties-core.md)** en este valor:

    `["Red", "Green"]`

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?

1. Asigne al control **Pantalla** predeterminado el nombre **Source**, agregue otro control **Pantalla** y asígnele el nombre **Target**.

1. En **origen**, agregue un **[forma](control-shapes-icons.md)** (por ejemplo, una flecha) y establezca su **[OnSelect](properties-core.md)** propiedad Esta fórmula:

    `Navigate(Target, ScreenTransition.Fade)`

    ¿Desea más información sobre la función **[Navegar](../functions/function-navigate.md)** u [otras funciones](../formula-reference.md)?

1. En **Target**, agregue un control **[Forma](control-shapes-icons.md)** (como una flecha) y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:

    `Navigate(Source, ScreenTransition.Fade)`

1. Establezca la propiedad **[Fill](properties-color-border.md)** de **Target** en esta fórmula:

    `If("Red" in ScreenFills.Selected.Value, RGBA(255, 0, 0, 1), RGBA(54, 176, 75, 1))`

1. Seleccione el **origen** pantalla y, a continuación, mientras mantiene presionada la tecla Alt, seleccione cualquiera de las opciones en el **[Radio](control-radio.md)** control y, a continuación, seleccione el **[Forma](control-shapes-icons.md)** control.

    **Destino** aparece en el color que seleccionó.

1. En **destino**, seleccione el **[forma](control-shapes-icons.md)** control para volver a **origen**.

1. (opcional) Seleccione la otra opción en el **[Radio](control-radio.md)** control y, a continuación, seleccione el **[forma](control-shapes-icons.md)** control para confirmar que **destino**  aparece en el otro color.

1. (opcional) Volver a ordenar las pantallas, mantener el mouse sobre **destino** en la barra de navegación izquierdo, seleccione los puntos suspensivos que aparece y, a continuación, seleccione **Subir**.

    **Destino** aparece en primer lugar cuando el usuario abre la aplicación.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

### <a name="color-contrast"></a>Contraste de color

Cuando la **pantalla** es de hecho el fondo del texto, debe haber un contraste de color adecuado entre:

- **[Fill](properties-color-border.md)** y el texto
- **[BackgroundImage](properties-visual.md)** y el texto (si procede)

Por ejemplo, si un control **Pantalla** contiene un control **[Etiqueta](control-text-box.md)** y esta tiene relleno transparente, la propiedad **[Fill](properties-color-border.md)** de la pantalla se convierte de hecho en el color de fondo de la etiqueta.

Además de texto, podría también comprobar el contraste de color con objetos gráficos esenciales como las imágenes de estrella de un control **[Clasificación](control-rating.md)**.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla

- Debe haber un nombre significativo para cada **pantalla**. El nombre de la pantalla se puede ver y editar de la misma manera que otros controles: en la vista de árbol del panel de controles o en el encabezado del panel de propiedades.

    > [!NOTE]
  > Cuando se carga una nueva **pantalla**, los lectores de pantalla anunciarán su nombre.
