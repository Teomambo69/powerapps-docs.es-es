---
title: "Inserción de archivos multimedia en una aplicación y su carga | Microsoft Docs"
description: "Aprenda a mostrar los archivos multimedia de una aplicación y a cargarlos en un origen de datos."
services: 
suite: powerapps
documentationcenter: 
author: karthik-1
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/12/2017
ms.author: sharik
ms.openlocfilehash: 849bde71d8f5dcf6505721758e2edca0921146bb
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="using-multimedia-files-in-powerapps"></a>Utilizar archivos multimedia en PowerApps
En este tema, aprenderá a insertar archivos multimedia en la aplicación, a cargar dibujos en un origen de datos y a mostrar imágenes procedentes de un origen de datos en la aplicación. El origen de datos que vamos a usar en este tema es un archivo de Excel guardado en OneDrive para la Empresa.

## <a name="prerequisites"></a>Requisitos previos
[Regístrese](signup-for-powerapps.md) en PowerApps e [instálelo](http://aka.ms/powerappsinstall). Cuando abra PowerApps, inicie sesión con las mismas credenciales que usó para registrarse.

## <a name="add-media-from-a-file-or-the-cloud"></a>Agregar contenido multimedia desde un archivo o la nube
Puede elegir el tipo de contenido multimedia que desea agregar; por ejemplo, imágenes, vídeo o audio.

1. En la pestaña **Contenido**, seleccione **Multimedia**.

2. En **Multimedia**, seleccione **Imágenes**, **Vídeos** o **Audio** y después **Examinar**:

    ![Examinar medios][1]

3. Elija el archivo que desea agregar y seleccione **Abrir**.

    Se abrirá la carpeta **Imágenes** de su equipo y podrá seleccionar una imagen o acceder a otra carpeta.

4. Cuando haya terminado de agregar archivos, presione Esc para volver al área de trabajo predeterminada.

5. En la pestaña **Insertar**, seleccione **Multimedia** y después **Imagen**, **Vídeo** o **Audio**:

    ![Seleccionar tipo de medio][8]

6. Si agrega un control de imagen, establezca la propiedad **[Imagen](controls/properties-visual.md)** en el archivo que agregó:  

    ![Configurar la propiedad Imagen](./media/add-images-pictures-audio-video/imageproperty.png)

    > [!NOTE]
> El nombre de archivo debe especificarse sin la extensión y entre comillas simples.

7. Si agrega un control de vídeo o audio, establezca la propiedad **Media** (Multimedia) en el archivo que agregó:  

    ![Configurar la propiedad Media (Multimedia)](./media/add-images-pictures-audio-video/mediaproperty.png)

    > [!NOTE]
> Para reproducir un vídeo de YouTube, la propiedad **Media** (Multimedia) del control de vídeo tiene que establecerse en la dirección URL correspondiente, que debe escribirse entre comillas dobles.

## <a name="add-media-from-azure-media-services"></a>Agregar contenido multimedia desde Azure Media Services
1. Desde su cuenta de Azure Media Services, cargue y publique sus recursos de vídeo desde **AMS > Configuración > Activos**.

2. Una vez publicado el vídeo, copie su dirección URL.

3. Desde PowerApps, agregue el control **Vídeo** desde **Insertar > Multimedia**.

4. Establezca la propiedad **Multimedia** en la dirección URL que copió.

    Como se muestra en este gráfico, puede elegir cualquier dirección URL de streaming que admita Azure Media Services:

    ![Configurar la propiedad Media (Multimedia)](./media/add-images-pictures-audio-video/ams-with-powerapps.png)

## <a name="add-images-from-the-cloud-to-your-app"></a>Agregar imágenes a la aplicación desde la nube
En este ejemplo, tiene imágenes guardadas en una cuenta de almacenamiento en la nube de OneDrive para la Empresa. Además, utiliza una tabla de Excel donde se almacenan las rutas de acceso de las imágenes y estas imágenes se muestran en la aplicación mediante un control de la galería.

En este ejemplo, vamos a utilizar [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip), que contiene algunos archivos .jpeg.

> [!NOTE]
> Las rutas de acceso a estas imágenes que se utilizan en el archivo de Excel deben escribirse usando barras diagonales. Cuando PowerApps guarda las rutas de las imágenes en una tabla de Excel, las rutas contienen barras diagonales inversas. Si utiliza rutas de imágenes que proceden, por ejemplo, de una tabla, debe cambiar las rutas de la tabla de Excel para que contengan barras diagonales en lugar de barras diagonales inversas. De lo contrario, no se mostrarán las imágenes.  

1. Descargue [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) y extraiga la carpeta **Assets** en la cuenta de almacenamiento en la nube.

2. Cambie el nombre de la carpeta **Assets** por **Assets_images**.

3. En una hoja de cálculo de Excel, cree una tabla de una sola columna y rellénala con los siguientes datos:

    ![Tabla Jackets](./media/add-images-pictures-audio-video/jackets.png)

4. Asigne el nombre **Jackets** a la tabla y el nombre **Assets.xlsx** al archivo de Excel.

5. En la aplicación, agregue la tabla **Jackets** como origen de datos.  

6. Agregue un control **Solo imagen** (pestaña **Insertar** > **Galería**) y establezca la propiedad **Elementos** en `Jackets`:  

    ![Propiedad Items](./media/add-images-pictures-audio-video/items-jackets.png)

    La galería se actualiza automáticamente con las imágenes:  

    ![Imágenes de Jackets](./media/add-images-pictures-audio-video/images.png)

    Cuando defina la propiedad **Elementos**, automáticamente se agregará la columna **PowerAppsId** (IdDePowerApps) a la tabla de Excel.

    En la tabla de Excel, la ruta de acceso de una imagen también puede ser una dirección URL. Una muestra de ello sería el archivo de ejemplo [Flooring Estimates](http://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx). Puede descargar este archivo en la cuenta de almacenamiento en la nube, agregar la tabla `FlooringEstimates` como origen de datos de la aplicación y establecer el control de la galería en `FlooringEstimates`. La galería se actualiza automáticamente con las imágenes.

## <a name="upload-pen-drawings-to-the-cloud"></a>Cargar dibujos en la nube
En este ejemplo, aprenderá a cargar dibujos en el origen de datos, OneDrive para la Empresa, y descubrirá cómo se guardan allí los dibujos.

1. En Excel, escriba **Image [image]** en la celda A1.

2. Siga estos pasos para crear una tabla:    

   1. Seleccione la celda A1.

   2. En la cinta **Insertar**, seleccione **Tabla**.

   3. En el cuadro de diálogo, seleccione **La tabla tiene encabezados** y **Aceptar**.

       ![Crear una tabla](./media/add-images-pictures-audio-video/create-table.png)

       Ahora, el archivo de Excel tiene formato de tabla. Para más información sobre el formato de tabla de Excel, consulte [Aplicar formato a una tabla de Excel](https://support.office.com/en-us/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370).

   4. Asigne a la tabla el nombre **Drawings**:

       ![Cambie el nombre de la tabla a Drawings](./media/add-images-pictures-audio-video/name-media-table.png)

3. Guarde el archivo de Excel en OneDrive para la Empresa como **SavePen.xlsx**.

4. En PowerApps, cree una [aplicación en blanco](get-started-create-from-blank.md).

5. En la aplicación, agregue la cuenta de OneDrive para la Empresa como [origen de datos](add-data-connection.md):

   1. Pulse o haga clic en la pestaña **Vista** y, luego, en **Orígenes de datos**.

       ![](./media/add-images-pictures-audio-video/choose-data-sources.png)

   2. Pulse o haga clic en **Agregar origen de datos** y en **OneDrive para la Empresa**.

       ![](./media/add-images-pictures-audio-video/select-source.png)

   3. Pulse o haga clic en **SavePen.xlsx**.

   4. Seleccione la tabla **Drawings** y pulse o haga clic en **Conectar**.

       ![Conectar](./media/add-images-pictures-audio-video/savepen.png)  

       Ahora, la tabla Drawings aparece como origen de datos.

6. En la pestaña **Insertar**, seleccione **Texto** y **Entrada manuscrita**.

7. Cambie el nombre del control a **MyPen**:  

    ![Cambiar nombre](./media/add-images-pictures-audio-video/rename-mypen.png)

8. En la pestaña **Insertar**, agregue el control **Botón** y establezca la propiedad **AlSeleccionar** en esta fórmula:

    **Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})**

9. Agregue un control de la **Galería de imágenes** (pestaña **Insertar** > **Galería**) y establezca la propiedad **Elementos** en `Drawings`. La propiedad **Image** (Imagen) del control de la galería se establece automáticamente en `ThisItem.Image`.

    Organice los controles tal y como se muestra a continuación:  

    ![Pantalla de ejemplo](./media/add-images-pictures-audio-video/screen.png)

10. Presione F5 o seleccione Vista previa ( ![Botón Vista previa](./media/add-images-pictures-audio-video/preview.png) ).

11. Dibuje algo en MyPen y seleccione el botón.

    En la primera imagen del control de la galería aparecerá lo que ha dibujado.

12. Agregue algo más al dibujo y seleccione el botón.

    En la segunda imagen del control de la galería aparecerá lo que ha dibujado.

13. Cierre la ventana de vista previa con la tecla Esc.

    En la cuenta de almacenamiento en la nube, se crea automáticamente la carpeta **SavePen_images**. Esta carpeta contiene las imágenes guardadas junto con los identificadores de los nombres de archivo. Para ver la carpeta, deberá actualizar la ventana del explorador (por ejemplo, pulsando F5).

    En **SavePen.xlsx**, la ruta de las nuevas imágenes se especifica en la columna **Image**.

### <a name="known-limitations"></a>Limitaciones conocidas
Para más información sobre cómo compartir datos de Excel en su organización, [repase estas limitaciones](connections/cloud-storage-blob-connections.md#sharing-excel-tables).

## <a name="for-more-information"></a>Más información
No olvide probar la aplicación en diferentes plataformas, como en [una ventana del explorador](https://home.dynamics.com/) y en un teléfono.

Para más información sobre escenarios más avanzados en los que el contenido multimedia se carga directamente en un origen de datos distinto, consulte algunas [sugerencias de profesionales para capturar imágenes](https://powerapps.microsoft.com/blog/image-capture-pro-tips/) y descubra cómo usar [conectores personalizados para cargar imágenes](https://powerapps.microsoft.com/blog/custom-api-for-image-upload/).

Otra forma de cargar archivos en un origen de datos consiste en usar la función [Patch](functions/function-patch.md).

[1]: ./media/add-images-pictures-audio-video/add-image-video-audio-file.png
[3]: ./media/add-images-pictures-audio-video/add-intro-sound.png
[4]: ./media/add-images-pictures-audio-video/add-picture.png
[5]: ./media/add-images-pictures-audio-video/camera-gallery.png
[6]: ./media/add-images-pictures-audio-video/audio-gallery.png
[7]: ./media/add-images-pictures-audio-video/pen-gallery.png
[8]: ./media/add-images-pictures-audio-video/mediaoptions.png
[9]: ./media/add-images-pictures-audio-video/imageproperty.png
[10]: ./media/add-images-pictures-audio-video/mediaproperty.png
[11]: ./media/add-images-pictures-audio-video/renamecamera.png
