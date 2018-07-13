---
title: 'Inicio rápido: generación de una aplicación a partir de Common Data Service for Apps | Microsoft Docs'
description: En este inicio rápido, genera automáticamente una aplicación en PowerApps para administrar datos en Common Data Service for Apps
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: anneta
ms.openlocfilehash: 50913e593cf279d0d1870cbe88fa1a3703059811
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39016039"
---
# <a name="quickstart-generate-an-app-from-common-data-service-for-apps-in-powerapps"></a>Inicio rápido: generación de una aplicación a partir de Common Data Service for Apps en PowerApps

En este tutorial rápido, usará Microsoft PowerApps para generar automáticamente una aplicación basada en una lista de cuentas de ejemplo en [Common Data Service (CDS) for Apps](../common-data-service/data-platform-intro.md). En esta aplicación, puede examinar todas las cuentas, mostrar detalles de una sola cuenta y crear, actualizar o eliminar una cuenta.

Si no está registrado para PowerApps, [regístrese gratuitamente](https://web.powerapps.com) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos
Para seguir este tutorial rápido, debe [cambiar a un entorno](working-with-environments.md) en el que se haya creado una base de datos en CDS for Apps que contenga datos y que permita actualizaciones. Si no existe ningún entorno de este tipo y tiene privilegios administrativos, puede [crear un entorno](../../administrator/environments-administration.md#create-an-environment) que cumpla este requisito.

## <a name="generate-an-app"></a>Generar una aplicación
1. Inicie sesión en [PowerApps](https://web.powerapps.com) y, si es necesario, cambie los entornos como se especificó anteriormente en este mismo tema.

    ![Página principal de PowerApps](./media/data-platform-create-app/sign-in.png)

1. En **Make apps like these** (Crear aplicaciones como estas), mantenga el puntero sobre **Start from data** (Iniciar desde datos) y, después, haga clic en **Crear esta aplicación**.

    ![Opción para crear una aplicación](./media/data-platform-create-app/make-this-app.png)

1. En el icono **Common Data Service**, seleccione **Diseño de teléfono**.

    ![Icono de conexión](./media/data-platform-create-app/connection-tile.png)

1. En **Elegir una tabla**, seleccione **Cuentas** y, después, seleccione **Conectar**.

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

La aplicación se abre en la pantalla de exploración, en la que se muestra una lista de las cuentas en un control denominado galería. Cerca de la parte superior de la pantalla, una barra de título muestra los iconos para actualizar los datos en la galería, ordenarlos alfabéticamente y agregar datos a la galería. Bajo la barra de título, un cuadro de búsqueda proporciona la opción de filtrar los datos en la galería según el texto que se escriba o pegue. 

De forma predeterminada, la galería muestra una dirección de correo electrónico, una ciudad y un nombre de cuenta. Como verá en los [siguientes pasos](data-platform-create-app.md#next-steps), puede personalizar la galería para cambiar la forma en que se muestran los datos e incluso mostrar otros tipos de datos.

![Pantalla de exploración](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>Guardar la aplicación
Probablemente le interesará realizar más cambios antes de usar esta aplicación o compartirla con otros usuarios. Como procedimiento recomendado, guarde el trabajo realizado hasta el momento antes de continuar.

1. Cerca de la esquina superior izquierda, seleccione la pestaña **Archivo**.

1. En la página **Configuración de la aplicación**, establezca el nombre de la aplicación en **AppGen**, cambie el color de fondo a rojo profundo y el icono a una marca de verificación.

    ![Página de configuración de la aplicación](./media/data-platform-create-app/app-settings.png)

1. Cerca del borde izquierdo, seleccione **Guardar** y, a continuación, en la esquina inferior izquierda, seleccione **Guardar**.

## <a name="next-steps"></a>Pasos siguientes
En este tutorial rápido, ha creado una aplicación para administrar datos de ejemplo sobre las cuentas en CDS for Apps. En el paso siguiente, personalizará la galería y otros elementos de la pantalla de exploración predeterminada para que se ajuste mejor a sus necesidades.

> [!div class="nextstepaction"]
> [Personalización de una galería](customize-layout-sharepoint.md)
