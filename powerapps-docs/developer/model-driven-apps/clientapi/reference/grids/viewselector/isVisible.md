---
title: isVisible (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d22cd046-064c-47ef-9e46-5cc4c8b6e280
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isvisible-client-api-reference"></a>isVisible (referencia de la API de cliente)



[!INCLUDE[./includes/isVisible-description.md](./includes/isVisible-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrícula de solo lectura

## <a name="syntax"></a>Sintaxis

`viewSelector.isVisible();`

## <a name="return-value"></a>Valor devuelto

**Tipo:** Booleano

**Descripción**: verdadero si está visible; falso en caso contrario.

## <a name="remarks"></a>Comentarios

Si el control de subcuadrícula no está configurado para mostrar el selector de vistas, al llamar a este método en el **ViewSelector** devuelto por el método GridControl.getViewSelector, se producirá un error.

Para obtener el objeto `viewSelector`, vea [ViewSelector](../viewselector.md).



