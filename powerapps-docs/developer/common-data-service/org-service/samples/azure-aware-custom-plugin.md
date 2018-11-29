---
title: Complemento personalizado con Azure (Common Data Service para aplicaciones) | Microsoft Docs
description: Este complemento personalizado puede publicar el contexto de la ejecución de canalización en Azure Service Bus.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-azure-aware-custom-plug-in"></a>Ejemplo: complemento personalizado con Azure

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-azure-aware-custom-plugin -->

El complemento demuestra cómo obtener el contexto de la ejecución y el servicio de seguimiento del parámetro de proveedor de servicios del método `Execute`. A continuación, el complemento publica el contexto en el extremo de Azure Service Bus y escribe información en el registro de seguimiento para facilitar la depuración. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Azureplugin).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Descargar o clonar el informe de [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local.
2. Abra la solución de ejemplo en Visual Studio y firme el ensamblado con una clave.
3. Registrar el complemento mediante la **herramienta de registro de complementos**

>[!NOTE]
> Este ejemplo requiere crear primero un extremo de servicio, y pasar su identificador al constructor de complementos con el parámetro no seguro de configuración cuando se registra el complemento.


