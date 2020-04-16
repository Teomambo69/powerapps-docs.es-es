---
title: 'Ejemplo: Publicar informes (Common Data Service) | MicrosoftDocs'
description: Este ejemplo muestra cómo publicar informes.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 0dc52a0cd6cdc45c15327b1f1b2bf9c5c1848153
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155704"
---
# <a name="publish-reports"></a>Publicación de informes

Este ejemplo muestra cómo publicar un informe mediante la creación de un registro **Informe** y los registros relacionados que lo hacen visible. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PublishReport).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito anteriormente, el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `Report` crea una instancia del objeto de informe.
2. El método `ReportCategory` establece la categoría del informe al que debe pertenecer el informe.
3. El método `ReportEntity` define qué entidad utiliza este informe.
4. El método `ReportVisibility` establece la visibilidad del informe.

### <a name="clean-up"></a>Limpiar

No se requiere limpieza para este ejemplo.