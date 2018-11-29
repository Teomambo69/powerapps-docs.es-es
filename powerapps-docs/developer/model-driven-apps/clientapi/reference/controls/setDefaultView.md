---
title: setDefaultView (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8c918cd4-d0ce-45e5-91a3-1addf11258c7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setdefaultview-client-api-reference"></a>setDefaultView (referencia de la API de cliente)



Establece la vista predeterminada para el cuadro de diálogo de control de búsqueda.

## <a name="control-types-supported"></a>Tipos de control admitidos

Búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).setDefaultView(viewId);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|viewId|String|Sí|El identificador de la vista que se establecerá como vista predeterminada.|

## <a name="example"></a>Ejemplo

Esta función **setDefaultViewSample** establecerá la vista predeterminada de búsqueda de contacto principal del formulario de entidad **account** en la vista **Mis contactos activos**.

```JavaScript
function setDefaultViewSample(executionContext) {
    var formContext = executionContext.getFormContext();
    formContext.getControl("primarycontactid").setDefaultView("{00000000-0000-0000-00AA-000010001003}");
}
```

### <a name="related-topics"></a>Temas relacionados

[getDefaultView](getDefaultView.md) 


