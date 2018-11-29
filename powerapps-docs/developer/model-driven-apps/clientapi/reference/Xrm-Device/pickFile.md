---
title: pickFile| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c777a0b8-2b07-458b-8a4f-8938f7a2e696
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="pickfile-client-api-reference"></a>pickFile (referencia de la API de cliente)



[!INCLUDE[./includes/pickFile-description.md](./includes/pickFile-description.md)]


## <a name="syntax"></a>Sintaxis

`Xrm.Device.pickFile(pickFileOptions).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|pickFileOptions |Objeto | No|Un objeto con los atributos siguientes:<br/>- **accept**: los tipos de archivo de imagen que seleccionar. Los valores válidos son "audio", "video" o "image". Cadena.<br/>- **allowMultipleFiles**: indica si se pueden seleccionar varios archivos. Booleano.<br/>- **maximumAllowedFileSize**: tamaño máximo de los archivos que seleccionar. Número.|
|successCallback |Función | Sí|Función a la que llamar cuando se devuelven los archivos seleccionados. Se pasa a la función una matriz de objetos con *cada* objeto con los atributos siguientes:<br/>- **fileContent**: el contenido del archivo. String <br/>- **fileName**: nombre del archivo. Cadena.<br/>- **fileSize**: tamaño del archivo en KB. Número.<br/>- **mimeType**: tipo de archivo MIME. Cadena.|
|errorCallback |Función | Sí|Una función para llamar cuando la operación tiene error. |
 

## <a name="return-value"></a>Valor devuelto
Si funciona, devuelve una promesa con matriz de objetos como se haya especificado anteriormente para la función **successCallback**.

### <a name="related-topics"></a>Temas relacionados
[Xrm.Device](../xrm-device.md)

