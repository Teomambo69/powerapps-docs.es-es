---
title: Herramienta SolutionPackager (Common Data Service) | Microsoft Docs
description: SolutionPackager es una herramienta que puede descomponer de forma reversible un archivo de solución comprimido de Common Data Service en varios archivos XML y otros archivos de forma que el sistema de control de código fuente pueda administrarlos fácilmente.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="solutionpackager-tool"></a>Herramienta SolutionPackager 

SolutionPackager es una herramienta que puede descomponer de forma reversible un archivo de solución comprimido de Common Data Service en varios archivos XML y otros archivos de forma que el sistema de control de código fuente pueda administrarlos fácilmente. Las secciones siguientes muestran cómo ejecutar la herramienta y cómo usar la herramienta con soluciones administradas y no administradas.  
  
<a name="bkm_where"></a>   

## <a name="where-to-find-the-solutionpackager-tool"></a>Dónde encontrar la herramienta de SolutionPackager  

 La herramienta SolutionPackager se distribuye como parte del paquete de NuGet [Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools). Ver [Descargar herramientas de NuGet](download-tools-nuget.md) para obtener información sobre cómo descargarlo.
  
<a name="arguments"></a>   

## <a name="solutionpackager-command-line-arguments"></a>Argumentos de la línea de comandos para SolutionPackager  

 SolutionPackager es una herramienta de línea de comandos que se puede invocar con los parámetros identificados en la tabla siguiente.  
  
|Argumento|Descripción|  
|--------------|-----------------|  
|/action: {Extract&#124;Pack}|Requerido. La acción para realizar. Una acción puede ser extraer un archivo .zip de solución en una carpeta, o comprimir una carpeta en un archivo .zip.|  
|/zipfile: \<ruta del archivo>|Requerido. La ruta y el nombre de un archivo .zip de solución. Para extraer, el archivo debe existir y ser de lectura. Al comprimir, se reemplaza el archivo.|  
|/folder: \<ruta de carpeta>|Requerido. La ruta a una carpeta. Al extraer, esta carpeta se crea y se rellena con los archivos componentes. Al comprimir, esta carpeta debe existir y contener los archivos componentes extraídos anteriormente.|  
|/packagetype: {Unmanaged&#124;Managed&#124;Both}|Opcional. Tipo de paquete para procesar. El valor predeterminado es Unmanaged. Este argumento se puede omitir en la mayoría de las ocasiones porque el tipo de paquete se puede leer desde dentro del archivo .zip o de los archivos componentes. Cuando se extrae y se especifica Both, los archivos .zip de solución administrada y no administrada deben estar presentes y procesarse en una sola carpeta. Cuando se comprime y se especifica Both, los archivos .zip de solución administrada y no administrada se crearán desde una carpeta. Para obtener más información, vea la sección sobre cómo trabajar con soluciones administradas y no administradas más adelante en este tema.|  
|/allowWrite:{Yes&#124;No}|Opcional. El valor predeterminado es Sí. Este argumento solo se usa durante una extracción. Cuando se especifica /allowWrite:No, la herramienta realiza todas las operaciones pero se evita que escriba o elimine cualquier archivo. La operación de extracción se puede evaluar con seguridad sin sobrescribir o eliminar ningún archivo existente.|  
|/allowDelete:{Yes&#124;No&#124;Prompt}|Opcional. El valor predeterminado es Prompt. Este argumento solo se usa durante una extracción. Cuando se especifica /allowDelete:Yes, los archivos presentes en la carpeta especificados por el parámetro /folder y que no se esperan, se eliminan de forma automática. Cuando se especifica /allowDelete:No, no se produce ninguna eliminación. Cuando se especifica /allowDelete:Prompt, se pide al usuario, a través de la consola, que permita o deniegue todas las operaciones de eliminación. Tenga en cuenta que si se especifica /allowWrite:No, no se producirán eliminaciones incluso si también se especifica /allowDelete:Yes.|  
|/clobber|Opcional. Este argumento solo se usa durante una extracción. Cuando se especifica /clobber, los archivos que tienen el atributo de solo lectura establecido se sobrescriben o eliminan. Cuando no se especifica, los archivos con atributo de solo lectura no se sobrescriben ni eliminan.|  
|/errorlevel: {Off&#124;Error&#124;Warning&#124;Info&#124;Verbose}|Opcional. El valor predeterminado es Info. Este argumento indica el nivel de información del registro para el resultado.|  
|/map: \<ruta de archivo>|Opcional. La ruta y el nombre de un archivo .xml que contiene directivas de asignación de archivos. Cuando se usa durante una extracción, los archivos suelen leer desde dentro de la carpeta especificada por el parámetro /folder y se leen desde ubicaciones alternativas tal como se especifica en el archivo de asignación. Durante la operación de compresión, los archivos que coinciden con las directivas no se escriben.|  
|/nologo|Opcional. Suprimir pancartas en tiempo de ejecución.|  
|/log: \<ruta de archivo>|Opcional. Una ruta y un nombre a un archivo de registro. Si ya existe el archivo, se agrega nueva información de registro al archivo.|  
|@ \<ruta de archivo >|Opcional. Una ruta y un nombre de archivo que contiene los argumentos de la línea de comandos de la herramienta.|  
|/sourceLoc: \<cadena>|Opcional. Este argumento genera un archivo de recursos de la plantilla, y solo es válido en el extracto.<br /><br /> Los valores posibles son `auto` o código de LCID/ISO para el idioma que desea exportar. Cuando se usa este argumento, se extraen los recursos de la cadena de configuración regional determinada como archivo de .resx neutro. Si `auto` o la forma larga o corta del cambio se especifica, se utilizan el local base o la solución. Puede usar la forma corta de comando: /src.|  
|/localize|Opcional. Extraiga o combine todos los recursos de cadena en los archivos de .resx. Puede usar la forma corta del comando: /loc.|  
  
<a name="use_command"></a>   

## <a name="use-the-map-command-argument"></a>Use el argumento del comando de /map  

La siguiente discusión detalla el uso del argumento /map a la herramienta SolutionPackager.  
  
Los archivos que están integrados en un sistema automatizado de compilación, como archivos .xap de Silverlight y ensamblados de complementos, no se comprueban normalmente en el control de origen. Los recursos web pueden estar presentes en control de origen en ubicaciones que no son directamente compatibles con la herramienta SolutionPackager. Al incluir el parámetro /map, se puede hacer que la herramienta SolutionPackager lea y comprima dichos archivos de ubicaciones alternativas y no desde la carpeta Extract como se haría habitualmente. El parámetro /map debe especificar el nombre y la ruta a un archivo XML que contiene directivas de asignación que indican al SolutionPackager que haga coincidir los archivos por su nombre y su ruta, e indica la ubicación alternativa para buscar el archivo que coincide. La siguiente información se aplica a todas las directivas de igual forma.  
  
- Se pueden enumerar varias directivas incluyendo las que coinciden con archivos idénticos. Las directivas que se enumeran al principio del archivo tienen prioridad sobre las que se enumeran después.  
  
- Si un archivo se hace coincidir con una directiva, se debe encontrar en al menos una ubicación alternativa. Si no se encuentran alternativas que coincidan, el SolutionPackager emitirá un error.  
  
- Las rutas de la carpeta y el archivo pueden ser absolutas o relativas. Las rutas relativas se evalúan siempre desde la carpeta especificada por el parámetro /folder.  
  
- Las variables de entorno se pueden especificar utilizando una sintaxis %variable%.  
  
- Se puede utilizar un comodín de carpeta "**" para indicar "en cualquier subcarpeta". Puede usarse solo como la parte final de una ruta, por ejemplo: “c:\folderA\\\*\*”.  
  
- Los comodines de nombre de archivo se pueden usar únicamente en las formas “*.ext” o “\*.\*”. No se admite ningún otro patrón.  
  
  Aquí se describen los tres tipos de asignaciones de las directivas, junto con un ejemplo que muestra cómo puede usarlos.  
  
<a name="Folder_mapping"></a>   

### <a name="folder-mapping"></a>Asignación de carpeta  

A continuación se ofrece información detallada sobre la asignación de carpetas.  
  
**Formato XML**

`<Folder map="folderA" to="folderB" />`  
  
**Descripción**

Las rutas de acceso que coincidan con "folderA" se cambiarán a "folderB".  
  
- La jerarquía de subcarpetas bajo cada una debe coincidir exactamente.  
  
- No se admiten los comodines de carpeta.  
  
- No se pueden especificar nombres de archivos.  
  
  **Ejemplos**

  ```xml  
  <Folder map="folderA" to="folderB" />  
  <Folder map="folderA\folderB" to="..\..\folderC\" />  
  <Folder map="WebResources\subFolder" to="%base%\WebResources" />  
  ```  
  
<a name="file_mapping"></a>   

### <a name="file-to-file-mapping"></a>Asignación de archivo a archivo  

A continuación se muestra información detallada sobre asignación de archivo a archivo.  
  
 **Formato XML**

`<FileToFile map="path\filename.ext" to="path\filename.ext" />`  
  
**Descripción**

Cualquier archivo que coincida con el parámetro de `map` se leerá desde el nombre y la ruta especificados en el parámetro de `to`.  
  
 Para el parámetro de `map`:  
  
- Se debe especificar un archivo. La ruta es opcional. Si no se especifica una ruta, deben hacerse coincidir los archivos de cualquier carpeta.  
  
- No se admiten los comodines de nombre de archivo.  
  
- Se admite el comodín de la carpeta.  
  
  Para el parámetro de `to`:  
  
- Se debe especificar un nombre de archivo y una ruta.  
  
- El nombre de archivo puede ser distinto del nombre del parámetro de `map`.  
  
- No se admiten los comodines de nombre de archivo.  
  
- Se admite el comodín de la carpeta.  
  
**Ejemplos**

```xml  
  <FileToFile map="assembly.dll" to="c:\path\folder\assembly.dll" />  
  <FileToFile map="PluginAssemblies\**\this.dll" to="..\..\Plugins\**\that.dll" />  
  <FileToFile map="Webresrouces\ardvark.jpg" to="%SRCBASE%\CrmPackage\WebResources\JPG format\aardvark.jpg" />  
```  
  
<a name="file_path_mapping"></a>   

### <a name="file-to-path-mapping"></a>Asignación de archivo a ruta  

A continuación se muestra información detallada sobre asignación de archivo a ruta.  
  
**Formato XML**

`<FileToPath map="path\filename.ext" to="path" />`  
  
**Descripción**  
 
Cualquier archivo que coincida con el parámetro de `map` se leerá desde la ruta especificada en el parámetro de `to`.  
  
Para el parámetro de `map`:  
  
- Se debe especificar un archivo. La ruta es opcional. Si no se especifica una ruta, deben hacerse coincidir los archivos de cualquier carpeta.  
  
- Se admiten los comodines de nombre de archivo.  
  
- Se admite el comodín de la carpeta.  
  
Para el parámetro de `to`:  
  
- Se debe especificar una ruta.  
  
- Se admite el comodín de la carpeta.  
  
- No se debe especificar un nombre de archivo.  
  
  **Ejemplos**

```xml  
  <FileToPath map="assembly.dll" to="c:\path\folder" />  
  <FileToPath map="PluginAssemblies\**\this.dll" to="..\..\Plugins\bin\**" />  
  <FileToPath map="*.jpg" to="%SRCBASE%\CrmPackage\WebResources\JPG format\" />  
  <FileToPath map="*.*" to="..\..\%ARCH%\%TYPE%\drop" />  
```  
  
<a name="Example_mapping"></a>   

### <a name="example-mapping"></a>Asignación de ejemplo  
El siguiente ejemplo de código XML muestra un archivo de asignación completo lo que permite que la herramienta SolutionPackager lea cualquier recurso web y los dos ensamblados generados predeterminados desde un proyecto de Developer Toolkit denominado CRMDevTookitSample.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Mapping>  
       <!-- Match specific named files to an alternate folder -->  
       <FileToFile map="CRMDevTookitSamplePlugins.dll" to="..\..\Plugins\bin\**\CRMDevTookitSample.plugins.dll" />  
       <FileToFile map="CRMDevTookitSampleWorkflow.dll" to="..\..\Workflow\bin\**\CRMDevTookitSample.Workflow.dll" />  
       <!-- Match any file in and under WebResources to an alternate set of sub-folders -->  
       <FileToPath map="WebResources\*.*" to="..\..\CrmPackage\WebResources\**" />  
       <FileToPath map="WebResources\**\*.*" to="..\..\CrmPackage\WebResources\**" />  
</Mapping>  
```  
  
<a name="managed"></a>   

## <a name="managed-and-unmanaged-solutions"></a>Soluciones administradas y no administradas  

 Un archivo comprimido de solución Common Data Service (.zip) se puede exportar en uno de dos tipos como se indica a continuación.  
  
 **Solución administrada**  
 Una solución completada lista para importarse en una organización. Una vez importados, los componentes no se pueden agregar ni quitar, aunque podrán permitir opcionalmente una mayor personalización. Esto se recomienda cuando el desarrollo de la solución esté completo.  
  
 **Solución no administrada**  
 Una solución abierta sin restricciones sobre qué se puede agregar, quitar o modificar. Esto se recomienda durante el desarrollo de una solución.  
  
 El formato de un archivo comprimido de solución será diferente en función del tipo, ya sea administrado o no administrado. El SolutionPackager puede procesar archivos de solución comprimidos de cualquier tipo. Sin embargo, la herramienta no puede convertir un tipo a otro. La única forma de convertir los archivos de solución a un tipo diferente, por ejemplo de no administrada a administrada, es importando el archivo de solución no administrada .zip en un servidor de Common Data Service y después exportando la solución como una solución administrada.  
  
 SolutionPackager puede procesar archivos .zip de soluciones administradas y no administradas como un conjunto combinado mediante el parámetro /PackageType:Both. Para realizar esta operación, es necesario exportar la solución dos veces en cada tipo, nombrando los archivos .zip de la forma siguiente.  
  
|||  
|-|-|  
|Unmanaged .zip file: AnyName.zip|Managed .zip file: AnyName_managed.zip|  
  
 La herramienta asumirá la presencia del archivo .zip administrado en la misma carpeta que el archivo no administrado y extraerá ambos archivos en una sola carpeta que mantiene las diferencias en caso de componentes administrados y no administrados.  
  
 Una vez que una solución se ha extraído como no administrada y administrada, es posible comprimir ambas desde esa única carpeta o cada tipo de forma individual, utilizando el parámetro /PackageType para especificar qué tipo crear. Al especificar los dos, se crearán dos archivos .zip mediante la convención de nomenclatura anterior. Si el parámetro /PackageType se pierde al comprimir desde una carpeta dual administrada y no administrada, de forma predeterminada se produce un solo archivo .zip no administrado.  
  
## <a name="troubleshooting"></a>Solución de problemas  

Si usa Visual Studio 2012 para editar los archivos de recursos creados por el empaquetador de la solución, puede recibir un mensaje cuando se vuelve a comprimir similar a este: `“Failed to determine version id of the resource file <filename>.resx the resource file must be exported from the solutionpackager.exe tool in order to be used as part of the pack process.”` Esto ocurre porque Visual Studio reemplaza las etiquetas de los metadatos del archivo de recursos con las etiquetas de datos.  
  
#### <a name="workaround"></a>Solución alternativa  
  
1. Abra el archivo de recursos en el editor de texto que prefiera y encuentre las siguientes etiquetas:  
  
   ```xml  
   <data name="Source LCID" xml:space="preserve">  
   <data name="Source file" xml:space="preserve">  
   <data name="Source package type" xml:space="preserve">  
   <data name="SolutionPackager Version" mimetype="application/x-microsoft.net.object.binary.base64">  
  
   ```  
  
2. Cambie el nombre del nodo de `<data>` a `<metadata>`.  
  
    Por ejemplo, esta cadena:  
  
   ```xml  
   <data name="Source LCID" xml:space="preserve">  
     <value>1033</value>  
   </data>  
  
   ```  
  
    Cambia a:  
  
   ```xml  
   <metadata name="Source LCID" xml:space="preserve">  
     <value>1033</value>  
   </metadata>  
  
   ```  
  
   Esto permite que el empaquetador de la solución lea e importe el archivo de recursos. Este problema se observa solo al utilizar el editor de recursos de Visual Studio.  
  
### <a name="see-also"></a>Vea también  
 [Control de código fuente con archivos de solución](use-source-control-solution-files.md)<br/>   
 [Referencia de archivo de componente de la solución](solution-component-file-reference-solutionpackager.md)<br/>   
 [Introducción a soluciones](introduction-solutions.md)
