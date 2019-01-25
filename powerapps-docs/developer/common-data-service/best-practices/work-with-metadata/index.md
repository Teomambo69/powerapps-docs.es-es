---
title: 'Desarrolladores: Procedimientos recomendados e instrucciones al trabajar con metadatos en Common Data Service para aplicaciones | Microsoft Docs'
description: Procedimientos recomendados e instrucciones dirigidos a desarrolladores que trabajan con metadatos en Common Data Service para aplicaciones en PowerApps.
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
ms.openlocfilehash: 938d3ea2337137b1c78a1f4849191a261ac7a30a
ms.sourcegitcommit: 11486fb4c16095e3fef785126003cac3e3e06c0d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2019
ms.locfileid: "54271571"
---
# <a name="best-practices-and-guidance-while-working-with-metadata-for-the-common-data-service-for-apps"></a>Procedimientos recomendados e instrucciones al trabajar con metadatos en Common Data Service para aplicaciones

Aquí se enumeran todas las instrucciones y procedimientos recomendados para interactuar y trabajar con metadatos en Common Data Service para aplicaciones.


|Procedimiento recomendado  |Descripción  |
|---------|---------|
|[Recuperar metadatos publicados](retrieve-published-metadata.md)     |La recuperación de metadatos no publicados no solo supone más sobrecarga para el procesamiento de la solicitud, haciendo que este se ralentice, sino que también podría devolver metadatos no solicitados por el usuario.         |
|[Recuperar columnas específicas de una entidad a través de las API de consulta](retrieve-specific-columns-entity-via-query-apis.md)     |Las consultas enviadas para recuperar datos deben incluir columnas concretas en la instancia ColumnSet asociada a la consulta, en lugar de Todas las columnas.         |

# <a name="see-also"></a>Vea también
[Trabajar con metadatos mediante código](../../metadata-services.md)<br />