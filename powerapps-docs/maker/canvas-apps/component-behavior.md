---
title: Fórmulas de comportamiento para componentes | Microsoft Docs
description: Realice una o varias tareas en la aplicación Canvas cuando se produzca una acción basada en componentes.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 28ea432e5d09684029f104d69f593e24dcc4cc14
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "77910995"
---
# <a name="behavior-formulas-for-components"></a>Fórmulas de comportamiento para componentes

> [!IMPORTANT]
> Esta característica todavía está en versión preliminar pública. Para obtener más información, vea [Características en versión preliminar y experimentales](working-with-experimental.md).

Especifique una o varias [fórmulas de comportamiento](working-with-formulas-in-depth.md) que se ejecuten cuando un evento desencadene un cambio en instancias de componente. 

Por ejemplo, establezca la propiedad **onreset** de un componente en una o varias fórmulas que realicen la inicialización, borrar entrada. Y restablecen los valores cuando se ejecuta la función de **restablecimiento** en las instancias del componente.

## <a name="onreset"></a>OnReset

Con un componente maestro seleccionado, seleccione **onreset** en la lista desplegable de propiedades (en el lado izquierdo de la barra de fórmulas) y, a continuación, escriba una o varias fórmulas.

> [!div class="mx-imgBorder"]
> ![ejemplo de onreset](./media/component-behavior/example-onreset.png)

Para probar **RESET**, configure un control para restablecer el componente. Por ejemplo, establezca la propiedad **alseleccionar** de un botón en esta fórmula: **RESET**(*ComponentName*).

### <a name="example---reset-timer"></a>Ejemplo: restablecer temporizador

> [!div class="mx-imgBorder"]
> ![ejemplo de onreset](./media/component-behavior/Resettimer.gif)

En este componente selector de hora, se usan dos variables para mostrar la hora _selectedHour y _selectedMinute. Cuando el selector se restablece, estas variables se deben restablecer a un valor predeterminado, por ejemplo, 12:12.  La propiedad onreset del componente tiene la siguiente fórmula: **set (_selectedHour, 12); Set (_selectedMinute, 12)**

Para desencadenar el restablecimiento, vaya a una pantalla e inserte una instancia del componente. Agregue un botón y configure alseleccionar del botón para llamar a **RESET (TimerComponent_instance)** para desencadenar onreset.

> [!div class="mx-imgBorder"]
> ![botón Restablecer](./media/component-behavior/reset-button.png)

## <a name="update-onreset-using-custom-property"></a>Actualizar onreset mediante la propiedad personalizada

Además de restablecer una instancia de componente desde fuera del componente, hay otro método para desencadenar el restablecimiento desde el interior. "**Generar onreset cuando cambia el valor**" es una opción al crear una propiedad de entrada personalizada. Y permite que los cambios de valor de esta propiedad desencadenen el restablecimiento del componente. Este método está diseñado para establecer y restablecer el valor predeterminado fácilmente. 

> ![Ejemplo de onreset](./media/component-behavior/property-trigger.png)

### <a name="example"></a>Ejemplo

> [!div class="mx-imgBorder"]
> ![ejemplo de onreset](./media/component-behavior/updateordernumber2.gif)

En el ejemplo anterior se muestra la revisión de los números de pedido y la actualización de los números. El componente numérico hacia arriba y hacia abajo se usa para aumentar o disminuir el número de pedidos. Al seleccionar la galería de la izquierda, se restablece el número predeterminado de componentes numéricos hacia arriba y hacia abajo para mostrar el número de orden de la herramienta seleccionada. "**Elevar el restablecimiento cuando cambia el valor**" hace posible restablecer el valor predeterminado cuando cambia la entrada. 

Para ello, Active "**elevar el restablecimiento cuando cambia el valor**" de la propiedad de entrada predeterminada. **Alreset** del componente está establecido en **set (_NumericValue, ' Numeric up '. DefaultValue)** . _numericValue es la variable para almacenar el valor del valor de pedido actual. Y establecen el **valor predeterminado** del control entrada de texto en **si (esblanco (_numericValue), ' numérico verticalmente '. DefaultValue, _numericValue)** . 

### <a name="see-also"></a>Vea también

- [Información general de los componentes de la aplicación Canvas](create-component.md)
- [Biblioteca de componentes de la aplicación Canvas](component-library.md)
