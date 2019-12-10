---
title: Introducción a la conexión de Dynamics 365 | Microsoft Docs
description: Crear una aplicación para administrar datos de Dynamics 365
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: matp
ms.reviewer: ''
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 37818e3c7cca175218826c1707ab83cd5c193ae7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723926"
ms.PowerAppsDecimalTransform: true
---
# <a name="connect-to-dynamics-365-from-power-apps"></a>Conexión a Dynamics 365 desde Power apps
Power apps le permite generar, personalizar, compartir y ejecutar rápidamente aplicaciones móviles con poco o ningún código. Mediante el conector de Dynamics 365, puede crear útiles aplicaciones móviles para compartir con su organización en tan solo unos minutos.

Si sigue los pasos descritos en este tema, creará una aplicación en la que los usuarios podrán examinar, agregar, eliminar y realizar actualizaciones en los contactos de Dynamics 365. Los usuarios pueden ejecutar la aplicación [en un explorador](../../../user/run-app-browser.md) o [en un dispositivo móvil](../../../user/run-app-client.md), como un teléfono.

## <a name="prerequisite"></a>Requisito previo
Para seguir este tutorial, necesita una cuenta de Microsoft Office 365 que incluye una suscripción a Dynamics 365.

## <a name="create-a-connection"></a>Crear una conexión
1. [Inicie sesión en Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. En el panel de navegación izquierdo, haga clic en **Conexiones**.
   
    ![Opción Conexión en el menú Archivo](./media/connection-dynamics-crmonline/file-connections.png)
3. Cerca de la esquina superior derecha, haga clic en **Nueva conexión**.
   
    ![Nueva conexión](./media/connection-dynamics-crmonline/new-connection.png)
4. En la lista de conexiones, haga clic en **Dynamics 365**.
   
    ![Opción Conexión en el menú Archivo](./media/connection-dynamics-crmonline/connection-d365.png)
5. En el cuadro de diálogo, haga clic en **Crear**.
   
    ![Crear conexión](./media/connection-dynamics-crmonline/create-connection.png)
6. En el cuadro de diálogo **Iniciar sesión en la cuenta**, indique sus credenciales para el inquilino Dynamics 365 (en línea).
   
    Se crea una conexión.

## <a name="generate-an-app-automatically"></a>Generar una aplicación automáticamente
1. [Inicie sesión en Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, luego, haga clic en **nueva aplicación** cerca de la esquina inferior izquierda.
   
    ![Nueva aplicación](./media/connection-dynamics-crmonline/new-app.png)
2. En **Comenzar con los datos**, haga clic en **Diseño de teléfono** en el icono **Dynamics 365**.
   
    ![Power apps seleccione conector Dynamics 365](./media/connection-dynamics-crmonline/phonelayout.png)
3. En **Conexiones**, seleccione la conexión que desee y, después, elija un conjunto de datos, que se corresponde a la instancia de Dynamics 365 que va a administrar en la aplicación.
4. En **Elegir una tabla**, haga clic en **Contactos** y, después, haga clic en **Conectar**.
5. En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.
   
    ![Alternancia de las vistas](./media/connection-dynamics-crmonline/toggle-view.png)

Power apps genera una aplicación de tres pantallas basada en registros de contacto.

* **ExaminarPantalla1**. Esta pantalla aparece de forma predeterminada cuando los usuarios abren la aplicación. En la barra de navegación izquierda, se muestra una vista en miniatura de esta pantalla sobre las otras dos pantallas.
* **PantallaDetalles1**. Esta pantalla aparece cuando los usuarios hacen clic en un elemento de **ExaminarPantalla1**.  En la barra de navegación izquierda, se muestra una vista en miniatura de **PantallaDetalles1** sobre las otras dos pantallas.
* **EditarPantalla1**. Esta pantalla aparece cuando los usuarios hacen clic en el icono de edición de un elemento en **PantallaDetalles1**. En la barra de navegación izquierda, se muestra una vista en miniatura de **EditarPantalla1** sobre las otras dos pantallas.

Puede ejecutar la aplicación en su estado inicial, pero podemos hacerla más útil si perfeccionamos la información en cada pantalla.

## <a name="customize-browsescreen1"></a>Personalizar ExaminarPantalla1
En este procedimiento, va a configurar **ExaminarPantalla1** para mostrar los nombres y apellidos de cada contacto. Los datos se ordenarán alfabéticamente por apellido e incluyen imágenes en una cuadrícula de dos columnas.

1. En **ExaminarPantalla1**, seleccione la galería haciendo clic en cualquier registro, excepto en el primero.
   
    ![Seleccionar diseño](./media/connection-dynamics-crmonline/select-gallery.png)
2. En el panel de la derecha, pulse o haga clic en la pestaña **Datos**.
3. En la lista de diseños, pulse o haga clic en el diseño que muestra imágenes y texto en una cuadrícula de dos columnas.
   
    Puede que necesite desplazarse hacia abajo para mostrar esta opción.
   
    ![Seleccionar diseño](./media/connection-dynamics-crmonline/select-layout.png)
4. Copie esta fórmula y, después, con la galería aún seleccionada, pegue la fórmula en la barra de fórmulas (a la derecha del botón **fx**):
   
    `SortByColumns(Search(Filter(Contacts;statuscode=1); TextSearchBox1.Text; "lastname"); "lastname"; If(SortDescending1; Descending; Ascending))`
5. En el panel derecho, establezca la lista desplegable superior en **firstname** y la lista desplegable central en **lastname**.
   
    ![Seleccionar Cuerpo1](./media/connection-dynamics-crmonline/firstname-lastname.png)
6. (opcional) En el menú **Archivo**, haga clic en **Guardar como**, escriba un nombre para la aplicación y haga clic en **Guardar**.
   
    De forma predeterminada, la aplicación se guardará en la nube. Haga clic en **Este equipo** para guardar la aplicación localmente.

## <a name="customize-detailsscreen1-and-editscreen1"></a>Personalizar PantallaDetalles1 y EditarPantalla1
1. En la barra de navegación izquierda, haga clic en la miniatura central para seleccionar **PantallaDetalles1**.
2. En **PantallaDetalles1**, haga clic en cualquier lugar debajo de la barra de título para mostrar las opciones de personalización del panel derecho.
   
    ![Mostrar personalización de formularios](./media/connection-dynamics-crmonline/show-customization.png)
3. En el panel derecho, haga clic en el icono de ojo de cada campo para mostrarlo.
   
    ![Ocultar campos](./media/connection-dynamics-crmonline/hide-field.png)
4. Haga clic en cualquier lugar bajo la barra de título para seleccionar **Formulario1**.
   
    ![Seleccionar Formulario1](./media/connection-dynamics-crmonline/select-form1.png)
5. En el panel derecho, haga clic en el icono de ojo para cada uno de estos campos, por lo que la pantalla mostrará una imagen (si la tabla contiene una) y otros cuatro campos para cada contacto:
   
   * **entityimage**
   * **firstname**
   * **lastname**
   * **mobilephone**
   * **emailaddress1**
     
     El panel derecho debe ser similar a este gráfico:
     
     ![Seleccionar Formulario1](./media/connection-dynamics-crmonline/show-fields.png)
6. Seleccione **EditarPantalla1** haciendo clic en la miniatura inferior de la barra de navegación izquierda.
7. Repita los pasos de este procedimiento para personalizar **EditarPantalla1** del mismo modo que en **PantallaDetalles1**.
8. (opcional) Guarde la aplicación.

## <a name="next-steps"></a>Pasos siguientes
* Pruebe la aplicación en modo de vista previa haciendo clic en **ExaminarPantalla1** en la barra de navegación izquierda y, después, presione F5 o haga clic ![Modo de vista previa](./media/connection-dynamics-crmonline/runpowerapp.png) cerca de la esquina superior derecha.
* [Comparta la aplicación](../share-app.md).
* [Agregue un segundo origen de datos](../add-data-connection.md).

