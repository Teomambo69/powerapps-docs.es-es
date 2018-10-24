---
title: Eliminación de una aplicación controlada por modelos | Microsoft Docs
description: Obtenga información sobre cómo eliminar o quitar una aplicación controlada por modelos desde el entorno de PowerApps.
keywords: ''
ms.date: 05/31/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 9
topic-status: Drafting
ms.openlocfilehash: 9512c0b1c13f408b92c0c18f08946ea9afa1e62b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39710895"
---
# <a name="delete-a-model-driven-app"></a>Eliminación de una aplicación controlada por modelos

Elimine o quite las aplicaciones que están obsoletas en su entorno.

1. Inicie sesión en [PowerApps](https://web.powerapps.com/).
2. Abra el [Explorador de soluciones](advanced-navigation.md#solution-explorer). 
3. En la ventana de la solución, en **Componentes**, seleccione **Aplicaciones**.
4. Seleccione la aplicación que desea eliminar y, a continuación, elija **Eliminar** en la barra de comandos.

    ![Eliminar una aplicación](media/app-module-solution-window.png "Eliminar una aplicación")

5. En el mensaje de confirmación que aparece, seleccione **Eliminar**.

   La aplicación se elimina de su entorno.
  
Si el componente tiene dependencias (por ejemplo, relaciones), debe quitarlas antes de poder eliminar la aplicación. Para ver las dependencias de una aplicación, seleccione la aplicación y, a continuación, seleccione **Mostrar dependencias** en la barra de comandos.

> [!NOTE]
> Cuando se elimina la aplicación, se recomienda que elimine su mapa de sitio asociados. Si no se elimina el mapa del sitio asociado, el Diseñador del mapa del sitio muestra un error la primera vez que intente crear otra aplicación con el mismo nombre. Sin embargo, puede omitir el error y no volverá a mostrarse al intentar volver a crear la aplicación.


