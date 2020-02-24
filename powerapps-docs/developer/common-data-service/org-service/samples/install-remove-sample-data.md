---
title: 'Ejemplo: instalar y eliminar datos de ejemplo (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo instalar y eliminar datos de ejemplo.
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
ms.openlocfilehash: 977025209c4fa4abac37ad99c6644cba6e846902
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956352"
---
# <a name="install-or-remove-sample-data"></a>Instalar o eliminar datos de ejemplo

Este ejemplo muestra cómo instalar o desinstalar los datos de ejemplo para una organización mediante el mensaje [InstallSampleDataRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.installsampledatarequest?view=dynamics-general-ce-9).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `InstallSampleDataRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para instalar los datos de ejemplo.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. Solicita a los usuarios que instalen o eliminen datos de muestra.
2. Si el usuario opta por instalar datos de ejemplo, el mensaje `InstallSampleDataRequest` instala los datos de ejemplo.
3. Si el usuario opta por instalar los datos de ejemplo, el mensaje `UninstallSampleDataRequest` quita los datos de ejemplo.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.