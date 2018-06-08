---
title: Edición de una aplicación | Microsoft Docs
description: Instrucciones paso a paso para editar aplicaciones y escenarios de bloqueo de sesión.
documentationcenter: na
author: karthik-1
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 05/19/2017
ms.author: sharik
ms.openlocfilehash: d6c857a75a21123cdd0e826682fc595a503d67fd
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "32328798"
---
# <a name="edit-an-app-in-powerapps"></a>Edición de una aplicación en PowerApps
Edite cualquier aplicación que haya creado, que posea, o para la que tiene permisos **Can edit** (Puede editar). Puede modificar una aplicación en PowerApps Studio. Si intenta editar una aplicación que está abierta para su edición en otra parte, un mensaje le indicará si es usted quien ya la tiene abierta o si es otro usuario.

## <a name="verify-your-permissions"></a>Comprobación de los permisos
1. Inicie sesión en [PowerApps](https://web.powerapps.com) y haga clic o pulse **Aplicaciones** en el menú **Archivo** (en el borde izquierdo).
   
    ![Opción Aplicaciones en el menú Archivo](./media/edit-app/file-apps.png)

2. En el selector de categorías de aplicación, pulse o haga clic en **Aplicaciones que puedo editar**.

    Puede editar cualquier aplicación de la lista que aparece. También puede buscar una aplicación escribiendo uno o más caracteres en el cuadro de búsqueda cerca de la esquina superior derecha.

    > [!NOTE]
    > Si aún así no ve la aplicación que desea editar, compruebe que ha seleccionado el entorno correcto cerca de la esquina superior derecha.
   
    ![Lista de entornos](./media/edit-app/environment-list.png)

1. Haga clic o pulse en los puntos suspensivos (...) de la aplicación que quiera modificar y, después, pulse o haga clic en **Editar**.

## <a name="collaborate-on-an-app"></a>Colaboración en una aplicación
Cualquier persona que tenga un permiso **Can edit** (Puede editar) para una aplicación puede modificarla, pero no puede haber más de una persona a la vez editando la aplicación. Si se intenta modificar una aplicación que alguien ya está editando, aparece el mensaje a continuación. No puede continuar hasta que la otra persona cierre la aplicación (o se agote el tiempo de espera de su sesión).

![](./media/edit-app/applock-otheruser.png)

Este mensaje también aparece si abre una aplicación para su edición y luego intenta abrirla en otro dispositivo o en otra ventana del explorador. Puede invalidar la sesión anterior, pero podría perder los cambios que no haya guardado.

![](./media/edit-app/applock-selfuser.png)

## <a name="next-steps"></a>Pasos siguientes
Más información sobre cómo agregar una [pantalla](add-screen-context-variables.md), un [control](add-configure-controls.md) o una [conexión de datos](add-data-connection.md).

