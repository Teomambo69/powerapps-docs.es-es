---
title: "Visualización de licencias de usuario | Microsoft Docs"
description: Los administradores pueden descargar una lista de licencias de usuario para PowerApps y Microsoft Flow.
services: 
suite: powerapps
documentationcenter: na
author: manasmamsft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/02/2017
ms.author: manasma
ms.openlocfilehash: ba60c227b287532f6abe2e2b2e88f6cbe7dd0cd3
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="identify-powerapps-users-in-your-organization"></a>Identificación de los usuarios de PowerApps de su organización
Si es un administrador global para Office 365 o un administrador de inquilinos de Azure Active Directory, puede descargar una lista de usuarios de su organización que no solo tenga licencia para usar PowerApps, Microsoft Flow o ambos, sino que también hayan tenido acceso a cualquiera de esos productos. La lista contiene el nombre de cada usuario, la dirección de correo electrónico, el tipo de licencia y otra información. Por ejemplo, usuario podría tener:

* una licencia de prueba para PowerApps o Microsoft Flow
* acceso a ambos productos a través de una licencia de Office 365
* acceso a ambos productos a través de una licencia de Dynamics 365
* acceso desde planes de PowerApps y Microsoft Flow

## <a name="download-the-list-of-users"></a>Descarga de la lista de usuarios
1. En el centro de administración PowerApps, pulse o haga clic en **Licencias de usuario**, cerca del borde izquierdo.
   
    **Importante**: Esta opción está disponible para los administradores globales de Office 365 y únicamente para los administradores de inquilinos de Azure Active Directory.
   
    ![Archivo y Compartir](./media/admin-view-user-licenses/leftnav.png)
2. Pulse o haga clic en **Download a list of active user licenses** (Descargar una lista de licencias de usuario activas).
   
    ![Archivo y Compartir](./media/admin-view-user-licenses/download-list.png)
   
    El archivo puede tardar unos minutos en descargarse. Espere unos minutos para que el archivo .csv se descargue y, a continuación, ábralo en Excel.
   
    **Nota**: Si cierra la ventana antes de que el archivo termine la descarga, es posible que deba reiniciar el proceso.

En este ejemplo se muestran dos usuarios que tienen licencias de PowerApps y Microsoft Flow por distintos medios. Jane Doe tiene acceso a través de una suscripción a Office 365 y John Doe tiene una licencia de prueba para cada producto.

![Archivo y Compartir](./media/admin-view-user-licenses/table2.png)

Esta lista no contiene usuarios con licencias para PowerApps y Microsoft Flow que nunca han accedido a ellas. Puede ver todas las licencias de usuario en el [centro de administración de Office 365][1].

Si un usuario ha dejado la organización, la lista mostrará **Desconocido** en columnas como **Nombre de usuario** y **Dirección de correo electrónico**. Si la lista muestra **Desconocido** pero nadie ha dejado la organización, espere unos minutos y vuelva a descargar la lista.

Para agregar licencias de usuario, abra el [centro de administración de Office 365][1].

<!--Reference links in article-->
[1]:https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc
