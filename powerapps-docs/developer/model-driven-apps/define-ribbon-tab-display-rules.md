---
title: Definir las reglas de visualización de la pestaña cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo definir las reglas de visualización de la pestaña de la cinta de opciones.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
- ''
ms.topic: article
ms.assetid: 916f4e82-01a3-2476-c2a4-ff71caa4195c
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5ad0f76512d423cbe94072cc96ec09da1b56ce9c
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276156"
---
# <a name="define-ribbon-tab-display-rules"></a>Definir las reglas de visualización de la pestaña de la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-tab-display-rules -->

Las reglas de visualización de las pestañas controlan si una pestaña específica se muestra para una cinta o si no se muestra.  
  
 A diferencia de otros elementos de la cinta como grupos o controles específicos, debe proporcionar explícitamente una regla de visualización de pestañas para que una pestaña se muestre en la cinta. De manera predeterminada, los demás elementos de la cinta siempre están visibles a menos que una regla de visualización los elimine.  
  
 Los elementos `<TabDisplayRule>` requieren que el atributo `TabCommand` coincida con un valor de atributo `<Tab>` `Command`.  
  
 En `RibbonDiffXml`, las pestañas pueden definirse para entidades específicas, o bien, pueden definirse globalmente. Si la pestaña se define para una entidad, el único tipo de regla válido es `<EntityRule>`. Dado que la definición de una pestaña en un ámbito de una entidad determinada ya limita la pestaña con esa entidad solamente, los únicos atributos válidos son `AppliesTo` (`PrimaryEntity` o `SelectedEntity`) y `Context` (`Form`, `HomePageGrid`, `SubGridStandard`, o `SubGridAssociated`).  
  
 Cuando define una regla de visualización de pestaña a nivel global en `RibbonDiffXml` para las cintas de aplicación, puede aplicar tanto los elementos `EntityRule` como los elementos `<PageRule>`.  
  
### <a name="see-also"></a>Vea también  
 [Personalizar comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Definir escalabilidad para elementos de la cinta de opciones](define-scaling-ribbon-elements.md)   
 [Pasar parámetros a una dirección URL con la cinta de opciones](pass-parameters-url-by-using-ribbon.md)