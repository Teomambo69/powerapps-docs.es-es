---
title: Eliminar campos en Power Apps | MicrosoftDocs
description: Aprenda a eliminar campos
ms.custom: ''
ms.date: 06/20/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 578ac950-da16-4ec6-a0a4-25f3aaa3b96e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 224c07600a13b0adf9cedd7592be7f1c2befec90
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864094"
---
# <a name="delete-fields"></a>Eliminar campos

<a name="BKMK_DeletingFields"></a>   
 
 Como usuario con el rol de seguridad de administrador del sistema, puede eliminar campos personalizados que no sean parte de una solución administrada. Si elimina campos, los datos almacenados en los campos se perderán. La única forma de recuperar datos de un campo que se haya eliminado es restaurar la base de datos de un punto anterior a la eliminación del campo.  
  
 Antes de poder eliminar una entidad personalizada, debe quitar las dependencias que pueden existir en otros componentes de la solución. Abra el campo y use el botón **Mostrar dependencias** de la barra de menú para ver los **Componentes dependientes**. Por ejemplo, si el campo se usa en un formulario o una vista, primero debe quitar las referencias al campo en esos componentes de la solución.  
  
 Si elimina un campo de búsqueda, la relación de entidad 1:N correspondiente se eliminará automáticamente.  

 ## <a name="next-steps"></a>Pasos siguientes

 [Eliminación de entidades personalizadas ](data-platform-delete-entity.md)
