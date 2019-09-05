---
title: Fórmulas de comportamiento para componentes | Microsoft Docs
description: Desencadenar una aplicación para realizar una o más tareas cuando se produce una acción basada en componentes.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8ec4edd835f12fb6fccf04ba0fb27f1e755cac0
ms.sourcegitcommit: ea3ab5926541c60a9e7c17f52f937c9812d48c71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2019
ms.locfileid: "70310062"
---
# <a name="behavior-formulas-for-components"></a>Fórmulas de comportamiento para componentes

> [!IMPORTANT]
> Esta característica sigue siendo experimental y está deshabilitada de forma predeterminada. Para obtener más información, vea [características experimentales y de vista previa](working-with-experimental.md).

Especifique una o varias [fórmulas de comportamiento](working-with-formulas-in-depth.md) que se ejecuten cuando un evento desencadene un cambio en instancias de componente. Por ejemplo, establezca la propiedad **onreset** de un componente en una o varias fórmulas que realicen la inicialización, borren la entrada y restablezcan los valores cuando la función de **restablecimiento** se ejecute en las instancias del componente.

## <a name="onreset"></a>OnReset

Con un componente seleccionado, seleccione **onreset** en la lista desplegable de propiedades (en el lado derecho de la barra de fórmulas) y, a continuación, escriba una o varias fórmulas.

> [!div class="mx-imgBorder"]
> ![Ejemplo de onreset](./media/component-behavior/example-onreset.png)

Para probar **RESET**, configure un control para restablecer el componente. Por ejemplo, establezca la propiedad **alseleccionar** de un botón en esta fórmula: **Restablecer** (*ComponentName*)

> [!div class="mx-imgBorder"]
> ![Botón restablecer](./media/component-behavior/reset-button.png)
