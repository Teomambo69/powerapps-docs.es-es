---
title: "Creación de una aplicación a partir de una plantilla | Microsoft Docs"
description: "Instrucciones detalladas para crear una aplicación automáticamente basada en una plantilla y, a continuación, guardarla."
services: 
suite: powerapps
documentationcenter: na
author: linhtranms
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/03/2017
ms.author: sharik
ms.openlocfilehash: e8479535098bfd07121d618bc293628c67773b1c
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="create-and-run-an-app-from-a-template"></a>Crear y ejecutar una aplicación a partir de una plantilla
Cree una aplicación automáticamente basada en una plantilla de un escenario específico y, a continuación, ejecútela para entender su comportamiento predeterminado. Experimente con la forma de personalizar una aplicación y, a continuación, guárdela y compártala con otros usuarios.

## <a name="prerequisites"></a>Requisitos previos
* [Suscríbase](signup-for-powerapps.md) a PowerApps, [instálelo](http://aka.ms/powerappsinstall), ábralo e inicie sesión con las mismas credenciales que usó para suscribirse.

    > [!NOTE]
> Para usar esta característica, asegúrese de que utiliza la versión 2.0.510, o cualquier versión posterior. Para identificar la versión, abra el menú **Archivo** (en el borde izquierdo), haga clic o pulse en **Cuenta** y, después, mire en **Información del producto**.

* Una cuenta de almacenamiento en la nube como DropBox, OneDrive o Google Drive.

## <a name="create-an-app"></a>Crear una aplicación
1. Desde PowerApps Studio para Windows o PowerApps Studio para web, haga clic o pulse en **Nuevo** (cerca del borde izquierdo de la pantalla).

    ![Opción Nuevo en el menú Archivo](./media/get-started-test-drive/file-new.png)
2. En el icono **Plantillas de aplicación**, pulse o haga clic en **Diseño de teléfono**.

   > [!NOTE]
> También se pueden crear aplicaciones desde una plantilla con un diseño para tableta, pero este tutorial se centra en la opción de teléfono.

   ![Opción para crear una aplicación para una tableta o un teléfono](./media/get-started-test-drive/phone-app.png)

   Aparece una lista de plantillas.

3. Si no tiene una conexión a una cuenta de almacenamiento en la nube:

   1. En la parte inferior de la pantalla, pulse o haga clic en **Elegir**.

       ![Opción para crear la conexión dentro de la vista de plantilla](./media/get-started-test-drive/add-connection.png)
   2. Pulse o haga clic en la cuenta que desea usar.

       ![Conexión de la lista para crear una aplicación a partir de una plantilla](./media/get-started-test-drive/store-data.png)
   3. Especifique sus credenciales y pulse o haga clic en **Usar** para conceder acceso.

       La conexión aparece en la parte inferior de la pantalla.

4. En la lista de plantillas, haga clic o pulse en una plantilla y, a continuación, haga clic o pulse en **Usar** (cerca de la esquina inferior derecha).

    ![Abrir una plantilla de PowerApps](./media/get-started-test-drive/open-template.png)

    Los datos de ejemplo se copian en su cuenta de almacenamiento en la nube, se crea la aplicación y aparece la página principal.

## <a name="run-the-app"></a>Ejecutar la aplicación
Una aplicación creada a partir de una plantilla se abre en el área de trabajo predeterminada en la que pasará la mayor parte del tiempo personalizándola. Antes de realizar cualquier cambio en la aplicación, siga los pasos de esta sección para explorar cómo funciona la aplicación en el modo **vista previa**.

> [!TIP]
> Diseñe y desarrolle las aplicaciones en el área de trabajo predeterminado, pero pruébela en modo **Vista previa** antes de compartirlas con otras personas.

1. Si no ha utilizado PowerApps antes, realice un paseo introductorio (o haga clic o pulse en **Omitir**).

    ![Pantalla inicial del paseo introductorio](./media/get-started-test-drive/quick-tour.png)

    Siempre puede realizar el paseo más tarde haciendo clic o pulsando en el icono del signo de interrogación situado cerca de la esquina superior derecha de la pantalla y, a continuación, haciendo clic o pulsando en **Take the intro tour** (Realizar paseo introductorio).

2. En la barra de navegación izquierda, haga clic o pulse la pantalla que esté más cerca de la parte superior.

3. Presione F5 (o haga clic o pulse en la flecha derecha situada en la esquina superior derecha) para abrir la aplicación en modo de **vista previa**.

    ![Botón para abrir el modo de vista previa](./media/get-started-test-drive/open-preview.png)

    La aplicación se rellena por adelantado con datos de ejemplo para demostrar la funcionalidad de la aplicación. Por ejemplo, la aplicación Cost Estimator contiene datos para crear citas y estimar el costo de la instalación de un producto específico para suelos en una sala de un tamaño determinado.

4. Explore el comportamiento predeterminado de la aplicación y compruebe que los datos de su cuenta en la nube reflejan los cambios.

    Por ejemplo, concierte una cita y cree una estimación del costo en la aplicación Cost Estimator.

5. Vuelva al área de trabajo predeterminada seleccionando el icono de la **'X'** situado en la esquina superior derecha (bajo la barra de título de PowerApps).

    ![Botón para cerrar el modo de vista previa](./media/get-started-test-drive/close-preview.png)

## <a name="customize-the-app"></a>Personalizar la aplicación
Puede personalizar esta aplicación, o cualquier otra, de las siguientes maneras (por citar algunas):

* [cambiar el tamaño de pantalla, la orientación o ambas](set-aspect-ratio-portrait-landscape.md)
* [agregar otro origen de datos](add-data-connection.md)
* [agregar una o más pantallas](add-screen-context-variables.md)
* [agregar y configurar más controles](add-configure-controls.md)
* [cambiar el comportamiento de la aplicación](working-with-formulas.md)

## <a name="next-steps"></a>Pasos siguientes
1. Presione Ctrl-S, proporcione un nombre a su aplicación y, a continuación, haga clic o pulse **Guardar** para guardar la aplicación en la nube.
2. [Comparta su aplicación](share-app.md) con otras personas de su organización.

    > [!NOTE]
> Antes de compartir una aplicación, asegúrese de que las personas con quienes la comparta tengan acceso a los datos. Por ejemplo, quiere [compartir una hoja de Excel u otro archivo](share-app-data.md) en una cuenta de almacenamiento en la nube.
