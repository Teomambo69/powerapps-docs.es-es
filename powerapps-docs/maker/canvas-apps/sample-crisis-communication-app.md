---
title: 'Aplicación de comunicación de crisis: plantilla de ejemplo | Microsoft Docs'
description: Obtenga información sobre la plantilla de ejemplo de comunicación de crisis en Power apps.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/25/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b4a356903c741b97a9b8dbe49d402f71f7196f0b
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328548"
---
# <a name="set-up-and-learn-about-the-crisis-communication-sample-template-in-power-apps"></a>Configuración y información sobre la plantilla de ejemplo de comunicación de crisis en Power apps

La aplicación de comunicación de crisis proporciona una experiencia fácil de utilizar para conectar usuarios con información sobre una crisis. Reciba rápidamente actualizaciones de noticias internas de la empresa, Obtenga respuestas a las preguntas más frecuentes y obtenga acceso a información importante, como vínculos y contactos de emergencia. Esta aplicación requiere un mínimo de configuración para personalizarla.

En este tutorial, aprenderá a:

- Cree una ubicación para los datos.
- Importe la aplicación de comunicación de crisis y su aplicación de administración.
- Cree contenido para la aplicación.
- Importar flujos para enviar notificaciones a los usuarios.
- Cree un equipo de equipos administrados centralmente para agregar datos y responder de forma eficaz a los problemas.

Tiempo estimado para completar estos pasos: **20&ndash;25 minutos**.

> [!NOTE]
> La plantilla de ejemplo de comunicación de crisis también está disponible para los planes de Power apps US Government y Power Automatic US Government. Las direcciones URL de servicio para Power apps y Power automatice las versiones gubernamentales de EE. UU. son diferentes de las versiones comerciales. Más información: las [direcciones URL del servicio de administración pública de EE. UU.](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#power-apps-us-government-service-urls) y la potencia de las [direcciones URL del servicio gobierno de EE. UU.](https://docs.microsoft.com/power-automate/us-govt#power-automate-us-government-service-urls)

## <a name="demo-crisis-communication-app"></a>Demostración: aplicación de comunicación de crisis

Vea cómo usar la solución de comunicación de crisis.

> [!VIDEO https://www.youtube.com/embed/23SypLXiOTw]

## <a name="prerequisites"></a>Requisitos previos

- [Regístrese](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) para Power apps.
- Debe tener una licencia de SharePoint Online válida y permisos para crear listas.
- Debe tener un sitio de SharePoint público en el que pueda almacenar los datos de la aplicación.
- Descargue los recursos de [aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution).

> [!IMPORTANT]
> Para cualquier comentario o problema relacionado con la aplicación de comunicación de crisis, use los vínculos siguientes:
> - **[Los](https://aka.ms/crisis-communication-feedback)**
> - **[Problemas](https://aka.ms/crisis-communication-issues)**

## <a name="demo-build-and-deploy-the-crisis-communication-app"></a>Demo: compilar e implementar la aplicación de comunicación de crisis

Vea cómo compilar e implementar la aplicación de comunicación de crisis.

> [!VIDEO https://www.youtube.com/embed/Wykrwf9dZ-Y]

## <a name="create-a-home-for-your-data"></a>Crear un hogar para los datos

Los datos de la aplicación se almacenan en listas de SharePoint, por lo que el primer paso es crear un nuevo sitio de SharePoint.

### <a name="create-a-sharepoint-site"></a>Crear un sitio de SharePoint

1. Inicie sesión en [Office Online](https://www.office.com)y, a continuación, seleccione **SharePoint**.
1. Seleccione **crear sitio**.

    ![Sitio de SharePoint de ejemplo](media/sample-crisis-communication-app/01-Create-Site.png)

1. Seleccione **sitio de grupo**.

    ![Sitio de grupo](media/sample-crisis-communication-app/02-Team-Site.png)

1. Escriba un nombre y una descripción para el sitio.
1. Establezca la **configuración de privacidad** en **público** para que todos los usuarios de la empresa puedan obtener la información necesaria.

    ![Configuración del sitio](media/sample-crisis-communication-app/03-Privacy-Settings.png)

1. Seleccione **Siguiente**.
1. Agregue propietarios adicionales para el sitio (opcional).
1. Seleccione **Finalizar**.

### <a name="create-sharepoint-lists-for-the-app"></a>Crear listas de SharePoint para la aplicación

La aplicación usa varias listas para almacenar sus datos. Puede usar el flujo DeploySPLists, disponible en el paquete de [recursos](#prerequisites)descargados, para crear automáticamente estas listas.

#### <a name="import-the-sharepoint-list-deployment-flow"></a>Importar el flujo de implementación de la lista de SharePoint

1. Vaya a [Flow.Microsoft.com](https://flow.microsoft.com).
1. Seleccione **Mis flujos** en el panel de navegación izquierdo.
1. Seleccione **importar** en la barra de comandos.
1. Carga de **DeploySPLists. zip**<!--edit to the file name okay, here and in the following instances?--> paquete del repositorio de GitHub.

    ![Importar paquete](media/sample-crisis-communication-app/import-package.png)

1. Agregue una conexión de SharePoint para el nuevo flujo; para ello, seleccione el vínculo **seleccionar durante la importación** y rellene el formulario.

    ![Importar configuración](media/sample-crisis-communication-app/import-settings.png)

1. Si necesita crear una nueva conexión de SharePoint, seleccione **crear nuevo** en el panel **importar configuración** .
1. Seleccione **nueva conexión** en la barra de comandos.

    ![Creación de una nueva conexión](media/sample-crisis-communication-app/create-connection.png)

1. Busque el nombre de la conexión, por ejemplo *SharePoint*.
1. Seleccione la conexión que creó.<!--edit okay?-->
1. Seleccione **Guardar**.
1. Seleccione **Importar**.

#### <a name="edit-the-sharepoint-list-deployment-flow"></a>Editar el flujo de implementación de la lista de SharePoint

1. Una vez finalizada la importación, vaya a **Mis flujos** y actualice la lista de flujos.
1. Seleccione el flujo recién importado, **DeploySPLists**.
1. Seleccione **Editar** en la barra de comandos.
1. Abra la tarjeta **variable: sitio de destino para listas** .
1. En **valor**, escriba el nombre del sitio de SharePoint.
1. Abra la tarjeta **variable: nombre** de la aplicación.
1. En **valor**, escriba el nombre de la aplicación; de forma predeterminada, el nombre es la **comunicación de crisis**.

    ![Parámetros de flujo](media/sample-crisis-communication-app/04-Flow-Settings.png)

1. Seleccione **Guardar**.

#### <a name="run-the-sharepoint-list-deployment-flow"></a>Ejecutar el flujo de implementación de lista de SharePoint

1. Vuelva a la pantalla de detalles del flujo de **DeploySPLists** .
1. Seleccione **Ejecutar** en la barra de comandos.
1. Seleccione **continuar**y, a continuación, seleccione **Ejecutar flujo**.

    ![Iniciar sesión para ejecutar el flujo](media/sample-crisis-communication-app/sign-in-flow.png)

    ![Ejecución del flujo](media/sample-crisis-communication-app/run-flow.png)

> [!NOTE]
> Podría recibir un error que indica que se requieren servicios de ubicación.
Si esto ocurre, permitir que los servicios de ubicación accedan<!--edit okay? I wasn't sure what this meant.--> Power Automatice y actualice la página antes de volver a intentarlo.

El flujo crea las siguientes listas de SharePoint en el sitio de SharePoint.<!--general note; You don't need to introduce tables or graphics with colons, only lists.-->

| **Mostrar título**| **Propósito** | **Descripción** |
|-|-|-|
| CI_LogosAssets| Para que se haga referencia al logotipo y/u otras imágenes desde la aplicación. Se hará referencia al logotipo en Power apps mediante un vínculo directo o mediante el número de identificación del logotipo que quiere usar. | La biblioteca para los logotipos relacionados y otros recursos de imagen para la aplicación *[nombre de la aplicación]* . |
| CI_configAdminSetup | Se usa para la configuración de características del administrador de la aplicación.<br>**Nota**: esta lista debe ser de solo lectura para todos los miembros que no sean administradores. | Lista de configuración de administración para la aplicación *[nombre de la aplicación]* .
| CI_Contacts | Usar el tipo de contenido contactos predeterminado para capturar información acerca de los contactos. (No se incluye ningún selector de personas, por lo que es posible que esta lista tenga que mantenerse manualmente<!--edit okay?--> para asegurarse de que sus datos están actualizados).<br>**Nota**: esto depende de que el tipo de lista de contactos global sea un tipo de contenido predeterminado en la lista. | La lista de contactos para la aplicación *[nombre de la aplicación]* .|
| CI_CompanyNews | Colección de elementos de noticias de la **empresa** . | Una lista para administrar los elementos de noticias que aparecen en la aplicación *[nombre de la aplicación]* . Puede usar la columna en **desuso** para quitar elementos de noticias de las vistas de la aplicación.<!--edit okay, here and below? You use this pattern ("remove ___ from the app views") in the "Helpful tips" description, and it seems a bit more descriptive than "filter ___ out of the app".-->, mientras se conservan como un registro. | 
| CI_FAQ  | Preguntas más frecuentes. | La lista de preguntas más frecuentes para la aplicación *[nombre de la aplicación]* . Puede usar la columna en **desuso** para quitar los elementos de preguntas más frecuentes de las vistas de la aplicación, a la vez que los conserva como un registro. |
| CI_UsefulLinks<!--edit okay? The sharepoint-lists.png screenshot later in this article shows it as "Usefulinks," which probably isn't correct either.--> | Lista de hipervínculos útil. | La lista de hipervínculos útiles para la aplicación *[nombre de la aplicación]* . Puede usar la columna en **desuso** para quitar elementos de hipervínculo de las vistas de la aplicación, mientras que los conservan como un registro. |
| CI_Employee | Seguimiento del estado actual de presencia de los empleados. Ejemplos: **trabajar desde casa**, **sin enfermo**, **en el abandono personal**y **fuera de vacaciones**.  **Nota**: se supone que el estado **que se va a trabajar** es y no se incluye en las opciones de lista. | <!--Please check the following edit carefully. This cell was duplicated by mistake from the previous row. Does the note about the "Deprecated" column apply here?-->La lista de mensajes que indican el estado de la presencia de un empleado para la aplicación *[nombre de la aplicación]* . Puede usar la columna en **desuso** para quitar mensajes de estado de las vistas de la aplicación, a la vez que los conserva como un registro. |
| CI_HelpfulTips             | Sugerencias útiles que los usuarios han contribuido a sus colegas. | Lista para la administración de sugerencias compartidas para la aplicación *[nombre de la aplicación]* . Puede usar la columna en **desuso** para quitar sugerencias de las vistas de la aplicación, mientras se conservan como un registro.  |

> [!NOTE]
> - Todas estas columnas de la lista se deben considerar como dependencias.
    Proteja las listas de cambios de esquemas accidentales (por ejemplo, se permite agregar nuevas columnas, pero eliminar columnas podría interrumpir la aplicación).
> - Tenga cuidado al eliminar elementos de lista; la eliminación de elementos de lista elimina los registros históricos. Puede activar o desactivar el valor de degradación. <!--Style Guide-->de **no** a **sí** para quitar registros de contactos, noticias, preguntas más frecuentes o vínculos.<!--Should this include status messages too?-->

## <a name="import-and-set-up-the-crisis-communication-app"></a>Importación y configuración de la aplicación de comunicación de crisis

Una vez creadas todas las listas de SharePoint, puede importar la aplicación y conectarla a los nuevos orígenes de datos.

> [!NOTE]
> Si no desea usar la aplicación de administración, puede editar estas mismas propiedades editando las listas de SharePoint manualmente.

### <a name="import-the-app"></a>Importación de la aplicación

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
1. Seleccione **aplicaciones** en el panel de navegación izquierdo.
1. Seleccione **importar** en la barra de comandos.
1. Cargue el archivo **CrisisCommunication. zip** del repositorio de github.

    > [!NOTE]
    > Si el inquilino se encuentra en un entorno GCC, cargue **CrisisCommunicationGCC. zip**.

    ![Importar el paquete de la aplicación](media/sample-crisis-communication-app/31-Import-App.png)

1. Complete la conexión importar configuración para **Microsoft Teams** y **usuarios de Office 365** seleccionando las conexiones adecuadas mediante el hipervínculo **seleccionar durante la importación** . Es posible que tenga que crear una [nueva conexión](add-data-connection.md), si aún no existe.
1. Seleccione **Importar**.

### <a name="update-the-sharepoint-connections"></a>Actualizar las conexiones de SharePoint

1. Vuelva a la lista de **aplicaciones** .
1. Seleccione **más comandos** (...) para la aplicación de **comunicación de crisis** .
1. Seleccione **Editar** en el menú contextual.

    ![Editar la aplicación](media/sample-crisis-communication-app/05-Edit-App.png)

1. Inicie sesión o cree las conexiones necesarias y, a continuación, seleccione **permitir**.

1. Vaya a los orígenes de datos en el panel izquierdo.

    ![Orígenes de datos](media/sample-crisis-communication-app/data-sources.png)

1. Quitar las listas de SharePoint existentes dentro de la aplicación<!--Alternatively, this could be "Right-click the name of each existing SharePoint list, and then select **Remove**" if that's how the context menu works here. I think the graphic will be clear enough for the reader, though.-->, porque no apuntan al sitio de SharePoint actual.

    ![Quitar orígenes de datos](media/sample-crisis-communication-app/remove-data-source.png)

1. Agregue las listas desde su propio sitio de SharePoint. Para empezar, busque **SharePoint** en la barra de búsqueda.

    ![Buscar SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. Seleccione **SharePoint**y, a continuación, elija una conexión.

    ![Conexión de SharePoint](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Copie y pegue la dirección URL en el sitio de SharePoint en el campo de texto y, a continuación, seleccione **conectar**.

    ![Dirección URL del sitio de SharePoint](media/sample-crisis-communication-app/site-url.png)

1. Seleccione todas las listas y bibliotecas de SharePoint y, a continuación, seleccione **conectar**.

    ![Conexión a listas de SharePoint](media/sample-crisis-communication-app/sharepoint-lists.png)

1. Seleccione **Guardar**y, a continuación, seleccione **publicar**.

### <a name="optional-enable-location-updates"></a>Opcional: habilitar actualizaciones de ubicación

Esta aplicación permite registrar la ubicación de un usuario y almacenarla en el sitio de SharePoint cada vez que un usuario establece su estado. El equipo de administración de crisis puede ver estos datos en un informe de Power BI.

> [!NOTE]
> La habilitación de actualizaciones de ubicación es opcional. Puede omitir esta sección si no desea realizar un seguimiento de la ubicación del usuario.

**Para habilitar las actualizaciones de ubicación**

1. Busque el control **btnDateRange** .
1. Abra la propiedad **alseleccionar** del control **btnDateRange** en la barra de fórmulas.
1. Copie y pegue el siguiente fragmento de código en la barra de fórmulas de la propiedad **alseleccionar** .

    > [!NOTE]
    > El siguiente fragmento de código está diseñado para trabajar con versiones de la solución anteriores a 2020.03.16.


    ```
        UpdateContext({locSaveDates: true});
    // Store the output properties of the calendar in static variables and collections.
    ClearCollect(submittedDates,Sort(Filter(selectedDates,ComponentId=CalendarComponent.Id),Date,Ascending));
    Set(varStartDate,First(submittedDates).Date);
    Set(varEndDate,First(Sort(submittedDates,Date,Descending)).Date);
    // Create a new record for work status for each date selected in the date range.
    ForAll(
        Filter(
            RenameColumns(submittedDates,"Date","DisplayDate"),
            ComponentId=CalendarComponent.Id,
            !(DisplayDate in colDates.Date)
        ),
        Patch('CI_Employee Status',Defaults('CI_Employee Status'),
            {
                Title: varUser.userPrincipalName,
                Date: DisplayDate,
                Notes: "",
                PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                
                // To implement location, add a comma to the line above and uncomment the lines below for latitude and longitude.
                // Latitude: Text(Location.Latitude),
                // Longitude: Text(Location.Longitude)
            }
        )
    );
        // Update existing dates with the new status.
        ForAll(
            AddColumns(
                Filter(
                    RenameColumns(submittedDates,"Date","DisplayDate"),
                    ComponentId=CalendarComponent.Id,
                    DisplayDate in colDates.Date
                ),
                
                // Get the current record for each existing date.
                "LookUpId",LookUp(RenameColumns(colDates,"ID","DateId"),And(Title=varUser.userPrincipalName,Date=DisplayDate)).DateId
            ),
            Patch('CI_Employee Status',LookUp('CI_Employee Status',ID=LookUpId),
                {
                    PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                }
            )
        );
        If(
            IsEmpty(Errors('CI_Employee Status')),
            
            // Update the list of work status for the logged-in user.
            ClearCollect(colDates,Filter('CI_Employee Status',Title=varUser.userPrincipalName));
            // Send an email receipt to the logged-in user.
            UpdateContext(
                {
                    locReceiptSuccess: 
                    Office365Outlook.SendEmailV2(
                        // To: send an email to oneself
                        varUser.mail,
                        // Subject
                        Proper(WorkStatusComponent.Selected.Value) & ": " & varStartDate & If(varStartDate<>varEndDate," - " & varEndDate),
                        // Body
                        WorkStatusComponent.Selected.DateRangeReceipt & ": " &
                        // Create a bulleted list of dates
                        "<ul>" & 
                            Concat(submittedDates,"<li>" & Date & Char(10)) &
                        "</ul>"
                    )
                }
            );
            If(
                locReceiptSuccess,
                Notify("You successfully submitted your work status. An email has been sent to you with a summary.",NotificationType.Success,3000),
                Notify("There was an error sending an email summary, but you successfully submitted your work status.",NotificationType.Success,3000);
            );
            
            Navigate('Share to Team Screen',LookUp(colStyles,Key="navigation_transition").Value),
            
            // Case: Error submitting work status
            Notify(varString.WorkStatusError,NotificationType.Warning)
        );
        UpdateContext({locSaveDates: false})
    ```

### <a name="optional-add-additional-work-status-messages"></a>Opcional: agregar mensajes de estado de trabajo adicionales

Si desea agregar más estado de trabajo<!--Interesting fact: there is no plural of "status."--> los mensajes más allá del **trabajo desde casa** y **fuera de la oficina**, puede hacerlo completando los pasos siguientes. Para empezar, debe actualizar el sitio de SharePoint.

1. Vuelva al sitio de SharePoint y, a continuación, seleccione **contenido del sitio**.
1. Seleccione **Estado de CI_Employee**.
1. Si la columna **PresenceStatus** no está presente, seleccione **Agregar columna**.
1. Seleccione **Mostrar u ocultar columnas**.

    ![Mostrar u ocultar columnas](media/sample-crisis-communication-app/36-hide-show-columns.png)

1. Seleccionar<!--edit okay? I didn't know what "Check" meant here.--> **PresenceStatus**.
1. Haga clic en **Aplicar**.
1. Seleccione la columna **PresenceStatus** .

    ![Seleccionar la columna PresenceStatus](media/sample-crisis-communication-app/37-show-presence.png)

1. Seleccione **configuración de columnas**y, a continuación, seleccione **Editar**.

    ![Editar la columna PresenceStatus](media/sample-crisis-communication-app/38-edit-column.png)

1. Agregue los mensajes de estado de trabajo adicionales en el campo **Opciones** .

> [!NOTE]
> Anote el nombre de las nuevas opciones; los usará en pasos posteriores.

Ahora debe realizar algunos ajustes en la aplicación para mostrar los nuevos mensajes de estado de trabajo.

1. Abrir la aplicación en Power apps Studio<!--edit okay?-->.
1. Seleccione la pantalla **Estado del trabajo** .
1. Establezca la barra de fórmulas en la función **divisible** .

    ![Mostrar presencia](media/sample-crisis-communication-app/39-onvisible-for-screen.png)

1. Edite la plantilla siguiente y reemplace los valores por los suyos propios.
<!--I took the liberty of editing these strings to use contractions, which is Microsoft style now.-->
    ```
        ,"<Name of option in SharePoint list; case sensitive>",
        Table(
            {
                Icon: <Image file>,
                DateRangeQuestion: "Select the dates you'll be <Name of status>.",
                DateRangeReceipt: "You're currently <Name of status>.",
                ShareToTeamEmail: "I'll be <Name of status> on these dates",
                AutoReplyMessage: "I'll be <Name of status> on these dates"
            }
        )
    ```

1. Reemplace la cadena de `/* TEMPLATE FOR ADDITIONAL WORK STATUS OPTIONS */` por la plantilla.
1. Seleccione **Guardar**y, a continuación, seleccione **publicar**.

### <a name="update-the-request-for-help-flow"></a>Actualización de la solicitud de flujo de ayuda

Este flujo envía una tarjeta adaptable a un equipo central de equipos, solicitando ayuda.

![Solicitud de ayuda](media/sample-crisis-communication-app/21-Request-Help.png)

Antes de completar el paso siguiente, cree un equipo de administración de crisis en Teams. Después de crear el equipo, puede obtener el identificador del mismo y colocarlo en el flujo. Más información sobre cómo crear un equipo de equipos: [crear un equipo de equipos de administración de crisis central](#create-a-central-crisis-management-teams-team)

1. Vaya al canal de equipos al que desea enviar todas las solicitudes de ayuda.
1. Seleccione **más opciones** (...) para el canal.
1. Seleccione **obtener vínculo a canal**.

    ![Obtener un vínculo al canal](media/sample-crisis-communication-app/17-Get-link-to-channel.png)

1. Copie el vínculo y péguelo en un editor de texto.

    ![Copiar el vínculo del equipo](media/sample-crisis-communication-app/18-Copy-link.png)

1. Extraiga el **identificador del equipo**, que es todo después `groupId=` y antes de `&tenantId=`. <br> Por ejemplo, en la siguiente dirección URL, el ID. de canal es<!--suggest using a line break here and in the next step so you don't have to include any closing punctuation.--> <br>`8bc7c0c2-0d4c-4fb8-af99-32da74c9237b`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`
   
1. Extraiga el **identificador del canal**, que es todo después `https://teams.microsoft.com/l/channel/` y antes de `/General`. <br> Por ejemplo, en la siguiente dirección URL, el ID. de canal es<br> `19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`.

1. Vaya a [Flow.Microsoft.com](https://flow.microsoft.com).

1. Seleccione **Mis flujos** en el panel de navegación izquierdo.

1. Seleccionar **más comandos** (...)  en **CrisisCommunication. request**y seleccione **Editar**.

    ![Editar la solicitud de flujo de ayuda](media/sample-crisis-communication-app/20-Edit-Flow.png)

1. Abra la tarjeta ID. del **equipo** .

1. Pegue el identificador del equipo en el campo **valor** .

1. Abra la tarjeta ID. de **canal** .

1. Pegue el identificador de canal en el campo **valor** .

    ![Establecer identificadores de equipo y de canal](media/sample-crisis-communication-app/22-Set-Team-IDs.png)

1. Desplácese hacia abajo hasta las acciones **obtener tiempo** y actualice la acción de **convertir zona horaria** con la opción de horas de origen y destino.

    ![Convertir la configuración de zona horaria](media/sample-crisis-communication-app/convert-time-zone.png)

## <a name="optional-configure-a-shared-inbox"></a>Opcional: configurar una bandeja de entrada compartida<a name="optional-configure-shared-inbox"></a>

El flujo CrisisCommunication. request extrae las solicitudes desde la bandeja de entrada antes de enviarlas a los equipos. Si prefiere enviar correos electrónicos de solicitud a una bandeja de entrada compartida, siga estos pasos.

> [!NOTE]
> Puede omitir esta sección si no desea enviar correos electrónicos de solicitud a una bandeja de entrada compartida.

1. Abra el flujo **CrisisCommunication. request** en modo de edición.
1. Seleccione **más comandos** (...) desde el momento en que **un correo electrónico llega a V3**.
1. Seleccione **Eliminar**.

     ![Eliminar el conector](media/sample-crisis-communication-app/33-delete-connector.png)

1. Busque y seleccione **Cuándo llega un nuevo correo electrónico a un buzón compartido (V2)**.
1. Escriba la dirección de bandeja de entrada compartida en **dirección de buzón**.
1. Abra la tarjeta de **comentarios** .
1. Seleccione **Agregar un valor dinámico** para **valor**.
1. Busque y seleccione **cuerpo**.

     ![Seleccionar cuerpo](media/sample-crisis-communication-app/35-body.png)

1. Abra la tarjeta **obtener tarjeta de Perfil de usuario (V2)** .
1. Seleccione **Agregar un valor dinámico**.
1. Busque y seleccione **entre**.

     ![Seleccionar de](media/sample-crisis-communication-app/34-from.png)

## <a name="import-and-set-up-the-admin-app"></a>Importación y configuración de la aplicación de administración

Para administrar la aplicación que ha importado, repita los mismos pasos para la aplicación de administración.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
1. Seleccione **aplicaciones** en el panel de navegación izquierdo.
1. Seleccione **importar** en la barra de comandos.
1. Cargue el archivo **CrisisCommunicationAdmin. zip** del repositorio de github.

    ![Importar el paquete de la aplicación de administración](media/sample-crisis-communication-app/import-app.png)

1. Seleccione **Importar**.

### <a name="update-sharepoint-connections-for-the-admin-app"></a>Actualizar las conexiones de SharePoint para la aplicación de administración

1. Vuelva a la lista de **aplicaciones** .
1. Seleccione **más comandos** (...) para la **aplicación de administración de comunicaciones de crisis**.
1. Seleccione **Editar** en el menú contextual.

    ![Editar la aplicación de administración](media/sample-crisis-communication-app/08-Edit-Admin-App.png)

1. Inicie sesión o cree las conexiones necesarias y, a continuación, seleccione **permitir**.

1. Vaya a los orígenes de datos en el panel izquierdo.

    ![Orígenes de datos](media/sample-crisis-communication-app/data-sources.png)

1. Quite las listas de SharePoint existentes dentro de la aplicación, ya que no apuntan al sitio de SharePoint actual.<!--Please see previous editor's note.-->

    ![Quitar orígenes de datos](media/sample-crisis-communication-app/remove-data-source.png)

1. Agregue las listas desde su propio sitio de SharePoint. Para empezar, busque **SharePoint** en la barra de búsqueda.

    ![Buscar SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. Seleccione **SharePoint**y, a continuación, elija una conexión.

    ![Conexión de SharePoint](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Copie y pegue la dirección URL en el sitio de SharePoint en el campo de texto y, a continuación, seleccione **conectar**.

    ![Dirección URL del sitio de SharePoint](media/sample-crisis-communication-app/site-url.png)

1. Seleccione todas las listas y bibliotecas de SharePoint y, a continuación, seleccione **conectar**.

    ![Conexión a listas de SharePoint](media/sample-crisis-communication-app/sharepoint-lists.png)

1. Seleccione **Guardar**y, a continuación, seleccione **publicar**.

## <a name="create-initial-content-for-the-app"></a>Crear contenido inicial para la aplicación

En este punto, ha importado correctamente la aplicación de comunicación de crisis y su aplicación de administración. Ahora puede empezar a crear el contenido inicial. Para empezar, abra la aplicación de administración de comunicaciones de crisis.

Si tiene un entorno GCC, debe habilitar el modo GCC. Más información: [Cómo configurar clientes móviles para entornos GCC](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#configure-mobile-clients).

![La aplicación de administración de comunicaciones de crisis](media/sample-crisis-communication-app/09-Admin-App.png)

La aplicación de administración se usa para personalizar toda la información de la aplicación de comunicación de crisis y también para configurar las opciones de clave de los flujos que lo acompañan.

> [!NOTE]
> Como recordatorio&mdash;si no desea usar la aplicación de administración, puede editar estas propiedades editando las listas de SharePoint manualmente.

### <a name="set-up-key-parameters-under-admin-settings"></a>Configurar parámetros de clave en la configuración de administración

Para inicializar la aplicación, debe proporcionar todos los campos obligatorios. para ello, vaya a **configuración de administración**.

Complete todos los campos como se muestra en la tabla siguiente y, a continuación, seleccione **Guardar**.

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** | **Ejemplo** |
|-|-|-|-|
| Correo electrónico de administrador | AdminContactEmail | Aquí es donde se envían las solicitudes de correo electrónico. Deben establecerse en su dirección de correo electrónico. Si desea enviar notificaciones a otra bandeja de entrada, consulte [configuración opcional de bandeja de entrada compartida](#optional-configure-shared-inbox), anteriormente en este artículo. | admin@contoso.com |
| URL del logotipo | Logotipo | El logotipo de la aplicación que aparece en la esquina superior izquierda. | https://contoso.com/logo.png |
| IDENTIFICADOR de grupo de AAD | AADGroupID | Se usa para enviar notificaciones a los usuarios acerca de las actualizaciones internas de la empresa a través de las **noticias notificar a los usuarios acerca de nuevas crisis**<!--Can you rename this flow to "Notify users of new crisis communication news"? Or maybe even "Notify users of breaking news about the crisis"?--> transmite. Siga las instrucciones siguientes para obtener el identificador de Azure Active Directory (Azure AD) del grupo. | c0ddf873-b4fe-4602-b3a9-502dd944c8d5 |
| URL DE APLICACIÓN | AppURL | La ubicación de la aplicación de usuario, de modo que el flujo de **noticias notificar a los usuarios sobre nuevas comunicaciones de crisis** puede redirigir a los usuarios allí después de seleccionar **leer más**. | https://apps.preview.powerapps.com/play/<app URL>? tenantId =<tenant ID>
| Fuente RSS de gobierno | GovernmentRSSFeed | Se usa para rellenar la característica de noticias mundiales en la aplicación. Resulta útil si desea proporcionar información adicional a sus empleados desde una fuente de confianza. | https://www.who.int/rss-feeds/news-english.xml |
| Método de notificación | PreferredSentNotification | Lo usa el flujo **de noticias notificar a los usuarios sobre nuevas comunicaciones de crisis** para determinar qué canal de distribución debe usar al enviar notificaciones. Este campo es obligatorio. | Correo electrónico, notificación de equipos, notificación de extracción |
| Marcas de características | Feature1... 203 | Se usa para deshabilitar o habilitar cada característica en la aplicación. |  |

> [!NOTE]
> La notificación de equipos y las notificaciones de extracción no se admiten actualmente en GCC.


#### <a name="finding-the-azure-ad-id-for-your-distribution-group"></a>Búsqueda del identificador de Azure AD del grupo de distribución
<!--note from editor: The Cloud Style Guide says don't use "AAD" for "Azure AD."-->
1. Vaya a [AAD.portal.Azure.com](https://aad.portal.azure.com).
1. Seleccione **Azure Active Directory** en el panel de navegación izquierdo.
1. Seleccione **grupos**.
1. Busque y seleccione el grupo de distribución.
1. Copie el campo ID. de **objeto** .

    ![Obtención del identificador de Azure AD](media/sample-crisis-communication-app/11-AAD-Group-ID.png)

1. Pegue el identificador en el campo ID. de **grupo de AAD** en la aplicación de administración.<!--Can you have this changed to "Azure AD group ID"? -->

### <a name="set-up-emergency-contacts"></a>Configurar contactos de emergencia

1. Vaya a **contactos**de la empresa.
1. Seleccione **crear nuevo contacto**.
1. Rellene el formulario con los detalles de contacto.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Nombre completo | FullName | Nombre del contacto. |
| Correo electrónico | Correo electrónico | La dirección de correo electrónico que se muestra para el contacto. |
| País | País | País del contacto. Este campo se utiliza para agrupar los contactos; puede usar otros valores para agrupar contactos por si los países no tienen sentido. |
| Comentarios | Comentarios | Muestra información adicional sobre el contacto; útil para describir cuándo ponerse en contacto con este contacto. |
| Obsoleto | Obsoleto | Use para ocultar un contacto de emergencia existente. |

### <a name="set-up-initial-company-news"></a>Configuración de noticias iniciales de la empresa

1. Vaya a **noticias**de la compañía.
1. Seleccione **crear nueva publicación**.
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | Título de la actualización. |
| Detalles | Detalles | La actualización completa. Puede usar HTML en este campo. |
| Promociona | Promociona | Un mensaje breve acerca de la actualización. Se usa en el flujo de **noticias notificar a los usuarios sobre nuevas comunicaciones de crisis** y en la galería de actualizaciones. |
| Obsoleto | Obsoleto | Use para ocultar una publicación existente. |

### <a name="set-up-helpful-tips"></a>Configurar sugerencias útiles

1. Vaya a **sugerencias útiles**.
1. Seleccione **nueva sugerencia**.
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | Título de la sugerencia útil. |
| Dirección URL del recurso | ResourceURL | Vínculo a material de lectura adicional. (Opcional) |
| Subtítulo | Básicas | Un subtítulo de la sugerencia. (Opcional) |
| Descripción | Descripción | Descripción completa de la sugerencia útil. |
| Obsoleto | Obsoleto | Use para ocultar una sugerencia útil. |

### <a name="set-up-links"></a>Configurar vínculos

1. Vaya a **vínculos**.
1. Seleccione **crear nuevo vínculo**.
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | Texto del vínculo. |
| URL | URL | Dirección URL del vínculo. |
| Descripción | Descripción | Detalles adicionales sobre el vínculo. (Opcional) |
| Obsoleto | Obsoleto | Use para ocultar un vínculo. |

### <a name="set-up-faqs"></a>Configuración de preguntas más frecuentes

1. Vaya a **preguntas más frecuentes**.
1. Seleccione **crear nuevas preguntas más frecuentes**.
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | La pregunta en las preguntas más frecuentes. |
| Clasificación | Clasificación | El orden de la pregunta en las preguntas más frecuentes. |
| Respuesta | Respuesta | La respuesta a la pregunta en las preguntas más frecuentes. |
| Obsoleto | Obsoleto | Use para ocultar una pregunta en las preguntas más frecuentes. |

## <a name="test-and-share-the-app"></a>Prueba y uso compartido de la aplicación

Ahora que ha configurado correctamente todos los datos, puede probar la aplicación para asegurarse de que funciona.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
2. Seleccione **aplicaciones** en el panel de navegación izquierdo.
3. Seleccione **comunicación de crisis** para reproducir la aplicación.

Una vez que haya probado correctamente la aplicación, puede compartirla con todos los usuarios de su empresa.

## <a name="import-and-set-up-the-notification-flow"></a>Importar y configurar el flujo de notificación

La aplicación usa un flujo para enviar notificaciones a los usuarios finales cada vez que hay una nueva actualización de la compañía.

### <a name="import-the-news-notification-flow"></a>Importar el flujo de notificaciones de noticias

1. Vaya a [Flow.Microsoft.com](https://flow.microsoft.com).
1. Seleccione **Mis flujos** en el panel de navegación izquierdo.
1. Seleccione **importar** en la barra de comandos.
1. Cargue el paquete **CrisisCommunicationNewsNotification. zip** del repositorio de github.

    > [!NOTE]
    > Si el inquilino se encuentra en un entorno GCC, cargue **CrisisCommunicationNewsNotificationGCC. zip**.

    ![Carga de CrisisCommunicationNewsNotification. zip](media/sample-crisis-communication-app/upload-news-notification.png)

1. Agregue conexiones para el nuevo flujo seleccionando el vínculo **seleccionar durante la importación** para cada conexión y, a continuación, rellene el formulario.

    ![Seleccionar durante la importación](media/sample-crisis-communication-app/select-during-import.png)

1. Si necesita crear una nueva conexión, seleccione **crear nuevo** en el panel **importar configuración** .
1. Seleccione **nueva conexión** en la barra de comandos.

    ![Creación de una nueva conexión](media/sample-crisis-communication-app/create-connection.png)

1. Busque el nombre de la conexión; por ejemplo, **notificación de PowerApps (versión preliminar)**.

    ![Nombre de conexión de ejemplo](media/sample-crisis-communication-app/notifications.png)

1. Seleccione la conexión que desee.
1. Si va a crear una conexión a las **notificaciones de PowerApps (versión preliminar)**, verá el cuadro de diálogo tal como se muestra en la siguiente imagen.

    ![Cuadro de diálogo notificaciones](media/sample-crisis-communication-app/notifications-dialog.png)

1. Para obtener el identificador, vaya a la lista de **aplicaciones** .
1. Seleccione **más comandos** (...) para la aplicación de **comunicación de crisis** y, a continuación, seleccione **detalles**.

    ![Detalles de la conexión](media/sample-crisis-communication-app/06-App-Details.png)

1. Copie el **Id. de aplicación**.

    ![IDENTIFICADOR de la aplicación](media/sample-crisis-communication-app/07-App-ID.png)

1. Pegue el identificador de la aplicación en el cuadro de diálogo creación de conexión y, a continuación, seleccione **crear**.

    ![Crear una conexión](media/sample-crisis-communication-app/target-app-id.png)

1. Una vez creada la nueva conexión, vuelva al panel **importar configuración** y seleccione **Actualizar lista**.
1. Ahora debería aparecer la nueva conexión. Selecciónelo y, a continuación, seleccione **Guardar**.
1. Cuando haya terminado de agregar todas las conexiones, seleccione **importar**.

    ![Importación de conexiones](media/sample-crisis-communication-app/imported-connections.png)

### <a name="edit-the-news-notification-flow"></a>Editar el flujo de notificación de noticias

1. Una vez finalizada la importación, vaya a **Mis flujos**.
1. Seleccione el flujo recién importado y **notifique a los usuarios nuevas noticias sobre la comunicación de crisis**.

    > [!NOTE]
    > Si cargó el paquete GCC, el nombre de flujo es **notificar a los usuarios sobre las novedades de la comunicación de crisis en gcc**.

1. Seleccione **Editar** en la barra de comandos.
1. Abra la tarjeta **cuando se publique un nuevo elemento** .
1. En **dirección del sitio**, escriba el nombre del sitio de SharePoint.
1. En **nombre de lista**, escriba **CI_CompanyNews**.
1. Abra la tarjeta **obtener opciones de configuración de administración** .
1. En **dirección del sitio**, escriba el nombre del sitio de SharePoint.
1. En **nombre de lista**, escriba **CI_configAdminSetup**.
1. Abra la **variable Initialize: leer más** tarjeta de texto.
1. En **valor**, escriba **leer más** (en el lenguaje nativo).

    ![Configuración de Flow](media/sample-crisis-communication-app/flow-options.png)

1. Seleccione **Guardar**.

> [!NOTE]
> Es posible que reciba un error si aún no se ha autorizado una de las conexiones.
Si esto ocurre, abra la tarjeta con la conexión no autorizada y vuelva a autorizarla.


### <a name="optional-sending-notifications-to-more-than-5000-users"></a>Opcional: envío de notificaciones a más de 5000 usuarios

La acción **obtener miembros del grupo** actual está limitada a la extracción de 5000 usuarios si usa la licencia de Office de Power Automatic. Si tiene una licencia Premium y desea distribuir hasta 100000 usuarios, puede seguir estos pasos para enviar a más usuarios.

1. Seleccione el menú **...** para la tarjeta **obtener miembros del grupo** .

    ![Seleccione... MENU](media/sample-crisis-communication-app/40-Settings.png)

1. Seleccione **Configuración**.

1. Cambie el campo **umbral** a 100.000

    ![Establecimiento del campo umbral](media/sample-crisis-communication-app/41-Threshold.png)

1. Seleccionar **listo**

1. Seleccione **Guardar**.

### <a name="test-the-news-notification-flow"></a>Probar el flujo de notificación de noticias

Para probar el flujo de notificaciones de noticias, vaya a la aplicación de administración y cree una nueva actualización interna de la empresa. Más adelante, todos los usuarios de la lista de distribución recibirán una actualización del método de notificación que prefiera.

> [!NOTE]
> Si se producen errores, asegúrese de que ha escrito correctamente el identificador de grupo de la lista de distribución en la configuración de la aplicación de administración.

## <a name="monitor-office-absences-with-power-bi"></a>Supervisar las ausencias de Office con Power BI

Después de haber implementado la aplicación y de que los usuarios empiecen a enviar notificaciones que estarán fuera de la oficina por diversos motivos (por ejemplo, por enfermedad o trabajando desde casa), puede usar un informe de Power BI para realizar un seguimiento del número de personas que han enviado notificaciones y dónde se encuentran.  
Tenga en cuenta que debe [Habilitar el seguimiento de ubicación](#optional-enable-location-updates) para que el control de mapa funcione. 

> [!IMPORTANT]
> Para que el informe de Power BI funcione, debe tener al menos una entrada en la lista **Estado de CI_Employee** .

Necesitaremos información de la lista de SharePoint de **estado CI_Employee** que hemos creado anteriormente, así que vamos a obtenerla primero. Abra la lista en el sitio y, a continuación, seleccione Configuración de la **lista** en el icono de **configuración** .

![Configuración de la lista de estado de empleado](media/sample-crisis-communication-app/001-SharePointList-ListSettings-nolines.PNG)

Anote el nombre del sitio y el ID. de la lista en la barra de direcciones del explorador, tal como se muestra en la siguiente imagen.

![Lista de Estados de empleados e ID. de sitio](media/sample-crisis-communication-app/002-SharePointList-AddressAndId-nolines.PNG)

En este momento, estamos listos para abrir el informe de Power BI. Abra Power BI y, a continuación, abra el archivo **. pbix de informe de estado de presencia** . Mantenga el mouse sobre el lado derecho del origen de datos de **Estado de CI_Employee** hasta que vea los puntos suspensivos. Selecciónelo y, a continuación, seleccione **Editar consulta**.

![Editar consulta](media/sample-crisis-communication-app/003-PowerBI-EditQuery-nolines.PNG)

Una vez abierto el editor de Power Query, haga clic con el botón secundario en el origen de datos de **Estado de CI_Employee** y seleccione **editor avanzado**.

![Power Query Editor avanzado](media/sample-crisis-communication-app/004-PowerQuery-AdvancedEditor-nolines.PNG)

Aquí es donde usamos el nombre del sitio y el ID. de lista de la lista de SharePoint.

Copie el nuevo sitio de SharePoint en la cadena SharePoint. Tables tal como se muestra en la siguiente ilustración.<!--Edit okay? This is a case where the image shows information that the text doesn't, so I'm not sure how to make this descriptive enough for people who aren't looking at the graphics, or people with low vision.--> y el ID. de lista en los tres lugares donde se resalta el GUID y, a continuación, seleccione **listo**.

![Power Query actualizaciones de Editor avanzado](media/sample-crisis-communication-app/005-PowerQuery-AdvancedEditorUpdates-nolines.PNG)

Si ve algún error de conexión después de actualizar la información de conexión, es posible que tenga que actualizar las credenciales usadas para conectarse a la lista de SharePoint. 

**Para actualizar la conexión**

1. En el menú **archivo** , seleccione **Opciones y configuración**y, a continuación, seleccione **configuración de origen de datos**.

    ![Configuración de origen de datos](media/sample-crisis-communication-app/PBI-1-DataSourceSettings.PNG)

1. Seleccione **Editar permisos**.

    ![Editar permisos](media/sample-crisis-communication-app/PBI-2-DataSourceSettings-EditPermissions.PNG)

1. Asegúrese de que el tipo de **credenciales** está establecido en **cuenta de organización**y use las credenciales para tener acceso a la lista de SharePoint.

    ![Editar permisos](media/sample-crisis-communication-app/PBI-3-OrganizationalAccount.PNG)

Seleccione **cerrar & aplicar** para actualizar el informe y extraer los datos de la lista de SharePoint.

![Power Query cerrar y aplicar](media/sample-crisis-communication-app/006-PowerQuery-CloseAndApply-nolines.PNG)

Ahora tenemos un informe de Power BI que muestra tanto la información geográfica de las ausencias de Office para el día actual como una tendencia de dichas ausencias durante varios días. Podemos publicar el informe para que otras personas de la organización puedan verlo.

![Power BI publicar informe](media/sample-crisis-communication-app/007-PowerBI-Publish-nolines.PNG)

El informe ya está publicado. Puede compartirlo con otros usuarios de su organización. También puede [programar la frecuencia de actualización del informe](https://docs.microsoft.com/power-bi/refresh-scheduled-refresh).

## <a name="integrate-your-app-into-teams"></a>Integre su aplicación en Teams

Ahora que tiene una aplicación en funcionamiento que se ha compartido con todos los usuarios, puede implementar la aplicación mediante la creación de un equipo de administración de crisis dentro de los equipos para responder a los problemas.

### <a name="deploy-the-app-to-the-app-bar"></a>Implementación de la aplicación en la barra de la aplicación

Si es un administrador de equipos, puede enviar la aplicación a todos los usuarios en la barra de la aplicación Teams.

![Barra de la aplicación en Teams](media/sample-crisis-communication-app/19-App-in-Teams.png)

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
1. Seleccione **aplicaciones** en el panel de navegación izquierdo.
1. Seleccione **más comandos** (...) para la aplicación de **comunicación de crisis** .
1. Seleccione **Agregar a equipos**.

    ![Agregar a equipos](media/sample-crisis-communication-app/24-Add-to-Teams.png)

1. Seleccione **Descargar aplicación**.

    ![Descargar aplicación](media/sample-crisis-communication-app/25-Download-App.png)

1. Abra Teams.
1. Vaya a **aplicaciones** en la barra de la aplicación.
1. Seleccione **cargar una aplicación personalizada**.
1. Si es un administrador de equipos, podrá cargar una aplicación para todo el inquilino. Seleccione **cargar para contoso** (donde *contoso* representa el nombre de su inquilino).<!--Edit okay? The screenshot said "Contoto," which I fixed.-->.

    ![Carga de la aplicación](media/sample-crisis-communication-app/26-Upload-for-Contoso.png)

1. Cargue el archivo que descargó de Power apps.
1. Vaya al [centro de administración de equipos](https://admin.teams.microsoft.com/dashboard).
1. En el panel de navegación izquierdo, en **aplicaciones de equipo**, seleccione **directivas de configuración**.

    ![Directivas de configuración de aplicaciones](media/sample-crisis-communication-app/27-Setup-Policies.png)

1. Seleccione **global (configuración de toda la organización)**.
1. Seleccione **agregar aplicaciones**.

    ![Agregar aplicación](media/sample-crisis-communication-app/28-Add-App.png)

1. Busque y seleccione la aplicación de **información de crisis** que ha cargado.

    ![Agregar aplicación anclada](media/sample-crisis-communication-app/29-Add-Pinned-App.png)

1. Seleccione **Agregar**.
1. Seleccione **Guardar**.

> [!NOTE]
> Los usuarios pueden tardar hasta 24 horas en ver la aplicación anclada automáticamente en la barra de la aplicación.

### <a name="create-a-central-crisis-management-team-in-teams"></a>Crear un equipo central de administración de crisis en Teams<a name="create-a-central-crisis-management-teams-team"></a>

Para coordinar la respuesta de crisis, querrá crear un equipo central de administración de crisis en Teams y rellenarlo con toda la información pertinente. Este equipo solo debe compartirse con el equipo de respuesta central.

1. Vaya a equipos.
1. Seleccione **equipos** en la barra de la aplicación izquierda.
1. Seleccione **unirse o crear un equipo**.
1. Seleccione **crear equipo**y, a continuación, complete los pasos restantes.

    ![Crear un equipo](media/sample-crisis-communication-app/23-Create-Team.png)

Después de haber creado correctamente el equipo, puede anclar la información relevante como pestañas. Por ejemplo, puede que desee anclar la aplicación de administración de crisis para el equipo o el Power BI informe.

**Para agregar la aplicación de administración como una pestaña**

1. Seleccione el botón **+** .
1. Busque y seleccione **Power apps**.
1. Busque y seleccione **Administración de información de crisis**.

    ![Anclar aplicación](media/sample-crisis-communication-app/32-Pin-Teams-app.png)

1. Seleccione **Guardar**.

**Para agregar el informe Power BI como una pestaña**

1. Seleccione el botón **+** .
1. Busque y seleccione **Power BI**.
1. Busque y seleccione el informe de Power BI.
1. Seleccione **Guardar**.

## <a name="faq"></a>Preguntas más frecuentes

* **¿Qué licencias necesito para ejecutar esta solución?**

    - La solución de esta aplicación usa conectores de Office, por lo que una licencia de Power apps inicializada de Office es suficiente para ejecutar y reproducir las aplicaciones de usuario y de administración. Más información: [Introducción a las licencias](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus) de la plataforma de energía
    - Si desea usar el informe de Power BI (empaquetado como parte de la solución), necesitará una licencia de Power BI. Más información: [Power BI precios](https://powerbi.microsoft.com/pricing/)

* **¿Dónde debo ir si tengo comentarios sobre la solución?**

    Nos encantaría conocer su experiencia en la implementación y personalización de esta solución. Para compartir su experiencia, vaya a [aka.ms/crisis-Communication-feedback](https://aka.ms/crisis-communication-feedback).

* **Parece que he encontrado un error con la aplicación; ¿Dónde debo ir?**

   Para archivar un error con la solución, vaya a [aka.ms/crisis-Communication-issues](https://aka.ms/crisis-communication-issues).

* **¿Qué características no se admiten actualmente en GCC?**

    El conector Power Automate de robot para equipos y el conector de notificaciones de extracción no están disponibles actualmente para GCC. Use la opción correo electrónico para avisar a los usuarios acerca de las actualizaciones de noticias internas en su lugar.

* **¿Cómo puedo actualizar la aplicación?**

    Si desea actualizar la aplicación, siga los pasos descritos en [aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution).

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para obtener comentarios sobre la plantilla de ejemplo de comunicación de crisis, vaya a [aka.ms/crisis-Communication-feedback](https://aka.ms/crisis-communication-feedback).
- Para notificar un problema con la aplicación de comunicación de crisis, vaya a [aka.ms/crisis-Communication-issues](https://aka.ms/crisis-communication-issues).

***Declinación de responsabilidades:*** *esta aplicación es un ejemplo y se puede usar con Microsoft Power apps y los equipos para la diseminación de información de referencia únicamente. Esta aplicación no está prevista ni está disponible para su uso como dispositivo médico, soporte clínico, herramienta de diagnóstico u otra tecnología pensada para usarse en el diagnóstico, la cura, la mitigación, el tratamiento o la prevención de la enfermedad o en otras condiciones, y Microsoft no concede ninguna licencia o derecho para usar esta aplicación con este fin.  Esta aplicación no está diseñada ni pretende ser un sustituto de asesoramiento médico profesional, diagnóstico, tratamiento o valoración y no debe usarse como tal.  El cliente asume el único riesgo y responsabilidad de cualquier uso de esta aplicación.  Microsoft no garantiza que la aplicación o los materiales proporcionados en la conexión serán suficientes para fines médicos o para cumplir los requisitos sanitarios de cualquier persona.* 

### <a name="see-also"></a>Vea también
<!--note from editor: "Next steps" would work if you gave the reader some action items, but reference topics are random access by nature, so the heading is rightly "See also." -->
- [Referencia sobre fórmulas](formula-reference.md)
- [Referencia sobre controles](reference-properties.md)
