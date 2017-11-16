---
title: "Creación de una relación entre listas de SharePoint a través de un campo de búsqueda | Microsoft Docs"
description: "Cree una relación entre listas de SharePoint mediante el uso de un campo de búsqueda."
services: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/20/2017
ms.author: sharik
ms.openlocfilehash: b589a03f592c02547dce0e74a5c4d3ac74c436a1
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-link-sharepoint-lists-using-lookup-fields"></a>Cómo vincular listas de SharePoint mediante campos de búsqueda
En este tutorial se muestra cómo se pueden conectar dos listas de SharePoint con campos de búsqueda.

## <a name="overview"></a>Información general
SharePoint proporciona dos tipos de campos de búsqueda:

* **Búsqueda**: vincula a otra lista: por ejemplo, una lista *Orders* puede tener un campo de búsqueda que vincule a los clientes de una lista *Customer*;
* **Elección**: al hacer clic o pulsar en el campo, se muestra un pequeño menú de elementos entre los que elegir.

En este tutorial, compilará una aplicación que usa estos tipos de campos de búsqueda.

### <a name="what-do-you-use-lookup-fields-for"></a>¿Para qué se usan los campos de búsqueda?
Los datos de una empresa son numerosos y complejos. Los datos de una lista de SharePoint a menudo están relacionados con los de otra lista. Los campos de búsqueda son la principal forma de unir dichos datos empresariales.

Por ejemplo, podría tener una lista **Orders** que tenga un campo de búsqueda que vincule a una lista **Customers** para mostrar el cliente que realizó el pedido. El campo de búsqueda de la lista **Orders** también permite obtener otros datos de la lista **Customers**. También podría usar un campo de búsqueda para conectar la lista **Orders** a una lista **Product** y obtener la información necesaria sobre el producto pedido, como imágenes del producto, especificaciones, detalles del fabricante, etc.

### <a name="what-are-choice-fields-used-for"></a>¿Para qué se usan los campos Elección?
Los campos **Elección** se usan para listas muy cortas, pero en lugar de crear realmente una lista independiente, se incluyen los valores de la lista en un pequeño menú, que aparece al pulsar o hacer clic en el campo **Elección**, en el que debe seleccionar uno de los valores.

Algunos ejemplos son datos como el código de estado de cliente, la disponibilidad de los productos, los códigos de los estados y básicamente cualquier lista fija que sea relativamente corta. De hecho, estos datos se podrían implementar como listas independientes y, luego, utilizar un campo **Búsqueda** para vincularlos, pero normalmente resulta más fácil y rápido implementarlos como campos **Elección**.

## <a name="create-the-lists-in-sharepoint"></a>Crear las listas en SharePoint
En este tutorial, se vinculan dos listas personalizadas de SharePoint, por ejemplo, **Assets** y **RepairShop**. La lista **Assets** se usa para realizar un seguimiento de los equipos de hardware en un equipo. Puesto que el hardware se estropea con el tiempo, usamos la lista **RepairShop** para realizar un seguimiento de las tiendas locales que pueden arreglarlo.

### <a name="the-lookup-fields-used-in-this-example"></a>Los campos de búsqueda usados en este ejemplo
La lista **RepairShop** usa el campo *ContactEmail* para identificar la tienda. Esta lista se define en primer lugar para que cada fila de la lista **Assets** apunte a un algún elemento.

La lista **Assets** tiene dos campos de búsqueda:

* uno denominado *RepairShop*, del tipo **Búsqueda**, que usa direcciones de correo electrónico para apuntar a las entradas de la lista **RepairShop**;
* uno denominado *AssetType*, del tipo **Elección**, en el que se enumeran los tipos de hardware que podría ser este recurso.

Lo más probable es que defina campos adicionales en función de la información de la que necesite realizar un seguimiento.

### <a name="define-the-repairshop-list-and-add-data"></a>Definir la lista RepairShop y agregar datos
Esto se hace en primer lugar, para que cuando agregue datos a la lista **Assets**, haya entradas de **RepairShop** disponibles para su elección en el campo de búsqueda *Assets.RepairShop*.

1. En el sitio de SharePoint, cree una nueva lista **RepairShop**.
   
    ![](./media/sharepoint-lookup-fields/new-list.png)
2. Agregue un campo *ContactEmail* del tipo **Una línea de texto**.
   
    ![](./media/sharepoint-lookup-fields/add-email-field.png)
3. Agregue los demás campos que necesite.
4. Pulse o haga clic en **+ Nuevo** para escribir datos de ejemplo en la lista; al menos tres filas con distintos valores de *ContactEmail*. Cuando resulte necesario reparar un recurso, elija uno de esos valores.
   
    ![](./media/sharepoint-lookup-fields/add-repair-shops.png)

### <a name="define-the-assets-list"></a>Definir la lista Assets
1. En el sitio de SharePoint, cree una nueva lista **Assets**.
2. Pulse o haga clic el signo más y elija **Más**.
   
    ![](./media/sharepoint-lookup-fields/choose-more-type.png)
3. Agregue un campo *AssetType* del tipo **Elección** y, en el cuadro de texto **Escriba cada opción en una línea distinta**, escriba los valores que desee que aparezcan en el menú para elegir. Luego pulse o haga clic en **Aceptar**.
   ![](./media/sharepoint-lookup-fields/define-choice-column.png)
4. Empiece a agregar otro campo. Al igual que en el paso 2, pulse o haga clic en el signo más y elija **Más**.
5. Agregue un campo *RepairShop* del tipo **Búsqueda**, elija **RepairShop** en el cuadro de texto **Obtener información de** y elija *ContactEmail* en el cuadro de texto **En esta columna**. Luego pulse o haga clic en **Aceptar**.
   ![](./media/sharepoint-lookup-fields/setup-lookup-column.png)
6. Agregue los campos adicionales que desee.

## <a name="create-an-app-from-the-assets-list"></a>Crear una aplicación de la lista Assets
Puede usar esta aplicación para agregar datos a la lista **Assets**.

1. Abra PowerApps Studio. Si no está familiarizado con PowerApps, [regístrese gratuitamente](https://powerapps.microsoft.com) con la dirección de correo electrónico de su organización y siga las instrucciones para descargar PowerApps Studio desde la Tienda Windows.
2. En el menú **Archivo** (en el borde izquierdo), pulse o haga clic en **Nuevo** y, luego, pulse o haga clic en **SharePoint**.

![](./media/sharepoint-lookup-fields/create-app.png)

1. Elija su sitio de SharePoint en la lista **Sitios recientes** o escriba la URL de su sitio directamente en el cuadro de texto. Pulse o haga clic en **Ir**.

![](./media/sharepoint-lookup-fields/choose-sharepoint-site.png)

1. Elija la lista principal desde el sitio de SharePoint; en este ejemplo, **Assets**. Pulse o haga clic en el botón **Conectar**, situado en la esquina inferior derecha.

![](./media/sharepoint-lookup-fields/choose-main-list.png)

## <a name="add-data-to-the-assets-list"></a>Agregar datos a la lista Assets
Ahora puede ejecutar la aplicación y ver el aspecto de la pantalla para ver detalles de los campos de búsqueda.

1. Presione F5 o seleccione la vista previa ( ![](./media/sharepoint-lookup-fields/preview.png) ).
2. Pulse o haga clic en el símbolo **+** situado en la esquina superior derecha para agregar una entrada.
3. Escriba un **Título** para este recurso.
4. Pulse o haga clic en la flecha desplegable de **AssetType**. Los valores mostrados son aquellos que especificó cuando creó este campo. Elija una de las entradas.
   
    ![](./media/sharepoint-lookup-fields/fill-asset-type-3.png)
5. Pulse o haga clic en la flecha desplegable de **RepairShop**. Elija una de las entradas.
   
    ![](./media/sharepoint-lookup-fields/fill-repair-shop-3.png)
6. En la esquina superior derecha, pulse o haga clic en la marca de verificación para guardar la nueva entrada.
7. (Opcional) Repita este procedimiento para agregar tantos elementos a la lista como desee.
8. Presione Esc para volver al área de trabajo predeterminada.

## <a name="for-more-information"></a>Más información
* [Introducing support for lookups and a new sample app](https://powerapps.microsoft.com/blog/support-for-lookups/) (Presentación del soporte técnico para búsquedas y una nueva aplicación de ejemplo)
* [Performance, Refresh button, ForAll, and multiple field lookups](https://powerapps.microsoft.com/blog/performance-refresh-forall-multiple-field-lookups-531/) (Rendimiento, botón Actualizar, ForAll y búsquedas en varios campos)
* [Generate an app by using a Common Data Service database](data-platform-create-app.md) (Generar una aplicación mediante una base de datos de Common Data Service)
* [Create an app from scratch using a Common Data Service database](data-platform-create-app-scratch.md) (Crear una aplicación desde cero mediante una base de datos de Common Data Service)

