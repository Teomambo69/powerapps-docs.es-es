---
title: getGlobalContext.client (referencia API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontextclient-client-api-reference"></a>getGlobalContext.client (referencia de la API de cliente)



Proporciona acceso a los métodos para determinar qué cliente se usa, si el cliente está conectado al servidor y qué tipo de dispositivo se está utilizando.

`var clientContext = Xrm.Utility.getGlobalContext().client`

Los siguientes métodos están disponibles para el contexto del cliente.

## <a name="getclient"></a>getClient

Devuelve un valor que indica el cliente en que se ejecuta el script. 

### <a name="syntax"></a>Sintaxis

`clientContext.getClient()`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: Los valores devueltos son:

Value |Cliente | 
|---|---|
|Web |Aplicación web|
|Web |Interfaz unificada|
|Outlook |Outlook |
|Móvil |Aplicación móvil |

## <a name="getclientstate"></a>getClientState

Devuelve un valor para indicar el estado del cliente.

### <a name="syntax"></a>Sintaxis

`clientContext.getClientState()`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: Los valores devueltos son:

Value |Cliente | 
|---|---|
|En línea |Aplicación web, Outlook, aplicación móvil, interfaz unificada|
|Desconectado |Outlook, aplicación móvil|

## <a name="getformfactor"></a>getFormFactor

Devuelve información acerca del tipo de dispositivo que el usuario está usando.

### <a name="syntax"></a>Sintaxis

`clientContext.getFormFactor()`

### <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: Los valores devueltos son:

Value |Factor de formulario | 
|---|---|
|0 |Desconocida|
|1 |Escritorio|
|2 |Tableta |
|3 |Número de teléfono |

## <a name="isoffline"></a>isOffline

Devuelve información si el servidor está en línea o sin conexión.

### <a name="syntax"></a>Sintaxis

`clientContext.isOffline()`

### <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: **true** si el servidor está sin conexión; **false** en caso contrario.

## <a name="related-topics"></a>Temas relacionados

[Configuración de organización](organizationSettings.md)

[Configuración de usuario](userSettings.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)

