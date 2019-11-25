---
title: Crear la primera aplicación controlada por modelos desde cero con PowerApps | Microsoft Docs
description: Aprenda cómo crear una aplicación controlada por modelos simple
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/05/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9c41feb81fbe90c1ca675105fe898b667f61b2b9
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752615"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>Crear la primera aplicación controlada por modelos desde cero
El diseño de una aplicación controlada por modelos es un enfoque centrado en los componentes para el desarrollo de la aplicación. En este tema, simplificará el modo de crear una aplicación controlada por modelos usando una de las entidades estándar que esté disponible en el entorno de PowerApps.

> [!TIP]
> Para obtener todos sobre las aplicaciones controladas por modelos, empiece aquí: [Comprender los componentes de aplicaciones controladas por modelos](model-driven-app-components.md). 

## <a name="sign-in-to-powerapps"></a>Iniciar sesión en PowerApps
Inicie sesión en [PowerApps](https://make.powerapps.com/). Si aún no tiene una cuenta de [!INCLUDE [powerapps](../../includes/powerapps.md)], seleccione el vínculo **Introducción gratuita**. 

## <a name="create-your-model-driven-app"></a>Cree su aplicación controlada por modelos

1.  Seleccione el entorno que desee o vaya al [Centro de administración de PowerApps](https://admin.powerapps.com/) para crear uno nuevo.

  > [!IMPORTANT]
  > Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).   

2. En la página **Inicio** , seleccione **Empezar en blanco una aplicación basada en modelos**.
<!-- ![Start-from-blank_model](media/build-first-model-driven-app/start-from-blank-model-driven.png) -->

3.  En la página **Crear una nueva aplicación**, especifique los siguientes detalles y, a continuación, seleccione **Hecho**: 
  - **Nombre**: escriba un nombre para la aplicación, como *Mi primera aplicación*. 
  - **Nombre único**: de forma predeterminada, el nombre único usa el nombre que especifica en la casilla **Nombre** sin espacios y precedida por el prefijo del editor y un guión bajo (_). Por ejemplo, *crecf_Myfirstapp*. Más información: [Cambiar el prefijo del editor de soluciones](../common-data-service/change-solution-publisher-prefix.md)
  - **Descripción**: escriba una breve descripción de lo que es o hace la aplicación, como *Esta es mi primera aplicación*.
Para obtener información acerca de las propiedades adicionales de la aplicación, consulte [Crear una aplicación](create-edit-app.md#create-an-app).

    > [!div class="mx-imgBorder"] 
    > ![](media/create-new-app.png "Create a new app") 


## <a name="add-components-to-your-app"></a>Agregar componentes a la aplicación
En el diseñador de aplicaciones puede agregar componentes a la aplicación.
1.  Seleccione la flecha **Abrir el diseñador del mapa del sitio** para abrir el diseñador del mapa del sitio. 

    ![Crear nuevo mapa del sitio](media/build-first-model-driven-app/new-sitemap.png)

2.  En el diseñador del mapa del sitio, seleccione **Nueva subárea**, en el panel derecho seleccione la pestaña **Propiedades** y, a continuación, seleccione las siguientes propiedades.
  - **Tipo**: Entidad
  - **Entidad**: Cuenta

    ![Agregar componentes al mapa del sitio](media/build-first-model-driven-app/sitemap.png)

3.  Seleccione **Guardar y cerrar**.
4.  En el lienzo del diseñador de aplicaciones, seleccione **Formularios** y, en el panel derecho, bajo el grupo **Formularios principales**, seleccione el formulario **Cuenta**.

    ![Formulario Cuenta principal](media/build-first-model-driven-app/main-form.png)

5.  En el lienzo del diseñador de aplicaciones, seleccione **Vistas** y, a continuación, seleccione las vistas **Cuentas activas**, **Todas las cuentas** y **Mis cuentas activas**.

    ![Vistas de Cuenta](media/build-first-model-driven-app/views.png)

6. En el lienzo del diseñador de aplicaciones, seleccione **Gráficos** y seleccione el gráfico **Cuentas por sector**.
7. En la barra de herramientas del diseñador de aplicaciones, seleccione **Guardar**.

    ![Barra de herramientas del diseñador de aplicaciones - Guardar](media/build-first-model-driven-app/app-designer-toolbar.png)
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>Publicar la aplicación
En la barra de herramientas del diseñador de aplicaciones, seleccione **Publicar**.

Después de que publique la aplicación, la podrá ejecutar o compartir con otros.

![Aplicación simple de la entidad Cuenta](media/build-first-model-driven-app/accounts-quickstart-app.png)

## <a name="next-steps"></a>Pasos siguientes
En este tema, creó una aplicación controlada por modelos simple. 
- Para ver cómo quedará la aplicación cuando la ejecute, consulte [Ejecutar una aplicación controlada por modelos en un dispositivo móvil](../../user/run-app-client-model-driven.md).
- Para obtener más información sobre cómo compartir la aplicación, consulte [Compartir una aplicación controlada por modelos](share-model-driven-app.md).
- Para ver una introducción y para obtener todos los detalles sobre cómo crear aplicaciones controladas por modelos, consulte: [Comprender los componentes de aplicaciones controladas por modelos](model-driven-app-components.md).
