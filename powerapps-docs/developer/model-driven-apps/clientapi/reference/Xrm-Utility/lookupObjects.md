---
title: lookupObjects (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 01/24/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="lookupobjects-client-api-reference"></a>lookupObjects (referencia de la API de cliente)



[!INCLUDE[./includes/lookupObjects-description.md](./includes/lookupObjects-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.Utility.lookupObjects(lookupOptions).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

**lookupOptions**: objeto. Define las opciones para abrir el cuadro de diálogo de búsqueda. Tiene las siguientes propiedades:

|Nombre de la propiedad |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|allowMultiSelect|Boolean|No|Indica si la búsqueda permite que se seleccione más de un elemento.|
|defaultEntityType|String|No|El tipo de entidad predeterminada que se usa.|
|defaultViewId|String|No|La vista predeterminada que se usa.|
|disableMru|Boolean|No|Decide si mostrar un el elemento (MRU) usado más recientemente.<br />Disponible solo en la interfaz unificada.|
|entityTypes|Matriz|No|Los tipos de entidad que se muestran.|
|filtros|Matriz de objetos|No|Usado para filtrar los resultados. Cada objeto en la matriz contiene los siguientes atributos:<br /><ul><li>**filterXml**: cadena. El elemento de filtro FetchXML a aplicar.</li><li>**entityLogicalName**: cadena. El tipo de entidad a la que aplicará este filtro.</li></ul>|
|showBarcodeScanner|Boolean|No|Indica si el control de búsqueda debe mostrar el escáner de código de barras en los clientes móviles.|
|viewIds|Matriz|No|Las vistas que están disponibles en el selector de vistas. Se admiten únicamente vistas del sistema.|
|successCallback |Función |Sí |Una función para llamar cuando se llama al control de búsqueda. Se pasa una matriz de objetos con las siguientes propiedades:<br/><ul><li>**entityType**: cadena. Tipo de entidad del registro seleccionado en el control de búsqueda.</li><li>**id**: cadena. Identificador del registro seleccionado en el control de búsqueda.</li><li>**nombre**: cadena. Nombre del registro seleccionado en el control de búsqueda.</li>|
|errorCallback |Función |Sí |Una función a la que se llama cuando se cancela el control de búsqueda o se produce un error en la operación.  |


### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility](../xrm-utility.md)
