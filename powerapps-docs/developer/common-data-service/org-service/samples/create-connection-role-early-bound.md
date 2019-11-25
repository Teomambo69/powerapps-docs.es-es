---
title: 'Ejemplo: Creación de un rol de conexión (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear un rol de conexión.
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
ms.openlocfilehash: 9ad3fd39f00d68af3a115c3bed2cc6d984eeeeb0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749739"
---
# <a name="sample-create-a-connection-role"></a>Ejemplo: crear un rol de conexión

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-create-connection-role-early-bound -->

Este ejemplo muestra cómo crear un rol de conexión que puede usarse para cuentas y contactos. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConnectionRole).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo crear un rol de conexión que puede usarse para cuentas y contactos.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración
1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración
1. Define algunos tipos anónimos para definir el intervalo de los valores de propiedad de conexión posibles.
2. Crea un rol de conexión para la cuenta y la entidad de contacto.
3. Crea un registro de código de tipo de objeto de rol de conexión para cuenta y la entidad Contacto.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en [Configuración](#setup).
    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
