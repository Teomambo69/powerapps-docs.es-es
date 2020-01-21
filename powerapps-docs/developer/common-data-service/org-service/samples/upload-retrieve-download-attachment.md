---
title: 'Ejemplo: cargar, recuperar y descargar datos adjuntos(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo cargar, recuperar y descargar un archivo adjunto
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
ms.openlocfilehash: 7e1f871cdf456322737df9da5990ae671f769034
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934140"
---
# <a name="sample-upload-retrieve-and-download-an-attachment"></a>Ejemplo: cargar, recuperar y descargar datos adjuntos

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-upload-retrieve-download-attachment -->

El ejemplo muestra cómo cargar, recuperar y descargar un archivo adjunto para una anotación utilizando los métodos [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9) y [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/URDAttachement).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los métodos `IOrganizationService` están diseñados para usarse en un escenario donde se proporciona acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `Annotation` crea instancias de un objeto de anotación.
1. El método `IOrganizationService` crea y carga el objeto de anotación

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.
