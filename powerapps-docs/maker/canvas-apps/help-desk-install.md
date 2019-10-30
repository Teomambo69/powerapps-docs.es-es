---
title: Instalar y configurar el ejemplo de servicio de asistencia en aplicaciones de lienzo | Microsoft Docs
description: Instrucciones paso a paso para instalar y configurar en PowerApps el ejemplo de servicio de asistencia en aplicaciones de lienzo.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6c9195bb9256c3d977300e61efe3f2cc88cfbf67
ms.sourcegitcommit: 0e7bdaea83adaa15da4d5c9ddbcd0b2bcbee01df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73063398"
---
# <a name="install-and-configure-the-help-desk-sample-in-powerapps"></a>Instalar y configurar el ejemplo de servicio de asistencia de PowerApps

Instrucciones paso a paso para instalar y configurar en PowerApps el ejemplo de servicio de asistencia en aplicaciones de lienzo.

Tiempo estimado para completar estos pasos: **10-15 minutos**

> [!TIP]
> En este [vídeo](https://youtu.be/z4cdtD6hB_4) puede ver una demostración de este proceso.

## <a name="overview-of-the-sample"></a>Información general sobre el ejemplo

El Departamento de soporte técnico proporciona una experiencia fácil de utilizar para conectar a los usuarios finales con profesionales de soporte técnico. Encuentre rápidamente respuestas a sus preguntas más importantes, realice un seguimiento del progreso de los vales abiertos y revise los detalles de las solicitudes anteriores. Esta aplicación requiere un mínimo de configuración para personalizarla.

![Pantalla inicial de la aplicación Help Desk de PowerApps](./media/help-desk-install/Login-screen.png)

> [!TIP]
> Vea este [vídeo](https://youtu.be/sl5fXwwnvzI) para aprender a usar el ejemplo de Help Desk de PowerApps.

## <a name="prerequisites"></a>Requisitos previos

- [Inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps.
- Debe tener una licencia de SharePoint Online válida y permiso para crear listas.

## <a name="create-the-helpdesk-sharepoint-list"></a>Crear la lista de SharePoint de Help Desk

Esta lista almacena los vales del servicio Help Desk.

1. Abra un explorador web y vaya a https://admin.microsoft.com.
2. Inicie sesión con una cuenta que tenga permiso para crear listas de SharePoint.
3. Desplácese a la colección de sitios en la que quiera alojar la lista de Help Desk.
4. Haga clic en el **icono de engranaje** situado en la parte superior derecha de la página web.
5. Haga clic en **Agregar una aplicación**.
6. En el cuadro de texto **Buscar una aplicación**, escriba **Personalizado**.
7. Haga clic en el **icono de búsqueda**.
8. Haga clic en la aplicación **Lista personalizada**.
9. En el cuadro de texto **Nombre**, escriba **HelpDesk**.

    > [!IMPORTANT]
    > Si elige otro nombre para la lista, asegúrese de anotarlo ya que tendrá que sustituirlo en todos los casos por HelpDesk durante el proceso de instalación y configuración.

10. Haga clic en **Crear**.

### <a name="create-description-column"></a>Crear una columna de descripción

1. Seleccione los puntos suspensivos junto a la lista de HelpDesk y haga clic en **Configuración**.
2. Haga clic en **Crear columna**.
3. En el cuadro de texto **Nombre de columna**, escriba **Descripción**.
4. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Varias líneas de texto**.
5. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
6. En la lista de botones de radio **Especificar el tipo de texto que se permite**, seleccione **Texto sin formato**.
7. Haga clic en **Aceptar**.

### <a name="create-category-column"></a>Crear una columna de categoría

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Categoría**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Elección**.
4. En el cuadro de texto **Escriba cada opción en una línea distinta**, especifique los valores siguientes, cada uno en una línea diferente: 
    - Problema con equipo portátil/PC
    - Problema con software de equipo portátil/PC
5. En la lista de botones de radio **Aplicar valores únicos**, seleccione **No**.
6. En la lista de botones de radio **Mostrar opciones con**, seleccione **Menú desplegable**.
7. En el cuadro de texto **Valor predeterminado**, escriba **Problema con equipo portátil/PC**.
8. Haga clic en **Aceptar**.

### <a name="create-percentcomplete-column"></a>Crear una columna PercentComplete

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **PercentComplete**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Número (1, 10, 100)** .
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **No**.
5. Haga clic en **Aceptar**.

### <a name="create-priority-column"></a>Crear una columna de prioridad

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Prioridad**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Elección**.
4. En el cuadro de texto **Escriba cada opción en una línea distinta**, especifique los valores siguientes, cada uno en una línea diferente: 
    - ALTA
    - MEDIO
    - BAJA
5. En la lista de botones de radio **Aplicar valores únicos**, seleccione **No**.
6. En la lista de botones de radio **Mostrar opciones con**, seleccione **Menú desplegable**.
7. En el cuadro de texto **Valor predeterminado**, escriba **BAJA**.
8. Haga clic en **Aceptar**.

### <a name="create-taskstatus-column"></a>Crear una columna de estado de la tarea

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Estado de la tarea**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Elección**.
4. En el cuadro de texto **Escriba cada opción en una línea distinta**, especifique los valores siguientes, cada uno en una línea diferente: 
    - SIN INICIAR
    - EN CURSO
    - COMPLETADA
    - APLAZADA
    - ESPERANDO CSR
5. En la lista de botones de radio **Aplicar valores únicos**, seleccione **No**.
6. En la lista de botones de radio **Mostrar opciones con**, seleccione **Menú desplegable**.
7. En el cuadro de texto **Valor predeterminado**, escriba **SIN INICIAR**.
8. Haga clic en **Aceptar**.

### <a name="create-assignedto-column"></a>Crear una columna Asignado a

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Asignado a**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Persona o grupo**.
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **No**.
5. En la lista de botones de radio **Permitir varios valores**, seleccione **NO**.
6. Haga clic en **Aceptar**.

### <a name="edit-title-column"></a>Editar la columna "Título"

1. Haga clic en el vínculo de la columna **Título**.
2. En la lista de botones de radio **Esta columna debe contener información**, seleccione **No**.
3. Haga clic en **Aceptar**.

## <a name="download-the-app"></a>Descarga de la aplicación

1.  [Descargue](http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip) el paquete PowerApps y guárdelo en su equipo.

## <a name="create-connections"></a>Crear conexiones

1.  En un explorador web, vaya a [web.powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2.  Inicie sesión con las mismas credenciales que utilizó para suscribirse.
3.  En el menú de la izquierda, seleccione **Datos** y luego **Conexiones**.
    
### <a name="create-office-365-outlook-connection"></a>Crear una conexión de Outlook de Office 365

1.  Haga clic en **+ Nueva conexión**.
2.  En el cuadro de búsqueda **Buscar**, escriba **Office 365 Outlook**.
3.  Seleccione **Office 365 Outlook** en la lista.
4.  Haga clic en **Crear**.
5.  En la ventana emergente, seleccione la cuenta con la que inició sesión.

### <a name="create-sharepoint-connection"></a>Crear una conexión de SharePoint

1.  Haga clic en **+ Nueva conexión**.
2.  En el cuadro de texto **Buscar**, escriba **SharePoint**.
3.  Seleccione **SharePoint** en la lista.
4.  Haga clic en **Crear**.
5.  En la ventana emergente, seleccione la cuenta con la que inició sesión.

### <a name="create-office-365-users-connection"></a>Crear una conexión a Usuarios de Office 365

1.  Haga clic en **+ Nueva conexión**.
2.  En el cuadro de búsqueda **Buscar**, escriba **Usuarios de Office 365**.
3.  Seleccione **Usuarios de Office 365** en la lista.
4.  Haga clic en **Crear**.
5.  En la ventana emergente, seleccione la cuenta con la que inició sesión.

## <a name="import-the-app"></a>Importación de la aplicación

1. En un explorador web, vaya a https://web.powerapps.com.
2. Inicie sesión con las mismas credenciales que utilizó para suscribirse.
3. En el menú de la izquierda, seleccione **Aplicaciones**. 
4. Haga clic en **Importar paquete (versión preliminar)** .
    
   ![Pantalla Importar paquete](./media/help-desk-install/import-package.png)

5. Haga clic en el botón **Cargar** y seleccione el paquete de PowerApps que descargó en pasos anteriores.
6. Para los tipos de recurso **Aplicación** y **Flujo**, establezca **IMPORTAR CONFIGURACIÓN** en **Crear como nueva**.
7. Para las conexiones **SharePoint** y **Outlook**, establezca **IMPORTAR CONFIGURACIÓN** en **Seleccionar durante la importación**.
    
   ![Pantalla Importar configuración](./media/help-desk-install/import-settings.png)

8. Haga clic en el **icono rojo** correspondiente a la **conexión de SharePoint**.
9. En la lista de conexiones, haga clic en el elemento que tenga su nombre de usuario.

   ![Pantalla Importar configuración](./media/help-desk-install/import-settings-sharepoint.png)

10. Haga clic en **Guardar**.
11. Haga clic en el **icono rojo** correspondiente a la **conexión de Office 365 Outlook**.
12. En la lista de conexiones, haga clic en el elemento que tenga su nombre de usuario.

    ![Pantalla Importar configuración](./media/help-desk-install/import-settings-office365outlook.png)

13. Haga clic en **Guardar**.

    > [!TIP] 
    > Cuando haya terminado, tendrá un aspecto similar al siguiente.

    ![Pantalla Importar configuración](./media/help-desk-install/import-settings-done.png)

14. Haga clic en **Importar** y espere hasta que finalice el proceso.

    ![Pantalla Importar configuración](./media/help-desk-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-list"></a>Configuración de la aplicación para usar la lista de SharePoint

1. En Pasos siguientes, haga clic en **Abrir aplicación**.
2. Haga clic en **Permitir** cuando se le solicite permiso.

### <a name="delete-connections"></a>Eliminar conexiones

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
1. En el panel **datos** , seleccione los puntos suspensivos (...) junto a **Departamento de soporte técnico**y, a continuación, seleccione **quitar**.

### <a name="helpdesk-list"></a>Lista de Help Desk

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
1. En el panel **Datos**, seleccione **Agregar origen de datos** > **Nueva conexión** > **SharePoint** > **Crear**.
1. En la lista **Sitios recientes**, seleccione el sitio de SharePoint en el que creó la lista de HelpDesk.

    > [!TIP] 
    > Si el sitio no aparece en la lista, escriba o pegue la dirección URL al sitio de SharePoint en el cuadro de texto y seleccione **Ir**.

1. En el cuadro de **búsqueda** de la parte superior de la lista, escriba o pegue el **Departamento de soporte técnico**.
1. Active la casilla junto a **Departamento de soporte técnico**y, a continuación, seleccione **conectar**.

### <a name="update-admin-list"></a>Actualizar la lista de administradores

1. Seleccione **LoginScreen**.
2. Seleccione **OnStart** en la lista desplegable.
3. Expanda la ventana de fórmulas y busque la colección **AdminList**.
4. Reemplace <strong>user@microsoft.com</strong> por los administradores de Help Desk.

    ![Actualizar la lista de administradores](./media/help-desk-install/Change-admin.png)
    
   > [!TIP]
   > Si tiene más de un administrador, use una coma para delimitar la lista de administradores. Ejemplo: "admin1@microsoft.com","admin2@microsoft.com".
   > Para asegurarse de que las direcciones de AdminList coinciden con el formato que PowerApps espera, seleccione Ver > Variables > Global > MyProfile y consulte la columna "Mail" para ver el formato de correo electrónico esperado.

1. Seleccione **Archivo** > **Guardar** > **Publicar** > **Publicar esta versión**.

## <a name="modify-the-flow"></a>Modificación del flujo

1.  En el menú de la izquierda, seleccione **Flujos**.
2.  Si es necesario, inicie sesión con las mismas credenciales que utilizó para suscribirse.
3.  Seleccione **Mis flujos** en el menú superior.
4.  Junto al flujo **HelpDeskFlow** , haga clic en el icono de lápiz. 
 
    ![Pantalla Editar flujo](./media/help-desk-install/edit-flow.png)

5.  Expanda la acción **Obtener elementos**. 
6.  Modifique los campos **Dirección del sitio** y **Nombre de lista** para que coincidan con la lista de SharePoint de Help Desk que ha creado.
    
    ![Pantalla Editar flujo](./media/help-desk-install/edit-flow-getitems.png)

    > [!TIP] 
    > No es necesario que se escriban manualmente, se pueden elegir en las listas desplegables.

7.  Expanda **Cambiar**.
8.  Expanda la caja **SIN INICIAR**.
9.  Expanda la acción **Caso no iniciado**.
10. Cambie el campo **Para** de modo que coincida con la dirección de correo electrónico del administrador de Help Desk.

    ![Pantalla Editar flujo](./media/help-desk-install/edit-flow-condition-send-email.png) 

11. Haga clic en **Actualizar flujo**.

## <a name="play-the-app"></a>Reproducir la aplicación

1. En el explorador web, haga clic en **Aplicaciones**.
2. Haga clic en los puntos suspensivos (...) junto a la aplicación del Departamento de soporte técnico.
3. Haga clic en **Abrir**. 

> [!TIP]
> Vea este [vídeo](https://youtu.be/sl5fXwwnvzI) para aprender a usar el ejemplo de Help Desk de PowerApps.

## <a name="next-steps"></a>Pasos siguientes
- [Personalizar un formulario de lista de SharePoint](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [Agregar y configurar un control](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [Editar y administrar permisos para una lista de SharePoint o una biblioteca](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
