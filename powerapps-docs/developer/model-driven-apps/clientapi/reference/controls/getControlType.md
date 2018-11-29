---
title: getControlType (referencia de la API de cliente) en aplicaciones basadas en modelos para Dynamics 365| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcontroltype-client-api-reference"></a>getControlType (referencia de la API de cliente)



Devuelve un valor que categoriza los controles.

## <a name="control-types-supported"></a>Tipos de control admitidos

Todas

## <a name="syntax"></a>Sintaxis

`getControl(arg).getControlType();`

**Valor de retorno**:

**Tipo**: Cadena

|Valor devuelto |Descripción|
|--|--|
|standard|Un control estándar|
|iframe|Un control de IFRAME|
|kbsearch|Un control de búsqueda de knowledge base|
|búsqueda|Un control de búsqueda|
|conjunto de opciones de selección múltiple|Un control de conjunto de opciones de selección múltiple|
|notas|Un control de notas|
|optionset|Un control de conjunto de opciones|
|quickform | Un control de [vista rápida](../formContext-ui-quickForms.md)|
|subgrid | Un control de [subcuadrícula](../grids.md)|
|timercontrol | Un control de temporizador|
|timelinewall | Un control de escala de tiempo (para una interfaz unificada)|
|webresource | Un control de recurso web|
|customcontrol: \<*namespace*>.\<*name*> | Un control personalizado para clientes móviles de Dynamics 365 (teléfonos y tabletas)|
|customsubgrid:\<*namespace*>.\<*name*> | Un control de conjunto de datos personalizado para clientes móviles de Dynamics 365 (teléfonos y tabletas)|

### <a name="related-topics"></a>Temas relacionados

[Controles](../controls.md)

[getControl](getcontrol.md)


