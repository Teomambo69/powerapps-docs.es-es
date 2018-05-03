---
title: Guía de inicio rápido para crear su primera aplicación controlada por modelos desde cero con PowerApps | Microsoft Docs
description: Aprenda a crear una sencilla aplicación controlada por modelos.
documentationcenter: ''
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 04/18/2018
ms.author: matp
ms.openlocfilehash: 3a9696a025608de3c142277da4059e7e8c5ec5ad
ms.sourcegitcommit: 45fac73f04aa03b5796ae6833d777f4757e67945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="quickstart-build-your-first-model-driven-app-from-scratch"></a>Guía de inicio rápido: Creación de su primera aplicación controlada por modelos desde cero
El diseño de aplicaciones controladas por modelos es un enfoque de componentes centrado en el desarrollo de aplicaciones. En esta guía de inicio rápido, va a simplificar la creación de una aplicación controlada por modelos mediante una de las entidades estándar disponibles en el entorno [!INCLUDE [powerapps](../../includes/powerapps.md)]. 

## <a name="sign-in-to-powerapps"></a>Inicio de sesión en PowerApps
Inicie sesión en [PowerApps](https://web.powerapps.microsoft.com/). Si todavía no tiene una cuenta de [!INCLUDE [powerapps](../../includes/powerapps.md)], haga clic en el vínculo **Inicio gratuito**. 

## <a name="create-your-model-driven-app"></a>Creación de la aplicación controlada por modelos

1.  Seleccione el entorno que desee, o bien, vaya al [Centro de administración de PowerApps](https://admin.powerapps.microsoft.com/) para crear uno.
2.  En el panel de navegación de la izquierda, seleccione **Basado en modelos**. 

    ![Controlado por modelos](media/build-first-model-driven-app/choose-design-mode.png)

3. En el panel izquierdo, seleccione **Aplicaciones** y, después, seleccione **Crear una aplicación**.

4.  En la página **Crear una aplicación**, escriba la siguiente información y, después, seleccione **Listo**: 
  - **Nombre**: escriba un nombre para la aplicación, como *Myfirstapp*. 
  - **Descripción**: escriba una descripción breve de lo que la aplicación es o hace, como *Esta es mi primera aplicación*.
Para más información sobre las propiedades de la aplicación adicionales, consulte [Crear una aplicación](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app#create-an-app).
 
    ![Crear nueva-aplicación](media/build-first-model-driven-app/create-new-app.png)

## <a name="add-components-to-your-app"></a>Agregar componentes a la aplicación
Desde el diseñador de aplicaciones, va a agregar componentes a la aplicación.
1.  Seleccione la flecha **Abrir el Diseñador del mapa del sitio** para abrir el diseñador. 

    ![Crear mapa del sitio](media/build-first-model-driven-app/new-sitemap.png)

2.  En el diseñador del mapa del sitio, seleccione **Nueva subárea**, en el panel derecho seleccione la pestaña **Propiedades** y, finalmente, seleccione las siguientes propiedades.
  - **Tipo**: entidad
  - **Entidad**: cuenta

    ![Agregar componentes al mapa del sitio](media/build-first-model-driven-app/sitemap.png)

3.  Haga clic en **Guardar y cerrar**.
4.  En el lienzo del diseñador de aplicaciones, seleccione **Formularios** y, después, en el panel derecho en el grupo **Formularios principales**, seleccione el formulario **Cuenta**.

    ![Formulario principal de la cuenta](media/build-first-model-driven-app/main-form.png)

5.  En el lienzo del diseñador de aplicaciones, seleccione **Vistas** y, después, seleccione las vistas **Cuentas activas** , **Todas las cuentas** y **Mis cuentas activas**.

    ![Vistas de cuentas](media/build-first-model-driven-app/views.png)

6. En el lienzo del diseñador de aplicaciones, seleccione **Gráficos** y, después, seleccione el gráfico **Cuentas por sector**.
7. En la barra de herramientas del diseñador de aplicaciones, haga clic en **Guardar**.

    ![Guardar en la barra de herramientas del diseñador de aplicaciones](media/build-first-model-driven-app/app-designer-toolbar.png)
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>Publicar la aplicación
En la barra de herramientas del diseñador de aplicaciones, seleccione **Publicar**.

Después de publicar la aplicación, ya está preparada para que la ejecute o la comparta con otros.

![Aplicación de entidad de cuenta sencilla](media/build-first-model-driven-app/accounts-quickstart-app.png)

## <a name="next-steps"></a>Pasos siguientes
En esta guía de inicio rápido, ha creado una aplicación sencilla controlada por modelos. Para ver el aspecto de la aplicación cuando la ejecuta, consulte [Inicio rápido: Ejecución de una aplicación controlada por modelos en un dispositivo móvil](../../user/run-app-client-model-driven.md).
Para obtener información sobre cómo compartir la aplicación, siga el tutorial sobre cómo compartir una aplicación controlada por modelos [Compartir una aplicación controlada por modelos](share-model-driven-app.md).
