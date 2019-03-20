---
title: Plantilla de pantalla de las personas | Microsoft Docs
description: Comprender cómo funciona la plantilla de pantalla de las personas para las aplicaciones de lienzo y cómo ampliar la pantalla para sus casos de uso
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
ms.openlocfilehash: 85da6f5414cc25d1145f0fa8910e8c78bfb74533
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459445"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla de las personas para las aplicaciones de lienzo

En una aplicación de lienzo, agregue una pantalla de las personas que permite a los usuarios buscar personas dentro de sus organizaciones. Los usuarios pueden buscar, seleccionar y agregar personas a una colección. Puede cambiar qué tipos de datos aparecen en la Galería de resultados de búsqueda, use las selecciones de las personas para enviar un correo electrónico y realizar otras personalizaciones.

También puede agregar otras pantallas basadas en plantillas que muestren diferentes datos de Office 365, como [correo electrónico](email-screen-overview.md), un usuario [calendario](calendar-screen-overview.md), y [disponibilidad](meeting-screen-overview.md) de personas posible que los usuarios ¿desea invitar a una reunión.

Esta información general aprenderá:
> [!div class="checklist"]
> * Cómo usar la pantalla predeterminada de las personas.
> * Cómo modificar la pantalla.
> * Cómo integrar aplicaciones en la pantalla.

Para un análisis más profundo de la funcionalidad de la pantalla de forma predeterminada, consulte el [referencia de la pantalla de las personas](people-screen-reference.md).

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de personas de la plantilla:

1. [Inicie sesión en](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) a PowerApps y, a continuación, crear una aplicación o abrir una aplicación existente en PowerApps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de tableta.

1. En el **inicio** pestaña de la cinta de opciones, seleccione **nueva pantalla** > **personas**.

    De forma predeterminada, la pantalla tiene un aspecto similar al siguiente:

    ![Estado de la pantalla de personas inicial](media/people-screen/people-screen-empty.png)

1. Para iniciar la búsqueda de usuarios, seleccione el cuadro de entrada de texto en la parte superior y comience a escribir el nombre de un compañero de trabajo. Los resultados de búsqueda aparecen debajo del cuadro de entrada de texto:

    ![estado de búsqueda de personas pantalla](media/people-screen/people-browse-gall-full.png)

1. Al seleccionar personas de los resultados de búsqueda, se agregan a la **MyPeople** colección. Se restablece la barra de valor de entrada de búsqueda, revelando la colección de personas que ha seleccionado:

    ![las personas de la pantalla resultados de la colección](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>Modificar la pantalla

Puede modificar la funcionalidad predeterminada de esta pantalla por [que muestra datos diferentes para las personas](people-screen-overview.md#show-different-data-for-people).

Si desea modificar la pantalla adicional, utilice el [referencia de la pantalla de las personas](./people-screen-reference.md) como guía.

### <a name="show-different-data-for-people"></a>Mostrar datos diferentes para las personas

Esta pantalla usa la [Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) operación de búsqueda para los usuarios de su organización. Proporciona campos adicionales para cada evento más allá de lo que aparece en el **UserBrowseGallery** control. Agregar o cambiar los campos de la galería es un proceso sencillo:

1. En el **UserBrowseGallery**, seleccione una etiqueta para modificar (o agregue uno y manténgala seleccionada).

1. Con su **texto** propiedad seleccionada en la barra de fórmulas, reemplace el contenido con `ThisItem.`

    IntelliSense muestra una lista de campos que se pueden seleccionar.

1. Seleccione el campo que desee.

    El **texto** propiedad debería actualizarse a `ThisItem.{FieldSelection}`.

## <a name="integrate-the-screen-into-an-app"></a>Integrar la pantalla en una aplicación

La pantalla de personas es un conjunto eficaz de controles por derecho propio, pero normalmente realiza mejor como parte de una aplicación más grande y más versátil. Puede integrar esta pantalla en una aplicación de mayor tamaño de varias maneras, incluyendo [mediante la lista de personas almacenados en caché](people-screen-overview.md#use-your-cached-list-of-people).

### <a name="use-your-cached-list-of-people"></a>Use la lista de personas almacenados en caché

La pantalla de las personas se almacena en memoria caché las selecciones de personas en el **MyPeople** colección. Debe llamar su escenario de negocio para realizar una búsqueda de persona, necesitará saber cómo utilizar esta colección. En este caso, guiaremos a través de cómo conectarse a esta pantalla a una pantalla rudimentaria de correo electrónico y enviar correos electrónicos a los usuarios de la **MyPeople** colección. También obtendrá información sobre cómo el [pantalla de correo electrónico](./email-screen-overview.md) funciona.

1. Agregar el origen de datos de Office 365 Outlook a la aplicación seleccionando el **vista** pestaña, seleccione **orígenes de datos** > **agregar origen de datos**y buscando la oficina Conector de outlook 365. Es posible que deba seleccionar **nueva conexión** para encontrarlo.
1. Después de insertar la pantalla de personas, inserte una nueva pantalla en blanco. Dentro de esa pantalla, agregue un icono de flecha atrás, dos cuadros de entrada de texto y un icono de envío.
1. Cambiar el nombre de la pantalla para **EmailScreen**, el icono de flecha Atrás para **BackIcon**, un cuadro de entrada de texto en **SubjectLine**, el otro a **MessageBody**y el icono de envío para **SendIcon**.
1. Establecer el **Alseleccionar** propiedad de **BackIcon** a `Back()`.
1. Establecer el **Alseleccionar** propiedad de **SendIcon** en esta fórmula:

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    En este caso, usa el conector de Outlook para enviar un correo electrónico. Se le pasa `Concat(MyPeople, UserPrincipalName & ";")` como la lista de destinatarios. Esta fórmula concatena todas las direcciones de correo electrónico en el **MyPeople** colección en una sola cadena con punto y coma separa. Esto no es diferente de escritura de una cadena de direcciones de correo electrónico separadas por punto y coma en la línea "Para" del cliente de correo electrónico favoritos.
    * Pasamos `SubjectLine.Text` como el asunto del mensaje, y `MessageBody.Text` como el cuerpo del mensaje.
1. En la pantalla de personas, en la esquina superior derecha, inserte el **correo** icono.
   Cambie el color del icono a todo lo que le acomode.
1. Establecer el **Alseleccionar** propiedad de la **SendIcon** a `Navigate( EmailScreen, None )`.

    Ahora tiene una aplicación de dos pantallas en el que puede seleccionar usuarios, redactar un mensaje de correo electrónico y envíelo. Si quiere, puede probarlo, pero tenga cuidado, ya que los envíos de la aplicación envía un correo electrónico a todos los usuarios agregue a la **MyPeople** colección.

## <a name="next-steps"></a>Pasos siguientes

* [Consulte la documentación de referencia para esta pantalla](./people-screen-reference.md).
* [Más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
