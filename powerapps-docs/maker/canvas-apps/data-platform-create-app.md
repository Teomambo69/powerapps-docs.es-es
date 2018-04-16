---
title: Generación de una aplicación en PowerApps para Common Data Service for Apps (inicio rápido) | Microsoft Docs
description: Genere automáticamente una aplicación en PowerApps para administrar datos en Common Data Service for Apps.
services: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/10/2018
ms.author: anneta
ms.openlocfilehash: 78429fc5d0220b5cc9e8dc726583c2e9e543f85a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-for-generating-an-app-in-powerapps-for-the-common-data-service-for-apps"></a>Inicio rápido para generar una aplicación en PowerApps para Common Data Service for Apps

En este tutorial, usará PowerApps para generar automáticamente la primera aplicación en función de una lista de cuentas de ejemplo en [Common Data Service for Apps](../common-data-service/data-platform-intro.md). En esta aplicación, puede examinar todas las cuentas, mostrar detalles de una sola cuenta y crear, actualizar o eliminar una cuenta.

Para seguir este tutorial rápido, debe cambiar a un [entorno](working-with-environments.md) en el que se haya creado una base de datos en Common Data Service y contenga datos. Si no existe ningún entorno de este tipo y tiene privilegios administrativos, puede [crear un entorno](../../administrator/environments-administration.md#create-an-environment) que cumpla este requisito.

Si no tiene una licencia para PowerApps, puede [registrarse gratuitamente](../signup-for-powerapps.md).

## <a name="generate-an-app"></a>Generar una aplicación
1. Inicie sesión en [PowerApps](https://web.powerapps.com).

    ![Página principal de PowerApps](./media/data-platform-create-app/sign-in.png)

1. En **Make apps like these** (Crear aplicaciones como estas), mantenga el puntero sobre **Start from data** (Iniciar desde datos) y, después, haga clic en **Crear esta aplicación**.

    ![Opción para crear una aplicación](./media/data-platform-create-app/make-this-app.png)

1. En **Comenzar con los datos**, haga clic en la flecha que apunta a la derecha.

    ![Icono de flecha](./media/data-platform-create-app/right-arrow.png)

1. En **Conexiones**, seleccione la conexión a Common Data Service.

1. Escriba **Cuentas** en el cuadro de búsqueda (junto al borde derecho), haga clic en **Cuentas** en **Choose a table** (Elegir una tabla) y, después, haga clic en **Conectar**.

    ![Seleccionar una entidad](./media/data-platform-create-app/select-entity.png)

Después de unos minutos, la aplicación se abre en la pantalla de exploración, en la que se muestra una lista de las cuentas. Cerca de la parte superior de la pantalla, en una barra de título se muestran iconos para actualizar la lista, ordenarla y crear una cuenta. Bajo la barra de título, un cuadro de búsqueda proporciona la opción de filtrar la lista según el texto que se escriba o pegue. 

De forma predeterminada, la lista muestra una imagen, una dirección de correo electrónico, una ciudad y un identificador para esa cuenta. Pero la lista se puede personalizar, lo que se denomina una galería, para mostrar otros tipos de datos.

![Pantalla de exploración](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>Guardar la aplicación
Probablemente le interesará realizar más cambios antes de usar esta aplicación o compartirla con otros usuarios. Como procedimiento recomendado, guarde el trabajo realizado hasta el momento antes de continuar.

1. Cerca de la esquina superior izquierda, pulse o haga clic en la pestaña **Archivo**.

1. En la página **Configuración de la aplicación**, establezca el nombre de la aplicación en **AppGen**, cambie el color de fondo a rojo profundo y el icono a una marca de verificación.

    ![Página de configuración de la aplicación](./media/data-platform-create-app/app-settings.png)

1. Cerca del borde izquierdo, haga clic o pulse en **Guardar**.

## <a name="next-steps"></a>Pasos siguientes
En este tutorial rápido, ha creado una aplicación para administrar datos de ejemplo sobre las cuentas en Common Data Service for Apps. En el paso siguiente, personalizará la pantalla de exploración predeterminada para que se ajuste mejor a sus necesidades.

> [!div class="nextstepaction"]
> [Personalizar una pantalla de exploración predeterminada](customize-layout-sharepoint.md).
