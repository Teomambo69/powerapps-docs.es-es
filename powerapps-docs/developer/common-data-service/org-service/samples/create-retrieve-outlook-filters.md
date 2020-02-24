---
title: " Crear y recuperar filtros de Outlook (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo crear y recuperar filtros para Outlook
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
ms.openlocfilehash: 7835bd8552a19e5440380a470acc700f2280e1f5
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017360"
---
# <a name="create-and-retrieve-outlook-filters"></a>Crear y recuperar filtros de Outlook

Este ejemplo muestra cómo recuperar filtros para Outlook.

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreartRetrieveOutlookFilters).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito anteriormente, el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `fetchXml` crea y recupera el filtro sin conexión. En su cliente de Outlook, esto aparecerá en la pestaña Filtros del sistema en **Archivo -> CRM -> Sincronizar -> Filtros de Outlook**.
2. El método `InstantiateFiltersRequest` activa las plantillas sin conexión seleccionadas para el usuario actual.
3. El método `ResetUserFilterRequest` restablece la configuración predeterminada de las plantillas sin conexión del usuario actual.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

