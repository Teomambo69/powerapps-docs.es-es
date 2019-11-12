---
title: Plantilla de pantalla de reunión | Microsoft Docs
description: Comprenda cómo funciona la plantilla de pantalla de reunión para las aplicaciones de canvas y amplíe la pantalla para sus propios casos de uso
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2b300b0d90803ae08aaf262dde5642f4d448c05f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541432"
ms.PowerAppsDecimalTransform: true
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla de reunión para las aplicaciones de Canvas

En una aplicación de lienzo, agregue una pantalla de reunión que permita a los usuarios crear y enviar convocatorias de reunión desde sus cuentas de Office 365 Outlook. Los usuarios pueden buscar asistentes en su organización y agregar direcciones de correo electrónico externas. Si el inquilino tiene salas de reuniones integradas en Outlook, los usuarios también pueden seleccionar una ubicación.

También puede agregar otras pantallas basadas en plantillas que muestren datos diferentes de Office 365, como el [correo electrónico](email-screen-overview.md), las [personas](people-screen-overview.md) de una organización y el [calendario](calendar-screen-overview.md)de un usuario.

Esta información general le enseña la funcionalidad de alto nivel de la pantalla.

Para profundizar más en la funcionalidad predeterminada de esta pantalla, consulte la [referencia](meeting-screen-reference.md)de la pantalla de la reunión.

## <a name="prerequisite"></a>Requisito previo

Está familiarizado con cómo agregar y configurar pantallas y otros controles a medida que [crea una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de reunión desde la plantilla:

1. [Inicie sesión](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps y, después, cree una aplicación o abra una aplicación existente en PowerApps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de Tablet PC.

1. En la pestaña **Inicio** de la cinta de opciones, seleccione **nueva pantalla** > **reunión**.

  Cuando se rellena, ambas pestañas de la pantalla de la reunión tienen un aspecto similar al siguiente:

  ![Pantalla de la reunión, ambas pestañas](media/meeting-screen/meeting-screen-full-both.png)

Algunas notas útiles:

* La pantalla de la reunión permite a un usuario de la aplicación crear una reunión en Outlook.
  Los usuarios pueden buscar y agregar asistentes y, opcionalmente, agregar una sala de reuniones a la reunión.
* Para buscar un usuario en su organización, empiece a escribir su nombre en el cuadro de entrada de texto en "asistentes".
* Al buscar personas, solo se devuelven los 15 resultados principales.
* Para agregar direcciones de correo electrónico para los asistentes fuera de la organización, escriba la dirección de correo electrónico completa y válida y seleccione el icono "+" que aparece a la derecha de la dirección de correo electrónico.
* Para crear una reunión, debe agregar al menos una persona como asistente, proporcionar un asunto y seleccionar una hora de reunión en la pestaña **programación** .
* Después de enviar la solicitud de reunión, se borra toda la información de la reunión.
* La instrucción **alseleccionar** del icono de envío (esquina superior derecha) contiene esta fórmula:
    ```powerapps-comma
    Set( _myCalendarName; 
        LookUp( 'Office365'.CalendarGetTables().value; DisplayName = "Calendar" ).Name 
    );;
    ```
* "Calendar" es el nombre para mostrar predeterminado de la mayoría de los calendarios del usuario de Office, pero su organización puede ser diferente. Si es así, puede cambiar "Calendar" por el término adecuado para su organización.
* Recibirá un error si intenta programar una reunión que se produzca en el pasado o agregar más de 20 personas a una reunión.

## <a name="next-steps"></a>Pasos siguientes

* [Vea la documentación de referencia de esta pantalla](./meeting-screen-reference.md).
* [Obtenga más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Obtenga más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
