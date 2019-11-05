---
title: Configuración de un tipo de paso condicional para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar un tipo de paso condicional para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ec3e568b239bf66c0d4554e244d5afef2d5ef673
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553679"
---
# <a name="add-a-conditional-step-type"></a>Agregar un tipo de paso condicional

Un paso de formulario web puede ser un tipo ' condition ' que indica que el paso debe evaluar una expresión. Si la expresión se evalúa como true, se muestra el siguiente paso. Si la expresión se evalúa como false y se ha especificado la "siguiente etapa si se produce un error en la condición", se mostrará ese paso. La entidad actual es el destino que se usa para evaluar la expresión. El origen del registro es el origen del registro del paso anterior.

## <a name="attributes"></a>Atributos

| Nombre                         | Descripción                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Cumple                    | Expresión condicional que se va a evaluar.                                                                                                                                                                                           |
| Paso siguiente si se produce un error en la condición | El tipo de paso condicional, a diferencia de todos los demás, tiene dos búsquedas de paso siguiente. Se respetará la búsqueda de paso siguiente predeterminada si la condición se evalúa como true. Esta propiedad establece el paso siguiente si la condición se evalúa como false. |

Los operandos disponibles son los siguientes:

| Operandos (s)    | Tipo                   |
|---------------|------------------------|
| =, ==         | es igual a                 |
| !=            | No es igual a             |
| &gt;          | Mayor que           |
| &lt;          | Menor que              |
| &gt;=         | Mayor o igual que |
| &lt;=         | Menor o igual que    |
| &             | And                    |
| \|             | Or                     |
| !             | No                    |
| =\*, = =\*,-= | Forma                   |
| ! =\*          | No es como               |

## <a name="format"></a>Formato

El formato de la expresión es el siguiente:

\[nombre lógico de atributo de entidad\] \[operando\] valor \[\]

Ejemplo:

nuevo\_categorycode = 750101

Una condición puede tener varias expresiones. Puede usar paréntesis para agrupar expresiones anidadas, por ejemplo:

New\_categorycode = 750101 & gendercode = 2

-   New\_categorycode = 750101 & (gendercode = 2 | gendercode = 3)

-   nombre de la nueva\_= Jane Doe

-   New\_twooptionfield = true

-   New\_twooptionfield = false

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Pasos de Web Form para portales](web-form-steps.md)  
[Tipo de paso cargar formulario/pestaña carga](load-form-step.md)  
[Tipo de paso de redirección](add-redirect-step.md)  
[Agregar JavaScript personalizado](add-custom-javascript.md)  

