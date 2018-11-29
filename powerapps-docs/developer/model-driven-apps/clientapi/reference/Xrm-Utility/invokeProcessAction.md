---
title: invokeProcessAction (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e71012ba-249d-4ae7-8891-f7d3ae16a20a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="invokeprocessaction-client-api-reference"></a>invokeProcessAction (referencia de la API de cliente)



[!INCLUDE[./includes/invokeProcessAction-description.md](./includes/invokeProcessAction-description.md)] 

Para obtener más información acerca de las acciones, consulte [Usar acciones](/flow/actions)

## <a name="syntax"></a>Sintaxis

`Xrm.Utility.invokeProcessAction(name,parameters).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

|Nombre |Escriba |Requerido |Descripción |
|---|---|---|---|
|nombre|String|Sí|Nombre de la acción del proceso al que se va a llamar.|
|parámetros|objeto|No|Objeto que contiene parámetros de entrada de la acción. Defina un objeto utilizando pares de elementos `key:value`, donde `key` es de tipo **cadena**.|
|successCallback |Función |Sí |Función a la que se llama cuando se llama a la acción.  |
|errorCallback |Función |Sí |Una función para llamar cuando la operación tiene error.  |

## <a name="returns"></a>Devuelve

Si funciona, devuelve el resultado de la API web junto con el resultado de la acción.

### <a name="related-topics"></a>Temas relacionados

[Usar acciones](/flow/actions)

[Xrm.Utility](../xrm-utility.md)


