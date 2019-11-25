---
title: Evitar usar window.top | MicrosoftDocs
description: Describe cómo evitar errores de script y el comportamiento incorrecto de las aplicaciones asociado con el uso de window.top en personalizaciones de JavaScript.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: daa8e5a4a8aaff4b2aecb0942783a84eed328dfb
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749455"
---
# <a name="avoid-using-windowtop"></a>Evite usar window.top

**Categoría**: compatibilidad, listo para actualización, migración en línea

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

- El siguiente error de script se mostrará a los usuarios o se incluirá en los registros de errores: `Error: Blocked a frame with origin "https://<yourinstance>.dynamics.com" from accessing a cross-origin frame.`
- Es posible que las personalizaciones no se comporten correctamente en el contexto de Dynamics 365 App for Outlook, Dynamics 365 para teléfonos y tabletas, o una aplicación externa que hospeda Common Data Service en un Iframe.

  > [!NOTE]
  > Es posible que haya diversas situaciones donde la administración del error lo enmascara y sigue el procesamiento de script, por lo que produce un comportamiento inesperado.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Evite el uso de `window.top` en scripts que se ejecuten en el contexto de Dynamics 365 App for Outlook, Dynamics 365 para teléfonos y tabletas o en una aplicación externa que hospede Common Data Service en un Iframe. Aunque estos escenarios no se den actualmente en su organización, debe evitar usar `window.top` o protegerse frente a este problema.

 > [!IMPORTANT]
 > El uso de `window.parent` o variaciones de la jerarquía principal (por ejemplo,`window.parent.parent`) puede producir los mismos síntomas.

A continuación se describen los métodos recomendados:

- Evitar el uso del objeto `window.top` en conjunto.

- Si usar `window.top` es la única opción disponible, primero pruébelo para determinar si se puede acceder a `window.top` mediante el script a continuación. Si no está disponible, proporcione una lógica alternativa o una experiencia de usuario de reserva.

  > [!NOTE]
  > Aunque se recomienda evitar usar `window.top`, este script se incluye en aquellos casos extremos donde puede ser que es la única opción disponible.

    ```javascript
    function isTopAccessible() {
        try {
                window.top.location;
                return true;
            }
            catch (err) {
                return false;
            }
        }
    }

    var canAccess = isTopAccessible();
    alert(canAccess);
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

Se debe evitar cualquier uso de `window.top`, si es posible. Los siguientes son ejemplos de patrones que se ven habitualmente.

> [!WARNING]
> Estos escenarios deben evitarse.

```javascript
// Getting or setting variables at the top level
var myValue = window.top.myGlobalVariable;

// Attempting to access the Xrm namespace at the top level
myValue = window.top.Xrm.Page.getAttribute("field1");
```

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

En los escenarios mencionados, `window.top` se refiere a la ventana propiedad de un contexto de aplicaciones externo a Dynamics 365. Debido a los distintos orígenes, el explorador presenta al usuario con un error de seguridad de origen cruzado.

### <a name="see-also"></a>Vea también
[Aplicar la lógica de negocios usando scripting de cliente en aplicaciones basadas en modelos que usan JavaScript](/powerapps/developer/model-driven-apps/client-scripting)<br/>
[Eventos en formularios y cuadrículas en aplicaciones basadas en modelos](/powerapps/developer/model-driven-apps/clientapi/events-forms-grids)<br/>