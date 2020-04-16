---
title: 'Ejemplo: Escucha de cola persistente (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir una aplicación de escucha de Azure Service Bus para un contrato persistente de extremo de cola.
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
ms.openlocfilehash: f277caf86819ee00ead90855a6d60e09e76ec077
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155708"
---
# <a name="sample-persistent-queue-listener"></a>Ejemplo: escucha de cola persistente

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-persistent-queue-listener -->

Este ejemplo muestra cómo escribir una aplicación de escucha de Azure Service Bus para un contrato persistente de extremo de cola. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PersistentQueueListener).

La aplicación de escucha espera a que se publique un mensaje en el bus del servicio y a que esté disponible en la cola del extremo. Cuando un mensaje está disponible en la cola, el paquete de escucha lee el mensaje, imprime el contexto de ejecución contenido en el mensaje a la consola y elimina el mensaje de la cola.
