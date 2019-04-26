---
title: Adición de imágenes en Excel | Microsoft Docs
description: Instrucciones paso a paso para agregar archivos de imagen y dibujos a Excel en una cuenta de almacenamiento en la nube
author: adrianorth
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/25/2016
ms.author: aorth
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d2e61a312aa3824c24b7058da4b34aa9c5cf462c
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63321533"
---
# <a name="add-images-to-excel-from-powerapps"></a>Agregar imágenes en Excel desde PowerApps
Cree automáticamente una aplicación donde los usuarios puedan ver, agregar o eliminar imágenes de archivos o dibujos desde un control de **entrada manuscrita**. La aplicación necesita un archivo de Excel que debe crearse y cargarse en una cuenta de almacenamiento en la nube.

## <a name="prerequisites"></a>Requisitos previos

* Es necesario tener conocimientos acerca de cómo [agregar y configurar controles](add-configure-controls.md).
* Es necesario tener conocimientos acerca de cómo [configurar los datos de Excel como tabla](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370?ui=en-US&rs=en-US&ad=US).
* [PowerApps debe tener conexión ](add-data-connection.md) con una cuenta de almacenamiento en la nube (como Dropbox, OneDrive o Google Drive) en la que se pueda guardar un archivo de Excel.

## <a name="create-the-data-source-and-the-app"></a>Crear el origen de datos y la aplicación
1. En Excel, escriba **Caption** e **Image [image]** en dos celdas contiguas (por ejemplo, A1 y B1) que estén justo encima de dos celdas vacías.
2. Aplique el formato de tabla tanto a las celdas que acaba de actualizar como a las que están debajo y asigne un nombre a la tabla (por ejemplo, **Images**).
   
    ![Crear una tabla](./media/add-images-to-excel/create-table.png)
3. Guarde el archivo (por ejemplo, como **ImageDemo**) y cárguelo en la cuenta de almacenamiento en la nube.
4. En PowerApps, en el menú **Archivo**, pulse o haga clic en **Nuevo** (si aún no ha abierto la aplicación, encontrará esta opción en el lado izquierdo) y, en el icono de la cuenta de almacenamiento en la nube, pulse o haga clic en **Diseño de teléfono**.
   
    ![Seleccione la cuenta de almacenamiento en la nube](./media/add-images-to-excel/select-account.png)
5. En **Elegir un archivo de Excel**, pulse o haga clic en el archivo que creó.
   
    ![Seleccione el libro](./media/add-images-to-excel/select-workbook.png)
6. En **Elegir una tabla**, pulse o haga clic en la tabla que creó y en **Conectar**.
   
    ![Seleccione la tabla](./media/add-images-to-excel/select-table.png)
7. Si aparece el paseo introductorio, puede seguirlo, o bien pulsar o hacer clic en **Omitir**.
   
    ![Primera pantalla del recorrido rápido](./media/add-images-to-excel/quick-tour.png)

## <a name="add-an-image-from-a-file"></a>Agregar imágenes desde un archivo
1. Abra el modo de vista previa; para ello, presione F5 (también puede pulsar o hacer clic en el botón de reproducción situado junto a la esquina superior derecha) y pulse o haga clic en el icono con el signo más que se encuentra en la esquina superior derecha.
   
    ![Icono con el signo más](./media/add-images-to-excel/plus-icon.png)
2. En el cuadro **Título**, escriba o pegue una breve descripción del archivo de imagen que desea agregar y pulse o haga clic debajo para seleccionar el archivo.
3. En el cuadro de diálogo **Abrir**, busque el archivo que desea agregar y pulse o haga clic en **Abrir**.
   
    ![Agregue un título y una imagen](./media/add-images-to-excel/add-image.png)
4. Pulse o haga clic en el icono con la marca de verificación de la esquina superior derecha para guardar los cambios.
   
    ![Guardar cambios](./media/add-images-to-excel/checkmark-icon.png)
5. Agregue todas las imágenes que desee repitiendo estos tres últimos pasos. Cuando haya terminado, presione Esc para volver al área de trabajo predeterminada.
6. (Opcional) Elimine los controles **Etiqueta** que muestren el título de cada imagen.

## <a name="add-a-drawing"></a>Agregar un dibujo
1. Abra **EditarPantalla1** pulsando o haciendo clic en la barra de navegación externa y pulse o haga clic en la tarjeta de imagen para seleccionarla.
   
    ![Seleccione la tarjeta de imagen](./media/add-images-to-excel/select-card.png)
2. En el panel derecho, pulse o haga clic en el selector de la tarjeta de imagen y en **Agregar notas**.
   
    ![Agregar notas](./media/add-images-to-excel/add-notes.png)
3. Abra **ExaminarPantalla1** pulsando o haciendo clic en la barra de navegación izquierda y abra el modo de vista previa.
4. Pulse o haga clic en el icono con el signo más situado en la esquina superior derecha, agregue un título y haga un dibujo en el control **Entrada manuscrita**.
   
    ![Haga un dibujo](./media/add-images-to-excel/draw-picture.png)
5. Pulse o haga clic en el icono con la marca de verificación de la esquina superior derecha para guardar los cambios.
   
    ![Guardar cambios](./media/add-images-to-excel/checkmark-icon.png)
6. Agregue todos los dibujos que desee repitiendo estos dos últimos pasos. Cuando haya terminado, presione Esc para volver al área de trabajo predeterminada.

