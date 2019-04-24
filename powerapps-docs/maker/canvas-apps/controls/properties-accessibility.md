---
title: Propiedades de accesibilidad para las aplicaciones de lienzo | Microsoft Docs
description: Información de referencia sobre las propiedades como TabIndex y Tooltip
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/26/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5fa8b6fecdf690114cbf6a0945f2dfec66b067c3
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560424"
---
# <a name="accessibility-properties-for-canvas-apps"></a>Propiedades de accesibilidad para las aplicaciones de lienzo

Configuración de propiedades que contribuyen a formas alternativas de interacción con los controles adecuadas para los usuarios con discapacidades.

## <a name="properties"></a>Propiedades

**AccessibleLabel**: etiqueta para lectores de pantalla. Un valor vacío para los controles Imagen, Icono y Forma hará que el lector de pantalla no los vea y los trate como adornos.

**Live** : cómo los lectores de pantalla deben anunciar los cambios al contenido. Disponible solo en el **[etiqueta](control-text-box.md)** control.

* Cuando se establece en **desactivar**, el lector de pantalla no anuncia los cambios.
* Cuando se establece en **educados**, el lector de pantalla finalice antes de anunciar los cambios que se produjeron mientras el lector de pantalla ha estado hablando en términos.
* Cuando se establece en **Assertive**, interrumpe el lector de pantalla para anunciar los cambios que se produjeron mientras el lector de pantalla ha estado hablando.

Obtenga información sobre cómo [anunciar cambios dinámicos con las regiones activas](../accessible-apps-live-regions.md).

**TabIndex**: orden de navegación del teclado en relación con otros controles.

El valor predeterminado cero especifica el orden de tabulación predeterminado, en función de la coordenada XY del control.  Establecer un valor mayor que cero moverá el orden de tabulación del control por delante de todos los controles con los valores predeterminados.  Un control con un valor TabIndex de 2 estará precedido por uno con un valor TabIndex de 3 o superior cuando se aplique la tabulación.

Tenga en cuenta que los contenedores como los controles Form y Gallery siempre tabularán todos los elementos del contenedor antes de continuar con los controles fuera del contenedor.  El orden de tabulación del contenedor es el valor más bajo de TabIndex de un control secundario.

Si se establece TabIndex en -1, se deshabilitará el acceso mediante tabulación al control; en el caso de los controles Imágenes, Iconos y Formas, se convertirán en elementos no interactivos.
