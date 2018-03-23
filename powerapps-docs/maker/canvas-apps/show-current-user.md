---
title: Visualización de detalles sobre el usuario actual | Microsoft Docs
description: Insertar la función User para mostrar el nombre y la dirección de correo electrónico del usuario con la sesión iniciada en PowerApps
services: ''
suite: powerapps
documentationcenter: ''
author: lonu
manager: anneta
editor: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: lonu
ms.openlocfilehash: b337188360ba592d504a7364fdbeb3a2973b8ee0
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="show-information-about-a-powerapps-user"></a>Mostrar información sobre un usuario de PowerApps
La función User puede mostrar el nombre completo, la dirección de correo electrónico y la imagen asociada con el usuario que ha iniciado sesión. Puede utilizar esta información para rellenar automáticamente un formulario.

Por ejemplo, puede utilizar esta característica para:

* Crear una "hoja" de inicio de sesión para que los usuarios asistan al curso, ir como voluntario a eventos, inscribirse en un quiosco, etc.
* Mostrar el nombre completo en una aplicación de recursos humanos.
* Especificar automáticamente una dirección de correo electrónico automáticamente al ponerse en contacto con el departamento de soporte técnico.

Básicamente, puede usar la característica en cualquier lugar en el que los usuarios se beneficien de un formulario o etiquetas que se rellenen automáticamente

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>Mostrar los detalles del usuario
1. En la pestaña **Insertar**, haga clic o pulse en **Multimedia** y, a continuación, en **Image**.
   
   ![][2]
2. Establezca la propiedad **[Image](controls/properties-visual.md)** en esta fórmula:
   <br>**User().Image**
   
    ![][3]
3. En la pestaña **Insertar**, haga clic o pulse en **Texto** y, a continuación, haga clic o pulse en **Etiqueta**:  
   
    ![][4]
4. Establezca la propiedad **[Text](controls/properties-core.md)** en esta fórmula:
   <br>**User().FullName**
   
   ![][6]
   
   Al hacerlo, la etiqueta se rellena automáticamente con su nombre completo. Mueva la etiqueta para que esté bajo el control de imagen, de forma similar a la siguiente:
   
   ![][5]
5. Agregue otra etiqueta y establezca su propiedad **[Text](controls/properties-core.md)** en esta fórmula:
   <br>**User().Email**  
   
    ![][8]
   
    Al hacerlo, la etiqueta se rellena automáticamente con su dirección de correo electrónico. Mueva la etiqueta para que esté bajo la primera etiqueta, de forma similar a la siguiente:  
   
    ![][7]

[2]: ./media/show-current-user/add-image.png
[3]: ./media/show-current-user/imageproperty.png
[4]: ./media/show-current-user/insertlabel.png
[5]: ./media/show-current-user/label.png
[6]: ./media/show-current-user/textproperty.png
[7]: ./media/show-current-user/secondlabel.png
[8]: ./media/show-current-user/email.png
[9]: ./media/show-current-user/preview.png
