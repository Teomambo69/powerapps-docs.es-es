---
title: Mostrar detalles sobre el usuario actual en una aplicación de lienzo | Microsoft Docs
description: En Power Apps, mostrar el nombre y la dirección de correo electrónico del usuario que inició sesión en una aplicación de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f77ec80cfaf579c836277f0e29d3b84b325a0462
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674610"
---
# <a name="show-information-about-a-power-apps-user-in-a-canvas-app"></a>Mostrar información sobre un usuario de Power Apps en una aplicación de lienzo

En Power Apps, muestre el nombre completo, la dirección de correo electrónico y la imagen asociada al usuario que ha iniciado sesión en una aplicación de lienzo. Puede utilizar esta información, por ejemplo, para rellenar automáticamente un formulario.

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
