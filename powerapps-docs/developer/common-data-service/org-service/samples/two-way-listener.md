---
title: 'Ejemplo: escucha bidireccional (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir un módulo de escucha de Azure Service Bus para un contrato de extremo bidireccional.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-two-way-listener"></a>Ejemplo: escucha bidireccional

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-two-way-listener -->

Este ejemplo muestra cómo escribir un escucha de `Azure Service Bus` para un contrato de extremo bidireccional. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/TwoWayListener).

Este ejemplo registra un complemento de servicio remoto que se ejecuta siempre que un mensaje se publica en un extremo bidireccional en `Azure Service Bus`. Cuando el complemento se ejecuta, imprime en la consola el contenido del contexto de ejecución contenido en el mensaje.
