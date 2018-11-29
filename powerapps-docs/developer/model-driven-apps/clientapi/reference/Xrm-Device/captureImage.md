---
title: captureImage | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1b24e8b2-20af-4e75-8c00-1aa393c07aef
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="captureimage-client-api-reference"></a>captureImage (referencia de la API de cliente)



[!INCLUDE[./includes/captureImage-description.md](./includes/captureImage-description.md)]


## <a name="syntax"></a>Sintaxis

`Xrm.Device.captureImage(imageOptions).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|imageOptions |Objeto | No|Un objeto con los atributos siguientes:<br/>- **allowEdit**: indica si editar la imagen antes de guardar. Booleano.<br/>- **height**: altura de la imagen que capturar. Número.<br/>- **preferFrontCamera**: indica si se va a capturar la imagen con la cámara delantera del dispositivo. Booleano.<br/>- **quality**: calidad del archivo de imagen en porcentaje. Número.<br/>- **width**: anchura de la imagen que capturar. Número.|
|successCallback |Función | Sí|Una función para llamar cuando se devuelve una imagen. Un objeto de imagen codificado en base64 con los siguientes atributos se pasa a la función:<br/>- **fileContent**: el contenido del archivo de imagen. String <br/>- **fileName**: nombre del archivo de imagen. Cadena.<br/>- **fileSize**: tamaño del archivo de imagen en KB. Número.<br/>- **mimeType**: tipo MIME de archivo de imagen. Cadena.|
|errorCallback |Función | Sí|Una función para llamar cuando la operación tiene error. |
 

## <a name="return-value"></a>Valor devuelto
Si funciona, devuelve un objeto de imagen codificado base64 con los atributos especificados previamente.

## <a name="remarks"></a>Comentarios
Este método solo es compatible para los clientes móviles.

### <a name="related-topics"></a>Temas relacionados
[Xrm.Device](../xrm-device.md)

