---
title: openSearchResult (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1f9169ce-cba3-4bb6-af20-f86140139cfe
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="opensearchresult-client-api-reference"></a>openSearchResult (referencia de la API de cliente)



Abre un resultado de la búsqueda en el control de búsqueda especificando el número de resultado. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
var openResultStatus = kbSearchControl.openSearchResult(resultNumber, mode);
```

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|resultNumber|Número|Sí|Valor numérico que especifica el número de resultado que se abrirá. El número de resultado empieza en 1.|
|mode|String|No|Especifique "Inline" o "Popout". Si no especifica un valor para el argumento, se usa la opción predeterminada ("Inline").<br/><br/>El modo "Inline" abrirá el resultado en línea en el panel de lectura del control o en una pestaña del panel de referencia en caso del panel de referencia. El modo "Popout" abre el resultado en una ventana emergente.|

## <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: estado de apertura del resultado de la búsqueda especificado. Devuelve 1 si es correcto; 0 si es error. El método devolverá -1 si el valor resultNumber especificado no está presente o si el valor mode especificado no es válido.