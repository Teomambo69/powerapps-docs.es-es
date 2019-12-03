---
title: Función User | Microsoft Docs
description: Información de referencia para la función User en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f95a6f7769cde01e99bc4c18fab0ae60ae6b8c96
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680153"
---
# <a name="user-function-in-powerapps"></a>Función User en PowerApps
Muestra información sobre el usuario actual.

## <a name="description"></a>Descripción
La función **User** muestra un [registro](../working-with-tables.md#records) de información sobre el usuario actual:

| Propiedad | Descripción |
| --- | --- |
| **User().Email** |Dirección de correo electrónico del usuario actual. |
| **User().FullName** |Nombre completo del usuario actual, incluidos nombres y apellidos. |
| **User().Image** |Imagen del usuario actual. Será una URL de imagen con formato "blob:*identificador*". Establezca la propiedad **[Image](../controls/properties-visual.md)** del control **[Imagen](../controls/control-image.md)** en este valor para mostrar la imagen en la aplicación. |

> [!NOTE]
> La información devuelta es para el usuario actual de Power apps.  Coincidirá con la información de la "cuenta" que se muestra en los reproductores y estudios de Power Apps, que puede encontrarse fuera de las aplicaciones creadas.  Es posible que no coincida con la información del usuario actual en Office 365 u otros servicios.

## <a name="syntax"></a>Sintaxis
**User**()

## <a name="examples"></a>Ejemplos
El usuario actual de Power apps tiene la siguiente información:

* Nombre completo: **"John Doe"**
* Dirección de correo electrónico: **"john.doe@contoso.com"**
* Imagen: ![](media/function-user/john-doe-picture.png) 

|       Fórmula       |                                                                    Descripción                                                                    |                                                 Resultado                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             Registro de toda la información del usuario de Power apps actual.                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 La dirección de correo electrónico del usuario de Power apps actual.                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   Nombre completo del usuario actual de Power apps.                                                    |                                               "John Doe"                                                |
|  **User().Image**   | La dirección URL de la imagen para el usuario actual de Power apps.  Establezca la propiedad **Image** del control **Imagen** en este valor para mostrar la imagen en la aplicación. | "blob:1234...5678"<br><br>Con **ImageControl.Image**:<br>![](media/function-user/john-doe-picture.png) |

