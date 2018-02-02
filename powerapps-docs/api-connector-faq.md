---
title: P+F sobre los conectores de API | Microsoft Docs
description: Encuentre respuestas a preguntas acerca de los requisitos, los desencadenadores y otros temas.
services: 
suite: powerapps
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: b945f2775e26327557255a75f18e87a638a9fe66
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="api-connector-faq-powerapps"></a>P+F sobre los conectores de API (PowerApps)
## <a name="requirements"></a>Requisitos
**P:** Si no soy un fabricante de software independiente, ¿puedo crear un conector?

**R:** Para comercializar públicamente un conector, es necesario ser el propietario del servicio subyacente o tener los derechos explícitos para usar la API.

**P:** ¿Puedo crear un conector sin API de REST?

**A:** No. Para crear un conector de API, se necesita compatibilidad con API de REST de HTTP estables para el servicio.

**P:** ¿Cuáles son los tipos de autenticación compatibles?

**R:** Se admiten los siguientes estándares de autenticación:

* OAuth2.0 (Azure Active Directory incluido)
* Clave de API
* Autenticación básica

## <a name="triggers"></a>Desencadenadores
**P:** ¿Puedo crear desencadenadores sin webhooks? 

**R:** Los conectores de API para Microsoft Flow y Logic Apps únicamente permiten crear desencadenadores basados en webhook. Si desea utilizar otras formas de implementación, póngase en contacto con [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com) y proporcione más detalles sobre la API.

## <a name="miscellaneous"></a>Varios
**P:** Mis API utilizan un host dinámico. ¿Cómo se implementa en OpenAPI?

**R:** La característica de conector de API no es compatible con los hosts dinámicos. Para el proceso de desarrollo y pruebas, utilice un host estático. Durante el proceso de envío, hable con su contacto de Microsoft sobre la implementación dinámica.

**P:**  ¿Se admite la colección Postman V2?

**R:** No, Postman V2 no es compatible actualmente.

**P:** ¿Se admite OpenAPI 3.0?

**R:** No, OpenAPI 2.0 es actualmente la única versión admitida.

