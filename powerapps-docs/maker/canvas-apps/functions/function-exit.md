---
title: Función Salir | Microsoft Docs
description: Información de referencia para la función exit en Power Apps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/02/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e0ed91cc66f5b42bbea769443ad086476245029c
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759807"
---
# <a name="exit-function-in-power-apps"></a>Función exit en Power apps
Sale de la aplicación que se está ejecutando actualmente y, opcionalmente, cierra la sesión del usuario actual.

## <a name="description"></a>Descripción
La función **Exit** permite salir de la aplicación en ejecución. El usuario se devuelve a la lista de aplicaciones. El usuario puede seleccionar otra aplicación para abrirla.  

**Exit** detiene cualquier otra evaluación de las fórmulas. Las llamadas de función encadenadas con un [operador de punto y coma](operators.md) después de la **salida** no se llevan a cabo.   

Use el argumento opcional *SignOut* para cerrar la sesión del usuario actual fuera de las aplicaciones de energía. *SignOut* es útil cuando se comparten dispositivos para garantizar la seguridad del usuario.

Al crear la aplicación, al llamar a **Exit** no se cierra o se cierra la sesión del usuario.  Sin embargo, detiene la evaluación del resto de la fórmula.

**Exit** solo se puede usar en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

> [!NOTE]
> No se admite el cierre de sesión con la función **Exit** mientras se ejecuta la aplicación en un explorador Web.

## <a name="syntax"></a>Sintaxis
**Exit**([*SignOut*])

* *SignOut* : opcional. Valor booleano que, si *es true* , firmará el usuario actual fuera de Power apps.  El valor predeterminado es *false* y el usuario mantiene la sesión iniciada.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | 
| --- | --- | 
| **Exit ()** | Sale de la aplicación actual y deja que el usuario inicie sesión.  El usuario se devuelve a la lista de aplicaciones.  |
| **Exit (&nbsp;true&nbsp;)** | Sale de la aplicación actual y el usuario cierra la sesión.  El usuario deberá volver a iniciar sesión con sus credenciales antes de ejecutar una aplicación. | 


