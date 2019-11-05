---
title: Propiedades de accesibilidad de las aplicaciones de Canvas | Microsoft Docs
description: Información de referencia sobre propiedades como TabIndex e ToolTip
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/26/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2e11de4af02347154c65500659df94a6b2183540
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73539430"
---
# <a name="accessibility-properties-for-canvas-apps"></a>Propiedades de accesibilidad de las aplicaciones de Canvas

Configuración de propiedades que contribuyen a formas alternativas de interacción con los controles adecuadas para los usuarios con discapacidades.

## <a name="properties"></a>Propiedades

**AccessibleLabel**: etiqueta para lectores de pantalla. Un valor vacío para los controles Imagen, Icono y Forma hará que el lector de pantalla no los vea y los trate como adornos.

En **directo** : cómo los lectores de pantalla deben anunciar cambios en el contenido. Solo está disponible en el control **[etiqueta](control-text-box.md)** .

* Cuando se establece en **OFF**, el lector de pantalla no anuncia cambios.
* Cuando se establece en **educado**, el lector de pantalla termina de hablar antes de anunciar los cambios que se produjeron mientras estaba hablando el lector de pantalla.
* Cuando se establece en **assertive**, el lector de pantalla se interrumpe para anunciar los cambios que se produjeron mientras estaba hablando el lector de pantalla.

Obtenga información sobre cómo [anunciar cambios dinámicos con regiones activas](../accessible-apps-live-regions.md).

**TabIndex** : determina si el control participa en la navegación con el teclado.

La navegación mediante el teclado es un aspecto importante de cualquier aplicación.  Para muchos, el teclado es más eficaz que usar la función táctil o un mouse y permite que los lectores de pantalla tengan discapacidades visuales.  El orden de navegación debe:
- Reflejar lo que se verá visualmente.
- Solo tiene una tabulación en los controles que son interactivos.
- Siga un orden intuitivo y luego hacia abajo "Z" o hacia abajo y después por orden "inverso-N".

Los requisitos anteriores se cumplirán con los valores de **TabIndex** predeterminados y se recomienda que no los cambie.  El valor predeterminado es lo que la mayoría de los usuarios esperan visualmente y funcionará bien con un lector de pantalla.  Sin embargo, puede haber casos en los que desee invalidar el valor predeterminado.  Use la propiedad **TabIndex** y el [control de **Grupo mejorado** ](https://powerapps.microsoft.com/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/) (experimental) para realizar ajustes en el orden de navegación.  

La propiedad **TabIndex** tiene dos valores recomendados:

| Valor de TabIndex | Comportamiento | Valor predeterminado para |
|----------------|----------|-------------|
| 0 | El control participa en la navegación con el teclado. | [**Botón**](control-button.md), [**entrada de texto**](control-text-input.md), [**cuadro combinado**](control-combo-box.md)y otros controles normalmente interactivos. |
| &minus;1 | El control no participa en la navegación con el teclado. | [**Etiqueta**](control-text-box.md), [**imagen**](control-image.md), [**icono**](control-shapes-icons.md)y otros controles que normalmente no son interactivos. |

Generalmente, el orden de navegación va de izquierda a derecha y de arriba abajo, en un patrón "Z". El orden se basa en los valores de **las propiedades X e y de** los controles. Si los controles se mueven dinámicamente en la pantalla (por ejemplo, al tener una fórmula para **X** o **Y** basada en un temporizador u otro control), el orden de navegación también cambiará dinámicamente.

Utilice el [control de **Grupo mejorado** ](https://powerapps.microsoft.com/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/) (experimental) para agrupar los controles que se deben navegar juntos o para crear columnas en un patrón "inverso-N".  En la parte superior del ejemplo siguiente, los campos de nombre están incluidos en un control de grupo mejorado, lo que hace que la navegación continúe antes de moverse.  En la parte inferior del ejemplo, no se usa ningún control de grupo y la navegación continúa hacia arriba y luego hacia abajo como normal, lo que no es intuitivo dado las agrupaciones de control. 

![Animación que muestra un control de grupo mejorado que hace que la navegación continúe dentro de un grupo antes de pasar a otro](media/properties-accessibility/enhanced-group.gif)

Del mismo modo, la tabulación de los contenedores, como los controles de [**formulario**](control-form-detail.md) y de [**Galería**](control-gallery.md) , navegará por todos los elementos del contenedor antes de continuar con el siguiente control fuera del contenedor.  

Los controles que tienen un valor de propiedad **visible** de *false* o un valor de propiedad **DisplayMode** de **Disabled** no se incluyen en la navegación.  

Al usar un explorador, el desplazamiento desde el último control de la pantalla se moverá a los controles integrados del explorador, como la dirección URL.  

> [!WARNING]
> Evite valores de **TabIndex** mayores que 0. En última instancia, los controles se representan en HTML en los que incluso el [W3C ha advertido](https://www.w3.org/TR/wai-aria-practices/#kbd_general_between) de que se recomienda encarecidamente que los autores no utilicen estos valores. Muchas herramientas HTML avisan de valores mayores que 0, al igual que el [Comprobador de aplicaciones](../accessibility-checker.md) cuando informa de la comprobación del orden de los elementos de la pantalla.  Todo por una buena razón: el uso de **TabIndex** de esta manera puede ser muy difícil de obtener y puede hacer que las tecnologías de asistencia como los lectores de pantalla no se puedan usar.
> 
> Cuando existen controles con **TabIndex** mayor que 0, los usuarios navegarán a los controles con valores de **TabIndex** cada vez mayores (1, después 2, etc.). Cuando los usuarios hayan navegado por todos los controles con valores de **TabIndex** positivos, finalmente navegarán a los controles con **TabIndex** de 0, incluidos los controles integrados del explorador. Cuando hay varios controles con el mismo **TabIndex**, su posición **X** e **y** determina su orden relativo.





