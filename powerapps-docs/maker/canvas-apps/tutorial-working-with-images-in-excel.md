---
title: Almacenamiento de imágenes en un archivo Excel | Microsoft Docs
description: Cómo guardar una imagen en una tabla de Excel de una cuenta de almacenamiento en nube
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/15/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f201d1fbad574174e4427698ae28439f26419514
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63318379"
---
# <a name="how-to-save-images-in-an-excel-file-and-then-add-these-images-to-your-app"></a>Cómo guardar imágenes en un archivo de Excel y luego agregar estas imágenes a la aplicación

En este tutorial se hará lo siguiente:

* Crear un archivo de Excel y darle el formato de tabla
* Crear una conexión a OneDrive para la Empresa. Servirá cualquier cuenta de almacenamiento en nube. En este tutorial, se usa OneDrive para la Empresa.
* Crear una aplicación con un control de entrada manuscrita
* Guardar las imágenes creadas desde el control de entrada manuscrita en un archivo de Excel
* Mostrar imágenes de un archivo de Excel en la aplicación

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]
* Obtenga información sobre cómo [agregar un origen de datos](add-data-connection.md)

## <a name="create-the-excel-file-as-a-table"></a>Creación del archivo de Excel como tabla

1. En un archivo de Excel en blanco, asígnele a una columna el nombre **Image [imagen]**.
2. Siga estos pasos para crear una tabla:    
   
   1. Seleccione cualquier fragmento de datos en cualquier fila y columna. Por ejemplo, seleccione **Imagen**.
   2. En la cinta **Insertar**, seleccione **Tabla**.
   3. En la ventana de diálogo, seleccione **La tabla tiene encabezados** y, luego, **Aceptar**.
      
      Ahora, el archivo de Excel tiene formato de tabla. El artículo sobre cómo [dar formato de tabla a los datos](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370) proporciona información adicional sobre el formato de tabla en Excel.
   4. Asigne a la tabla el nombre **Drawings**:  
      
      ![Cambio del nombre de la tabla a Drawings](./media/tutorial-working-with-images-in-excel/drawings-table.png)
3. Asigne el nombre **SavePen.xlsx** al archivo de Excel y guárdelo en la cuenta de almacenamiento en nube (OneDrive para la Empresa, Dropbox, etc.).

## <a name="create-an-app-with-the-pen-control"></a>Creación de una aplicación con el control de entrada manuscrita
1. En PowerApps, cree una [aplicación en blanco](get-started-create-from-blank.md).
2. En la aplicación, agregue la cuenta de almacenamiento en nube como un [origen de datos](add-data-connection.md). Una vez que la agregue como origen de datos, agregue **SavePen.xlsx** como conexión y, luego, seleccione la tabla **Drawings**:  
   ![Conectar](./media/tutorial-working-with-images-in-excel/savepen.png)  
   
   Ahora, la tabla Drawings aparece como origen de datos.
3. En el menú **Insertar**, seleccione **Texto** y, luego, **Entrada manuscrita**. Cámbiele el nombre a **MyPen**:  
   
   ![Cambiar nombre](./media/tutorial-working-with-images-in-excel/rename-mypen.png)
4. Agregue un control **Botón** (menú **Insertar**) y establezca su propiedad **OnSelect** en la fórmula siguiente:  
   `Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})`
5. Agregue un control **Galería de imágenes** (menú **Insertar** > **Galería**) y establezca su propiedad **Items** en `Drawings`. La propiedad **Image** del control de galería se establece automáticamente en `ThisItem.Image`.
   
   La pantalla debe ser similar a la siguiente:  
   
   ![Pantalla de ejemplo](./media/tutorial-working-with-images-in-excel/screen.png)  
6. Presione F5 o seleccione Vista previa (![](./media/tutorial-working-with-images-in-excel/preview.png)). Dibuje algo en MyPen y seleccione el botón. En la primera imagen del control de galería aparecerá lo que ha dibujado. Agregue algo más al dibujo y seleccione el botón. En la segunda imagen del control de galería aparecerá lo que ha dibujado.
   
   Cierre la ventana de vista previa.
7. Vaya a la cuenta de almacenamiento en nube. Hay una nueva carpeta **SavePen_images** que se crea automáticamente. Es posible que tenga que actualizar para ver la carpeta nueva. Esta carpeta contiene las imágenes guardadas junto con los identificadores de los nombres de archivo.
   
    Abra SavePen.xlsx. La columna Image incluye la ruta de acceso a estas imágenes nuevas.

## <a name="add-the-image-in-an-excel-file-to-your-app"></a>Incorporación de una imagen de un archivo de Excel en la aplicación
En otro ejemplo, puede guardar imágenes en una cuenta de almacenamiento en nube y, luego, usar una tabla de Excel para mostrar las imágenes en la aplicación.

En este ejemplo, se usa [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip), que contiene algunos archivos .jpeg.

> [!NOTE]
> Cuando se muestran imágenes de un archivo de Excel, en la ruta de acceso a estas imágenes se deben usar barras diagonales. Cuando PowerApps guarda imágenes en una tabla de Excel (como con los pasos anteriores), la ruta de acceso usa barras diagonales inversas. De ese modo, también puede usar **SavePen_images** del ejemplo anterior. Si lo hace, cambie las rutas de acceso en la tabla de Excel para usar barras diagonales en lugar de barras diagonales inversas. De lo contrario, no se mostrarán las imágenes.  

1. Descargue [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) y extraiga la carpeta **Assets** en la cuenta de almacenamiento en nube.
2. En una hoja de cálculo de Excel, cree una tabla similar a la siguiente:
   
    ![Tabla Jackets](./media/tutorial-working-with-images-in-excel/jackets.png)
3. Asigne a la tabla el nombre **Jackets**. Asigne al archivo de Excel el nombre **Assets.xlsx**. También puede cambiar el nombre de la carpeta **Assets** a **Assets_images**.
4. En la aplicación, agregue la tabla **Jackets** como origen de datos.  
5. Agregue un control **Solo imagen** (menú **Insertar** > **Galería**) y establezca la propiedad **Items** en `Jackets`:  
   
    ![Propiedad Items](./media/tutorial-working-with-images-in-excel/items-jackets.png)
   
    La galería se actualiza automáticamente con las imágenes:  
   
    ![Imágenes de chaquetas](./media/tutorial-working-with-images-in-excel/images.png)

Cuando defina la propiedad Items, la tabla de Excel se actualizará automáticamente con una columna nueva llamada **PowerAppsId**.

En la tabla de Excel, la ruta de acceso de una imagen también puede ser una dirección URL. Descargue el archivo de ejemplo [Flooring Estimates](http://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) en la cuenta de almacenamiento en nube, agregue la tabla `FlooringEstimates` como origen de datos de la aplicación y, luego, establezca el control de galería en `FlooringEstimates`. La galería se actualiza automáticamente con las imágenes.

## <a name="learn-more"></a>Más información
[Incorporación de imagen, vídeo o sonido](add-images-pictures-audio-video.md)  
[Visualización de datos en un gráfico de líneas, circular o de barras en la aplicación](use-line-pie-bar-chart.md)  
[Información sobre tablas y registros de PowerApps](working-with-tables.md)

