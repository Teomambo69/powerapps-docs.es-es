---
title: 'Aplicación de comunicación de crisis: plantilla de ejemplo | Microsoft Docs'
description: Obtenga información sobre la plantilla de ejemplo de comunicación de crisis en Power apps.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/12/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ce3974f399948f1f9ccd125c0b9727f51abc644b
ms.sourcegitcommit: 3066c2800a939fbcaaac4262c802843e2d80b88c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431863"
---
# <a name="set-up-and-learn-about-the-crisis-communication-sample-template-in-power-apps"></a>Configuración y información sobre la plantilla de ejemplo de comunicación de crisis en Power apps

Instrucciones paso a paso para instalar y configurar la aplicación de comunicación de crisis para Power apps.

Tiempo estimado para completar estos pasos: **20-25 minutos**

## <a name="overview-of-the-app"></a>Información general de la aplicación

La aplicación de *comunicación de crisis* proporciona una experiencia fácil de utilizar para conectar a los usuarios finales con información sobre una crisis. Reciba rápidamente actualizaciones de noticias internas de la empresa, Obtenga respuestas a las preguntas más frecuentes y obtenga acceso a información importante, como vínculos y contactos de emergencia. Esta aplicación requiere un mínimo de configuración para personalizarla.

En este tutorial, aprenderá a:
- Crear una ubicación para los datos
- Importar la aplicación de comunicación de crisis y su aplicación de administración
- Crear contenido para la aplicación
- Importar flujos para enviar notificaciones a los usuarios
- Crear un equipo de equipos administrados centralmente para agregar datos y responder eficazmente a los problemas

> [!NOTE]
> La plantilla de ejemplo de comunicación de crisis también está disponible para los planes Power apps y Power automatice US Government. Las direcciones URL de servicio para Power apps y Power automatice la versión de la administración pública de EE. UU. son diferentes de la versión comercial. Más información: las [direcciones URL del servicio de administración pública de EE. UU.](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#power-apps-us-government-service-urls) y la potencia de las [direcciones URL del servicio gobierno de EE. UU.](https://docs.microsoft.com/power-automate/us-govt#power-automate-us-government-service-urls)

## <a name="demo-crisis-communication-app"></a>Demostración: aplicación de comunicación de crisis

Vea cómo usar la solución de comunicación de crisis:

> [!VIDEO https://www.youtube.com/embed/23SypLXiOTw]

## <a name="prerequisites"></a>Requisitos previos

- [Regístrese](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) para Power apps.
- Debe tener una licencia de SharePoint Online válida y permisos para crear listas.
- Debe tener un sitio de SharePoint público en el que pueda almacenar los datos de la aplicación.
- Descargue los recursos de [aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution).

> [!IMPORTANT]
> Para cualquier comentario o problema relacionado con la **aplicación de comunicación de crisis**, use los vínculos siguientes:
> - **[Los](https://aka.ms/crisis-communication-feedback)**
> - **[Problemas](https://aka.ms/crisis-communication-issues)**

## <a name="demo-build-and-deploy-crisis-communication-app"></a>Demostración: creación e implementación de una aplicación de comunicación de crisis

Vea cómo compilar e implementar la aplicación de comunicación de crisis:

> [!VIDEO https://www.youtube.com/embed/Wykrwf9dZ-Y]

## <a name="create-a-home-for-your-data"></a>Crear un hogar para los datos

Los datos de la aplicación residirán en las listas de SharePoint. En primer lugar, es necesario crear un nuevo sitio de SharePoint para comenzar.

### <a name="create-a-sharepoint-site"></a>Crear un sitio de SharePoint

1. Inicie sesión en [Office Online](https://www.office.com) y seleccione **SharePoint**.
1. Seleccione crear sitio y seleccione siguiente:

    ![Sitio de SharePoint de ejemplo](media/sample-crisis-communication-app/01-Create-Site.png)

1. Seleccionar sitio de Grupo:

    ![Sitio de grupo](media/sample-crisis-communication-app/02-Team-Site.png)

1. Asigne un nombre y una descripción al sitio.
1. Establezca la configuración de privacidad en pública para que todos los usuarios de la empresa puedan obtener la información necesaria:

    ![Configuración del sitio](media/sample-crisis-communication-app/03-Privacy-Settings.png)

1. Seleccione Siguiente.
1. Opcionalmente, agregue propietarios adicionales.
1. Seleccione Finalizar.

### <a name="create-the-sharepoint-lists-for-app"></a>Crear las listas de SharePoint para la aplicación
La aplicación requiere varias listas que almacenan todos los datos. Para automatizar la creación de las listas de SharePoint, puede usar el flujo *DeploySPLists* disponible en el [paquete de recursos](#prerequisites)descargados.

#### <a name="import-the-sharepoint-list-deployment-flow"></a>Importar el flujo de implementación de la lista de SharePoint
1. Vaya a [Flow.Microsoft.com](https://flow.microsoft.com)
1. Seleccione **Mis flujos** en el panel de navegación izquierdo.
1. Seleccione el botón **importar** en la barra de comandos.
1. Cargue el paquete **DeploySPList. zip** del repositorio de github.

    ![Importar paquete](media/sample-crisis-communication-app/import-package.png)

1. Agregue una conexión de SharePoint para el nuevo flujo; para ello, seleccione el vínculo **seleccionar durante la importación** y rellene el formulario.

    ![Importar configuración](media/sample-crisis-communication-app/import-settings.png)

1. Si necesita crear una nueva conexión de SharePoint, empiece seleccionando **crear nuevo** en el panel importar configuración.
1. Seleccione **nueva conexión** en la barra de comandos:

    ![Creación de una nueva conexión](media/sample-crisis-communication-app/create-connection.png)

1. Busque el nombre de la conexión, por ejemplo *SharePoint*.
1. Seleccione la conexión adecuada.
1. Seleccione **Guardar**.
1. Seleccione **Importar**.

#### <a name="edit-the-sharepoint-list-deployment-flow"></a>Editar el flujo de implementación de la lista de SharePoint

1. Una vez finalizada la importación, vuelva a **Mis flujos** y actualice la lista de flujos.
1. Seleccione el flujo recién importado **DeploySPList**.
1. Seleccione **Editar** en la barra de comandos.
1. Abra la tarjeta llamada **variable: sitio de destino para listas**.
1. Cambie el valor al nombre de su sitio de SharePoint.
1. Abra la tarjeta denominada **variable: nombre**de la aplicación.
1. Cambie el valor por el nombre de la aplicación; de forma predeterminada, es "comunicación de crisis".

    ![Parámetros de flujo](media/sample-crisis-communication-app/04-Flow-Settings.png)

1. Seleccione **Guardar** para confirmar los cambios.

#### <a name="run-the-sharepoint-list-deployment-flow"></a>Ejecutar el flujo de implementación de lista de SharePoint

1. Vuelva a la pantalla de detalles del **flujo de DeploySPList.**
1. Seleccione **Ejecutar** en la barra de comandos.
1. Seleccione **continuar** y, a continuación, **Ejecutar flujo** para desencadenar el flujo.

    ![Iniciar sesión para ejecutar el flujo](media/sample-crisis-communication-app/sign-in-flow.png)

    ![Ejecución del flujo](media/sample-crisis-communication-app/run-flow.png)

> [!NOTE]
> Es posible que reciba un error que indica que se requieren servicios de ubicación.
Si esto ocurre, permita que los servicios de ubicación alimenten y actualicen la página antes de volver a intentarlo.

A continuación, el flujo creará las siguientes listas de SharePoint en el sitio de SharePoint:

| **Mostrar título**| **Propósito** | **Descripción** |
|-|-|-|
| CI_LogosAssets| Para mantener el logotipo y/u otras imágenes a las que se hace referencia desde la aplicación. Se hará referencia al logotipo en Power apps mediante un vínculo directo o mediante el número de identificación del logotipo deseado. | Biblioteca para los logotipos relacionados y otros recursos de imagen para la aplicación [nombre de la aplicación]. |
| CI_configAdminSetup | Para la configuración de características del administrador de la herramienta. **Nota**: esta lista solo debe leerse para todos los miembros que no sean administradores. | Lista de configuración de administración para la aplicación [nombre de la aplicación].
| CI_Contacts | Usar el tipo de contenido contactos predeterminado para capturar información acerca de los contactos. (No se incluye ningún selector de personas, por lo que puede requerir mantenimiento para asegurarse de que los datos estén actualizados).  **Nota**: esto depende del tipo de lista de contactos global como un tipo de contenido predeterminado en la lista. | Lista de contactos para la aplicación [nombre de la aplicación].|
| CI_CompanyNews | Colección de elementos de noticias de la empresa. | Lista para la administración de los elementos de noticias visibles en la aplicación [nombre de la aplicación]. La columna en desuso se puede usar para filtrar elementos de noticias de la aplicación (retenerlos como un registro). | 
| CI_FAQ  | Preguntas más frecuentes. | Preguntas más frecuentes sobre la aplicación [nombre de la aplicación]. La columna en desuso se puede usar para filtrar elementos de preguntas más frecuentes de la aplicación (retenerlos como un registro). |
| CI_UsefullLinks | Lista de hipervínculos útiles | Lista de hipervínculos útil para la aplicación [nombre de la aplicación]. La columna desusada se puede usar para filtrar elementos de hipervínculo de la aplicación (retenerlos como un registro). |
| CI_Employee | Seguimiento del estado actual de presencia de los empleados. Ejemplos: *trabajar desde casa*; *enfermo*; *en el abandono personal*; y *fuera de vacaciones*.  **Nota**: se supone *que se va a trabajar* y no se incluye en las opciones de lista. | Lista de hipervínculos útil para la aplicación [nombre de la aplicación]. La columna desusada se puede usar para filtrar los elementos de los vínculos de la aplicación (retenerlos como un registro). |
| CI_HelpfulTips             | Los usuarios pueden aportar sugerencias útiles a los compañeros. | Lista para la administración de sugerencias compartidas para la aplicación [nombre de la aplicación]. La columna en desuso se puede usar para quitar sugerencias de las vistas de la aplicación (que se conservan como un registro en SPO).  |

> [!NOTE]
> - Todas las columnas de la lista enumeradas anteriormente se deben considerar como dependencias.
    Proteja las listas de cambios de esquemas accidentales (por ejemplo, se permite agregar nuevas columnas, pero eliminar columnas puede interrumpir la aplicación).
> - Tenga cuidado al eliminar elementos de lista; la eliminación de elementos de lista elimina los registros históricos. Puede alternar el valor de desuso de *no* a *sí* para quitar registros de contactos, noticias, preguntas más frecuentes o vínculos.

## <a name="import-and-set-up-the-crisis-communication-app"></a>Importación y configuración de la aplicación de comunicación de crisis

Ahora que se han creado todas las listas de SharePoint, ahora puede importar la aplicación y conectarla a los nuevos orígenes de datos.

> [!NOTE]
> Si no desea usar la aplicación de administración, también puede editar estas mismas propiedades editando las listas de SharePoint manualmente.

### <a name="import-the-app"></a>Importación de la aplicación

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
1. Seleccione **aplicaciones** en el panel de navegación izquierdo.
1. Seleccione **importar** en la barra de comandos.
1. Cargue el archivo **CrisisCommunication. zip** del repositorio de github:

    > [!NOTE]
    > Si el inquilino está en el entorno GCC, use **CrisisCommunicationGCC. zip**.

    ![Importar paquete de aplicación](media/sample-crisis-communication-app/31-Import-App.png)

1. Complete la conexión **importar configuración** para la **conexión de Microsoft Teams** y **los usuarios de Office 365** seleccionando las conexiones adecuadas mediante *seleccionar durante la importación* . Es posible que tenga que crear una [nueva conexión](add-data-connection.md) si ya no existe.
1. Seleccione **Importar**.

### <a name="update-the-sharepoint-connections"></a>Actualizar las conexiones de SharePoint

1. Vuelva a la lista de **aplicaciones** .
1. Seleccione **más comandos** (...) para la aplicación de **comunicación de crisis** .
1. Seleccione **Editar** en el menú contextual:

    ![Editar la aplicación](media/sample-crisis-communication-app/05-Edit-App.png)

1. **Inicie sesión** o cree las conexiones necesarias y seleccione **permitir**.

1. Navegue a los orígenes de datos en el panel izquierdo:

    ![Orígenes de datos](media/sample-crisis-communication-app/data-sources.png)

1. **Quite** las listas de SharePoint existentes dentro de la aplicación, ya que no apuntan al sitio de SharePoint actual:

    ![Quitar orígenes de datos](media/sample-crisis-communication-app/remove-data-source.png)

1. Agregue las listas desde su propio sitio de SharePoint. Para empezar, busque SharePoint en la barra de búsqueda:

    ![Buscar en SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. Seleccione **SharePoint** y elija una conexión:

    ![Conexión de SharePoint](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Copie y pegue la dirección URL en el sitio de SharePoint en el campo de texto y seleccione **conectar**:

    ![Dirección URL del sitio de SharePoint](media/sample-crisis-communication-app/site-url.png)

1. Seleccione todas las listas y bibliotecas de SharePoint y seleccione **conectar**:

    ![Conexión a listas de SharePoint](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **Guarde** y **publique** la aplicación.

#### <a name="optional-enable-location-updates"></a>Opcional: habilitar actualizaciones de ubicación

Esta aplicación permite registrar la ubicación de un usuario y almacenarla en el sitio de SharePoint cada vez que un usuario establece su estado.  El equipo de administración de crisis puede ver estos datos en un informe de Power BI. 

> [!NOTE]
> La habilitación de actualizaciones de ubicación es opcional. Puede omitir esta sección si no desea realizar un seguimiento de la ubicación del usuario.

Para habilitar esta funcionalidad, siga estos pasos:

  1. Busque el control **btnDateRange**
  1. Abra la propiedad **alseleccionar** del control **btnDateRante** en la barra de fórmulas.
  1. Copie y pegue el siguiente fragmento de código en la barra de fórmulas de la propiedad **alseleccionar** :

  ```
    UpdateContext({locSaveDates: true});
    // Store the output properties of the calendar in static variables and collections.
    Set(varStartDate,First(Sort(Filter(selectedDates,ComponentId=CalendarComponent.Id),Date,Ascending)).Date);
    Set(varEndDate,First(Sort(Filter(selectedDates,ComponentId=CalendarComponent.Id),Date,Descending)).Date);
    // Create a new record for work status for each date selected in the date range.
    ForAll(
        Filter(
            RenameColumns(selectedDates,"Date","DisplayDate"),
            ComponentId=CalendarComponent.Id,
            !(DisplayDate in colDates.Date)
        ),
        Patch('CI_Employee Status',Defaults('CI_Employee Status'),
            {
                Title: varUser.userPrincipalName,
                Date: DisplayDate,
                Notes: "",
                PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value),
                Latitude: Text(Location.Latitude),
                Longitude: Text(Location.Longitude)
            }
        )
    );
    // Update existing dates with the new status.
    ForAll(
        AddColumns(
            Filter(
                RenameColumns(selectedDates,"Date","DisplayDate"),
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
                    varUser.mail,
                    Proper(WorkStatusComponent.Selected.Value) & ": " & varStartDate & " - " & varEndDate,
                    Switch(
                        WorkStatusComponent.Selected.Value,
                        "working from home",varString.WorkStatusMessageHome,
                        "out of office",varString.WorkStatusMessageOutOfOffice
                    ) & ": " &
                    // Create a bulleted list of dates
                    "<ul>" & 
                        Concat(Sort(Filter(selectedDates,ComponentId=CalendarComponent.Id),Date),"<li>" & Date & Char(10)) &
                    "</ul>"
                )
            }
        );
        If(
            locReceiptSuccess,
            Notify("You successfully submitted your work status. An email has been sent to you with a summary.",NotificationType.Success,5000),
            Notify("There was an error sending an email summary, but you successfully submitted your work status.",NotificationType.Success,5000);
        );
        
        Navigate('Share to Team Screen',LookUp(colStyles,Key="navigation_transition").Value),
        
        Notify(
            varString.WorkStatusError,
            NotificationType.Warning
        )
    );
    UpdateContext({locSaveDates: false})
```

### <a name="update-the-request-help-flow"></a>Actualizar el flujo de ayuda de la solicitud

Este flujo enviará una tarjeta adaptable a un equipo central de equipos que solicita ayuda.

![Importar paquete de aplicación](media/sample-crisis-communication-app/21-Request-Help.png)

Antes de completar el paso siguiente, cree primero un equipo de equipos para el equipo de administración de crisis. Una vez hecho esto, puede obtener el identificador del mismo y colocarlo en el flujo. Si necesita ayuda para crear un equipo de equipos, vaya a [creación de un equipo central de equipos de administración de crisis](#create-a-central-crisis-management-teams-team).

1. Navegue hasta el canal de equipos al que desea exponer todas las solicitudes de ayuda.
1. Seleccione el menú **...** para el canal.
1. Seleccione **obtener vínculo a canal**.

    ![Obtener vínculo al canal](media/sample-crisis-communication-app/17-Get-link-to-channel.png)

1. Copie el vínculo y péguelo en un editor de texto.

    ![Copiar vínculo](media/sample-crisis-communication-app/18-Copy-link.png)

1. Extraiga el identificador del equipo, que es todo después `groupId=` y antes de `&tenantId=`. <br> Por ejemplo, en la siguiente dirección URL, el ID. de canal sería `8bc7c0c2-0d4c-4fb8-af99-32da74c9237b`:
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`.
   
1. Extraiga el identificador del canal, que es todo después `https://teams.microsoft.com/l/channel/` y antes de `/General`. <br> Por ejemplo, en la siguiente dirección URL, el ID. de canal sería `19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2`:
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`.

1. Vaya a [Flow.Microsoft.com](https://flow.microsoft.com).

1. Seleccione **Mis flujos** en el panel de navegación izquierdo.

1. Seleccionar **más comandos** (...)  para **CrisisCommunication. request** y seleccione **Editar**.

    ![Editar la aplicación](media/sample-crisis-communication-app/20-Edit-Flow.png)

1. Abra la tarjeta ID. del **equipo** .

1. Pegue el identificador del equipo en el campo **valor** .

1. Abra la tarjeta ID. de **canal** .

1. Pegue el identificador de canal en el campo **valor** .

    ![Establecer identificadores de equipo](media/sample-crisis-communication-app/22-Set-Team-IDs.png)

1. Desplácese hacia abajo hasta las acciones **obtener tiempo** y actualice la acción de **convertir zona horaria** con la opción de horas de origen y destino:

    ![Convertir zona horaria](media/sample-crisis-communication-app/convert-time-zone.png)

## <a name="optional-configure-shared-inbox"></a>Opcional: configuración de la bandeja de entrada compartida

El flujo **CrisisCommunication. request** extrae las solicitudes desde la bandeja de entrada antes de enviarlas a los equipos. Si desea enviar correos electrónicos de solicitud a una bandeja de entrada compartida, siga estos pasos.

> [!NOTE]
> La configuración de la bandeja de entrada compartida es opcional. Puede omitir esta sección si no desea enviar correos electrónicos de solicitud a una bandeja de entrada compartida.

1. Abra el flujo **CrisisCommunication. request** en modo de *edición* .
1. Seleccione **...** desde el **cuando llega un correo electrónico V3**.
1. Seleccione **Eliminar**:

     ![Eliminar conector](media/sample-crisis-communication-app/33-delete-connector.png)

1. Busque y seleccione **Cuándo llega un nuevo correo electrónico a un buzón compartido (V2)** .
1. Escriba la dirección de bandeja de entrada compartida en **dirección de buzón**.
1. Abra la tarjeta de **comentarios** .
1. Seleccione el botón **Agregar un valor dinámico** para **valor**.
1. Busque y seleccione **Body**:

     ![Seleccionar cuerpo](media/sample-crisis-communication-app/35-body.png)

1. Abra la tarjeta **obtener tarjeta de Perfil de usuario (V2)** .
1. Seleccione el botón **Agregar un valor dinámico** .
1. Busque y seleccione **entre**:

     ![Seleccionar de](media/sample-crisis-communication-app/34-from.png)

## <a name="import-and-set-up-the-admin-app"></a>Importación y configuración de la aplicación de administración

Para administrar la aplicación que ha importado, querrá repetir los mismos pasos para la aplicación de administración.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
1. Seleccione **aplicaciones** en el panel de navegación izquierdo.
1. Seleccione **importar** en la barra de comandos.
1. Cargue el archivo **CrisisCommunicationAdmin. zip** del repositorio de github:

    ![Importar paquete de aplicación](media/sample-crisis-communication-app/import-app.png)

1. Seleccione **Importar**.

### <a name="update-the-sharepoint-connections"></a>Actualizar las conexiones de SharePoint

1. Vuelva a la lista de **aplicaciones** .
1. Seleccione **más comandos** (...) para aplicación de **aplicación de administración de comunicaciones de crisis** .
1. Seleccione **Editar** en el menú contextual:

    ![Editar la aplicación](media/sample-crisis-communication-app/08-Edit-Admin-App.png)

1. **Inicie sesión** o cree las conexiones necesarias y seleccione **permitir**.

1. Navegue a los orígenes de datos en el panel izquierdo:

    ![Orígenes de datos](media/sample-crisis-communication-app/data-sources.png)

1. **Quite** las listas de SharePoint existentes dentro de la aplicación, ya que no apuntan al sitio de SharePoint actual:

    ![Quitar orígenes de datos](media/sample-crisis-communication-app/remove-data-source.png)

1. Agregue las listas desde su propio sitio de SharePoint. Para empezar, busque SharePoint en la barra de búsqueda:

    ![Buscar en SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. Seleccione **SharePoint** y elija una conexión:

    ![Conexión de SharePoint](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Copie y pegue la dirección URL en el sitio de SharePoint en el campo de texto y seleccione **conectar**:

    ![Dirección URL del sitio de SharePoint](media/sample-crisis-communication-app/site-url.png)

1. Seleccione todas las listas y bibliotecas de SharePoint y seleccione **conectar**:

    ![Conexión a listas de SharePoint](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **Guarde** y **publique** la aplicación de administración.

## <a name="create-initial-content-for-the-app"></a>Crear contenido inicial para la aplicación

Ha importado correctamente la aplicación de comunicación de crisis y su aplicación de administración.

Ahora puede empezar a crear el contenido inicial. Para empezar, abra la aplicación de administración de comunicaciones de crisis.

![Aplicación de administración](media/sample-crisis-communication-app/09-Admin-App.png)

La aplicación de administración permite personalizar toda la información dentro de la aplicación de comunicación de crisis y configurar también los valores de clave para los flujos que lo acompañan.

> [!NOTE]
> Como recordatorio, si no desea usar la aplicación de administración, también puede editar estas mismas propiedades mediante la edición manual de las listas de SharePoint.

### <a name="setup-key-parameters-under-admin-settings"></a>Configuración de parámetros de clave en la configuración de administración

Para inicializar la aplicación, debe proporcionar todos los campos obligatorios. para ello, vaya a **configuración de administración**.

Complete todos los campos y seleccione **Guardar**.

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** | **Ejemplo** |
|-|-|-|-|
| Correo electrónico de administrador | AdminContactEmail | Aquí es donde se envían las solicitudes de correo electrónico. Deben establecerse en su dirección de correo electrónico. Si desea enviar notificaciones a otra bandeja de entrada, siga la [configuración de bandeja de entrada compartida opcional](#optional-configure-shared-inbox). | admin@contoso.com |
| URL del logotipo | Logotipo | El logotipo de la aplicación que aparecerá en la esquina superior izquierda. | https://contoso.com/logo.png |
| IDENTIFICADOR de grupo de AAD | AADGroupID | Se usa para enviar notificaciones a los usuarios finales acerca de las actualizaciones internas de la empresa mediante el flujo *de noticias notificar a los usuarios sobre nuevas novedades en la comunicación de crisis* . Siga las instrucciones siguientes para obtener el ID. de AAD de su grupo. | c0ddf873-b4fe-4602-b3a9-502dd944c8d5 |
| URL DE APLICACIÓN | AppURL | La ubicación de la aplicación de usuario final para que el flujo de *noticias notificar a los usuarios sobre nuevas comunicaciones de crisis* puede redirigir a los usuarios después de seleccionar **leer más**. | https://apps.preview.powerapps.com/play/<app URL>? tenantId =<tenant ID>
| Fuente RSS de gobierno | GovernmentRSSFeed | Se usa para rellenar la característica de noticias mundiales dentro de la aplicación. Resulta útil si desea proporcionar información adicional a sus empleados desde una fuente de confianza. | https://www.who.int/rss-feeds/news-english.xml |
| Método de notificación | PreferredSentNotification | Lo usa el flujo *de noticias notificar a los usuarios sobre nuevas comunicaciones de crisis* para determinar qué canal de distribución debe usar al enviar notificaciones. Este campo es obligatorio. | Correo electrónico, notificación de equipos, notificación de extracción |
| Marcas de características | Feature1... 203 | Se usa para deshabilitar o habilitar cada característica dentro de la aplicación. |  |

> [!NOTE]
> La notificación de equipos y las notificaciones de extracción no se admiten actualmente en GCC.


#### <a name="finding-the-aad-of-your-distribution-group"></a>Búsqueda del AAD del grupo de distribución
1. Vaya a [AAD.portal.Azure.com](https://aad.portal.azure.com)
1. Seleccione **Azure Active Directory** en el panel de navegación izquierdo.
1. Seleccione **grupos**.
1. Busque y seleccione el grupo de distribución.
1. Copie el campo ID. de **objeto** .

    ![Obtención del identificador de AAD en Azure](media/sample-crisis-communication-app/11-AAD-Group-ID.png)

1. Pegue el identificador en el campo ID. de **grupo de AAD** dentro de la aplicación de administración.

### <a name="setup-emergency-contacts"></a>Configuración de contactos de emergencia

1. Vaya a **contactos** de la empresa
1. Seleccione **crear nuevo contacto**
1. Rellene el formulario con los detalles de contacto.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Nombre completo | FullName | Nombre del contacto. |
| Correo electrónico | Correo electrónico | El correo electrónico que se mostrará para el contacto. |
| País | País | País del contacto. Se usará para agrupar los contactos, por lo que puede usar este campo para otras agrupaciones si los países no tienen sentido. |
| Comentarios | Comentarios | Muestra información adicional sobre el contacto; útil para describir cuándo ponerse en contacto con este contacto. |
| Obsoleto | Obsoleto | Permite ocultar un contacto de emergencia existente. |

### <a name="setup-initial-company-news"></a>Configuración de noticias iniciales de la empresa

1. Vaya a **noticias** de la compañía
1. Seleccione **crear nueva publicación**
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | Título de la actualización. |
| Detalles | Detalles | La actualización completa. Puede usar HTML en este campo. |
| Promociona | Promociona | Un mensaje breve acerca de la actualización. Se utilizará en el flujo de *noticias notificar a los usuarios sobre nuevas comunicaciones de crisis* y en la galería de actualizaciones. |
| Obsoleto | Obsoleto | Permite ocultar una publicación existente. |

### <a name="setup-helpful-tips"></a>Información de utilidad de configuración

1. Vaya a **sugerencias útiles**.
1. Seleccione **nueva sugerencia**.
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | Título de la sugerencia útil. |
| Dirección URL del recurso | ResourceURL | Vínculo a material de lectura adicional. opta |
| Subtítulo | Básicas | Subtítulo de la sugerencia. opta |
| Descripción | Descripción | Descripción completa de la sugerencia útil. |
| Obsoleto | Obsoleto | Permite ocultar una sugerencia útil. |

### <a name="setup-links"></a>Vínculos de configuración

1. Navegue a **vínculos**.
1. Seleccione **crear nuevo vínculo**.
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | Texto del vínculo. |
| URL | URL | Dirección URL del vínculo. |
| Descripción | Descripción | Detalles adicionales sobre el vínculo. opta |
| Obsoleto | Obsoleto | Permite ocultar un vínculo. |

### <a name="setup-faqs"></a>Preguntas más frecuentes sobre la instalación

1. Vaya a **preguntas más frecuentes**.
1. Seleccione **crear nuevas preguntas más frecuentes**.
1. Rellene el formulario.

*Esquema de lista:*

| **Nombre del campo** | **Nombre lógico en SharePoint** | **Propósito** |
|-|-|-|
| Título | Título | La pregunta de las preguntas más frecuentes. |
| Clasificación | Clasificación | El orden de las preguntas más frecuentes. |
| Respuesta | Respuesta | La respuesta a las preguntas más frecuentes |
| Obsoleto | Obsoleto | Permite ocultar preguntas más frecuentes. |

## <a name="test-and-share-the-app"></a>Prueba y uso compartido de la aplicación

Ahora que ha configurado correctamente todos los datos, ahora puede probar la aplicación para asegurarse de que funciona:

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
2. Seleccione **aplicaciones** en el panel de navegación izquierdo.
3. Seleccione **comunicación de crisis** para reproducir la aplicación.

Una vez que haya probado la aplicación correctamente, puede compartirla con todos los usuarios de su empresa.

## <a name="import-and-set-up-the-notification-flow"></a>Importar y configurar el flujo de notificación

La aplicación usa un flujo para enviar notificaciones a los usuarios finales cada vez que hay una nueva actualización de la compañía.

### <a name="import-the-news-notification-flow"></a>Importar el flujo de notificaciones de noticias

1. Vaya a [Flow.Microsoft.com](https://flow.microsoft.com)
1. Seleccione **Mis flujos** en el panel de navegación izquierdo.
1. Seleccione el botón **importar** en la barra de comandos.
1. Cargue el paquete **CrisisCommunicationNewsNotification. zip** del repositorio de github:

    > [!NOTE]
    > Si el inquilino está en el entorno GCC, use **CrisisCommunicationNewsNotificationGCC. zip**.

    ![Carga de CrisisCommunicationNewsNotification. zip](media/sample-crisis-communication-app/upload-news-notification.png)

1. Agregue conexiones para el nuevo flujo seleccionando el vínculo **seleccionar durante la importación** para cada conexión y rellenando el formulario:

    ![Seleccionar durante la importación](media/sample-crisis-communication-app/select-during-import.png)

1. Si necesita crear una nueva conexión, empiece seleccionando **crear nuevo** en el panel importar configuración.
1. Seleccione **nueva conexión** en la barra de comandos:

    ![Creación de una nueva conexión](media/sample-crisis-communication-app/create-connection.png)

1. Busque el nombre de la conexión; por ejemplo, **notificación de PowerApps (versión preliminar)** :

    ![Notificaciones](media/sample-crisis-communication-app/notifications.png)

1. Seleccione la conexión adecuada.
1. Si va a crear una conexión a las **notificaciones de PowerApps (versión preliminar),** verá el siguiente cuadro de diálogo:

    ![Cuadro de diálogo notificaciones](media/sample-crisis-communication-app/notifications-dialog.png)

1. Para obtener el identificador, vaya a la lista de **aplicaciones** .
1. Seleccione los **comandos más** (...) para la aplicación de **comunicación de crisis** y seleccione Detalles:

    ![More (comando)](media/sample-crisis-communication-app/06-App-Details.png)

1. Copie el **identificador**de la aplicación:

    ![IDENTIFICADOR de la aplicación](media/sample-crisis-communication-app/07-App-ID.png)

1. Pegue el **identificador** de la aplicación en el cuadro de diálogo de creación de la conexión y seleccione **crear**:

    ![Pegar ID. de aplicación](media/sample-crisis-communication-app/target-app-id.png)

1. Una vez que haya creado la nueva conexión, vuelva al panel **importar configuración** y seleccione el botón **Actualizar lista** .
1. La nueva conexión debería aparecer ahora y puede seleccionarla y seleccionar **Guardar**.
1. Seleccione **importar** cuando haya terminado de agregar todas las conexiones.

    ![Importación de conexiones](media/sample-crisis-communication-app/imported-connections.png)

### <a name="edit-the-news-notification-flow"></a>Editar el flujo de notificación de noticias

1. Una vez finalizada la importación, vuelva a **Mis flujos**.
1. Seleccione el flujo recién importado **para notificar a los usuarios sobre nuevas noticias sobre la comunicación de crisis**.

    > [!NOTE]
    > Si cargó el paquete GCC, el nombre de flujo es **notificar a los usuarios sobre las novedades de la comunicación de crisis GCC**.

1. Seleccione **Editar** en la barra de comandos.
1. Abra la tarjeta a la que **se llama cuando se publica un nuevo elemento**.
1. Cambie la **dirección del sitio** al nombre de su sitio de SharePoint.
1. Cambie el **nombre** de la lista a **CI_CompanyNews**.
1. Abra la tarjeta llamada **obtener los valores de configuración de administración**.
1. Cambie la **dirección del sitio** al nombre de su sitio de SharePoint.
1. Cambie el **nombre** de la lista a **CI_configAdminSetup**.
1. Abra la tarjeta llamada **Initialize variable (leer más texto)** .
1. Cambie el **valor** a "leer más" en el lenguaje nativo.

    ![Configuración de Flow](media/sample-crisis-communication-app/flow-options.png)

1. Seleccione **Guardar** para confirmar los cambios.

> [!NOTE]
> Es posible que reciba un error si aún no se ha autorizado una de las conexiones.
Si esto ocurre, abra la tarjeta con la conexión no autorizada y vuelva a autorizarla.

### <a name="test-the-news-notification-flow"></a>Probar el flujo de notificación de noticias

Para probar el flujo de notificaciones de noticias, vuelva a la aplicación de administración y cree una nueva actualización interna de la empresa.
Más adelante, todos los usuarios de la lista de distribución recibirán una actualización por su preferencia de notificación preferida.

> [!NOTE]
> Si se producen errores, asegúrese de que ha escrito correctamente en el identificador del grupo de distribución en la configuración de administración dentro de la aplicación de administración.

## <a name="monitor-office-absences-with-power-bi"></a>Supervisar las ausencias de Office con Power BI

Una vez que haya implementado la aplicación y los usuarios empiecen a notificar que están fuera de la oficina por diversos motivos (por ejemplo, por enfermedad o trabajando desde casa), ahora puede usar un informe de Power BI para realizar un seguimiento de la cantidad y el lugar donde se encuentran esas personas. Tenga en cuenta que debe [Habilitar el seguimiento de ubicación](#optional-enable-location-updates) para que el control de mapa funcione.

Para empezar, puede utilizar el informe de ejemplo ' informe de estado de presencia. pbix ' disponible en el [paquete de recursos](#prerequisites)descargados.
Si es necesario, descargue [Power BI Desktop](https://powerbi.microsoft.com/downloads). También se necesitará parte de la información de la lista de SharePoint de **Estado de CI_Employee** creada antes, así que vamos a obtenerla primero. Abra la lista en el sitio y seleccione Configuración de la lista en el icono de configuración:

![Configuración de la lista de estado de empleado](media/sample-crisis-communication-app/001-SharePointList-ListSettings-nolines.PNG)

Anote el **nombre del sitio** y el identificador de la **lista** en la barra de direcciones del explorador:

![Lista de Estados de empleados e ID. de sitio](media/sample-crisis-communication-app/002-SharePointList-AddressAndId-nolines.PNG)

En este momento, estamos preparados para abrir el informe Power BI; Inicie Power BI y abra el archivo **. pbix de informe de estado de presencia** . Mueva el mouse sobre el lado derecho del origen de datos de **Estado de CI_Employee** hasta que vea los puntos suspensivos, selecciónelo y seleccione la opción "editar consulta":

![Editar consulta](media/sample-crisis-communication-app/003-PowerBI-EditQuery-nolines.PNG)

Una vez abierto el editor de Power Query, haga clic con el botón secundario en el origen de datos de **Estado de CI_Employee** y seleccione el **editor avanzado**:

![Power Query Editor avanzado](media/sample-crisis-communication-app/004-PowerQuery-AdvancedEditor-nolines.PNG)

Aquí es donde usaremos el nombre del sitio y el ID. de lista de la lista de SharePoint: Copie el nuevo sitio de SharePoint en la tabla y el identificador de la lista en los tres lugares donde tenemos un GUID como resaltado y seleccione **listo**.

![Power Query actualizaciones de Editor avanzado](media/sample-crisis-communication-app/005-PowerQuery-AdvancedEditorUpdates-nolines.PNG)

Si ve algún error de conexión después de actualizar la información de conexión, es posible que tenga que actualizar las credenciales usadas para conectarse a la lista de SharePoint. Siga estos pasos para actualizar la conexión:

1. Seleccione el menú **archivo** , **Opciones y configuración** y, a continuación, seleccione **configuración de origen de datos**:

    ![Configuración de origen de datos](media/sample-crisis-communication-app/PBI-1-DataSourceSettings.PNG)

1. Seleccione **Editar permisos**:

    ![Editar permisos](media/sample-crisis-communication-app/PBI-2-DataSourceSettings-EditPermissions.PNG)

1. Asegúrese de que el tipo de *credenciales* está establecido en *cuenta de organización*y use las credenciales para tener acceso a la lista de SharePoint.

    ![Editar permisos](media/sample-crisis-communication-app/PBI-3-OrganizationalAccount.PNG)

Seleccione **cerrar & aplicar** para actualizar el informe y extraer los datos de la lista de SharePoint.

![Power Query cerrar y aplicar](media/sample-crisis-communication-app/006-PowerQuery-CloseAndApply-nolines.PNG)

Ahora tenemos un informe de Power BI que muestra la información geográfica de las ausencias de Office para el día actual y una tendencia de esas ausencias en muchos días. Ahora podemos publicar el informe para que otras personas de la organización puedan verlo.

![Power BI publicar informe](media/sample-crisis-communication-app/007-PowerBI-Publish-nolines.PNG)

El informe ya está publicado. Puede compartirlo con otros usuarios de su organización. También puede [programar la frecuencia de actualización del informe](https://docs.microsoft.com/power-bi/refresh-scheduled-refresh).

## <a name="integrate-your-app-into-teams"></a>Integre su aplicación en Teams

Ahora que tiene una aplicación en funcionamiento que se ha compartido con todos los usuarios, puede implementar la aplicación mediante equipos y crear un equipo de administración de crisis en Microsoft Teams para responder a los problemas.

### <a name="deploy-the-app-to-the-app-bar"></a>Implementación de la aplicación en la barra de la aplicación

Si es un administrador de equipos, puede enviar la aplicación a todos los usuarios dentro de la barra de aplicaciones de Teams.

![Aplicación en Teams](media/sample-crisis-communication-app/19-App-in-Teams.png)

1. Inicie sesión en [Power Apps](https://make.powerapps.com).
1. Seleccione **aplicaciones** en el panel de navegación izquierdo.
1. Seleccione el menú **...** para la aplicación de **comunicación de crisis** .
1. Seleccione **Agregar a equipos**.

    ![Agregar a equipos](media/sample-crisis-communication-app/24-Add-to-Teams.png)

1. Seleccione **Descargar aplicación**.

    ![Descargar aplicación](media/sample-crisis-communication-app/25-Download-App.png)

1. Abrir **equipos**
1. Vaya a **aplicaciones** en la barra de la aplicación izquierda.
1. Seleccione **cargar una aplicación personalizada**.
1. Si es un administrador de equipos, verá la capacidad de cargar una aplicación para todo el inquilino. Seleccione **cargar para contoso**.

    ![Cargar](media/sample-crisis-communication-app/26-Upload-for-Contoso.png)

1. Cargue el archivo que descargó de Power apps.
1. Navegue hasta el [centro de administración de equipos](https://admin.teams.microsoft.com/dashboard)
1. Seleccione **directivas de configuración** en **aplicaciones de equipo** en el panel de navegación izquierdo.

    ![Directivas de configuración de aplicaciones](media/sample-crisis-communication-app/27-Setup-Policies.png)

1. Seleccione **global (configuración de toda la organización)** .
1. Seleccione **agregar aplicaciones**.

    ![Agregar aplicación](media/sample-crisis-communication-app/28-Add-App.png)

1. Busque y seleccione la aplicación de **información de crisis** que ha cargado.

    ![Agregar aplicación anclada](media/sample-crisis-communication-app/29-Add-Pinned-App.png)

1. Seleccione **Agregar**.
1. Seleccione **Guardar**.

> [!NOTE]
> Los usuarios pueden tardar hasta 24 horas en ver la aplicación anclada automáticamente en la barra de la aplicación.

### <a name="create-a-central-crisis-management-teams-team"></a>Crear un equipo central de equipos de administración de crisis

Para coordinar la respuesta de crisis, querrá crear un equipo central de equipos para el equipo de administración de crisis y rellenarlo con toda la información relevante.

1. Vaya a equipos.
1. Seleccione **equipos** en la barra de la aplicación izquierda.
1. Seleccione **unirse o crear un equipo**.
1. Seleccione **crear equipo** y complete los pasos restantes.

    ![Crear equipo](media/sample-crisis-communication-app/23-Create-Team.png)

Una vez que haya creado correctamente el equipo, puede anclar la información relevante como pestañas. Por ejemplo, puede que desee anclar la aplicación de administración de crisis en el equipo o el Power BI informe. Para agregar la aplicación de administración como una pestaña:

1. Seleccione el botón **+** .
1. Busque y seleccione **Power apps**.
1. Busque y seleccione **Administración de información de crisis**.

    ![Anclar aplicación](media/sample-crisis-communication-app/32-Pin-Teams-app.png)

1. Seleccione **Guardar**.

Para agregar el informe Power BI:

1. Seleccione el botón **+** .
1. Busque y seleccione **Power BI**.
1. Busque y seleccione el informe de Power BI.
1. Seleccione **Guardar**.

## <a name="faq"></a>Preguntas más frecuentes

1. **¿Qué licencias necesito para ejecutar esta solución?**

    - La solución de esta aplicación usa conectores de Office. Por lo tanto, una licencia de Power apps inicializada de Office es suficiente para ejecutar y reproducir las aplicaciones de usuario y de administración. Obtenga más [información en Introducción a licencias de Power Platform](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus). 
    - Si desea usar el informe de Power BI (empaquetado como parte de la solución), deberá tener una licencia de Power BI. Obtenga más información en [Power BI precios](https://powerbi.microsoft.com/pricing/).

1. **¿Dónde debo ir si tengo comentarios sobre la solución?**

    Nos encantaría conocer la experiencia de implementación y personalización de la solución. Para compartir su experiencia, vaya a [aka.ms/crisis-Communication-feedback](https://aka.ms/crisis-communication-feedback).

1. **Parece que he encontrado un error con la aplicación; ¿Dónde debo ir?**

   Para archivar un error con la solución, vaya a [aka.ms/crisis-Communication-issues](https://aka.ms/crisis-communication-issues).

1. **¿Qué características no se admiten actualmente en GCC?**

    El conector Power Automate de robot para equipos y el conector de notificaciones de extracción no están disponibles actualmente para GCC. Use la opción correo electrónico para alertar a los usuarios acerca de las actualizaciones de noticias internas de GCC.

## <a name="issues--feedback"></a>Problemas & comentarios

- Para obtener **comentarios** sobre la *plantilla de ejemplo de comunicación de crisis*, vaya a [aka.ms/crisis-Communication-feedback](https://aka.ms/crisis-communication-feedback).
- Para **notificar un problema** con la *aplicación de comunicación de crisis*, vaya a [aka.ms/crisis-Communication-issues](https://aka.ms/crisis-communication-issues).

***Declinación de responsabilidades:*** *esta aplicación es un ejemplo y se puede usar con Microsoft Power apps y los equipos para la diseminación de información de referencia únicamente. Esta aplicación no está prevista ni está disponible para su uso como dispositivo médico, soporte clínico, herramienta de diagnóstico u otra tecnología pensada para usarse en el diagnóstico, la cura, la mitigación, el tratamiento o la prevención de la enfermedad o en otras condiciones, y Microsoft no concede ninguna licencia o derecho para usar esta aplicación con este fin.  Esta aplicación no está diseñada ni pretende ser un sustituto de asesoramiento médico profesional, diagnóstico, tratamiento o valoración y no debe usarse como tal.  El cliente asume el único riesgo y responsabilidad de cualquier uso de esta aplicación.  Microsoft no garantiza que la aplicación o los materiales proporcionados en la conexión serán suficientes para fines médicos o para cumplir los requisitos sanitarios de cualquier persona.* 

## <a name="next-steps"></a>Pasos siguientes

- [Referencia sobre fórmulas](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [Referencia sobre controles](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties)
