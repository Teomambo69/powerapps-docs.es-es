---
title: getGlobalContext.organizationSettings (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: badf4f82-cb47-4864-aa43-bb777d04de4d
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontextorganizationsettings-client-api-reference"></a>getGlobalContext.organizationSettings (referencia de la API de cliente)



Devuelve la información sobre la configuración de la organización actual. 

`var organizationSettings = Xrm.Utility.getGlobalContext().organizationSettings`

El objeto **organizationSettings** proporciona las siguientes propiedades.

## <a name="attributes"></a>atributos

Devuelve atributos y sus valores como pares `key:value` que están disponibles para la entidad de organización. Los valores adicionales estarán disponibles como atributos si se especifican como dependencias de atributo en la lista de dependencias de recursos web. `key` será el nombre lógico del atributo.

### <a name="syntax"></a>Sintaxis

`organizationSettings.attributes`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: un objeto con atributos y sus valores.

## <a name="basecurrencyid"></a>baseCurrencyId 

Devuelve el id. de la divisa base para la organización actual.

### <a name="syntax"></a>Sintaxis

`organizationSettings.baseCurrencyId`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: id. de la divisa base.

## <a name="defaultcountrycode"></a>defaultCountryCode 

Devuelve el código de país o región predeterminado para los números de teléfono de la organización actual.

### <a name="syntax"></a>Sintaxis

`organizationSettings.defaultCountryCode`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: código de país o región predeterminado para números de teléfono.

## <a name="isautosaveenabled"></a>isAutoSaveEnabled 

Indica si la opción de guardado automático está habilitada para la organización actual.

### <a name="syntax"></a>Sintaxis

`organizationSettings.isAutoSaveEnabled`

### <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: **true** si se habilita; **false** en caso contrario.

## <a name="languageid"></a>languageId 

Devuelve el identificador de idioma preferido para la organización actual.

### <a name="syntax"></a>Sintaxis

`organizationSettings.languageId`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: id. de idioma preferido. Por ejemplo:

`1033`

## <a name="organizationid"></a>organizationId 

Devuelve el id. de la organización actual.

### <a name="syntax"></a>Sintaxis

`organizationSettings.organizationId`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: id. de la organización actual.

## <a name="uniquename"></a>uniqueName 

Devuelve el nombre único de la organización actual.

### <a name="syntax"></a>Sintaxis

`organizationSettings.uniqueName`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: el nombre único de la organización actual.

## <a name="useskypeprotocol"></a>useSkypeProtocol 

Indica si se usa el protocolo Skype para la organización actual.

### <a name="syntax"></a>Sintaxis

`organizationSettings.useSkypeProtocol`

### <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: **true** si se usa el protocolo Skype; **false** en caso contrario.


## <a name="related-topics"></a>Temas relacionados

[Contexto de cliente](client.md)

[Configuración de usuario](userSettings.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)