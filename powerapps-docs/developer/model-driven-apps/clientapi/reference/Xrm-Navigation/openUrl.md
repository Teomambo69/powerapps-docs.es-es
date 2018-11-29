---
title: openUrl (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 29cb3685-21aa-42fc-8e84-0074dcc69197
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openurl-client-api-reference"></a>openUrl (referencia de la API de cliente)



[!INCLUDE[./includes/openUrl-description.md](./includes/openUrl-description.md)]

## <a name="syntax"></a>Sintaxis

`Xrm.Navigation.openUrl(url,openUrlOptions)`

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|dirección url|String|Sí|Dirección URL que se va a abrir.|
|openUrlOptions|Objeto|No|Opciones para abrir la dirección URL. El objeto contiene los atributos siguientes:<br/>- **height**: número (opcional). Alto de la ventana para mostrar la página resultante, en píxeles.<br/>- **width**: número (opcional). Ancho de la ventana para mostrar la página resultante, en píxeles.|

## <a name="remarks"></a>Comentarios

Este método es muy útil para que los clientes móviles abran una dirección URL en un explorador sin correcciones de compatibilidad (shim).

 ### <a name="related-topics"></a>Temas relacionados

[Xrm.Navigation](../xrm-navigation.md)

