---
title: Autenticarse en Common Data Service con la API web (Common Data Service)| Microsoft Docs
description: Obtenga más información acerca de las formas diferentes de administrar la autenticación al usar la API web.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 767f39d4-6a8e-48f0-bf7d-69ea1191acef
caps.latest.revision: 8
author: JimDaly
ms.author: jdaly
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 85dbea11497c05393c1376f53318ae8a50e22930
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155112"
---
# <a name="authenticate-to-common-data-service-with-the-web-api"></a>Autenticarse en Common Data Service con la API web


Debe usar OAuth como se describe en [Usar OAuth con Common Data Service](../authenticate-oauth.md).

El código que escribe para administrar la autenticación cuando usa la API web dependen del tipo de implementación y dónde está su código.  
  
### <a name="authenticate-with-javascript-in-web-resources"></a>Autenticarse con JavaScript en recursos web  

Cuando usa la API web con JavaScript en recursos web HTML, los scripts de formularios o los comandos de la cinta de opciones no necesita incluir ningún código para autenticación. En cada uno de estos casos la aplicación ya autentica al usuario y administra la autenticación.  

Si está creando una aplicación de una sola página (SPA) mediante JavaScript puede usar la biblioteca de adal.js como se explica en [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página](../oauth-cross-origin-resource-sharing-connect-single-page-application.md).  
  
### <a name="see-also"></a>Vea también
 
[Usar la API web de Common Data Service](overview.md)<br />
[Tipos y operaciones de API web](web-api-types-operations.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Usar OAuth con Common Data Service](../authenticate-oauth.md)<br />
[Usar OAuth con uso compartido de recursos de origen cruzado para conectar una Aplicación de una sola página](../oauth-cross-origin-resource-sharing-connect-single-page-application.md)
