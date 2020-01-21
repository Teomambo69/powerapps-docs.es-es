---
title: 'Ejemplo: Recuperar información de zona horaria (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar la información de zona horaria
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
ms.openlocfilehash: 9eb0be763eb04aceb5de5918b6bd32cffdce6833
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934192"
---
# <a name="sample-retrieve-time-zone-information"></a>Ejemplo: recuperar información de zona horaria

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-time-zone-information -->

Este ejemplo muestra cómo recuperar la información de zona horaria. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveTimeZone).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El método `RetrieveAllTimeZonesForLocale` está diseñado para usarse en un escenario donde usa el Id. de configuración local actual para recuperar todas las zonas horarias.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `RetrieveCurrentUSerSettings` recupera el código y el id. de configuración local de la zona horaria del usuario actual.
2. El método `RetrieveAllTimeZonesForLocale` usa el id. de configuración local actual y recupera todas las zonas horarias.
3. El método `GetTimeZoneCodeByLocaleAndName` recupera el código la zona horaria por nombre e id. de configuración local.
4. El método `RetrieveTimeZoneById` recupera la zona horaria por id.
5. El método `RetrieveTimeZonesLessThan50` recupera zonas horarias menos de 50.
6. El método `RetrieveLocalTimeFromUTCTime` recupera la hora local desde la hora UTC.
7. El método `RetrieveUTCTimeFromLocalTime` recupera la hora UTC desde la hora local.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
