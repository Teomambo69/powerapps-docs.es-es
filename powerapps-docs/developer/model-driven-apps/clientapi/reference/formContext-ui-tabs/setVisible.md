---
title: setVisible (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 485d9843-5907-49e4-971b-0e86f3bd1eb8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setvisible-client-api-reference"></a>setVisible (referencia de la API de cliente)



[!INCLUDE[./includes/setVisible-description.md](./includes/setVisible-description.md)] 

## <a name="syntax"></a>Sintaxis

`tabObj.setVisible(bool);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|bool|Boolean|Sí|Especifique **true** para mostrar la pestaña; **false** para ocultarla.|

## <a name="remarks"></a>Comentarios

Otra forma de ocultar una pestaña es ocultar todas las secciones que contiene. Si todas las secciones de una pestaña no están visibles, la pestaña no estará visible.

### <a name="related-topics"></a>Temas relacionados

[getVisible](getVisible.md)



