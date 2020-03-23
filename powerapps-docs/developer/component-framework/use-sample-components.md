---
title: ¿Cómo usar los componentes de ejemplo? (Power Apps Component Framework) | Microsoft Docs
description: Proporciona información sobre cómo puede usar los componentes de muestra creados usando Power Apps Component Framework en sus aplicaciones de lienzo y basadas en modelo
keywords: ''
author: Nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 11/25/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: a674b37fd4616a21fe8d61336f255debafd552dd
ms.sourcegitcommit: 3b68c4e29be4e8f68c0bfb88abdd1bbdf0187c57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "3080842"
---
# <a name="how-to-use-the-sample-components"></a>¿Cómo usar los componentes de ejemplo?

Todos los componentes de ejemplo enumerados en esta sección están disponibles para descargar [aquí](https://go.microsoft.com/fwlink/?linkid=2088525) para que pueda probarlos en sus aplicaciones de lienzo o basadas en modelo.

Los temas de los componentes de ejemplo individuales en esta sección le proporcionan una visión general del componente de ejemplo, su apariencia visual y el manifiesto, el código y los recursos para el componente de ejemplo.

## <a name="before-you-can-try-the-sample-components"></a>Antes de poder probar los componentes de ejemplo
Para probar los componentes de ejemplo, primero debe:
- [Descargar](https://go.microsoft.com/fwlink/?linkid=2088525) los componentes de ejemplo para tener una copia local.
- Instalar [Power Apps CLI](https://aka.ms/PowerAppsCLI).

## <a name="try-the-sample-components"></a>Probar los componentes de ejemplo
Siga los pasos a continuación para importar y probar los componentes de ejemplo en su aplicación de lienzo o basada en modelo:

1. Vaya a la carpeta de su equipo donde haya descargado los componentes de ejemplo y extraiga el archivo .zip.  
1. Abra el símbolo del sistema del desarrollador para Visual Studio 2017 y vaya a la carpeta del componente de ejemplo en la carpeta extraída que desea ver en tiempo de ejecución. Por ejemplo, vaya a \<carpeta_extraída>/carpeta TS_IncrementComponent.
1. Ejecute el siguiente comando para obtener todas las dependencias necesarias:
    ```CLI
    npm install
    ```
1. Cree una nueva carpeta con el comando `mkdir <folder name>` dentro de la carpeta del componente de ejemplo y vaya a la carpeta con el comando `cd <folder name>`. 
1. Cree un nuevo proyecto de solución en la carpeta usando el comando siguiente:
    ```CLI
    pac solution init --publisher-name <Name of the publisher> --publisher-prefix <Publisher prefix>
    ```
1. Después de que se crea el nuevo proyecto de solución, debe hacer referencia a la ubicación donde se ubica el componente de ejemplo. Puede agregar la referencia usando el comando siguiente.
    ```CLI
    pac solution add-reference --path <Path to the root of the sample component>
    ```
1. Para generar un archivo zip del proyecto de la solución, deberá `cd` en el directorio del proyecto de la solución y compilar el proyecto usando el comando siguiente:
    
     ```CLI
     msbuild /t:restore
    ```
1. De nuevo, ejecute el comando `msbuild`.
1. El archivo .zip de la solución generada estará disponible en la carpeta `Solution\bin\debug`. Debe [importar la solución](/powerapps/maker/common-data-service/import-update-export-solutions) manualmente en el entorno de Common Data Service mediante el portal web una vez que el archivo zip esté listo. Alternativamente, para importar la solución usando los comandos de Power Apps CLI, consulte las secciones [Conexión al entorno](https://docs.microsoft.com/powerapps/developer/component-framework/import-custom-controls#connecting-to-your-environment) e [Implementación](https://docs.microsoft.com/powerapps/developer/component-framework/import-custom-controls#deploying-code-components).
1. Finalmente, para agregar componentes de código a sus aplicaciones de lienzo y basadas en modelo, consulte [Agregar componentes a las aplicaciones basadas en modelo](https://docs.microsoft.com/powerapps/developer/component-framework/add-custom-controls-to-a-field-or-entity) y [Agregar componentes a las aplicaciones de lienzo](https://docs.microsoft.com/powerapps/developer/component-framework/component-framework-for-canvas-apps#add-components-to-a-canvas-app).
