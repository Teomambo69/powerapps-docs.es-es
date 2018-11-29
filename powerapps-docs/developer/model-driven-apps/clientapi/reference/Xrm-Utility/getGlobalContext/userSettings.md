---
title: getGlobalContext.userSettings (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 44296667-f1cd-49be-a300-7259bc3b41e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontextusersettings-client-api-reference"></a>getGlobalContext.userSettings (Referencia de API de cliente)



Devuelve la información sobre la configuración del usuario actual.

`var userSettings = Xrm.Utility.getGlobalContext().userSettings`

El objeto **userSettings** proporciona las siguientes propiedades y un método.

## <a name="dateformattinginfo"></a>dateFormattingInfo 

Devuelve la información del formato de fecha para el usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.dateFormattingInfo`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: un objeto con información sobre el formato de fecha como **FirstDayOfWeek**, **LongDatePattern**, **MonthDayPattern**, **TimeSeparator**, etc.

## <a name="defaultdashboardid"></a>defaultDashboardId 

Devuelve el Id. del panel predeterminado para el usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.defaultDashboardId`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: Id. del panel predeterminado. 

## <a name="isguidedhelpenabled"></a>isGuidedHelpEnabled 

Indica si la ayuda guiada está habilitada para el usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.isGuidedHelpEnabled`

### <a name="return-value"></a>Valor devuelto

**Tipo:** Booleano

**Descripción**: verdadero si se habilita; falso en caso contrario. 

## <a name="ishighcontrastenabled"></a>isHighContrastEnabled 

Indica si el contraste alto está habilitado para el usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.isHighContrastEnabled`

### <a name="return-value"></a>Valor devuelto

**Tipo:** Booleano

**Descripción**: verdadero si se habilita; falso en caso contrario.

## <a name="isrtl"></a>isRTL 

Indica si el idioma para el usuario actual es un idioma que se escribe de derecha a izquierda (RTL).

### <a name="syntax"></a>Sintaxis

`userSettings.isRTL`

### <a name="return-value"></a>Valor devuelto

**Tipo:** Booleano

**Descripción**: verdadero si es RTL; falso en caso contrario.

## <a name="languageid"></a>languageId 

Devuelve el Id. de idioma para el usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.languageId`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: Id. de idioma.

## <a name="securityroleprivileges"></a>securityRolePrivileges 

Devuelve una matriz de cadenas que represente los valores de GUID de cada privilegio de rol de seguridad con el que está asociado el usuario o cualquier equipo al que está asociado el usuario.

### <a name="syntax"></a>Sintaxis

`userSettings.securityRolePrivileges`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Matriz

**Descripción**: valores GUID de cada uno de los privilegios de rol de seguridad.

## <a name="securityroles"></a>securityRoles 

Devuelve una matriz de cadenas que represente los valores de GUID del rol de seguridad con el que está asociado el usuario o cualquier equipo al que está asociado el usuario.

### <a name="syntax"></a>Sintaxis

`userSettings.securityRoles`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Matriz

**Descripción**: valores GUID de cada rol de seguridad. Por ejemplo:

`["0d3dd20a-17a6-e711-a94e-000d3a1a7a9b", "ff42d20a-17a6-e711-a94e-000d3a1a7a9b"]`

## <a name="transactioncurrencyid"></a>transactionCurrencyId 

Devuelve el Id. de la divisa de la transacción para el usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.transactionCurrencyId`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: Id. de la divisa de la transacción.

## <a name="userid"></a>userId 

Devuelve el GUID del valor de **SystemUser.Id** para el usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.userId`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: el Id. del usuario. Por ejemplo:

`"{75B5BA27-FD41-4D45-8E3A-C8446C95F0CC}"`

## <a name="username"></a>userName 

Devuelve el nombre del usuario actual.

### <a name="syntax"></a>Sintaxis

`userSettings.userName`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: nombre del usuario actual.

## <a name="gettimezoneoffsetminutes-method"></a>Método getTimeZoneOffsetMinutes

Devuelve la diferencia en minutos entre la hora local y el Horario universal coordinado (UTC).

### <a name="syntax"></a>Sintaxis

`userSettings.getTimeZoneOffsetMinutes()`

### <a name="return-value"></a>Valor devuelto

**Tipo**: número

**Descripción**: desplazamiento de huso horario en minutos.

## <a name="related-topics"></a>Temas relacionados

[Contexto de cliente](client.md)

[Configuración de organización](organizationSettings.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)

