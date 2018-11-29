---
title: formContext.ui.sections (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Aprenda a trabajar con procesos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e362dfb2-cb64-49f5-b3d4-d77e813325ca
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuisections-client-api-reference"></a>formContext.ui.sections (referencia de la API de cliente)



Una sección contiene métodos para administrar la forma en la que aparece además de para acceder a la pestaña que contiene la sección.

Puede recuperar un objeto de la sección (por ejemplo, **sectionObj**) con el código de ejemplo siguiente:

```JavaScript
var tabObj = formContext.ui.tabs.get(arg);
var sectionObj = tabObj.sections.get(arg);
```

## <a name="properties"></a>Propiedades

- **Controles**: la recopilación de controles de la sección proporciona acceso a los controles de una sección. Para obtener información sobre los métodos expuestos por las recopilaciones, vea [Recopilaciones (referencia de la API de cliente)](collections.md). Para obtener información acerca de las propiedades y los métodos expuestos por los objetos de esta recopilación, consulte [Controles (referencia de la API de cliente)](controls.md).


## <a name="methods"></a>Métodos

|Nombre | Descripción |
|--|--|
|[getLabel](formcontext-ui-sections/getLabel.md)|[!INCLUDE[formcontext-ui-sections/includes/getLabel-description.md](formcontext-ui-sections/includes/getLabel-description.md)]|
|[getName](formcontext-ui-sections/getName.md)|[!INCLUDE[formcontext-ui-sections/includes/getName-description.md](formcontext-ui-sections/includes/getName-description.md)]|
|[getParent](formcontext-ui-sections/getParent.md)|[!INCLUDE[formcontext-ui-sections/includes/getParent-description.md](formcontext-ui-sections/includes/getParent-description.md)]|
|[getVisible](formcontext-ui-sections/getVisible.md)|[!INCLUDE[formcontext-ui-sections/includes/getVisible-description.md](formcontext-ui-sections/includes/getVisible-description.md)]|
|[setLabel](formcontext-ui-sections/setLabel.md)|[!INCLUDE[formcontext-ui-sections/includes/setLabel-description.md](formcontext-ui-sections/includes/setLabel-description.md)]|
|[setVisible](formcontext-ui-sections/setVisible.md)|[!INCLUDE[formcontext-ui-sections/includes/setVisible-description.md](formcontext-ui-sections/includes/setVisible-description.md)]|

### <a name="related-topics"></a>Temas relacionados

[formcontext.ui.tabs](formcontext-ui-tabs.md)

[formContext](../clientapi-form-context.md)