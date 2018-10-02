---
title: Establecimiento de propiedades para campos en PowerApps | MicrosoftDocs
description: Aprenda cómo establecer propiedades administradas de un campo
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
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-managed-properties-for-fields"></a>Establecer las propiedades administradas de los campos

<a name="BKMK_SettingManagedProperties"></a>   

 Las Propiedades administradas se aplican únicamente al incluir campos en una solución administrada e importar la solución en otro entorno. Estos valores permiten al responsable de la solución tener un determinado control sobre el nivel de personalización que desea permitir a los usuarios que instalen la solución administrada al personalizar este campo. Para establecer las propiedades administradas de un campo, seleccione **Propiedades administradas** en la barra de menú.  
  
 La opción **Se puede personalizar** controla el resto de opciones. Si esta opción es `False`, no se aplicará ninguno de los demás valores. Si es `True`, puede especificar las demás opciones de personalización.  
  
 Si el campo es personalizable, defina las siguientes opciones en `True` o `False`.  
  
- **Se puede modificar el nombre para mostrar**  
  
- **Se puede cambiar el nivel de requisito**  
  
- **Se puede cambiar propiedades adicionales**  
  
 Estas opciones se explican por sí mismas. Si establece todas las opciones individuales en `False`, también puede establecer **Se puede personalizar** en `False`.  

 ## <a name="next-steps"></a>Pasos siguientes

 [Crear y editar campos](create-edit-fields.md)
