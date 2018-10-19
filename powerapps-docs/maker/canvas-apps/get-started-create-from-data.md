---
title: Generar una aplicación desde Excel | Microsoft Docs
description: Use PowerApps para generar automáticamente una aplicación de lienzo mediante un archivo de Excel almacenado en una cuenta de almacenamiento en la nube.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b1531289c55772aaa9ee521c92cc8b5dbfe16ad4
ms.sourcegitcommit: 02d0234bd84352bf1c43d0fc9225ab60947a0add
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49317031"
---
# <a name="generate-a-canvas-app-from-excel-in-powerapps"></a>Generar una aplicación desde Excel en PowerApps

En este tema, generará automáticamente su primera aplicación de lienzo en PowerApps con los datos de una tabla de Excel. Podrá seleccionar un archivo de Excel, generar una aplicación y, después, ejecutar la aplicación que genere. En todas las aplicaciones generadas se incluyen pantallas para examinar los registros, mostrar detalles de los registros y crear o actualizar registros. Mediante la generación de una aplicación, se puede obtener rápidamente una aplicación en funcionamiento con datos de Excel y, después, se puede personalizar para ajustarla mejor a las necesidades. 

El archivo de Excel debe estar en una cuenta de almacenamiento en la nube, como OneDrive, Google Drive o Dropbox. En este tema se usa OneDrive para la Empresa.

Si no tiene una licencia para PowerApps, puede [registrarse gratuitamente](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Requisitos previos ##
Para seguir este tema con exactitud, descargue el archivo [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) en Excel y guárdelo en la [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md).

> [!IMPORTANT]
> Puede usar su propio archivo de Excel, pero los datos deberán tener formato de tabla. Para obtener más información, vea [Dar formato a una tabla](how-to-excel-tips.md). 

## <a name="generate-the-app"></a>Generar la aplicación
1. Inicie sesión en [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. En **Cree su propia aplicación**, mantenga el puntero sobre **Iniciar a partir de datos** y seleccione **Crear esta aplicación**.

    ![Opción para crear una aplicación](./media/get-started-create-from-data/start-from-data.png)

1. En **Comenzar con los datos**, pulse o haga clic en **Diseño de teléfono** en el icono de la cuenta de almacenamiento en la nube.

    ![Opción para crear una aplicación](./media/get-started-create-from-data/odfb-tile.png)

1. Si se le solicita, pulse o haga clic en **Conectar** y proporcione las credenciales para esa cuenta.

1. En **Choose an Excel file** (Elegir un archivo de Excel), vaya a **FlooringEstimates.xlsx** y haga clic o pulse en él. 

1. En **Elegir una tabla**, haga clic o pulse en **FlooringEstimates** y, a continuación, haga clic o pulse **Conectar**.

    ![Opción para crear una aplicación](./media/get-started-create-from-data/choose-table.png)

## <a name="run-the-app"></a>Ejecutar la aplicación
1. Para abrir la vista previa, presione F5 (o haga clic o pulse en el icono de reproducción situado cerca de la esquina superior derecha).

    ![Abrir vista previa](./media/get-started-create-from-data/open-preview.png)

1. Alterne el criterio de ordenación pulsando o haciendo clic en el icono Ordenar cerca de la esquina superior derecha.

    ![Icono Ordenar](./media/get-started-create-from-data/sort-icon.png)

1. Para filtrar la lista, escriba o pegue uno o varios caracteres en el cuadro de búsqueda.

1. Pulse o haga clic en el icono Más para agregar un registro, agregue los datos que quiera y, después, pulse o haga clic en el icono de marca de verificación para guardar los cambios.

1. Pulse o haga clic en la flecha siguiente del registro que ha agregado, pulse o haga clic en el icono de lápiz para editar el registro, actualice uno o varios campos y, después pulse o haga clic en el icono de marca de verificación para guardar los cambios.

1. Pulse o haga clic en la flecha siguiente del registro que ha agregado, pulse o haga clic en el icono de lápiz para editar el registro, actualice uno o varios campos y, después pulse o haga clic en el icono Cancelar para descartar los cambios.

1. Pulse o haga clic en la flecha siguiente del registro que ha agregado y, después, pulse o haga clic en el icono Papelera para eliminar ese registro.

## <a name="next-steps"></a>Pasos siguientes
Personalice la pantalla de exploración predeterminada para que se ajuste mejor a sus necesidades. Por ejemplo, puede ordenar y filtrar la lista por nombre de producto, no por categoría.

> [!div class="nextstepaction"]
> [Personalizar una pantalla de exploración predeterminada](customize-layout-sharepoint.md).
