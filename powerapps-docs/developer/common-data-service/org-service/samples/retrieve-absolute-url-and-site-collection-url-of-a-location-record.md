---
title: 'Ejemplo: Recuperar una dirección URL absoluta y una dirección URL de colección de sitios (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo recuperar la dirección URL absoluta y la dirección URL de la colección de sitios de una ubicación de SharePoint.
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
ms.openlocfilehash: 43929bf09ee211596c6a2043be48a796c387e5e9
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934236"
---
# <a name="sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record"></a>Ejemplo: recuperar una dirección URL absoluta y una dirección URL de colección de sitios de un registro de ubicación

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/integration-dev/sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record -->

En este ejemplo se muestra cómo recuperar la dirección URL absoluta y la dirección URL de la colección de sitios de un registro de ubicación de SharePoint Server mediante el mensaje [RetrieveAbsoluteAndSiteCollectionUrlRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveabsoluteandsitecollectionurlrequest?view=dynamics-general-ce-9).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `RetrieveAbsoluteAndSiteCollectionUrlRequest` se proporcionan para se pueden usar en un escenario que contiene datos necesarios para recuperar la dirección URL absoluta y la dirección URL de la colección de sitios para un registro de ubicación de SharePoint.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización. 
1. El método `CreateRequireRecords` crea registros de entidad usados por el ejemplo.

### <a name="demonstrate"></a>Demostración

La `RetrieveAbsoluteAndSiteCollectionUrlRequest` se usa para recuperar la dirección URL absoluta y la dirección URL de la colección de sitios del registro de SharePoint.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
