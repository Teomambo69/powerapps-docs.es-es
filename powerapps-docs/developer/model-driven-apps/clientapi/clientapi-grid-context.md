---
title: Contexto de cuadrícula de API de cliente en aplicaciones basadas en modelos| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: f884d7d4-31e6-4080-acd9-493e81e6b278
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="client-api-grid-context"></a>Contexto de cuadrícula de la API del cliente

Las cuadrículas presentan datos en formato tabular. Las cuadrículas pueden abarcar todo el formulario o pueden ser uno de los elementos de un formulario; estos últimos se denominan **subcuadrículas**.

El objeto de contexto de cuadrícula de la API de cliente proporciona una referencia a una subcuadrícula en un formulario con respecto al que se ejecuta el código actual. 

> [!NOTE]
> Obtener el contexto de una cuadrícula (que abarca el formulario completo) solo se admite en comandos de la cinta de opciones. Más información: [Formulario y cuadrícula en las acciones de la cinta](/powerapps/developer/model-driven-apps/pass-data-page-parameter-ribbon-actions#form-and-grid-context-in-ribbon-actions)

Utilice el objeto [formContext](clientapi-form-context.md) para obtener una instancia del formulario donde el código se ejecuta y después recuperar el control de subcuadrícula en el formulario. Por ejemplo, cuando conoce el nombre de un control de subcuadrícula (por ejemplo, la subcuadrícula **Contactos** en el formulario de cuentas predeterminado), puede tener acceso a él utilizando el siguiente código, por ejemplo.

```JavaScript
function doSomething(executionContext) {
   var formContext = executionContext.getFormContext(); // get the form Context
   var gridContext = formContext.getControl("Contacts"); // get the grid context

   // Perform operations on the subgrid
}
```

## <a name="related-topics"></a>Temas relacionados

[Contexto de formulario de la API del cliente](clientapi-form-context.md)<br/>
[Contexto de ejecución de la API de cliente](clientapi-execution-context.md)<br/>
[Comprender el modelo de objetos de la API de cliente](understand-clientapi-object-model.md)<br/>
[Cuadrículas y subcuadrículas](reference/grids.md)

