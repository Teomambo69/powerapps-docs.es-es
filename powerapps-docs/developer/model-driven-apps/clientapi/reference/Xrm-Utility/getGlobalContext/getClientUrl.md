---
title: getClientUrl (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getclienturl-client-api-reference"></a>getClientUrl (referencia de la API de cliente)



Devuelve la dirección URL base que se usó para acceder a la aplicación.

## <a name="syntax"></a>Sintaxis

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getClientUrl();
``` 

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: los valores devueltos se asemejarán a los que se muestran en la tabla siguiente.

|Value |Cliente |
|---|---|
|https://[org].crm.dynamics.com|aplicaciones basadas en modelos (en línea)|
|http(s)://[server]/[org]|aplicaciones basadas en modelos (local)|
|http://localhost:2525|aplicaciones basadas en modelos para Outlook con acceso sin conexión cuando está sin conexión|

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)





