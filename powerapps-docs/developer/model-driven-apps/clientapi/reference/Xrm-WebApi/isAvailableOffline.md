---
title: isAvailableOffline (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: ea9eacc0-2e31-49f4-a329-dcdf430a5a7e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isavailableoffline-client-api-reference"></a>isAvailableOffline (referencia de la API de cliente)



[!INCLUDE[./includes/isAvailableOffline-description.md](./includes/isAvailableOffline-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.WebApi.offline.isAvailableOffline(entityLogicalName);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Obligatoria</th>
<th>Descripción</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>String</td>
<td>Sí</td>
<td>Nombre lógico de la entidad. Por ejemplo: "cuenta".</td>
</tr>

</table>

## <a name="return-value"></a>Valor devuelto

**Tipo**: Booleano.

**Descripción**: true si la entidad está presente en el perfil de usuario y actualmente está disponible para su uso en modo sin conexión; en caso contrario false.

[Xrm.WebApi.offline](offline.md)

[Xrm.WebApi](../xrm-webapi.md)




