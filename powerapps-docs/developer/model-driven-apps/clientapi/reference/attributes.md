---
title: Atributos en aplicaciones basadas en modelos | MicrosoftDocs
description: Aprenda a trabajar con atributos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: powerapps
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
<li><a href="attributes/controls-collection.md" data-raw-source="[controls](attributes/controls-collection.md)">controles</a></li>
<li><a href="attributes/addOnChange.md" data-raw-source="[addOnChange](attributes/addOnChange.md)">addOnChange</a></li>
<li><a href="attributes/fireOnChange.md" data-raw-source="[fireOnChange](attributes/fireOnChange.md)">fireOnChange</a></a></li>
<li><a href="attributes/getAttributeType.md" data-raw-source="[getAttributeType](attributes/getAttributeType.md)">getAttributeType</a></li>
<li><a href="attributes/getFormat.md" data-raw-source="[getFormat](attributes/getFormat.md)">getFormat</a></li>
<li><a href="attributes/getIsDirty.md" data-raw-source="[getIsDirty](attributes/getIsDirty.md)">getIsDirty</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="attributes/getName.md" data-raw-source="[getName](attributes/getName.md)">getName</a></li>
<li><a href="attributes/getParent.md" data-raw-source="[getParent](attributes/getParent.md)">getParent</a></li>
<li><a href="attributes/getRequiredLevel.md" data-raw-source="[getRequiredLevel](attributes/getRequiredLevel.md)">getRequiredLevel</a></li>
<li><a href="attributes/getSubmitMode.md" data-raw-source="[getSubmitMode](attributes/getSubmitMode.md)">getSubmitMode</a></li>
<li><a href="attributes/getUserPrivilege.md" data-raw-source="[getUserPrivilege](attributes/getUserPrivilege.md)">getUserPrivilege</a></li>
<li><a href="attributes/getValue.md" data-raw-source="[getValue](attributes/getValue.md)">getValue</a></li>
</ul>
</td>
<td>
<ul>

<li><a href="attributes/isValid.md" data-raw-source="[isValid](attributes/isValid.md)">isValid</a></li>
<li><a href="attributes/removeOnChange.md" data-raw-source="[removeOnChange](attributes/removeOnChange.md)">removeOnChange</a></li>
<li><a href="attributes/setRequiredLevel.md" data-raw-source="[setRequiredLevel](attributes/setRequiredLevel.md)">setRequiredLevel</a></li>
<li><a href="attributes/setSubmitMode.md" data-raw-source="[setSubmitMode](attributes/setSubmitMode.md)">setSubmitMode</a></li>
<li><a href="attributes/setValue.md" data-raw-source="[setValue](attributes/setValue.md)">setValue</a></li>
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
<li><a href="attributes/getInitialValue.md" data-raw-source="[getInitialValue](attributes/getInitialValue.md)">getInitialValue</a></li>
<li><a href="attributes/getOption.md" data-raw-source="[getOption](attributes/getOption.md)">getOption</a></li>
<li><a href="attributes/getOptions.md" data-raw-source="[getOptions](attributes/getOptions.md)">getOptions</a></a></li>
<li><a href="attributes/getSelectedOption.md" data-raw-source="[getSelectedOption](attributes/getSelectedOption.md)">getSelectedOption</a></li>
<li><a href="attributes/getText.md" data-raw-source="[getText](attributes/getText.md)">getText</a></li>
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
<li><a href="attributes/getMax.md" data-raw-source="[getMax](attributes/getMax.md)">getMax</a></li>
<li><a href="attributes/getMin.md" data-raw-source="[getMin](attributes/getMin.md)">getMin</a></li>
<li><a href="attributes/getPrecision.md" data-raw-source="[getPrecision](attributes/getPrecision.md)">getPrecision</a></a></li>
<li><a href="attributes/setPrecision.md" data-raw-source="[setPrecision](attributes/setPrecision.md)">setPrecision</a></li>
<li><a href="attributes/getText.md" data-raw-source="[getText](attributes/getText.md)">getText</a></li>
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




