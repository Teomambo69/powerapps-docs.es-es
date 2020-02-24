---
title: 'Ejemñlo: trabajar con atributos (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo trabajar con atributos
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
ms.openlocfilehash: 245e7091a0e7ccc9eee9b463be5d81f2a5df31d9
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956349"
---
# <a name="work-with-attribute-metadata"></a>Trabajar con metadatos de atributos

Este ejemplo muestra cómo llevar a cabo varias acciones en atributos. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkWithAttributes).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo crear diferentes tipos de atributos en Common Data Service.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `BooleanAttributeMetadata` crea un atributo de tipo booleano.
2. El mensaje `DateTimeAttributeMetadata` crea un atributo de tipo fecha-hora.
3. El mensaje `DecimalAttributeMetadata` crea un atributo de tipo decimal.
4. El mensaje `IntegerAttributeMetadata` crea un atributo de tipo entero.
5. El mensaje `MemoAttributeMetadata` crea un atributo de tipo memorando.
6. El mensaje `MoneyAttributeMetadata` crea un atributo de tipo dinero.
7. El mensaje `PicklistAttributeMetadata` crea un atributo de tipo lista desplegable.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.