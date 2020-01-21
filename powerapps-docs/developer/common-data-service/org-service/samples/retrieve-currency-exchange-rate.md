---
title: 'Ejemplo: Recuperar el tipo de cambio de divisas (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo crear una nueva divisa y recuperar y mostrar el tipo de cambio de divisas.
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
ms.openlocfilehash: 62a85f5a13bd05cf4b730e747a71a1b88467055b
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934228"
---
# <a name="sample-retrieve-currency-exchange-rate"></a>Ejemplo: recuperar el tipo de cambio de divisas

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-currency-exchange-rate -->

Este ejemplo muestra cómo crear una nueva divisa, y cómo recuperar y mostrar el tipo de cambio de la divisa con respecto a la divisa base de la organización. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveCurrencyExchangeRate).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RetrieveExchangeRateRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para recuperar el tipo de cambio.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización. 
2. El método `TransactionCurrency` crea una nueva divisa de ejemplo.

### <a name="demonstrate"></a>Demostración

El mensaje `RetrieveExchangeRateRequest` recupera el tipo de cambio con respecto a la divisa base de la organización.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
