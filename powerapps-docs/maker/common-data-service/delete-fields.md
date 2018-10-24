---
title: Eliminación de campos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo eliminar campos.
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 578ac950-da16-4ec6-a0a4-25f3aaa3b96e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 82e560f063f2e46190420b6be5cef4cc55d9ab4f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39700758"
---
# <a name="delete-fields"></a>Eliminación de campos

<a name="BKMK_DeletingFields"></a>   
 
 Como usuario con el rol de seguridad de administrador del sistema, puede eliminar campos personalizados que no formen parte de una solución administrada. Si elimina campos, los datos almacenados en los campos se perderán. La única forma de recuperar datos de un campo que se haya eliminado es restaurar la base de datos de un punto anterior a la eliminación del campo.  
  
 Antes de poder eliminar una entidad personalizada, debe quitar las dependencias que pueden existir en otros componentes de la solución. Abra el campo y use el botón **Mostrar dependencias** de la barra de menú para ver los **Componentes dependientes**. Por ejemplo, si el campo se usa en un formulario o una vista, primero debe quitar las referencias al campo en esos componentes de la solución.  
  
 Si elimina un campo de búsqueda, la relación de entidad 1:N correspondiente se eliminará automáticamente.  

 ## <a name="next-steps"></a>Pasos siguientes

 [Eliminación de entidades personalizadas](data-platform-delete-entity.md)
