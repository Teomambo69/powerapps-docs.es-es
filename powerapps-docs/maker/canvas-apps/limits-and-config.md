---
title: Requisitos del sistema, límites y valores de configuración | Microsoft Docs
description: Requisitos del sistema, límites y valores de configuración para PowerApps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: PowerApps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/07/2018
ms.author: sharik
ms.openlocfilehash: 5bf57ec96569751b3db656abdf04cebb1e13133a
ms.sourcegitcommit: 45fac73f04aa03b5796ae6833d777f4757e67945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="system-requirements-limits-and-configuration-values"></a>Requisitos del sistema, límites y valores de configuración
Este tema contiene los requisitos de plataforma de dispositivo y explorador web, así como los límites y los valores de configuración para PowerApps.

## <a name="supported-platforms-for-running-apps-using-the-powerapps-app"></a>Plataformas compatibles para ejecutar aplicaciones con la aplicación PowerApps
| **Versión mínima requerida** | **Se recomienda** |
| --- | --- |
| iOS 9.3 o posterior |iOS 10 o posterior con al menos 2 GB de RAM |
| Android 5 o posterior |Android 7 o posterior con al menos 4 GB de RAM |
| Windows 8.1 o posterior (solo para PC) |Windows 10 Fall Creators Update con al menos 8 GB de RAM|

## <a name="supported-browsers-for-running-apps"></a>Exploradores admitidos para ejecutar aplicaciones
| **Explorador** | **Sistema operativo** |
| --- | --- |
| Google Chrome (versión más reciente)<br>(se recomienda) |Windows 7 SP1, 8.1 y 10 <br>Android 5 o posterior <br>iOS 8 o posterior<br>MacOS |
| Microsoft Edge (versión más reciente)<br>(se recomienda) |Windows 10 |
| Microsoft Internet Explorer 11 (con la función Vista de compatibilidad desactivada) |Windows 7 SP1, 8.1 y 10 |
| Mozilla Firefox (versión más reciente) |Windows 7 SP1, 8.1 y 10 <br> Android 5 o posterior <br>iOS 8 o posterior <br>MacOS |
| Apple Safari (versión más reciente) |iOS 8 o posterior <br>MacOS |

## <a name="supported-browsers-for-powerapps-studio"></a>Exploradores admitidos para PowerApps Studio
| **Explorador** | **Sistema operativo** |
| --- | --- |
| Google Chrome (versión más reciente)<br>(se recomienda) |Windows 7 SP1, 8.1 y 10 <br>MacOS |
| Microsoft Edge (versión más reciente)<br>(se recomienda) |Windows 10 |
| Microsoft Internet Explorer 11 (con la función Vista de compatibilidad desactivada) |Windows 7 SP1, 8.1 y 10 |

## <a name="request-limits"></a>Límites de solicitudes
Estos límites se aplican a todas y cada una de las solicitudes de salida:

| Nombre | Límite |
| --- | --- |
| Tiempo de espera |180 segundos |
| Número de reintentos |4 |

> [!NOTE]
> El valor de reintento puede variar. Para ciertas condiciones de error, no es necesario volver a intentarlo.

## <a name="ip-addresses"></a>Direcciones IP
Las solicitudes de PowerApps usan direcciones IP que dependen de la región del [entorno](../../administrator/environments-overview.md) en que se encuentra la aplicación. No publicamos los nombres de dominio completos disponibles para los escenarios de PowerApps.

Las llamadas realizadas desde una API conectada a través de una aplicación (por ejemplo, la API de SQL o la API de SharePoint) proceden de la dirección IP que se especificará más adelante en este mismo tema.

Estas direcciones se deben usar si, por ejemplo, se deben incluir en la lista blanca las direcciones IP de una instancia de Azure SQL Database.

| Región | IP de salida |
| --- | --- |
| Asia |52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124 |
| Australia |13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35 |
| Canadá |52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56 |
| Europa |52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254 |
| India |52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245 |
| Japón |104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229 |
| Estados Unidos |104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191 |
| Estados Unidos (acceso anticipado) |52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29 |

## <a name="required-services"></a>Servicios requeridos
Esta lista identifica todos los servicios con los que PowerApps Studio se comunica y sus usos. La red **no** debe bloquear estos servicios.

| Dominios | Protocolos | Usa |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |Runtime de conectores/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph: para obtener la información de usuario (por ejemplo, la foto del perfil) |
| gallery.azure.com |https |Aplicaciones de ejemplo y plantilla |
| *.azure-apim.net |https |Hubs de API: subdominios diferentes para cada configuración regional |
| *.powerapps.com |https |WebAuth + Portal |
| *.azureedge.net |https |WebAuth |
| *.blob.core.windows.net |https |Blob Storage |
| vortex.data.microsoft.com |https |Telemetría |
