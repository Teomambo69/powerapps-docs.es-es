---
title: Introducción a la conexión de SharePoint | Microsoft Docs
description: Vea las funciones, respuestas y ejemplos disponibles para SharePoint.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0c0f4744e7b323e3262a63278e7c12348142a99b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727719"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>Conectarse a SharePoint desde una aplicación de lienzo

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

Conéctese a un sitio de SharePoint para generar una aplicación automáticamente a partir de una lista personalizada o cree una conexión antes de agregar datos a una aplicación existente o de crear una aplicación desde cero.

Dependiendo de dónde residan los datos, puede realizar uno de estos métodos o ambos:

- Mostrar datos de una lista personalizada en un sitio de SharePoint Online o en un sitio local.
- Mostrar imágenes y reproducir archivos de vídeo o audio en una biblioteca (solo SharePoint Online).

## <a name="generate-an-app"></a>Generar una aplicación

Si desea administrar los datos en una lista personalizada, Power apps puede [generar una aplicación de tres pantallas automáticamente](../app-from-sharepoint.md). Los usuarios pueden examinar la lista en la primera pantalla, mostrar los detalles de un elemento en la segunda pantalla y crear o actualizar elementos en la tercera pantalla.

> [!NOTE]
> Si la lista de SharePoint contiene una columna de **elección**, **búsqueda**, o **persona o grupo** , vea [Mostrar datos en una galería](connection-sharepoint-online.md#show-list-columns-in-a-gallery) más adelante en este tema.

## <a name="create-a-connection"></a>Crear una conexión

1. [Inicie sesión en Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **datos** > **conexiones** en la barra de navegación izquierda y, a continuación, seleccione **nueva conexión** cerca de la esquina superior izquierda.

    > [!div class="mx-imgBorder"]
    > ![seleccione datos > conexiones en la barra de navegación izquierda y, a continuación, seleccione nueva conexión cerca de la esquina superior izquierda.](./media/connection-sharepoint-online/new-connection.png)

1. En el cuadro de búsqueda situado cerca de la esquina superior derecha, escriba o pegue **SharePoint**y, a continuación, seleccione **SharePoint**.

    > [!div class="mx-imgBorder"]
    > ![en el cuadro de búsqueda situado cerca de la esquina superior derecha, escriba o pegue SharePoint y, a continuación, seleccione SharePoint.](./media/connection-sharepoint-online/select-sharepoint.png)

1. Realice cualquiera de estos conjuntos de pasos:

    - Para conectarse a SharePoint Online, seleccione **conectar directamente (Cloud Services)** , seleccione **crear**y, a continuación, proporcione las credenciales (si se le solicita).

        > [!div class="mx-imgBorder"]
        > ![para conectarse a SharePoint Online, seleccione conectar directamente (Cloud Services)](./media/connection-sharepoint-online/select-online.png)

        Se crea la conexión y puede agregar datos a una aplicación existente o crear una aplicación desde cero.

    - Para conectarse a un sitio local, seleccione **conectar con la puerta de enlace de datos local**.

        > [!div class="mx-imgBorder"]
        > ![para conectarse a un sitio local, seleccione * * conectar con puerta de enlace de datos local](./media/connection-sharepoint-online/select-onprem.png)

        Especifique **Windows** como tipo de autenticación y, después, especifique sus credenciales. (Si las credenciales incluyen un nombre de dominio, especifíquelo como *dominio\alias*).

        > [!div class="mx-imgBorder"]
        > ![especificar las credenciales](./media/connection-sharepoint-online/specify-creds.png)

        En **elegir una puerta de enlace**, seleccione la puerta de enlace que desea usar y, después, seleccione **crear**.

        > [!NOTE]
        > Si no tiene una puerta de enlace de datos local instalada, [Instale una](../gateway-reference.md)y, después, seleccione el icono para actualizar la lista de puertas de enlace.

        > [!div class="mx-imgBorder"]
        > ![elegir puerta de enlace](./media/connection-sharepoint-online/choose-gateway.png)

        Se crea la conexión y puede agregar datos a una aplicación existente o crear una aplicación desde cero.

## <a name="add-data-to-an-existing-app"></a>Agregar datos a una aplicación existente

1. En Power apps Studio, abra la aplicación que quiere actualizar, seleccione la pestaña **vista** y, a continuación, seleccione **orígenes de datos**.

    > [!div class="mx-imgBorder"]
    > ![en la pestaña vista y, a continuación, seleccione orígenes de datos](./media/connection-sharepoint-online/view-data-sources.png)

1. En el panel **datos** , seleccione **Agregar origen de datos** > **SharePoint**.

1. En **conectar a un sitio de SharePoint**, seleccione una entrada en la lista **sitios recientes** (o escriba o pegue la dirección URL del sitio que desea usar) y, a continuación, seleccione **conectar**.

    > [!div class="mx-imgBorder"]
    > ![seleccionar](./media/connection-sharepoint-online/select-sp-site.png) de sitio

1. En **elegir una lista**, active la casilla de los **documentos** o una o más listas que desee usar y, a continuación, seleccione **conectar**:

    > [!div class="mx-imgBorder"]
    > ![en elegir una lista, active la casilla de los documentos o una o más listas que desee usar y, después, seleccione conectar](./media/connection-sharepoint-online/select-sp-tables.png)

    No todos los tipos de listas aparecen de forma predeterminada. Power apps admite listas personalizadas, no listas basadas en plantillas. Si el nombre de la lista que desea usar no aparece, desplácese hasta la parte inferior y, a continuación, escriba el nombre de la lista en el cuadro que contiene el nombre de la **tabla personalizada**.

    > [!div class="mx-imgBorder"]
    > ![escriba el nombre de la lista en el cuadro que contiene escriba un nombre de lista personalizado.](./media/connection-sharepoint-online/custom-list.png)

    El origen o los orígenes de datos se agregan a la aplicación.

## <a name="build-your-own-app-from-scratch"></a>Cree su propia aplicación desde cero

Aplique los conceptos de [creación de una aplicación desde cero](../get-started-create-from-blank.md) a SharePoint en lugar de Excel.

## <a name="show-list-columns-in-a-gallery"></a>Mostrar columnas de lista en una galería

Si la lista personalizada contiene cualquiera de estos tipos de columnas, muestre los datos en un control **Galería** mediante la barra de fórmulas para establecer la propiedad **texto** de uno o varios controles **etiqueta** de la Galería:

- Para una columna de **elección** o de **búsqueda** , especifique **ThisItem.** _ColumnName_ **. Valor** para mostrar los datos de esa columna.

    Por ejemplo, especifique **ThisItem.Location.Value** si tiene una columna **Opción** denominada **Ubicación** y especifique **ThisItem.PostalCode.Value** si tiene una columna **Búsqueda** denominada **CódigoPostal**.

- Para una columna de **persona o grupo** , especifique **ThisItem.** _ColumnName_ **. DisplayName** para mostrar el nombre para mostrar del usuario o el grupo.

    Por ejemplo, especifique **ThisItem.Manager.DisplayName** para mostrar los nombres de una columna **Persona o grupo** denominada **Administrador**.

    También puede mostrar información distinta acerca de los usuarios, como direcciones de correo electrónico o puestos de trabajo. Para mostrar una lista completa de opciones, especifique **ThisItem.** _ColumnName_ **.** (incluido el punto final).

    > [!NOTE]
    > En el caso de una columna **CreatedBy** , especifique **ThisItem. Author. DisplayName** para mostrar los nombres para mostrar de los usuarios que han creado elementos en la lista. Para una columna **ModifiedBy**, especifique **ThisItem.Editor.DisplayName** para mostrar los nombres de los usuarios que han modificado elementos en la lista.

- Para una columna de **metadatos administrados** , especifique **ThisItem.** _ColumnName_ **. Etiqueta** para mostrar los datos de esa columna.

    Por ejemplo, especifique **ThisItem.Languages.Label** si tiene una columna **Metadatos administrados** denominada **Idiomas**.

## <a name="show-data-from-a-library"></a>Mostrar datos de una biblioteca

Si tiene varias imágenes en una biblioteca de SharePoint, puede Agregar un control de **lista desplegable** a la aplicación para que los usuarios puedan especificar la imagen que se va a mostrar. También puede aplicar los mismos principios a otros controles, como los controles de la **Galería** y otros tipos de datos, como los vídeos.

1. Si aún no lo ha hecho, [cree una conexión](#create-a-connection)y, a continuación, [agregue los datos a una aplicación existente](#add-data-to-an-existing-app).

1. Agregue un control **lista** desplegable y asígnele el nombre **ImageList**.

1. Establezca la propiedad **Items** de **ImageList** en **Documents**.

1. En la pestaña **propiedades** del panel derecho, abra la lista de **valores** y, a continuación, seleccione **nombre**.

    Los nombres de archivo de las imágenes de la biblioteca aparecen en **ImageList**.

    > [!div class="mx-imgBorder"]
    > ![lista de imágenes](./media/connection-sharepoint-online/dropdown-items.png)

1. Agregue un control **imagen** y establezca su propiedad **imagen** en esta expresión:

    `ImageList.Selected.'Link to item'`

1. Presione F5 y, a continuación, seleccione un valor diferente en **ImageList**.

    Aparece la imagen que ha especificado.

    > [!div class="mx-imgBorder"]
    > ![imagen de ejemplo](./media/connection-sharepoint-online/golden-honey.png)

Puede [descargar una aplicación de ejemplo](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp) que muestra un enfoque más complejo para mostrar los datos de una biblioteca de SharePoint.

1. Después de descargar la aplicación, Abra [Power apps Studio](https://us.create.powerapps.com/studio/#), seleccione **abrir** en la barra de navegación izquierda y, a continuación, seleccione **examinar**.
1. En el cuadro de diálogo **abrir** , busque y abra el archivo que ha descargado y, a continuación, agregue una biblioteca de SharePoint como origen de datos siguiendo los dos primeros procedimientos de este tema.

> [!NOTE]
> De forma predeterminada, esta aplicación muestra las [advertencias de delegación](../delegation-overview.md), pero puede omitirlas si la biblioteca contiene menos de 500 elementos.

En esta aplicación de una pantalla, la lista de la esquina inferior izquierda muestra todos los archivos de la biblioteca.

- Puede buscar un archivo escribiendo o pegando uno o más caracteres en el cuadro de búsqueda cerca de la parte superior.
- Si la biblioteca contiene carpetas, puede filtrar la lista de archivos; para ello, seleccione un icono de filtro en la lista de carpetas situada justo debajo de la barra de título.

Cuando encuentre el archivo que desea, selecciónelo para mostrarlo en el control de **vídeo**, **imagen**o **audio** a lo largo del lado derecho.

> [!div class="mx-imgBorder"]
> ![imagen de ejemplo](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>Problemas conocidos

### <a name="lists"></a>Coge

Power apps puede leer nombres de columna que contienen espacios, pero los espacios se reemplazan por el código de escape hexadecimal **"\_x0020\_"** . Por ejemplo, **"nombre de columna"** en SharePoint aparecerá como **"Column_x0020_Name"** en Power apps cuando se muestre en el diseño de datos o se use en una fórmula.

No se admiten todos los tipos de columnas y no todos los tipos de columnas admiten todos los tipos de tarjetas.

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

### <a name="libraries"></a>Libre

- No se pueden cargar archivos de Power Apps en una biblioteca.
- No se pueden mostrar archivos PDF de una biblioteca en un control de PDF Viewer.
- Power apps Mobile no es compatible con la función de **descarga** .
- Si los usuarios van a ejecutar la aplicación en Power apps Mobile o en la aplicación de Windows 10, use la función **Launch** para mostrar el contenido de la biblioteca en una galería.

## <a name="next-steps"></a>Pasos siguientes

- Más información sobre cómo [mostrar datos a partir de un origen de datos](../add-gallery.md).
- Más información sobre cómo [ver detalles y crear o actualizar registros](../add-form.md).
- Consulte otros tipos de [orígenes de datos](../connections-list.md) a los que se puede conectar.
