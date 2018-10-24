---
title: Definición de propiedades administradas de campos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo establecer las propiedades administradas de un campo
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 4ddcfcf3-5604-4b93-a5ee-589d4fb97fa4
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: be3b04bbc324520904c765506e32d6027927e214
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712191"
---
# <a name="set-managed-properties-for-fields"></a>Establecimiento de las propiedades administradas de campos

<a name="BKMK_SettingManagedProperties"></a>   

 Las propiedades administradas solo se aplican al incluir campos en una solución administrada e importarla en otro entorno. Esta configuración permite que un responsable de la solución ejerza cierto control sobre el nivel de personalización que quien instala la solución administrada puede tener cuando personaliza este campo. Para establecer las propiedades administradas de un campo, seleccione **Propiedades administradas** en la barra de menús.  
  
 La opción **Se puede personalizar** controla todas las demás opciones. Si esta opción es `False`, no se aplican ninguno de los demás ajustes. Si es `True`, puede especificar otras opciones de personalización.  
  
 Si el campo se puede personalizar, establezca las siguientes opciones en `True` o `False`.  
  
- **Se puede modificar el nombre para mostrar**  
  
- **Se puede cambiar el nivel de requisito**  
  
- **Se pueden cambiar las propiedades adicionales**  
  
 Estas opciones se entienden fácilmente. Si establece todas las opciones individuales en `False`, también puede establecer **Se puede personalizar** en `False`.  

 ## <a name="next-steps"></a>Pasos siguientes

 [Crear y editar campos](create-edit-fields.md)