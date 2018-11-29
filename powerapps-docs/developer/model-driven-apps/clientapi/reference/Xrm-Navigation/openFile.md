---
title: openFile (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6a2497fe-08ad-4953-b3ff-44c72bc25082
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openfile-client-api-reference"></a>openFile (referencia de la API de cliente)



[!INCLUDE[./includes/openFile-description.md](./includes/openFile-description.md)]

## <a name="syntax"></a>Sintaxis

`Xrm.Navigation.openFile(file,openFileOptions)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|archivo |Objeto | Sí|Un objeto que describe el archivo que se va a abrir. El objeto tiene los siguientes atributos:<br/>- **fileContent**: cadena. Contenido del archivo.  <br/>- **fileName**: cadena. Nombre del archivo.<br/>- **fileSize**: número. Tamaño del archivo en KB.<br/>- **mimeType**: cadena. Tipo MIME del archivo.|
|openFileOptions |Número | No|Especifique si se abre o se guarda el archivo:<br/> `1:Open`<br/> `2:Save`<br/>Si no especifica este parámetro, se pasa **1** (abrir) de forma predeterminada.|

### <a name="related-topics"></a>Temas relacionados

[Xrm.Navigation](../xrm-navigation.md)
