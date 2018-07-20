---
title: Funciones Habilitar y Deshabilitar | Microsoft Docs
description: Información de referencia para las funciones Enable y Disable en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 1b5395459dd5833d054755dadca37bc9b39785c9
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39019075"
---
# <a name="enable-and-disable-functions-in-powerapps"></a>Funciones Enable y Disable en PowerApps
Activa o desactiva una [señal](signals.md).

## <a name="overview"></a>Información general
Algunas señales pueden cambiar con frecuencia, lo cual obliga a la aplicación a volver a calcular cuando se producen los cambios.  Los cambios rápidos durante un largo período de tiempo pueden agotar la batería del dispositivo. Puede utilizar estas funciones para activar o desactivar manualmente una señal.

Cuando no se usa una señal, esta se desactiva automáticamente.

## <a name="description"></a>Descripción
Las funciones **Enable** y **Disable** permiten activar y desactivar una señal respectivamente.

Estas funciones solo funcionan actualmente para la señal de **[ubicación](signals.md)**.

Estas funciones no tienen ningún valor devuelto. Se pueden usar únicamente en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Enable**( *Señal* )<br>**Disable**( *Señal* )

* *Señal*: requerido.  La señal que va a activar o desactivar.

