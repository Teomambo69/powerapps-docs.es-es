---
title: Edición de mensajes de entidades del sistema con PowerApps | MicrosoftDocs
description: Obtenga información sobre cómo editar mensajes de entidad del sistema
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="edit-system-entity-messages"></a>Editar mensajes de entidades del sistema

El nombre para mostrar predeterminado de algunas entidades del sistema se usa en texto y mensajes de error de la interfaz de usuario en Common Data Service for Apps. Si cambia el nombre para mostrar, también debe actualizar los mensajes que usan el nombre para mostrar predeterminado. Por ejemplo, si cambia el nombre para mostrar de *Cuenta* a *Empresa*, podría aparecer un mensaje de error con el nombre antiguo.  

No puede editar mensajes del sistema mediante el portal de PowerApps, debe usar el explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

En el explorador de soluciones, debajo de la entidad, si ve un nodo **Mensajes**, puede editar determinado texto que incluye referencias al nombre para mostrar de la entidad original. 

![Mensajes de la entidad](../model-driven-apps/media/entity-messages.png)

Modificar este texto es bastante sencillo. Haga doble clic en el mensaje para ver un formulario con tres campos:  
  
|Campo|Descripción|  
|-----------|-----------------|  
|**Cadena para mostrar predeterminada**|Muestra el texto original.|  
|**Cadena para mostrar personalizada**|Edite este texto para cambiar la cadena para mostrar.|  
|**Comentario**|Opcional. Incluya un comentario sobre lo que cambió y porqué.|  
  
Parte de texto del mensaje puede tener marcadores. Estos marcadores son números con llaves a ambos lados. Por ejemplo: `{0}`. Estos marcadores permiten insertar texto en el mensaje. Si modifica mensajes, asegúrese de mantener esos marcadores. 

Seleccione ![Guardar](media/save-entity-icon-solution-explorer.png) para guardar los cambios. Seleccione **Guardar y cerrar** para cerrar el formulario al guardar.

> [!NOTE]
> Aunque la IU expuesta para editar mensajes de entidad del sistema incluye muchas referencias a los nombres de entidad, no los incluye todos. Para un enfoque más completo, consulte [Actualizar texto localizable en el idioma base](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language)

## <a name="programmatically-update-entity-display-strings"></a>Actualizar mediante programación las cadenas para mostrar de la entidad

Para los desarrolladores que buscan una forma de trabajar con estos elementos en código, las cadenas para mostrar se almacenan en la entidad [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md). 

La entidad `DisplayString` no contiene las cadenas para mostrar predeterminadas. Los dos atributos de esta entidad que contienen texto son [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) y [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString). De forma predeterminada, estos valores de atributo son nulos a menos que se haya personalizado y publicado la cadena para mostrar. El valor de `PublishedDisplayString` es de solo lectura y refleja el valor publicado actualmente de `CustomDisplayString`.
 
## <a name="see-also"></a>Vea también
[Editar una entidad](edit-entities.md)<br />
[Traducir texto localizable para aplicaciones controladas por modelos](../model-driven-apps/translate-localizable-text.md)
