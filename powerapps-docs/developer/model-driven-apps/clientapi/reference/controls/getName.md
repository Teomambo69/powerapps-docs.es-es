---
title: getName (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="getname-client-api-reference"></a>getName (referencia de la API de cliente)



Devuelve el nombre asignado al control.

>[!NOTE]
>El nombre asignado a un control no se determina hasta que el formulario se carga. Los cambios en el formulario pueden cambiar el nombre asignado a un determinado control. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getName();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: el nombre del control.

### <a name="related-topics"></a>Temas relacionados

[Controles](../controls.md)

