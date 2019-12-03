---
title: Instalar y configurar el ejemplo de informe de gastos en aplicaciones de lienzo | Microsoft Docs
description: Instrucciones paso a paso para, en Power Apps, instalar y configurar el ejemplo de informe de gastos para aplicaciones de canvas.
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
ms.openlocfilehash: 43d2632612a473f226a9c8c964ecb42837074cc6
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731475"
---
# <a name="install-and-configure-the-expense-report-sample-for-canvas-apps-in-power-apps"></a>Instalación y configuración del ejemplo de informe de gastos para aplicaciones de lienzo en Power apps

Instrucciones paso a paso para instalar y configurar el ejemplo de informe de gastos. También puede obtener una vista previa de la aplicación de ejemplo [aquí](https://aka.ms/previewmyexpenses).

Tiempo estimado para completar estos pasos: **10-15 minutos**

> [!TIP]
> Vea [este vídeo](https://youtu.be/kJXZPILfbwU) para una demostración sobre cómo usar la aplicación de ejemplo de informe de gastos. 

Realice un seguimiento de los informes de gastos desde el envío hasta la aprobación. Los elementos de línea de recuento como gastos individuales se acumulan y envían para su aprobación cuando están listos. Esta aplicación requiere un mínimo de configuración para personalizarla.

![Pantalla inicial del informe de gastos de PowerApps](./media/expense-report-install/expense-report-powerapp.png)

> [!TIP]
> Vea [este](https://youtu.be/kJXZPILfbwU) vídeo para aprender a usar el ejemplo de informe de gastos.

## <a name="prerequisites"></a>Requisitos previos

- [Regístrese](../signup-for-powerapps.md) en Power apps.

## <a name="create-the-expenses-list"></a>Creación de la lista Gastos

En esta lista se almacenan los informes de gastos.

1. Abra un explorador web y vaya a https://admin.microsoft.com.
2. Inicie sesión con una cuenta que tenga permiso para crear listas.
3. Desplácese a la colección de sitios donde quiera alojar la lista de gastos.
4. Haga clic en el icono de engranaje situado en la parte superior derecha de la página web.
5. Haga clic en **Agregar una aplicación**.
6. En el cuadro de texto **Buscar una aplicación**, escriba **Personalizado**.
7. Haga clic en el **icono de búsqueda**.
8. Haga clic en la aplicación **Lista personalizada**.
9. En el cuadro de texto **Nombre**, escriba **Gastos**.

    > [!IMPORTANT]
    > Si elige otro nombre para la lista, anótelo, ya que tendrá que sustituirlo en todos los casos por Gastos durante el proceso de instalación y configuración.

10. Haga clic en **Crear**.

### <a name="create-cost-center-column"></a>Crear una columna Cost Center

1. Haga clic en la lista **Gastos**.
2. Haga clic en el icono de engranaje situado en la parte superior derecha de la página web.
3. Haga clic en **Configuración de la lista**.
4. Haga clic en **Crear columna**.
5. En el cuadro de texto **Nombre de columna**, escriba **Cost Center**.
6. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Elección**.
7. En el cuadro de texto **Escriba cada opción en una línea distinta**, especifique los valores siguientes, cada uno en una línea diferente: 
    - Microsoft
    - Contoso
8. En el cuadro de texto **Valor predeterminado**, escriba **Microsoft**.
9. Haga clic en **Aceptar**.

### <a name="create-comments-column"></a>Crear una columna de comentarios

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Comentarios**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Varias líneas de texto**.
4. Haga clic en **Aceptar**.

### <a name="create-status-column"></a>Crear una columna de estado

1. Haga clic en la lista **Gastos**.
2. Haga clic en el **icono de engranaje** situado en la parte superior derecha de la página web.
3. Haga clic en **Configuración de la lista**.
4. Haga clic en **Crear columna**.
5. En el cuadro de texto **Nombre de columna**, escriba **Estado**.
6. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Elección**.
7. En el cuadro de texto **Escriba cada opción en una línea distinta**, especifique los valores siguientes, cada uno en una línea diferente: 
    - Ábra
    - Pendiente
    - Approved
8. En el cuadro de texto **Valor predeterminado**, escriba **Abierto**.
9. Haga clic en **Aceptar**.

### <a name="create-approvername-column"></a>Crear una columna ApproverName

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **ApproverName**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Persona o grupo**.
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. Haga clic en **Aceptar**.

### <a name="create-datesubmitted-column"></a>Crear una columna DateSubmitted

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **DateSubmitted**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Fecha y hora**.
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. Haga clic en **Aceptar**.

### <a name="create-startdate-column"></a>Crear una columna StartDate

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **StartDate**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Fecha y hora**.
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. Haga clic en **Aceptar**.

### <a name="create-enddate-column"></a>Crear una columna EndDate

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **EndDate**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Fecha y hora**.
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. Haga clic en **Aceptar**.

## <a name="create-the-lineitems-list"></a>Creación de la lista LineItems

En esta lista se almacenan los elementos de línea asociados a cada informe de gastos.

1. Desplácese a la misma colección de sitios en la que ha creado la lista Gastos.
2. Haga clic en el icono de engranaje situado en la parte superior derecha de la página web.
3. Haga clic en **Agregar una aplicación**.
4. En el cuadro de texto **Buscar una aplicación**, escriba **Personalizado**.
5. Haga clic en el **icono de búsqueda**.
6. Haga clic en la aplicación **Lista personalizada**.
7. En el cuadro de texto **Nombre**, escriba **LineItems**.

    > [!IMPORTANT] 
    > Si elige otro nombre para la lista, anótelo, ya que tendrá que sustituirlo en todos los casos por LineItems durante el proceso de instalación y configuración.

8. Haga clic en **Crear**.
 
### <a name="create-category-column"></a>Crear una columna de categoría

1. Haga clic en la lista **LineItems**.
2. Haga clic en el icono de engranaje situado en la parte superior derecha de la página web.
3. Haga clic en **Configuración de la lista**.
4. Haga clic en **Crear columna**.
5. En el cuadro de texto **Nombre de columna**, escriba **Categoría**.
6. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Elección**.
7. En el cuadro de texto **Escriba cada opción en una línea distinta**, especifique los valores siguientes, cada uno en una línea diferente: 
    - Comida y bebida
    - Transporte
    - Necesidades del negocio
8. En el cuadro de texto **Valor predeterminado**, escriba **Comida y bebida**.
9. Haga clic en **Aceptar**.

### <a name="create-cost-column"></a>Crear una columna de costo

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Costo**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Número (1, 10, 100)** .
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. Haga clic en **Aceptar**.

### <a name="create-date-column"></a>Crear una columna de fecha

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Fecha**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Fecha y hora**.
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. Haga clic en **Aceptar**.

### <a name="create-description-column"></a>Crear una columna de descripción

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **Descripción**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Varias líneas de texto**.
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. En la lista de botones de radio **Especificar el tipo de texto que se permite**, seleccione **Texto sin formato**.
6. Haga clic en **Aceptar**.

### <a name="create-reportid-column"></a>Crear una columna ReportID

1. Haga clic en **Crear columna**.
2. En el cuadro de texto **Nombre de columna**, escriba **ReportID**.
3. En la lista de botones de radio **El tipo de información de esta columna es**, seleccione **Búsqueda (información ya disponible en este sitio)** .
4. En la lista de botones de radio **Esta columna debe contener información**, seleccione **Sí**.
5. En la lista desplegable **Obtener información de**, seleccione la lista **Gastos** que ha creado.
6. En la lista desplegable **En esta columna**, seleccione **Id**.
7. Haga clic en **Aceptar**.

### <a name="edit-title-column"></a>Editar columna de título

1. Haga clic en el vínculo de la columna **Título**.
2. En la lista de botones de radio **Esta columna debe contener información**, seleccione **No**.
3. Haga clic en **Aceptar**.

## <a name="download-the-expense-report-app"></a>Descargar la aplicación Informe de gastos

1. En un explorador web, desplácese hasta el siguiente vínculo:

    [https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip](https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip).

2. Descargue el paquete de ejemplo de Power apps de informe de gastos y guárdelo en el equipo.

## <a name="create-connections"></a>Crear conexiones

1.  En un explorador Web, vaya a [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2.  Inicie sesión con las mismas credenciales que utilizó para suscribirse.
3.  En el menú de la izquierda, seleccione **Conexiones**.

### <a name="create-an-approvals-connection"></a>Creación de una conexión de aprobaciones

1.  Haga clic en **+ Nueva conexión**.
2.  En el cuadro de búsqueda **Buscar**, escriba **Aprobaciones**.
3.  Seleccione **Aprobaciones** en la lista.
4.  Haga clic en **Crear**.
    
### <a name="create-an-office-365-outlook-connection"></a>Creación de una conexión de Office 365 Outlook

1.  Haga clic en **+ Nueva conexión**.
2.  En el cuadro de búsqueda **Buscar**, escriba **Office 365 Outlook**.
3.  Seleccione **Office 365 Outlook** en la lista.
4.  Haga clic en **Crear**.
5.  En la ventana emergente, seleccione la cuenta con la que inició sesión.

### <a name="create-a-sharepoint-connection"></a>Creación una conexión de SharePoint

1.  Haga clic en **+ Nueva conexión**.
2.  En el cuadro de texto **Buscar**, escriba **SharePoint**.
3.  Seleccione **SharePoint** en la lista.
4.  Haga clic en **Crear**.
5.  En la ventana emergente, seleccione la cuenta con la que inició sesión.

## <a name="import-the-app"></a>Importación de la aplicación

1. En un explorador web, vaya a https://make.powerapps.com.
1. Inicie sesión con las mismas credenciales que utilizó para suscribirse.
1. En la barra de navegación izquierda, seleccione **Aplicaciones** e **Importar paquete (versión preliminar)** .

    ![Pantalla Importar paquete](./media/expense-report-install/import-package.png)

1. Seleccione **Cargar** y, después, el paquete que ha descargado anteriormente.
1. Para los tipos de recurso **Aplicación** y **Flujo**, establezca **IMPORTAR CONFIGURACIÓN** en **Crear como nueva**.
1. Para las conexiones **SharePoint** y **Outlook**, establezca **IMPORTAR CONFIGURACIÓN** en **Seleccionar durante la importación**.

    ![Pantalla Importar configuración](./media/expense-report-install/import-settings.png)

1. Seleccione el icono rojo correspondiente a la **conexión de SharePoint**.
1. En la lista de conexiones, seleccione el elemento que tenga su nombre de usuario.

    ![Pantalla Importar configuración](./media/expense-report-install/import-settings-sharepoint.png)

1. Seleccione **Guardar**.
1. Seleccione el icono rojo correspondiente a la **conexión de aprobación**.
1. En la lista de conexiones, seleccione el elemento que tenga su nombre de usuario.

    ![Pantalla Importar configuración](./media/expense-report-install/import-settings-approvals.png)

1. Seleccione **Guardar**.
1. Seleccione el icono rojo correspondiente a la **conexión de Office 365 Outlook**.
1. En la lista de conexiones, seleccione el elemento que tenga su nombre de usuario.

    ![Pantalla Importar configuración](./media/expense-report-install/import-settings-office365outlook.png)

1. Seleccione **Guardar**.

    > [!TIP] 
    > Cuando haya terminado, tendrá un aspecto similar al siguiente:

    ![Pantalla Importar configuración](./media/expense-report-install/import-settings-done.png)

1. Seleccione **Importar** y espere hasta que finalice el proceso.

    ![Pantalla Importar configuración](./media/expense-report-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-lists"></a>Configurar la aplicación para usar las listas de SharePoint

1. En el explorador web, seleccione **Aplicaciones**.
2. Seleccione el botón de puntos suspensivos (...) situado junto a la aplicación de informe de gastos.
3. Seleccione **Editar en la Web** > **Permitir**.

### <a name="delete-connections"></a>Eliminar conexiones
1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
1. En el panel **Datos**, seleccione los puntos suspensivos (...) al lado de  **Gastos** y seleccione **Quitar**.
1. Repita el paso anterior para quitar el origen de datos **LineItems**.

### <a name="expenses-list"></a>Lista de gastos

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
1. En el panel **Datos**, seleccione **Agregar origen de datos** > **Nueva conexión** > **SharePoint** > **Crear**.
1. En la lista **Sitios recientes**, seleccione el sitio de SharePoint en el que creó la lista Gastos.

    > [!TIP] 
    > Si el sitio no aparece en la lista, escriba o pegue la dirección URL al sitio de SharePoint en el cuadro de texto y seleccione **Ir**.

1. En el cuadro **Búsqueda** de la parte superior de la lista, escriba o pegue **Gastos**.
1. Active la casilla de junto a **Gastos** y seleccione **Conectar**.

### <a name="lineitems-list"></a>Lista de LineItems

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
1. En el panel **Datos**, seleccione **SharePoint**.
1. En la lista **Sitios recientes**, seleccione el sitio de SharePoint en el que creó la lista LineItems.

    > [!TIP] 
    > Si el sitio no aparece en la lista, escriba o pegue la dirección URL al sitio de SharePoint en el cuadro de texto y seleccione **Ir**.

1. En el cuadro **Búsqueda** de la parte superior de la lista, escriba o pegue **LineItems**.
1. Active la casilla de junto a **LineItems** y seleccione **Conectar**.
1. Seleccione **Archivo** > **Guardar** > **Publicar** > **Publicar esta versión**.

## <a name="modify-the-flow"></a>Modificación del flujo

1. En la barra de navegación izquierda, seleccione **Flujos**.
1. Si es necesario, proporcione las mismas credenciales que usó para suscribirse.
1. Cerca de la parte superior de la pantalla, seleccione **Mis flujos**.
1. Junto al flujo **ApproveExpense**, seleccione el icono de lápiz.

    ![Pantalla Editar flujo](./media/expense-report-install/edit-flow.png)

1. Expanda la acción **Obtener elementos**. 
1. Modifique los campos **Dirección del sitio** y **Nombre de lista** para que coincidan con la lista Gastos que ha creado en SharePoint.

    ![Pantalla Editar flujo](./media/expense-report-install/edit-flow-getitems.png)

    > [!TIP] 
    > No es necesario que se escriban manualmente, se pueden seleccionar en las listas desplegables.

1. Expanda la **Condición**.
1. Expanda la sección **En caso positivo**.
1. Expanda la acción **Cambiar estado de elemento a Aprobado**.
1. Modifique los campos **Dirección del sitio** y **Nombre de lista** para que coincidan con la lista Gastos que ha creado en SharePoint.

    ![Pantalla Editar flujo](./media/expense-report-install/edit-flow-condition-ifyes.png) 

    > [!TIP] 
    > No es necesario que se escriban manualmente, se pueden seleccionar en las listas desplegables.

1. Expanda la sección **En caso negativo**.
1. Expanda la acción **Cambiar estado de elemento a Abierto**.
1. Modifique los campos **Dirección del sitio** y **Nombre de lista** para que coincidan con la lista Gastos que ha creado en SharePoint. 

    ![Pantalla Editar flujo](./media/expense-report-install/edit-flow-condition-ifno.png)

    > [!TIP] 
    > No es necesario que se escriban manualmente, se pueden seleccionar en las listas desplegables.

14. Seleccione **Actualizar flujo**.

## <a name="play-the-app"></a>Reproducir la aplicación

1. En el explorador web, seleccione **Aplicaciones**.
1. Seleccione los puntos suspensivos (...) situados junto a la aplicación de informe de gastos y seleccione **Abrir**.

## <a name="next-steps"></a>Pasos siguientes
- [Personalizar un formulario de lista de SharePoint](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [Agregar y configurar un control](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [Editar y administrar permisos para una lista de SharePoint o una biblioteca](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
