---
title: 'Ejemplo: Módulo de escucha bidireccional (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir un módulo de escucha de Azure Service Bus para un contrato de extremo bidireccional.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 84190ef0fcbe74c91fc12bafbd208d991296c0b5
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155552"
---
# <a name="sample-two-way-listener"></a>Ejemplo: escucha bidireccional

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-two-way-listener -->

Este ejemplo muestra cómo escribir un escucha de `Azure Service Bus` para un contrato de extremo bidireccional. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/TwoWayListener).

Este ejemplo registra un complemento de servicio remoto que se ejecuta siempre que un mensaje se publica en un extremo bidireccional en `Azure Service Bus`. Cuando el complemento se ejecuta, imprime en la consola el contenido del contexto de ejecución contenido en el mensaje.
