---
title: 'Ejemplo: Recuperar datos adjuntos de correo electrónico para una plantilla de correo electrónico(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar los datos adjuntos de correo electrónico asociados con una plantilla de correo electrónico
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-retrieve-email-attachments-for-an-email-template"></a>Ejemplo: recuperar datos adjuntos de correo electrónico para una plantilla de correo electrónico

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-email-attachments-email-template -->

Este ejemplo muestra cómo recuperar los datos adjuntos de correo electrónico asociados con una plantilla de correo electrónico mediante el método [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveEmailAttach).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El método `IOrganizationService.RetrieveMultiple` está diseñada para usarse en un escenario donde recupera una colección de registros.


## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea una plantilla de correo electrónico de ejemplo mediante el método `Template`.

### <a name="demonstrate"></a>Demostración

1. La `QueryExpression` recupera todos los datos adjuntos.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
