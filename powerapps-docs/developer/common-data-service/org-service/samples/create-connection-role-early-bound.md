---
title: 'Ejemplo: Creación de un rol de conexión (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear un rol de conexión.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 566c9d6609f62dc06227a16f651dac8e2e48ac9f
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155891"
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

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. Define algunos tipos anónimos para definir el intervalo de los valores de propiedad de conexión posibles.
2. Crea un rol de conexión para la cuenta y la entidad de contacto.
3. Crea un registro de código de tipo de objeto de rol de conexión para cuenta y la entidad Contacto.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
