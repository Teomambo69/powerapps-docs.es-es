---
title: Funciones Habilitar y Deshabilitar | Microsoft Docs
description: "Información de referencia para las funciones Enable y Disable en PowerApps, incluidos ejemplos y sintaxis"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: b4051bdb312707cfafe63a97b5e77a2860feb60c
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="enable-and-disable-functions-in-powerapps"></a>Funciones Enable y Disable en PowerApps
Activa o desactiva una [señal](signals.md).

## <a name="overview"></a>Información general
Algunas señales pueden cambiar con frecuencia, lo cual obliga a la aplicación a volver a calcular cuando se producen los cambios.  Los cambios rápidos durante un largo período de tiempo pueden agotar la batería del dispositivo. Puede utilizar estas funciones para activar o desactivar manualmente una señal.

Cuando no se usa una señal, esta se desactiva automáticamente.

## <a name="description"></a>Descripción
Las funciones **Enable** y **Disable** permiten activar y desactivar una señal respectivamente.

Estas funciones solo funcionan actualmente para la señal de **[ubicación](signals.md)**.

Estas funciones no tienen ningún valor devuelto. Se pueden usar únicamente en [fórmulas de comportamiento](../working-with-formulas-in-depth.md#behavior-formulas).

## <a name="syntax"></a>Sintaxis
**Enable**( *Señal* )<br>**Disable**( *Señal* )

* *Señal*: requerido.  La señal que va a activar o desactivar.

