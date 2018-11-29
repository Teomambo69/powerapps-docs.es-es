---
title: getCurrentAppProperties (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5f8d91ff-ba0d-4e90-a79a-18e32d09baa3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcurrentappproperties-client-api-reference"></a>getCurrentAppProperties (referencia de la API de cliente)



Devuelve las propiedades de la aplicación de negocio actual de las aplicaciones basadas en modelos.

## <a name="syntax"></a>Sintaxis

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getCurrentAppProperties().then(successCallback, errorCallback);
``` 

## <a name="parameters"></a>Parámetros

|Nombre |Escriba |Requerido |Descripción |
|---|---|---|---|
|successCallback |Función |Sí |Una función a la que se llama cuando se devuelve información de propiedades de la aplicación de negocio. Un objeto con los siguientes atributos (propiedades de aplicacion) se pasa a la función:<br/>- **appId**<br/>- **displayName**<br/>- **uniqueName**<br/>- **url**<br/>- **webResourceId**<br/>- **webResourceName**<br/>- **welcomePageId**<br/>- **welcomePageName**|
|errorCallback |Función |Sí |Una función para llamar cuando la operación tiene error.  |

## <a name="return-value"></a>Valor devuelto

Si se llama a este método en el contexto de una aplicación de negocio, devuelve las propiedades de esa aplicación. De lo contrario, se produce un error.

### <a name="related-topics"></a>Temas relacionados

[Crear, administrar, y publicar aplicaciones basadas en modelos con código](../../../../create-manage-model-driven-apps-using-code.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md) 



