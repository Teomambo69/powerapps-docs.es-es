---
title: showProgressIndicator (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 36e17a06-e381-4efd-b3a6-62391377b613
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="showprogressindicator-client-api-reference"></a>showProgressIndicator (referencia de la API de cliente)



[!INCLUDE[./includes/showProgressIndicator-description.md](./includes/showProgressIndicator-description.md)]

Cualquier llamada posterior a este método actualizará el mensaje mostrado en el cuadro de diálogo de progreso existente con el mensaje especificado en la última llamada al método.

>[!WARNING]
>El cuadro de diálogo de progreso bloquea la UI hasta que es cerrada con el método [closeProgressIndicator](closeProgressIndicator.md). Así que debe usar este método con precaución.

## <a name="syntax"></a>Sintaxis

`Xrm.Utility.showProgressIndicator(message)`

## <a name="parameters"></a>Parámetros 

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|mensaje|String|Sí|El mensaje que se muestra en el cuadro de diálogo de progreso.|



### <a name="related-topics"></a>Temas relacionados

[closeProgressIndicator](closeProgressIndicator.md)

[Xrm.Utility](../xrm-utility.md)  



