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
<li><a href="controls/addNotification.md" data-raw-source="[addNotification](controls/addNotification.md)">addNotification</a></li>
<li><a href="controls/clearNotification.md" data-raw-source="[clearNotification](controls/clearNotification.md)">clearNotification</a></li>
<li><a href="controls/getAttribute.md" data-raw-source="[getAttribute](controls/getAttribute.md)">getAttribute</a></a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setNotification.md" data-raw-source="[setNotification](controls/setNotification.md)">setNotification</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
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
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getInitialUrl.md" data-raw-source="[getInitialUrl](controls/getInitialUrl.md)">getInitialUrl</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getObject.md" data-raw-source="[getObject](controls/getObject.md)">getObject</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getSrc.md" data-raw-source="[getSrc](controls/getSrc.md)">getSrc</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setSrc.md" data-raw-source="[setSrc](controls/setSrc.md)">setSrc</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
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
<li><a href="controls/addOnPostSearch.md" data-raw-source="[addOnPostSearch](controls/addOnPostSearch.md)">addOnPostSearch</a></li>
<li><a href="controls/addOnResultOpened.md" data-raw-source="[addOnResultOpened](controls/addOnResultOpened.md)">addOnResultOpened</a></li>
<li><a href="controls/addOnSelection.md" data-raw-source="[addOnSelection](controls/addOnSelection.md)">addOnSelection</a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getSearchQuery.md" data-raw-source="[getSearchQuery](controls/getSearchQuery.md)">getSearchQuery</a></li>
<li><a href="controls/getSelectedResults.md" data-raw-source="[getSelectedResults](controls/getSelectedResults.md)">getSelectedResults</a></li>
<li><a href="controls/getTotalResultCount.md" data-raw-source="[getTotalResultCount](controls/getTotalResultCount.md)">getTotalResultCount</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/openSearchResult.md" data-raw-source="[openSearchResult](controls/openSearchResult.md)">openSearchResult</a></li>
<li><a href="controls/removeOnPostSearch.md" data-raw-source="[removeOnPostSearch](controls/removeOnPostSearch.md)">removeOnPostSearch</a></li>

</ul>
</td>
<td>
<ul>
<li><a href="controls/removeOnResultOpened.md" data-raw-source="[removeOnResultOpened](controls/removeOnResultOpened.md)">removeOnResultOpened</a></li>
<li><a href="controls/removeOnSelection.md" data-raw-source="[removeOnSelection](controls/removeOnSelection.md)">removeOnSelection</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setSearchQuery.md" data-raw-source="[setSearchQuery](controls/setSearchQuery.md)">setSearchQuery</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
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
<li><a href="controls/addCustomFilter.md" data-raw-source="[addCustomFilter](controls/addCustomFilter.md)">addCustomFilter</a></li>
<li><a href="controls/addCustomView.md" data-raw-source="[addCustomView](controls/addCustomView.md)">addCustomView</a></li>
<li><a href="controls/addNotification.md" data-raw-source="[addNotification](controls/addNotification.md)">addNotification</a></li>
<li><a href="controls/addPreSearch.md" data-raw-source="[addPreSearch](controls/addPreSearch.md)">addPreSearch</a></li>
<li><a href="controls/clearNotification.md" data-raw-source="[clearNotification](controls/clearNotification.md)">clearNotification</a></li>
<li><a href="controls/getAttribute.md" data-raw-source="[getAttribute](controls/getAttribute.md)">getAttribute</a></a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDefaultView.md" data-raw-source="[getDefaultView](controls/getDefaultView.md)">getDefaultView</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getEntityTypes.md" data-raw-source="[getEntityTypes](controls/getEntityTypes.md)">getEntityTypes</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/removePreSearch.md" data-raw-source="[removePreSearch](controls/removePreSearch.md)">removePreSearch</a></li>
<li><a href="controls/setDefaultView.md" data-raw-source="[setDefaultView](controls/setDefaultView.md)">setDefaultView</a></li>

</ul>
</td>
<td>
<ul>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
<li><a href="controls/setEntityTypes.md" data-raw-source="[setEntityTypes](controls/setEntityTypes.md)">setEntityTypes</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setNotification.md" data-raw-source="[setNotification](controls/setNotification.md)">setNotification</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
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
<li><a href="controls/addNotification.md" data-raw-source="[addNotification](controls/addNotification.md)">addNotification</a></li>
<li><a href="controls/addOption.md" data-raw-source="[addOption](controls/addOption.md)">addOption</a></li>
<li><a href="controls/clearNotification.md" data-raw-source="[clearNotification](controls/clearNotification.md)">clearNotification</a></li>
<li><a href="controls/clearOptions.md" data-raw-source="[clearOptions](controls/clearOptions.md)">clearOptions</a></li>
<li><a href="controls/getAttribute.md" data-raw-source="[getAttribute](controls/getAttribute.md)">getAttribute</a></a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/removeoption.md" data-raw-source="[removeOption](controls/removeoption.md)">removeOption</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setNotification.md" data-raw-source="[setNotification](controls/setNotification.md)">setNotification</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

## <a name="quickform-control-type"></a>Tipo de control quickform

Para obtener información acerca de los métodos compatibles con este tipo de control, consulte [formContext.ui.quickForms](formcontext-ui-quickforms.md).

## <a name="subgrid-control-type"></a>Tipo de control subgrid

Para obtener información acerca de los métodos compatibles con este tipo de control, consulte [Cuadrículas y subcuadrículas](grids.md).

## <a name="timelinewall-control-type"></a>Tipo de control timelinewall

El control timeline es un nuevo tipo de control que se introdujo en aplicaciones Dynamics 365 for Customer Engagement, versión 9.0 que muestra los mensajes, actividades y notas en una vista unificada. Estos son los métodos disponibles para este tipo de control.

<table>
<tr>
<td>
<ul>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>

<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/refresh.md" data-raw-source="[refresh](controls/refresh.md)">actualizar</a></li>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
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
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>

<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getState.md" data-raw-source="[getState](controls/getState.md)">getState</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/refresh.md" data-raw-source="[refresh](controls/refresh.md)">actualizar</a></li>

</ul>
</td>
<td>
<ul>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

## <a name="webresource-control-type"></a>Tipo de control webresource

Un control de recursos de web tiene el mismo conjunto de métodos disponibles que el control iframe. Consulte [Tipo de control iframe](#iframe-control-type)


### <a name="related-topics"></a>Temas relacionados

[Atributos](attributes.md)
