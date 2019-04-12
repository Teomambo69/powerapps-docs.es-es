---
title: 'Ejemplo: escucha de Rest (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir un agente de escucha de Azure Service Bus para un contrato de extremo REST.
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
# <a name="sample-rest-listener"></a>Ejemplo: agente de escucha de REST

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rest-listener -->

Este ejemplo muestra cómo escribir una aplicación de escucha de `Azure Service Bus` para un contrato de extremo de `REST`. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RESTListener).

Este ejemplo registra un complemento de servicio remoto que se ejecuta siempre que un mensaje se publica en un extremo de `REST` en el bus de servicio. Cuando el complemento se ejecuta, imprime en la consola el contenido del contexto de ejecución contenido en el mensaje.
