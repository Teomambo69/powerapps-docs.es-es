---
title: "Configuración de listas para la integración de SharePoint Online con PowerApps, Microsoft Flow y Power BI | Microsoft Docs"
description: En esta tarea, se configuraran las listas de SharePoint para usarlas como origen de datos para aplicaciones, flujos, informes y paneles.
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/19/2017
ms.author: mblythe
ms.openlocfilehash: ad9033b51142d1bb6b014abe0cc049a0b5c27ee5
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="set-up-lists-for-sharepoint-online-integration-with-powerapps-microsoft-flow-and-power-bi"></a>Configuración de listas para la integración de SharePoint Online con PowerApps, Microsoft Flow y Power BI
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales acerca del uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

SharePoint tiene una gran cantidad de características para la colaboración y el uso compartido, pero nos centraremos en una característica de este escenario: las [listas de SharePoint](https://support.office.com/article/Introduction-to-lists-0A1C3ACE-DEF0-44AF-B225-CFA8D92C52D7). Una lista no es más que una colección de datos que se pueden compartir con los miembros del equipo y otros usuarios del sitio. Analizaremos las listas que se usan en este escenario y, después, podrá crearlas en su propio sitio de SharePoint Online.

## <a name="step-1-understand-the-lists"></a>Paso 1: Información de las listas
La primera lista es **Project Requests**, en la que un solicitante del proyecto agrega una solicitud. A continuación, el aprobador de proyecto examina la solicitud y la aprueba o rechaza.

| **Columna de lista** | **Tipo de datos** | **Notas** |
| --- | --- | --- |
| Título |Una línea de texto |Columna predeterminada, se utiliza para el nombre del proyecto |
| Descripción |Una línea de texto | |
| ProjectType |Una línea de texto |Valores: hardware nuevo, hardware actualizado, software nuevo, software actualizado |
| RequestDate |Fecha | |
| Requestor |Una línea de texto | |
| EstimatedDays |Número |Permite la comparación de la estimación del solicitante con la estimación del jefe de proyecto con la fecha real |
| Approved |Una línea de texto |Valores: pendiente, sí o no |

> [!NOTE]
> También utilizamos la columna **ID**, que genera SharePoint y que está oculta de forma predeterminada. Utilizamos tipos de datos básicos para simplificar, pero una aplicación real podría utilizar tipos más complejos, como **Persona o grupo** en la columna **Requestor**. Para obtener información sobre los tipos de datos que admite PowerApps, consulte [Conexión de Microsoft PowerApps a SharePoint](connections/connection-sharepoint-online.md#known-issues).

La segunda lista es **Project Details**, que realiza un seguimiento de los detalles de todos los proyectos aprobados, como el jefe de proyecto asignado.

| **Columna de lista** | **Tipo de datos** | **Notas** |
| --- | --- | --- |
| Título |Una línea de texto |Columna predeterminada, se utiliza para el nombre del proyecto |
| RequestID |Número |Coincide con el valor de la lista **Project Requests** de la columna **ID** |
| ApprovedDate |Fecha | |
| Estado |Una línea de texto |Valores: no iniciado, en curso, completado |
| ProjectedStartDate |Fecha |El momento en que el jefe de proyecto estima que se va a iniciar el proyecto |
| ProjectedEndDate |Fecha |El momento en que el jefe de proyecto estima que se va a finalizar el proyecto |
| ProjectedDays |Número |Días hábiles; normalmente se calcularían, pero no en este escenario |
| ActualDays |Número |Para los proyectos completados |
| PMAssigned |Una línea de texto |Jefe de proyecto |

## <a name="step-2-create-and-review-the-lists"></a>Paso 2: Creación y revisión de las listas
Para continuar con el escenario, debe crear las dos listas de SharePoint y rellenarlas con datos de ejemplo. Le mostraremos cómo hacerlo mediante la creación de la lista y el pegado en ella de datos de ejemplo. Asegúrese de que dispone de los archivos de Excel del [paquete de descarga](https://aka.ms/o4ia0f).

> [!NOTE]
> Use Internet Explorer para este paso.

### <a name="create-the-lists"></a>Creación de las listas

1. En Internet Explorer, en el sitio de SharePoint, haga clic o pulse en **New** (Nuevo) y , luego, en **List** (Lista).
   
    ![Crear una lista de SharePoint nueva](./media/sharepoint-scenario-setup/01-01-01-new-list.png)

2. Escriba el nombre "Project Requests" y haga clic o pulse **Create** (Crear).
   
    ![Especificar un nombre para la lista nueva](./media/sharepoint-scenario-setup/01-01-02-create-list.png)
   
    Se crea la lista **Project Requests** con el campo predeterminado **Title**.
   
    ![Lista de Project Requests](./media/sharepoint-scenario-setup/01-01-03-initial-list.png)

### <a name="add-columns-to-the-list"></a>Adición de columnas a la lista

1. Haga clic o pulse en el ![icono de elemento nuevo](./media/sharepoint-scenario-setup/icon-new.png) y , después, en **Single line of text** (Una línea de texto).
   
    ![Campo para agregar una línea de texto](./media/sharepoint-scenario-setup/01-01-04-add-column.png)

2. Escriba el nombre "Description" y haga clic o pulse en **Save** (Guardar).
   
3. Repita los pasos **1.** y **2.** para las demás columnas de la lista:
   
   1. **Single line of text** (Una línea de texto) > "ProjectType"
   2. **Date** (Fecha) > "RequestDate"
   3. **Single line of text** (Una línea de texto) > "Requestor"
   4. **Number** (Número) > "EstimatedDays"
   5. **Single line of text** (Una línea de texto) > "Approved"

### <a name="copy-data-into-the-list"></a>Copia de datos en la lista
1. Haga clic o pulse en **Quick edit** (Edición rápida).
   
    ![Edición rápida de la lista](./media/sharepoint-scenario-setup/01-01-06-quick-edit.png)
2. Seleccione las celdas de la cuadrícula.
   
    ![Lista con todas las columnas](./media/sharepoint-scenario-setup/01-01-07-empty-grid.png)
3. Abra el libro project-requests.xlsx y seleccione todos los datos (no los encabezados).
   
    ![Tabla de Excel Project Requests](./media/sharepoint-scenario-setup/01-01-08-excel-table.png)
4. Copie los datos y péguelos en la cuadrícula de SharePoint y haga clic en o pulse en **Done**  (Listo).
   
    ![Lista completada con datos](./media/sharepoint-scenario-setup/01-01-09-full-grid.png)
5. Repita el proceso de creación y copia de la lista "Project Details", para lo que usará el libro project-details.xlsx. Consulte la tabla Project Details en [Paso 1: Información de las listas](#step-1-understand-the-lists), ya que contiene los tipos de datos y los nombres de las columnas.

## <a name="step-3-update-connections-to-samples---optional"></a>Paso 3: Actualización de conexiones a ejemplos (opcional)
Como se mencionó en la introducción a esta serie de tutoriales, en el [paquete de descarga](https://aka.ms/o4ia0f) se han incluido dos aplicaciones de ejemplo y un informe. Este escenario se puede completar sin usar estos ejemplos, pero si desea usarlos, es preciso que actualice las conexiones a las listas de SharePoint. Actualícelas para que usen *sus* listas como origen de datos, en lugar de las nuestras.

### <a name="update-connections-for-the-sample-apps"></a>Actualizar las conexiones de las aplicaciones de ejemplo

1. En [PowerApps Studio](https://create.powerapps.com/studio/), haga clic en **Abrir** (o púlselo) en el panel izquierdo. 

2. Haga clic o pulse **Examinar** y abra el archivo **project-management-app.msapp** que descargó.

3. Haga clic o pulse **Permitir** para que PowerApps pueda usar SharePoint.

4. En la cinta de opciones, en la pestaña **Vista**, pulse o haga clic en **Orígenes de datos**.

    ![Orígenes de datos de PowerApps](./media/sharepoint-scenario-setup/01-03-01-data-sources.png)
5. En el panel **Datos**, haga clic o pulse el botón de puntos suspensivos (**...** ) que se encuentra al lado de **Detalles del proyecto** y haga clic o pulse en **Quitar**.
   
    ![Quitar origen de datos de Project Details](./media/sharepoint-scenario-setup/01-03-02-remove.png)
6. Pulse o haga clic en **Agregar origen de datos**.
   
    ![Agregar origen de datos](./media/sharepoint-scenario-setup/01-03-03-add.png)

7. Le mostraremos dos formas de conectarse a la lista, en función de si PowerApps ya ha establecido automáticamente una conexión de SharePoint, o no: 

    * Si ve una conexión de SharePoint, haga clic o pulse en ella.

        ![Conexión existente](./media/sharepoint-scenario-setup/01-03-03aa-existing-connection.png)

    * Si ve ninguna conexión de SharePoint, haga clic o pulse en **Nueva conexión**.

        ![Nueva conexión](./media/sharepoint-scenario-setup/01-03-03a-new-connection.png)

        A continuación, haga clic o pulse **SharePoint** y, después, **Crear**.
   
        ![Conexión de SharePoint](./media/sharepoint-scenario-setup/01-03-03b-sharepoint.png)

8. Escriba la dirección URL del sitio de SharePoint Online que contiene las listas que creó y pulse o haga clic en **Ir**.
   
    ![Dirección URL de SharePoint](./media/sharepoint-scenario-setup/01-03-03c-sharepoint-url.png)
9. Seleccione la lista **Project Details** y pulse o haga clic en **Conectar**.
   
    ![Lista Project Details](./media/sharepoint-scenario-setup/01-03-03d-project-details.png)
   
    El panel **Datos** muestra la conexión que creó.
   
    ![Orígenes de datos](./media/sharepoint-scenario-setup/01-03-03e-data-sources.png)

10. Haga clic o pulse el botón de puntos suspensivos (**...** ) que se encuentra al lado de **Detalles del proyecto** y haga clic o pulse en **Actualizar**.
    
    ![Actualizar origen de datos de Project Details](./media/sharepoint-scenario-setup/01-03-02-remove.png)

11. Haga clic en ![Icono Ejecutar aplicación](./media/sharepoint-scenario-setup/icon-run-arrow.png) en la esquina superior derecha para ejecutar la aplicación y asegúrese de que la conexión funciona correctamente.

12. Haga clic o pulse **Archivo** y guarde la aplicación en la nube. 

12. Repita los pasos de esta sección en **app.msapp de las solicitudes de proyecto**, mediante el uso de la lista **Project Requests**.

### <a name="update-connections-for-the-sample-report"></a>Actualizar las conexiones del informe de ejemplo
1. Abra **project-analysis.pbix** en Power BI Desktop.

2. En la cinta de opciones, en la pestaña **Inicio**, pulse o haga clic en **Editar consultas** y, luego, en **Configuración de origen de datos**.
   
    ![Editar consultas](./media/sharepoint-scenario-setup/01-03-04-edit-queries.png)

3. Pulse o haga clic en **Cambiar origen**.
   
    ![Configuración de origen de datos](./media/sharepoint-scenario-setup/01-03-05-settings.png)

4. Escriba la dirección URL del sitio de SharePoint Online, haga clic o pulse **Aceptar** y, finalmente, **Cerrar**.
   
    ![Dirección URL de lista de SharePoint](./media/sharepoint-scenario-setup/01-03-06-list-url.png)

5. Power BI Desktop muestra un banner debajo de la cinta de opciones, con el fin de que pueda aplicar los cambios y trasladar los datos del nuevo origen. Haga clic o pulse en **Aplicar cambios**.
   
    ![Aplicar cambios de consulta](./media/sharepoint-scenario-setup/01-03-07-apply.png)

6. Inicie sesión con una cuenta de Microsoft (la cuenta que utiliza para acceder a SharePoint Online) y haga clic o pulse en **Conectar**.
   
    ![Conectarse a SharePoint Online](./media/sharepoint-scenario-setup/01-03-08-connect.png)

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso de esta serie de tutoriales es [generar una aplicación para controlar las solicitudes de proyecto](sharepoint-scenario-generate-app.md).

