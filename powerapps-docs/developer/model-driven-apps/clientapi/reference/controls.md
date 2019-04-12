---
title: Controles en las aplicaciones basadas en modelos para Dynamics 365 | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="controls-client-api-reference"></a>Controles (referencia de la API de cliente)



Un control representa un elemento HTML incluido en el formulario. Algunos controles se enlazan a un atributo específico, mientras que otros pueden representar controles sin enlazar como un IFRAME, un recurso web o una subcuadrícula que se ha agregado al formulario. 

El objeto **control** proporciona métodos para cambiar la presentación o el comportamiento de un control e identificar el atributo correspondiente. El acceso a los controles se realiza utilizando una de las colecciones siguientes: 
- **formContext.ui.controls**
- **formContext.ui Section.controls**
- **formContext.data.entity** **Attribute.controls**

El método **formContext**.[getControl](controls/getControl.md) es un acceso directo para acceder a **formContext.ui.controls.get**. 

Los controles se clasifican por tipo. Puede determinar el tipo de un control mediante el método [getControlType](controls/getControlType.md). Algunos métodos de control solo están disponibles para tipos específicos de controles.

En este tema se ofrece información sobre los métodos disponibles por tipo de control. 

## <a name="standard-control-type"></a>Tipo de control standard

Estos son los métodos disponibles para un control estándar.

<table>
<tr>
<td>
<ul>
<li>[addNotification](controls/addNotification.md)</li>
<li>[clearNotification](controls/clearNotification.md)</li>
<li>[getAttribute](controls/getAttribute.md)</a></li>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[setDisabled](controls/setDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setNotification](controls/setNotification.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

Los siguientes métodos para el control estándar están [obsoletos](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) en esta versión: addOnKeyPress, fireOnKeyPress y removeOnKeyPress.

## <a name="iframe-control-type"></a>Tipo de control iframe

Estos son los métodos disponibles para un control IFRAME.

<table>
<tr>
<td>
<ul>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getInitialUrl](controls/getInitialUrl.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getObject](controls/getObject.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getSrc](controls/getSrc.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[setDisabled](controls/setDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setSrc](controls/setSrc.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="kbsearch-knowledge-base-search-control-type"></a>Tipo de control kbsearch (búsqueda de knowledge base)

Estos son los métodos disponibles para el control de búsqueda de knowledge base.

<table>
<tr>
<td>
<ul>
<li>[addOnPostSearch](controls/addOnPostSearch.md)</li>
<li>[addOnResultOpened](controls/addOnResultOpened.md)</li>
<li>[addOnSelection](controls/addOnSelection.md)</li>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getParent](controls/getParent.md)</li>
<li>[getSearchQuery](controls/getSearchQuery.md)</li>
<li>[getSelectedResults](controls/getSelectedResults.md)</li>
<li>[getTotalResultCount](controls/getTotalResultCount.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[openSearchResult](controls/openSearchResult.md)</li>
<li>[removeOnPostSearch](controls/removeOnPostSearch.md)</li>

</ul>
</td>
<td>
<ul>
<li>[removeOnResultOpened](controls/removeOnResultOpened.md)</li>
<li>[removeOnSelection](controls/removeOnSelection.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setSearchQuery](controls/setSearchQuery.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

>[!NOTE]
>Cuando el control de búsqueda de knowledge base se agrega al panel social, el nombre del control será "searchwidgetcontrol_notescontrol". Este nombre no se puede cambiar. 

## <a name="lookup-control-type"></a>Tipo de control lookup.

Estos son los métodos disponibles para un control de búsqueda.

<table>
<tr>
<td>
<ul>
<li>[addCustomFilter](controls/addCustomFilter.md)</li>
<li>[addCustomView](controls/addCustomView.md)</li>
<li>[addNotification](controls/addNotification.md)</li>
<li>[addPreSearch](controls/addPreSearch.md)</li>
<li>[clearNotification](controls/clearNotification.md)</li>
<li>[getAttribute](controls/getAttribute.md)</a></li>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDefaultView](controls/getDefaultView.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getEntityTypes](controls/getEntityTypes.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[removePreSearch](controls/removePreSearch.md)</li>
<li>[setDefaultView](controls/setDefaultView.md)</li>

</ul>
</td>
<td>
<ul>
<li>[setDisabled](controls/setDisabled.md)</li>
<li>[setEntityTypes](controls/setEntityTypes.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setNotification](controls/setNotification.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="multiselectoptionset-and-optionset-control-types"></a>Tipos de control multiselectoptionset y optionset

Tanto los controles de conjunto de opciones de selección múltiple como conjunto de opciones tienen el mismo conjunto de métodos disponibles.

<table>
<tr>
<td>
<ul>
<li>[addNotification](controls/addNotification.md)</li>
<li>[addOption](controls/addOption.md)</li>
<li>[clearNotification](controls/clearNotification.md)</li>
<li>[clearOptions](controls/clearOptions.md)</li>
<li>[getAttribute](controls/getAttribute.md)</a></li>
<li>[getControlType](controls/getControlType.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[removeOption](controls/removeoption.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setDisabled](controls/setDisabled.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setNotification](controls/setNotification.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="quickform-control-type"></a>Tipo de control quickform

Para obtener información acerca de los métodos compatibles con este tipo de control, consulte [formContext.ui.quickForms](formcontext-ui-quickforms.md).

## <a name="subgrid-control-type"></a>Tipo de control subgrid

Para obtener información acerca de los métodos compatibles con este tipo de control, consulte [Cuadrículas y subcuadrículas](grids.md).

## <a name="timelinewall-control-type"></a>Tipo de control timelinewall

El control timeline es un nuevo tipo de control que se introdujo en aplicaciones basadas en modelos (en línea), versión 9.0 que muestra los mensajes, actividades y notas en una vista unificada. Estos son los métodos disponibles para este tipo de control.

<table>
<tr>
<td>
<ul>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>

<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[actualizar](controls/refresh.md)</li>
<li>[setDisabled](controls/setDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="timer-control-type"></a>Tipo de control timer

Estos son los métodos disponibles para el control timer.

<table>
<tr>
<td>
<ul>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>

<li>[getParent](controls/getParent.md)</li>
<li>[getState](controls/getState.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[actualizar](controls/refresh.md)</li>

</ul>
</td>
<td>
<ul>
<li>[setDisabled](controls/setDisabled.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="webresource-control-type"></a>Tipo de control webresource

Un control de recursos de web tiene el mismo conjunto de métodos disponibles que el control iframe. Consulte [Tipo de control iframe](#iframe-control-type)

### <a name="related-topics"></a>Temas relacionados

[Atributos](attributes.md)