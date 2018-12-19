---
title: Usar la API web de Common Data Service para aplicaciones (Common Data Service para aplicaciones) | Microsoft Docs
description: 'La API web de Common Data Service para aplicaciones implementa OData v4 y proporciona una experiencia de desarrollo que puede usarse en una gran variedad de lenguajes de programación, plataformas y dispositivos.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 15c4039e-a3ca-4116-ba1d-3ac88cba3ae1
caps.latest.revision: 15
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-common-data-service-for-apps-web-api"></a>Usar la API web de Common Data Service para aplicaciones

La API web es uno de dos servicios web que puede usar para trabajar con datos y metadatos en Common Data Service para aplicaciones. El otro es el [Servicio de organización](../org-service/overview.md).

La API web de CDS para aplicaciones proporciona una experiencia de desarrollo que se puede usar en una gran variedad de lenguajes de programación, plataformas, y dispositivos. La API web implementa OData (Open Data Protocol), versión 4.0, un estándar de OASIS para crear y consumir API RESTful con orígenes de datos enriquecidos. Puede obtener más información sobre este protocolo en [http://www.odata.org/](http://www.odata.org/). Los detalles sobre esta norma están disponibles en [https://www.oasis-open.org/standards#odatav4.0](https://www.oasis-open.org/standards#odatav4.0).  
  
Dado que la API web se basa en estándares abiertos, no proporcionamos ensamblados para una experiencia de desarrollador específica. Puede crear solicitudes HTTP para operaciones específicas o usar bibliotecas de terceros para generar clases para cualquier idioma o plataforma que desee. Puede encontrar una lista de bibliotecas compatibles con OData versión 4.0 en [http://www.odata.org/libraries/](http://www.odata.org/libraries/).  

## <a name="web-api-and-the-organization-service"></a>API web y el servicio de organización

Es útil reconocer que el servicio de organización es lo que define la plataforma. La API web proporciona una experiencia de programación RESTful, pero en definitiva todas las operaciones de datos pasan por el servicio de organización subyacente. El servicio de organización define las operaciones admitidas como mensajes. Cada mensaje tiene un nombre. Estos nombres están asociados con los eventos que se usan en el marco de trabajo de eventos para evaluar qué extensiones registradas hay que iniciar. Más información: [Marco de trabajo de eventos](../event-framework.md)

La API web permite hacer las mismas operaciones que el servicio de organización, pero las presenta con estilo RESTful. OData v4 permite usar operaciones con nombre mediante *funciones* o *acciones*. La mayoría de los mensajes disponibles en el servicio de organización se exponen como una función o acción con nombre correspondiente. Esos mensajes que se corresponden con operaciones CRUD no están disponibles en la API web porque, al ser un servicio, RESTful, tienen implementaciones que usan los métodos HTTP GET, POST, PATCH y DELETE, pero dentro de la plataforma los mensajes *recuperar*, *crear*, *actualizar* y *eliminar* solo se invocan tal cual cuando se realizan las operaciones correspondientes mediante los ensamblados de .NET Framework.

  
### <a name="related-sections"></a>Secciones relacionadas

[Trabajar con datos mediante código](../work-with-data-cds.md)<br />
[OData - lo mejor para REST](http://www.odata.org/)<br />
[OData Versión 4.0 Parte 1: Protocol Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)<br />
[OData Versión 4.0 Parte 2: URL Conventions Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part2-url-conventions.html)<br />
[OData Versión 4.0 Parte 3: Common Schema Definition Language (CSDL) Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part3-csdl.html)