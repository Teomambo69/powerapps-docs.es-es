---
title: Recursos web (aplicaciones basadas en modelos) | Microsoft Docs
description: Los recursos web son archivos virtuales que se almacenan en la base de datos de CDS para aplicaciones y que se pueden recuperar mediante una dirección URL única.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-resources-in-model-driven-apps"></a>Recursos web en aplicaciones basadas en modelos

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/web-resources -->


Los recursos web son *archivos virtuales* que se almacenan en la base de datos de Common Data Service para aplicaciones y que se pueden recuperar mediante una dirección URL única.  
  
<a name="BKMK_CapabilitiesOfWebResources"></a>   
## <a name="capabilities-of-web-resources"></a>Capacidades de los recursos web  
 Los recursos web representan los archivos que se pueden usar para ampliar la aplicación web de CDS para aplicaciones, como los archivos html, JavaScript y CDS y diversos formatos de imagen. Puede usar recursos web en personalizaciones de formularios, el `SiteMap` o la aplicación de cinta de opciones porque se les puede hacer referencia mediante sintaxis URL.  
  
 La sintaxis URL para los recursos web permite referencias de la ruta de acceso relativa. Con las herramientas de desarrollo, se puede crear un grupo de archivos interdependientes en un servidor de desarrollo mediante tipos de archivos compatibles con los recursos web. A continuación, si se usa la convención de nomenclatura coherente y referencias de la ruta de acceso relativa, el sitio web funcionará después de cargar todos los archivos en CDS para aplicaciones.
  
 Puesto que los recursos web se almacenan en CDS para aplicaciones y son componentes de la solución, se pueden exportar e instalar fácilmente en otras organizaciones de CDS para aplicaciones. Los recursos web también están disponibles para los usuarios de CDS para aplicaciones para Microsoft Office Outlook con acceso sin conexión cuando están desconectados porque se sincronizan con los datos de usuario.  
  
 Puede usar el editor de formularios para agregar y configurar recursos web habilitados por formulario en los formularios de entidad.  
  
 Puesto que los recursos web se almacenan como registros en la base de datos, se pueden administrar mediante programación usando técnicas estándar para crear, recuperar y actualizar registros. Los recursos web basados en texto (JScript, CSS, XML, XSL, RESX, and HTML) se pueden editar y guardar en la aplicación.  
  
<a name="BKMK_LimitationsOfWebResources"></a>   
### <a name="limitations-of-web-resources"></a>Limitaciones de los recursos web  
 No hay ningún tipo de recurso web que admita las capacidades de una página ASP.NET(.aspx) para ejecutar código en el servidor. Los recursos web se limitan a archivos estáticos o a archivos que se procesan en el explorador. Un recurso web puede contener un código que se procesa en el explorador para ejecutar las llamadas al servicio web para interactuar con los datos de CDS para aplicaciones.
  
 Los recursos web solo están disponibles mediante el contexto de seguridad de la aplicación web de CDS para aplicaciones. Sólo los usuarios de CDS para aplicaciones con licencia con los privilegios necesarios pueden tener acceso a ellos.  
  
#### <a name="size-limitations"></a>Limitaciones de tamaño  
El tamaño máximo de los archivos que se pueden cargar se determina mediante la propiedad Organization.MaxUploadFileSize. Esta propiedad se define en la pestaña Correo electrónico de Configuración del sistema en la aplicación Dynamics 365. Esta configuración limita el tamaño de los archivos que pueden adjuntarse a los mensajes de correo electrónico, notas y recursos web. La configuración predeterminada es 5 MB.
  
<a name="BKMK_WebResourceTypes"></a>   
## <a name="web-resource-types"></a>Tipos de recursos web  
 Puede usar diez formatos de archivo para crear recursos web. En la siguiente tabla se enumera cada formato de archivo, las extensiones de archivo permitidas y el valor de tipo que se usa con cada uno.  
  
|Archivo|Extensiones de archivo|Tipo|  
|----------|---------------------|----------|  
|Página web (HTML)|.htm, .html|1|  
|Hoja de estilos (CSS)|.css|2|  
|Script (JScript)|.js|3|  
|Datos (XML)|.xml|4|  
|Imagen (PNG)|.png|5|  
|Imagen (JPG)|.jpg|6|  
|Imagen (GIF)|.gif|7|  
|Silverlight (XAP)|.xap|8|  
|Hoja de estilos (XSL)|.xsl, .xslt|9|  
|Imagen (ICO)|.ico|10|  
|Formato vectorial (SVG)|.svg|11|  
|Cadena (RESX)|.resx|12|  
  
<a name="BKMK_ReferencingWebResources"></a>   
## <a name="reference-web-resources"></a>Recursos web para referencias  
 Hay varios métodos que se pueden usar para hacer referencia a recursos web.  
  
> [!NOTE]
>  -   Cuando sea posible, use la directiva `$webresource`. Solo las referencias que usan la directiva `$webresource` en los comandos del mapa del sitio o de la cinta de opciones establecerán dependencias. Las dependencias no se crean cuando los recursos web se hacen referencia mutuamente.  
>       - Para mostrar un recurso web de Silverlight fuera de un formulario o gráfico de entidad, cree un recurso web HTML como página host para el recurso web de Silverlight. Después, use la directiva $webresource: para abrir el recurso web HTML.
  
<a name="BKMK_WebResourceDirective"></a>   
### <a name="webresource-directive"></a>Directiva $webresource  
 Debe usar siempre la directiva `$webresource` al hacer referencia a un recurso web de un control de la cinta de opciones o de una subárea de `SiteMap`. Use la directiva `$webresource` donde el XML permita un valor de dirección URL. En el siguiente ejemplo se muestra su uso.  
  
```xml  
$webresource:<name of Web Resource>  
```  
  
> [!NOTE]
>  Cuando se usa la directiva `$webresource`, CDS para aplicaciones creará o actualizará las dependencias de la solución.  
  
### <a name="xrmnavigationopenwebresource"></a>Xrm.Navigation.openWebResource  
 La función Xrm.Navigation.[openWebResource](clientapi/reference/Xrm-Navigation/openWebResource.md) abre una nueva ventana de recurso web HTML con los parámetros para pasar el nombre del recurso web, de los datos de cadena de consulta que se pasarán en el parámetro de datos, e información sobre el alto y ancho de la ventana.  
  
 La URL generada incluye el símbolo único GUID para que se cargue el recurso web almacenado en caché.  
  
<a name="BKMK_RelativeUrl"></a>   
### <a name="relative-url"></a>Dirección URL relativa  
 Al hacer referencia a un recurso web de las áreas que no son compatibles con la directiva `$webresource:`, se puede usar una URL relativa. Para habilitar esta opción, se recomienda usar una convención de nomenclatura coherente para los recursos web, que refleje una estructura de archivos virtual. El prefijo de personalización del editor de soluciones se incluirá siempre como prefijo del nombre del recurso web. Esto puede representar una carpeta "raíz" virtual para todos los recursos web agregados para ese editor. Puede usar posteriormente el carácter de barra diagonal (/) para simular una estructura de carpetas que se mantendrá en el servidor web.  
  
 Desde otro recurso web, debe usar siempre URL relativas para que se hagan referencia mutuamente. Por ejemplo, para que el recurso web de página web `new_/content/contentpage.htm` haga referencia al recurso web CSS `new_/Styles/styles.css`, establezca el vínculo de la siguiente manera:  
  
```html  
<link rel="stylesheet" type="text/css" href="../styles/styles.css" />  
```  
  
 Para que el recurso web de página web `new_/content/contentpage.htm` abra el recurso web de página web `isv_/foldername/dialogpage.htm` , establezca el vínculo de la siguiente manera:  
  
```html  
<a href="../../isv_/foldername/dialogpage.htm">Dialog Page</a>  
```  
  
> [!NOTE]
>  No use una URL relativa con la carpeta WebResources como la ruta raíz para la URL. Por ejemplo, no use esta opción: `/WebResources/<name of web resource>`. Cuando un usuario pertenece a más de una organización en un servidor, esta ruta se referirá siempre a la organización predeterminada. Si el usuario no está usando su organización predeterminada y el recurso web esperado no está incluido en la organización predeterminada del usuario, aparecerá el error "Archivo no encontrado" incluso si el recurso web aparece en la organización en la que está trabajando el usuario en ese momento.  
  
<a name="BKMK_FullUrl"></a>   
### <a name="full-url"></a>URL completo  
 El siguiente ejemplo muestra el estilo de URL que puede usar para ver los recursos web.  
  
```  
<CDS for Apps URL>/WebResources/<name of web resource>  
```  
  
 La aplicación procesará esta URL y devolverá el archivo que contiene la versión más reciente del recurso web. Esta URL tendrá este aspecto:  
  
```  
<CDS for Apps URL>/%7B<version value>%7D/WebResources/<name of web resource>  
```  
  
 El valor versión se actualiza cuando se publican personalizaciones y asegura que el explorador usa la versión más reciente almacenada en la memoria caché del recurso web. Por este motivo, use una ruta de acceso relativa a un recurso web, la función Xrm.Navigation.[openWebResource](clientapi/reference/Xrm-Navigation/openWebResource.md) o el [$webresource Directive](web-resources.md#BKMK_WebResourceDirective) (cuando sea posible) porque el valor versión se incluirá automáticamente. Para recursos web grandes las consecuencias en el rendimiento serán significativas si no usa la versión almacenada en la memoria caché del archivo.  
  
 El siguiente ejemplo muestra una dirección URL para CDS para aplicaciones, donde `MyOrganization` es el nombre de la organización y `new_/test/test.htm` es el nombre del recurso web:  
  
```  
https://MyOrganization.crm.dynamics.com/WebResources/new_/test/test.htm  
```  
  
> [!NOTE]
>  Incluir el carácter "/" y la extensión de nombre de archivo en el nombre del recurso web es una práctica recomendada opcional.  
  
  
 Cuando escriba código para hacer referencia a un recurso web que funciona para CDS para aplicaciones, debe usar la función [getClientUrl](clientapi/reference/Xrm-Utility/getGlobalContext/getClientUrl.md).

## <a name="community-tools"></a>Herramientas de la Comunidad

**WebResources Manager** es una herramienta que la comunidad XrmToolbox ha desarrollada para CDS para aplicaciones. Consulte el tema [herramientas para desarrolladores](developer-tools.md) para comunidad de herramientas desarrolladas.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de CDS for Apps y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com). 
  
### <a name="see-also"></a>Vea también  

 [Crear recursos web accesibles](create-accessible-web-resources.md)<br />
 [Recursos web de página web (HTML)](webpage-html-web-resources.md)<br />
 [Recursos web de Script (JScript)](script-jscript-web-resources.md)<br />
 [Recursos web de imágenes](image-web-resources.md)<br />
 [Recursos web de hoja de estilo (XSL)](stylesheet-xsl-web-resources.md)<br />
 [Recursos web (XML) de datos](data-xml-web-resources.md)<br />
 [Recursos web de hoja de estilo (CSS)](css-web-resources.md)<br />
 [Referencia de la entidad WebResource](../common-data-service/reference/entities/webresource.md)<br />
 [Ejemplo: Pasar varios valores a un recurso web mediante el parámetro de datos](sample-pass-multiple-values-web-resource-through-data-parameter.md)<br />
 [Ejemplo: Importación de archivos como recursos web](sample-import-files-web-resources.md)<br />
 [Agilice el desarrollo de recursos web con Fiddler AutoResponder](streamline-javascript-development-fiddler-autoresponder.md)
