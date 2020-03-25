---
title: Pasar los datos de una página como parámetros de las acciones de la cinta de opciones (aplicaciones orientadas a modelos) | Documentos de Microsoft
description: 'En este tema se describen las opciones para usar el elemento de <CrmParameter> para recuperar estos valores. '
ms.custom: ''
ms.date: 02/15/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: hazhouMSFT
ms.author: hazhou
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 329e9f1845bfdfc9f2afa87528fbfd10bc4aa886
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109062"
---
# <a name="pass-data-from-a-page-as-a-parameter-to-ribbon-actions"></a>Pasar los datos desde una página como parámetro de las acciones de la cinta de opciones

Cuando define una acción en una cinta de opciones, suele necesario pasar datos desde la página a una función de JavaScript o a una dirección URL. En este tema se describen las opciones para usar el elemento [\<CrmParameter\>](https://msdn.microsoft.com/library/gg309332.aspx) para recuperar estos valores.

## <a name="form-and-grid-context-in-ribbon-actions"></a>Contexto de formulario y cuadrícula en las acciones de la cinta

Para pasar la información del contexto de ejecución (*contexto de formulario* o *contexto cuadrícula*) a la función JavaScript para las acciones de la cinta, especifique **PrimaryControl** como el valor de contexto de formulario o **SelectedControl** para el contexto de cuadrícula como el valor `<CrmParameter>` en la definición de la cinta. **SelectedControl** pasará en el contexto de la cuadrícula, para las subcuadrículas y las cuadrículas de página principal. **PrimaryControl** o el valor **SelectedControl** se usa como argumento en la característica de JavaScript para *contexto de formulario* o *contexto de cuadrícula* respectivamente. 

Por ejemplo, aquí tenemos una definición de la cinta de ejemplo donde pasamos el parámetro **PrimaryControl** a la función JavaScript:

```xml
<CommandDefinition Id="SampleCommand">
  <EnableRules/>
  <DisplayRules/>
  <Actions>
    <JavaScriptFunction Library="$webresource:new_mySampleScript.js" FunctionName="mySampleFunction">
      <CrmParameter Value="PrimaryControl" />
    </JavaScriptFunction>
  </Actions>
</CommandDefinition>
```

A continuación, en el archivo de recursos web **new_mySampleScript.js** al que se hace referencia en el ejemplo anterior, defina la función JavaScript con la variable **primaryControl** como argumento. Este argumento proporciona el contexto de *formulario* donde se ejecute el comando de la cinta:

```JavaScript
function mySampleFunction(primaryControl) {
    var formContext = primaryControl;
    // Perform operations using the formContext object
}
```

También puede especificar **CommandProperties** como el valor `<CrmParameter>` en la definición de la cinta para pasar detalles sobre el evento en el control de la cinta. Puede usar esto para enviar información contextual a su función JavaScript donde las acciones específicas pueden determinarse en función del contexto del evento.

> [!NOTE]
> Obtener *contexto de forma* y *contexto cuadrícula* para las funciones de JavaScript para acciones de la cinta es diferente de cómo obtener estos valores en forma de secuencias de comandos. Para obtener información sobre cómo obtener estos contextos y secuencias de comandos de formulario, vea [contexto del formulario de la API del cliente](clientapi/clientapi-form-context.md) y [contexto de cuadrícula de la API de cliente](clientapi/clientapi-grid-context.md).

## <a name="form-values"></a>Valores de formulario

Con una cinta de opciones de formulario, puede usar las colecciones de `data.entity`.[atributos](clientapi/reference/attributes.md) y de `ui`.[controles](clientapi/reference/controls.md) para recuperar y establecer valores de los campos conocidos. 

Por ejemplo, el código de ejemplo siguiente muestra cómo recuperar el campo de nombre de la cuenta en el formulario de cuenta y, después, establecer un valor en el campo de websiteurl según el valor del nombre de cuenta:

```JavaScript
function mySampleFunction(primaryControl) {
    var formContext = primaryControl;    
    var accountName = formContext.getControl("name").getAttribute().getValue();    

    // Set the WebSiteURL field if account name contains "Contoso"
    if (accountName.toLowerCase().search("contoso") != -1) {
        formContext.getAttribute("websiteurl").setValue("https://www.contoso.com");
    }
    else {
        Xrm.Navigation.openAlertDialog({ text: "Account name does not contain 'Contoso'." });
    }
}
```

  
## <a name="grid-values"></a>Valores de la cuadrícula  
 La mayoría de los valores disponibles para el elemento de `<CrmParameter>` se relacionan con el trabajo con datos que se muestran en una cuadrícula o gráfico de jerarquías. Mediante las opciones de la enumeración del atributo de `Value`, puede aislar fácilmente los elementos por:  
  
- **Elementos seleccionados**  
  
    -   SelectedControlSelectedItemCount  
  
    -   SelectedControlSelectedItemIds  
  
    -   SelectedControlSelectedItemReferences  
  
- **Todos los elementos**  
  
    -   SelectedControlAllItemCount  
  
    -   SelectedControlAllItemIds  
  
    -   SelectedControlAllItemReferences  
  
- **Elementos no seleccionados**  
  
    -   SelectedControlUnselectedItemCount  
  
    -   SelectedControlUnselectedItemIds  
  
    -   SelectedControlUnselectedItemReferences  
  
  Para cada una de estas agrupaciones, puede recopilar el número de elementos y de identificadores de GUID. Si pasa los valores a una dirección URL, también puede recuperar objetos `EntityReference` que contienen toda la información necesaria para identificar exclusivamente los objetos de la cuadrícula. Estos parámetros se aplican si la página vista es la cuadrícula principal (`HomepageGrid`) o una subcuadrícula situada en un formulario. Cuando se usa conjuntamente con el parámetro de `SelectedEntityTypeName`, tiene toda la información que debería tener que pasar a otra aplicación.  
  
 
  
## <a name="other-context-information"></a>Otra información de contexto  
 Además de los valores de los datos, puede recuperar la información de contexto cliente mediante [\<CrmParameter\>](https://msdn.microsoft.com/library/gg309332.aspx).  Puede usar las siguientes opciones como el valor del elemento `CrmParameter`: `OrgName`, `OrgLcid` y `UserLcid`.
 
 Para una acción de `<Url>`, también puede usar el atributo de `PassParams` para incluir información contextual.  
  
 Las opciones de `Value` `PrimaryEntityTypeName` y `FirstPrimaryItemId` brindan información para un registro de entidad. Puede usar `PrimaryItemIds` para una cinta de opciones de `HomepageGrid` para obtener una lista de todos los elementos que se muestran.
  
### <a name="see-also"></a>Vea también  
 [Personalizar la cinta de opciones](customize-commands-ribbon.md)   
 [Pasar parámetros a una dirección URL con la cinta de opciones](pass-parameters-url-by-using-ribbon.md)    
 [Definir acciones de la cinta de opciones](define-ribbon-actions.md)   
 [Definir acciones personalizadas para modificar la cinta de opciones](define-custom-actions-modify-ribbon.md)<br>
 [Contexto de formulario de la API del cliente](clientapi/clientapi-form-context.md)<br>
 [Contexto de cuadrícula de la API del cliente](clientapi/clientapi-grid-context.md)<br>
 
