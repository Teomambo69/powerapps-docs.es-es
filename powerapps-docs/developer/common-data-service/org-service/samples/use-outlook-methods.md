---
title: " Usar métodos de Outlook (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo usar los métodos de Outlook.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: b1609c29dde65e77c6cecda39f9f1b651847dae6
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "3020097"
---
# <a name="sample-use-dynamics-365-for-outlook-methods"></a>Ejemplo: Usar métodos de Dynamics 365 for Outlook

Este ejemplo muestra cómo usar los métodos disponibles en el ensamblado [Microsoft.Crm.Outlook.Sdk.dll](https://docs.microsoft.com/dotnet/api/microsoft.crm.outlook.sdk?view=dynamics-outlookclient-ce-9). Puede descargar el ejemplo desde [aquí]().

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El ensamblado de `Microsoft.Crm.Outlook.sdk` se utiliza en un escenario que contiene tipos que proporcionan interacción programática con Microsoft Dynamics 365 for Outlook y Microsoft Dynamics 365 for Microsoft Office Outlook con acceso sin conexión.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito anteriormente, el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `CrmOutlookService` configura el servicio.
2. El método `CrmOutlookService.IsCrmClientOffline` comprueba si el cliente está sin conexión.
3. El método `CrmOutlookService.GoOnline()` conecta el cliente. Este método se sincronizará automáticamente con la base de datos, no es necesario llamar al método `Sync()`.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.