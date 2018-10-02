---
title: Eliminar una aplicación controlada por modelos | MicrosoftDocs
description: Aprenda a eliminar o quitar una aplicación controlada por modelos de su entorno de PowerApps.
keywords: ''
ms.date: 05/31/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="delete-a-model-driven-app"></a>Eliminar una aplicación controlada por modelos

Elimine o quite aplicaciones obsoletas en su entorno.

1. Iniciar sesión en [PowerApps](https://web.powerapps.com/).
2. Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer). 
3. En la ventana de la solución, en **Componentes**, seleccione **Aplicaciones**.
4. Seleccione la aplicación que desea eliminar y, a continuación, seleccione **Eliminar** en la barra de comandos.

    ![Eliminar una aplicación](media/app-module-solution-window.png "Eliminar una aplicación")

5. En el mensaje de confirmación que aparece, seleccione **Eliminar**.

   Se elimina la aplicación de su entorno.
  
Si el componente tiene dependencias (como relaciones), primero debe quitar las dependencias para poder eliminar la aplicación. Para ver las dependencias de una aplicación, seleccione la aplicación y, a continuación, seleccione **Mostrar dependencias** en la barra de comandos.

> [!NOTE]
> Cuando se elimina la aplicación, se recomienda que elimine su mapa de sitio asociado. Si no se elimina el mapa de sitio asociado, el diseñador del mapa de sitio muestra un error la primera vez que intenta crear otra aplicación con el mismo nombre. Sin embargo, puede omitir el error y el error no aparecerá cuando intente volver a crear la aplicación.


