---
title: Atributos en aplicaciones basadas en modelos | MicrosoftDocs
description: Aprenda a trabajar con atributos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="attributes-client-api-reference"></a>Atributos (referencia de la API de cliente)



Los atributos contienen datos en el formulario o las cuadrículas de aplicaciones basadas en modelos. Use la colección de `formContext.data.entity.attributes` o el método de acceso directo `formContext.getAttribute` para acceder a una colección de atributos. Para obtener más información acerca de las colecciones, vea [Colecciones (referencia de la API de cliente)](collections.md). 

Para obtener acceso a un atributo dentro de la colección, debe pasar el nombre (cadena) o el valor de índice (número) del atributo como un argumento al método. Por ejemplo: `formContext.getAttribute(arg)`

Los atributos se clasifican por tipo. Puede determinar el tipo de un atributo mediante el método [getAttributeType](attributes/getAttributeType.md). Algunos métodos de atributos solo están disponibles para tipos específicos de atributos.

En este tema se ofrece información sobre los métodos disponibles por tipo de atributo. 

## <a name="all-attribute-types"></a>Todos los tipos de atributos

<table>
<tr>
<td>
<ul>
<li>[controles](attributes/controls-collection.md)</li>
<li>[addOnChange](attributes/addOnChange.md)</li>
<li>[fireOnChange](attributes/fireOnChange.md)</a></li>
<li>[getAttributeType](attributes/getAttributeType.md)</li>
<li>[getFormat](attributes/getFormat.md)</li>
<li>[getIsDirty](attributes/getIsDirty.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getName](attributes/getName.md)</li>
<li>[getParent](attributes/getParent.md)</li>
<li>[getRequiredLevel](attributes/getRequiredLevel.md)</li>
<li>[getSubmitMode](attributes/getSubmitMode.md)</li>
<li>[getUserPrivilege](attributes/getUserPrivilege.md)</li>
<li>[getValue](attributes/getValue.md)</li>
</ul>
</td>
<td>
<ul>

<li>[isValid](attributes/isValid.md)</li>
<li>[removeOnChange](attributes/removeOnChange.md)</li>
<li>[setRequiredLevel](attributes/setRequiredLevel.md)</li>
<li>[setSubmitMode](attributes/setSubmitMode.md)</li>
<li>[setValue](attributes/setValue.md)</li>
</ul>
</td>
</tr>
</table>


## <a name="boolean-attribute-type"></a>Tipo de atributo Boolean
Además de los métodos disponibles para todos los tipos de atributos tal como se explicó anteriormente, el método siguiente está disponible solo para el atributo **booleano**:

- [getInitialValue](attributes/getInitialValue.md)

## <a name="lookup-attribute-type"></a>Tipo de atributo Lookup
Además de los métodos disponibles para todos los tipos de atributos tal como se explicó anteriormente, el método siguiente está disponible solo para el atributo **lookup**:

- [getIsPartyList](attributes/getIsPartyList.md)

## <a name="multiselectoptionset-and-optionset-attribute-types"></a>Tipos de atributos MultiSelectOptionSet y OptionSet

Además de los métodos disponibles para todos los tipos de atributos tal como se explicó anteriormente, los métodos siguientes están disponibles solo para los atributos **multiselectoption** y **optionset**:

<table>
<tr>
<td>
<ul>
<li>[getInitialValue](attributes/getInitialValue.md)</li>
<li>[getOption](attributes/getOption.md)</li>
<li>[getOptions](attributes/getOptions.md)</a></li>
<li>[getSelectedOption](attributes/getSelectedOption.md)</li>
<li>[getText](attributes/getText.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="number-attribute-type-decimal-double-integer-money"></a>Tipos de atributo Number (decimal, doble, entero, dinero)
Los siguientes métodos están disponibles para los atributos **decimal**, **double** e **integer**:

<table>
<tr>
<td>
<ul>
<li>[getMax](attributes/getMax.md)</li>
<li>[getMin](attributes/getMin.md)</li>
<li>[getPrecision](attributes/getPrecision.md)</a></li>
<li>[setPrecision](attributes/setPrecision.md)</li>
<li>[getText](attributes/getText.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="string-attribute-type"></a>Tipo de atributo String
Además de los métodos disponibles para todos los tipos de atributos tal como se explicó anteriormente, el método siguiente está disponible solo para el atributo **string**:

- [getMaxLength](attributes/getMaxLength.md)

### <a name="related-topics"></a>Temas relacionados

[Atributos compuestos](composite-attributes.md)

[Comprender el modelo de objetos Xrm](../understand-clientapi-object-model.md)

[Controles (referencia de la API de cliente)](controls.md)




