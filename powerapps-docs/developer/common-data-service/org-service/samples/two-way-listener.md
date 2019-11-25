---
title: 'Ejemplo: Módulo de escucha bidireccional (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir un módulo de escucha de Azure Service Bus para un contrato de extremo bidireccional.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 66918421cb999ccb3d24764172bbf43062b49f6e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749857"
---
# <a name="sample-two-way-listener"></a>Ejemplo: escucha bidireccional

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-two-way-listener -->

Este ejemplo muestra cómo escribir un escucha de `Azure Service Bus` para un contrato de extremo bidireccional. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/TwoWayListener).

Este ejemplo registra un complemento de servicio remoto que se ejecuta siempre que un mensaje se publica en un extremo bidireccional en `Azure Service Bus`. Cuando el complemento se ejecuta, imprime en la consola el contenido del contexto de ejecución contenido en el mensaje.
