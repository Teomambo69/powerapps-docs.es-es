---
title: Introducción a la conexión de SharePoint | Microsoft Docs
description: Consulte las funciones, respuestas y ejemplos disponibles para SharePoint.
author: sarafankit
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 07/12/2017
ms.author: ankitsar
ms.openlocfilehash: 8a49e0e4e866e7e9eda4834904ee84c082140376
ms.sourcegitcommit: 7354a0c61578fcc0b9965bf557b9d7c553c73e96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34803314"
---
# <a name="connect-to-sharepoint-from-powerapps"></a>Conexión a SharePoint desde PowerApps
![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

Conéctese a un sitio de SharePoint para generar automáticamente una aplicación de una lista, crear una aplicación desde cero o actualizar una aplicación existente.

## <a name="known-issues"></a>Problemas conocidos
Puede agregar datos de una lista personalizada, pero no una biblioteca. Además, no se admiten todos los tipos de columnas y no todos los tipos de columnas admiten todos los tipos de tarjetas.

| Tipo de columna | Soporte técnico | Tarjetas predeterminadas |
| --- | --- | --- |
| Una línea de texto |Sí |Ver texto |
| Varias líneas de texto |Sí |Ver texto |
| Opción |Sí |Ver búsqueda<br>Editar consulta<br>Ver la selección múltiple<br>Editar selección múltiple |
| Número |Sí |Ver porcentaje<br>Ver clasificación<br>Ver texto |
| Divisa |Sí |Ver porcentaje<br>Ver clasificación<br>Ver texto |
| Fecha y hora |Sí |Ver texto |
| Búsqueda |Sí |Ver búsqueda<br>Editar consulta<br>Ver la selección múltiple<br>Editar selección múltiple |
| Booleano (Sí/No) |Sí |Ver texto<br>Alternar vista |
| Persona o grupo |Sí |Ver búsqueda<br>Editar consulta<br>Ver la selección múltiple<br>Editar selección múltiple |
| Hipervínculo |Sí |Ver URL<br>Ver texto |
| Imagen |Sí (solo lectura) |Ver imagen<br>Ver texto |
| Datos adjuntos |Sí (solo lectura) |Ver los datos adjuntos|
| Calculado |Sí (solo lectura) | |
| Resultado de la tarea |No | |
| Datos externos |No | |
| Metadatos administrados |Sí (solo lectura) | |
| Clasificación |No | |

PowerApps lee las columnas que contienen espacios, pero estos se sustituyen por el código de escape hexadecimal **"\_x0020\_"**. Por ejemplo, el **"Nombre de columna"** en SharePoint aparecerá como **"Nombre_x0020_de_columna"** en PowerApps cuando se muestre en el diseño de datos o se use en una fórmula.

## <a name="prerequisites"></a>Requisitos previos
1. [Inicie sesión](../../signup-for-powerapps.md) en PowerApps.

1. [Inicie sesión](http://web.powerapps.com) en PowerApps con las mismas credenciales que usó para suscribirse.

1. Junto al borde de la izquierda, seleccione **Aplicaciones** y, después, haga clic en **Crear una aplicación** en el titular.

## <a name="create-an-app"></a>Crear una aplicación
* [Genere una aplicación automáticamente](../app-from-sharepoint.md) basándose en los datos de una lista de SharePoint.

    La aplicación tendrá tres pantallas de forma predeterminada: una para examinar registros, otra para mostrar detalles acerca de un registro y otra para crear o actualizar un registro. Cuando se genera la aplicación, lo más probable es que quiera personalizar [la pantalla de exploración](../customize-layout-sharepoint.md) y [las pantallas de detalles y de edición](../customize-forms-sharepoint.md) para adaptarlas a sus necesidades.

    **Nota**: Si la lista de SharePoint contiene una columna **Opción**, **Buscar**, o **Persona o grupo**, consulte la sección [Mostrar datos en una galería](connection-sharepoint-online.md#show-data-in-a-gallery) de este mismo tema.

* Puede crear su propia aplicación desde cero: para ello [conéctese a SharePoint](../connect-to-sharepoint.md), revise los conceptos en [Crear una aplicación desde cero ](../get-started-create-from-blank.md) y aplíquelos en SharePoint en lugar de en Excel.

## <a name="add-a-sharepoint-list-to-an-existing-app"></a>Agregar una lista de SharePoint a una aplicación existente
1. En PowerApps Studio, abra la aplicación que desea actualizar.

2. En la pestaña **Vista** de la cinta de opciones, pulse o haga clic en **Orígenes de datos**

3. En el panel de la derecha, haga clic o pulse en **Agregar origen de datos**.

    ![Agregar origen de datos](./media/connection-sharepoint-online/add-data-source.png)

4. Pulse o haga clic en **Nueva conexión**, pulse o haga clic en **SharePoint** y, finalmente, pulse o haga clic en **Conectar**.

    ![Agregar una conexión de SharePoint](./media/connection-sharepoint-online/add-sharepoint.png)

5. Especifique el tipo de sitio de SharePoint al que desea conectarse:

    ![Especificar el tipo de conexión](./media/connection-sharepoint-online/choose-type.png)

   * Pulse o haga clic en **Conectar directamente (servicios en la nube)** para conectarse a SharePoint Online.

   * Pulse o haga clic en **Conectar mediante una puerta de enlace de datos local** para conectarse a un sitio de SharePoint local.

       Especifique **Windows** como tipo de autenticación y, después, especifique sus credenciales. (Si las credenciales incluyen un nombre de dominio, especifíquelo como *dominio\alias*).

       ![Especificar las credenciales](./media/connection-sharepoint-online/specify-creds.png)

       **Nota**: Si no tiene una puerta de enlace de datos local instalada, [instale una](../gateway-reference.md) y pulse o haga clic en el icono para actualizar la lista de puertas de enlace.

       En **Elegir una puerta de enlace**, pulse o haga clic en la puerta de enlace que desea usar.

       ![Elegir puerta de enlace](./media/connection-sharepoint-online/choose-gateway.png)

6. Pulse o haga clic en **Conectar**.

7. En **Conectar a un sitio de SharePoint**, pulse o haga clic en una entrada de la lista **Sitios recientes** (o escriba o pegue la dirección URL del sitio que quiere utilizar) y, a continuación, pulse o haga clic en **Ir**.

    ![Seleccionar un sitio de SharePoint](./media/connection-sharepoint-online/select-sp-site.png)

8. En **Elegir una lista**, active la casilla de las listas que desee usar y pulse o haga clic en **Conectar**:  

    ![Seleccionar tablas en SharePoint](./media/connection-sharepoint-online/select-sp-tables.png)

    No todos los tipos de listas aparecen de forma predeterminada. Si el nombre de la lista que desea usar no aparece, desplácese a la parte inferior y escriba el nombre de la lista en el cuadro que contiene el texto **Enter a custom list name** (Escriba el nombre de lista personalizado).

    ![Lista personalizada en SharePoint](./media/connection-sharepoint-online/custom-list.png)

    Los orígenes de datos se agregan a la aplicación.

    ![Lista de orígenes de datos agregados a la aplicación](./media/connection-sharepoint-online/data-sources-list.png)

## <a name="show-data-in-a-gallery"></a>Mostrar datos en una galería
Para mostrar datos de cualquiera de estos tipos de columnas en una galería, use la barra de fórmulas para establecer la propiedad **Texto** de uno o varios controles **Etiqueta** de dicha galería:

* Para una columna **Opción** o **Buscar**, especifique **ThisItem.[ColumnName].Value** para mostrar los datos de esa columna.

    Por ejemplo, especifique **ThisItem.Location.Value** si tiene una columna **Opción** denominada **Ubicación** y especifique **ThisItem.PostalCode.Value** si tiene una columna **Búsqueda** denominada **CódigoPostal**.

* Para una columna **Persona o grupo**, especifique **ThisItem.[ColumnName].DisplayName** para mostrar el nombre del usuario o del grupo.

    Por ejemplo, especifique **ThisItem.Manager.DisplayName** para mostrar los nombres de una columna **Persona o grupo** denominada **Administrador**.

    También puede mostrar información distinta acerca de los usuarios, como direcciones de correo electrónico o puestos de trabajo. Para mostrar una lista completa de opciones, especifique **ThisItem.[ColumnName].** (con el punto final).

    **Nota**: Para una columna **CreatedBy**, especifique **ThisItem.Autor.DisplayName** para mostrar los nombres de los usuarios que han creado elementos en la lista. Para una columna **ModifiedBy**, especifique **ThisItem.Editor.DisplayName** para mostrar los nombres de los usuarios que han modificado elementos en la lista.

* Para una columna **Metadatos administrados**, especifique **ThisItem.[ColumnName].Label** para mostrar los datos de esa columna.

    Por ejemplo, especifique **ThisItem.Languages.Label** si tiene una columna **Metadatos administrados** denominada **Idiomas**.

## <a name="next-steps"></a>Pasos siguientes
* Más información sobre cómo [mostrar datos a partir de un origen de datos](../add-gallery.md).
* Más información sobre cómo [ver detalles y crear o actualizar registros](../add-form.md).
* Consulte otros tipos de [orígenes de datos](../connections-list.md) a los que se puede conectar.
