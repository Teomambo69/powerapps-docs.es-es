---
title: 'Ejemplo: Módulo de escucha unidireccional (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo la aplicación registra un complemento de servicio remoto que se ejecuta cada vez que un mensaje se publica en un extremo unidireccional.
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
ms.openlocfilehash: 5e588160d35ccc86155134584b4031eb795e4191
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155724"
---
# <a name="sample-one-way-listener"></a>Ejemplo: módulo de escucha unidireccional

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-one-way-listener -->

Este ejemplo muestra cómo escribir un escucha de `Azure Service Bus` para un contrato de extremo unidireccional. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OneWayListeners).

Este ejemplo de aplicación de escucha registra un complemento de servicio remoto que se ejecuta cada vez que un mensaje se publica en un extremo unidireccional en `Azure Service Bus`. Cuando se ejecuta el complemento, refleja en la consola los contenidos del contexto de la ejecución incluidos en el mensaje. 
