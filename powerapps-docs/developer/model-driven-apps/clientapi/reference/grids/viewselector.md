---
title: Métodos ViewSelector (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 37fbabaf-e2ce-4e46-a54e-e46bd884197b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="viewselector-methods-client-api-reference"></a>Métodos ViewSelector (Referencia de API de cliente)



Proporciona métodos para obtener o para establecer la información sobre el selector de vistas del control de subcuadrícula. Si el control de subcuadrícula no está configurado para mostrar el selector de vistas, al llamar a los métodos **ViewSelector** se producirá un error.

ViewSelector está disponible solo para cuadrículas de solo lectura. ViewSelector se devuelve por el método **gridContext**.[getViewSelector](gridcontrol/getViewSelector.md) .

```JavaScript
var viewSelector = gridContext.getViewSelector();
```

Métodos

|Nombre|Descripción|Disponible para|
|--|--|--|
|[getCurrentView](viewselector/getCurrentView.md)|[!INCLUDE[viewselector/includes/getCurrentView-description.md](viewselector/includes/getCurrentView-description.md)]|Cuadrícula de solo lectura|
|[isVisible](viewselector/isVisible.md)|[!INCLUDE[viewselector/includes/isVisible-description.md](viewselector/includes/isVisible-description.md)]|Cuadrícula de solo lectura|
|[setCurrentView](viewselector/setCurrentView.md)|[!INCLUDE[viewselector/includes/setCurrentView-description.md](viewselector/includes/setCurrentView-description.md)]|Cuadrícula de solo lectura|


### <a name="related-topics"></a>Temas relacionados

[gridContext](../grids.md#bkmk_gridcontext)

[Cuadrículas y subcuadrículas en aplicaciones basadas en modelos](../grids.md)


