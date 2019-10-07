---
title: Plantilla de pantalla People | Microsoft Docs
description: Comprenda cómo funciona la plantilla de pantalla People para las aplicaciones de canvas y cómo ampliar la pantalla para sus propios casos de uso
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
ms.openlocfilehash: da7f7c037010df0da30e0363f988ac616f9fb6cc
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995674"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla People para aplicaciones de Canvas

En una aplicación de lienzo, agregue una pantalla de personas que permita a los usuarios buscar personas dentro de sus organizaciones. Los usuarios pueden buscar, seleccionar y agregar personas a una recopilación. Puede cambiar los tipos de datos que aparecen en la galería de resultados de la búsqueda, usar las selecciones de los usuarios para enviar un correo electrónico y realizar otras personalizaciones.

También puede agregar otras pantallas basadas en plantillas que muestren datos diferentes de Office 365, como el [correo electrónico](email-screen-overview.md), el [calendario](calendar-screen-overview.md)de un usuario y la [disponibilidad](meeting-screen-overview.md) de personas que los usuarios quieran invitar a una reunión.

Esta información general le enseña:
> [!div class="checklist"]
> * Cómo usar la pantalla usuarios predeterminados.
> * Cómo modificar la pantalla.
> * Cómo integrar la pantalla en aplicaciones.

Para profundizar más en la funcionalidad predeterminada de esta pantalla, consulte la [referencia de la pantalla People](people-screen-reference.md).

## <a name="prerequisite"></a>Requisito previo

Está familiarizado con cómo agregar y configurar pantallas y otros controles a medida que [crea una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de contactos de la plantilla:

1. [Inicie sesión](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps y, después, cree una aplicación o abra una aplicación existente en PowerApps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de Tablet PC.

1. En la pestaña **Inicio** de la cinta de opciones, seleccione **nueva pantalla** > **personas**.

    De forma predeterminada, la pantalla tiene un aspecto similar al siguiente:

    ![Estado de la pantalla de usuarios iniciales](media/people-screen/people-screen-empty.png)

1. Para iniciar la búsqueda de usuarios, seleccione el cuadro entrada de texto en la parte superior y comience a escribir el nombre de un compañero de trabajo. Los resultados de la búsqueda aparecen debajo del cuadro de entrada de texto:

    ![Estado de búsqueda de pantalla de personas](media/people-screen/people-browse-gall-full.png)

1. Al seleccionar usuarios de los resultados de la búsqueda, se agregan a la colección **People** . Se restablece el valor de entrada de la barra de búsqueda y se revela la colección de personas que ha seleccionado:

    ![resultados de la colección de pantallas People](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>Modificar la pantalla

Puede modificar la funcionalidad predeterminada de esta pantalla [mostrando datos diferentes para las personas](people-screen-overview.md#show-different-data-for-people).

Si desea modificar la pantalla con más detalle, use la [referencia de la pantalla People](./people-screen-reference.md) como guía.

### <a name="show-different-data-for-people"></a>Mostrar datos diferentes para las personas

Esta pantalla usa la operación [Office365Users. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) para buscar usuarios en la organización. Proporciona campos adicionales para cada evento más allá de lo que aparece en el control **UserBrowseGallery** . Agregar o cambiar campos en la Galería es un proceso sencillo:

1. En **UserBrowseGallery**, seleccione una etiqueta para modificarla (o agréguela y manténgala seleccionada).

1. Con su propiedad **Text** seleccionada, en la barra de fórmulas, reemplace el contenido por `ThisItem.`

    IntelliSense muestra una lista de los campos que puede seleccionar.

1. Seleccione el campo que desee.

    La propiedad **Text** debe actualizarse a `ThisItem.{FieldSelection}`.

## <a name="integrate-the-screen-into-an-app"></a>Integración de la pantalla en una aplicación

La pantalla People es un conjunto eficaz de controles en su propio derecho, pero normalmente funciona mejor como parte de una aplicación más grande y versátil. Puede integrar esta pantalla en una aplicación más grande de varias maneras, incluido [el uso de la lista de personas almacenada en caché](people-screen-overview.md#use-your-cached-list-of-people).

### <a name="use-your-cached-list-of-people"></a>Usar la lista de personas almacenadas en caché

La pantalla People almacena en caché las selecciones de los usuarios **en la colección People.** En caso de que su escenario empresarial llame a una búsqueda de personas, deberá saber cómo usar esta colección. Aquí, le guiará por el modo de conectar esta pantalla a una pantalla de correo electrónico rudimentaria y enviar correos electrónicos a los usuarios de la colección de mis **personas** . También obtendrá información sobre cómo funciona la [pantalla de correo electrónico](./email-screen-overview.md) .

1. Agregue el origen de datos Office 365 Outlook a la aplicación. para ello, seleccione la pestaña **Ver** , seleccione **orígenes de datos** > **Agregar origen de datos**y busque el conector Office 365 Outlook. Es posible que tenga que seleccionar **nueva conexión** para encontrarla.
1. Después de insertar la pantalla People, inserte una nueva pantalla en blanco. Dentro de esa pantalla, agregue un icono de flecha atrás, dos cuadros de entrada de texto y un icono de envío.
1. Cambie el nombre de la pantalla a **EmailScreen**, el icono de flecha atrás a **icono**de retroceso, un cuadro de entrada de texto a **SubjectLine**, el otro a **MessageBody**y el icono de envío a **SendIcon**.
1. Establezca la propiedad **alseleccionar** del **icono** de en `Back()`.
1. Establezca la propiedad **alseleccionar** de **SendIcon** en esta fórmula:

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    Aquí está usando el conector de Outlook para enviar un correo electrónico. Se pasa `Concat(MyPeople, UserPrincipalName & ";")` como la lista de destinatarios. Esta fórmula concatena todas las direcciones de correo electrónico de la colección **People** en una sola cadena con puntos y comas separando. No es diferente de escribir una cadena de direcciones de correo electrónico separadas por punto y coma en la línea "para" de su cliente de correo electrónico favorito.
    * Está pasando `SubjectLine.Text` como asunto del mensaje y `MessageBody.Text` como cuerpo del mensaje.
1. En la pantalla People, en la esquina superior derecha, inserte el icono **mail** .
   Cambie el color del icono a lo que le convenga.
1. Establezca la propiedad **alseleccionar** de **SendIcon** en `Navigate( EmailScreen, None )`.

    Ahora tiene una aplicación de dos pantallas en la que puede seleccionar usuarios, crear un mensaje de correo electrónico para ellos y, a continuación, enviarlo. No dude en probarlo, pero tenga cuidado, ya que la aplicación envía mensajes de correo electrónico a todos los usuarios que agregue a la colección de mis **personas** .

## <a name="next-steps"></a>Pasos siguientes

* [Vea la documentación de referencia de esta pantalla](./people-screen-reference.md).
* [Obtenga más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Obtenga más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
