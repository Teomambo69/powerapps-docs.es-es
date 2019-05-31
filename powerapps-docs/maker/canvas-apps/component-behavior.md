---
title: Las fórmulas de comportamiento para los componentes | Microsoft Docs
description: Desencadenar una aplicación para llevar a cabo una o varias tareas cuando se produce una acción basada en componentes.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7275395a4c21afaebc60e9635461afc08f5e84a0
ms.sourcegitcommit: afe958805d8e1cfa4fdf02c7bceea947185f71f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66420323"
---
# <a name="behavior-formulas-for-components"></a>Fórmulas de comportamiento de componentes

> [!IMPORTANT]
> Esta característica está todavía experimental y está deshabilitado de forma predeterminada. Para obtener más información, consulte [características experimentales y de vista previa](working-with-experimental.md).

Especifique uno o más [fórmulas de comportamiento](working-with-formulas-in-depth.md) que se ejecutan cuando un evento desencadena un cambio en las instancias del componente. Por ejemplo, establezca un componente **OnReset** propiedad a una o más fórmulas que realizar la inicialización, Borrar entrada y restablecer los valores cuando el **restablecer** función se ejecuta en las instancias del componente.

## <a name="onreset"></a>OnReset ##

Con un componente seleccionado, seleccione **OnReset** en la lista desplegable de propiedades (en el lado derecho de la barra de fórmulas) y, a continuación, escriba una o más fórmulas.

> [!div class="mx-imgBorder"]
> ![OnReset ejemplo](./media/component-behavior/example-onreset.png)

Para probar **OnReset**, configurar un control para restablecer el componente. Por ejemplo, establecer el **OnSelect** propiedad de un botón en esta fórmula: **Restablecer**(*ComponentName*)

> [!div class="mx-imgBorder"]
> ![Botón Restablecer](./media/component-behavior/reset-button.png)
