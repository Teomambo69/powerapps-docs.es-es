---
title: Crear una aplicación de lienzo desde Common Data Service | Microsoft Docs
description: En Power Apps, cree automáticamente una aplicación de lienzo para administrar datos en Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c62a690073e591c693d914000511b586dfc97b69
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959389"
---
# <a name="create-a-canvas-app-from-common-data-service-in-power-apps"></a>Creación de una aplicación de lienzo desde Common Data Service en Power apps

En Power Apps, cree una aplicación de lienzo basada en una lista de cuentas de ejemplo en [Common Data Service](../common-data-service/data-platform-intro.md). En esta aplicación, puede examinar todas las cuentas, mostrar detalles de una sola cuenta y crear, actualizar o eliminar una cuenta.

Si no se ha registrado en Power Apps, [Regístrese gratuitamente](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para seguir esta guía de inicio rápido, debe tener asignado el rol de seguridad [creador de entorno](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles) y debe [cambiar a un entorno](working-with-environments.md) en el que se haya creado una base de datos de Common Data Service, contenga datos y permita actualizaciones. Si no existe ningún entorno de este tipo y tiene privilegios administrativos, puede [crear un entorno](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment) que cumpla este requisito.

## <a name="create-an-app"></a>Crear una aplicación

1. Inicie sesión en [Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y, si es necesario, cambie los entornos como se especificó anteriormente en este tema.

1. En **Cree su propia aplicación**, mantenga el puntero sobre **Iniciar a partir de datos** y seleccione **Crear esta aplicación**.

    ![Opción para crear una aplicación](./media/data-platform-create-app/start-from-data.png)

1. En el icono **Common Data Service**, seleccione **Diseño de teléfono**.

    ![Icono de conexión](./media/data-platform-create-app/connection-tile.png)

1. En **Elegir una tabla**, seleccione **Cuentas** y, después, seleccione **Conectar**.

1. Si aparece el cuadro de diálogo **Bienvenido a Power apps Studio** , seleccione **omitir**.

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
En esta guía de inicio rápido, ha creado una aplicación para administrar datos de ejemplo sobre cuentas en Common Data Service. En el paso siguiente, personalizará la galería y otros elementos de la pantalla de exploración predeterminada para que se ajuste mejor a sus necesidades.

> [!div class="nextstepaction"]
> [Personalización de una galería](customize-layout-sharepoint.md)
