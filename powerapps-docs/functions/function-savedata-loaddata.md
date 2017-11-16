---
title: Funciones SaveData y LoadData | Microsoft Docs
description: "Información de referencia para las funciones SaveData y LoadData en PowerApps, incluida la sintaxis"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: aa62882841ee4d585720a2241dff8b9f35c88059
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>Funciones SaveData y LoadData en PowerApps
Guarda y vuelve a cargar una [colección](../working-with-data-sources.md#collections).

## <a name="description"></a>Descripción
La función **SaveData** almacena una colección para su uso posterior con un nombre.  

La función **LoadData** vuelve a cargar una colección por el nombre guardado anteriormente con **SaveData**. No se puede utilizar esta función para cargar una colección de otro origen.  

**LoadData** no crea la colección; la función solo rellena una colección existente. Primero tiene que crear la colección con las [columnas](../working-with-tables.md#columns) correctas utilizando **[Recopilar](function-clear-collect-clearcollect.md)**.

El almacenamiento está cifrado y se encuentra en una ubicación privada en el dispositivo local, aislado de otros usuarios y otras aplicaciones.  

## <a name="syntax"></a>Sintaxis
**SaveData**( *Colección*, *Nombre* )<br>**LoadData**( *Collection*, *Name* [, *IgnoreNonexistentFile* ])

* *Colección*: requerido.  Colección para almacenar o cargar.
* *Nombre*: requerido.  Nombre del almacenamiento. Tiene que usar el mismo nombre para guardar y cargar el mismo conjunto de datos. El espacio de nombres no se comparte con otros usuarios o aplicaciones.
* *IgnoreNonexistentFile*: opcional. Valor booleano (**true**/**false**) que indica si la función **LoadData** debe mostrar o ignorar los errores cuando no encuentre un archivo coincidente. Si especifica **false**, se mostrarán los errores. Si especifica **true**, se omitirán los errores, lo que resulta útil para escenarios sin conexión. **SaveData** puede crear un archivo si el dispositivo está desconectado (es decir, si el estado **Connection.Connected** es **false**).

## <a name="examples"></a>Ejemplos
| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **If(Connection.Connected, ClearCollect(LocalTweets, Twitter.SearchTweet("PowerApps", {maxResults: 100})),LoadData(LocalTweets, "Tweets", true))** |Si el dispositivo está conectado, cargue la colección LocalTweets del servicio Twitter; si no lo está, cargue la colección de la caché de archivos local. |El contenido se presenta tanto si el dispositivo está conectado como desconectado. |
| **SaveData(LocalTweets, "Tweets")** |Guarde la colección LocalTweets como una caché de archivos local en el dispositivo. |Los datos se guardan localmente para que **LoadData** puede cargarlos en una colección. |

