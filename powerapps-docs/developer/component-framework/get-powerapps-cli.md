---
title: Obtener herramientas para el marco de componentes de PowerApps | Microsoft Docs
description: Obtenga el Microsoft PowerApps CLI para crear, depurar e implementar componentes de código mediante el marco de componentes de PowerApps.
keywords: Marco de componentes de PowerApps, componentes de código, marco de componentes
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 496b7d443775da075dd8da52ac4b0a754121bf28
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2019
ms.locfileid: "72340032"
---
# <a name="get-tooling-for-powerapps-component-framework"></a>Obtener herramientas para el marco de componentes de PowerApps

Use la **CLI de Microsoft PowerApps** (interfaz de línea de comandos) para crear, depurar e implementar componentes de código mediante el marco de componentes de PowerApps. La CLI de PowerApps permite a los desarrolladores crear componentes de código rápidamente. En el futuro, se ampliará para incluir la compatibilidad con las experiencias de desarrollo y administración del ciclo de vida de las aplicaciones (ALM) adicionales. 

## <a name="what-is-microsoft-powerapps-cli"></a>Qué es Microsoft PowerApps CLI 

Microsoft PowerApps CLI es una sencilla interfaz de línea de comandos para desarrolladores que permite a los desarrolladores y a los fabricantes de aplicaciones crear componentes de código. Las herramientas de la CLI de PowerApps son el primer paso para una historia de ALM completa en la que los desarrolladores de la empresa y los ISV pueden crear, compilar, depurar y publicar sus extensiones y personalizaciones de forma rápida y eficaz.  

## <a name="install-microsoft-powerapps-cli"></a>Instalación de la CLI de Microsoft PowerApps

Para obtener Microsoft PowerApps CLI, haga lo siguiente:

1. Instale [NPM](https://www.npmjs.com/get-npm) (viene con node. js) o [node. js](https://nodejs.org/en/) (viene con NPM). Se recomienda LTS (compatibilidad a largo plazo) versión 10.15.3 LTS porque parece ser el más estable.

1. Instale [.NET Framework 4.6.2 Developer Pack](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Si aún no tiene Visual Studio 2017 o una versión posterior, siga una de estas opciones:
   - Opción 1: instalar [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) o posterior.
   - Opción 2: instalar el [SDK de .net Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) y, a continuación, instalar [Visual Studio Code](https://code.visualstudio.com/Download).

1. Instale [Microsoft POWERAPPS CLI](https://aka.ms/PowerAppsCLI).
1. Para aprovechar todas las funcionalidades más recientes, actualice las herramientas de la CLI de PowerApps a la versión más reciente con este comando:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Para implementar el componente de código mediante la CLI de PowerApps, debe tener un entorno de Common Data Service con privilegios de administrador del sistema o de personalización del sistema.
> - Actualmente, la CLI de PowerApps solo es compatible con Windows 10.

## <a name="microsoft-powerapps-cli-telemetry"></a>Telemetría de la CLI Microsoft PowerApps

El equipo de características está agregando la telemetría para comprender qué características o funcionalidades suelen usar los desarrolladores en la herramienta de la CLI de PowerApps. Los datos agregados nos permiten proporcionar la mejor experiencia a los clientes centrándose en lo que es esencial.

> [!NOTE]
> Para deshabilitar la colección de telemetría, ejecute el comando `pac telemetry disable`. Para volver a convertir la telemetría, use el `pac telemetry enable` de comandos.


## <a name="uninstall-microsoft-powerapps-cli"></a>Desinstalación de la CLI de Microsoft PowerApps

Para desinstalar las herramientas de la CLI de PowerApps, ejecute el archivo MSI desde [aquí](https://aka.ms/PowerAppsCLI). 

Si es un participante de vista previa privada y tiene una versión anterior de la CLI, siga estos pasos:

1. Para averiguar dónde está instalada la CLI de PowerApps, abra un símbolo del sistema y escriba `where pac`.
1. Elimine la carpeta PowerAppsCLI.
1. Abra la herramienta de variables de entorno ejecutando el comando `rundll32 sysdm.cpl,EditEnvironmentVariables` en el símbolo del sistema.
1. Haga doble clic en `Path` bajo la sección `User variable for...`.
1. Seleccione la fila que contiene la ruta de acceso PowerAppsCLI y seleccione el botón **eliminar** en el lado derecho.
1. Seleccione **Aceptar** dos veces.

### <a name="see-also"></a>Vea también

[Implementar componentes con TypeScript](implementing-controls-using-typescript.md)<br/>
