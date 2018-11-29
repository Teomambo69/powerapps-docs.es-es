---
title: getEntityReference (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: b8e23eee-f20f-4db9-9cc6-7fa5dd7ce2bb
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentityreference-client-api-reference"></a>getEntityReference (referencia de la API de cliente)



[!INCLUDE[./includes/getEntityReference-description.md](./includes/getEntityReference-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`gridEntity.getEntityReference();`

## <a name="return-value"></a>Valor devuelto

**Tipo** de búsqueda

**Descripción**: Objeto de búsqueda que hace referencia el registro de la fila. El objeto tiene los siguientes atributos:
- **entityType**: cadena. El nombre lógico para el registro en la fila. Los mismos datos devueltos por el método **GridEntity**.[getEntityName](getEntityName.md).
- **id**: cadena. El identificador para el registro en la fila. Los mismos datos devueltos por el método **GridEntity**.[getId](getId.md).
- **nombre**: cadena. El valor del atributo principal del registro de la fila. Los mismos datos devueltos por el método **GridEntity**.[getPrimaryAttributeValue](getPrimaryAttributeValue.md).

## <a name="remarks"></a>Comentarios

Para obtener el objeto `gridEntity`, vea [GridEntity](../gridentity.md). 

