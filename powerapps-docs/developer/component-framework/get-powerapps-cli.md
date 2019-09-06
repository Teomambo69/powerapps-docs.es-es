---
title: Obtener útiles para PowerApps Component Framework | Microsoft Docs
description: 'Consiga Microsoft PowerApps CLI para crear, depurar e implementar componentes personalizados con PowerApps Component Framework.'
keywords: 'Marco de componentes de PowerApps, Componentes personalizados, Marco de componentes'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/18/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
---

# <a name="get-tooling-for-powerapps-component-framework"></a>Obtener útiles para PowerApps Component Framework

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Use **Microsoft PowerApps CLI** (interfaz de la línea de comandos) para crear, depurar e implementar componentes personalizados utilizando PowerApps Component Framework. PowerApps CLI permite a los desarrolladores crear rápidamente componentes de PowerApps component framework y en el futuro se expandirá para incluir compatibilidad para experiencias adicionales de desarrollo y administración del ciclo de vida de la aplicación (ALM). 

## <a name="what-is-microsoft-powerapps-cli"></a>¿Qué es Microsoft PowerApps CLI? 

Microsoft PowerApps CLI es una interfaz de línea de comandos sencilla y completa para desarrolladores que permite crear el componente personalizado. PowerApps CLI también es el primer paso hacia un sistema de ALM completo donde los desarrolladores de la empresa y los ISV pueden crear, compilar, depurar y publicar las extensiones y personalizaciones de sus aplicaciones de PowerApps y Dynamics 365 Customer Engagement de forma rápida y eficiente.  

> [!IMPORTANT]
> - Microsoft PowerApps CLI son una versión preliminar y pueden ser diferentes de la versión lanzada comercialmente.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 
> - Si proporciona comentarios acerca del software a Microsoft, usted concede a Microsoft, sin cargo alguno, el derecho de usar, compartir y comercializar sus comentarios de cualquier modo y con cualquier objetivo. 
> - Microsoft no ofrece soporte técnico para esta versión preliminar de característica. El soporte técnico de Microsoft no podrá ayudarle con los problemas o las preguntas que pueda tener.

## <a name="install-microsoft-powerapps-cli"></a>Instalar Microsoft PowerApps CLI

Para utilizar Microsoft PowerApps CLI, realice lo siguiente:

1. Instale [Npm](https://www.npmjs.com/get-npm)(se incluye con Node.js) o instale [Node.js](https://nodejs.org/en/) (se incluye con npm). Se recomienda la versión LTS (soporte de largo plazo) 10.15.3 LTS, pues parece ser la más estable.

1. Instale [Paquete de desarrollador .NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Si aún no tiene Visual Studio 2017 o posterior, siga una de las opciones a continuación:
   - Opción 1: Instale [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) o posterior.
   - Opción 2: Instale [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) e instale [Visual Studio Code](https://code.visualstudio.com/Download).

1. Instalar [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI).



> [!NOTE]
> - Para implementar el componente personalizado utilizando PowerApps CLI, deberá tener un entorno Common Data Service con privilegios de administrador del sistema o personalizador del sistema.
> - PowerApps CLI se admite actualmente solo en Windows 10.

## <a name="update-microsoft-powerapps-cli-to-the-latest-version"></a>Actualizar Microsoft PowerApps CLI a la última versión

Para actualizar Microsoft PowerApps CLI a la última versión y aprovechar las últimas capacidades, ejecute el comando siguiente en la ventana de Developer Command Prompt for VS 2017:

```CLI
pac install latest
```

### <a name="what-else-do-i-need-to-know"></a>¿Qué más necesito saber?

Si ya ha creado un proyecto de solución o un proyecto de PowerApps Component Framework, asegúrese de actualizar estos proyectos a los últimos paquetes. Esto le ayudará a aprovechar las capacidades que acaba de agregar con sus proyectos existentes. Los proyectos recién creados contendrán ya estos valores.

- Actualice la etiqueta de la versión en su `pcfproj` situado en la carpeta de proyecto de PowerApps Component Framework:

   ```XML
   <PackageReference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="0.*"/>
   ```
- Actualice la etiqueta de la versión en su `cdsproj` situado en la carpeta de proyecto de la solución:

   ```XML
   <PackageReference Include="Microsoft.PowerApps.MSBuild.Solution" Version="0.*"/>
   ```

    > [!NOTE] 
    > Después de realizar los cambios mencionados, ejecute el comando `msbuild /t:restore` para actualizar el proyecto a la versión correcta.


- Actualice la etiqueta de la versión en su archivo `package.json` situado en la carpeta de proyecto de PowerApps Component Framework:

  ```JSON
  "devDependencies":{
   "pcf-scripts": "^0",
   "pcf-start": "^0"
    }
  ```
   > [!NOTE]
   > Después de realizar los cambios anteriores, el uso de 'npm update' en el símbolo del sistema siempre actualizará el proyecto a la versión correcta.

## <a name="microsoft-powerapps-cli-telemetry"></a>Telemetría de Microsoft PowerApps CLI

La característica de equipo está agregando telemetría anónima para comprender qué características o capacidades de la herramienta PowerApps CLI usan con más frecuencia los desarrolladores. Los datos agregados nos permiten proporcionar la mejor experiencia a los clientes centrándonos en lo verdaderamente importante.

> [!NOTE]
> Para deshabilitar la colección de telemetría, ejecute el comando `pac telemetry --enable false`. Para volver a activar la telemetría, use el comando `pac telemetry --enable true`.

## <a name="uninstall-microsoft-powerapps-cli"></a>Desinstalar Microsoft PowerApps CLI

Para desinstalar la herramienta PowerApps CLI, ejecute MSI desde [aquí](https://aka.ms/PowerAppsCLI). 

Si usted es participante de Versión preliminar privada y tiene una versión anterior de CLI, siga estos pasos:

1. Para averiguar dónde está instalado PowerApps CLI, abra un símbolo del sistema y escriba `where pac`
1. Elimine la carpeta de PowerAppsCLI.
1. Abra la herramienta de variables de entorno ejecutando el comando `rundll32 sysdm.cpl,EditEnvironmentVariables` en el símbolo del sistema
1. Haga doble clic en `Path` en la sección `User variable for...`
1. Seleccione la fila que contiene la ruta de PowerAppsCLI y haga clic en el botón Eliminar en el lado derecho
1. Haga clic en **Aceptar** dos veces.

### <a name="see-also"></a>Vea también

[Implementación de componentes en TypeScript](implementing-controls-using-typescript.md)<br/>

