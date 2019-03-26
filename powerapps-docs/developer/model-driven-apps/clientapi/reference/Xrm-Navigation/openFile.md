---
title: openFile (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 01/25/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 6a2497fe-08ad-4953-b3ff-44c72bc25082
author: KumarVivek
ms.author: kvivek
manager: annbe
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
|openFileOptions |Objeto | No|Un objeto que describe si abrir o guardar el archivo. El objeto tiene los siguientes atributos.<br/>- **openMode**: especifique `1` para abrir; `2` para guardar. <br/>Si no especifica este parámetro, se pasa a `1` (abrir) de forma predeterminada.<br/>Este parámetro solo se admite en la Interfaz unificada.|

### <a name="related-topics"></a>Temas relacionados

[Xrm.Navigation](../xrm-navigation.md)
