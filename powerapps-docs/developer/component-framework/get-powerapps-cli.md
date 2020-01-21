---
title: Obtener útiles para Power Apps component framework | Microsoft Docs
description: Consiga Microsoft Power Apps CLI para crear, depurar e implementar componentes de código con Power Apps component framework.
keywords: Power Apps component framework, componentes de código, component framework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 16362dea63560e973c73fd5b94a80532faa515b2
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909274"
---
# <a name="get-tooling-for-power-apps-component-framework"></a>Obtener útiles para de Power Apps component framework

Use **Microsoft Power Apps CLI** (interfaz de la línea de comandos) para crear, depurar e implementar componentes de código utilizando Power Apps component framework. Power Apps CLI permite a los desarrolladores crear componentes de código rápidamente. En el futuro, se expandirá para incluir compatibilidad para desarrollo adicional y experiencias de administración del ciclo de vida de aplicaciones (ALM). 

## <a name="what-is-microsoft-power-apps-cli"></a>¿Qué es Microsoft Power Apps CLI? 

Microsoft Power Apps CLI es una completa interfaz de línea de comandos básica para desarrolladores que permite a los desarrolladores y creadores de aplicaciones crear componentes de código. 

Los útiles de Power Apps CLI son el primer paso hacia un sistema de ALM completo donde los desarrolladores de la empresa y los ISV pueden crear, compilar, depurar y publicar las extensiones y personalizaciones de forma rápida y eficiente.  

## <a name="install-microsoft-power-apps-cli"></a>Instalar Microsoft Power Apps CLI

Para obtener Microsoft Power Apps CLI, realice lo siguiente:

1. Instale [Npm](https://www.npmjs.com/get-npm)(se incluye con Node.js) o [Node.js](https://nodejs.org/en/) (se incluye con npm). Recomendamos LTS (soporte a largo plazo) versión 10.15.3 o superior.

1. Instale [Paquete de desarrollador .NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Si aún no tiene Visual Studio 2017 o posterior, siga una de estas opciones a continuación:
   - Opción 1: Instale [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) o posterior.
   - Opción 2: Instale [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) e instale [Visual Studio Code](https://code.visualstudio.com/Download).

1. Instalar [Microsoft Power Apps CLI](https://aka.ms/PowerAppsCLI).
1. Para aprovechar todas las últimas capacidades, actualice los útiles de Power Apps CLI a la última versión mediante este comando:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Para implementar el componente de código utilizando Power Apps CLI, deberá tener un entorno de Common Data Service con privilegios de administrador del sistema o personalizador del sistema.
> - Actualmente, Power Apps CLI se admite actualmente solo en Windows 10.

## <a name="common-commands"></a>Comandos comunes

Esta tabla enumera algunos comandos comunes utilizados en la CLI

|Comando|Descripción|Ejemplos|
|------|-----------|--------|
|**pcf**|Comandos para trabajar con Power Apps component framework. Tiene los siguientes parámetros: <br/> - **init**: inicializa el proyecto de componentes de código. Tiene los siguientes parámetros <br/> - *namespace*: espacio de nombres del componente de código. <br/> - *name*: nombre del componente de código. <br/> - *template* : campo o conjunto de datos <br/> - **push**: envía el componente de código a la instancia de Common Data Service con los cambios más recientes. Tiene el siguiente parámetro: <br/> - *publisher-prefix*: prefijo del anunciante de la organización.| `pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>` <br/> <br/> `pac pcf push --publisher-prefix <your publisher prefix>`|
|**solución**|Comandos para trabajar con proyectos de Common Data Service. Tiene los siguientes parámetros: <br/> - **init**: inicializa el proyecto de la solución. Tiene los siguientes parámetros:<br/> - *publisher-name*: nombre del anunciante de la organización. <br/> - *publisher-prefix*: prefijo del anunciante de la organización. <br/> - **add-reference**: establece la ruta de referencia de la carpeta del proyecto de componentes enviando el parámetro `path`.<br/> - **clon**: crea un proyecto de solución basado en el proyecto de solución existente al pasar los siguientes parámetros `name`, `version` y `include`|`pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>` <br/><br/> `pac solution add-reference --path <path to your Power Apps component framework project>`<br/><br/> `pac solution clone –name<name of the solution to be exported> --version <version of your solution> --include <settings that should be included>`|
|**auth**|Comandos para autenticar Common Data Service. Tiene los siguientes parámetros: <br/> - **create**: crea el perfil de autenticación para la organización enviando el parámetro `url`. Debe pasar la URL de la organización para el parámetro `url`. <br/> - **list**: proporciona la lista de perfiles de autenticación. <br/> - **select**: proporciona una forma cambiar entre los perfiles de autenticación creados anteriormente enviando el parámetro `index`.<br/>**eliminar**: elimina el perfil de autenticación creado al pasar el parámetro `index`.|`pac auth create --url <your Common Data Service org’s url>` <br/> <br/> `pac auth list` <br/><br/> `Pac auth select --index <index of the active profile>`|
|**telemetry**|Administra la configuración de telemetría. Tiene los siguientes parámetros: <br/>- *habilitar*: habilita la opción de telemetría.<br/> - *deshabilitar*: deshabilita la opción de telemetría.<br/> - *estado*: devuelve si la telemetría está habilitada o deshabilitada.|`pac telemetry enable` <br/><br/> `pac telemetry disable`|
|**org**|Comando para trabajar con Common Data Service.|`pac org who`|
|**complemento**|Crea un proyecto de complementos|`pac plugin init`|


## <a name="uninstall-microsoft-power-apps-cli"></a>Desinstalar Microsoft Power Apps CLI

Para desinstalar los útiles Power Apps CLI, ejecute MSI desde [aquí](https://aka.ms/PowerAppsCLI). 

Si usted es participante de una **Versión preliminar privada** y tiene una versión anterior de CLI, siga estos pasos:

1. Para averiguar dónde está instalado Power Apps CLI, abra un símbolo del sistema y escriba `where pac`.
1. Elimine la carpeta de PowerAppsCLI.
1. Abra la herramienta de variables de entorno ejecutando el comando `rundll32 sysdm.cpl,EditEnvironmentVariables` en el símbolo del sistema.
1. Haga doble clic en `Path` en la sección `User variable for...`.
1. Seleccione la fila que contiene la ruta de PowerAppsCLI y seleccione el botón **Eliminar** en el lado derecho.
1. Seleccione **Aceptar** dos veces.

### <a name="see-also"></a>Vea también

[Crear el primer componente de código](implementing-controls-using-typescript.md)<br/>
