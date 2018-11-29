---
title: getNavigationBehavior (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getnavigationbehavior-client-api-reference"></a>getNavigationBehavior (referencia de la API de cliente)



[!INCLUDE[./includes/getNavigationBehavior-description.md](./includes/getNavigationBehavior-description.md)]

> [!NOTE]
> Este método está disponible solo para la [Interfaz unificada](/dynamics365/get-started/whats-new/customer-engagement/new-in-version-9#unified-interface-framework-for-new-apps). 

## <a name="syntax"></a>Sintaxis

```
stageObj.getNavigationBehavior().allowCreateNew = function () {
    return true|false;
}
```

## <a name="returns"></a>Devuelve

**Tipo**: Objeto 

**Descripción**: un objeto con la propiedad `allowCreateNew` que le permite definir si el botón **crear** estará disponible en una fase posterior para que el usuario pueda crear una instancia de entityB a partir del formulario entityA en un escenario de navegación de flujo de proceso de negocio entre entidades. 

Por ejemplo, este es el caso del botón **crear** en la fase **desarrollar** del flujo de proceso de negocio de ejemplo **AccountToContactProcess** que le permite crear un registro de contacto a partir del formulario de cuenta.

![](../../../../media/clientapi_getNavigationBehavior.png)

La propiedad `allowCreateNew` devolverá **sin definir** para los registros de flujo de proceso de negocio que no implementan una navegación entre entidades.

## <a name="example"></a>Ejemplo

El código de ejemplo siguiente muestra cómo puede ocultar o mostrar el botón **crear** para una fase activa de un flujo de proceso de negocio según su nombre.

```JavaScript
function sampleFunction(executionContext) {
    var formContext = executionContext.getFormContext();
    formContext.data.process.getActiveStage.getNavigationBehavior().allowCreateNew = function () {
        if (formContext.data.process.getName() === 'Test Process') {
            return false; // Create button is not available
        }
        else {
            return true; // Create button is available
        }
    }
}
```

### <a name="related-topics"></a>Temas relacionados
 
[formContext.data.process](../../formContext-data-process.md)

