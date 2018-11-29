---
title: Atributos compuestos en aplicaciones basadas en modelos | MicrosoftDocs
description: Obtenga información sobre el método de addOnchange para atributos para establecer una función a la que se llamará cuando se cambia el valor del atributo.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9f3b2fed-fde5-46e4-8c59-43aa51aa82df
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="composite-attributes"></a>Atributos compuestos 



Algunos campos agregados a un formulario pueden representar varios elementos de datos. Estos *atributos compuestos* se comportan de manera diferente a los demás atributos cuando se muestran en la aplicación web y debe escribir scripts de manera diferente para utilizarlos correctamente.

En la tabla siguiente se enumeran los atributos compuestos disponibles en aplicaciones basadas en modelos:

<table>
    <tbody>
        <tr>
            <th scope="col">
                <p>
Entidad </p>
            </th>
            <th scope="col">
                <p>
Nombre para mostrar </p>
            </th>
            <th scope="col">
                <p>
Nombre lógico </p>
            </th>
        </tr>
        <tr>
            <td rowspan="2">
                <p>
Cuenta </p>
            </td>
            <td>
                <p>
                    <strong>Dirección 1</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección 2</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="3">
                <p>
Contacto </p>
            </td>
            <td>
                <p>
                    <strong>Nombre completo</strong>
                </p>
            </td>
            <td>
                <p>
fullname </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección 1</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección 2</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="3">
                <p>
Cliente potencial </p>
            </td>
            <td>
                <p>
                    <strong>Nombre completo</strong>
                </p>
            </td>
            <td>
                <p>
fullname </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección 1</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección 2</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="3">
                <p>
Usuario </p>
            </td>
            <td>
                <p>
                    <strong>Nombre completo</strong>
                </p>
            </td>
            <td>
                <p>
fullname </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Otra dirección</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>        
        <tr>
            <td rowspan="2">
                <p>
Oferta </p>
            </td>
            <td>
                <p>
                    <strong>Dirección de facturación</strong>
                </p>
            </td>
            <td>
                <p>
billto_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección de envío</strong>
                </p>
            </td>
            <td>
                <p>
shipto_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="2">
                <p>
Orden </p>
            </td>
            <td>
                <p>
                    <strong>Dirección de facturación</strong>
                </p>
            </td>
            <td>
                <p>
billto_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección de envío</strong>
                </p>
            </td>
            <td>
                <p>
shipto_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="2">
                <p>
Factura </p>
            </td>
            <td>
                <p>
                    <strong>Dirección de facturación</strong>
                </p>
            </td>
            <td>
                <p>
billto_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Dirección de envío</strong>
                </p>
            </td>
            <td>
                <p>
shipto_composite </p>
            </td>
        </tr>
    </tbody>
</table>

## <a name="composite-attributes-in-the-web-application"></a>Atributos compuestos en la aplicación web

Cuando se añadan los campos de los atributos compuestos a un formulario principal, la aplicación web solamente mostrará el atributo compuesto. Cuando alguien edite el campo, aparecerá un control flotante que mostrará los atributos individuales que forman el atributo compuesto. 

Por ejemplo, el campo **dirección** en un formulario de contacto es un atributo compuesto. Haga clic en el campo de control flotante **dirección** con atributos individuales que forman el atributo compuesto. 

![Ejemplo de atributo compuesto](../../media/clientapi_compositeattribute.png)

Aunque no se agreguen de manera explícita al formulario del editor de formularios, cada uno de los atributos que forman parte del atributo están disponibles para el formulario. Aunque puede leer el valor del valor compuesto mediante [getValue](attributes/getValue.md), no puede usar [setValue](attributes/setValue.md) para cambiar el valor del atributo compuesto directamente; debe establecer uno o varios atributos a los que se hace referencia mediante el atributo compuesto.

Puede obtener acceso a los controles constituyentes individuales mostrados en el control flotante por nombre. Estos controles utilizan la siguiente convención de nomenclatura: \<**nombre de control compuesto**>\_compositionLinkControl_\<**nombre de atributo constituyente**>. 

Para acceder simplemente al control **address_line1** en el control **address1_composite** debe utilizar: 

`formContext.getControl("address1_composite_compositionLinkControl_address1_line1")`

## <a name="composite-attributes-in-mobile-clients"></a>Atributos compuesto de clientes móviles
Los clientes de móviles de aplicaciones basadas en modelos usan las mismas definiciones de formulario usadas para las entidades que tienen atributos compuestos, pero las interpretan de forma distinta. Si se encuentra un atributo compuesto en la definición del formulario, mostrará todos los atributos que forman parte del atributo compuesto en esa sección del formulario. No se necesita un menú emergente debido a que todos los campos son visibles. Puede escribir de scripts para el formulario que tiene acceso a cada uno de los atributos individuales como si se hubiesen agregado individualmente al formulario.
Sin embargo, el control compuesto real no estará presente en la página de clientes móviles de aplicaciones basadas en modelos.

## <a name="mitigate-the-differences"></a>Mitigación de las diferencias

Si desea tener acceso al campo de nombre completo para las entidades de contactos , clientes potenciales o usuarios, mediante el método **formContext.data.entity**. [getPrimaryAttributeValue](formContext-data-entity/getPrimaryAttributeValue.md) es un modo sencillo de obtener el valor para este atributo sin hacer referencia a él directamente. Este método funciona en la aplicación web y en clientes móviles de aplicaciones basadas en modelos.

Si tiene un código que necesite leer el valor de uno de los atributos compuestos de dirección, para funcionar con ambos clientes, necesita separar el código mediante el método [getClient](Xrm-Utility/getGlobalContext/client.md#getclient) como se muestra en la siguiente función que mostrará la dirección formateada con el método **Xrm.Navigatio**. [openAlertDialog](Xrm-Navigation/openAlertDialog.md) en la aplicación web principal o la versión de aplicación para móviles del mismo formulario.

```JavaScript
function showAddressDialog(executionContext) {
    var address1_compositeValue;
    var formContext = executionContext.getFormContext();
    if (Xrm.Utility.getGlobalContext().client.getClient() != "Mobile") {
        address1_compositeValue = formContext.getAttribute("address1_composite").getValue();
    }
    else {
        var address1_line1 = formContext.getAttribute("address1_line1").getValue();
        var address1_line2 = formContext.getAttribute("address1_line2").getValue();
        var address1_line3 = formContext.getAttribute("address1_line3").getValue();
        var address1_city = formContext.getAttribute("address1_city").getValue();
        var address1_stateorprovince = formContext.getAttribute("address1_stateorprovince").getValue();
        var address1_postalcode = formContext.getAttribute("address1_postalcode").getValue();
        var address1_country = formContext.getAttribute("address1_country").getValue();

        // Achieve equivalent formatting
        //address1_line1
        //address1_line2
        //address1_line3
        //address1_city, address1_stateorprovince address1_postalcode
        //address1_country

        var addressText = "";
        if (address1_line1 != null) {
            addressText += address1_line1 + "\n";
        }
        if (address1_line2 != null) {
            addressText += address1_line2 + "\n";
        }
        if (address1_line3 != null) {
            addressText += address1_line3 + "\n";
        }
        if (address1_city != null) {
            addressText += address1_city + ", ";
        }
        if (address1_stateorprovince != null) {
            addressText += address1_stateorprovince + " ";
        }
        if (address1_postalcode != null) {
            addressText += address1_postalcode + "\n";
        }
        addressText += address1_country;

        address1_compositeValue = addressText;
    }
    Xrm.Navigation.openAlertDialog({ text: address1_compositeValue });
    console.log(address1_compositeValue);
}
```

### <a name="related-topics"></a>Temas relacionados
[Atributos](attributes.md)





