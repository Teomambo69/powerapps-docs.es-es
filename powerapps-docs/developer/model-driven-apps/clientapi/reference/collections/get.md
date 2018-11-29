---
title: Método get para colecciones (referencia de la API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
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
# <a name="get-method-for-collections-client-api-reference"></a>obtener método de colecciones (referencia de la API de cliente)



[!INCLUDE[./includes/get-description.md](./includes/get-description.md)]

## <a name="syntax"></a>Sintaxis

`collection.get([String][Number][delegate function(attribute, index)])`

## <a name="parameters"></a>Parámetros

|Parámetro  |Valor devuelto |Tipo devuelto  |
|---------|------|-------|
|Ninguna  |Todos los objetos de la colección  |Matriz|
|String  |El objeto en el que el nombre coincide con los argumentos<br/><br/>Los objetos devueltos en el espacio de nombres **formContext.data.process** no contienen nombres. Por lo tanto, usar el parámetro de cadena de este método no devuelve ningún objeto.  |Objeto|
|Número  |El objeto en el que el índice coincide con el número  |Objeto|
|función de delegado (atributo, índice)  |Los objetos que hacen que la función de delegado devuelva **true**.  |Matriz|


### <a name="related-topics"></a>Temas relacionados
[Colecciones de la API de cliente](../collections.md)

[forEach](forEach.md)

[getLength](getLength.md)

