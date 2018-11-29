---
title: setCurrentView (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f5ee65bf-2964-49c9-9dd2-d81416353bf3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setcurrentview-client-api-reference"></a>setCurrentView (referencia de la API de cliente)



[!INCLUDE[./includes/setCurrentView-description.md](./includes/setCurrentView-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrícula de solo lectura

## <a name="syntax"></a>Sintaxis

`viewSelector.setCurrentView(object);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|objeto|Búsqueda de objetos|Sí|Especifique el objeto de búsqueda que tenga los siguientes atributos:<br/>- **entityType**: Número. El código de tipo de objeto para SavedQuery (1039) o UserQuery (4230) que representa la vista que el usuario puede seleccionar.<br/>- **id**: cadena. El identificador de la vista que el usuario puede seleccionar.<br/>- **name**: cadena. El nombre de la vista que el usuario puede seleccionar.|

## <a name="remarks"></a>Comentarios

Si el control de subcuadrícula no está configurado para mostrar el selector de vistas, al llamar a este método en el objeto `viewSelector` producirá un error.

Para obtener el objeto `viewSelector`, vea [ViewSelector](../viewselector.md).

## <a name="example"></a>Ejemplo

```JavaScript
function setView(executionContext) {
    var ContactsIFollow = {
        entityType: 1039, // SavedQuery
        id: "3A282DA1-5D90-E011-95AE-00155D9CFA02",
        name: "Contacts I Follow"
    }
    // Get the gridContext
    var formContext = executionContext.getFormContext();
    var gridContext = formContext.getControl("Contacts");

    // Set the view using ContactsIFollow
    gridContext.getViewSelector().setCurrentView(ContactsIFollow);
}
```

### <a name="related-topics"></a>Temas relacionados

[ViewSelector](../viewselector.md)




