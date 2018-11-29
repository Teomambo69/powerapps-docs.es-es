---
title: 'Paso 4: Crear un paquete de AppSource para la aplicación (Common Data Service para aplicaciones) | Microsoft Docs'
description: Obtenga información sobre cómo crear un paquete de AppSource (archivo .zip) para incluir los archivos de datos de demostración y de la solución junto con otros archivos necesarios.
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
# <a name="step-4-create-an-appsource-package-for-your-app"></a>Paso 4: Crear un paquete de AppSource para la aplicación

Debe crear un paquete de AppSource (archivo .zip) para incluir los archivos de datos de demostración y de la solución junto con otros archivos necesarios. Un paquete AppSource consta de los archivos siguientes:

|Archivo|Descripción|
|--|--|
|Archivo de paquete|Un archivo de paquete utilizado por la herramienta Package Deployer para implementar las soluciones y los datos de la configuración de prueba en varios idiomas.|
|[Tipos_contenido].xml|Archivo que proporciona información de tipo MIME sobre las extensiones de tipos de archivo en el paquete de AppSource. Normalmente son tipos de archivos .config, .dll, .exe, .xml y .zip, pero se puede agregar prácticamente cualquier tipo de archivo que sea compatible con Windows.|
|Archivo de icono|Un archivo de imagen para el icono de paquete appsource; el tamaño debería ser de 32 x 32 píxeles. Los formatos de imagen válidos son PNG y JPG.|
|Archivo HTML|Archivo que contiene los términos de licencia.|
|input.xml|Archivos que describen el activos del paquete de AppSource.|


## <a name="create-a-package-file"></a>Crear un archivo de paquete

Un paquete le permite agrupar y distribuir varios archivos relacionados con la aplicación a la vez. 

1. Crear un paquete de Dynamics 365 para incluir los archivos de datos de configuración y la solución que haya creado en [Paso 2: crear una solución administrada para su aplicación](create-solution-app-appsource.md). Un paquete también puede contener código personalizado que puede ejecutarse antes, durante o después de que se implemente el paquete en la instancia de CDS for Apps. Para obtener más información sobre la creación de archivos de paquete, consulte [Crear paquetes para el Package Deployer de Dynamics 365](/dynamics365/customer-engagement/developer/create-packages-package-deployer).

    Después de crear un paquete, el paquete constará de lo siguiente:

    - Carpeta **\<nombrepaquete>**: Esta carpeta contiene todas las soluciones, datos de configuración, archivos sin formato y contenido para el paquete. Por ejemplo: **PkgFolder**.  
  
    - **\<PackageName>.dll**: el ensamblado contiene el código personalizado para el paquete. Por ejemplo: **SamplePackage.dll**.

2. A continuación, cree un archivo **[Tipo_contenido].xml** que proporcione información de tipo MIME de las extensiones de tipos de archivo que se incluyen en su paquete. Esto es independiente del archivo que se volverá a incluir en el paquete de AppSource. Aquí tiene un contenido de ejemplo de un archivo Tipos_contenido].xml con tipos de archivo enumerados:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="xml" ContentType="application/octet-stream" />
      <Default Extension="xaml" ContentType="application/octet-stream" />
      <Default Extension="dll" ContentType="application/octet-stream" />
      <Default Extension="zip" ContentType="application/octet-stream" />
      <Default Extension="jpg" ContentType="application/octet-stream" />
      <Default Extension="gif" ContentType="application/octet-stream" />
      <Default Extension="png" ContentType="application/octet-stream" />
      <Default Extension="htm" ContentType="application/octet-stream" />
      <Default Extension="html" ContentType="application/octet-stream" />
      <Default Extension="db" ContentType="application/octet-stream" />
      <Default Extension="css" ContentType="application/octet-stream" />
    </Types>
    ```

3. Comprima (zip) los archivos siguientes en un archivo denominado *package.zip*:
   - Carpeta de paquete (PkgFolder)
   - Paquete de dll (SamplePackage.dll)
   - [Tipos_contenido].xml

     Para comprimir estos archivos, vaya a la carpeta donde estos archivos están presentes, selecciónelos todos, haga clic con el botón derecho del mouse y seleccione **Enviar a** > **carpeta comprimida (zip)**.

     ![Comprima los archivos de un paquete](media/appsource-zip-package.png) 

4. Cambie el nombre del archivo .zip por **package.zip**.

## <a name="create-contenttypesxml"></a>Cree [Tipos_contenido].xml

Puede volver a utilizar el archivo **[Tipos_contenido].xml** que ha creado en la sección anterior en el paso 2.

## <a name="create-an-icon-for-your-appsource-package"></a>Cree un icono para el paquete de AppSource

Cree un archivo de icono del tamaño de 32 x 32 para mostrar junto con el nombre de la solución preferida y la descripción en el portal del centro de administración de Dynamics 365. Los formatos de archivo válidos son PNG y JPG.

## <a name="create-an-html-file-for-license-terms"></a>Cree un archivo HTML para términos de licencia

Cree un archivo HTML que contiene los términos de licencia. Puede tener un archivo HTML por idioma para mostrar los términos de licencia en el idioma de usuario seleccionado si la aplicación admite varios idiomas.

## <a name="create-inputxml-file"></a>Cree el archivo input.xml

Cree un archivo *input.xml* que proporciona información sobre el paquete y el contenido del paquete. Aquí se muestra el contenido de un archivo **input.xml** de muestra; cada elemento se explica más adelante en la tabla.

```xml
<?xml version="1.0" encoding="utf-8"?>
<PvsPackageData>
  <ProviderName>Microsoft</ProviderName>
  <PackageFile>package.zip</PackageFile>
  <SolutionAnchorName>SampleSolution.zip</SolutionAnchorName>
  <StartDate>12/01/2017</StartDate>
  <EndDate>01/01/2021</EndDate>
  <SupportedCountries>US,CA</SupportedCountries>
  <LearnMoreLink>http://www.microsoft.com</LearnMoreLink>
  <Locales>
    <PackageLocale Code="1033" IsDefault="true">
      <Logo>logo32x32.png</Logo>
      <Terms>
        <PackageTerm File="TermsOfUse.html" />
      </Terms>
    </PackageLocale>
  </Locales>
</PvsPackageData>
```


Aquí tiene una descripción de los elementos del archivo **input.xml**.

|Elemento|Descripción|
|--|--|
|ProviderName|Nombre del proveedor de soluciones. Si lo crea un equipo interno de Microsoft, especifique **Microsoft**.|
|PackageFile|Nombre de paquete (archivo .zip) para la herramienta Package Deployer. Este archivo zip debería contener el conjunto de paquete, la carpeta de paquete con los activos de la aplicación y el archivo Tipos_contenido.xml. Por ejemplo, el archivo package.zip creado en la sección [crear un archivo de paquete](#create-a-package-file).|
|SolutionAnchorName|Nombre del archivo zip de la solución en el paquete que se usa para el nombre y la descripción de los activos de la solución.|
|SolutionAnchorName|Nombre del archivo zip de la solución en el paquete que se usa para el nombre y la descripción de los activos de la solución.|
|StartDate|Fecha en la que la aplicación comienza a estar disponible en AppSource. El formato es DD/MM/AAAA.|
|Fecha de finalización|Fecha en la que la aplicación deja de estar disponible en AppSource. El formato es DD/MM/AAAA.|
|SupportedCountries|Lista separada por comas de países o regiones donde la aplicación debería estar disponible. En el momento de escribir este artículo, la lista de países admitidos es la siguiente: AE,AL,AM,AO,AR,AT,AU,AZ,BA,BB,BD,BE,BG,BH,BM,BN,BO,BR,BY,CA,CH,CI,CL,CM,CO,CR,CV,CW,CY,CZ,DE,DK,DO,DZ,EC,EE,EG,ES,FI,FR,GB,GE,GH,GR,GT,HK,HN,HR,HU,ID,IE,IL,IN,IQ,IS,IT,JM,JO,JP,KE,KG,KN,KR,KW,KY,KZ,LB,LK,LT,LU,LV,LY,MA,MC,MD,ME,MK,MN,MO,MT,MU,MX,MY,NG,NI,NL,NO,NZ,OM,PA,PE,PH,PK,PL,PR,PS,PT,PY,QA,RO,RS,RU,RW,SA,SE,SG,SI,SK,SN,SV,TH,TM,TN,TR,TT,TW,UA,US,UY,UZ,VE,VI,VN,ZA,ZW|
|LearnMoreLink|Dirección URL de la página de información detallada de este paquete.|
|Locales|Instancia de este nodo para cada idioma que desee que se admita en la interfaz de usuario de soluciones preferidas. Este nodo contiene los elementos secundarios siguientes:<br/>- **PackageLocale.Code**: LCID del idioma de este nodo. Ejemplo: el inglés de Estados Unidos es 1033<br/>- **PackageLocale.IsDefault**: indica el idioma predeterminado. Se usa como idioma de reserva por si el idioma que el cliente elige no está disponible.<br/>- **Logo**: logotipo para el paquete de la aplicación. El tamaño de la imagen debe ser 32 x 32. Los formatos de imagen válidos son PNG y JPG.<br/>- **Términos**: nombre del archivo HTML que contiene los términos de licencia para cada idioma.|

## <a name="add-the-items-to-an-appsource-package"></a>Agregue los elementos a un paquete AppSource

El último paso consiste en agregar todos los componentes que haya creado previamente en un archivo único comprimido (zip), que será el paquete de origen de la aplicación.

1. Desplácese a la carpeta que contiene el archivo de paquete [Tipo_contenido]XML, el icono, el archivo de términos de la licencia (HTML), selecciónelos todos, haga clic con el botón derecho del mouse en y seleccione **Enviar a** > **Carpeta comprimida (zip)**.

    ![Paquete AppSource](media/appsource-package.png)

    > [!IMPORTANT]
    > Debe seguir la estructura de contenido precisamente para su paquete tal y como se indica aquí o de lo contrario el paquete generará un error durante la certificación. Algunos problemas comunes que dan lugar a un error de certificación son nombres de archivo incorrectos o una estructura de archivo anidada.

2. Cambie el nombre del archivo correctamente en función de la aplicación. Se recomienda incluir el nombre de su compañía y el nombre de la aplicación. Por ejemplo: **Microsoft_SamplePackage.zip**.
 

> [!div class="nextstepaction"]
> [Paso 5: Almacenar el paquete de AppSource en Azure Storage](store-appsource-package-azure-storage.md) 
