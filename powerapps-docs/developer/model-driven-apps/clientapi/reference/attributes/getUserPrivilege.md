---
title: getUserPrivilege (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0a3f0349-af9a-418a-b99d-5085999884eb
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getuserprivilege-client-api-reference"></a>getUserPrivilege (referencia de la API de cliente)



Devuelve un objeto con tres propiedades booleanas correspondientes a privilegios que indican si el usuario puede crear, leer o actualizar los valores de los datos de un atributo. Esta funcionalidad se usa cuando la seguridad de nivel de campo modifica los privilegios de un usuario para un atributo determinado. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getUserPrivilege()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto. 

**Descripción**: el objeto tiene tres propiedades booleanas:
- canRead
- canUpdate
- canCreate

