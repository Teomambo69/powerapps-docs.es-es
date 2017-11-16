---
title: "Generación de una aplicación a partir de datos de Excel | Microsoft Docs"
description: "Cree una aplicación automáticamente basándose en un archivo de Excel en la nube, personalice la aplicación y, a continuación, explore cómo funciona."
services: 
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: karthikb
ms.openlocfilehash: e6ad4896beb28b5b38b22706838fec5f6a6840ec
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="generate-an-app-from-excel-data"></a>Creación de una aplicación a partir de datos de Excel
Cree una aplicación automáticamente en función de los datos de un archivo Excel que se carga en una cuenta de almacenamiento en la nube, como OneDrive. Después de generar la aplicación, personalícela para que se adapte mejor a sus necesidades y, después, ejecútela para asegurarse de que funciona según lo esperado.

De forma predeterminada, las aplicaciones generadas tienen tres pantallas:

* **BrowseScreen1** muestra un subconjunto de uno o varios campos, una barra de búsqueda y un botón de ordenación que permite que los usuarios encuentren fácilmente un registro específico.
* **DetailsScreen1** muestra algunos o todos los campos de un registro específico.
* **EditScreen1** proporciona elementos de interfaz de usuario que permiten que los usuarios creen o actualicen un registro y guarden los cambios.

**Nota**: También puede generar una aplicación a partir de una [lista personalizada de SharePoint](app-from-sharepoint.md).

## <a name="prerequisites"></a>Requisitos previos
* [Suscríbase](signup-for-powerapps.md) a PowerApps y, después, siga estos pasos:
  * Instale [PowerApps Studio para Windows](http://aka.ms/powerappsinstall) en un equipo que ejecute Windows 8, Windows 8.1 o Windows 10.
  * Abra [PowerApps Studio para la web](create-app-browser.md) (versión preliminar) en un explorador.
* Inicie sesión en PowerApps con las mismas credenciales que utilizó para suscribirse.
* Para seguir este tutorial exactamente, descargue este [archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx).
  
    **Importante**: Puede utilizar su propio archivo de Excel si los datos tienen formato de tabla. Para más información, consulte [Crear o eliminar una tabla de Excel](https://support.office.com/en-us/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).
* Cargue el archivo de Excel en OnDrive y otra [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md).

## <a name="create-an-app"></a>Crear una aplicación
1. En PowerApps Studio, pulse o haga clic en **Nuevo** en el menú **Archivo** (cerca del borde izquierdo).
   
    ![Opción Nuevo en el menú Archivo](./media/get-started-create-from-data/file-new.png)
2. Siga cualquiera de estos pasos:
   
   * Si aparece la cuenta en la nube en **Comenzar con los datos**, pulse o haga clic en **Diseño de teléfono**.
     
     ![Opción para crear una aplicación a partir de datos](./media/get-started-create-from-data/create-from-data.png)
   * Si no aparece la cuenta de almacenamiento en la nube en **Comenzar con los datos**, haga clic en la flecha situada al final de la fila de iconos. Si aparece la cuenta en la lista de conexiones, haga clic o pulse en esa entrada.
   * Si su cuenta de almacenamiento en la nube no aparece en **Comenzar con los datos** ni en la lista de conexiones, haga clic o pulse en **Nueva conexión**; después, haga clic o pulse en la entrada de la cuenta. Haga clic o pulse en **Conectar** y siga las indicaciones para configurar la conexión.
     
     ![Conectarse a OneDrive](./media/get-started-create-from-data/connect-onedrive.png)
3. En **Choose an Excel file** (Elegir un archivo de Excel), vaya a **FlooringEstimates.xlsx** y haga clic o pulse en él.
   
    ![Archivo de Excel llamado FlooringEstimates](./media/get-started-create-from-data/choose-spreadsheet.png)  
4. En **Elegir una tabla**, haga clic o pulse en **FlooringEstimates**.  
   
    ![Seleccionar tabla FlooringEstimates](./media/get-started-create-from-data/choose-table.png)
5. Haga clic o pulse en **Conectar** para generar la aplicación.
6. Si se le pide que realice un paseo introductorio, haga clic o pulse en **Siguiente** para familiarizarse con las áreas principales de la interfaz de usuario de PowerApps (o haga clic o pulse en **Omitir**).
   
    ![Elegir Siguiente para el paseo](./media/get-started-create-from-data/quick-tour.png)
   
    **Nota**: Siempre puede realizar el paseo más tarde haciendo clic o pulsando en el icono del signo de interrogación situado cerca de la esquina superior derecha de la pantalla y, a continuación, haciendo clic o pulsando en **Take the intro tour** (Realizar paseo introductorio).

## <a name="change-the-gallery-layout"></a>Cambiar el diseño de la galería
Cuando se crea una aplicación, tiene un diseño predeterminado en función de los datos, pero puede personalizarlo para ajustarlo a sus necesidades.

1. En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.
   
    ![Alternancia de las vistas](./media/get-started-create-from-data/toggle-view.png)
2. Haga clic o pulse en la miniatura superior para asegurarse de que la pantalla de exploración (**BrowseScreen1**) está seleccionada.
3. Haga clic o pulse en cualquier parte de la galería, por ejemplo, en la primera imagen.
   
    ![Selección de la imagen](./media/get-started-create-from-data/select-image.png)
4. En el panel derecho, abra la lista **Diseño** y luego haga clic o pulse en un diseño que contenga una imagen, un título y un subtítulo.
   
    ![Seleccionar diseño](./media/get-started-create-from-data/select-layout.png)
   
    El diseño de la aplicación cambia para reflejar su elección.
   
    ![BrowseScreen1 con el nuevo diseño](./media/get-started-create-from-data/browse-layout.png)

## <a name="change-the-data-that-appears"></a>Cambiar los datos que aparecen
1. En **Buscar en elementos**, haga clic o pulse en **Carpet** para seleccionar el control **Etiqueta**.
   
   La lista asociada se resalta en el panel derecho.
   
   ![Selección de la primera etiqueta](./media/get-started-create-from-data/select-gallery-textbox.png)
2. En el panel derecho, abra la lista resaltada y haga pulse o haga clic en **Nombre**.
   
    ![Establecimiento de la primera etiqueta](./media/get-started-create-from-data/set-gallery-textbox.png)
3. Abra la lista inferior y pulse o haga clic en **Categoría**.
   
    ![Establecer la categoría](./media/get-started-create-from-data/set-category.png)
   
    **BrowseScreen1** cambia para mostrar un nombre y una categoría para cada registro.
   
    ![BrowseScreen1 con el nuevo contenido](./media/get-started-create-from-data/browse-content.png)
   
    **Nota**: De forma predeterminada, puede desplazarse por la lista (denominada galería) mediante la rueda del mouse o deslizándose hacia arriba y hacia abajo por una pantalla táctil. Para usar un trackpad o un mouse sin rueda, seleccione la galería, pulse o haga clic en **Mostrar barra de desplazamiento** en la lista de propiedades, y reemplace **false** por **true** en la barra de fórmulas.

## <a name="change-the-order-of-fields-in-a-form"></a>Cambiar el orden de los campos de un formulario
1. En la barra de navegación izquierda, pulse o haga clic en la miniatura intermedia para abrir la pantalla de detalles (**DetailsScreen1**).
   
    ![Miniatura de DetailScreen1](./media/get-started-create-from-data/detail-screen-thumbnail.png)
2. Pulse o haga clic en la imagen para mostrar las opciones que están disponibles para personalizar el formulario.
   
    ![Seleccionar una tarjeta](./media/get-started-create-from-data/select-card.png)
3. En el panel derecho, arrastre el campo **Nombre** a la parte superior de la lista.
   
    ![Mover una tarjeta](./media/get-started-create-from-data/move-card.png)
   
    La pantalla se actualiza para reflejar los cambios realizados.
   
    ![Nombre al principio de la pantalla](./media/get-started-create-from-data/name-first.png)

## <a name="change-a-control"></a>Cambiar un control
1. En la barra de navegación izquierda, pulse o haga clic en la miniatura inferior para abrir la pantalla de edición (**EditScreen1**).
   
    ![Miniatura de EditScreen1](./media/get-started-create-from-data/edit-screen-thumbnail.png)
2. Pulse o haga clic en **Información general**.
   
    En este paso se selecciona la tarjeta Información general. Cada tarjeta contiene texto que describe el propósito de la tarjeta. También puede personalizar los controles en una tarjeta. Para más información, consulte [Control Card en PowerApps](controls/control-card.md).
   
    ![Seleccione la tarjeta de información general](./media/get-started-create-from-data/select-overview.png)
3. En el panel derecho, pulse o haga clic en la flecha hacia abajo de la tarjeta, desplácese hacia abajo y pulse o haga clic en **Editar texto multilínea**.
   
    En este paso se muestra información general de cada producto en un control que es lo suficientemente grande como para mostrar el texto.
   
    ![Cambiar tarjeta](./media/get-started-create-from-data/card-selector.png)

## <a name="run-the-app"></a>Ejecutar la aplicación
A medida que personaliza una aplicación, puede probar los cambios mediante la ejecución de la aplicación en el modo de vista previa.

1. En la barra de navegación izquierda, pulse o haga clic en la miniatura superior para abrir la pantalla de navegación (**BrowseScreen1**).
2. Para abrir el modo de vista previa, presione F5 o pulse o haga clic en el botón **Reproducir**, situado cerca de la esquina superior derecha.
   
    ![Icono de vista previa](./media/get-started-create-from-data/open-preview.png)
3. En **BrowseScreen1**, pulse o haga clic en la flecha situada a la derecha de un registro para mostrar el registro en la pantalla de detalles (**DetailsScreen1**).
   
    ![Seleccionar una flecha en BrowseScreen1](./media/get-started-create-from-data/select-record.png)
4. En **DetailsScreen1**, haga clic o pulse en el icono de lápiz en la esquina superior derecha para mostrar el registro en la pantalla de edición (**EditScreen1**).
   
    ![Editar un registro](./media/get-started-create-from-data/edit-record.png)
5. En **EditScreen1**, cambie la información de uno o varios campos y, a continuación, haga clic o pulse en la marca de verificación de la esquina superior derecha para guardar los cambios.
   
    ![Guardar cambios en EditScreen1](./media/get-started-create-from-data/save-record.png)
6. Cierre el modo de vista previa presionando Esc (o pulsando o haciendo clic en el icono Cerrar, debajo de la barra de título).
   
    ![Cerrar el modo de vista previa](./media/get-started-create-from-data/close-preview.png)

## <a name="known-limitations"></a>Limitaciones conocidas
Para más información sobre cómo compartir datos de Excel en su organización, [repase estas limitaciones](connections/cloud-storage-blob-connections.md#sharing-excel-tables).

## <a name="next-steps"></a>Pasos siguientes
* Para guardar la aplicación de forma que se pueda ejecutar desde otros dispositivos, pulse Ctrl-S.
* Ahora que ha aprendido cómo generar una aplicación de datos, puede [crear una aplicación desde el principio](get-started-create-from-blank.md).
* [Comparta la aplicación](share-app.md) para que otras personas puedan ejecutarla.

