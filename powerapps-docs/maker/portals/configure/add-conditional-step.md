---
title: Configurar un tipo de paso condicional para un portal | MicrosoftDocs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761117"
---
# <a name="add-a-conditional-step-type"></a>Agregar un tipo de paso condicional

Un paso de formulario web puede ser de tipo 'Condición', lo que indica que el paso debe evaluar una expresión. Si expresión se evalúa como true, se mostrará el siguiente paso. Si expresión se evalúa como false y si se ha especificado el 'Paso siguiente si la condición da error', ese paso se mostrará. La entidad actual es el destino usado para evaluar la expresión. El origen del registro está configurado de manera predeterminada como el origen del registro del paso anterior.

## <a name="attributes"></a>Atributos

| Nombre                         | Descripción                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Condición                    | La expresión condicional que se evaluará                                                                                                                                                                                           |
| Paso siguiente si la condición da error | El tipo de paso condicional, a diferencia de las demás, tiene dos búsquedas del siguiente paso. La búsqueda predeterminada del siguiente paso se respetará si la condición se evalúa como true. Esta propiedad define el siguiente paso si la condición se evalúa como false. |

Los operandos disponibles son los siguientes:

| Operando(s)    | Tipo                   |
|---------------|------------------------|
| =, ==         | Es igual a                 |
| !=            | No es igual             |
| &gt;          | Mayor que           |
| &lt;          | Menor que              |
| &gt;=         | Mayor o igual que |
| &lt;=         | Menor o igual que     |
| &             | Y                    |
| \|             | O                     |
| !             | No                    |
| =\*, ==\*, -= | Como                   |
| !=\*          | No como               |

## <a name="format"></a>Formato

El formato de la expresión es el siguiente:

\[nombre lógico de atributo de entidad\] \[operando\] \[valor\]

Ejemplo:

new\_categorycode = 750101

Una condición puede tener varias expresiones. Puede usar paréntesis agrupar expresiones anidadas, por ejemplo:

new\_categorycode = 750101 & gendercode = 2

-   new\_categorycode = 750101 & (gendercode = 2 | gendercode = 3)

-   new\_name = Jane Doe

-   new\_twooptionfield = true

-   new\_twooptionfield = false

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Pasos de formulario web para portales](web-form-steps.md)  
[Tipo de paso Cargar formulario/Cargar pestaña](load-form-step.md)  
[Tipo del paso de redireccionamiento](add-redirect-step.md)  
[Agregar JavaScript personalizado](add-custom-javascript.md)  

