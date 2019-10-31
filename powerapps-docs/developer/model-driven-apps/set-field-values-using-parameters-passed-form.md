---
title: Establecer valores de campo con los parámetros pasados a un formulario (aplicaciones basadas en modelos) | Microsoft Docs
description: Puede establecer los valores predeterminados para los nuevos registros creados por los usuarios especificando los valores de los atributos en la URL que se usa para abrir el formulario.
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
# <a name="set-field-values-using-parameters-passed-to-a-form"></a>Establecer valores de campo usando parámetros pasados a un formulario

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/set-field-values-using-parameters-passed-form -->

Puede establecer los valores predeterminados para los nuevos registros creados por los usuarios especificando los valores de los atributos en la URL que se usa para abrir el formulario. De forma predeterminada, estos valores se establecen en el formulario, pero los usuarios pueden modificarlos antes de guardar el registro.  
  
<a name="BKMK_PassingParameters"></a>   
## <a name="pass-parameters-to-set-field-record-values"></a>Pasar parámetros para establecer valores de registros de campo  
  
> [!NOTE]
>  Puede pasar valores de parámetros al formulario para establecer los valores de los campos mediante la función `Xrm.Navigation.`[openForm](clientapi/reference/Xrm-Navigation/openForm.md). Para ver un ejemplo, consulte [Ejemplo: Utilizar Xrm.Navigation.openForm para abrir una nueva ventana](set-field-values-using-parameters-passed-form.md#BKMK_ExampleXrmNavigationOpentForm).  
  
 Al abrir un nuevo formulario usando la dirección URL, puede incluir argumentos en el parámetro `extraqs` para establecer los valores de los campos. Deben cumplirse los siguientes requisitos:  
  
- Debe codificar los parámetros que se pasan en el parámetro `extraqs`. Para codificar los parámetros, use [encodeURIComponent](https://msdn.microsoft.com/library/aeh9cef7\(VS.85\).aspx).  
  
- Los nombres de los argumentos de cadena de consulta deben coincidir con los nombres de los atributos de la entidad o incluirlos.  
  
- Los valores que se pasan deben ser válidos.  
  
- El valor no puede ser un script.  
  
  Los intentos de pasar un parámetro o un valor no válido producirán un error.  
  
- Para los campos booleanos, use el valor entero `0` o `1`, o el valor de texto `true` o `false` para establecer el valor.  
  
- Para los campos de fecha y hora, use el valor de texto de la fecha.  
  
<a name="BKMK_ExampleSetValueStringFields"></a>   

## <a name="example-set-the-value-for-string-fields"></a>Ejemplo: Establecimiento del valor para los campos de cadena  
 El siguiente ejemplo establece el valor del campo **Name** de un nuevo registro de cuenta en “New Account”.  
  
 El valor sin codificar para el parámetro `extraqs` es “name=New Account”.  
  
```  
/main.aspx?etn=account&extraqs=name%3DNew%20Account&pagetype=entityrecord  
```  
  
<a name="BKMK_SetLookupFieldValues"></a>   

## <a name="set-values-for-lookup-fields"></a>Establecer valores para campos de búsqueda  
 La siguiente tabla describe cinco tipos de campos de búsqueda. Para obtener ejemplos campos de búsqueda, vea [Ejemplo: Establecimiento del valor para los campos de búsqueda](set-field-values-using-parameters-passed-form.md#BKMK_setValueLookupfields) y [Ejemplo: Utilizar Xrm.Navigation.openForm para abrir una nueva ventana](set-field-values-using-parameters-passed-form.md#BKMK_ExampleXrmNavigationOpentForm).  
  
|Tipo de búsqueda|Descripción|  
|-----------------|-----------------|  
|búsqueda sencilla|Permite una sola referencia a un tipo de entidad.|  
|búsqueda de cliente|Permite una única referencia a una cuenta o un registro de contacto.|  
|búsqueda de propietario|Permite una única referencia a un equipo o un registro de usuario del sistema.|  
|búsqueda de tipo partylist|Permite asignar varias referencias a varias entidades.|  
|búsqueda Referente a|Permite asignar una sola referencia a varias entidades.|  
  
 Las directrices siguientes se aplican al establecer el valor de una búsqueda en un formulario mediante un argumento de cadena de consulta:  
  
-   Para las búsquedas sencillas debe establecer el valor y el texto que desea mostrar en la búsqueda. Use el sufijo “name” con el nombre del atributo para establecer el valor del texto.  
  
     No use ningún otro argumento.  
  
-   Para las búsquedas de cliente y propietario debe establecer el valor y el nombre de la misma manera que para las búsquedas sencillas. Además debe usar el sufijo “type” para especificar el tipo de entidad. Los valores permitidos son account, contact, systemuser y team.  
  
-   No se pueden establecer los valores para búsquedas de partylist o regarding.  
  
<a name="BKMK_setValueLookupfields"></a>   

## <a name="example-set-the-value-for-lookup-fields"></a>Ejemplo: Establecimiento del valor para los campos de búsqueda  
 Para establecer valores para los campos de búsqueda, use el valor de los datos, el valor del nombre y, solo para las búsquedas de cliente o propietario, especifique el valor de tipo para el campo respectivo. El siguiente ejemplo establece el campo de propietario en un usuario denominado “Mark Folkerts”.  
  
 El valor sin codificar para el parámetro `extraqs` es “**ownerid**={B8C6E040-656E-DF11-B414-00155DB1891A}&**owneridname**=Mark Folkerts&**owneridtype**=systemuser”.  
  
```  
/main.aspx?etn=lead&pagetype=entityrecord&extraqs=ownerid%3D%7bB8C6E040-656E-DF11-B414-00155DB1891A%7d%26owneridname%3DMark%20Folkerts%26owneridtype%3Dsystemuser  
```  
  
 El siguiente ejemplo establece el campo del contacto principal a un usuario con el nombre “Yvonne McKay (ejemplo)”. El valor no codificado para el parámetro `extraqs` es “**primarycontactid**={43b58571-eefa-e311-80c1-00155d2a68c4}&**primarycontactidname**=Yvonne McKay (ejemplo)”.  
  
```  
/main.aspx?etn=account&pagetype=entityrecord&extraqs=primarycontactid%3D%7B43b58571-eefa-e311-80c1-00155d2a68c4%7D%26primarycontactidname%3DYvonne%20McKay%20(sample)  
```  
  
> [!NOTE]
>  Para una búsqueda sencilla como esta, no tiene que establecer un valor de tipo.  
  
<a name="BKMK_SetValueDateFields"></a>   

## <a name="example-set-the-value-for-date-fields"></a>Ejemplo: Establecimiento del valor para los campos de fecha  
 El siguiente ejemplo establece el campo **Fecha estimada de cierre** para una nueva oportunidad como 31 de enero de 2011. El valor sin codificar para el parámetro `extraqs` es “estimatedclosedate=01/31/11”.  
  
```  
/main.aspx?etn=opportunity&extraqs=estimatedclosedate%3D01%2F31%2F11&pagetype=entityrecord  
```  
  
<a name="BKMK_SampleSEtValueOptionSetFields"></a>   

## <a name="example-set-the-value-for-option-set-fields"></a>Ejemplo: Establecimiento del valor para los campos de conjunto de opciones  
 Para establecer el valor de un campo de **Conjunto de opciones**, establezca el valor entero para la opción. El siguiente ejemplo establece el valor del campo **Role** en “Decision Maker” en un nuevo registro de contacto.  
  
 El valor sin codificar para el parámetro `extraqs` es “accountrolecode=1”.  
  
```  
/main.aspx?etn=contact&extraqs=accountrolecode%3D1&pagetype=entityrecord  
``` 

<a name="BKMK_SampleSEtValueMultiSelectOptionSetFields"></a> 
  
## <a name="example-set-the-value-for-multi-select-option-set-fields"></a>Ejemplo: Establecer el valor para campos de conjuntos de opciones multiselección

Para establecer el valor del campo **conjunto de opciones multiselección**, indique valores enteros para las opciones de la URL que se utiliza para abrir el formulario. Por ejemplo, establezca las opciones para el campo **Aficiones**, el valor sin codificar para el parámetro extraqs será "hobbies=[1,3,4]".   

```  
/main.aspx?etn=contact&extraqs=hobbies%3D%5B1%2C3%2C4%5D&pagetype=entityrecord   
``` 
  
<a name="BKMK_ExampleXrmNavigationOpentForm"></a>   

## <a name="example-use-xrmnavigationopenform-to-open-a-new-window"></a>Ejemplo: Utilizar Xrm.Navigation.openForm para abrir una nueva ventana  
 El siguiente ejemplo establece los valores predeterminados de distintos campos y muestra cómo usar la función `Xrm.Navigation`.[openForm](clientapi/reference/Xrm-Navigation/openForm.md). Es equivalente al ejemplo anterior que utilizaba el método `window.open`.  
  
```Javascript  
function OpenNewContact() {  
 var parameters = {};  
 //Set the Parent Customer field value to “Contoso”.  
 parameters["parentcustomerid"] = "2878282E-94D6-E111-9B1D-00155D9D700B";  
 parameters["parentcustomeridname"] = "Contoso";  
 parameters["parentcustomeridtype"] = "account";  
 //Set the Address Type to “Primary”.  
 parameters["address1_addresstypecode"] = "3";  
 //Set text in the Description field.  
 parameters["description"] = "Default values for this record were set programmatically.";  
 //Set Do not allow E-mails to "Do Not Allow".  
 parameters["donotemail"] = "1";  
  
 // Define the entity name to open the form  
 var entityFormOptions = {};
 entityFormOptions["entityName"] = "contact";

// Open the form
 Xrm.Navigation.openForm(entityFormOptions, parameters).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });  
}  
```  
  
<a name="BKMK_ExampleWindowOpen"></a>   

## <a name="example-use-windowopen-to-open-a-new-window"></a>Ejemplo: Uso de window.open para abrir una ventana nueva  
 El siguiente ejemplo establece los valores predeterminados de varios campos distintos y muestra cómo usar [encodeURIComponent](https://msdn.microsoft.com/library/aeh9cef7\(VS.85\).aspx) para codificar el valor del parámetro `extraqs`. Si usa el método [window.open](https://msdn.microsoft.com/library/ms536651\(VS.85\).aspx), puede controlar las características de la ventana que se abre.  
  
```Javascript  
function OpenNewContact() {  
    //Set the Parent Customer field value to “Contoso”.  
    var extraqs = "parentcustomerid={F01F3F6D-896E-DF11-B414-00155DB1891A}";  
    extraqs += "&parentcustomeridname=Contoso";  
    extraqs += "&parentcustomeridtype=account";  
    //Set the Address Type to “Primary”.  
    extraqs += "&address1_addresstypecode=3";  
    //Set text in the Description field.  
    extraqs += "&description=Default values for this record were set programatically.";  
    //Set Do not allow E-mails to "Do Not Allow".  
    extraqs += "&donotemail=1";  
    //Set features for how the window will appear.  
    var features = "location=no,menubar=no,status=no,toolbar=no";  
    // Open the window.  
    window.open("/main.aspx?etn=contact&pagetype=entityrecord&extraqs=" +  
     encodeURIComponent(extraqs), "_blank", features, false);  
}  
```  
  
### <a name="see-also"></a>Vea también  

 [Abrir formularios y vistas con una dirección URL](open-forms-views-dialogs-reports-url.md)   
 [openForm](clientapi/reference/Xrm-Navigation/openForm.md)  
 [Configurar un formulario para aceptar parámetros querystring personalizados](configure-form-accept-custom-querystring-parameters.md)
