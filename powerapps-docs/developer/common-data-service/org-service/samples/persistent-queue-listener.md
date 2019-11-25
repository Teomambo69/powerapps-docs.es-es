---
title: 'Ejemplo: Escucha de cola persistente (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir una aplicación de escucha de Azure Service Bus para un contrato persistente de extremo de cola.
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
ms.openlocfilehash: c558df03a54c1eaa53d876b3c135c90790f3b3b5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749887"
---
# <a name="sample-persistent-queue-listener"></a>Ejemplo: escucha de cola persistente

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-persistent-queue-listener -->

Este ejemplo muestra cómo escribir una aplicación de escucha de Azure Service Bus para un contrato persistente de extremo de cola. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PersistentQueueListener).

La aplicación de escucha espera a que se publique un mensaje en el bus del servicio y a que esté disponible en la cola del extremo. Cuando un mensaje está disponible en la cola, el paquete de escucha lee el mensaje, imprime el contexto de ejecución contenido en el mensaje a la consola y elimina el mensaje de la cola.
