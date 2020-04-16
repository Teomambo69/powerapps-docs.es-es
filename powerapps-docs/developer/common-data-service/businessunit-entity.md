---
title: Entidad BusinessUnit (Common Data Service) | Microsoft Docs
description: Una organización en Common Data Service, como una sociedad de cartera o una compañía, se compone de unidades de negocio.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8b10a53a1dde7e0a86d92a9601bcbc01d8577010
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156392"
---
# <a name="businessunit-entity"></a>Entidad BusinessUnit

Una organización en Common Data Service, como una sociedad de cartera o una compañía, se compone de unidades de negocio. Una *unidad de negocio* es una unidad de la organización superior. Las unidades de negocio pueden ser elementos principales de otras unidades de negocio (unidades de negocio secundarias). La primera unidad de negocio creada para una organización se denomina unidad de negocio raíz. Las unidades de negocio se pueden eliminar, pero la unidad de negocio raíz no se puede eliminar.  
  
- Una *unidad de negocio principal* es cualquier unidad de negocio con una o varias unidades de negocio que le informan en la jerarquía.  
  
- Una *unidad de negocio secundaria* es una unidad de negocio situada inmediatamente debajo de otra en la jerarquía empresarial de una organización.  
  
 Una unidad de negocio puede ser propietaria de los registros, como se define en el tipo de propiedad de la definición de los metadatos de una entidad. 
  
 Los roles de seguridad se asocian a unidades de negocio. Puede llamar al mensaje <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest> para averiguar la unidad de negocio del usuario con sesión iniciada actualmente o del usuario suplantado.

### <a name="see-also"></a>Vea también

[Referencia de entidad de BusinessUnit](reference/entities/businessunit.md)
[Entidades de seguridad](security-model.md)