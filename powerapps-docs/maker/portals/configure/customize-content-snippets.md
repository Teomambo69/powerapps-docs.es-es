---
title: Personalización del contenido mediante fragmentos de código en un portal | MicrosoftDocs
description: Obtenga información sobre cómo personalizar el contenido mediante fragmentos de código.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 362bbe27850e8e72d7af4b2fb32b42796334d579
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552828"
---
# <a name="customize-content-by-using-content-snippets"></a>Personalización del contenido mediante fragmentos de código

Los fragmentos de código son pequeños fragmentos de contenido editable que puede colocar un desarrollador en una plantilla de página, lo que permite que el contenido personalizable rellene cualquier parte del diseño de una página fácilmente. Los controles de fragmento de código, que son responsables de representar el contenido de los fragmentos de código en el portal orientado a la web, se colocan en una plantilla de página por parte de los desarrolladores.

## <a name="edit-snippets"></a>Editar fragmentos de código

Los fragmentos de código se pueden editar a través de la aplicación de administración del portal. La potencia principal del fragmento de código es el hecho de que se puede abstraer un poco de contenido (aparte de la copia principal de la página) y editarlo por separado, lo que permite básicamente que todo el contenido estático del sitio esté totalmente administrado por contenido y sea editable.

1. Abra la [aplicación administración del portal](configure-portal.md).

2.  Vaya a **portales** > **fragmentos de código de contenido**.

3.  Para crear un nuevo fragmento de código, seleccione **nuevo**.

4.  Para editar un fragmento de código existente, seleccione un **fragmento de contenido** existente en la cuadrícula.

Escriba valores para los campos siguientes:

| Nombre    | Descripción                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| Nombre    | Un desarrollador puede usar el nombre para colocar el valor del fragmento de código en una plantilla de página dentro del código del portal. |
| Bsitio | El sitio web que está asociado con el fragmento de código.                                                              |
| Value   | Contenido del fragmento de código que se va a mostrar en el portal. Puede contener texto sin formato o marcado HTML.         |



