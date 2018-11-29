---
title: Recursos web de script (JScript) (aplicaciones basadas en modelos) | Microsoft Docs
description: Más información sobre cómo usar recursos web JavaScript para crear una biblioteca de funciones de JavaScript a las que se puede acceder desde cualquier parte.
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
# <a name="script-jscript-web-resources"></a>Recursos web de script (JScript)

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/script-jscript-web-resources -->

Los recursos web de Script(JScript) se usan para crear una biblioteca de funciones de JScript a las que se puede acceder desde cualquier parte.  
  
<a name="BKMK_capabilties"></a>   
## <a name="capabilities-of-script-web-resources"></a>Capacidades de los recursos web de script  
 Con los recursos web de JavaScript, puede administrar de forma más eficiente el código usado en los scripts de formulario, los recursos web de página web (HTML) o los comandos de la cinta de opciones vinculándolos a una biblioteca compartida de funciones de JavaScript.  
  
<a name="BKMK_limitations"></a>   
## <a name="limitations-of-script-web-resources"></a>Limitaciones de los recursos web de script  
 Como todos los recursos web, los recursos web de JavaScript usan el contexto de seguridad de aplicaciones basadas en modelos. Sólo los usuarios con licencia con los privilegios necesarios pueden tener acceso a ellos.  
  
> [!NOTE]
>  Las referencias incluidas en código entre los recursos web no se siguen como dependencias de solución.  
  
<a name="BKMK_Using"></a>   
## <a name="using-javascript-libraries"></a>Uso de bibliotecas de JavaScript  
 Para obtener más información el modo de desarrollar y probar bibliotecas de JavaScript y sobre cómo asociarlas con comandos de la cinta de opciones y eventos de formulario, consulte [Scripting del cliente con JavaScript](client-scripting.md).  
  
<a name="BKMK_Referencing"></a>   
## <a name="referencing-a-script-web-resource-from-a-webpage-web-resource"></a>Referencia a un recurso web de script estilo desde un recurso web de página web  
 Todos los recursos web pueden usar direcciones URL relativas para hacer referencia unos a otros. En el siguiente ejemplo, para que el recurso web de página web `new_/content/contentpage.htm` haga referencia al recurso web de JavaScript `new_/scripts/myScript.js`, agregue el siguiente código HTML al elemento de encabezado de `new_/content/contentpage.htm`.  
  
```html  
<script type="text/jscript" src="../scripts/myScript.js"></script>  
```  
  
 Para hacer referencia a un JavaScript desde otro editor, la ruta debe incluir el prefijo de personalización de ese editor. Por ejemplo, para que la página `new_/content/contentpage.htm` haga referencia a la página `MyIsv_/scripts/customscripts.js`, el valor del atributo `src` debe ser `../../MyIsv_/scripts/customscripts.js`.  
  
### <a name="see-also"></a>Vea también  
 [Scripting del cliente con JavaScript](client-scripting.md)   
 [Recursos web](web-resources.md)   
 [Uso de recursos web de página web (HTML)](webpage-html-web-resources.md)   
 [Uso de recursos web de hojas de estilo (CSS)](css-web-resources.md)   
 [Uso de recursos web de datos (XML)](data-xml-web-resources.md)   
 [Uso de recursos web de imagen (JPG, PNG, GIF)](image-web-resources.md)   
 [Usar recursos web de hoja de estilo (XSL)](stylesheet-xsl-web-resources.md)   
 [Agilice el desarrollo de recursos web con Fiddler AutoResponder](streamline-javascript-development-fiddler-autoresponder.md)    
