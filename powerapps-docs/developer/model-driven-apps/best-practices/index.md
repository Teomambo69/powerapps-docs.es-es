---
title: 'Programadores: Prácticas recomendadas e instrucciones para aplicaciones basadas en modelos | Microsoft Docs'
description: Prácticas recomendadas e instrucciones para programadores de aplicaciones basadas en modelos en Power Apps.
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
ms.openlocfilehash: 70d150d0405bf6196387a39c807a26ba3e6efbfa
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883506"
---
# <a name="best-practices-and-guidance-for-model-driven-apps"></a>Prácticas recomendadas e instrucciones para aplicaciones basadas en modelos

Las aplicaciones basadas en modelos son un modelo centrado en los componentes para la programación de aplicaciones que puede ampliar un desarrollador para lograr una experiencia mucho adaptada. Cuando personaliza aplicaciones basadas en modelos, un programador debe tener en cuenta las instrucciones y las prácticas recomendadas establecidas. 

En esta sección se informará sobre los problemas que hemos identificado, su impacto, y entenderá la información para resolverlos. Explicaremos las cuestiones de fondo sobre por qué las cosas deben realizarse de tal forma que se eviten posibles problemas en el futuro. Esto puede ser una ventaja para la utilidad, la compatibilidad y el rendimiento del entorno. La documentación de las instrucciones admite la información existente en de las guías de programación y administración.

## <a name="targeted-customization-types"></a>Tipos específicos de personalización
La documentación aborda los siguientes tipos de personalización:

- Diseño de aplicaciones basadas en modelos
- Diseño de un formulario de entidad
- Scripting del cliente
- Recursos web

## <a name="sections"></a>Secciones
Cada artículo de las instrucciones incluye la mayor parte o todas las secciones siguientes:

- Título: descripción de las instrucciones.
- Categoría: una o varias áreas perjudicadas si no se siguen las instrucciones.
- Impacto potencial: el nivel de riesgo (alto, medio o bajo) que afecta al entorno por no seguir las instrucciones.
- Síntomas: posibles signos que indican que las instrucciones no se han seguimiento.
- Instrucciones: recomendaciones que también pueden incluir ejemplos.
- Patrones problemáticos: descripción o ejemplos de no seguir las instrucciones.
- Información adicional: información de respaldo para tener una visión más amplia.
- Vea también: referencias para obtener más información sobre algo que aparece en el artículo.

## <a name="categories"></a>Categorías
Cada artículo de las instrucciones se clasifica en una o más de las categorías siguientes:

- Uso: uso incorrecto de una API, patrón o configuración particulares.
- Diseño: defectos de diseño en una personalización.
- Rendimiento: personalización o patrón que puede generar un efecto negativo en el rendimiento en áreas como la administración de la memoria, el uso de la CPU, el tráfico de red o la experiencia de usuario.
- Seguridad: vulnerabilidades potenciales en una personalización que se puedo explotar en un entorno en tiempo de ejecución.
- Actualizaciones preparadas: personalización o patrón que puede aumentar el riesgo de tener una versión de la actualización que no se realice correctamente.
- Migración en línea: personalización o patrón que puede aumentar el riesgo de tener una migración en línea que no se realice correctamente.
- Capacidad de mantenimiento: personalización que incrementa innecesariamente la cantidad de esfuerzo de desarrollo para realizar cambios, la frecuencia de los cambios obligatorios o la oportunidad para realizar regresiones.
- Compatibilidad: personalización o patrón que no está dentro de los límites de la instrucciones publicadas de compatibilidad, incluido el uso de API eliminadas o la implementación de técnicas prohibidas.