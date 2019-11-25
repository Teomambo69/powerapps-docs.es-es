---
title: Eliminar una aplicación controlada por modelos | MicrosoftDocs
description: Aprenda a eliminar o quitar una aplicación controlada por modelos de su entorno de PowerApps.
keywords: ''
ms.date: 10/08/2019
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 026420ad6a5f3ab3e74c9c0d11f87f8a52ffa417
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756233"
---
# <a name="delete-a-model-driven-app"></a>Eliminar una aplicación controlada por modelos
Elimine o quite aplicaciones obsoletas en su entorno.

> [!IMPORTANT]
> Si se instaló una aplicación basada en modelo en la solución predeterminada como parte de una solución administrada, consulte [Eliminar una aplicación basada en modelo que se instaló como parte de una solución administrada](#delete-a-model-driven-app-that-was-installed-as-part-of-a-managed-solution).

1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. En el panel de navegación izquierdo, seleccione **Aplicaciones**. 
3. Seleccione la aplicación que desea eliminar y, a continuación, seleccione **Eliminar** en la barra de comandos.
4. En el mensaje de confirmación que aparece, seleccione **Eliminar**.

   Se elimina la aplicación de su entorno.
  
Si el componente tiene dependencias (como relaciones), primero debe quitar las dependencias para poder eliminar la aplicación. Para ver las dependencias de una aplicación, seleccione la aplicación y, a continuación, seleccione **Mostrar dependencias** en la barra de comandos.

> [!NOTE]
> Cuando se elimina la aplicación, se recomienda que elimine su mapa de sitio asociado. Si no se elimina el mapa de sitio asociado, el diseñador del mapa de sitio muestra un error la primera vez que intenta crear otra aplicación con el mismo nombre. Sin embargo, puede omitir el error y el error no aparecerá cuando intente volver a crear la aplicación.

## <a name="delete-a-model-driven-app-that-was-installed-as-part-of-a-managed-solution"></a>Eliminar una aplicación basada en modelo que se instaló como parte de una solución administrada
Para eliminar una aplicación basada en modelo que se instaló en el entorno como parte de una solución administrada, elimine la solución administrada. 

### <a name="delete-a-managed-solution"></a>Eliminar una solución administrada 
Todos los componentes de la solución administrada se eliminan al eliminar la solución.
1.  Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2.  En el panel de navegación izquierdo, seleccione **Soluciones**.
3.  En la lista **Soluciones**, seleccione la solución administrada que desea eliminar y en la barra de herramientas, seleccione **Eliminar**. 

