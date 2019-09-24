---
title: Crear diseños con capacidad de respuesta en aplicaciones de Canvas | Microsoft Docs
description: Información de referencia sobre la configuración de propiedades de alto, ancho, X e y en los controles de las aplicaciones de lienzo
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm-msft
ms.date: 9/20/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: eee82691b288f21749fe58adbf02ab5ffc3bd8b4
ms.sourcegitcommit: 7016ff837eff2cb0985fc71edab95cbf99335677
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159855"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>Crear diseños con capacidad de respuesta en aplicaciones de lienzo

Antes de compilar una aplicación de lienzo en PowerApps, especifique si desea adaptar la aplicación para un teléfono o una tableta. Esta opción determina el tamaño y la forma del lienzo en el que compilará la aplicación.

Una vez realizada esta opción, puede elegir entre varias opciones si selecciona **archivo** > **aplicación configuración** > **tamaño y orientación**. Puede elegir la orientación vertical u horizontal y el tamaño de la pantalla (solo tableta). También puede bloquear o desbloquear la relación de aspecto y la rotación de dispositivos de soporte (o no).

Estas opciones se superponen entre sí cuando se diseñan diseños de pantalla. Si la aplicación se ejecuta en un dispositivo de un tamaño diferente o en la web, todo el diseño se escala para ajustarse a la pantalla donde se ejecuta la aplicación. Si una aplicación diseñada para un teléfono se ejecuta en una ventana grande del explorador, por ejemplo, la aplicación se escala para compensar y buscar el tamaño de su espacio. La aplicación no puede aprovechar los píxeles adicionales mostrando más controles o más contenido.

Si crea un diseño con capacidad de respuesta, los controles pueden responder a diferentes dispositivos o tamaños de ventana, por lo que hay varias experiencias más naturales. Para lograr un diseño dinámico, ajuste algunos valores y escriba expresiones en toda la aplicación. 

## <a name="disable-scale-to-fit"></a>Deshabilitar escalado para ajustar

Puede configurar cada pantalla para que su diseño se adapte al espacio real en el que se ejecuta la aplicación.

Puede activar la capacidad de respuesta desactivando la opción **escalar para ajustar** de la aplicación, que está activada de forma predeterminada. Al desactivar esta opción, también desactivará la **relación de aspecto de bloqueo** porque ya no está diseñando para una forma de pantalla específica. También puede especificar si la aplicación admite la rotación de dispositivos.

![Deshabilitar la configuración de ajuste de escala](media/create-responsive-layout/scale-to-fit-off.png)

Para que la aplicación responda, debe realizar pasos adicionales, pero este cambio es el primer paso para hacer posible la capacidad de respuesta.

## <a name="understand-app-and-screen-dimensions"></a>Descripción de las dimensiones de la aplicación y la pantalla

Para que los diseños de la aplicación respondan a los cambios en las dimensiones de la pantalla, escribirá fórmulas que usen las propiedades **ancho** y **alto** de la pantalla. Para mostrar estas propiedades, abra una aplicación en PowerApps Studio y, a continuación, seleccione una pantalla. Las fórmulas predeterminadas para estas propiedades aparecen en la pestaña **avanzadas** del panel derecho.

**Ancho** = `Max(App.Width; App.DesignWidth)`

**Alto** = `Max(App.Height; App.DesignHeight)`

Estas fórmulas hacen referencia a las propiedades **width**, **height**, **DesignWidth**y **DesignHeight** de la aplicación. Las propiedades de **ancho** y **alto** de la aplicación se corresponden con las dimensiones de la ventana del dispositivo o del explorador en el que se ejecuta la aplicación. Si el usuario cambia el tamaño de la ventana del explorador (o gira el dispositivo si ha desactivado la **orientación del bloqueo**), los valores de estas propiedades cambian dinámicamente. Las fórmulas de las propiedades **width** y **height** de la pantalla se vuelven a evaluar cuando cambian estos valores.

Las propiedades **DesignWidth** y **DesignHeight** provienen de las dimensiones que se especifican en el panel **tamaño de pantalla + orientación** de la configuración de la **aplicación**. Por ejemplo, si selecciona la distribución del teléfono en orientación vertical, **DesignWidth** es 640 y **DesignHeight** es 1136.

Como se usan en las fórmulas de las propiedades de **ancho** y **alto** de la pantalla, puede pensar en **DesignWidth** y **DesignHeight** como las dimensiones mínimas para las que diseñará la aplicación. Si el área real disponible para la aplicación es incluso menor que estas dimensiones mínimas, las fórmulas de las propiedades de **ancho** y **alto** de la pantalla garantizan que sus valores no se volverán más pequeños que los mínimos. En ese caso, el usuario debe desplazarse para ver todo el contenido de la pantalla.

Después de establecer los valores de **DesignWidth** y **DesignHeight**de la aplicación, no tendrá que cambiar las fórmulas predeterminadas para las propiedades de **ancho** y **alto** de la pantalla. Más adelante, en este tema se describen los casos en los que es posible que desee personalizar estas fórmulas.

## <a name="use-formulas-for-dynamic-layout"></a>Usar fórmulas para el diseño dinámico

Para crear un diseño con capacidad de respuesta, puede buscar y cambiar el tamaño de cada control mediante el uso de fórmulas en lugar de valores de coordenadas absolutas (constantes). Estas fórmulas expresan la posición y el tamaño de cada control en cuanto al tamaño total de la pantalla o con respecto a otros controles de la pantalla.

> [!IMPORTANT]
> Después de escribir las fórmulas para las propiedades **X**, **y**, **ancho** y **alto** de un control, las fórmulas se sobrescribirán con valores constantes si arrastra posteriormente el control en el editor de lienzos. Cuando empiece a usar fórmulas para lograr el diseño dinámico, debe evitar arrastrar los controles.

En el caso más simple, un control llena una pantalla completa. Para crear este efecto, establezca las propiedades del control en estos valores:

| Propiedad      | Value            |
|--------|---------------|
| **X1**      | `0`             |
| **SÍ**      | `0`             |
| **Ancho**  | `Parent.Width`  |
| **Alto** | `Parent.Height` |

Estas fórmulas utilizan el operador **Parent** . Para un control colocado directamente en una pantalla, el **elemento primario** se refiere a la pantalla. Con estos valores de propiedad, el control aparece en la esquina superior izquierda de la pantalla (0,0) y tiene el mismo **ancho** y **alto** que la pantalla.

Más adelante en este tema, aplicará estos principios (y el operador **principal** ) para colocar controles dentro de otros contenedores, como galerías, controles de grupo y componentes.

Como alternativa, el control solo puede rellenar la mitad superior de la pantalla. Para crear este efecto, establezca la propiedad **height** en **Parent. Height** /2 y deje las demás fórmulas sin modificar.

Si desea que un segundo control rellene la mitad inferior de la misma pantalla, puede tomar al menos otros dos enfoques para crear sus fórmulas. Para simplificar, puede adoptar este enfoque:

| Control | Propiedad | Fórmula           |
|-|----------|-------------------|
| **Esquina superior** | **X1**        | `0`                 |
| **Esquina superior** | **SÍ**        | `0`                 |
| **Esquina superior** | **Ancho**    | `Parent.Width`      |
| **Esquina superior** | **Alto**   | `Parent.Height / 2` |
| **Inferiores** | **X1**        | `0`                 |
| **Inferiores** | **SÍ**        | `Parent.Height / 2` |
| **Inferiores** | **Ancho**    | `Parent.Width`      |
| **Inferiores** | **Alto**   | `Parent.Height / 2` |

![Control superior e inferior](media/create-responsive-layout/dynamic-layout.png)

Esta configuración lograría el efecto que desea, pero debe editar cada fórmula si ha cambiado de opinión sobre los tamaños relativos de los controles. Por ejemplo, puede decidir que el control superior solo ocupará la parte superior de la pantalla, con el control inferior que rellenará los dos tercios más bajos. 

Para crear ese efecto, debe **actualizar la propiedad** **alto** del control **superior** y las propiedades y y **alto** del control **inferior** . En su lugar, considere la posibilidad de escribir las fórmulas para el control **inferior** en lo que respecta al control **superior** (y a sí mismo), como en este ejemplo:


| Control | Propiedad | Fórmula           |
|-|----------|-------------------|
| **Esquina superior** | **X1**        | `0`                 |
| **Esquina superior** | **SÍ**        | `0`                 |
| **Esquina superior** | **Ancho**    | `Parent.Width`      |
| **Esquina superior** | **Alto**   | `Parent.Height / 2` |
| **Inferiores** | **X1**        | `0`                       |
| **Inferiores** | **SÍ**        | `Upper.Y + Upper.Height`  |
| **Inferiores** | **Ancho**    | `Parent.Width`            |
| **Inferiores** | **Alto**   | `Parent.Height - Lower.Y` |

![Ajuste de tamaño relativo de los controles superior e inferior](media/create-responsive-layout/dynamic-layout2.png)

Con estas fórmulas en su lugar, solo tiene que cambiar la propiedad **alto** del control **superior** para expresar una fracción diferente del alto de la pantalla. El control **inferior** se mueve automáticamente y cambia de tamaño para que tenga en cuenta el cambio.

Puede usar estos patrones de fórmulas para expresar las relaciones de diseño comunes entre un control, denominado **C**, y su control primario o relacionado, denominado **D**.

| Relación entre C y su elemento primario | Propiedad | Fórmula | Ilustración |
|--|--|--|--|
| **C** rellena el ancho del elemento primario, con un margen de *N* | **X1**| `N` | ![Ejemplo de ancho de relleno de C de primario](media/create-responsive-layout/c1.png) |
|  | **Ancho** | `Parent.Width - (N * 2)` |  |
| **C** rellena el alto del elemento primario, con un margen de *N* | **SÍ** | `N` | ![Ejemplo de alto relleno de C de primario](media/create-responsive-layout/c2.png) |
|  | **Alto** | `Parent.Height - (N * 2)` |  |
| **C** alineado con el borde derecho del elemento primario, con el margen de *N* | **X1** | `Parent.Width - (C.Width + N)` | ![Ejemplo de alineación de C con el borde del elemento primario](media/create-responsive-layout/c3.png) |
| **C** alineado con el borde inferior del elemento primario, con el margen de *N* | **SÍ** | `Parent.Height - (C.Height + N)` | ![Ejemplo de alineación de C con el borde del elemento primario](media/create-responsive-layout/c4.png) |
| **C** centrado horizontalmente en el elemento primario | **X1** | `(Parent.Width - C.Width) / 2` | ![Ejemplo de C centrado horizontalmente en el elemento primario](media/create-responsive-layout/c5.png) |
| **C** centrado verticalmente en el elemento primario | **SÍ** | `(Parent.Height - C.Height) / 2` | ![Ejemplo de C centrado verticalmente en el elemento primario](media/create-responsive-layout/c6.png) |

| Relación entre C y D | Propiedad | Fórmula | Ilustración |
|--|--|--|--|
| **C** alineada horizontalmente con **d** y el mismo ancho que **d** | **X1** | `D.X` | ![Ejemplo de patrón](media/create-responsive-layout/d1.png) |
|  | **Ancho**    | `D.Width` |  |
| **C** alineada verticalmente con **d** y el mismo alto que **d**  | **SÍ** | `D.Y` | ![Ejemplo de patrón](media/create-responsive-layout/d2.png) |
|  | **Alto** | `D.Height` |  |
| Borde derecho de **C** alineado con el borde derecho de **D** | **X1** | `D.X + D.Width - C.Width` | ![Ejemplo de patrón](media/create-responsive-layout/d3.png) |
| Borde inferior de **C** alineado con el borde inferior de **D** | **SÍ** | `D.Y + D.Height - C.Height` | ![Ejemplo de patrón](media/create-responsive-layout/d4.png) |
| **C** centrado horizontalmente con respecto a **D** | **X1** | `D.X + (D.Width - C.Width) / 2`  | ![Ejemplo de patrón](media/create-responsive-layout/d5.png) |
| **C** centrado verticalmente con relación a **D** | **SÍ** | `D.Y + (D.Height - C.Height) /2` | ![Ejemplo de patrón](media/create-responsive-layout/d6.png) |
| **C** situado a la derecha de **D** con un espacio de N | **X1** | `D.X + D.Width + N` | ![Ejemplo de patrón](media/create-responsive-layout/d7.png) |
| **C** situado debajo de **D** con un espacio de *N*             | **SÍ** | `D.Y + D.Height + N` | ![Ejemplo de patrón](media/create-responsive-layout/d8.png) |
| **C** rellena el espacio entre **D** y el borde derecho del elemento primario | **X1** | `D.X + D.Width` | ![Ejemplo de patrón](media/create-responsive-layout/d9.png) |
|  | **Ancho** | `Parent.Width - C.X` |  |
| **C** rellena el espacio entre **D** y el borde inferior del elemento primario | Y | `D.Y + D.Height` | ![Ejemplo de patrón](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>Diseño jerárquico

A medida que se crean pantallas que contienen más controles, se volverá más cómodo (o incluso necesario) para colocar los controles en relación con un control primario, en lugar de con respecto a la pantalla o un control relacionado. Al organizar los controles en una estructura jerárquica, puede hacer que las fórmulas sean más fáciles de escribir y mantener.

### <a name="galleries"></a>Galerías

Si usa una galería en la aplicación, deberá diseñar los controles dentro de la plantilla de la galería. Puede colocar estos controles escribiendo fórmulas que usan el operador **Parent** , que hará referencia a la plantilla de la galería. En las fórmulas de los controles de una plantilla de la galería, use las propiedades **Parent. TemplateHeight** y **Parent. TemplateWidth** ; No use **Parent. width** y **Parent. Height**, que hacen referencia al tamaño total de la galería.

![Galería vertical que muestra el ancho y el alto de la plantilla](media/create-responsive-layout/gallery-vertical.png)

### <a name="container-control"></a>Control contenedor

Puede usar una característica experimental, el control **contenedor** , como control primario. Para activar esta característica, seleccione Configuración de**aplicación** > de **archivo** > **Configuración avanzada**.

Considere el ejemplo de un encabezado en la parte superior de una pantalla. Es habitual tener un encabezado con un título y varios iconos con los que los usuarios puedan interactuar. Puede crear este encabezado mediante el control **contenedor** , que contiene un control **etiqueta** y dos controles **Icon** :

![Ejemplo de encabezado con un grupo](media/create-responsive-layout/header-group.png)

Establezca las propiedades de estos controles en estos valores:

| Propiedad | Encabezado | MENU | cercanos | Título |
|--|--|--|--|--|
| **X1** | `0`  | `0` | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **SÍ** | `0` | `0` | `0` | `0` |
| **Ancho**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **Alto** | `64` | `Parent.Height` | `Parent.Height` | `Parent.Height` |

Para el control de encabezado `Parent` , hace referencia a la pantalla. Para los demás, `Parent` hace referencia al control de **encabezado** .

Una vez escritas estas fórmulas, puede ajustar el tamaño o la posición del control de **encabezado** cambiando las fórmulas de sus propiedades. Los tamaños y las posiciones de los controles secundarios se ajustarán automáticamente en consecuencia.

### <a name="components"></a>Componentes

Si usa otra característica experimental, denominada componentes, puede crear bloques de creación y volver a usarlos en toda la aplicación. Al igual que con el control **contenedor** , los controles que se colocan dentro de un componente deben basar `Parent.Width` sus fórmulas de posición y tamaño en y `Parent.Height`, que hacen referencia al tamaño del componente. Más información: [Cree un componente](create-component.md).

## <a name="adapting-layout-for-device-size-and-orientation"></a>Adaptación del diseño para el tamaño y la orientación del dispositivo

Hasta ahora, ha aprendido a usar fórmulas para cambiar el tamaño de cada control en respuesta al espacio disponible, manteniendo los controles alineados entre sí. Pero es posible que desee o necesite realizar cambios de diseño más significativos en respuesta a diferentes tamaños y orientaciones de dispositivo. Cuando un dispositivo se gira de la orientación vertical a la horizontal, por ejemplo, puede que desee cambiar de un diseño vertical a uno horizontal. En un dispositivo más grande, puede presentar más contenido o reorganizarlo para proporcionar un diseño más atractivo. En un dispositivo más pequeño, es posible que tenga que dividir el contenido en varias pantallas.

### <a name="device-orientation"></a>Orientación del dispositivo

Las fórmulas predeterminadas para las propiedades de **ancho** y **alto** de una pantalla, como en este tema descrito anteriormente, no proporcionarán necesariamente una buena experiencia si un usuario gira un dispositivo. Por ejemplo, una aplicación diseñada para un teléfono en orientación vertical tiene un **DesignWidth** de 640 y un **DesignHeight** de 1136. La misma aplicación en un teléfono con orientación horizontal tendrá estos valores de propiedad:

- La propiedad **ancho** de la pantalla se establece `Max(App.Width; App.DesignWidth)`en. El **ancho** de la aplicación (1136) es mayor que su **DesignWidth** (640), por lo que la fórmula se evalúa como 1136.
- La propiedad **alto** de la pantalla se establece `Max(App.Height; App.DesignHeight)`en. El **alto** de la aplicación (640) es menor que el de **DesignHeight** (1136), por lo que la fórmula se evalúa como 1136.

Con un **alto** de pantalla de 1136 y un alto de dispositivo (en esta orientación) de 640, el usuario debe desplazar la pantalla verticalmente para mostrar todo su contenido, lo que podría no ser la experiencia que desea.

Para adaptar las propiedades de **ancho** y **alto** de la pantalla a la orientación del dispositivo, puede usar estas fórmulas:

**Ancho** = `Max(App.Width; If(App.Width < App.Height; App.DesignWidth; App.DesignHeight))`

**Alto** = `Max(App.Height; If(App.Width < App.Height; App.DesignHeight; App.DesignWidth))`

Estas fórmulas intercambian los valores de **DesignWidth** y **DesignHeight** de la aplicación, en función de si el ancho del dispositivo es menor que el alto (orientación vertical) o superior al alto (orientación horizontal).

Después de ajustar las fórmulas de **ancho** y **alto** de la pantalla, es posible que también desee reorganizar los controles de la pantalla para usar mejor el espacio disponible. Por ejemplo, si cada uno de los dos controles ocupa la mitad de la pantalla, puede apilarlos verticalmente en vertical, pero organizarlos en paralelo en horizontal.

Puede usar la propiedad **orientación** de la pantalla para determinar si la pantalla está orientada vertical u horizontalmente.

> [!NOTE]
> En la orientación horizontal, los controles **superior** e **inferior** aparecen como controles izquierdo y derecho.

| Control | Propiedad | Fórmula |
|--|----------|---|
| **Esquina superior** | **X1** | `0` |
| **Esquina superior** | **SÍ** | `0` |
| **Esquina superior** | **Ancho** | `If(Parent.Orientation = Layout.Vertical; Parent.Width; Parent.Width / 2)` |
| **Esquina superior** | **Alto**   | `If(Parent.Orientation = Layout.Vertical; Parent.Height / 2; Parent.Height)` |
| **Inferiores** | X | `If(Parent.Orientation = Layout.Vertical; 0; Upper.X + Upper.Width)`  |
| **Inferiores** | Y | `If(Parent.Orientation = Layout.Vertical; Upper.Y + Upper.Height; 0)` |
| **Inferiores** | **Ancho** | `Parent.Width - Lower.X` |
| **Inferiores** | **Alto** | `Parent.Height - Lower.Y` |

![expresiones para adaptar una orientación vertical](media/create-responsive-layout/portrait.png)

![expresiones para adaptar una orientación horizontal](media/create-responsive-layout/landscape.png)

### <a name="screen-sizes-and-breakpoints"></a>Tamaños de pantalla y puntos de interrupción

Puede ajustar el diseño en función del tamaño del dispositivo. La propiedad **tamaño** de la pantalla clasifica el tamaño actual del dispositivo. El tamaño es un entero positivo; el tipo ScreenSize proporciona constantes con nombre para facilitar la lectura. En esta tabla se enumeran las constantes:

| constante              | Value | Tipo de dispositivo típico (con la configuración de la aplicación predeterminada) |
|-----------------------|-------|--------------------------------------------------|
| Filtrar. pequeño      | 1     | Número                                            |
| ScreenSize. Medium     | 2     | Tableta, mantenida en vertical                          |
| Filtrar. grande      | 3     | Tableta, conservada horizontalmente                        |
| ScreenSize. ExtraLarge | 4     | Equipo de escritorio                                 |

Use estos tamaños para tomar decisiones sobre el diseño de la aplicación. Por ejemplo, si desea que un control esté oculto en un dispositivo de tamaño de teléfono pero visible en caso contrario, puede establecer la propiedad **visible** del control en esta fórmula:

`Parent.Size >= ScreenSize.Medium`

Esta fórmula se evalúa como **true** cuando el tamaño es medio o mayor y **false** en caso contrario.

Si desea que un control ocupe una fracción diferente del ancho de la pantalla en función del tamaño de la pantalla, establezca la propiedad **ancho** del control en esta fórmula:

```powerapps-comma
Parent.Width *  
    Switch(Parent.Size;  
        ScreenSize.Small; 0,5;  
        ScreenSize.Medium; 0,3;  
        0,25)
```
Esta fórmula establece el ancho del control en la mitad del ancho de la pantalla en una pantalla pequeña, tres décimas de ancho de pantalla en una pantalla mediana y un cuarto del ancho de la pantalla en todas las demás pantallas.

## <a name="custom-breakpoints"></a>Puntos de interrupción personalizados

La propiedad de **tamaño** de la pantalla se calcula comparando la propiedad **ancho** de la pantalla con los valores de la propiedad **SizeBreakpoints** de la aplicación. Esta propiedad es una tabla de números de una sola columna que indica los puntos de interrupción de ancho que separan los tamaños de pantalla con nombre:

En una aplicación creada para tabletas o Web, el valor predeterminado de la propiedad **SizeBreakpoints** de la aplicación es **[600; 900; 1200]** . En una aplicación creada para teléfonos, el valor es **[1200; 1800; 2400]** . (Los valores de las aplicaciones de teléfono se duplican porque estas aplicaciones usan coordenadas que son, de hecho, el doble de las coordenadas usadas en otras aplicaciones).

![valores predeterminados de la propiedad app. SizeBreakpoints](media/create-responsive-layout/default-breakpoints.png)

Puede personalizar los puntos de interrupción de la aplicación cambiando los valores de la propiedad **SizeBreakpoints** de la aplicación. Seleccione **aplicación** en la vista de árbol, seleccione **SizeBreakpoints** en la lista de propiedades y, a continuación, edite los valores en la barra de fórmulas. Puede crear tantos puntos de interrupción como necesite la aplicación, pero solo los tamaños del 1 al 4 se corresponden con los tamaños de pantalla con nombre. En las fórmulas, puede hacer referencia a tamaños más allá de extragrande por sus valores numéricos (5, 6, etc.).

También puede especificar menos puntos de interrupción. Por ejemplo, la aplicación podría necesitar solo tres tamaños (dos puntos de interrupción), por lo que los tamaños de pantalla posibles serán pequeño, mediano y grande.

## <a name="known-limitations"></a>Limitaciones conocidas

El lienzo de creación no responde a las fórmulas de ajuste de tamaño creadas. Para probar el comportamiento de respuesta, guarde y publique la aplicación y, a continuación, ábrala en dispositivos o en ventanas del explorador de distintos tamaños y orientaciones.

Si escribe expresiones o fórmulas en las propiedades **X**, **y**, **ancho**y **alto** de un control, sobrescribirá esas expresiones o fórmulas si posteriormente arrastra el control a una ubicación diferente o cambia el tamaño del control arrastrando su borde.
