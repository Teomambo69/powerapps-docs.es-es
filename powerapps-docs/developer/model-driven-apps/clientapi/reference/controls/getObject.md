---
title: getObject (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: ad68d177-3715-468e-b4af-8cf9b3c77799
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getobject-client-api-reference"></a>getObject (referencia de la API de cliente)



Devuelve el objeto del formulario que representa un IFRAME o un recurso web. 

## <a name="control-types-supported"></a>Tipos de control admitidos

iframe, webresource

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getObject();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: el objeto depende del tipo de control:
- Un IFRAME devuelve el elemento [IFrame](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) del Document Object Model (DOM).
- Un recurso web de Silverlight devolverá el elemento [Object](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object) del DOM que representa el complemento Silverlight incrustado.



