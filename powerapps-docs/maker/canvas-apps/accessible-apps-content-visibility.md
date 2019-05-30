---
title: Mostrar u ocultar el contenido de las tecnologías de asistencia en las aplicaciones de lienzo | Microsoft Docs
description: Técnicas para mostrar contenido únicamente a los usuarios de visión reducidos o únicamente a los usuarios de lector de pantalla sólo para aplicaciones de lienzo
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c680767bc6a56f0596eba03dd555c1c9a0205346
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61550097"
---
# <a name="show-or-hide-content-from-assistive-technologies-for-canvas-apps"></a>Mostrar u ocultar el contenido de las tecnologías de asistencia para las aplicaciones de lienzo

En la mayoría de los casos, todos los usuarios puedan tener acceso a todo el contenido, pero en ocasiones es posible que desee mostrar contenido únicamente a los usuarios de visión reducidos o solo a los usuarios de lector de pantalla. Por ejemplo, es posible que desea que los usuarios de lector de pantalla solo para tener acceso a las descripciones de las tendencias del gráfico que sean evidentes para los usuarios de visión reducidos. También puede ocultar un icono de usuarios de lector de pantalla si lo describe una etiqueta adyacente. Otra descripción en el icono sería innecesariamente detallado.

## <a name="hide-content-from-all-users"></a>Ocultar el contenido de todos los usuarios

* Establecer **[Visible](controls/properties-core.md)** en false.

## <a name="hide-content-from-sighted-users-and-show-it-to-screen-reader-users"></a>Ocultar el contenido de los usuarios de visión reducidos y mostrarla a los usuarios de lector de pantalla

Use cualquiera de estas técnicas:

* Establecer **[tamaño](controls/properties-text.md)** en 0.
* Establecer **[ancho](controls/properties-size-location.md)** y **[alto](controls/properties-size-location.md)** en 1.
* Establecer  **[X](controls/properties-size-location.md)** ,  **[Y](controls/properties-size-location.md)** , o ambas propiedades tal que el control está fuera de la pantalla.
* Establecer **[Color](controls/properties-color-border.md)** y las propiedades relacionadas con transparente.
* Colocar un rectángulo **[forma](controls/control-shapes-icons.md)** anteriormente el contenido y el conjunto **[rellenar](controls/properties-color-border.md)** en el mismo color que el color de fondo de la pantalla.

> [!NOTE]
> Los usuarios todavía pueden usar un teclado para tener acceso a un control interactivo, como un  **[botón](controls/control-button.md)** , aunque se oculte utilizando una de las técnicas de la lista anterior. Establecer **[TabIndex](controls/properties-accessibility.md)** en -1 si desea impedir que los usuarios acceso al control presionando la tecla Tab.

## <a name="hide-content-from-screen-reader-users-and-show-it-to-sighted-users"></a>Ocultar el contenido de los usuarios de lector de pantalla y mostrarla a los usuarios de visión reducidos

* Para  **[imagen](controls/control-image.md)** ,  **[icono](controls/control-shapes-icons.md)** , y **[forma](controls/control-shapes-icons.md)** establecer controles, **[AccessibleLabel](controls/properties-accessibility.md)** en la cadena vacía "".

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre [propiedades de accesibilidad](controls/properties-accessibility.md) de controles en las aplicaciones de lienzo.
