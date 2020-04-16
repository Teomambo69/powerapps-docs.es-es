---
title: Complemento con Azure personalizado (Common Data Service) | Microsoft Docs
description: Este complemento personalizado puede publicar el contexto de la ejecución de canalización en Azure Service Bus.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f9dd7300882307bd06941b91ece152bf97002f83
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155924"
---
# <a name="sample-azure-aware-custom-plug-in"></a>Ejemplo: complemento personalizado con Azure

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-azure-aware-custom-plugin -->

El complemento demuestra cómo obtener el contexto de la ejecución y el servicio de seguimiento del parámetro de proveedor de servicios del método `Execute`. A continuación, el complemento publica el contexto en el extremo de Azure Service Bus y escribe información en el registro de seguimiento para facilitar la depuración. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Azureplugin).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Descargar o clonar el informe de [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local.
2. Abra la solución de ejemplo en Visual Studio y firme el ensamblado con una clave.
3. Registrar el complemento mediante la **herramienta de registro de complementos**

>[!NOTE]
> Este ejemplo requiere crear primero un extremo de servicio, y pasar su identificador al constructor de complementos con el parámetro no seguro de configuración cuando se registra el complemento.


