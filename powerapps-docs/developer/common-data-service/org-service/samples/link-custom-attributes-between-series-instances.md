---
title: 'Ejemplo: Vincular atributos personalizados entre series e instancias(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo vincular atributos personalizados entre series e instancias.
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
ms.openlocfilehash: fc884a2e4ee1118cef35bdfa4838f4343f061d84
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749891"
---
# <a name="sample-link-custom-attributes-between-series-and-instances"></a>Ejemplo: vincular atributos personalizados entre series e instancias

Este ejemplo muestra cómo vincular un atributo personalizado creado para una serie de citas periódicas (`RecurringAppointmentMaster`) con un atributo personalizado creado para las instancias de citas (`Appointment`). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/LinkAttributes).

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `CreateAttributeRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para crear atributos personalizados.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El mensaje `StringAttributeMetadata` crea atributos de cadena personalizados para instancia de citas periódicas e instancia de cita.
2. El `LinkedAttributeId` vincula el atributo personalizado al atributo personalizado de la cita.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
