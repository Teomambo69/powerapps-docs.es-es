---
title: Propiedades de accesibilidad | Microsoft Docs
description: Información de referencia acerca de propiedades como TabIndex y Tooltip
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/26/2017
ms.author: fikaradz
ms.openlocfilehash: 062267a93ca625513d0280c753eefaaacd743811
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="accessibility-properties-in-powerapps"></a>Propiedades de accesibilidad en PowerApps
Configuración de propiedades que contribuyen a formas alternativas de interacción con los controles adecuadas para los usuarios con discapacidades.

### <a name="properties"></a>Propiedades
**AccessibleLabel**: etiqueta para lectores de pantalla. Un valor vacío para los controles Imagen, Icono y Forma hará que el lector de pantalla no los vea y los trate como adornos.

**TabIndex**: orden de navegación del teclado en relación con otros controles.

El valor predeterminado cero especifica el orden de tabulación predeterminado, en función de la coordenada XY del control.  Establecer un valor mayor que cero moverá el orden de tabulación del control por delante de todos los controles con los valores predeterminados.  Un control con un valor TabIndex de 2 estará precedido por uno con un valor TabIndex de 3 o superior cuando se aplique la tabulación.

Tenga en cuenta que los contenedores como los controles Form y Gallery siempre tabularán todos los elementos del contenedor antes de continuar con los controles fuera del contenedor.  El orden de tabulación del contenedor es el valor más bajo de TabIndex de un control secundario.

Si se establece TabIndex en -1, se deshabilitará el acceso mediante tabulación al control; en el caso de los controles Imágenes, Iconos y Formas, se convertirán en elementos no interactivos.
