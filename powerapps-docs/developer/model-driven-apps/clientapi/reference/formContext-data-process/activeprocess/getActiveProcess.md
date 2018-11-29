---
title: getActiveProcess (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a977a250-b79f-4c88-a6af-776350b110f7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getactiveprocess-client-api-reference"></a>getActiveProcess (referencia de la API de cliente)



[!INCLUDE[./includes/getActiveProcess-description.md](./includes/getActiveProcess-description.md)]

## <a name="syntax"></a>Sintaxis

`var activeProcess = formContext.data.process.getActiveProcess();`

## <a name="return-value"></a>Valor devuelto

**Tipo:**: Proceso. 

**Descripción**: el proceso activo actual. Vea [Métodos de proceso](../../formContext-data-process.md#process-methods) para los métodos de acceso a las propiedades del proceso devuelto.

### <a name="related-topics"></a>Temas relacionados

[setActiveProcess)](setActiveProcess.md)

[formContext.data.process](../../formContext-data-process.md)
 


