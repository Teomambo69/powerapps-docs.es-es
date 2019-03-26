---
title: Quitar personalizaciones desactivadas o deshabilitadas | MicrosoftDocs
description: Las personalizaciones desactivadas o deshabilitadas se deben quitar de una solución para mejorar la administración de las soluciones y para reducir el riesgo de usar o de administrar un componente obsoleto.
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
---
# <a name="remove-deactivated-or-disabled-customizations"></a>Quitar personalizaciones desactivadas o deshabilitadas

**Categoría**: mantenimiento, compatibilidad

**Potencial de impacto**: bajo

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Las personalizaciones desactivadas o deshabilitadas se deben quitar de una solución para mejorar la administración de las soluciones y para reducir el riesgo de usar o de administrar un componente obsoleto.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Asegúrese de que cada componente de la solución qué esté desactivado o deshabilitado, sea porque se ha hecho intencionadamente.  Si es así y ya no se volver a usar, considere quitarlo de la solución para evitar cualquier posible confusión para los usuarios y los personalizadores del sistema. Estos componentes incluyen:

- Pasos de procesamiento de mensajes del SDK
- Procesos
- Reglas de creación y actualización de registros
- SLA

Así como los componentes de la entidad como:

- Formularios
- Vistas
- Reglas de negocio

![Procesos desactivados](../media/deactivated-processes.png)

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Aplicar la lógica empresarial personalizada con reglas de negocio y flujos en aplicaciones basadas en modelos](/powerapps/maker/model-driven-apps/guide-staff-through-common-tasks-processes)<br />
[Eventos en formularios y cuadrículas en aplicaciones basadas en modelos](/powerapps/developer/model-driven-apps/clientapi/events-forms-grids)<br/>