---
title: captureVideo | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9580d05a-a91f-4126-b94b-4d1068da35fa
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="capturevideo-client-api-reference"></a>captureVideo (referencia de la API de cliente)



[!INCLUDE[./includes/captureVideo-description.md](./includes/captureVideo-description.md)]


## <a name="syntax"></a>Sintaxis

`Xrm.Device.captureVideo().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|successCallback |Función | Sí|Una función para llamar cuando se devuelve vídeo. Un objeto de vídeo codificado en base64 con los siguientes atributos se pasa a la función:<br/>- **fileContent**: el contenido del archivo de vídeo. String <br/>- **fileName**: nombre del archivo de vídeo. Cadena.<br/>- **fileSize**: tamaño del archivo de vídeo en KB. Número.<br/>- **mimeType**: tipo MIME del archivo de vídeo. Cadena.|
|errorCallback |Función | Sí|Una función para llamar cuando la operación tiene error. |
 

## <a name="return-value"></a>Valor devuelto
Si funciona, devuelve un objeto de vídeo codificado base64 con los atributos especificados previamente.

## <a name="remarks"></a>Comentarios
Este método solo es compatible para los clientes móviles.

### <a name="related-topics"></a>Temas relacionados
[Xrm.Device](../xrm-device.md)

