---
title: 'Control Pantalla: referencia | Microsoft Docs'
description: Información sobre el control Pantalla, con propiedades y ejemplos
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b0e189bc2bfd922839373f009fcc54a34217daba
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404344"
ms.PowerAppsDecimalTransform: true
---
# <a name="screen-control-in-power-apps"></a>Control de pantalla en Power apps

Elemento de la interfaz de usuario que contiene uno o más controles de una aplicación.

## <a name="description"></a>Descripción

La mayoría de las aplicaciones tienen varios controles **Pantalla** que contienen controles **[Etiqueta](control-text-box.md)** , **[Botón](control-button.md)** y otros controles que muestran los datos y son compatibles con la navegación. Para obtener información sobre cómo agregar una pantalla, cambiar el orden de las pantallas y configurar la navegación, consulte [Agregar una pantalla](../add-screen-context-variables.md).

## <a name="key-properties"></a>Propiedades principales

**[ImagenDeFondo](properties-visual.md)** : nombre de un archivo de imagen que aparece en el fondo de una pantalla.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

## <a name="additional-properties"></a>Propiedades adicionales

**Height** : el alto de la pantalla. Si la aplicación responde ([**escalar para ajustarse a**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) está **desactivada**) y el dispositivo en el que se ejecuta la aplicación es menor que esta propiedad, la pantalla se puede desplazar verticalmente.

**[PosiciónDeLaImagen](properties-visual.md)** : posición (**Rellenar**, **Ajustar**, **Estirar**, **Icono** o **Centrar**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.

**Nombre** : el nombre de la pantalla.

**AlEstarOculto**: el comportamiento de una aplicación cuando el usuario navega fuera de una pantalla.

**AlEstarVisible**: el comportamiento de una aplicación cuando el usuario navega a una pantalla.  Utilice esta propiedad para configurar las variables y cargar previamente los datos usados por la pantalla.  Use la propiedad [**app. OnStart**](../functions/object-app.md#onstart-property) para configurarla una vez cuando se inicie la aplicación.

**Orientación** : la orientación de la pantalla. Si su **ancho** es mayor que su **alto**, la orientación será **layout. horizontal**; de lo contrario, será **layout. vertical**.

**Tamaño** : un entero positivo que clasifica el tamaño de la pantalla. La clasificación se determina comparando la propiedad **width** de la pantalla con los valores de la propiedad [**app. SizeBreakpoints**](../functions/signals.md) . El tipo **ScreenSize** consta de cuatro valores (**pequeño**, **mediano**, **grande**y **extragrande**) que corresponden a los enteros comprendidos entre 1 y 4.

**Ancho** : el ancho de la pantalla. Si la aplicación responde ([**escalar para ajustarse a**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) está **desactivada**) y el dispositivo en el que se ejecuta la aplicación es más estrecho que esta propiedad, la pantalla se puede desplazar horizontalmente.

## <a name="related-functions"></a>Funciones relacionadas

[**Distinct**( *DataSource*; *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Ejemplo

1. Agregue un control **[Radio](control-radio.md)** , asígnele el nombre **ScreenFills** y establezca su propiedad **[Elementos](properties-core.md)** en este valor:

    `["Red"; "Green"]`

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?

1. Asigne al control **Pantalla** predeterminado el nombre **Source**, agregue otro control **Pantalla** y asígnele el nombre **Target**.

1. En **origen**, agregue un control **[forma](control-shapes-icons.md)** (como una flecha) y establezca su propiedad **[alseleccionar](properties-core.md)** en esta fórmula:

    `Navigate(Target; ScreenTransition.Fade)`

    ¿Desea más información sobre la función **[Navegar](../functions/function-navigate.md)** u [otras funciones](../formula-reference.md)?

1. En **Target**, agregue un control **[Forma](control-shapes-icons.md)** (como una flecha) y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:

    `Navigate(Source; ScreenTransition.Fade)`

1. Establezca la propiedad **[Fill](properties-color-border.md)** de **Target** en esta fórmula:

    `If("Red" in ScreenFills.Selected.Value; RGBA(255; 0; 0; 1); RGBA(54; 176; 75; 1))`

1. Seleccione la pantalla **origen** y, a continuación, mantenga presionada la tecla Alt, seleccione cualquiera de las opciones del control **[radio](control-radio.md)** y, a continuación, seleccione el control **[forma](control-shapes-icons.md)** .

    **Destino** aparece en el color que ha seleccionado.

1. En **destino**, seleccione el control **[forma](control-shapes-icons.md)** para volver al **origen**.

1. opta Seleccione la opción otros en el control **[radio](control-radio.md)** y, a continuación, seleccione el control **[forma](control-shapes-icons.md)** para confirmar que el **destino** aparece en el otro color.

1. opta Reordene las pantallas manteniendo el mouse sobre el **destino** en la barra de navegación izquierda, seleccionando los puntos suspensivos que aparecen y seleccionando **subir**.

    El **destino** aparece en primer lugar cuando el usuario abre la aplicación.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

### <a name="color-contrast"></a>Contraste de color

Cuando la **pantalla** es de hecho el fondo del texto, debe haber un contraste de color adecuado entre:

- **[Fill](properties-color-border.md)** y el texto
- **[BackgroundImage](properties-visual.md)** y el texto (si procede)

Por ejemplo, si un control **Pantalla** contiene un control **[Etiqueta](control-text-box.md)** y esta tiene relleno transparente, la propiedad **[Fill](properties-color-border.md)** de la pantalla se convierte de hecho en el color de fondo de la etiqueta.

Además de texto, podría también comprobar el contraste de color con objetos gráficos esenciales como las imágenes de estrella de un control **[Clasificación](control-rating.md)** .

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla

- Debe haber un nombre significativo para cada **pantalla**. El nombre de la pantalla se puede ver y editar de la misma manera que otros controles: en la vista de árbol del panel de controles o en el encabezado del panel de propiedades.

    > [!NOTE]
  > Cuando se carga una nueva **pantalla**, los lectores de pantalla anunciarán su nombre.
