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
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f3932d21683b83008e95f03ba2aae646d2b8e491
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836470"
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

