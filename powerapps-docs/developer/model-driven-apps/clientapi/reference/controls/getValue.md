---
title: getValue (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="getvalue-client-api-reference"></a>getValue (referencia de la API de cliente)



Obtiene el último valor de un control a medida que el usuario escribe caracteres en un campo específico de texto o de número. Este método le ayuda a crear experiencias interactivas validando datos y alertando a los usuarios a medida que escriben caracteres en un control.

El método getValue es diferente del método [getValue](../attributes/getvalue.md) del atributo porque el método de control recupera el valor del control cuando el usuario escribe en el control, mientras que el método getValue del atributo recupera el valor después de que el usuario confirma (guarda) el campo. 

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getValue();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: el último valor de datos de un control.

