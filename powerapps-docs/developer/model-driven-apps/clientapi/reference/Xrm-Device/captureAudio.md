---
title: captureAudio| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: fa39d18e-4b82-423a-84a0-e54450b7964e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="captureaudio-client-api-reference"></a>captureAudio (referencia de la API de cliente)



[!INCLUDE[./includes/captureAudio-description.md](./includes/captureAudio-description.md)]


## <a name="syntax"></a>Sintaxis

`Xrm.Device.captureAudio().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|successCallback |Función | Sí|Una función para llamar cuando se devuelve audio. Un objeto de audio codificado en base64 con los siguientes atributos se pasa a la función:<br/>- **fileContent**: el contenido del archivo de audio. String <br/>- **fileName**: nombre del archivo de audio. Cadena.<br/>- **fileSize**: tamaño del archivo de audio en KB. Número.<br/>- **mimeType**: tipo MIME del archivo de audio. Cadena.|
|errorCallback |Función | Sí|Una función para llamar cuando la operación tiene error. |
 

## <a name="return-value"></a>Valor devuelto
Si funciona, devuelve un objeto de audio codificado base64 con los atributos especificados previamente.

## <a name="remarks"></a>Comentarios
Este método solo es compatible para los clientes móviles.

### <a name="related-topics"></a>Temas relacionados
[Xrm.Device](../xrm-device.md)

