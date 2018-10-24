---
title: Edición de mensajes de entidad del sistema con PowerApps | Microsoft Docs
description: Aprenda cómo editar mensajes de entidad del sistema
ms.custom: ''
ms.date: 05/15/2018
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
ms.assetid: 3ccbd8de-8d6f-4058-87f7-15463667cfc6
caps.latest.revision: 41
ms.author: matp
manager: kvivek
ms.openlocfilehash: 797d6855bea421abd90752dd9ae0ad73a9d92f38
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39702886"
---
# <a name="edit-system-entity-messages"></a>Edición de mensajes de entidad del sistema

El nombre para mostrar predeterminado de algunas entidades del sistema se utiliza en el texto de la interfaz de usuario y en los mensajes de error del servicio Common Data Service para aplicaciones. Si cambia el nombre para mostrar, también debe actualizar cualquier mensaje que utilice el nombre para mostrar predeterminado. Por ejemplo, si cambia el nombre para mostrar de *Cuenta* a *Empresa*, todavía podría ver un mensaje de error con el nombre antiguo.  

No se pueden editar los mensajes del sistema mediante el portal de PowerApps; hay que utilizar el Explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

En el Explorador de soluciones, debajo de la entidad, si ve un nodo **Mensajes**, puede editar cierto texto que incluye referencias al nombre para mostrar de la entidad original. 

![Mensajes de la entidad](../model-driven-apps/media/entity-messages.png)

La edición de este texto es muy sencilla. Haga doble clic en el mensaje para ver un formulario con tres campos:  
  
|Campo|Descripción|  
|-----------|-----------------|  
|**Cadena para mostrar predeterminada**|Muestra el texto original.|  
|**Cadena para mostrar personalizada**|Edite este texto para cambiar la cadena para mostrar.|  
|**Comentario**|Opcional. Incluya un comentario sobre lo que ha cambiado y por qué.|  
  
Algunos de los mensajes de texto pueden tener marcadores de posición en ellos. Estos marcadores de posición son números con corchetes a cada lado. Por ejemplo: `{0}`. Estos marcadores de posición permiten insertar texto en el mensaje. Si edita los mensajes, asegúrese de mantener estos marcadores de posición. 

Seleccione ![Guardar](media/save-entity-icon-solution-explorer.png) para guardar los cambios. Haga clic en **Guardar y cerrar** para cerrar formulario cuando lo guarde.

> [!NOTE]
> Aunque la interfaz de usuario expuesta a la edición de mensajes de entidades del sistema incluye muchas referencias a nombres de entidades, no incluye todas ellas. Para un enfoque más completo, consulte [Updating localizable text in the base language](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language) (Actualización de texto localizable en el idioma base).

## <a name="programmatically-update-entity-display-strings"></a>Actualización mediante programación de cadenas para mostrar de entidad

Para los desarrolladores que buscan una forma de trabajar con ellos en código, las cadenas para mostrar se almacenan en la entidad [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md). 

La entidad `DisplayString` no contiene las cadenas para mostrar predeterminadas. Los dos atributos para esta entidad que contienen texto son [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) y [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString). De forma predeterminada, estos valores de atributo son valores NULL a menos que la cadena para mostrar se haya personalizado y publicado. El valor `PublishedDisplayString` es de solo lectura y refleja el valor `CustomDisplayString` publicado actualmente.
 
## <a name="see-also"></a>Vea también
[Edición de una entidad](edit-entities.md)<br />
[Traducción de texto localizable para aplicaciones controladas por modelos](../model-driven-apps/translate-localizable-text.md)
