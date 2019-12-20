---
title: Requisitos del sistema, límites y valores de configuración para aplicaciones de lienzo | Microsoft Docs
description: Requisitos del sistema, límites y valores de configuración para aplicaciones de lienzo integradas en Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/30/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed59b379b55a38a1e5a3454d26d07ae93d106e4f
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75204120"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>Requisitos del sistema, límites y valores de configuración para aplicaciones de lienzo
Este tema contiene los requisitos de la plataforma del dispositivo y del explorador Web, así como los límites y los valores de configuración de las aplicaciones de canvas.

## <a name="supported-platforms-for-running-canvas-apps-using-the-power-apps-mobile-app"></a>Plataformas admitidas para ejecutar aplicaciones de lienzo con la aplicación móvil de Power apps

| **Versión mínima requerida** | **Se recomienda** |
| --- | --- |
| iOS 12 o posterior |iOS 12 o posterior|
| Android 7 o posterior |Android 7 o posterior |
| Windows 8.1 o posterior (solo para PC) |Windows 10 Fall Creators Update con al menos 8 GB de RAM|

> [!NOTE]
> Actualmente no se admiten las nuevas características de la [aplicación móvil](/powerapps/user/run-app-client)plataforma Windows para Power apps. En esta plataforma no están disponibles características como la opción de Common Data Service mejorada y el acceso de invitado. Se recomienda usar un reproductor Web en Windows para aprovechar todo el conjunto de funcionalidades. Las actualizaciones de la plataforma de aplicaciones móviles de Power apps para Windows se anunciarán en el futuro.

## <a name="supported-browsers-for-running-canvas-apps"></a>Exploradores admitidos para ejecutar aplicaciones de lienzo

| **Explorador** | **Sistema operativo** |
| --- | --- |
| Google Chrome (versión más reciente)<br>(se recomienda) |Windows 7 SP1, 8.1 y 10 <br>Android 5 o posterior <br>iOS 8 o posterior<br>MacOS |
| Microsoft Edge (versión más reciente)<br>(se recomienda) |Windows 10 |
| Microsoft Internet Explorer 11 (con la función Vista de compatibilidad desactivada) |Windows 7 SP1, 8.1 y 10 |
| Mozilla Firefox (versión más reciente) |Windows 7 SP1, 8.1 y 10 <br> Android 5 o posterior <br>iOS 8 o posterior <br>MacOS |
| Apple Safari (versión más reciente) |iOS 8 o posterior <br>MacOS |

## <a name="supported-browsers-for-power-apps-studio"></a>Exploradores admitidos para Power apps Studio

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
Las solicitudes de Power apps usan direcciones IP que dependen de la región del [entorno](../../administrator/environments-overview.md) en el que se encuentra la aplicación. No publicamos los nombres de dominio completos disponibles para los escenarios de Power apps.

Las llamadas realizadas desde una API conectada a través de una aplicación (por ejemplo, la API de SQL o la API de SharePoint) proceden de la dirección IP que se especificará más adelante en este mismo tema.

Estas direcciones se deben usar si, por ejemplo, se deben incluir en la lista blanca las direcciones IP de una instancia de Azure SQL Database.

> [!IMPORTANT]
>   Si tiene configuraciones existentes, actualícelo tan pronto como sea posible antes del 30 de septiembre de 2018 para que incluyan y coincidan con las direcciones IP de esta lista para las regiones donde existen las aplicaciones de Power apps.

| Región | IP de salida |
| --- | --- |
| Asia | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19 |
| Australia  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174 |
| Brasil | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Canadá | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| Europa | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| India  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| Japón | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| Sudamérica | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Reino Unido | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| Estados Unidos | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| Estados Unidos (acceso anticipado)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>Servicios requeridos
Esta lista identifica todos los servicios a los que se comunica Power apps Studio y sus usos. La red **no** debe bloquear estos servicios.

| Dominios | Protocolos | Usa |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |Runtime de conectores/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph: para obtener información de usuario (por ejemplo, la foto de perfil) |
| gallery.azure.com |https |Aplicaciones de ejemplo y plantilla |
| \*. azure-apim.net |https |Hubs de API: subdominios diferentes para cada configuración regional |
| \*. powerapps.com |https | create.powerapps.com, make.powerapps.com, content.powerapps.com y make.powerapps.com |
| \*. azureedge.net |https | create.powerapps.com, make.powerapps.com, content.powerapps.com y make.powerapps.com |
| \*. blob.core.windows.net |https | Blob Storage |
| \*. flow.microsoft.com | https | create.powerapps.com, make.powerapps.com, content.powerapps.com y make.powerapps.com |
| *. dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |Telemetría |
| host | https | Power apps Mobile

> [!NOTE]
> Si usa una VPN, debe configurarse para excluir localhost de la tunelización de Power apps Mobile.

## <a name="size-limits"></a>Límites de tamaño

Puede encontrar información sobre los límites de tamaño en el texto, los hipervínculos, las imágenes y los elementos multimedia en los [tipos de datos](functions/data-types.md#text-hyperlink-image-and-media).

## <a name="power-apps-per-app-plan"></a>Power apps por plan de aplicación

La información está ahora disponible en la sección [Power apps por plan de aplicación](/power-platform/admin/signup-for-powerapps-admin#power-apps-per-app-plan) de la guía de administración de la plataforma de energía.
