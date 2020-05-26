---
title: Recursos web de imágenes (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo usar los recursos web de imágenes para hacer que las imágenes estén disponibles para su uso
ms.custom: ''
ms.date: 03/11/2020
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
ms.openlocfilehash: a55cebde012018b68aac06cf144e1b91a9e065f5
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275932"
---
# <a name="image-web-resources"></a>Recursos web de imagen

Use los recursos web de imagen para hacer que las imágenes estén disponibles para su uso en aplicaciones basadas en modelos.  

Hay cinco tipos de recursos web de imágenes: 
* Formato PNG
* Formato JPG
* Formato GIF
* Formato ICO
* Formato vectorial (SVG)

> [!NOTE]
> Los recursos web de formato de vector (SVG) se agregaron con las aplicaciones basadas en modelos.

  
<a name="BKMK_Capabilities"></a>   
## <a name="capabilities-of-image-web-resources"></a>Capacidades de los recursos web de imagen  
 Con recursos web de imagen es posible agregar imágenes cuando las necesite. Los usos habituales incluyen:  
  
- Iconos de entidad personalizada  
- Iconos para controles de cinta personalizada y subáreas del `SiteMap`.  
- Gráficos decorativos para formularios de entidad y recursos web de páginas web.  
- Imágenes de fondo usadas por recursos web CSS.  

Use los recursos web de formato de vector (SVG) para cualquier icono que se muestre en la aplicación. Las imágenes vectoriales se definen como Scalable Vector Graphics (SVG), un formato de imagen vectorial basado en XML. La ventaja de las imágenes vectoriales sobre otros recursos web de imagen es que son escalables. Puede definir una imagen vectorial y reutilizarla en lugar de proporcionar varios tamaños de imágenes. Usará estos con una nueva sesión<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IconVectorName> propiedad para definir el icono de una entidad personalizada en lugar de las propiedades `IconLargeName`, `IconMediumName` o `IconSmallName`.

> [!NOTE]
> Los recursos web de formato vectorial (SVG) se tratan como recursos web [Script (JScript)](/powerapps/developer/model-driven-apps/script-jscript-web-resources) y conllevan los mismos riesgos de seguridad que los recursos web Script (JScript) porque los archivos SVG permiten la incrustación JScript.
  
<a name="BKMK_Limitations"></a>   
## <a name="limitations-of-image-web-resources"></a>Limitaciones de los recursos web de imagen  
 Como todos los recursos web, los recursos web de imagen usan el contexto de seguridad. Solo los usuarios con licencia con los privilegios necesarios pueden tener acceso a ellos.  
 
  
<a name="BKMK_ReferenceFromWebPageWebResource"></a>   
## <a name="reference-an-image-web-resource-from-a-webpage-web-resource"></a>Haga referencia a un recurso web de imagen desde un recurso web de página web  
 Todos los recursos web pueden usar direcciones URL relativas para hacer referencia unos a otros. En el siguiente ejemplo, para el recurso web de la página web (HTML) new_/content/contentpage.htm que hace referencia al recurso web de imágenes new_/Images/image1.png, agregue el código HTML siguiente a new_/content/contentpage.htm:  
  
```html  
<img src="../Images/image1.png" />  
```  
  
<a name="BKMK_ReferenceFromForm"></a>   
## <a name="reference-an-image-web-resource-from-a--form"></a>Haga referencia a un recurso web de imagen desde un formulario de   
  
#### <a name="add-an-image-to-an-entity-form"></a>Agregar una imagen a un formulario de entidad  
  
1.  Navegue hasta el editor de formularios para una entidad.  
  
2.  Seleccione donde desea agregar la imagen en el formulario.  
  
3.  En la pestaña **Insertar**, haga clic en **Recurso web**.  
  
4.  En la pestaña **General**, seleccione la imagen del recurso web que desea agregar.  
  
5.  Escriba un nombre para el recurso web. También puede especificar una etiqueta y un texto alternativo.  
  
6.  En la pestaña **Formato**, puede definir:  
  
    -   El número de columnas que las imágenes deben usar.  
  
    -   El número de filas que las imágenes deben usar el o si deben expandirse automáticamente para usar el espacio disponible.  
  
    -   El tamaño de la imagen con las siguientes opciones:  
  
        - **Acercar a la idoneidad**  
  
        - **Estire a la idoneidad (mantener las relaciones de aspecto)**  
  
        - **Original**  
  
        - **Específico,**  
  
    -   Si selecciona “Específico”, puede especificar el alto y ancho deseados en píxeles.  
  
7.  Haga clic en **Aceptar**.  
  
8.  Debe guardar los cambios y publicar el formulario antes de que los usuarios puedan ver la imagen en el formulario.  
  
<a name="BKMK_ReferenceWithWebResourcedirective"></a>   
## <a name="reference-an-image-web-resource-from-a-ribbon-element-or-from-the-site-map-subarea"></a>Haga referencia a un recurso web de imagen desde un elemento de la cinta de opciones o desde una subárea del mapa del sitio  
 Use la directiva de `$webresource:` para especificar una imagen del recurso web que desee utilizar como icono de la cinta de opciones o en la navegación de la aplicación mediante mapa del sitio. El siguiente ejemplo muestra cómo especificar los iconos para un botón de la cinta de opciones.  
  
```xml  
<Button Id="MyISV.opportunity.form.actions.FlyoutAnchor.Button.1" Image16by16="$webresource:new_/icons/oneIcon16.png" Image32by32="$webresource:new_/icons/oneIcon32.png"/>  
```  
  
> [!NOTE]
> Mediante la directiva de `$webresource:` se agrega una dependencia de la solución que impide eliminar los recursos web de imagen a los que se hace referencia mientras otro componente de la solución los esté usando.  
  
### <a name="see-also"></a>Vea también  
 [Recursos web](web-resources.md)   
 [Uso de recursos web de página web (HTML)](webpage-html-web-resources.md)   
 [Uso de recursos web de hojas de estilo (CSS)](css-web-resources.md)   
 [Usar recursos web de script (JScript)](script-jscript-web-resources.md)   
 [Usar recursos web de datos (XML)](data-xml-web-resources.md)   
 [Usar recursos web Silverlight (XAP)](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)  
 [Usar recursos web de hoja de estilo (XSL)](stylesheet-xsl-web-resources.md)
