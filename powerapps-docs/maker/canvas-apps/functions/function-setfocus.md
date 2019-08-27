---
title: Función SetFocus | Microsoft Docs
description: Información de referencia de la función SetFocus en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fce0148e77432aa136a6279eb7fb69c0ca3b0846
ms.sourcegitcommit: de77b6d5f77e84961fff9a399622ba8eeb48d4c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037063"
---
# <a name="setfocus-function-in-powerapps"></a>Función SetFocus en PowerApps
Mueve el foco de entrada a un control concreto. 

## <a name="description"></a>DESCRIPCIÓN
La función **SetFocus** proporciona a un control el foco de entrada.  El control recibe las pulsaciones de teclas del usuario, lo que les permite escribir en un control entrada de texto o usar la tecla *entrar* para seleccionar un botón.  El usuario también puede usar la tecla *Tab* , tocar, Mouse u otro gesto para desplazar el foco de entrada. El comportamiento de la tecla *Tab* se rige por la [propiedad **TabIndex** ](../controls/properties-accessibility.md).

Utilice la función **SetFocus** para establecer el foco cuando (cada uno de ellos tiene un ejemplo a continuación):
- control de entrada recién expuesto o habilitado, para guiar al usuario en lo que viene después y para una entrada de datos más rápida.
- un formulario se valida, para centrarse y mostrar el control de entrada infractor para una resolución rápida.
- se muestra una pantalla para centrar el primer control de entrada con la propiedad **visible** de la [**pantalla**](../controls/control-screen.md).

El control con el foco puede ser visualmente diferente en función de las propiedades [**FocusedBorderColor**](../controls/properties-color-border.md) y [**FocusedBorderThickness**](../controls/properties-color-border.md) .

## <a name="limitatoins"></a>Limitatoins

**SetFocus** solo se puede usar con:
- [**Button**](../controls/control-button.md) (control)
- Control de [**icono**](../controls/control-shapes-icons.md)
- Control de [**imagen**](../controls/control-image.md)
- Control [**Etiqueta**](../controls/control-text-box.md)
- [**TextInput**](../controls/control-text-input.md) (control)

No se puede establecer el foco en los controles que se encuentran dentro de un control de [**Galería**](../controls/control-gallery.md) , un control de [**formulario de edición**](../controls/control-form-detail.md) o un [componente](../create-component.md).  **SetFocus** se puede usar con un control en una pantalla de scrollbale.

Solo puede establecer el foco en los controles de la misma pantalla que la fórmula que contiene la llamada de **SetFocus** .

El intento de establecer el foco en un control que tiene la propiedad [**DisplayMode**](../controls/properties-core.md) establecida en deshabilitado no tiene ningún efecto.  El foco permanecerá en el lugar en el que se encontraba anteriormente.

En Apple iOS, el teclado en pantalla solo se mostrará automáticamente si se inició **SetFocus** mediante una acción de usuario directa.  Por ejemplo, al invocar a partir de la propiedad alseleccionar de un botón, se mostrará el teclado en pantalla, mientras que al invocar desde la vista **visible** de una pantalla no. 

Solo puede usar **SetFocus** en fórmulas de [comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**SetFocus** ( *Control* )

* *Control* (se requiere).  Control que se va a asignar al foco de entrada.

## <a name="examples"></a>Ejemplos

### <a name="focus-on-a-newly-exposed-or-enabled-input-control"></a>Centrarse en un control de entrada recién expuesto o habilitado

Muchos carros de la compra permiten al cliente usar la dirección de envío como dirección de facturación, lo que evita la necesidad de escribir la misma información dos veces.  Si se desea una dirección de facturación diferente, los cuadros de entrada de texto de dirección de facturación están habilitados y resulta útil guiar al cliente a estos controles recién habilitados para una entrada de datos más rápida.  

![Animación de la elección de usar una dirección de facturación personalizada, con el foco desplazado al control de entrada de nombre de facturación como resultado, desactivando la sincronización automática con las direcciones de envío](media/function-setfocus/shipping-billing.gif)

Hay muchas fórmulas en juego aquí, pero la que mueve el foco está en la propiedad **AlDesactivar** del control de **casilla** :

```powerappa-dot
SetFocus( BillingName ) 
```

La tecla *Tab* también se puede usar para cambiar el foco rápidamente de un campo a otro.  Para ilustrar mejor, la tecla *Tab* no se utilizó en la animación.

Para crear este ejemplo:
1. Cree una nueva aplicación.
1. Agregue [controles **etiqueta** ](../controls/control-text-box.md) con el texto "dirección de envío", "nombre:", "dirección:", "dirección de facturación", "nombre:" y "dirección:" y colóquelos tal como se muestra en la animación.
1. Agregue un [control **entrada de texto** ](../controls/control-text-input.md) y cambie su nombre por **ShippingName**.
1. Agregue un [control **entrada de texto** ](../controls/control-text-input.md) y cambie su nombre por **ShippingAddress**.
1. Agregue un [control **casilla** ](../controls/control-check-box.md) y cambie su nombre a **SyncAddresses**.
1. Establezca la propiedad **texto** de este control en la fórmula `"Use Shipping address as Billing address"`.
1. Agregue un [control **entrada de texto** ](../controls/control-text-input.md) y cambie su nombre por **BillingName**.
1. Establezca la propiedad **predeterminada** de este control en la fórmula `ShippingName`.
1. Establezca la propiedad **DisplayMode** de este control en la fórmula `If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )`.  Esto habilitará o deshabilitará automáticamente este control según el estado del control de casilla.
1. Agregue un [control **entrada de texto** ](../controls/control-text-input.md) y cambie su nombre por **BillingAddress**.
1. Establezca la propiedad **predeterminada** de este control en la fórmula `ShippingAddress`.
1. Establezca la propiedad **DisplayMode** de este control en la fórmula `If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )`.  Esto habilitará o deshabilitará automáticamente este control según el estado del control de casilla.
1. Establezca la propiedad **default** de la casilla de verificación en la `true`fórmula.  De forma predeterminada, la dirección de facturación usará el mismo valor que la dirección de envío.
1. Establezca la propiedad alcomprobar de la casilla en la fórmula `Reset( BillingName ); Reset( BillingAddress )`.  Si el usuario decide sincronizar las direcciones de envío y facturación, se borrará cualquier entrada del usuario en los campos de dirección de facturación, lo que permitirá que las propiedades predeterminadas de cada una de ellas extraigan los valores de los campos de dirección de envío correspondientes.
1. Establezca la propiedad **AlDesactivar** de la casilla de verificación en la `SetFocus( BillingName )`fórmula.  Si el usuario elige tener una dirección de facturación diferente, se moverá el foco al primer control en la dirección de facturación.  Los controles ya se habrán habilitado debido a sus propiedades **DisplayMode** .

### <a name="focus-on-validation-issues"></a>Céntrese en los problemas de validación

> [!NOTE]
> Aunque este ejemplo parece ser un control de **formulario de edición** , desafortunadamente el control no admite todavía **SetFocus** .  En su lugar, en este ejemplo se usa una pantalla desplazable para hospedar los controles de entrada.

Al validar un formulario, puede resultar útil no solo mostrar un mensaje si hay un problema, sino también tener el usuario en el campo que causa el error.  Puede ser especialmente útil si el campo en cuestión se desplaza fuera de la pantalla y no es visible.

![Animación de la validación de un formulario de entrada de datos y de que no solo se muestra un mensaje, sino que también se establece el foco de entrada en el control de entrada infractor, incluso si se desplaza fuera de la pantalla.](media/function-setfocus/scrollable-screen.gif)

En esta animación, el botón de validación se presiona repetidamente hasta que todos los campos se han rellenado correctamente.  Tenga en cuenta que el puntero del mouse no se desplaza hacia abajo desde la parte superior de la pantalla.   En su lugar, la función **SetFocus** ha desplazado el foco de entrada al control que requiere atención con esta fórmula:

```powerapps-dot
If( IsBlank( Name ), 
        Notify( "Name requires a value", Error ); SetFocus( Name ),
    IsBlank( Street1 ), 
        Notify( "Street Address 1 requires a value", Error ); SetFocus( Street1 ),
    IsBlank( Street2 ), 
        Notify( "Street Address 2 requires a value", Error ); SetFocus( Street2 ),
    IsBlank( City ), 
        Notify( "City requires a value", Error ); SetFocus( City ),
    IsBlank( County ), 
        Notify( "County requires a value", Error ); SetFocus( County ),
    IsBlank( StateProvince ), 
        Notify( "State or Province requires a value", Error ); SetFocus( StateProvince ),
    IsBlank( PostalCode ), 
        Notify( "Postal Code requires a value", Error ); SetFocus( PostalCode ),
    IsBlank( Phone ), 
        Notify( "Contact Phone requires a value", Error ); SetFocus( Phone ),
    Notify( "Form is Complete", Success )
)
```

Para crear este ejemplo:
1. Cree una nueva aplicación de teléfono en blanco.
1. En el menú **Insertar** , seleccione **nueva pantalla**y, a continuación, seleccione desplazable.
1. En la sección central de la pantalla, agregue controles de **entrada de texto** yasígneles un nombre, **Street1**, **calle2**, **City**, **County**, **StateProvince**, PostalCode y **teléfono**. Agregue controles de **etiqueta** por encima de cada uno de ellos para identificar los campos.  Es posible que tenga que cambiar el tamaño de la sección si no es lo suficientemente larga como para ajustarse a todos los controles.
1. Agregue un control [ **icono** ](../controls/control-shapes-icons.md) de marca de verificación en la parte superior de la pantalla, encima de la sección desplazable.  
1. Establezca la propiedad alseleccionar del control de icono en la fórmula `If( IsBlank( ...` indicada anteriormente.

### <a name="focus-when-displaying-a-screen"></a>Foco al mostrar una pantalla

> [!NOTE]
> Aunque este ejemplo parece ser un control de **formulario de edición** , el control no admite unforutnatley **SetFocus** todavía.  En su lugar, en este ejemplo se usa una pantalla desplazable para hospedar los controles de entrada.

De forma similar a exponer un control de entrada, cuando se muestra una pantalla de entrada de datos resulta útil centrar el primer control de entrada para una entrada de datos más rápida.

![Animación que muestra una comparación en paralelo del uso de SetFocus en lugar de usarlo cuando se muestra una pantalla de entrada de datos](media/function-setfocus/visible-setfocus.gif)

En esta animación, la pantalla de entrada de datos de la izquierda no usa **SetFocus**.  Cuando no se muestra, no hay ningún control de entrada que tenga el foco, lo que requiere que el usuario realice una tabulación, toque, mouse o use otro medio para centrar el campo de **nombre** antes de que se pueda escribir en él un valor.

A la derecha, tenemos exactamente la misma aplicación con la propiedad **visible** de la pantalla de entrada de datos establecida en esta fórmula:

```powerapps-dot
SetFocus( Name )
```

Esto establece el foco en el campo de **nombre** automáticamente.  El usuario puede empezar a escribir y tabular inmediatamente entre los campos sin ninguna acción anterior requerida.

Para crear este ejemplo:
1. Cree la aplicación "Céntrese en los problemas de validación" anterior.
1. En esta pantalla, establezca la propiedad **divisible** en la fórmula `SetFocus( Name )`.
1. Agregue una segunda pantalla.
1. Agregue un [control de **botón** ](../controls/control-button.md).
1. Establezca la propiedad alseleccionar de este control en la fórmula `Navigate( Screen1 )`.
1. Obtenga una vista previa de la aplicación en esta pantalla.  Presione el botón.  Se evaluará la fórmula **divisible** y el campo **nombre** estará automáticamente en el foco.
