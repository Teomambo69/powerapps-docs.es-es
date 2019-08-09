---
title: Actualizar PowerApps CLI| Microsoft Docs
description: Actualizar PowerApps CLI
keywords: 'Marco de componentes de PowerApps, Componentes personalizados, Marco de componentes'
ms.author: nabuthuk
manager: kvivek
ms.date: 05/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47c4426c-e963-4ef6-a4b7-d56591ca8ac2
---

# <a name="updating-tooling-to-latest-version"></a>Actualizar útiles a la última versión

Para actualizar Microsoft PowerApps CLI a la última versión 02.856.1 y aprovechar las últimas capacidades, ejecute el comando siguiente en la ventana de Developer Command Prompt for VS 2017.

```CLI
pac install latest
```

## <a name="what-else-do-i-need-to-know"></a>¿Qué más necesito saber?

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
