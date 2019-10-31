---
title: Obtener útiles para PowerApps Component Framework | Microsoft Docs
description: 'Consiga Microsoft PowerApps CLI para crear, depurar e implementar componentes de código con PowerApps Component Framework.'
keywords: 'PowerApps component framework, componentes de código, Component Framework'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
---

# <a name="get-tooling-for-powerapps-component-framework"></a>Obtener útiles para de PowerApps Component Framework

Use **Microsoft PowerApps CLI** (interfaz de la línea de comandos) para crear, depurar e implementar componentes de código utilizando PowerApps Component Framework. PowerApps CLI permite a los desarrolladores crear rápidamente componentes de código y en el futuro se expandirá para incluir compatibilidad para experiencias adicionales de desarrollo y administración del ciclo de vida de la aplicación (ALM). 

## <a name="what-is-microsoft-powerapps-cli"></a>¿Qué es Microsoft PowerApps CLI? 

Microsoft PowerApps CLI es una interfaz de línea de comandos para desarrolladores básica y completa que ayuda a los desarrolladores y creadores de aplicaciones a crear componentes de código. Los útiles de PowerApps CLI son el primer paso hacia un sistema de ALM completo donde los desarrolladores de la empresa y los ISV pueden crear, compilar, depurar y publicar las extensiones y personalizaciones de forma rápida y eficiente.  

## <a name="install-microsoft-powerapps-cli"></a>Instalar Microsoft PowerApps CLI

Para obtener Microsoft PowerApps CLI, realice lo siguiente:

1. Instale [Npm](https://www.npmjs.com/get-npm)(se incluye con Node.js) o instale [Node.js](https://nodejs.org/en/) (se incluye con npm). Se recomienda la versión LTS (soporte de largo plazo) 10.15.3 LTS, pues parece ser la más estable.

1. Instale [Paquete de desarrollador .NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Si aún no tiene Visual Studio 2017 o posterior, siga una de las opciones a continuación:
   - Opción 1: Instale [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) o posterior.
   - Opción 2: Instale [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) e instale [Visual Studio Code](https://code.visualstudio.com/Download).

1. Instalar [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI).
1. Para aprovechar todas las últimas capacidades, actualice los útiles PowerApps CLI a la última versión usando el comando.

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Para implementar el componente de código utilizando PowerApps CLI, deberá tener un entorno de Common Data Service con privilegios de administrador del sistema o personalizador del sistema.
> - Actualmente, PowerApps CLI se admite actualmente solo en Windows 10.

## <a name="microsoft-powerapps-cli-telemetry"></a>Telemetría de Microsoft PowerApps CLI

La característica de equipo está agregando la telemetría para comprender qué características o capacidades usan con más frecuencia los desarrolladores en la herramienta PowerApps CLI. Los datos agregados nos permiten proporcionar la mejor experiencia a los clientes centrándonos en lo verdaderamente esencial.

> [!NOTE]
> Para deshabilitar la colección de telemetría, ejecute el comando `pac telemetry disable`. Para volver a activar la telemetría, use el comando `pac telemetry enable`.

## <a name="uninstall-microsoft-powerapps-cli"></a>Desinstalar Microsoft PowerApps CLI

Para desinstalar los útiles PowerApps CLI, ejecute MSI desde [aquí](https://aka.ms/PowerAppsCLI). 

Si usted es participante de Versión preliminar privada y tiene una versión anterior de CLI, siga estos pasos:

1. Para averiguar dónde está instalado PowerApps CLI, abra un símbolo del sistema y escriba `where pac`.
1. Elimine la carpeta de PowerAppsCLI.
1. Abra la herramienta de variables de entorno ejecutando el comando `rundll32 sysdm.cpl,EditEnvironmentVariables` en el símbolo del sistema.
1. Haga doble clic en `Path` en la sección `User variable for...`
1. Seleccione la fila que contiene la ruta de PowerAppsCLI y haga clic en el botón Eliminar en el lado derecho.
1. Haga clic en **Aceptar** dos veces.

### <a name="see-also"></a>Vea también

[Implementación de componentes en TypeScript](implementing-controls-using-typescript.md)<br/>
