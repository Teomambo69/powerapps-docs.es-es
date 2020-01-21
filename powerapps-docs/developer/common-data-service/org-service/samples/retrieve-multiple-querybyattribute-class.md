---
title: 'Ejemplo: recuperar varios con la clase QueryByAttribute(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo usar la clase QueryByAttribute
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
ms.openlocfilehash: 0a6b20686f4e02afff576eb54133d061e4b82f18
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934212"
---
# <a name="sample-retrieve-multiple-with-the-querybyattribute-class"></a>Ejemplo: recuperar varios con la clase QueryByAttribute

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-retrieve-multiple-querybyattribute-class -->

Este ejemplo muestra cómo utilizar [QueryByAttribute](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.query.querybyattribute?view=dynamics-general-ce-9) en el método [RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleQueryByAttribute).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

La clase `QueryByAttribute` está diseñada para usarse en un escenario donde contiene una consulta que se expresa como un conjunto de pares de atributo y valor.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Account` crea 2 registros de cuenta.

### <a name="demonstrate"></a>Demostración

El método `QueryByAttribute` crea consulta con QueryByAttribute.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.
