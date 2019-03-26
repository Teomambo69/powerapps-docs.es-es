---
title: Deslice parámetros a una dirección URL usando la cinta de opciones (aplicaciones orientadas a modelo) | Documentos de Microsoft
description: Obtenga información acerca de cómo pasar parámetros a una dirección URL con la cinta de opciones
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
# <a name="pass-parameters-to-a-url-by-using-the-ribbon"></a>Pasar parámetros a una dirección URL con la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/pass-parameters-url-by-using-ribbon -->

Las acciones de la cinta de opciones se definen en el elemento de `<Actions>` de un elemento de `<CommandDefinition>` . Existen varias formas de pasar la información contextual de aplicaciones orientadas a modelos como parámetros de cadena de consulta a una dirección URL con la cinta de opciones.  
  
-   Use un elemento `<Url>`. En el elemento `Url` , use el atributo **PassParams** .  
  
-   Use un elemento `<Url>`, así como un elemento `<CrmParameter>` . Cuando se usa desde un elemento `Url` , debe establecerse el valor del atributo de nombre.  
  
-   Use un elemento `<JavaScriptFunction>`, así como un elemento `<CrmParameter>` .  
  
## <a name="use-the-passparams-attribute-to-set-dynamic-values"></a>Use el atributo PassParams para establecer valores dinámicos  
 El paso de parámetros a la dirección URL de destino mediante el atributo **PassParams** ofrece información a la aplicación de destino acerca del contexto del registro o el usuario. Todos los parámetros se pasan si el control de la cinta de opciones se configura mediante el atributo **PassParams** . En la tabla siguiente se muestran los parámetros admitidos.  
  
|Parámetro|Nombre|Descripción|  
|---------------|----------|-----------------|  
|`typename`|Nombre de entidad|Nombre de la entidad. Para las entidades personalizadas, se incluye el prefijo de personalización, por ejemplo, new_entityname.|  
|`type`|Código de tipo de entidad|Entero que identifica de forma única la entidad de la organización actual. **Nota:** Los valores de `Entity Type Code` están determinados por el orden en que se crea una entidad en una organización. `Entity Type Codes` para entidades personalizadas suelen ser distintas en distintas organizaciones.|  
|`id`|GUID de objeto|Identificador único global (GUID) que representa un registro.|  
|`orgname`|Nombre de la organización|Nombre único de la organización.|  
|`userlcid`|Código de idioma de usuario|Identificador del código de idioma que usa el usuario actual.|  
|`orglcid`|Código de idioma de la organización|Identificador de código de idioma que representa el idioma base de la organización.|  
  
[!INCLUDE[languagecode](../../includes/languagecode.md)]
  
> [!NOTE]
>  Se recomienda usar el nombre de la entidad en lugar del código de tipo de entidad porque el código de tipo de entidad puede variar entre las instalaciones de MDA.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra la dirección URL sin parámetros:  
  
```  
http://myserver/mypage.aspx  
```  
  
 El siguiente ejemplo muestra los parámetros incluidos cuando se muestra el control de la cinta de opciones para la entidad de cuenta, para una organización denominada "AdventureWorksCycle", cuando el idioma del usuario y el idioma base de la organización es el inglés, y el GUID para el registro de cuenta es DBD5DBFB-0666-DC11-A5D9-0003FF9CE217:  
  
```  
http://myserver/mypage.aspx?orgname=AdventureWorksCycle&userlcid=1033&orglcid=1033&type=1&typename=account&id=%7BDBD5DBFB-0666-DC11-A5D9-0003FF9CE217%7D  
```  
  
## <a name="use-a-querystring-parameter-in-the-url"></a>Use un parámetro Querystring en la dirección URL  
 Puede incluir un parámetro `querystring` en el atributo de la dirección URL. Esto puede ser muy útil si desea abrir un determinado registro o verlo mediante [Abrir formularios, vistas, cuadros de diálogo e informes con una dirección URL](open-forms-views-dialogs-reports-url.md).  
  
> [!NOTE]
>  No se podrá importar la cinta de opciones si la dirección URL incluye el carácter de la y comercial (&) que se usa para separar los parámetros múltiples de `querystring` en la dirección URL. Este carácter hacer que el XML no sea válido. Debe escapar el carácter de y comercial en el valor de atributo de la dirección URL con "&amp;".  
  
## <a name="reading-passed-parameters"></a>Leyendo parámetros pasados  
 Los parámetros pasados se leen normalmente en la página .aspx de destino mediante la propiedad `HttpRequest.QueryString`. Más información: [Propiedad de HttpRequest.QueryString](https://msdn.microsoft.com/library/system.web.httprequest.querystring.aspx)  
  
> [!NOTE]
>  Si el destino de la dirección URL es un recurso web, puede aceptar solo los parámetros identificados en el tema [Pasar parámetros a recursos web HTML](webpage-html-web-resources.md#BKMK_PassingParametersToWebResources). La única oportunidad para pasar valores personalizados es incluyéndolos en el parámetro `data` . Se necesita un determinado control especial para incluir varios valores en un único parámetro. Más información: [Ejemplo: Pasar varios valores a un recurso web de página web mediante el parámetro de datos](sample-pass-multiple-values-web-resource-through-data-parameter.md)  
  
### <a name="see-also"></a>Vea también

 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Abrir formularios y vistas con una dirección URL](open-forms-views-dialogs-reports-url.md)    
 [Definir las reglas de visualización de la pestaña de la cinta de opciones](define-ribbon-tab-display-rules.md)   
 [Ejemplo: Exportar definiciones de cinta de opciones](sample-export-ribbon-definitions.md)


