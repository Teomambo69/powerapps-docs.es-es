---
title: Introducción a la conexión de Office 365 Outlook | Microsoft Docs
description: Información de referencia, incluidos ejemplos, para la conexión de Office 365 Outlook con Power apps
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/20/2017
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1886514d036fe2b64ae82712128b14e19189fc73
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74728355"
---
# <a name="connect-to-office-365-outlook-from-power-apps"></a>Conexión a Office 365 Outlook desde Power apps
![Office 365 Outlook](./media/connection-office365-outlook/office365icon.png)

Si se conecta a Office 365 Outlook, puede mostrar, enviar, eliminar y responder a mensajes de correo electrónico, además de otras tareas.

Puede agregar controles para realizar estas funciones en la aplicación. Por ejemplo, puede agregar controles de **entrada de texto** para solicitar el destinatario, asunto y cuerpo del correo electrónico, y agregar un control de **botón** para enviar el correo.

En este tema se muestra cómo agregar Office 365 Outlook como una conexión, agregar Office 365 Outlook como origen de datos a su aplicación y cómo utilizar estos datos en distintos controles.

> [!IMPORTANT]
> En el momento de redacción este documento, la operación del calendario no admite eventos recurrentes.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-office-365-outlook"></a>Conexión a Office 365 Outlook
1. [Agregue una conexión de datos](../add-data-connection.md) y seleccione **Office 365 Outlook**:  
   
    ![Conexión a Office 365](./media/connection-office365-outlook/add-office.png)
2. Seleccione **Connect** (Conectar) y, si se pide que inicie sesión, escriba su cuenta profesional.

La conexión con Office 365 Outlook se ha creado y agregado a la aplicación. Ahora, está lista para utilizarse.

## <a name="show-messages"></a>Presentación de mensajes
1. En el menú **Insertar**, seleccione **Galería** y seleccione un control de la **galería con texto**.
2. Establezca su propiedad **[Elementos](../controls/properties-core.md)** en la fórmula siguiente:  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    Después de cambiar la configuración, cambie **diseño** a **título, subtítulo y cuerpo**.
    
    El control de galería se rellena automáticamente con algunos de los correos electrónicos.
    
3. En la galería, establezca la propiedad **Texto** de la primera etiqueta en `ThisItem.From`. Establezca la segunda etiqueta en `ThisItem.Subject`. Establezca la tercera etiqueta en `ThisItem.BodyPreview`. También puede cambiar el tamaño de las etiquetas.
   
    El control de galería se rellena automáticamente con algunas de las nuevas propiedades.
4. Esta función tiene varios parámetros opcionales disponibles. Establezca la propiedad **Elementos** de la galería en una de las fórmulas siguientes:
   
    `Office365.GetEmails({fetchOnlyUnread:false})`  
    `Office365.GetEmails({fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2, searchQuery:"powerapps"})`  
    `Office365.GetEmails({folderPath:"Deleted Items", fetchOnlyUnread:false, top:2, skip:3})`

## <a name="send-a-message"></a>Envío de un mensaje
1. En el menú **Insert** (Insertar), seleccione **Text** (Texto) y luego seleccione **Text input** (Entrada de texto).
2. Repita el paso anterior dos veces más, con lo que tendrá tres casillas y organícelas en una columna:  
   
    ![Tres cuadros en una columna](./media/connection-office365-outlook/threetextinput.png)
3. Cambie el nombre de los controles a:  
   
   * **entradaPara**
   * **entradaAsunto**
   * **entradaCuerpo**
4. En la pestaña **Insertar**, seleccione **Controles** y, a continuación, seleccione **Botón**. Establezca su propiedad **[AlSeleccionar](../controls/properties-core.md)** en la fórmula siguiente:  
   
    `Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text)`
5. Mueva el botón para que aparezca en todos los demás controles y establezca su propiedad **[Texto](../controls/properties-core.md)** en **"Enviar correo electrónico"** .
6. Presione F5 o seleccione el botón Vista previa (![botón Vista previa](./media/connection-office365-outlook/preview.png)). Escriba una dirección de correo electrónico válida en **entradaPara** y escriba el nombre que desee en los otros dos controles **Entrada de texto**.
7. Seleccione **Enviar correo electrónico** para enviar el mensaje. Presione Esc para volver al área de trabajo predeterminada.

## <a name="send-a-message-with-an-attachment"></a>Envío de un mensaje con datos adjuntos
Por ejemplo, puede crear una aplicación en la que el usuario haga fotos con la cámara del dispositivo y, luego, las envíe como datos adjuntos. Los usuarios también pueden adjuntar muchos otros tipos de archivos a una aplicación de correo electrónico.

Para agregar datos adjuntos a un mensaje, siga los pasos descritos en la sección anterior, pero agregue un parámetro para especificar que hay datos adjuntos (al establecer la propiedad **AlSeleccionar** del botón). Este parámetro se estructura como una tabla en la que se especifican hasta tres propiedades para los datos adjuntos:

* Nombre
* ContentBytes
* @odata.type

> [!NOTE]
> La propiedad @odata.type se puede especificar para un solo archivo adjunto y se puede establecer en una cadena vacía.

En este ejemplo, se enviará una foto como **file1.jpg**:

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""})})`

En este ejemplo, se enviará un archivo de audio junto con la foto:

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""}, {Name:"AudioFile", ContentBytes:microphone1.audio })})`

## <a name="delete-a-message"></a>Eliminación de un mensaje
1. En el menú **Insertar**, seleccione **Galería** y seleccione un control de la **galería con texto**.
2. Establezca su propiedad **[Elementos](../controls/properties-core.md)** en la fórmula siguiente:  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    El control de galería se rellena automáticamente con algunos de los correos electrónicos.
3. En la galería, establezca la propiedad **Texto** de la primera etiqueta en `ThisItem.Id`. Establezca la segunda etiqueta en `ThisItem.Subject`. Establezca la tercera etiqueta en `ThisItem.Body`.
4. Seleccione la primera etiqueta de la galería y cambie su nombre a **IdCorreoElectrónico**:
   
    ![Cambiar el nombre de la primera etiqueta](./media/connection-office365-outlook/renameheading.png)
5. Seleccione la tercera etiqueta de la galería y agregue un **botón** (menú **Insertar**). Establezca la propiedad **AlSeleccionar** del botón en la fórmula siguiente:  
   
    `Office365.DeleteEmail(EmailID.Text)`
6. Presione F5 o seleccione el botón Vista previa (![botón Vista previa](./media/connection-office365-outlook/preview.png)). Seleccione uno de los correos electrónicos de la galería y haga clic en el botón. 
    
    > [!NOTE]
    > Así se elimina el correo electrónico seleccionado de la Bandeja de entrada. Por lo tanto, tenga cuidado al elegirlos.
7. Presione Esc para volver al área de trabajo predeterminada.

## <a name="mark-a-message-as-read"></a>Marca de un mensaje como leído
En esta sección se usan los mismos controles que en [Eliminar un mensaje](connection-office365-outlook.md#delete-a-message).

1. Establezca la propiedad **AlSeleccionar** del botón en la fórmula siguiente:  
   
    `Office365.MarkAsRead(EmailID.Text)`
2. Presione F5 o seleccione el botón Vista previa (![botón Vista previa](./media/connection-office365-outlook/preview.png)). Seleccione uno de los mensajes de correo electrónico no leídos y haga clic en el botón.
3. Presione Esc para volver al área de trabajo predeterminada.

## <a name="helpful-links"></a>Vínculos útiles
* Para obtener una lista de todas las funciones y sus parámetros, consulte la [referencia de Office 365 Outlook](https://docs.microsoft.com/connectors/office365connector/).
* Consulte todas las [conexiones disponibles](../connections-list.md).  
* Más información sobre cómo [administrar las conexiones](../add-manage-connections.md).

