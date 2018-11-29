---
title: Recursos web de página web (HTML) (aplicaciones basadas en modelos) | Microsoft Docs
description: Este tema trata de cómo implementar recursos web HTML y sus capacidades y limitaciones
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
# <a name="webpage-html-web-resources"></a>Recursos web de página web (HTML)

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webpage-html-web-resources -->

Use los recursos web de la página web (HTML) para crear los elementos de la interfaz de usuario para las extensiones de cliente.

<a name="BKMK_Capabilities"></a>

## <a name="capabilities-of-html-web-resources"></a>Capacidades de los recursos web de HTML

Puesto que un recurso web HTML solo se transmite en secuencias al explorador del usuario, puede incluir cualquier contenido que se represente en el explorador del usuario.  

<a name="BKMK_Limitations"></a>

## <a name="limitations-of-html-web-resources"></a>Limitaciones de los recursos web de HTML  

- Un recurso web HTML no puede contener ningún código que se deba ejecutar en el servidor. Las páginas ASP.NET no se pueden cargar como recursos web HTML.

- Los recursos web HTML solo pueden aceptar un número limitado de parámetros de cadena de consulta. [Pasar los parámetros a recursos web HTML](webpage-html-web-resources.md#BKMK_PassingParametersToWebResources)  

<a name="BKMK_UsingTextEditor"></a>

## <a name="use-the-text-editor-for-html-web-resources"></a>Use el editor de texto de los recursos web HTML

 El editor de texto proporcionado en el formulario de recursos web se usa con la edición HTML, muy sencilla. Para obtener documentos HTML más sofisticados, debe modificar el código en un editor externo y usar el botón **Examinar** para cargar los contenidos del archivo.

 Por ejemplo, una página HTML más compleja que requiere que el script represente el contenido de la página empezará como el siguiente ejemplo.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
 <title></title>
 <script src="Script/Script.js" type="text/javascript"></script>
 <link href="CSS/Styles.css" rel="stylesheet" type="text/css" />
</head>
<body onload="SDK.ImportWebResources.showData()">
 <div id="results" />
</body>
</html>
```

 Cuando el documento se abra y se guarde en el editor de texto, el HTML se cambiará y pasará a esto.  

```html
<HTML><HEAD><TITLE></TITLE>
<META charset=utf-8></HEAD>
<BODY contentEditable=true onload=SDK.ImportWebResources.showData()>
<SCRIPT type=text/javascript src="Script/Script.js"></SCRIPT>
 <LINK rel=stylesheet type=text/css href="CSS/Styles.css">
<DIV id=results></DIV></BODY></HTML>
```

<a name="BKMK_PreventEditing"></a>

## <a name="prevent-editing-of-web-resources-for-managed-solutions"></a>Evitar la edición de recursos web de soluciones administradas

Debido a la característica HTML en recursos web que permite las modificaciones mediante el editor de texto, se recomienda que se usen propiedades administradas para establecer recursos web HTML complejos como no personalizables para soluciones administradas. Para ver los recursos web en la ventana de soluciones, abra el cuadro de diálogo **Propiedades administradas** para establecer la propiedad **Personalizable** en `false`.  

<a name="BKMK_ReferencingOtherWebResources"></a>

## <a name="reference-other-web-resources-from-an-html-web-resource"></a>Hacer referencia a otros recursos web desde un recurso web HTML

 Puede crear un conjunto de archivos relacionados fuera de aplicaciones basadas en modelos que use los tipos de archivo de recursos web. Si siempre usa rutas de acceso relativas e importa cada recurso web con una convención de nomenclatura coherente que refleje la estructura de carpetas del sitio web, verá que el recurso web HTML mantiene los vínculos con CSS, XML, JScript, imágenes y archivos Silverlight relacionados que se han importado como recursos web.  

 Por ejemplo, si crea un proyecto de aplicación web que usa la siguiente estructura de [carpeta]/archivo:  

-   page.htm

-   [Estilos]

    -   style.css
  
-   [Scripts] 
  
    -   script.js
  
 Al importar estos archivos como recursos web, puede poner un nombre en el que el prefijo de personalización del editor de soluciones sea "new", de la siguiente manera:  
  
-   `new_/page.htm`  
  
-   `new_/Styles/style.css`  
  
-   `new_/Scripts/script.js`  
  
 Si sigue este patrón, el recurso web `new_/page.htm` HTML puede hacer referencia a los otros archivos de la manera más habitual, utilizando rutas relativas, como se muestra en el ejemplo siguiente.  

```html
<script src="Scripts/script.js" type="text/javascript"></script>
<link href="Styles/style.css" rel="stylesheet" type="text/css" />
```

 El prefijo de personalización del editor de soluciones se convierte en una carpeta raíz virtual para todos los recursos web de la solución. Si cambia el prefijo de personalización, las rutas relativas en los recursos web HTML no se cambiarán.  
  
> [!NOTE]
>  - Un recurso web HTML agregado a un formulario no puede usar objetos globales definidos por la biblioteca JavaScript cargada en el formulario. Un recurso web HTML pueden interactuar con los objetos `Xrm.Page` o `Xrm.Utility` dentro del formulario mediante `parent.Xrm.Page` o `parent.Xrm.Utility`, pero los objetos globales definidos por scripts del formulario no serán accesibles utilizando el elemento principal. Debe cargar todas las bibliotecas que un recurso web HTML necesite dentro del un recurso web HTML de modo que no dependa de los scripts cargados en el formulario.  
> - Las referencias incluidas en código entre los recursos web no se siguen como dependencias de solución.  

 Dado que también se descargan recursos web para usuarios de Dynamics 365 for Microsoft Office Outlook con acceso sin conexión, los usuarios tendrán acceso al contenido del recurso web mientras están desconectados.  

<a name="BKMK_PassingParametersToWebResources"></a>

## <a name="pass-parameters-to-html-web-resources"></a>Pasar los parámetros a recursos web HTML

 Un recurso web HTML solo puede aceptar los parámetros de la tabla siguiente.

|Parámetro|Nombre|Descripción|
|---------------|----------|-----------------|
|typename|Nombre de entidad|El nombre de la entidad.|
|tipo|Código de tipo de entidad|Entero que identifica de forma única la entidad en una organización específica.|
|id.|GUID de objeto|GUID que representa un registro.|
|orgname|Nombre de la organización|Nombre único de la organización.|
|userlcid|Código de idioma de usuario|Identificador del código de idioma que usa el usuario actual.|
|orglcid|Código de idioma de la organización|Identificador del código de idioma que representa el idioma base de la organización.|
|Datos de |Parámetros de datos opcionales|Valor opcional que se puede pasar.|
|formid|Identificador del formulario|GUID que representa un Id. de formulario.|
|entrypoint|Punto de entrada|Un valor de cadena. Este parámetro está diseñado para pasarse como valor opcional a recursos web abiertos como contenido de ayuda personalizado para una entidad. Cuando está habilitada, la dirección URL de ayuda personalizada incluirá un valor de "formulario" o "hierarchychart".|
|pagemode||Solo para uso interno.|
|seguridad||Solo para uso interno.|
|tabSet||Solo para uso interno.|

 Para pasar más de un valor en el parámetro de datos, debe codificar los parámetros en el valor del parámetro de datos y después incluir lógica para descodificar varios parámetros mediante el script en el recurso web HTML. El tema [Ejemplo: Pasar varios valores a un recurso web a través de los datos parámetro](sample-pass-multiple-values-web-resource-through-data-parameter.md) muestra una solución para dirigirse pasando varios valores de parámetros.  

### <a name="see-also"></a>Vea también
 [Recursos web](web-resources.md)   
 [Crear recursos web accesibles](create-accessible-web-resources.md)   
 [Uso de recursos web de hojas de estilo (CSS)](css-web-resources.md)   
 [Usar recursos web de script (JScript)](script-jscript-web-resources.md)   
 [Uso de recursos web de datos (XML)](data-xml-web-resources.md)   
 [Uso de recursos web de imagen (JPG, PNG, GIF)](image-web-resources.md)   
 [Uso de recursos web de hoja de estilo (XSL)](stylesheet-xsl-web-resources.md)
