---
title: Usar controles de recursos IFRAME y web en un formulario (aplicaciones basadas en modelos) | Microsoft Docs
description: 'IFRAME y los controles de recursos web insertan contenido desde otra ubicación en las páginas mediante un elemento de IFRAME HTML.  '
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
# <a name="use-iframe-and-web-resource-controls-on-a-form"></a>Usar IFRAME y controles de recursos web en un formulario

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form -->


IFRAME y los controles de recursos web insertan contenido desde otra ubicación en las páginas mediante un elemento de IFRAME HTML.  

> [!NOTE]
>  Los diseños que elige para el formulario también se usan para el panel de lectura de Dynamics 365 for Outlook y los formularios usados por Dynamics 365 for tablets. Los recursos web e IFRAME no se muestran utilizando el panel de lectura de Dynamics 365 for Outlook, sin embargo, se admiten en Dynamics 365 for tablets. Si su IFRAME depende del acceso al objeto de `Xrm` de la página o a cualquier controlador de eventos de formulario, deberá configurar IFRAME para que no sea visible de forma predeterminada.  

 Puede usar un IFRAME para mostrar los contenidos de otro sitio web en un formulario, por ejemplo, en una página ASP.NET. No se puede mostrar un formulario de entidad en un iFrame incrustado en otro formulario de entidad.  

 Puede usar uno de los siguientes recursos web para mostrar los contenidos de recursos web en un formulario:  

-   [Recursos web de página web (HTML)](webpage-html-web-resources.md)  

-   [Recursos web de imagen (JPG, PNG, GIF, ICO)](image-web-resources.md)  


 En las siguientes secciones se describen sus opciones si desea que estos controles muestren más que contenido estático.  

<a name="BKMK_IframeSecurity"></a>   
## <a name="select-whether-to-restrict-cross-frame-scripting"></a>Seleccione si se restringe el scripting entre marcos  
 Use la opción **Restringir el scripting entre marcos cuando se admita** cuando no confíe totalmente en el contenido que aparece en un IFRAME. Cuando se seleccione esta opción, el IFRAME tendrá los atributos establecidos que se enumeran en la tabla siguiente.  


|        Atributo        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `security="restricted"` |                                                                                                                                                                                                                                                                                                    Este atributo solo es compatible con las versiones de Internet Explorer no anteriores a la versión 6. El atributo de seguridad aplica el ajuste de seguridad del usuario Sitios restringidos al archivo de origen del IFRAME. (La configuración de la zona se encuentra en la pestaña **Seguridad** del cuadro de diálogo **Opciones de Internet** .) De forma predeterminada, el scripting no está habilitado en la zona Sitios restringidos. Mediante el cambio de la configuración de seguridad de la zona, se pueden producir varios resultados negativos, incluido el permitir la ejecución de scripts. Para obtener más información, consulte [atributo de seguridad](https://msdn.microsoft.com/library/ie/ms534622.aspx).                                                                                                                                                                                                                                                                                                     |
|      `sandbox=""`       | Para exploradores que admiten este atributo, el contenido del IFRAME está esencialmente limitado a solo mostrar información. Se pueden aplicar las siguientes restricciones:<br /><br /> -   Los complementos del explorador están deshabilitados.<br />-   Los formularios y scripts están deshabilitados.<br />-   Los vínculos a otros contextos de navegación están deshabilitados.<br />-   El contenido se trata como procedente de un dominio diferente aunque el dominio sea el mismo.<br /><br /> Este atributo se define mediante W3C y es compatible con los siguientes exploradores:<br /><br /> - Internet Explorer 10, Internet Explorer 11, y Microsoft Edge <br />- Google Chrome<br />- Apple Safari<br />- Mozilla Firefox<br /><br /> Para obtener más información sobre el atributo de espacio aislado, consulte:<br /><br /> -   [Cómo proteger su sitio con espacios aislados HTML5](https://msdn.microsoft.com/hh563496)<br />-   [Atributo de espacios aislados WC3](http://dev.w3.org/html5/spec-author-view/the-iframe-element.html)<br />-   [Espacio aislado](https://msdn.microsoft.com/library/ie/hh673561.aspx) |

<a name="BKMK_EnableIFrameCommunicationAcrossDomains"></a>   

### <a name="enabling-iframe-communication-across-domains"></a>Activación de la comunicación de IFrame entre dominios  
 Hay momentos en los que conviene habilitar la comunicación para un IFRAME que contiene contenido de un dominio diferente. `Window.postMessage` es un método del explorador que proporciona esta capacidad para las versiones de Internet Explorer no anteriores a Internet Explorer 8. Google Chrome, Mozilla Firefox, y Apple Safari también lo admiten. Para obtener más información acerca del uso de `postMessage`, vea las entradas de blog siguientes.  

-   [Llamadas entre dominios al formulario principal](http://blogs.msdn.com/b/devkeydet/archive/2012/02/14/cross-domain-calls-to-the-parent-crm-2011-form.aspx)  

-   [Mensajería y RPC entre documentos](https://msdn.microsoft.com/magazine/ff800814.aspx)  

<a name="BKMK_PassContextualInformation"></a>   

## <a name="pass-contextual-information-about-the-record"></a>Pasar información contextual sobre el registro  
 Puede proporcionar información contextual pasando parámetros a la URL definida en el control. La página mostrada en el marco debe poder procesar los parámetros que se le pasan. Todos los parámetros de la siguiente tabla se pasan si IFRAME o el recurso web se configura mediante la utilización de la opción **Pasar código de tipo de objeto de registro e identificador único como parámetros**.  

 Puede especificar si se van a pasar todos los parámetros de la siguiente tabla.  


| Parámetro  |        Nombre        |                                 Descripción                                 |
|------------|--------------------|-----------------------------------------------------------------------------|
| `typename` |    Nombre de entidad     |                           El nombre de la entidad.                           |
|   `type`   |  Código de tipo de entidad  | El entero que identifica de forma única la entidad en una organización específica. |
|    `id`    |    GUID de objeto     |                      GUID que representa un registro.                       |
| `orgname`  | Nombre de la organización  |                    Nombre único de la organización.                     |
| `userlcid` | Código de idioma de usuario |    Identificador del código de idioma que usa el usuario actual.     |

 [!INCLUDE[languagecode](../../includes/languagecode.md)]  

> [!NOTE]
>  Se sugiere usar el nombre de la entidad en lugar del código de tipo porque el código de tipo de entidad para entidades personalizadas puede variar entre las organizaciones de Common Data Service.  

### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra la dirección URL sin parámetros.  

```  
http://myserver/mypage.aspx  
```  

 El siguiente ejemplo muestra la dirección URL con parámetros.  

```  
http://myserver/mypage.aspx?id=%7bB2232821-A775-DF11-8DD1-00155DBA3809%7d&orglcid=1033&orgname=adventureworkscycle&type=1&typename=account&userlcid=1033  
```  

### <a name="read-passed-parameters"></a>Leer parámetros pasados  

 Los parámetros pasados se leen normalmente en la página .aspx de destino mediante la propiedad **HttpRequest.QueryString**. En una página HTML, se puede acceder a los parámetros utilizando la propiedad **window.location.search** en JavaScript. Para obtener más información, consulte [HttpRequest.QueryString Property](http://msdn2.microsoft.com/library/system.web.httprequest.querystring.aspx) y [la propiedad de búsqueda](http://msdn2.microsoft.com/library/ms534620.aspx).  

<a name="BKMK_PassFormData"></a>  

## <a name="pass-form-data"></a>Pasar datos de formulario  

 Use el método [getValue](clientapi/reference/controls/getValue.md) en los atributos que contienen los datos que desea que pasen al otro sitio web y forme una cadena de los argumentos de cadena de consulta que pueda utilizar la otra página. A continuación, utilice un [evento OnChange de campo](clientapi/reference/events/attribute-onchange.md), un [evento OnReadyStateComplete de IFRAME](clientapi/reference/events/onreadystatecomplete.md) o un [evento TabStateChange de pestaña](clientapi/reference/events/tabstatechange.md) y el método [setSrc](clientapi/reference/controls/setSrc.md) para agregar los parámetros a la propiedad `src` del recurso IFRAME o web.  

 Si está usando el parámetro de datos para pasar datos a un recurso web de Silverlight , puede utilizar los métodos [getData](clientapi/reference/controls/getData.md) y [setData](clientapi/reference/controls/setData.md) para manipular el valor pasado a través del parámetro de datos. Para recursos web (HTML) de página web, use el método [setSrc](clientapi/reference/controls/setSrc.md) para manipular directamente el parámetro `querystring`.  

 Evite utilizar el [evento OnLoad](clientapi/reference/events/form-onload.md). Los IFRAMES y los recursos web se cargan de manera asincrónica y puede que el marco no haya acabado de cargarse antes de que finalice el script de eventos de `Onload`. Esto puede provocar que la propiedad `src` del recurso IFRAME o web que ha cambiado se sobrescriba con el valor predeterminado de la propiedad IFRAME o URL del recurso web.  

<a name="BKMK_ChangeThePage"></a>   

## <a name="change-the-url"></a>Cambiar la URL  

 Es posible que desee cambiar el destino de IFRAME en función de consideraciones como los datos del formulario o de si el usuario está trabajando sin conexión. Puede definir dinámicamente el destino del IFRAME.  

> [!NOTE]
>  Cuando cambie la página de destino del IFRAME, los parámetros no se pasarán a la nueva URL automáticamente. Debe anexar los parámetros de cadena de consulta a la URL antes de usar el método `setSrc`.  

### <a name="example"></a>Ejemplo  

 El siguiente ejemplo muestra cómo establecer la propiedad `src` para el IFRAME y cualquier parámetro usando el evento de `onChange` de un campo de conjunto de opciones.  

```javascript  
//Get the value of an option set attribute  
var value = Xrm.Page.data.entity.attributes.get("new_pagechooser").getValue();  
var newTarget = "";  
//Set the target based on the value of the option set  
switch (value) {  
    case 100000001:  
        newTarget = "http://myServer/test/pageOne.aspx";  
        break;  
    default:  
        newTarget = "http://myServer/test/pageTwo.aspx";  
        break;  
}  
//Get the default URL for the IFRAME, which includes the   
// query string parameters  
var IFrame = Xrm.Page.ui.controls.get("IFRAME_test");  
var Url = IFrame.getSrc();  
// Capture the parameters  
var params = Url.substr(Url.indexOf("?"));  
//Append the parameters to the new page URL  
newTarget = newTarget + params;  
// Use the setSrc method so that the IFRAME uses the  
// new page with the existing parameters  
IFrame.setSrc(newTarget);  
```  

## <a name="see-also"></a>Vea también  

 [Scripting del cliente con JavaScript](client-scripting.md)   
 

