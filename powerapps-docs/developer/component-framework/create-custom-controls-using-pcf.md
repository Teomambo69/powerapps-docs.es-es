---
title: Crear componente personalizado mediante útiles de marco de componentes de PowerApp| Microsoft Docs
description: Empiece a crear un componente mediante útiles de marco de componentes de PowerApps
keywords: 'Marco de componentes de PowerApps, Componentes personalizados, Marco de componentes'
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---

# <a name="create-debug-and-deploy-a-component-using--microsoft-powerapps-cli"></a>Crear, depurar e implementar un componente con Microsoft PowerApps CLI

Use la interfaz de la línea de comandos (CLI) de PowerApps para crear, depurar e implementar los componentes personalizados del marco de componentes de PowerApps. PowerApps CLI permitirá a los desarrolladores crear rápidamente componentes del marco de componentes de PowerApps y en el futuro se expandirá para incluir compatibilidad para experiencias adicionales de desarrollo y administración del ciclo de vida de la aplicación (ALM). 

## <a name="what-is-microsoft-powerapps-cli"></a>Qué es Microsoft PowerApps CLI 

Microsoft PowerApps CLI es una interfaz de línea de comandos sencilla y completa para desarrolladores que permite crear el componente personalizado. PowerApps CLI también es el primer paso hacia un sistema de ALM completo donde los desarrolladores de la empresa y los ISV pueden crear, compilar, depurar y publicar las extensiones y personalizaciones de sus aplicaciones de PowerApps y Dynamics 365 Customer Engagement de forma rápida y eficiente.  

## <a name="prerequisites-to-use-powerapps-cli"></a>Requisitos previos para usar PowerApps CLI

Para usar PowerApps CLI necesitará lo siguiente:

- Instale [Npm](https://www.npmjs.com/get-npm)(se incluye con Node.js) o instale [Node.js](https://nodejs.org/en/) (se incluye con npm). Se recomienda la versión LTS (soporte de largo plazo) 10.15.3 LTS, pues parece ser la más estable.
- Si aún no tiene Visual Studio 2017 o posterior, siga una de las opciones a continuación:
   - Opción 1: Instale Visual Studio 2017 o posterior
   - Opción 2: Instale .NET Core 2.2 SDK e instale Visual Studio Code
- Instale Microsoft PowerApps CLI desde [aquí](http://download.microsoft.com/download/D/B/E/DBE69906-B4DA-471C-8960-092AB955C681/powerapps-cli-0.1.51.msi)

> [!IMPORTANT]
> - Las herramientas de Microsoft PowerApps CLI son una versión preliminar y pueden ser diferentes de la versión lanzada comercialmente.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 
> - Si proporciona comentarios acerca del software a Microsoft, usted concede a Microsoft, sin cargo alguno, el derecho de usar, compartir y comercializar sus comentarios de cualquier modo y con cualquier objetivo. 
> - Microsoft no ofrece soporte técnico para esta versión preliminar de característica. El soporte técnico de Microsoft no podrá ayudarle con los problemas o las preguntas que pueda tener.

> [!NOTE]
> Para implementar el componente personalizado, necesitará el entorno Common Data Service con privilegios de administrador o personalizador del sistema.

> [!NOTE]
> PowerApps CLI se admite actualmente solo en Windows 10.

## <a name="creating-a-new-powerapps-component-framework-component"></a>Creación de un nuevo componente del marco de componentes de PowerApps

Para empezar, abra un nuevo Developer Command Prompt for VS 2017 después de instalar PowerApps CLI.

1. En el Developer Command Prompt for VS 2017, cree una nueva carpeta en el disco duro local, por ejemplo, `C:\Users\<your name>\Documents\My_PCF_Control`.
2. Vaya a la carpeta recién creada usando el comando `cd <specify your new folder path>`.
3. Ejecute el comando siguiente para crear un nuevo proyecto de componente pasando algunos parámetros básicos `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Hoy ofrecemos dos tipos de componentes **campo** y **conjunto de datos**.

4. Para recuperar todas las dependencias necesarias de proyecto, ejecute el comando `npm install`.
5. Abra la carpeta de proyecto (`C:\Users\<your name>\Documents\My_PCF_Control\<component name>`) en cualquier entorno de desarrollo de su elección y empiece con el desarrollo del componente personalizado. Si desea seguir un tutorial paso a paso desplácese hacia abajo para ver cómo se implementa un componente lineal de ejemplo.

## <a name="building-your-components"></a>Creación de los componentes

Para generar el componente puede abrir la carpeta en Visual Studio Code y usar el comando (Ctrl-Mayús-B), luego seleccione las opciones de compilación. Como alternativa, puede compilar el control rápidamente mediante el comando `npm run build` en la ventana de Developer Command Prompt for VS 2017.

## <a name="debugging-your-powerapps-component-framework-component"></a>Depurar el componente del marco de componentes de PowerApps

Una vez que termine de implementar la lógica del componente personalizado, ejecute el siguiente comando de iniciar el proceso de depuración `npm start`

> [!NOTE]
> Hoy solo puede visualizar el componente de campo, pero se proporcionará próximamente compatibilidad para el conjunto de datos. La imagen de debajo muestra un componente de ejemplo implementado en el tutorial siguiente. 

> [!div class="mx-imgBorder"]
> ![host-local](media/local-host.png "host local")

Como se muestra en la imagen de arriba, la ventana de exploración se abrirán con 3 secciones. El componente se generará en el panel izquierdo mientras que el panel derecho se compone de las secciones **Entradas** y **Salidas**

  - La sección**Entradas** es una interfaz de usuario interactiva que muestra todas las propiedades y sus tipos y grupos de tipos definidos en manifest.xml. Permitir escribir datos ficticios para cada propiedad. 
  - La sección**Salidas** genera la salida cada vez que se llama al método `getOutputs` de un componente.  
 
> [!NOTE]
> Si desea modificar `manifest.xml` o crear propiedades adicionales, deberá reiniciar el proceso de depuración antes de que aparezcan en la sección de entradas.

Cuando introduce datos ficticios, puede usar las funcionalidades de depuración del explorador para observar el comportamiento del componente. Cada explorador proporciona una herramienta de depuración para ayudarle a depurar el código nativo en el explorador. Normalmente, puede activar la depuración en el explorador presionando la tecla **F12** para mostrar la herramienta de desarrollo nativa usada para depuración. Hoy se admiten los exploradores Chrome y Edge.

Por ejemplo, en **Microsoft Edge**,

- Presione **F12** para abrir inspector.
- Haga clic en el componente
- En la barra superior, vaya a **Depurador** y luego empiece a buscar el nombre del componente descrito en el archivo Manifest en la barra de búsqueda. Por ejemplo, escriba el nombre del componente como `Hello World component`.

     > [!div class="mx-imgBorder"]
     > ![componente-depuración](media/debug-control.png "Componente de depuración")

> [!NOTE]
> Siempre es conveniente establecer puntos de interrupción en los métodos de ciclo de vida del componente como `init` y `updateView`

También puede interactuar con el componente localmente en tiempo real y observar elementos en DOM estableciendo un punto de interrupción en la pestaña Buzón del origen de la siguiente manera:

> [!div class="mx-imgBorder"]
> ![host-local](media/local-host.png "host local")

> [!div class="mx-imgBorder"]
> ![componente-depuración](media/debug-control-1.png "Componente de depuración 1")


 > [!NOTE]
 > Puede usar los siguientes pasos para realizar la depuración externa de bucle mediante Fiddler.
 >    1. Instale [Fiddler](https://www.telerik.com/download/fiddler)
 >    2. Siga los pasos para configurar [AutoResponder](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)

## <a name="deploying-your-powerapps-component-framework-components"></a>Implementar los componentes del marco de componentes de PowerApps

Una vez que finalice la depuración y el desarrollo, solo le queda un paso - implementar su nuevo componente.  

Siga los pasos indicados a continuación para crear e importar un archivo de [solución](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/solutions-overview):

1. Cree un nuevo directorios y vaya a él 'cd <new directory name>'
2. Cree un nuevo proyecto de solución en el directorio que elija usando el comando `pac solution init --publisherName <enter your publisher name> --customizationPrefix <enter your publisher name>` después de `cd <your new folder>`.

   > [!NOTE]
   > Los valores [publisherName](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/reference/entities/publisher) y [cutomizationPrefix](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/change-solution-publisher-prefix) deben ser únicos a su entorno.
 
3. Cuando se crea el nuevo proyecto de solución, debe hacer referencia a la ubicación donde se ubica el componente creado. Puede agregar la referencia usando el comando `pac solution add-reference --path <path or relative path of your PowerApps component framework project on disk>`
4. Para generar un archivo zip del proyecto de la solución, deberá `cd` en el directorio del proyecto de la solución y compilar el proyecto usando el comando `msbuild /t:restore` y luego `msbuild`

    > [!NOTE]
    > Si msbuild 15 no está en la ruta, abra Developer Command Prompt for Vs 2017 para ejecutar los comandos `msbuild`.

    > [!NOTE]
    > Al compilar la solución en la configuración de depuración, se genera un paquete de la solución no administrada. Un paquete de la solución administrada se genera compilando la solución en la configuración de versión. Estos valores pueden ser reemplazados especificando la propiedad SolutionPackageType en el archivo `cdsproj`.
    
    > [!NOTE]
    > Si desea que la compilación del proyecto emita una solución administrada o administrada y no administrada, abra la carpeta en la que creó el proyecto de solución, edite el archivo `cdsproj` y quite la marca de comentario del grupo de propiedades siguiente:
      ```XML
         <PropertyGroup>
          <SolutionPackageType>Managed</SolutionPackageType>
           </PropertyGroup>
      ```

    > [!NOTE]
    > También puede habilitar el empaquetamiento de soluciones adicionales [capacidades](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/compress-extract-solution-file-solutionpackager) agregando cualquiera de los elementos del grupo de propiedades a continuación:

     ```XML
       <PropertyGroup>
         <SolutionPackageErrorLevel />
         <SolutionPackageEnableLocalization />
        <SolutionPackagerWorkingDirectory />
        <SolutionPackageLogFilePath />
        <SolutionPackageZipFilePath />
        <SolutionPackageMapFilePath />
       </PropertyGroup>
     ```

5. El archivo zip generado de la solución se encuentra en `\bin\debug\`.
6. Debe [importar la solución](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-export-solutions) manualmente mediante el portal web una vez que el archivo zip esté listo.

## <a name="adding-custom-controls-to-entity-or-a-field"></a>Agregar controles personalizados a un campo o una entidad

Para agregar un componente personalizado como el componente del conjunto de datos o un componente de una tabla sencilla a una cuadrícula o vista, siga los pasos a los que se hace referencia en el tema [Agregar controles a campos y entidades](add-custom-controls-to-a-field-or-entity.md). 

## <a name="telemetry"></a>Telemetría

La característica de equipo está agregando telemetría anónima para comprender qué características o capacidades de la herramienta PowerApps CLI usan con más frecuencia los desarrolladores. Los datos agregados nos permiten proporcionar la mejor experiencia a los clientes centrándonos en lo verdaderamente importante.

> [!NOTE]
> Para deshabilitar la colección de telemetría, ejecute el comando `pac telemetry --enable false`. Para volver a activar la telemetría, use el comando `pac telemetry --enable true`.

## <a name="how-to-uninstall-microsoft-powerapps-cli"></a>Cómo desinstalar Microsoft PowerApps CLI

Para desinstalar la herramienta CLI ejecute MSI desde [aquí](http://download.microsoft.com/download/D/B/E/DBE69906-B4DA-471C-8960-092AB955C681/powerapps-cli-0.1.51.msi). Si usted es participante de Versión preliminar privada y tiene una versión anterior de CLI, siga los pasos manuales siguientes:

1. Para averiguar dónde está instalado PowerApps CLI, abra un símbolo del sistema y escriba `where pac`
1. Elimine la carpeta de PowerAppsCLI.
1. Abra la herramienta de variables de entorno ejecutando el comando `rundll32 sysdm.cpl,EditEnvironmentVariables` en el símbolo del sistema
1. Haga doble clic en `Path` en la sección `User variable for...`
1. Seleccione la fila que contiene la ruta de PowerAppsCLI y haga clic en el botón Eliminar en el lado derecho
1. Haga clic en Aceptar dos veces.

## <a name="known-configuration-issues-and-workarounds"></a>Problemas conocidos de configuración y soluciones alternativas

**Msbuild error MSB4036:**

1. El nombre de la tarea en el archivo del proyecto es igual que el nombre de la clase de tarea.
2. La clase de tarea es pública e implementa la interfaz de Microsoft.Build.Framework.ITask.
3. La tarea se declara correctamente con <UsingTask> en el archivo de proyecto o en los archivos *.tasks situados en el directorio <path>

**Resolución**

1. Abra el instalador de Visual Studio 
1. Para VS 2017, haga clic en Modificar 
1. Haga clic en Componentes individuales
1. En Herramientas de código, active **Destinos de NuGet y tareas de compilación**

### <a name="see-also"></a>Vea también

[Implementación de componentes en TypeScript](implementing-controls-using-typescript.md)<br/>
[Actualizar componentes existentes en nuevo formato de herramientas](updating-existing-controls.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
