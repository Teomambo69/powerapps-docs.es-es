---
title: Crear una aplicación de lienzo desde Excel | Microsoft Docs
description: Usar Power apps para crear automáticamente una aplicación de lienzo con un archivo de Excel almacenado en una cuenta de almacenamiento en la nube
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2199d94938e51154d0f616f424f674c408277b52
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959435"
---
# <a name="create-a-canvas-app-from-excel-in-power-apps"></a>Creación de una aplicación de lienzo desde Excel en Power apps

En este tema, creará su primera aplicación de lienzo en Power apps con datos de una tabla de Excel. Seleccionará un archivo de Excel, creará una aplicación y, a continuación, ejecutará la aplicación que cree. Cada aplicación creada incluye pantallas para examinar registros, mostrar detalles de los registros y crear o actualizar registros. Mediante la generación de una aplicación, se puede obtener rápidamente una aplicación en funcionamiento con datos de Excel y, después, se puede personalizar para ajustarla mejor a las necesidades. 

El archivo de Excel debe estar en una cuenta de almacenamiento en la nube, como OneDrive, Google Drive o Dropbox. En este tema se usa OneDrive para la Empresa.

Si no tiene una licencia de Power Apps, puede [registrarse de forma gratuita](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Requisitos previos

Para seguir este tema con exactitud, descargue el archivo [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) en Excel y guárdelo en la [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md).

> [!IMPORTANT]
> Puede usar su propio archivo de Excel, pero los datos deberán tener formato de tabla. Para obtener más información, vea [Dar formato a una tabla](how-to-excel-tips.md). 

## <a name="create-the-app"></a>Crear la aplicación

1. Inicie sesión en [Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

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

    Por ejemplo, escriba o pegue **miel** para mostrar el único registro para el que aparece esa cadena en el nombre, la categoría o la información general del producto.

    ![Ejemplo de filtro](./media/get-started-create-from-data/filter-example.png)

1. Agregar un registro:

    1. Seleccione el icono de signo más.

        ![Icono con el signo más](./media/get-started-create-from-data/plus-icon.png)

    1. Agregue los datos que desee y, a continuación, seleccione el icono de marca de verificación para guardar los cambios.

        ![Icono Guardar](./media/get-started-create-from-data/save-icon.png)

1. Editar un registro:

    1. Seleccione la flecha del registro que desea editar.

        ![Flecha siguiente](./media/get-started-create-from-data/next-arrow.png)

    1. Seleccione el icono de lápiz.

        ![Icono de lápiz](./media/get-started-create-from-data/pencil-icon.png)

    1. Actualice uno o varios campos y, a continuación, seleccione el icono de marca de verificación para guardar los cambios.

        ![Icono Guardar](./media/get-started-create-from-data/save-icon.png)

        Como alternativa, seleccione el icono Cancelar para descartar los cambios.

1. Eliminar un registro:

    1. Seleccione la flecha siguiente para el registro que desea eliminar.

        ![Flecha siguiente](./media/get-started-create-from-data/next-arrow.png)

    1. Seleccione el icono de la papelera.

        ![Icono de la papelera](./media/get-started-create-from-data/trash-icon.png)

## <a name="next-steps"></a>Pasos siguientes

Personalice la pantalla de exploración predeterminada para que se ajuste mejor a sus necesidades. Por ejemplo, puede ordenar y filtrar la lista por nombre de producto, no por categoría o por introducción.

> [!div class="nextstepaction"]
> [Personalizar una pantalla de exploración predeterminada](customize-layout-sharepoint.md).
