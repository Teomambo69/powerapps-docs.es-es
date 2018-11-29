---
title: formContext.ui.tabs (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Aprenda a trabajar con procesos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1888a882-7dfc-41a8-9bb4-d693d6046666
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuitabs-client-api-reference"></a>formContext.ui.tabs (referencia de la API de cliente)



Una pestaña es un grupo de secciones en una página. Contiene propiedades y métodos para manipular pestañas, así como el acceso a las secciones de la pestaña a través de la recopilación de secciones.

Puede recuperar un objeto de pestaña (por ejemplo, **tabObj**) con el código de ejemplo siguiente:

```JavaScript
var tabObj = formContext.ui.tabs.get(arg);
```

## <a name="properties"></a>Propiedades

- **Secciones**: la recopilación de secciones proporciona acceso a las secciones de la pestaña. Vea [Recopilaciones (referencia de la API de cliente)](collections.md) para obtener información sobre métodos para acceder a las secciones de la recopilación. Vea [Sección formContext.ui](formContext-ui-sections.md) para obtener información acerca de las propiedades y métodos de los objetos de la sección en la recopilación.

## <a name="methods"></a>Métodos

|Nombre | Descripción |
|--|--|
|[addTabStateChange](formcontext-ui-tabs/addTabStateChange.md)|[!INCLUDE[formcontext-ui-tabs/includes/addTabStateChange-description.md](formcontext-ui-tabs/includes/addTabStateChange-description.md)]|
|[getDisplayState](formcontext-ui-tabs/getDisplayState.md)|[!INCLUDE[formcontext-ui-tabs/includes/getDisplayState-description.md](formcontext-ui-tabs/includes/getDisplayState-description.md)]|
|[getLabel](formcontext-ui-tabs/getLabel.md)|[!INCLUDE[formcontext-ui-tabs/includes/getLabel-description.md](formcontext-ui-tabs/includes/getLabel-description.md)]|
|[getName](formcontext-ui-tabs/getName.md)|[!INCLUDE[formcontext-ui-tabs/includes/getName-description.md](formcontext-ui-tabs/includes/getName-description.md)]|
|[getParent](formcontext-ui-tabs/getParent.md)|[!INCLUDE[formcontext-ui-tabs/includes/getParent-description.md](formcontext-ui-tabs/includes/getParent-description.md)]|
|[getVisible](formcontext-ui-tabs/getVisible.md)|[!INCLUDE[formcontext-ui-tabs/includes/getVisible-description.md](formcontext-ui-tabs/includes/getVisible-description.md)]|
|[removeTabStateChange](formcontext-ui-tabs/removeTabStateChange.md)|[!INCLUDE[formcontext-ui-tabs/includes/removeTabStateChange-description.md](formcontext-ui-tabs/includes/removeTabStateChange-description.md)]|
|[setDisplayState](formcontext-ui-tabs/setDisplayState.md)|[!INCLUDE[formcontext-ui-tabs/includes/setDisplayState-description.md](formcontext-ui-tabs/includes/setDisplayState-description.md)]|
|[setFocus](formcontext-ui-tabs/setFocus.md)|[!INCLUDE[formcontext-ui-tabs/includes/setFocus-description.md](formcontext-ui-tabs/includes/setFocus-description.md)]|
|[setLabel](formcontext-ui-tabs/setLabel.md)|[!INCLUDE[formcontext-ui-tabs/includes/setLabel-description.md](formcontext-ui-tabs/includes/setLabel-description.md)]|
|[setVisible](formcontext-ui-tabs/setVisible.md)|[!INCLUDE[formcontext-ui-tabs/includes/setVisible-description.md](formcontext-ui-tabs/includes/setVisible-description.md)]|

### <a name="related-topics"></a>Temas relacionados

[formcontext.ui.tabs](formcontext-ui-tabs.md)

[formContext](../clientapi-form-context.md)

