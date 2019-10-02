---
title: Fórmulas de comportamiento para componentes | Microsoft Docs
description: Desencadenar una aplicación para realizar una o más tareas cuando se produce una acción basada en componentes.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 9/30/2019
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: baf7e74581819b3ea21542f30f96a0a6f517c0d5
ms.sourcegitcommit: 60fd1792430b9f3da08ec161cb2277506d795e3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "71705045"
---
# <a name="behavior-formulas-for-components"></a>Fórmulas de comportamiento para componentes

> [!IMPORTANT]
> Esta característica sigue siendo experimental y está deshabilitada de forma predeterminada. Para obtener más información, vea [características experimentales y de vista previa](working-with-experimental.md).

Especifique una o varias [fórmulas de comportamiento](working-with-formulas-in-depth.md) que se ejecuten cuando un evento desencadene un cambio en instancias de componente. Por ejemplo, establezca la propiedad **onreset** de un componente en una o varias fórmulas que realicen la inicialización, borren la entrada y restablezcan los valores cuando la función de **restablecimiento** se ejecute en las instancias del componente.

## <a name="onreset"></a>OnReset

Con un componente maestro seleccionado, seleccione **onreset** en la lista desplegable de propiedades (en el lado izquierdo de la barra de fórmulas) y, a continuación, escriba una o varias fórmulas.

> [!div class="mx-imgBorder"]
> @no__t 0OnReset ejemplo @ no__t-1

Para probar **RESET**, configure un control para restablecer el componente. Por ejemplo, establezca la propiedad **alseleccionar** de un botón en esta fórmula: **RESET**(*ComponentName*).

### <a name="example---reset-timer"></a>Ejemplo: restablecer temporizador

> [!div class="mx-imgBorder"]
> @no__t 0OnReset ejemplo @ no__t-1

En este componente selector de hora, se usan dos variables para mostrar la hora _selectedHour y _selectedMinute. Cuando el selector se restablece, estas variables se deben restablecer a un valor predeterminado, por ejemplo, 12: 305.  La propiedad onreset del componente tiene la siguiente fórmula: **Set (_selectedHour, 12); Set (_selectedMinute)**

Para desencadenar el restablecimiento, vaya a una pantalla e inserte una instancia del componente. Agregue un botón y configure alseleccionar del botón para llamar a **RESET (TimerComponent_instance)** para desencadenar onreset.

> [!div class="mx-imgBorder"]
> @no__t: botón 0Reset @ no__t-1

## <a name="update-onreset-using-custom-property"></a>Actualizar onreset mediante la propiedad personalizada

Además de restablecer una instancia de componente desde fuera del componente, hay otro método para desencadenar el restablecimiento desde el interior. "**Raise onreset When Changes Values**" es una opción al crear una propiedad de entrada personalizada y permite que los cambios de valor de esta propiedad desencadenen el restablecimiento del componente. Este método está diseñado para establecer y restablecer el valor predeterminado fácilmente. 

> ![Ejemplo de onreset](./media/component-behavior/property-trigger.png)

### <a name="example"></a>Ejemplo

> [!div class="mx-imgBorder"]
> @no__t 0OnReset ejemplo @ no__t-1

Este es un ejemplo de revisión de los números de pedido y la actualización de los números. El componente numérico hacia arriba y hacia abajo se usa para aumentar o disminuir el número de pedidos. Al seleccionar la galería de la izquierda, se restablece el número predeterminado de componentes numéricos hacia arriba y hacia abajo para mostrar el número de orden de la herramienta seleccionada. "**Elevar el restablecimiento cuando cambia el valor**" hace posible restablecer el valor predeterminado cuando cambia la entrada. 

Para ello, Active "**elevar el restablecimiento cuando cambia el valor**" de la propiedad de entrada predeterminada. **Alreset** del componente se establece en **set (_NumericValue, ' Numeric UpDown '). DefaultValue)** . _numericValue es la variable para almacenar el valor del valor de pedido actual. Y establecen el **valor predeterminado** del control entrada de texto en **si (esblanco (_numericValue), ' numérico verticalmente '. DefaultValue, _numericValue)** . 
