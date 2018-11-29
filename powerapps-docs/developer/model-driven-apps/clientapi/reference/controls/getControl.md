---
title: getControl (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 34715e1f-35c0-4b7f-971e-e0a6518f0722
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcontrol-client-api-reference"></a>getControl (referencia de la API de cliente)



Obtiene un control en el formulario. 

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg);`

El método **formContext.getControl(arg)** es un acceso directo para acceder a **formContext.ui.controls.get**.

## <a name="parameter"></a>Parámetro

**arg**: opcional. Puede acceder a un control de un formulario si pasa un argumento como el **nombre** o el **valor de índice** del control en un formulario. Por ejemplo, `formContext.getControl("firstname")` o `formContext.getControl(0)`


## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto o colección de objetos.

**Descripción**: un objeto si usa el método con parámetros; una colección de objetos si usa el método sin parámetros.



### <a name="related-topics"></a>Temas relacionados

[formContext](../../clientapi-form-Context.md)



