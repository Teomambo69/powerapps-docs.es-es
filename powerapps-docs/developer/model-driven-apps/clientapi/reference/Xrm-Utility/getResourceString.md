---
title: getResourceString (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d5e51eac-ce0a-4f4a-b7b6-495433e3f8c1
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getresourcestring-client-api-reference"></a>getResourceString (referencia de la API de cliente)



[!INCLUDE[./includes/getResourceString-description.md](./includes/getResourceString-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.Utility.getResourceString(webResourceName,key)` 

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|webResourceName|String|Sí|Nombre del recurso web.|
|tecla|String|Sí|Clave para la cadena traducida.|

## <a name="return-value"></a>Valor devuelto

Cadena traducida.

## <a name="remarks"></a>Comentarios

<!-- 
Content adapted from /developer/resx-web-resources 
If you change this, make sure that topic is in sync.
-->

Cuando se crean recursos web RESX es necesario establecer explícitamente el valor de idioma e incluir el identificador local (LCID) para el idioma correspondiente en el nombre del recurso web. Por ejemplo, `new_/strings/MyAppResources.1033.resx` contendría recursos para el idioma inglés. Consulte [Valores de identificadores de configuración regional de Microsoft](https://msdn.microsoft.com/library/ms912047(WinEmbedded.10).aspx) para ver la lista de valores LCID.

Por ejemplo, `Xrm.Utility.getResourceString("new_/strings/MyAppResources","hello")` devolverá el valor de la cadena traducida para la clave del recurso `hello` dentro del recurso web `new_/strings/MyAppResources.1033.resx` si el idioma preferido del usuario es el inglés. Tenga en cuenta que la función no hace referencia a ningún idioma específico o ningún nombre completo de recurso web RESX. Esta funcionalidad depende del recurso web RESX que se esté asociando al recurso web JavaScript que realiza la llamada como dependencia. Más información: [Dependencias de recursos web](../../../web-resource-dependencies.md).

El valor de cadena correspondiente vendrá determinado por la preferencia de idioma del usuario y los idiomas disponibles en la organización. Si no se encuentra una cadena traducida que coincida con las preferencias de idioma del usuario, la cadena traducida se revertirá automáticamente al idioma base de la organización. Si no se encuentra ninguna cadena traducida que coincida con el idioma base de la organización, se devolverá un valor nulo.

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility](../xrm-utility.md)<br />
[Recursos web de cadena (RESX)](../../../resx-web-resources.md)<br />
[Dependencias de recursos web](../../../web-resource-dependencies.md)



