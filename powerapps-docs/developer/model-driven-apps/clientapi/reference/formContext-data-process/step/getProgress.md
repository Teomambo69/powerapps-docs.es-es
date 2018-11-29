---
title: getProgress (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 56502c8b-af23-40d1-ad97-e780bb757d6d
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getprogress-client-api-reference"></a>getProgress (referencia de la API de cliente)



[!INCLUDE[./includes/getProgress-description.md](./includes/getProgress-description.md)]

## <a name="syntax"></a>Sintaxis

`var stepProgress = stepObj.getProgress();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: número. 

**Descripción**: devuelve uno de los siguientes valores:

|Value |Descripción|
|--|--|
|0|Ninguna|
|1|Procesando|
|2|Completado|
|3|Error|
|4|No válido|

## <a name="remarks"></a>Comentarios

Este método se admite solo para los pasos de acción; no para los pasos de datos. Los pasos de acción son botones de las fases de proceso de negocio en los que los usuarios pueden hacer clic para desencadenar una acción o un flujo de trabajo a petición. Paso de acción es una característica en vista previa que se introdujo en la versión v9.0. Más información: consulte la sección **Automatización de flujos de proceso de negocio con pasos de acción** en [Blog: Nuevas características de automatización y visualización para flujos de proceso de negocio (vista previa pública)](https://blogs.msdn.microsoft.com/crm/2017/10/25/new-automation-and-visualization-features-for-business-process-flows-public-preview/)

### <a name="related-topics"></a>Temas relacionados

[setProgress](setprogress.md)

[formContext.data.process](../../formContext-data-process.md)
 


