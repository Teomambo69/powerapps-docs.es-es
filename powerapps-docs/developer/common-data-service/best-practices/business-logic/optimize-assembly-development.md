---
title: Optimizar el desarrollo de ensamblados personalizados | MicrosoftDocs
description: Considere combinar actividades separadas de complementos y flujo de trabajo personalizado en un único ensamblado personalizado para mejorar el rendimiento y la capacidad de retención y traspase actividades de complementos y flujo de trabajo personalizado a múltiples ensamblados personalizados si el tamaño de un ensamblado está cerca de los límite de tamaño de ensamblados en espacios independientes.
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
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 926cc3f7ebb61d0d9c59df707f6d4d824d59599a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861845"
---
# <a name="optimize-assembly-development"></a>Optimizar el desarrollo de ensamblados

**Categoría**: diseño, mantenimiento, diseño

**Potencial de impacto**: bajo

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Cuando se desarrollan los ensamblados personalizados, se deben tener en cuenta algunas consideraciones:

1. Múltiples ensamblados diferentes personalizados
    - Mayor complejidad del mantenimiento
    - Incremento potencial de la duración de la ejecución de los complementos

2. La restricción del tamaño de ensamblado de espacio aislado es 16 MB en Common Data Service.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

> [!NOTE]
> Se está trabajando en las clarificaciones de las instrucciones respecto a detalles específicos de la optimización del desarrollo de ensamblados, por ejemplo, cómo combinar complementos independientes en un único ensamblado personalizado y sugerencias para minimizar el tamaño de los complementos.

### <a name="consolidate-plug-ins-or-custom-workflow-activities-into-a-single-assembly"></a>Consolidar actividades de complementos o de flujo de trabajo personalizado en un solo ensamblado

Las actividades de complementos y de flujo de trabajo personalizado desarrolladas para Common Data Service deben coexistir en único proyecto de Visual Studio. Considere realizar combinar las actividades individuales de complementos y de flujo de trabajo personalizado en solo proyecto/ensamblado de Visual Studio a menos que los complementos se inscriban en las excepciones siguientes:

1. La actividad de complementos o de flujo de trabajo personalizado debe implementarse selectivamente en un entorno pero no en otros usuarios.

2. El tamaño físico del ensamblado está cerca de 16 MB o los supera para una instancia de Common Data Service.


### <a name="move-plug-inscustom-workflow-activities-into-multiple-assemblies"></a>Mover actividades de complementos/actividades personalizadas a múltiples ensamblados

Power Apps y Dynamics 365 (online) tienen una limitación de tamaño de ensamblado de 16 MB, que no se puede cambiar. Si el tamaño del ensamblado se acerca a 16 MB, considere transferir las actividades de complementos y de flujo de trabajo personalizado a varios ensamblados.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

### <a name="multiple-assemblies"></a>Múltiples ensamblados
Tener múltiples ensamblados puede impactar a algunas áreas:

1. Rendimiento: cada ensamblado tiene un ciclo de vida administrado por Common Data Service.  Esto incluye la carga, el almacenamiento en caché y la descarga de ensamblados.  Disponer con más de un ensamblado hace que se desarrolle más trabajo en el servidor, que carga y almacena en caché el ensamblado, y puede afectar al tiempo de ejecución total de la actividad del complemento y de flujo de trabajo personalizado.

2. Mantenimiento: tener más de un proyecto de Visual Studio de actividad de complementos y de flujo de trabajo personalizado conlleva una administración del ciclo de vida de la aplicación (ALM) más compleja. Incrementa el riesgo y la cantidad de tiempo de actualizar o aplicar parches al proyecto pertinente para una actividad de complemento y de flujo de trabajo personalizado, empaquetando estas actividades dentro de una solución y administrándolas en una implementación.

### <a name="assembly-larger-than-16-mb"></a>Ensamblado mayor que 16 MB
No podrá registrar un ensamblado personalizado dentro de Common Data Service que sea mayor que 16 MB.

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Muy a menudo, los programadores crean un nuevo proyecto de Visual Studio para cada actividad de complementos o de flujo de trabajo personalizado.  A su vez, esto ocasiona que se genere un ensamblado diferente para cada actividad de complementos o de flujo de trabajo personalizado.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Marco de trabajo de eventos](../../event-framework.md)<br />
[Use complementos para ampliar los procesos de negocio](../../plug-ins.md)<br />
