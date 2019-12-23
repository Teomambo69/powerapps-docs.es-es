---
title: 'Programadores: Prácticas recomendadas e instrucciones para trabajar con metadatos para Common Data Service | Microsoft Docs'
description: Prácticas recomendadas e instrucciones para trabajar con metadatos para desarrolladores de Common Data Service en Power Apps.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9dfc455ce9903c95b78e24b2aba25a5fbe6d8734
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883546"
---
# <a name="best-practices-and-guidance-while-working-with-metadata-for-the-common-data-service"></a>Prácticas recomendadas e instrucciones para trabajar con metadatos para Common Data Service

La siguiente lista contiene todas las instrucciones y prácticas recomendadas sobre cómo interactuar y trabajar con metadatos en Common Data Service.


|Práctica recomendada  |Descripción  |
|---------|---------|
|[Recuperar metadatos publicados](retrieve-published-metadata.md)     |La recuperación de metadatos no publicados no solo agregará sobrecarga al procesamiento de la solicitud, con un rendimiento inferior, pero también puede devolver metadatos que no espera el solicitante.         |
|[Recuperar columnas específicas para una entidad mediante API de consulta](retrieve-specific-columns-entity-via-query-apis.md)     |Las consultas enviadas para recuperar datos deben incluir columnas específicas en la instancia de ColumnSet asociadas a la consulta en lugar de a todas las columnas.         |

### <a name="see-also"></a>Vea también
[Trabajar con metadatos con código](../../metadata-services.md)<br />