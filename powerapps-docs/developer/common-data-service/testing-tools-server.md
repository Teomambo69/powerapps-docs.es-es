---
title: Herramientas de pruebas para desarrollo del lado del servidor (Common Data Service) | Microsoft Docs
description: Obtenga más información sobre los marcos de prueba para desarrollo del lado del servidor.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9f4aedc7bc54dcf8d18ab3f9fb0aa1ae21d02b89
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749786"
---
# <a name="testing-tools-for-server-side-development"></a>Herramientas de pruebas para el desarrollo de servidor

Muchos programadores recomiendan encarecidamente incluir prueba de unidad como parte del proceso de desarrollo. Otros no están convencidos. Common Data Service no ofrece herramientas de prueba, pero debe tener en cuenta que hay herramientas de la comunidad disponibles que puede usar. Un marco popular para el desarrollo del lado del servidor es [Fake Xrm Easy](https://dynamicsvalue.com/home). Este marco se puede combinar con los marcos de prueba de .NET Framework que elija. [FakeItEasy](https://fakeiteasy.github.io/) es una opción común.

> [!NOTE]
> Microsoft no proporciona soporte para herramientas creadas por la comunidad. Si tiene algún problema con una herramienta de la comunidad, póngase en contacto con el editor.

## <a name="benefits-of-unit-testing"></a>Beneficios de pruebas de unidad

Las pruebas de unidad se recomiendan pero no se requieren. Cuando esté empezando o si la cantidad de código en la solución es relativamente pequeña, puede pensar que dedica más tiempo a escribir pruebas que a las funciones incluidas en la solución.

Los ventajas de las pruebas de unidad empiezan a aumentar cuando la solución se hace más grande y compleja. En particular con el desarrollo del lado del servidor, puede haber beneficios considerables en depurar localmente empleando los datos ficticios o falsos con un marco de prueba en lugar de tener que pasar por todos los pasos descritos en [Depurar complementos](debug-plug-in.md) para generar un perfil de depuración.

Cuando una solución se desarrolla con pruebas de unidad, los desarrolladores obtienen mayor productividad y un producto de mejor calidad.

### <a name="see-also"></a>Vea también

[Herramientas de pruebas para desarrollo del lado del cliente](../model-driven-apps/testing-tools-client.md)<br />
[Vídeo: Introducción a DevOps con Dynamics 365](https://youtu.be/AorM792M8nY)