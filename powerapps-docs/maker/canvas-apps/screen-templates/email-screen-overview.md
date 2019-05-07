---
title: Plantilla de filtro de correo electrónico | Microsoft Docs
description: Comprender el funcionamiento de la plantilla de filtro de correo electrónico para las aplicaciones de lienzo, y ampliar la pantalla para sus casos de uso
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a1aad5ca9e8c7f8b55b1645b04d6c8dc0b9c707b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539230"
ms.PowerAppsDecimalTransform: true
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla de correo electrónico para las aplicaciones de lienzo

En una aplicación de lienzo, agregue una pantalla de correo electrónico que permite a los usuarios enviar un correo electrónico desde su cuenta de Office 365 Outlook. Los usuarios pueden buscar los destinatarios de sus organizaciones y agregar las direcciones de correo electrónico externas, también. Puede agregar compatibilidad con adjuntos de la imagen, cambiar los datos de usuario que aparece en la Galería de búsqueda y realizar otras personalizaciones.

También puede agregar otras pantallas basadas en plantillas que muestren diferentes datos de Office 365, como un usuario [calendario](calendar-screen-overview.md), [personas](people-screen-overview.md) en una organización, y [disponibilidad](meeting-screen-overview.md) de los usuarios de las personas podrían desea invitar a una reunión.

Esta información general aprenderá:
> [!div class="checklist"]
> * Cómo usar la pantalla de correo electrónico predeterminado.
> * Cómo modificarlo.
> * Cómo se integran en una aplicación.

Para un análisis más profundo de la funcionalidad de la pantalla de forma predeterminada, consulte el [referencia de la pantalla de correo electrónico](email-screen-reference.md).

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de correo electrónico de la plantilla:

1. [Inicie sesión en](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) a PowerApps y, a continuación, crear una aplicación o abrir una aplicación existente en PowerApps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de tableta.

1. En el **inicio** pestaña de la cinta de opciones, seleccione **nueva pantalla** > **correo electrónico**.

    De forma predeterminada, la pantalla tiene un aspecto similar al siguiente:

    ![Pantalla de correo electrónico](media/email-screen/email-screen-full.png)

Algunas notas útiles:

* Para buscar usuarios en la organización, comience a escribir su nombre en el cuadro de entrada de texto debajo de "A".
* Cuando se buscan las personas, se devolverá solo los 15 primeros resultados.
* Para agregar direcciones de correo electrónico para destinatarios de correo electrónico fuera de su organización, escriba la dirección de correo electrónico válida, completa y seleccione el icono "+" que aparece a la derecha de la misma.
* Debe agregar a al menos una persona como destinatario y proporcionar un asunto para enviar un correo electrónico.
* Después de enviar el correo electrónico, el contenido de la línea de asunto y cuerpo del mensaje, así como la lista de destinatarios todos se borrarán.

## <a name="modify-the-screen"></a>Modificar la pantalla

Puede modificar la funcionalidad predeterminada de esta pantalla de varias maneras comunes:

* [Agregar compatibilidad con adjuntos de imagen](email-screen-overview.md#add-image-attachment-support)
* [Mostrar datos diferentes para las personas](email-screen-overview.md#show-different-data-for-people)

Si desea modificar la pantalla adicional, utilice el [referencia de la pantalla de correo electrónico](./email-screen-reference.md) como guía.

> [!IMPORTANT]
> Los pasos siguientes se supone que solo hay una pantalla de correo electrónico ha agregado a la aplicación. Si ha agregado más de uno, los nombres de control (como **iconMail1**) finalizará con un número diferente y necesita ajustar las fórmulas según sea necesario.

### <a name="add-image-attachment-support"></a>Agregar compatibilidad con adjuntos de imagen

Esto permite a los usuarios enviar una sola imagen con su correo electrónico como datos adjuntos.

1. En el **insertar** ficha, seleccione **Media**y, a continuación, seleccione **Agregar imagen**.
1. Establecer el nuevo control **Y** propiedad en esta expresión:

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. Con el **AddMediaWithImage** inserta control, establezca su alto sea inferior a 210.
1. En la vista de árbol de control, seleccione **AddMediaWithImage** > **...**   >  **Reordenar** > **enviar al fondo**.
   Esto impide que el control situado en la parte delantera de la **PeopleBrowseGallery** control.
1. Cambiar el **alto** propiedad de **EmailPeopleGallery** en esta fórmula:

    ```powerapps-comma
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2; 0 ); 
        304
    )
    ```

1. Establecer el **ShowScrollbar** propiedad de **EmailPeopleGallery** en esta expresión:

    ```EmailPeopleGallery1.Height >= 304```
    
    Esto impide que la altura máxima de insertar el **AddMediaWithImage** control fuera de la página.
    
1. Cambiar el **Alseleccionar** propiedad de la **iconMail** control en esta fórmula:

    ```powerapps-comma
    Set( _emailRecipientString; Concat(MyPeople; Mail & ";") );;
    If( IsBlank( UploadedImage1 );
        'Office365'.SendEmail( _emailRecipientString; 
            TextEmailSubject1.Text; 
            TextEmailMessage1.Text; 
            { Importance: "Normal" }
        );
        'Office365'.SendEmail( _emailRecipientString; 
            TextEmailSubject1.Text; 
            TextEmailMessage1.Text; 
            {
                Importance: "Normal";
                Attachments: Table(
                    {
                        Name: "Image.jpg"; 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );;
    Reset( TextEmailSubject1 );;
    Reset( TextEmailMessage1 );;
    Reset( AddMediaButton1 );;
    Clear( MyPeople )
    ```
    
    Esta fórmula comprueba si hay una imagen cargada. Si no hay ninguno, a continuación, usa el mismo `Office365.SendEmail` operación como antes. Si hay una imagen, se agrega como datos adjuntos en la tabla de datos adjuntos.
    Después de enviar el correo electrónico adicional **restablecer** se realiza en **AddMediaButton** para quitar la imagen cargada.
> [!NOTE]
> Para agregar más de un archivo adjunto a un correo electrónico, agregar registros a la tabla de datos adjuntos.

### <a name="show-different-data-for-people"></a>Mostrar datos diferentes para las personas

Esta pantalla usa la [Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) operación de búsqueda para los usuarios de su organización. Proporciona campos adicionales para cada evento más allá de lo que aparece en el **PeopleBrowseGallery** control. Agregar o cambiar los campos de la galería es sencillo:

1. En el **PeopleBrowseGallery** de control, seleccione una etiqueta para modificar (o agregue uno y manténgala seleccionada).

1. Con su **texto** propiedad seleccionada en la barra de fórmulas, reemplace el contenido con `ThisItem.`

    IntelliSense muestra una lista de campos que se pueden seleccionar.

1. Seleccione el campo que desee.

    El **texto** propiedad se actualiza a `ThisItem.{FieldSelection}`.

## <a name="integrate-the-screen-into-an-app"></a>Integrar la pantalla en una aplicación

La pantalla de correo electrónico es un conjunto eficaz de controles por derecho propio, pero normalmente realiza mejor como parte de una aplicación más grande y más versátil. Puede integrar esta pantalla en una aplicación de mayor tamaño de varias maneras, incluyendo [vinculación a la pantalla de calendario](email-screen-overview.md#linking-to-the-calendar-screen).

### <a name="linking-to-the-calendar-screen"></a>Vinculación a la pantalla de calendario

Siga los pasos descritos en la sección "Mostrar los asistentes del evento" de [información general de pantalla de calendario](./calendar-screen-overview.md#show-event-attendees) pero, en el paso final, establezca el **Navigate** función para abrir la pantalla de correo electrónico. Después de completar estos pasos, el **MyPeople** colección se rellena, lo que permite a los usuarios enviar correo electrónico a las personas que asiste a los eventos seleccionados.

> [!NOTE]
> Enviar este correo electrónico enviará un correo electrónico independiente del evento real en Outlook.

## <a name="next-steps"></a>Pasos siguientes

* [Consulte la documentación de referencia para esta pantalla](./email-screen-reference.md).
* [Más información sobre el conector de usuarios de Office 365 en PowerApps](../connections/connection-office365-users.md).
* [Vea todas las conexiones disponibles en PowerApps](../connections-list.md).