---
title: Función Restablecer| Microsoft Docs
description: Información de referencia de la función Reset en PowerApps, con sintaxis y ejemplos
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 07/06/2017
ms.author: gregli
ms.openlocfilehash: bc87fd823b37869298b453aba439bda6aabbb112
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="reset-function-in-powerapps"></a>Función Reset en PowerApps
Restablece un control a su valor predeterminado, descartando cualquier modificación del usuario.  

## <a name="description"></a>Descripción
La función **Reset** restablece un control al valor de su propiedad **Default**.  Se descartan los cambios que haya realizado el usuario.

No es posible restablecer los controles que estén en un control [**Galería**](../controls/control-gallery.md) o [**Editar formulario**](../controls/control-form-detail.md) desde fuera de dichos controles.  Los controles se puede restablecer desde las fórmulas de los controles que estén en la misma galería o formulario.  También es posible restablecer todos los controles de un formulario con la función [**ResetForm**](function-form.md). 

La función **Reset** es una alternativa al uso la propiedad **Reset** de los controles de entrada y, por lo general, se prefiere usar la función, en lugar de la propiedad.  La propiedad **Reset** puede ser una opción mejor si es preciso restablecer conjuntamente muchos controles de varias fórmulas.  La activación o desactivación de la propiedad **Reset** se puede realizar desde un control [**Botón**](../controls/control-button.md) con la fórmula **Reset = Button.Pressed** o desde una variable con **Reset = MyVar**, y la activación o desactivación de **MyVar** con la fórmula **Button.OnSelect = Set( MyVar, true ); Set( MyVar, false )**.    

Los controles de entrada también se restablecen cuando su propiedad **Default** cambia.

**Reset** no tiene ningún valor devuelto y solo se puede usar en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Reset**( *Control* )

* *Control* (se requiere). El control que se restablece.

## <a name="example"></a>Ejemplo
1. Inserte un control **Entrada de texto** en una pantalla.  De forma predeterminada, su nombre será **TextInput1** y el valor de su propiedad **Default** será **"Entrada de texto"**.
2. Escriba un valor nuevo en el cuadro de texto.  
3. Inserte un control **Botón** en la pantalla.
4. Establezca la propiedad **AlSeleccionar** del botón en **Reset( TextInput1 )**.
5. Seleccione el botón.  Esto puede hacerse incluso durante la creación mediante la realización de la selección hacia los extremos del control.
6. El contenido del cuadro de texto volverá al valor de la propiedad **Default**.

