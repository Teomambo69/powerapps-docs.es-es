---
title: getRelationship (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getrelationship-client-api-reference"></a>getRelationship (referencia de la API de cliente)



[!INCLUDE[./includes/getRelationship-description.md](./includes/getRelationship-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`gridContext.getRelationship();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto.

**Descripción**: objeto de relación con los siguientes atributos:
- **attributeName**: Cadena. Nombre del atributo.
- **nombre**: cadena. Nombre de la relación. 
- **navigationPropertyName**: Cadena. Nombre de la propiedad de navegación de esta relación.
- **relationshipType**: Número. Devuelve uno de los valores siguientes para indicar el tipo de relación:
    - 0: OneToMany
    - 1: ManyToMany
- **roleType**: Número. Devuelve uno de los valores siguientes para indicar el tipo de rol o de relación:
    - 1: Referencing
    - 2: AssociationEntity

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext).

### <a name="related-topics"></a>Temas relacionados

[openRelatedGrid](openRelatedGrid.md)

<!-- TODO:
[Customize entity relationship metadata](../../../../customize-entity-relationship-metadata.md) -->


