---
title: Plantilla de pantalla de correo electrónico | Microsoft Docs
description: Comprenda cómo funciona la plantilla de pantalla de correo electrónico para las aplicaciones de canvas y amplíe la pantalla para sus propios casos de uso
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2fd03b1a54b54c1abe1d6c30270861b6fc9b8054
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71989349"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla de correo electrónico para las aplicaciones de Canvas

En una aplicación de lienzo, agregue una pantalla de correo electrónico que permita a los usuarios enviar un correo electrónico desde su cuenta de Office 365 Outlook. Los usuarios pueden buscar destinatarios en sus organizaciones y agregar también direcciones de correo electrónico externas. Puede Agregar compatibilidad con datos adjuntos de imagen, cambiar los datos de usuario que aparecen en la galería de búsquedas y realizar otras personalizaciones.

También puede agregar otras pantallas basadas en plantillas que muestren datos diferentes de Office 365, como el [calendario](calendar-screen-overview.md)de un usuario, las [personas](people-screen-overview.md) de una organización y la [disponibilidad](meeting-screen-overview.md) de las personas a las que los usuarios quieran invitar a una reunión.

Esta información general le enseña:
> [!div class="checklist"]
> * Cómo usar la pantalla de correo electrónico predeterminada.
> * Cómo modificarlo.
> * Cómo integrarlo en una aplicación.

Para profundizar más en la funcionalidad predeterminada de esta pantalla, consulte la [referencia de la pantalla de correo electrónico](email-screen-reference.md).

## <a name="prerequisite"></a>Requisito previo

Está familiarizado con cómo agregar y configurar pantallas y otros controles a medida que [crea una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de correo electrónico desde la plantilla:

1. [Inicie sesión](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps y, después, cree una aplicación o abra una aplicación existente en PowerApps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de Tablet PC.

1. En la pestaña **Inicio** de la cinta de opciones, seleccione **nueva pantalla** > **correo electrónico**.

    De forma predeterminada, la pantalla tiene un aspecto similar al siguiente:

    ![Pantalla de correo electrónico](media/email-screen/email-screen-full.png)

Algunas notas útiles:

* Para buscar usuarios en la organización, empiece a escribir su nombre en el cuadro de entrada de texto que aparece debajo de "a".
* Al buscar personas, solo se devolverán los 15 resultados principales.
* Para agregar direcciones de correo electrónico a los destinatarios de correo electrónico fuera de la organización, escriba la dirección de correo electrónico completa y válida y seleccione el icono "+" que aparece a la derecha.
* Debe agregar al menos una persona como destinatario y proporcionar un asunto para enviar un correo electrónico.
* Después de enviar el correo electrónico, se borrarán todos los contenidos de la línea de asunto y el cuerpo del mensaje, así como la lista de destinatarios.

## <a name="modify-the-screen"></a>Modificar la pantalla

Puede modificar la funcionalidad predeterminada de esta pantalla de varias maneras comunes:

* [Agregar compatibilidad con datos adjuntos de imagen](email-screen-overview.md#add-image-attachment-support)
* [Mostrar datos diferentes para las personas](email-screen-overview.md#show-different-data-for-people)

Si desea modificar la pantalla con más detalle, use la [referencia de la pantalla de correo electrónico](./email-screen-reference.md) como guía.

> [!IMPORTANT]
> En los pasos siguientes se supone que ha agregado solo una pantalla de correo electrónico a la aplicación. Si ha agregado más de uno, los nombres de control (por ejemplo, **iconMail1**) terminarán con un número diferente y tendrá que ajustar las fórmulas según corresponda.

### <a name="add-image-attachment-support"></a>Agregar compatibilidad con datos adjuntos de imagen

Esto permite a los usuarios enviar una sola imagen con el correo electrónico como datos adjuntos.

1. En la pestaña **Insertar** , seleccione **medio**y, a continuación, seleccione **Agregar imagen**.
1. Establezca la propiedad **Y** del nuevo control en esta expresión:

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. Con el control **AddMediaWithImage** insertado, establezca su alto en un valor inferior a 210.
1. En la vista de árbol de control, seleccione **AddMediaWithImage** >  **...**  > **reordene** > **enviar al fondo**.
   Esto evita que el control esté delante del control **PeopleBrowseGallery** .
1. Cambie la propiedad **alto** de **EmailPeopleGallery** a esta fórmula:

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. Establezca la propiedad **ShowScrollbar** de **EmailPeopleGallery** en esta expresión:

    ```EmailPeopleGallery1.Height >= 304```
    
    Esto impide que el alto máximo Inserte el control **AddMediaWithImage** fuera de la página.
    
1. Cambie la propiedad **alseleccionar** del control **iconMail** a esta fórmula:

    ```powerapps-dot
    Set( _emailRecipientString, Concat(MyPeople, Mail & ";") );
    If( IsBlank( UploadedImage1 ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            { Importance: "Normal" }
        ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            {
                Importance: "Normal",
                Attachments: Table(
                    {
                        Name: "Image.jpg", 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );
    Reset( TextEmailSubject1 );
    Reset( TextEmailMessage1 );
    Reset( AddMediaButton1 );
    Clear( MyPeople )
    ```
    
    Esta fórmula comprueba si hay una imagen cargada. Si no hay ninguno, usa la misma operación `Office365.SendEmail` que antes. Si hay una imagen, se agrega como datos adjuntos en la tabla de datos adjuntos.
    Después de enviar el correo electrónico, se realiza una operación de **restablecimiento** adicional en **AddMediaButton** para quitar la imagen cargada.
> [!NOTE]
> Para agregar más de un archivo adjunto a un correo electrónico, agregue registros a la tabla de datos adjuntos.

### <a name="show-different-data-for-people"></a>Mostrar datos diferentes para las personas

Esta pantalla usa la operación [Office365Users. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) para buscar usuarios en la organización. Proporciona campos adicionales para cada evento más allá de lo que aparece en el control **PeopleBrowseGallery** . Agregar o cambiar campos en la Galería es sencillo:

1. En el control **PeopleBrowseGallery** , seleccione una etiqueta para modificarla (o agréguela y manténgala seleccionada).

1. Con su propiedad **Text** seleccionada, en la barra de fórmulas, reemplace el contenido por `ThisItem.`

    IntelliSense muestra una lista de los campos que puede seleccionar.

1. Seleccione el campo que desee.

    La propiedad de **texto** se actualiza a `ThisItem.{FieldSelection}`.

## <a name="integrate-the-screen-into-an-app"></a>Integración de la pantalla en una aplicación

La pantalla de correo electrónico es un conjunto eficaz de controles en su propio derecho, pero normalmente funciona mejor como parte de una aplicación más grande y versátil. Puede integrar esta pantalla en una aplicación más grande de varias maneras, como [la vinculación a la pantalla del calendario](email-screen-overview.md#linking-to-the-calendar-screen).

### <a name="linking-to-the-calendar-screen"></a>Vincular a la pantalla calendario

Siga los pasos descritos en la sección "Mostrar asistentes de eventos" de [información general](./calendar-screen-overview.md#show-event-attendees) de la pantalla de calendario pero, en el paso final, establezca la función **Navigate** para abrir la pantalla de correo electrónico. Después de completar estos pasos, se rellena la colección **People** , que permite a los usuarios enviar correo electrónico a las personas que asisten al evento seleccionado.

> [!NOTE]
> Al enviar este correo electrónico se enviará un correo electrónico independiente del evento real en Outlook.

## <a name="next-steps"></a>Pasos siguientes

* [Vea la documentación de referencia de esta pantalla](./email-screen-reference.md).
* [Obtenga más información sobre el conector de usuarios de Office 365 en PowerApps](../connections/connection-office365-users.md).
* [Vea todas las conexiones disponibles en PowerApps](../connections-list.md).