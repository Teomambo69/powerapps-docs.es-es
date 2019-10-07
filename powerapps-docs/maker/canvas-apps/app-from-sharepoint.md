---
title: Generación de una aplicación de lienzo a partir de una lista de SharePoint | Microsoft Docs
description: En PowerApps, genere automáticamente una aplicación de lienzo para administrar datos de una lista de SharePoint.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/09/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: af06a3707073498df65f782fc634c1e93b1760c5
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994079"
---
# <a name="generate-a-canvas-app-in-powerapps-from-a-sharepoint-list"></a>Generación de una aplicación de lienzo en PowerApps a partir de una lista de SharePoint

En este tema utilizará PowerApps para generar automáticamente una aplicación de lienzo basada en elementos de una lista de SharePoint. Puede generar la aplicación en PowerApps o SharePoint Online. En PowerApps, puede generar la aplicación a partir de una lista en un sitio de SharePoint local si se [conecta al sitio](connections/connection-sharepoint-online.md#create-a-connection) a través de una puerta de enlace de datos.

La aplicación que se genere contendrá tres pantallas:

- En la pantalla de exploración, puede desplazarse por todos los elementos de la lista.
- En la pantalla de detalles, puede mostrar toda la información sobre un solo elemento de la lista.
- En la pantalla de edición, puede crear un elemento o actualizar información sobre un elemento existente.

Puede aplicar los conceptos y las técnicas de este tema a cualquier lista de SharePoint. Para seguir exactamente los pasos:

1. En un sitio de SharePoint Online, cree una lista llamada **SimpleApp**.
2. En la columna de nombre **Título**, cree entradas para **Vainilla**, **Chocolate** y **Fresa**.

Los principios para generar una aplicación no cambiarán aunque cree una lista mucho más compleja con muchas columnas de diversos tipos tales como texto, fechas, números y moneda.

> [!IMPORTANT]
> PowerApps no admite todos los tipos de datos de SharePoint. Para más información, consulte [Problemas conocidos](connections/connection-sharepoint-online.md#known-issues).

## <a name="generate-an-app-from-within-powerapps"></a>Generación de una aplicación en PowerApps

1. Inicie sesión en [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. En **Cree su propia aplicación**, mantenga el puntero sobre **Iniciar a partir de datos** y seleccione **Crear esta aplicación**.

    ![Opción para crear una aplicación](./media/app-from-sharepoint/start-from-data.png)

1. En el icono de SharePoint, seleccione **Diseño de teléfono**.

    ![Opción para crear una aplicación](./media/app-from-sharepoint/sharepoint-tile.png)

1. Con la opción **Conectar directamente** seleccionada, haga clic en **Crear**.

    ![Crear conexión](./media/app-from-sharepoint/create-connection.png)

1. En **Conectar a un sitio de SharePoint**, escriba o pegue la dirección URL para el sitio de SharePoint Online y, después, haga clic en **Ir**.

    Incluya solo la dirección URL del sitio (no el nombre de la lista), como en este ejemplo:<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. En **Elegir una lista**, seleccione **SimpleApp** y, después, haga clic en **Conectar**.

    Después de unos minutos, la aplicación se abre en la pantalla de exploración, en la que se muestran los elementos creados en la lista. Si la lista tiene datos en más columnas además de **Título**, la aplicación mostrará esos datos. Cerca de la parte superior de la pantalla, en una barra de título se muestran iconos para actualizar la lista, ordenarla y crear un elemento en la lista. Bajo la barra de título, un cuadro de búsqueda proporciona la opción de filtrar la lista según el texto que se escriba o pegue. 

    ![Pantalla de exploración](./media/app-from-sharepoint/browse-screen.png)

    Probablemente le interesará realizar más cambios antes de usar esta aplicación o compartirla con otros usuarios. Como procedimiento recomendado, guarde el trabajo realizado hasta el momento antes de continuar presionando Ctrl-S. Asigne un nombre a la aplicación y, después, haga clic en **Guardar**.

## <a name="generate-an-app-from-within-sharepoint-online"></a>Generación de una aplicación en SharePoint Online

Si crea una aplicación de una lista personalizada desde la barra de comandos de SharePoint Online, la aplicación aparece como una vista de esa lista. También se puede ejecutar la aplicación en un dispositivo iOS o Android, además de un explorador web.

1. En SharePoint Online, abra una lista personalizada, seleccione **PowerApps** en la barra de comandos y luego elija **Crear una aplicación**.

    ![Crear una aplicación](./media/app-from-sharepoint/generate-new-app.png)

2. En el panel que aparece, escriba un nombre para la aplicación y seleccione **Crear**.

    ![Asignar un nombre a la aplicación](./media/app-from-sharepoint/app-name.png)

    Aparece una nueva pestaña en el explorador web que muestra la aplicación generada automáticamente basada en la lista de SharePoint. La aplicación aparece en PowerApps Studio, donde se puede personalizar.

    ![Aplicación predeterminada](./media/app-from-sharepoint/default-app.png)

3. (opcional) Actualice la pestaña del explorador para su lista de SharePoint (seleccionándola y presionando, por ejemplo, F5), y luego siga estos pasos para ejecutar o administrar la aplicación:

    - Para ejecutar la aplicación (en una pestaña independiente del explorador), seleccione **Abrir**.
    - Para permitir que otros usuarios de la organización ejecuten la aplicación, seleccione **Hacer pública esta vista**.

        Para permitir que otros usuarios editen la aplicación, [compártala](share-app.md) con permisos **Puede editar**.

    - Para quitar la vista de SharePoint, seleccione **Quitar esta vista**.

        Para quitar la aplicación de PowerApps, [elimine la aplicación](delete-app.md).

## <a name="next-steps"></a>Pasos siguientes
En este tema ha creado una aplicación para administrar datos en una lista de SharePoint. El siguiente paso es generar una aplicación a partir de una lista más compleja y, después, personalizar la aplicación (empezando por la pantalla de exploración) para que se ajuste mejor a las necesidades.

> [!div class="nextstepaction"]
> [Personalizar una pantalla de exploración predeterminada](customize-layout-sharepoint.md)
