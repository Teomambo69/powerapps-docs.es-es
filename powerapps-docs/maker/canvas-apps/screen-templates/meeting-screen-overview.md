---
title: Plantilla de pantalla de la reunión | Microsoft Docs
description: Comprender el funcionamiento de la plantilla de pantalla de la reunión para las aplicaciones de lienzo, y ampliar la pantalla para sus casos de uso
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 24f04ff9ce95f603f5f7d4dc7d217146b9eebef8
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61535987"
ms.PowerAppsDecimalTransform: true
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla de la reunión para las aplicaciones de lienzo

En una aplicación de lienzo, agregue una pantalla de reunión que permite a los usuarios crear y enviar convocatorias de reunión desde sus cuentas de Office 365 Outlook. Los usuarios pueden buscar los asistentes en su organización y agregue las direcciones de correo electrónico externas. Si el inquilino tiene salas de reuniones integradas en Outlook, los usuarios pueden seleccionar una ubicación de así.

También puede agregar otras pantallas basadas en plantillas que muestren diferentes datos de Office 365, como [correo electrónico](email-screen-overview.md), [personas](people-screen-overview.md) en una organización y un usuario [calendario](calendar-screen-overview.md).

En esta introducción se explica en la funcionalidad de alto nivel de la pantalla.

Para un análisis más profundo de la funcionalidad de la pantalla de forma predeterminada, consulte el [referencia de la pantalla de la reunión](meeting-screen-reference.md).

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de la reunión de la plantilla:

1. [Inicie sesión en](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) a PowerApps y, a continuación, crear una aplicación o abrir una aplicación existente en PowerApps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de tableta.

1. En el **inicio** pestaña de la cinta de opciones, seleccione **nueva pantalla** > **reunión**.

  Al rellenar, ambas fichas de la pantalla del área de encuentro un aspecto similar al siguiente:

  ![Pantalla de reunión, ambas fichas](media/meeting-screen/meeting-screen-full-both.png)

Algunas notas útiles:

* La pantalla de la reunión permite que un usuario de la aplicación crear una reunión en Outlook.
  Los usuarios pueden buscar y agregar a los asistentes y, opcionalmente, agregue una sala de reuniones a la reunión.
* Para buscar un usuario en su organización, comience a escribir su nombre en el cuadro de entrada de texto en "A los asistentes".
* Al realizar una búsqueda de personas, se devuelven únicamente los 15 primeros resultados.
* Para agregar direcciones de correo electrónico para los asistentes fuera de su organización, escriba la dirección de correo electrónico válida, completa y seleccione el icono "+" que aparece a la derecha de la dirección de correo electrónico.
* Para crear una reunión, debe agregar al menos una persona como un asistente, proporcione un asunto y seleccione una hora de reunión en la **programación** ficha.
* Después de enviar la convocatoria de reunión, se borra toda la información de la reunión.
* El **OnSelect** instrucción del icono (esquina superior derecha) de envío contiene esta fórmula:
    ```powerapps-comma
    Set( _myCalendarName; 
        LookUp( 'Office365'.CalendarGetTables().value; DisplayName = "Calendar" ).Name 
    );;
    ```
* "Calendar" es el nombre para mostrar de forma predeterminada para los calendarios del usuario de la mayoría Office, pero su organización puede diferir. Si es así, puede cambiar "Calendar" para el término adecuado para su organización.
* Se produce un error si intenta programar una reunión que se produce en el pasado o agregar más de 20 personas a una reunión.

## <a name="next-steps"></a>Pasos siguientes

* [Consulte la documentación de referencia para esta pantalla](./meeting-screen-reference.md).
* [Más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
