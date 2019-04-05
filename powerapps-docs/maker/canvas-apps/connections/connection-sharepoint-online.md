---
title: Introducción a la conexión de SharePoint | Microsoft Docs
description: Consulte las funciones disponibles, respuestas y ejemplos para SharePoint.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 65ce3b7736b55f3734d6da7d945965ed791a3ce4
ms.sourcegitcommit: 4fe0a71efd54c1f4d22a279aa74c6bde3d908b9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "59007898"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>Conectarse a SharePoint desde una aplicación de lienzo

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

Conectarse a un sitio de SharePoint para generar automáticamente una aplicación desde una lista personalizada, o cree una conexión antes de agregar datos a una aplicación existente o crear una aplicación desde cero.

Función de donde residen sus datos, puede tardar uno o ambos de estos enfoques:

- Mostrar datos de una lista personalizada en un sitio de SharePoint Online o un sitio local.
- Mostrar imágenes y reproducir archivos de audio o vídeos en una biblioteca (SharePoint Online solo).

## <a name="generate-an-app"></a>Generar una aplicación

Si desea administrar los datos en una lista personalizada, puede PowerApps [generar automáticamente una aplicación de tres pantallas de](../app-from-sharepoint.md). Los usuarios pueden examinar la lista en la primera pantalla, mostrar detalles de un elemento en la segunda pantalla y crear o actualizar los elementos de la tercera pantalla.

> [!NOTE]
> Si la lista de SharePoint contiene un **elección**, **búsqueda**, o **persona o grupo** columna, vea [mostrar datos en una galería](connection-sharepoint-online.md#show-list-columns-in-a-gallery) más adelante en este tema.

## <a name="create-a-connection"></a>Crear una conexión

1. [Inicie sesión en PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **datos** > **conexiones** en el panel de navegación izquierdo de la barra y, a continuación, seleccione **nueva conexión** cerca de la esquina superior izquierda.

    > [!div class="mx-imgBorder"]
    > ![Seleccione datos > conexiones en la barra de navegación izquierdo y, a continuación, seleccione nueva conexión cerca de la esquina superior izquierda.](./media/connection-sharepoint-online/new-connection.png)

1. En el cuadro de búsqueda cerca de la esquina superior derecha, escriba o pegue **SharePoint**y, a continuación, seleccione **SharePoint**.

    > [!div class="mx-imgBorder"]
    > ![En el cuadro de búsqueda cerca de la esquina superior derecha, escriba o pegue SharePoint y, a continuación, seleccione SharePoint.](./media/connection-sharepoint-online/select-sharepoint.png)

1. Realice uno de estos conjuntos de pasos:

    - Para conectarse a SharePoint Online, seleccione **conectar directamente (servicios en la nube)**, seleccione **crear**y, a continuación, proporcione las credenciales (si se le solicita).

        > [!div class="mx-imgBorder"]
        > ![Para conectarse a SharePoint Online, seleccione Conectar directamente (servicios en la nube)](./media/connection-sharepoint-online/select-online.png)

        Se crea la conexión, y puede agregar datos a una aplicación existente o crear una aplicación desde cero.

    - Para conectarse a un sitio local, seleccione **conectarse mediante puerta de enlace de datos local**.

        > [!div class="mx-imgBorder"]
        > ![Para conectarse al sitio local, seleccione ** Conectar mediante puerta de enlace de datos local)](./media/connection-sharepoint-online/select-onprem.png)

        Especifique **Windows** como tipo de autenticación y, después, especifique sus credenciales. (Si las credenciales incluyen un nombre de dominio, especifíquelo como *dominio\alias*).

        > [!div class="mx-imgBorder"]
        > ![Especificar las credenciales](./media/connection-sharepoint-online/specify-creds.png)

        En **elegir una puerta de enlace**, seleccione la puerta de enlace que desea usar y, a continuación, seleccione **crear**.

        > [!NOTE]
        > Si no tiene una puerta de enlace de datos local instalada, [instálela](../gateway-reference.md)y, a continuación, seleccione el icono para actualizar la lista de puertas de enlace.

        > [!div class="mx-imgBorder"]
        > ![Elegir puerta de enlace](./media/connection-sharepoint-online/choose-gateway.png)

        Se crea la conexión, y puede agregar datos a una aplicación existente o crear una aplicación desde cero.

## <a name="add-data-to-an-existing-app"></a>Agregar datos a una aplicación existente

1. En PowerApps Studio, abra la aplicación que desea actualizar, seleccione la **vista** pestaña y, a continuación, seleccione **orígenes de datos**.

    > [!div class="mx-imgBorder"]
    > ![En la pestaña de vista y, a continuación, seleccione los orígenes de datos](./media/connection-sharepoint-online/view-data-sources.png)

1. En el **datos** panel, seleccione **agregar origen de datos** > **SharePoint**.

1. En **conectar a un sitio de SharePoint**, seleccione una entrada en el **sitios recientes** lista (o escriba o pegue la dirección URL del sitio que desea usar) y, a continuación, seleccione **Connect**.

    > [!div class="mx-imgBorder"]
    > ![Seleccione el sitio](./media/connection-sharepoint-online/select-sp-site.png)

1. En **elegir una lista**, active la casilla de verificación **documentos** o una o varias listas que desea usar y, a continuación, seleccione **Connect**:

    > [!div class="mx-imgBorder"]
    > ![En elegir una lista, seleccione la casilla de verificación para los documentos o una o varias listas que desea usar y, a continuación, seleccione Conectar](./media/connection-sharepoint-online/select-sp-tables.png)

    No todos los tipos de listas aparecen de forma predeterminada. PowerApps admite listas personalizadas, no listas basadas en plantillas. Si el nombre de la lista que desea usar no aparece, desplácese hacia abajo y, a continuación, escriba el nombre de la lista en el cuadro que contiene **escriba el nombre de tabla personalizada**.

    > [!div class="mx-imgBorder"]
    > ![Escriba el nombre de la lista en el cuadro que contiene escriba un nombre de lista personalizada.](./media/connection-sharepoint-online/custom-list.png)

    El origen de datos o los orígenes se agregan a la aplicación.

## <a name="build-your-own-app-from-scratch"></a>Crear su propia aplicación desde cero

Aplicar los conceptos de [crear una aplicación desde cero](../get-started-create-from-blank.md) para SharePoint en lugar de Excel.

## <a name="show-list-columns-in-a-gallery"></a>Mostrar columnas de la lista en una galería

Si su lista personalizada contiene cualquiera de estos tipos de columnas, mostrar esos datos en un **galería** control mediante el uso de la barra de fórmulas para establecer el **texto** propiedad de uno o varios **etiqueta** controles de dicha galería:

- Para un **elección** o **búsqueda** columna, especificar **ThisItem.** _ColumnName_**. Valor** para mostrar los datos de esa columna.

    Por ejemplo, especifique **ThisItem.Location.Value** si tiene una columna **Opción** denominada **Ubicación** y especifique **ThisItem.PostalCode.Value** si tiene una columna **Búsqueda** denominada **CódigoPostal**.

- Para un **persona o grupo** columna, especificar **ThisItem.** _ColumnName_**. DisplayName** para mostrar el nombre del usuario o el grupo.

    Por ejemplo, especifique **ThisItem.Manager.DisplayName** para mostrar los nombres de una columna **Persona o grupo** denominada **Administrador**.

    También puede mostrar información distinta acerca de los usuarios, como direcciones de correo electrónico o puestos de trabajo. Para mostrar una lista completa de opciones, especifique **ThisItem.** _ColumnName_**.** (incluido el punto final).

    > [!NOTE]
    > Para un **CreatedBy** columna, especificar **Thisitem.autor.DisplayName** para mostrar los nombres de los usuarios que han creado elementos en la lista. Para una columna **ModifiedBy**, especifique **ThisItem.Editor.DisplayName** para mostrar los nombres de los usuarios que han modificado elementos en la lista.

- Para un **Managed Metadata** columna, especificar **ThisItem.** _ColumnName_**. Etiqueta** para mostrar los datos de esa columna.

    Por ejemplo, especifique **ThisItem.Languages.Label** si tiene una columna **Metadatos administrados** denominada **Idiomas**.

## <a name="show-data-from-a-library"></a>Mostrar datos desde una biblioteca

Si tiene varias imágenes en una biblioteca de SharePoint, puede agregar un **desplegable** para que los usuarios pueden especificar qué imagen para mostrar el control a la aplicación. También puede aplicar los mismos principios a otros controles, tales como **galería** controles y otros tipos de datos, como vídeos.

1. Si no lo ha hecho ya, [crear una conexión](#create-a-connection)y, a continuación, [agregar datos a una aplicación existente](#add-data-to-an-existing-app).

1. Agregar un **desplegable** controlar y asígnele el nombre **ImageList**.

1. Establecer el **elementos** propiedad de **ImageList** a **documentos**.

1. En el **propiedades** ficha del panel derecho, abrirlo el **valor** lista y, a continuación, seleccione **nombre**.

    Los nombres de archivo de las imágenes de la biblioteca aparecen en **ImageList**.

    > [!div class="mx-imgBorder"]
    > ![Lista de imágenes](./media/connection-sharepoint-online/dropdown-items.png)

1. Agregar un **imagen** y establezca su **imagen** propiedad en esta expresión:

    `ImageList.Selected.'Link to item'`

1. Presione F5 y, a continuación, seleccione un valor distinto en **ImageList**.

    Aparece la imagen que ha especificado.

    > [!div class="mx-imgBorder"]
    > ![Imagen de ejemplo](./media/connection-sharepoint-online/golden-honey.png)

También puede [descargar una aplicación de ejemplo](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp) que muestra un enfoque más complejo para mostrar datos desde una biblioteca de SharePoint.

1. Después de descargar la aplicación, abra [PowerApps Studio](https://us.create.powerapps.com/studio/#), seleccione **abrir** en el panel de navegación izquierdo de la barra y, a continuación, seleccione **examinar**.
1. En el **abrir** cuadro de diálogo, busque y abra el archivo que descargó y, a continuación, agregar una biblioteca de SharePoint como un origen de datos siguiendo los primeros dos procedimientos de este tema.

> [!NOTE]
> De forma predeterminada, esta aplicación muestra [advertencias de delegación](../delegation-overview.md), pero puede omitir si la biblioteca contiene menos de 500 elementos.

En esta aplicación de una sola pantalla, la lista en la esquina inferior izquierda muestra todos los archivos de la biblioteca.

- Puede buscar un archivo, escriba o pegue uno o más caracteres en el cuadro de búsqueda en la parte superior.
- Si la biblioteca contiene carpetas, puede filtrar la lista de archivos seleccionando un icono de filtro en la lista de carpetas solo en la barra de título.

Cuando encuentre el archivo que desea, seleccione para mostrarla en el **vídeo**, **imagen**, o **Audio** control a lo largo del lado derecho.

> [!div class="mx-imgBorder"]
> ![Imagen de ejemplo](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>Problemas conocidos

### <a name="lists"></a>Listas

PowerApps puede leer los nombres de columna que contienen espacios, pero los espacios se sustituyen con el código de escape hexadecimal **"\_x0020\_"**. Por ejemplo, el **"Nombre de columna"** en SharePoint aparecerá como **"Nombre_x0020_de_columna"** en PowerApps cuando se muestre en el diseño de datos o se use en una fórmula.

No todos los tipos de columnas se admiten y no todos los tipos de columnas admiten todos los tipos de tarjetas.

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

### <a name="libraries"></a>Bibliotecas

- No se puede cargar archivos desde PowerApps a una biblioteca.
- No se puede mostrar archivos PDF desde una biblioteca en un control de Visor de PDF.
- PowerApps Mobile no es compatible con la **descargar** función.
- Si los usuarios ejecutarán la aplicación en PowerApps Mobile o la aplicación de Windows 10, use el **iniciar** función para mostrar el contenido de la biblioteca en una galería.

## <a name="next-steps"></a>Pasos siguientes

- Más información sobre cómo [mostrar datos a partir de un origen de datos](../add-gallery.md).
- Más información sobre cómo [ver detalles y crear o actualizar registros](../add-form.md).
- Consulte otros tipos de [orígenes de datos](../connections-list.md) a los que se puede conectar.
