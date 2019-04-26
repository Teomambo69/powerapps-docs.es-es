---
title: Crear diseños de capacidad de respuesta en las aplicaciones de lienzo | Microsoft Docs
description: Información de referencia acerca de cómo configurar las propiedades de alto, ancho, X e Y en los controles en las aplicaciones de lienzo
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ddd11ddd40792ef1042536041554737ddb16547b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61562724"
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>Crear diseños de capacidad de respuesta en las aplicaciones de lienzo

Antes de compilar una aplicación de lienzo en PowerApps, especifique si desea adaptar la aplicación para una tableta o un teléfono. Esta opción determina el tamaño y forma del lienzo en el que va a crear la aplicación.

Después de realizar esa elección, puede realizar algunas opciones más si selecciona **archivo** > **configuración de la aplicación** > **tamaño y orientación de pantalla**. Puede elegir vertical o con orientación horizontal y el tamaño de pantalla (sólo Tablet PC). También puede bloquear o desbloquear la relación de aspecto y admite la rotación de dispositivos (o no).

Estas opciones forman la base de cada opción de que realizar al diseñar diseños de pantalla. Si la aplicación se ejecuta en un dispositivo de un tamaño diferente o en la web, todo el diseño se escala para ajustarse a la pantalla donde se ejecuta la aplicación. Por ejemplo, si una aplicación diseñada para un teléfono se ejecuta en una ventana del explorador de gran tamaño, la aplicación se escala para compensar y es demasiado grande para su espacio. La aplicación no puede sacar partido de los píxeles adicionales mostrando más controles o contenido más.

Si crea un diseño dinámico, los controles pueden responder a distintos dispositivos o tamaños de ventana, realizar que varias experiencias de resultar más naturales. Para lograr un diseño con capacidad de respuesta, ajustar la configuración y escribir expresiones en toda la aplicación. 

## <a name="disable-scale-to-fit"></a>Desactivar Ajustar al tamaño

Puede configurar todas las pantallas para que su diseño se adapta para el espacio real en el que se ejecuta la aplicación.

Activar la capacidad de respuesta mediante la desactivación de la aplicación **ajustar al tamaño** configuración, que está activada de forma predeterminada. Cuando se desactivará esta opción, también desactiva **Bloquear relación de aspecto** porque ya no se está diseñando para una forma de pantalla específica. (Se puede especificar si la aplicación admite la rotación de dispositivos.)

![Deshabilitar la escala para ajustarse a la configuración](media/create-responsive-layout/scale-to-fit-off.png)

Para mejorar la aplicación con capacidad de respuesta, debe realizar pasos adicionales, pero este cambio es el primer paso para hacer posible la capacidad de respuesta.

## <a name="understand-app-and-screen-dimensions"></a>Comprender las dimensiones de pantalla y la aplicación

Para realizar el diseño de la aplicación responder a cambios en las dimensiones de pantalla, deberá escribir fórmulas que usan la **ancho** y **alto** propiedades de la pantalla. Para mostrar estas propiedades, abrir una aplicación en PowerApps Studio y, a continuación, seleccione una pantalla. Las fórmulas predeterminadas para estas propiedades aparecen en la **avanzadas** ficha del panel derecho.

**Ancho** = `Max(App.Width, App.DesignWidth)`

**Alto** = `Max(App.Height, App.DesignHeight)`

Estas fórmulas que hacen referencia a la **ancho**, **alto**, **DesignWidth**, y **DesignHeight** propiedades de la aplicación. La aplicación **ancho** y **alto** propiedades corresponden a las dimensiones de la ventana del explorador o dispositivo en el que se ejecuta la aplicación. Si el usuario cambia el tamaño de la ventana del explorador (o gira el dispositivo si ha desactivado **bloquear orientación**), los valores de estas propiedades cambian dinámicamente. Las fórmulas en la pantalla **ancho** y **alto** se vuelven a evaluar las propiedades cuando cambian estos valores.

El **DesignWidth** y **DesignHeight** propiedades proceden de las dimensiones que se especifican en el **tamaño y orientación de pantalla** panel de **configuración de la aplicación**. Por ejemplo, si selecciona el diseño de teléfono en orientación vertical, **DesignWidth** es 640, y **DesignHeight** es 1136.

Ya que se usan en las fórmulas de la pantalla **ancho** y **alto** propiedades, se puede considerar **DesignWidth** y **DesignHeight** como las dimensiones mínimas para el que podrá diseñar la aplicación. Si el área real disponible para la aplicación es incluso más pequeño que estos mínimos las dimensiones, las fórmulas de la pantalla **ancho** y **alto** propiedades garantizan que sus valores no se convierten en un tamaño inferior a cantidades mínimas. En ese caso, el usuario debe desplazarse para ver todo el contenido de la pantalla.

Después de establecer la aplicación **DesignWidth** y **DesignHeight**, no (en la mayoría de los casos) tendrá que cambiar las fórmulas predeterminadas para cada pantalla **ancho** y **Alto** propiedades. Más adelante, en este tema se describen casos en los que puede que desee personalizar estas fórmulas.

## <a name="use-formulas-for-dynamic-layout"></a>Usar fórmulas para el diseño dinámico

Para crear un diseño dinámico, busque y tamaño de cada control mediante el uso de fórmulas en lugar de valores absolutos de las coordenadas (constantes). Estas fórmulas expresan posición y el tamaño en cuanto a tamaño global de la pantalla o en relación con otros controles en la pantalla de cada control.

> [!IMPORTANT]
> Después de escribir fórmulas para la **X**, **Y**, **ancho** y **alto** propiedades de un control, las fórmulas se sobrescribirá con Si arrastra el control a continuación en el lienzo del editor de valores constantes. Cuando empiece a usar fórmulas para lograr un diseño dinámico, debe evitar arrastra los controles.

En el caso más simple, un control pasa a ocupar una pantalla completa. Para crear este efecto, establezca las propiedades del control en estos valores:

| Propiedad      | Value            |
|--------|---------------|
| **X**      | `0`             |
| **Y**      | `0`             |
| **Width**  | `Parent.Width`  |
| **Height** | `Parent.Height` |

Estas fórmulas utilizan el **primario** operador. Para un control que se colocan directamente en una pantalla, **primario** hace referencia a la pantalla. Con estos valores de propiedad, el control aparece en la esquina superior izquierda de la pantalla (0, 0) y tiene el mismo **ancho** y **alto** como la pantalla.

Más adelante en este tema, va a aplicar estos principios (y el **primario** operador) para colocar los controles dentro de otros contenedores, tales como las galerías, agrupar controles y componentes.

Como alternativa, el control puede llenar sólo la mitad superior de la pantalla. Para crear este efecto, establezca el **alto** propiedad **Parent.Height** / 2 y deje las otras fórmulas sin cambios.

Si desea que un segundo control para rellenar la parte inferior de la mitad de la misma pantalla, que puede seguir al menos dos otros métodos para construir sus fórmulas. Por motivos de simplicidad, puede adoptar este enfoque:

| Control | Propiedad | Fórmula           |
|-|----------|-------------------|
| **superior** | **X**        | `0`                 |
| **superior** | **Y**        | `0`                 |
| **superior** | **Width**    | `Parent.Width`      |
| **superior** | **Height**   | `Parent.Height / 2` |
| **inferior** | **X**        | `0`                 |
| **inferior** | **Y**        | `Parent.Height / 2` |
| **inferior** | **Width**    | `Parent.Width`      |
| **inferior** | **Height**   | `Parent.Height / 2` |

![Superior e inferior de control](media/create-responsive-layout/dynamic-layout.png)

Esta configuración podría lograr el efecto que desee, pero deberá editar cada fórmula si cambia de opinión sobre los tamaños relativos de los controles. Por ejemplo, podría decidir que debe ocupar el control superior solo la superior un tercio de la pantalla, con el control de la parte inferior rellenando los dos tercios menor. 

Para crear ese efecto, deberá actualizar el **alto** propiedad de la **superior** control y el **Y** y **alto** propiedades de la **Inferior** control. En su lugar, considere la posibilidad de escribir las fórmulas para la **inferior** controlar en términos de la **superior** control (y sí mismo), como en este ejemplo:


| Control | Propiedad | Fórmula           |
|-|----------|-------------------|
| **superior** | **X**        | `0`                 |
| **superior** | **Y**        | `0`                 |
| **superior** | **Width**    | `Parent.Width`      |
| **superior** | **Height**   | `Parent.Height / 2` |
| **inferior** | **X**        | `0`                       |
| **inferior** | **Y**        | `Upper.Y + Upper.Height`  |
| **inferior** | **Width**    | `Parent.Width`            |
| **inferior** | **Height**   | `Parent.Height - Lower.Y` |

![Superior e inferior controla el tamaño relativo](media/create-responsive-layout/dynamic-layout2.png)

Con estas fórmulas en su lugar, debe cambiar solamente el **alto** propiedad de la **superior** control para expresar una fracción del alto de la pantalla diferentes. El **inferior** control se desplaza y cambia de tamaño para tener en cuenta el cambio automáticamente.

Puede usar estos patrones fórmulas para expresar las relaciones de diseño comunes entre un control denominado **C**y su elemento primario o un control relacionado, denominado **d**.

| Relación entre C y su elemento primario | Propiedad | Fórmula | Ilustración |
|--|--|--|--|
| **C** ancho del elemento primario, se rellena con un margen de *N* | **X**| `N` | ![Ejemplo de C de ancho de relleno del elemento primario](media/create-responsive-layout/c1.png) |
|  | **Width** | `Parent.Width - (N * 2)` |  |
| **C** alto del elemento primario, se rellena con un margen de *N* | **Y** | `N` | ![Ejemplo de C llenado alto del elemento primario](media/create-responsive-layout/c2.png) |
|  | **Height** | `Parent.Height - (N * 2)` |  |
| **C** alineado con el borde derecho del elemento primario, con el margen de *N* | **X** | `Parent.Width - (C.Width + N)` | ![Ejemplo de C que se alinea con el borde del elemento primario](media/create-responsive-layout/c3.png) |
| **C** alineado con el borde inferior del elemento primario, con el margen de *N* | **Y** | `Parent.Height - (C.Height + N)` | ![Ejemplo de C que se alinea con el borde del elemento primario](media/create-responsive-layout/c4.png) |
| **C** centra horizontalmente en el elemento primario | **X** | `(Parent.Width - C.Width) / 2` | ![Ejemplo de C que se centra horizontalmente en el elemento primario](media/create-responsive-layout/c5.png) |
| **C** centrado verticalmente en primario | **Y** | `(Parent.Height - C.Height) / 2` | ![Ejemplo de C centrado verticalmente en primario](media/create-responsive-layout/c6.png) |

| Relación entre C y D | Propiedad | Fórmula | Ilustración |
|--|--|--|--|
| **C** alineadas horizontalmente con **d.** y el mismo ancho que **d.** | **X** | `D.X` | ![Ejemplo de modelo](media/create-responsive-layout/d1.png) |
|  | **Width**    | `D.Width` |  |
| **C** alineado verticalmente con **d.** y la misma altura que **d.**  | **Y** | `D.Y` | ![Ejemplo de modelo](media/create-responsive-layout/d2.png) |
|  | **Height** | `D.Height` |  |
| Borde derecho del **C** alineado con el borde derecho de **d.** | **X** | `D.X + D.Width - C.Width` | ![Ejemplo de modelo](media/create-responsive-layout/d3.png) |
| Bottom edge de **C** alineado con el borde inferior de **d.** | **Y** | `D.Y + D.Height - C.Height` | ![Ejemplo de modelo](media/create-responsive-layout/d4.png) |
| **C** centrado horizontal relativo a **d.** | **X** | `D.X + (D.Width - C.Width) / 2`  | ![Ejemplo de modelo](media/create-responsive-layout/d5.png) |
| **C** centrado verticalmente relativo a **d.** | **Y** | `D.Y + (D.Height - C.Height) /2` | ![Ejemplo de modelo](media/create-responsive-layout/d6.png) |
| **C** situado a la derecha del **d.** con un espacio de N | **X** | `D.X + D.Width - N` | ![Ejemplo de modelo](media/create-responsive-layout/d7.png) |
| **C** coloca bajo **d.** , con un intervalo de *N*             | **Y** | `D.Y + D.Height + N` | ![Ejemplo de modelo](media/create-responsive-layout/d8.png) |
| **C** rellena el espacio entre **d.** y el borde derecho del elemento primario | **X** | `D.X + D.Width` | ![Ejemplo de modelo](media/create-responsive-layout/d9.png) |
|  | **Width** | `Parent.Width - C.X` |  |
| **C** rellena el espacio entre **d.** e inferior de borde del elemento primario | Y | `D.Y + D.Height` | ![Ejemplo de modelo](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>Formato jerárquico

Medida que genera las pantallas que contienen más controles, se convertirá en más conveniente (o incluso necesarios) para colocar controles en relación con un control principal, en lugar de con respecto a la pantalla o un control del mismo nivel. Al organizar los controles en una estructura jerárquica, puede hacer más fácil de escribir y mantener las fórmulas.

### <a name="galleries"></a>Galerías

Si usa una galería en la aplicación, deberá disponer de los controles dentro de la plantilla de la galería. Puede colocar estos controles para escribir las fórmulas que usan la **primario** operador, que hará referencia a la plantilla de la galería. En las fórmulas en los controles dentro de una plantilla de la galería, use el **Parent.TemplateHeight** y **Parent.TemplateWidth** propiedades; no use **Parent.Width** y **Parent.Height**, que hacen referencia el tamaño total de la galería.

![Galería vertical que muestra la plantilla de ancho y alto](media/create-responsive-layout/gallery-vertical.png)

### <a name="enhanced-group-control"></a>Control de grupo mejorada

Puede usar una característica experimental, una mejora **grupo** control, como un control principal. Para activar esta característica, seleccione **archivo** > **configuración de la aplicación** > **configuración avanzada**.

Considere el ejemplo de un encabezado en la parte superior de la pantalla. Es habitual tener un encabezado con un título y varios iconos con la que los usuarios pueden interactuar. Puede construir un encabezado de ese tipo mediante una mejora **grupo** controlar, que contiene un **etiqueta** control y dos **icono** controles:

![Ejemplo de encabezado mediante un grupo](media/create-responsive-layout/header-group.png)

Establecer las propiedades de estos controles a estos valores:

| Propiedad | Encabezado | Menú | Cerrar | Título |
|--|--|--|--|--|
| **X** | `0`  | `0` | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **Y** | `0` | `0` | `0` | `0` |
| **Width**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **Height** | `64` | `Parent.Height` | `Parent.Height` | `Parent.Height` |

Para el **encabezado** control, `Parent` hace referencia a la pantalla. Para los demás `Parent` hace referencia a la **encabezado** control.

Tras escribir estas fórmulas, puede ajustar el tamaño o posición de la **encabezado** control cambiando las fórmulas para sus propiedades. Los tamaños y posiciones de los controles secundarios se ajustarán automáticamente según corresponda.

### <a name="components"></a>Componentes

Si usa otra característica experimental, denominado componentes, puede crear bloques de creación y reutilizarlos en toda la aplicación. Igual que con el **grupo** control, los controles que se colocan dentro de un componente deben basar sus posición y tamaño de las fórmulas en `Parent.Width` y `Parent.Height`, que hacen referencia al tamaño del componente. Más información: [Crear un componente](create-component.md).

## <a name="adapting-layout-for-device-size-and-orientation"></a>Adaptar el diseño de orientación y el tamaño de dispositivo

Hasta ahora, ha aprendido a usar fórmulas para cambiar el tamaño de cada control en respuesta al espacio disponible, mientras mantiene los controles alineados entre sí. Pero es posible que quiere o necesita realizar cambios de diseño más importantes en respuesta a los dispositivos diferentes tamaños y orientaciones. Cuando un dispositivo se gira de vertical a horizontal, por ejemplo, puede cambiar de un diseño vertical a una horizontal. En un dispositivo de mayor tamaño, puede presentar más contenido o reorganizar para proporcionar un diseño más atractivo. En un dispositivo más pequeño, debe dividir el contenido entre varias pantallas.

### <a name="device-orientation"></a>Orientación del dispositivo

Las fórmulas predeterminadas para una pantalla **ancho** y **alto** propiedades, como en este tema se ha descrito anteriormente, no necesariamente proporcionan una buena experiencia si un usuario gira un dispositivo. Por ejemplo, una aplicación diseñada para un teléfono en orientación vertical tiene un **DesignWidth** de 640 y un **DesignHeight** de 1136. La misma aplicación en un teléfono con orientación horizontal tendrá estos valores de propiedad:

- La pantalla **ancho** propiedad está establecida en `Max(App.Width, App.DesignWidth)`. La aplicación **ancho** (1136) es mayor que su **DesignWidth** (640), por lo que la fórmula se evalúa como 1136.
- La pantalla **alto** propiedad está establecida en `Max(App.Height, App.DesignHeight)`. La aplicación **alto** (640) es menor que su **DesignHeight** (1136), por lo que la fórmula se evalúa como 1136.

Con una pantalla **alto** de 1136 y una altura de dispositivo (en esta orientación) de 640, el usuario debe desplazar la pantalla verticalmente para mostrar todo su contenido, que puede no ser la experiencia que desee.

Para adaptar la pantalla **ancho** y **alto** propiedades a la orientación del dispositivo, puede usar estas fórmulas:

**Ancho** = `Max(App.Width, If(App.Width < App.Height, App.DesignWidth, App.DesignHeight))`

**Alto** = `Max(App.Height, If(App.Width < App.Height, App.DesignHeight, App.DesignWidth))`

Estas fórmulas intercambiar la aplicación **DesignWidth** y **DesignHeight** valores, en función de si la anchura del dispositivo es menor que su altura (con orientación vertical) o más de su altura (orientación horizontal) .

Después de ajustar la pantalla **ancho** y **alto** fórmulas, es posible que también desea reorganizar los controles dentro de la pantalla para mejorar el uso de espacio disponible. Por ejemplo, si cada uno de los dos controles ocupa la mitad de la pantalla, puede apilarlos verticalmente en vertical pero Organícelos en paralelo en horizontal.

Puede usar la pantalla **orientación** propiedad para determinar si la pantalla está orientada horizontal o verticalmente.

> [!NOTE]
> En orientación horizontal, el **superior** y **inferior** controles aparecen como controles de la izquierda y derecho.

| Control | Propiedad | Fórmula |
|--|----------|---|
| **superior** | **X** | `0` |
| **superior** | **Y** | `0` |
| **superior** | **Width** | `If(Parent.Orientation = Layout.Vertical, Parent.Width, Parent.Width / 2)` |
| **superior** | **Height**   | `If(Parent.Orientation = Layout.Vertical, Parent.Height / 2, Parent.Height)` |
| **inferior** | X | `If(Parent.Orientation = Layout.Vertical, 0, Upper.X + Upper.Width)`  |
| **inferior** | Y | `If(Parent.Orientation = Layout.Vertical, Upper.Y + Upper.Height, 0)` |
| **inferior** | **Width** | `Parent.Width - Lower.X` |
| **inferior** | **Height** | `Parent.Height - Lower.Y` |

![expresiones para adaptar una orientación vertical](media/create-responsive-layout/portrait.png)

![expresiones para adaptar una orientación horizontal](media/create-responsive-layout/landscape.png)

### <a name="screen-sizes-and-breakpoints"></a>Tamaños de pantalla y los puntos de interrupción

Puede ajustar el diseño según el tamaño del dispositivo. La pantalla **tamaño** propiedad clasifica el tamaño actual del dispositivo. El tamaño es un entero positivo; el tipo de ScreenSize proporciona constantes con nombre para ayudar a mejorar la legibilidad. Esta tabla enumeran las constantes:

| Constante              | Value | Tipo de dispositivo típico (mediante la configuración de la aplicación de forma predeterminada) |
|-----------------------|-------|--------------------------------------------------|
| ScreenSize.Small      | 1     | Teléfono                                            |
| ScreenSize.Medium     | 2     | Tableta, sostenido verticalmente                          |
| ScreenSize.Large      | 3     | Tableta, horizontalmente                        |
| ScreenSize.ExtraLarge | 4     | Equipo de escritorio                                 |

Use estos tamaños para tomar decisiones sobre el diseño de la aplicación. Por ejemplo, si desea un control se oculta en un teléfono tamaño dispositivo pero visible en caso contrario, podría establecer el control **Visible** propiedad en esta fórmula:

`Parent.Size >= ScreenSize.Medium`

Esta fórmula se evalúa como **true** cuando el tamaño es de tamaño medio o grande y **false** en caso contrario.

Si desea un control para ocupar una fracción del ancho de pantalla en función del tamaño de pantalla diferentes, establezca el control **ancho** propiedad en esta fórmula:

```powerapps-dot
Parent.Width *  
    Switch(Parent.Size,  
        ScreenSize.Small, 0.5,  
        ScreenSize.Medium, 0.3,  
        0.25)
```
Esta fórmula establece el ancho del control a la mitad del ancho de pantalla en una pantalla pequeña, en décimas de tres del ancho de pantalla en una pantalla de medio y un cuarto del ancho de la pantalla en las pantallas de todos los demás.

## <a name="custom-breakpoints"></a>Puntos de interrupción personalizados

La pantalla **tamaño** propiedad se calcula comparando la pantalla **ancho** propiedad a los valores de la aplicación **SizeBreakpoints** propiedad. Esta propiedad es una tabla de una columna de números que indican los puntos de interrupción de ancho que separan los tamaños de pantalla con nombre:

En una aplicación creada para tableta o web, el valor predeterminado en la aplicación **SizeBreakpoints** son propiedad **[600, 900, 1200]**. En una aplicación creada para teléfonos, el valor es **[1200, 1800, 2400]**. (Los valores para las aplicaciones de teléfono se duplican porque dichas aplicaciones usan coordenadas que son eficazmente doble las coordenadas que se utilizan en otras aplicaciones).

![valores predeterminados de propiedad App.SizeBreakpoints](media/create-responsive-layout/default-breakpoints.png)

Puede personalizar los puntos de interrupción de la aplicación cambiando los valores de la aplicación **SizeBreakpoints** propiedad. Seleccione **aplicación** en la vista de árbol, seleccione **SizeBreakpoints** en la propiedad de lista y, a continuación, edite los valores de la barra de fórmulas. Puede crear muchos puntos de interrupción como la aplicación necesita, pero solo cambia el tamaño de 1 a 4 corresponden a los tamaños de pantalla con nombre. En las fórmulas, puede hacer referencia a los tamaños más allá de ExtraLarge por sus valores numéricos (5, 6 y así sucesivamente).

También puede especificar menos puntos de interrupción. Por ejemplo, la aplicación podría necesitar sólo tres tamaños (dos puntos de interrupción), por lo que los tamaños de pantalla posibles será pequeño, mediano y grande.

## <a name="known-limitations"></a>Limitaciones conocidas

El lienzo de creación no responde a las fórmulas de ajuste de tamaño que creó. Para probar el comportamiento de la capacidad de respuesta, guardar y publicar la aplicación y, a continuación, abrirlo en dispositivos o ventanas de explorador de varios tamaños y orientaciones.

Si escribe las expresiones o las fórmulas de la **X**, **Y**, **ancho**, y **alto** propiedades de un control, sobrescribirá los las expresiones o fórmulas si más adelante arrastrar el control a una ubicación diferente o cambiar el tamaño del control arrastrando su borde.
