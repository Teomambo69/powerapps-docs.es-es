---
title: Función Usuario | Microsoft Docs
description: Información de referencia para la función User en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2016
ms.author: gregli
ms.openlocfilehash: 05fcf0e10522bf8f70972ddc5b86d504afb28e4e
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022295"
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
> La información que se devuelve corresponde al usuario actual de PowerApps.  Coincidirá con la información de "cuenta" que aparece en los reproductores y estudio de PowerApps, que se puede encontrar fuera de toda aplicación creada.  Es posible que no coincida con la información del usuario actual en Office 365 u otros servicios.

## <a name="syntax"></a>Sintaxis
**User**()

## <a name="examples"></a>Ejemplos
El usuario actual de PowerApps tiene la información siguiente:

* Nombre completo: **"John Doe"**
* Dirección de correo electrónico: **"john.doe@contoso.com"**
* Imagen: ![](media/function-user/john-doe-picture.png) 

|       Fórmula       |                                                                    Descripción                                                                    |                                                 Resultado                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             Registro de toda la información del usuario actual de PowerApps.                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 La dirección de correo electrónico del usuario actual de PowerApps.                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   El nombre completo del usuario actual de PowerApps.                                                    |                                               "John Doe"                                                |
|  **User().Image**   | La URL de imagen del usuario actual de PowerApps.  Establezca la propiedad **Image** del control **Imagen** en este valor para mostrar la imagen en la aplicación. | "blob:1234...5678"<br><br>Con **ImageControl.Image**:<br>![](media/function-user/john-doe-picture.png) |

