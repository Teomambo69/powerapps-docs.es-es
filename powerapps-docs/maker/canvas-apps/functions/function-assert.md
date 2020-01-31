---
title: Función Aserción | Microsoft Docs
description: Información de referencia sobre la función Assert en Power Apps, incluida la sintaxis
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4319c3685db46f4277109e385a640e744402edc
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541299"
---
# <a name="assert-function-in-power-apps-test-studio"></a>Función Assert en Power Apps Test Studio

Una aserción es una expresión o condición que se evalúa como true o false en una prueba. Si la expresión devuelve false, se producirá un error en el caso de prueba. Las aserciones se usan para validar el resultado esperado de una prueba o un paso de prueba, respecto al resultado real y para que no se supere la prueba si la condición es false. Las aserciones pueden usarse para validar el estado de los controles de la aplicación, como los valores de las etiquetas, las selecciones de los cuadros de lista y otras propiedades de los controles.  

Los mensajes de aserción también se encuentran en una tabla Seguimientos en el registro TestCaseResult, tanto para las superadas como para aquellas que presentan errores. 

## <a name="syntax"></a>Sintaxis

*Assert(expresión, mensaje)*

- *Expresión*: obligatoria. Una expresión que se evalúa como true o false.
- *Mensaje*: no se requiere. Mensaje que describe el error de la aserción. 


## <a name="examples"></a>Ejemplos

```Assert(lblResult.Text = "Success", "lblResult value Expected : Success , Actual : " & lblResult.Text)```<br>
```Assert(ListBox1.Selected.Value = "Success", "ListBox1 selection Expected : Success,  Actual : " & ListBox1.Selected.Value)```<br>
```Assert(kudosAfterTest = kudosBeforeTest + 1, "Kudos count. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

### <a name="see-also"></a>Vea también

[Información general de Test Studio](../test-studio.md) <br>
[Trabajo con Test Studio](../working-with-test-studio.md)
