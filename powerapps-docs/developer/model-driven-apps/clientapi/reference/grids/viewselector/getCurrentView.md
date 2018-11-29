---
title: getCurrentView (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
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
# <a name="getcurrentview-client-api-reference"></a>getCurrentView (referencia de la API de cliente)



[!INCLUDE[./includes/getCurrentView-description.md](./includes/getCurrentView-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrícula de solo lectura

## <a name="syntax"></a>Sintaxis

`viewSelector.getCurrentView();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto de búsqueda

**Descripción**: el objeto de búsqueda tiene los siguientes atributos:

- **entityType**: Número. El código de tipo de objeto para SavedQuery (1039) o UserQuery (4230) que representa la vista que el usuario puede seleccionar.
- **id**: cadena. El identificador de la vista que el usuario puede seleccionar.
- **nombre**: cadena. El nombre de la vista que el usuario puede seleccionar.

## <a name="remarks"></a>Comentarios

Si el control de subcuadrícula no está configurado para mostrar el selector de vistas, al llamar a este método en el objeto `viewSelector` producirá un error.

Para obtener el objeto `viewSelector`, vea [ViewSelector](../viewselector.md).



