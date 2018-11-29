---
title: Recursos web de CSS (aplicaciones basadas en modelos) | Microsoft Docs
description: 'Use los recursos web de las hojas de estilo en cascada (CSS) para crear hojas de estilo para usar con recursos web de páginas web. '
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: a4e98fa7-930d-e320-5384-9f773775639b
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="css-web-resources"></a>Recursos web CSS

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/css-web-resources -->

Use los recursos web de las hojas de estilo en cascada (CSS) para crear hojas de estilo para usar con recursos web de páginas web.  
  
## <a name="capabilities-of-css-web-resources"></a>Capacidades de los recursos web de CSS  
 Con los recursos web de CSS, puede administrar el aspecto de los recursos web de páginas web al vincularlos a una biblioteca compartida de estilos CSS.  
  
### <a name="limitations-of-css-web-resources"></a>Limitaciones de los recursos web de CSS  
 Como todos los recursos web, los recursos web de CSS solo están disponibles en el contexto de seguridad. Solo los usuarios con licencia con los privilegios necesarios pueden tener acceso a ellos.
  
## <a name="referencing-a-style-sheet-web-resource-from-a-webpage-web-resource"></a>Referencia a un recurso web de hoja de estilo desde un recurso web de página web  
 Todos los recursos web pueden usar direcciones URL relativas para hacer referencia unos a otros. En el siguiente ejemplo, para que el recurso web de página web `sample_/content/contentpage.htm` haga referencia al recurso web de hoja de estilo `sample_/styles/styles.css`, agregue el siguiente ejemplo al elemento principal de sample_/content/contentpage.htm:  
  
```html  
<link rel="stylesheet" type="text/css" href="../styles/styles.css" />  
```  
  
 Para hacer referencia a una hoja de estilo de un editor diferente, la ruta debe incluir el prefijo de personalización del editor de soluciones. Por ejemplo, para que la página `sample_/content/contentpage.htm` haga referencia a la página `MyIsv_/styles/styles.css`, el valor del parámetro href debe ser `../../MyIsv_/styles/styles.css`.  
  
> [!NOTE]
>  Las referencias incluidas en código entre los recursos web no se siguen como dependencias de solución.  
  
### <a name="see-also"></a>Vea también  
 [Recursos web](web-resources.md)   
 [Uso de recursos web de página web (HTML)](webpage-html-web-resources.md)   
 [Usar recursos web de script (JScript)](script-jscript-web-resources.md)   
 [Usar recursos web de datos (XML)](data-xml-web-resources.md)   
 [Usar recursos web de imagen (JPG, PNG, GIF)](image-web-resources.md)   
 [Usar recursos web Silverlight (XAP)](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)  
 [Usar recursos web de hoja de estilo (XSL)](stylesheet-xsl-web-resources.md)   
 [Entidad WebResource](../common-data-service/reference/entities/webresource.md)
