---
title: getCurrentAppUrl (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
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
# <a name="getcurrentappurl-client-api-reference"></a>getCurrentAppUrl (referencia de la API de cliente)



Devuelve la dirección URL de la aplicación de negocio actual de las aplicaciones basadas en modelos.

## <a name="syntax"></a>Sintaxis

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getCurrentAppUrl();
``` 

## <a name="return-value"></a>Valor de retorno

**Tipo**: Cadena

**Descripción**: dirección URL de la aplicación de negocio actual. Posibles valores devueltos:

|Value |Cliente |
|---|---|
|https://[org].crm.dynamics.com/main.aspx?appid=[GUID]|aplicaciones basadas en modelos (en línea)|
|https://[server]/[org]/main.aspx?appid=[GUID]|aplicaciones basadas en modelos (local)|

### <a name="related-topics"></a>Temas relacionados

[Crear, administrar, y publicar aplicaciones basadas en modelos con código](../../../../create-manage-model-driven-apps-using-code.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md) 



