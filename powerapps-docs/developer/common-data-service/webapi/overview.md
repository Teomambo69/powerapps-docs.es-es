---
title: Usar la API web de Common Data Service (Common Data Service)| Microsoft Docs
description: La API web de Common Data Service implementa OData v4 y proporciona una experiencia de desarrollo que puede usarse en una gran variedad de lenguajes de programación, plataformas y dispositivos.
ms.custom: ''
ms.date: 03/31/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 15c4039e-a3ca-4116-ba1d-3ac88cba3ae1
caps.latest.revision: 15
author: JimDaly
ms.author: susikka
ms.reviewer: pehecke
manager: shujoshi
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bc52a5058b6246534761d5191d9fed49672ba5b1
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275808"
---
# <a name="use-the-common-data-service-web-api"></a>Use la API web de Common Data Service

La API web es uno de dos servicios web que puede usar para trabajar con datos y metadatos en Common Data Service. El otro es el [Servicio de organización](../org-service/overview.md).

La API web de Common Data Service proporciona una experiencia de desarrollo que puede usarse en una gran variedad de lenguajes de programación, plataformas, y dispositivos. La API web implementa OData (Open Data Protocol), versión 4.0, un estándar de OASIS para crear y consumir API RESTful con orígenes de datos enriquecidos. Puede obtener más información sobre este protocolo en [https://www.odata.org/](https://www.odata.org/). Los detalles sobre esta norma están disponibles en [https://www.oasis-open.org/standards#odatav4.0](https://www.oasis-open.org/standards#odatav4.0). 


Dado que la API web se basa en estándares abiertos, no proporcionamos ensamblados para una experiencia de desarrollador específica. Puede crear solicitudes HTTP para operaciones específicas o usar bibliotecas de terceros para generar clases para cualquier idioma o plataforma que desee. Puede encontrar una lista de bibliotecas compatibles con OData versión 4.0 en [https://www.odata.org/libraries/](https://www.odata.org/libraries/).  

## <a name="web-api-and-the-organization-service"></a>API web y el servicio de organización

Es útil reconocer que el servicio de organización es lo que define la plataforma. La API web proporciona una experiencia de programación RESTful, pero en definitiva todas las operaciones de datos pasan por el servicio de organización subyacente. El servicio de organización define las operaciones admitidas como mensajes. Cada mensaje tiene un nombre. Estos nombres están asociados con los eventos que se usan en el marco de trabajo de eventos para evaluar qué extensiones registradas hay que iniciar. Más información: [Marco de trabajo de eventos](../event-framework.md)

La API web permite hacer las mismas operaciones que el servicio de organización, pero las presenta con estilo RESTful. OData v4 permite usar operaciones con nombre mediante *funciones* o *acciones*. La mayoría de los mensajes disponibles en el servicio de organización se exponen como una función o acción con nombre correspondiente. Esos mensajes que se corresponden con operaciones CRUD no están disponibles en la API web porque, al ser un servicio, RESTful, tienen implementaciones que usan los métodos HTTP GET, POST, PATCH y DELETE, pero dentro de la plataforma los mensajes *recuperar*, *crear*, *actualizar* y *eliminar* solo se invocan tal cual cuando se realizan las operaciones correspondientes mediante los ensamblados de .NET Framework.

## <a name="getting-started"></a>Introducción

Ahora que ha leído una descripción general de la API web, vaya al tema [Introducción a la API web de Common Data Service](get-started-dynamics-365-web-api-csharp.md) para aprender a escribir en Visual Studio su primer programa C# que usa la API web.

Si es desarrollador de JavaScript y desea utilizar la API web en aplicaciones basadas en modelos, vaya a [JavaScript del lado del cliente utilizando la API web en aplicaciones basadas en modelos](get-started-web-api-client-side-javascript.md).
  
### <a name="related-sections"></a>Secciones relacionadas

[Trabajar con datos mediante código](../work-with-data-cds.md)<br />
[OData - lo mejor para REST](https://www.odata.org/)<br />
[OData Versión 4.0 Parte 1: Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)<br />
[OData Versión 4.0 Parte 2: URL Conventions Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part2-url-conventions.html)<br />
[OData Versión 4.0 Parte 3: Common Schema Definition Language (CSDL) Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part3-csdl.html)
