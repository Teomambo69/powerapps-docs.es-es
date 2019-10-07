---
title: Edición de una aplicación de lienzo | Microsoft Docs
description: Instrucciones paso a paso para editar aplicaciones de lienzo y escenarios de bloqueo de sesión en PowerApps.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/19/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ecbe46f28d7be215a5ec9d8efecebde5dc4656d4
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993016"
---
# <a name="edit-a-canvas-app-in-powerapps"></a>Edición de una aplicación de lienzo en PowerApps
Edite cualquier aplicación que haya compilado, de la que sea propietario o en la que tenga permisos **Puede editar**. Puede modificar una aplicación en PowerApps Studio. Si intenta editar una aplicación que está abierta para su edición en otra parte, un mensaje le indicará si es usted quien ya la tiene abierta o si es otro usuario.

## <a name="verify-your-permissions"></a>Comprobación de los permisos
1. Inicie sesión en [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y haga clic o pulse **Aplicaciones** en el menú **Archivo** (en el borde izquierdo).
   
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

