---
title: Edición de una aplicación | Microsoft Docs
description: Instrucciones paso a paso para editar aplicaciones y escenarios de bloqueo de sesión.
services: ''
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/19/2017
ms.author: sharik
ms.openlocfilehash: a71aa71ec80a60f2aec4ce179abcade3f9eef964
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="edit-an-app-in-powerapps"></a>Edición de una aplicación en PowerApps
Edite cualquier aplicación que haya creado, que posea, o para la que tiene permisos **Can edit** (Puede editar). Puede editar una aplicación en PowerApps Studio para web o PowerApps Studio para Windows. Si intenta editar una aplicación que está abierta para su edición en otra parte, un mensaje le indicará si es usted quien ya la tiene abierta o si es otro usuario.

## <a name="verify-your-permissions"></a>Comprobación de los permisos
1. Inicie sesión en [PowerApps](https://web.powerapps.com) y haga clic o pulse **Aplicaciones** en el menú **Archivo** (en el borde izquierdo).
   
    ![Opción Aplicaciones en el menú Archivo](./media/edit-app/file-apps.png)
2. Abra el selector de categorías de aplicación y haga clic en o pulse **Aplicaciones que me pertenecen** o **Aplicaciones con las que colaboro**.
   
    ![Selector de categorías de aplicación](./media/edit-app/app-category.png)
   
    Puede editar cualquier aplicación de la lista que aparece. También puede buscar una aplicación escribiendo uno o más caracteres en el cuadro de búsqueda cerca de la esquina superior derecha.
   
    > [!NOTE]
> Si aún así no ve la aplicación que desea editar, compruebe que ha seleccionado el entorno correcto cerca de la esquina superior derecha.
   
    ![Lista de entornos](./media/edit-app/environment-list.png)

## <a name="edit-an-app-in-powerapps-studio-for-web"></a>Edición de un aplicación en PowerApps Studio para web
1. Siga los pasos del procedimiento anterior para encontrar la aplicación que desea editar.
2. Haga clic o pulse el icono de información de la aplicación cerca del borde derecho.
   
    ![Icono de información](./media/edit-app/app-edit.png)
3. Haga clic o pulse el icono **Editar** cerca de la esquina superior derecha y, a continuación, haga clic en o pulse **Modificar en la web**.
   
    ![Icono Editar](./media/edit-app/edit-icon.png)

## <a name="edit-an-app-in-powerapps-studio-for-windows"></a>Edición de un aplicación en PowerApps Studio para Windows
1. Abra PowerApps Studio para Windows.
2. En la página que aparece de forma predeterminada, busque la aplicación que desea editar.
   
    Para encontrar más fácilmente una aplicación, haga clic o pulse el icono de búsqueda cerca de la esquina superior derecha y escriba uno o varios caracteres del nombre de la aplicación. También puede ordenar la lista por nombre, fecha de última modificación o fecha apertura más reciente. Si aún así la aplicación que desea todavía no aparece, confirme que se encuentra en el entorno de PowerApps adecuado, tal como se describe en el primer procedimiento.
   
    ![](./media/edit-app/sort-filter.png)
3. Cerca del borde derecho, pulse o haga clic en el icono del lápiz para la aplicación que desea editar.
   
    Puede editar cualquier aplicación para la que el icono del lápiz es negro, no gris.
   
    ![](./media/edit-app/app-editstudio.png)

## <a name="collaborate-on-an-app"></a>Colaboración en una aplicación
Cualquier persona que tenga un permiso **Can edit** (Puede editar) para una aplicación puede modificarla, pero no puede haber más de una persona a la vez editando la aplicación. Si se intenta modificar una aplicación que alguien ya está editando, aparece el mensaje a continuación. No puede continuar hasta que la otra persona cierre la aplicación (o se agote el tiempo de espera de su sesión).

![](./media/edit-app/applock-otheruser.png)

Este mensaje también aparece si abre una aplicación para su edición y luego intenta abrirla en otro dispositivo o en otra ventana del explorador. Puede invalidar la sesión anterior, pero podría perder los cambios que no haya guardado.

![](./media/edit-app/applock-selfuser.png)

## <a name="next-steps"></a>Pasos siguientes
Más información sobre cómo agregar una [pantalla](add-screen-context-variables.md), un [control](add-configure-controls.md) o una [conexión de datos](add-data-connection.md).

