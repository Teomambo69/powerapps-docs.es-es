---
title: 'Desarrolladores: Procedimientos recomendados e instrucciones para Common Data Service | Microsoft Docs'
description: Procedimientos recomendados e instrucciones dirigidos a desarrolladores de Common Data Service en PowerApps.
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
ms.date: 01/07/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c89042e1f94e6f891bfdc255c38f72929c27cb1e
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61528375"
---
# <a name="best-practices-and-guidance-for-the-common-data-service"></a>Procedimientos recomendados e instrucciones para Common Data Service

Common Data Service es un marco de trabajo extensible con el que los desarrolladores podrán crear experiencias muy personalizadas y adaptadas. Al personalizar, extender o integrar con Common Data Service, los desarrolladores deben tener en cuenta los procedimientos recomendados y las instrucciones establecidas. 

En esta sección se explicarán los problemas que hemos identificado y su impacto, así como las instrucciones para resolverlos. Explicaremos por qué las cosas deben realizarse de una manera determinada para evitar posibles problemas en el futuro. Esto ofrece ventajas como facilidad de uso, compatibilidad y rendimiento del entorno. Los documentos de instrucciones complementan la información existente en las guías para desarrolladores y administradores.

# <a name="targeted-customization-types"></a>Tipos de personalización tratados
La documentación trata estos tipos de personalización:

- Complementos y actividades de flujo de trabajo personalizados
- Trabajo con datos de Common Data Service
- Integraciones que amplían Common Data Service

# <a name="sections"></a>Secciones
Cada artículo de instrucciones incluye la mayoría o todas las secciones siguientes:

- Título: descripción de la instrucción
- Categoría: una o varias áreas afectadas por no seguir las instrucciones
- Impacto potencial: el nivel de riesgo (alto, medio o bajo) que afecta al entorno por no seguir las instrucciones
- Síntomas: indicaciones posibles de que no se han seguido las instrucciones
- Instrucciones: recomendaciones que también pueden incluir ejemplos
- Patrones problemáticos: descripción o ejemplos de no seguir las instrucciones
- Información adicional: detalles complementarios para tener una visión más amplia
- Vea también: referencias a más información sobre algo que se ha mencionado en el artículo

# <a name="categories"></a>Categorías
Cada artículo de instrucciones se clasifica con una o varias de estas categorías:

- Uso: uso inadecuado de una determinada API, patrón o configuración
- Diseño: errores de diseño en una personalización
- Rendimiento: personalización o patrón que pueden producir un efecto negativo sobre el rendimiento en áreas como la administración de memoria, el uso de CPU, el tráfico de red o la experiencia del usuario
- Seguridad: posibles vulnerabilidades en una personalización que podrían aprovecharse en un entorno en tiempo de ejecución
- Preparación de actualización: personalización o patrón que podrían aumentar el riesgo de tener una actualización de versión incorrecta
- Migración en línea: personalización o patrón que podrían aumentar el riesgo de tener una migración en línea incorrecta
- Mantenimiento: personalización que innecesariamente aumenta la cantidad de esfuerzo de desarrollo necesario para realizar cambios, la frecuencia de los cambios necesarios o la posibilidad de introducir regresiones
- Compatibilidad: personalización o patrón que se encuentra fuera de los límites de las instrucciones de compatibilidad publicada, incluido el uso de API quitadas o la implementación de técnicas prohibidas
