---
title: save (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a27f8267-9b24-42b7-a075-420a26db6693
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="save-client-api-reference"></a>Guardar (referencia de la API de cliente)



[!INCLUDE[./includes/save-description.md](./includes/save-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.entity.save(saveOption);`

## <a name="parameters"></a>Parámetros

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|saveOption|String|No|Especifique las opciones para guardar el registro. Si no se incluye ningún parámetro en el método, el registro simplemente se guardará. Esto es el equivalente a usar el comando **Guardar**.<br/>Puede especificar uno de los siguientes valores:<br/><br/>- **saveandclose**: Esto es equivalente a usar el comando **Guardar y cerrar**.<br/><br/>- **saveandnew**: Esto es equivalente a usar el comando **Guardar y nuevo**.|

## <a name="example"></a>Ejemplo

Para abrir un nuevo formulario después de guardar:

`formContext.data.entity.save("saveandnew");`

### <a name="related-topics"></a>Temas relacionados

[formContext.data.save](../formContext-data/save.md)

[formContext](../../clientapi-form-context.md)

