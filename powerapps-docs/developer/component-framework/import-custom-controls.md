---
title: Importar controles  | Microsoft Docs
description: Proceso para importar controles personalizados
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
---

# <a name="deploying-controls-into-common-data-service"></a>Implementación de controles en Common Data Service

En este tema se muestra cómo importar controles personalizados en Common Data Service. Después de desarrollar controles personalizados con PowerApps CLI, el siguiente paso es importar esos controles para poder ver los controles en tiempo de ejecución.

Siga los pasos indicados a continuación para crear e importar un archivo de solución:

1. Cree un nuevo proyecto de solución en el directorio que elija usando el comando `pac solution init --publisherName <enter your publisher name> --customizationPrefix <enter your publisher name>` después de `cd <your new folder>`.

   > [!NOTE]
   > Los valores `publisherName` y `cutomizationPrefix` deben ser únicos a su entorno.
 
2. Cuando se crea el nuevo proyecto de solución, debe hacer referencia a la ubicación donde se ubica el control creado. Puede agregar la referencia usando el comando `pac solution add-reference --<path of your PowerApps component framework project on disk>`
3. Para generar un archivo zip del proyecto de la solución, deberá `cd` en el directorio del proyecto de la solución y compilar el proyecto usando el comando `msbuild/t:restore` y `msbuild`

    > [!NOTE]
    > Si msbuild 15 no está en la ruta, abra Developer Command Prompt for Vs 2017 para ejecutar los comandos msbuild.

    > [!NOTE]
    > Al compilar la solución en la configuración de depuración, se genera un paquete de la solución no administrada. Un paquete de la solución administrada se genera compilando la solución en la configuración de versión. Estos valores pueden ser reemplazados especificando la propiedad SolutionPackageType en el archivo cdsproj.

4. Los archivos de solución generados de la solución se encuentran en `\bin\debug\`.
5. Debe importar la solución manualmente mediante el portal web.

## <a name="telemetry"></a>Telemetría

La característica de equipo está agregando telemetría anónima para comprender qué características o capacidades de la herramienta PowerApps CLI usan con más frecuencia los desarrolladores. Los datos agregados permiten proporcionar la mejor experiencia a los clientes centrándonos en lo verdaderamente importante.

Para deshabilitar la colección de telemetría, ejecute el comando `pac telemetry - -enabled false`. Para volver a activar la telemetría, use el comando `pac telemetry- -enabled true`.

### <a name="see-also"></a>Vea también

[Agregar controles a entidades o campos](add-custom-controls-to-a-field-or-entity.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)