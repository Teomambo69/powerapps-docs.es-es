---
title: addCustomView (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 482b8cd4-e643-48ea-8a54-d8601271ec81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addcustomview-client-api-reference"></a>addCustomView (referencia de la API de cliente)



Agrega una vista nueva para el cuadro de diálogo de búsqueda. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).addCustomView(viewId, entityName, viewDisplayName, fetchXml, layoutXml, isDefault)`

## <a name="parameters"></a>Parámetros

- **viewId**: cadena. La representación de cadena de un GUID para una vista.
    > [!NOTE]
    > Este valor nunca se guarda y solo debe ser único entre las otras vistas disponibles para la búsqueda. Funcionará una cadena para un GUID no válido, por ejemplo “00000000-0000-0000-0000-000000000001”. Se recomienda usar una herramienta como **guidgen.exe** para generar un GUID válido.  

- **entityName**: cadena. El nombre de la entidad.
- **viewDisplayName**: cadena. El nombre de la vista.
- **fetchXml**: cadena. La consulta de fetchXml para la vista.
- **layoutXml**: cadena. El XML que define el diseño de la vista.
- **isDefault**: booleano: indica si la vista debe ser la vista predeterminada.

## <a name="remarks"></a>Comentarios

Este método no funciona en búsquedas **Propietario**. Las búsquedas de propietario se usan para asignar registros propiedad del usuario.
