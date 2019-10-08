---
title: Funciones SaveData y LoadData | Microsoft Docs
description: Información de referencia para las funciones SaveData y LoadData en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e716de7a3551e2195d3f3459540a6f68acb4fd51
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992290"
ms.PowerAppsDecimalTransform: true
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>Funciones SaveData y LoadData en PowerApps
Guarda y vuelve a cargar una [colección](../working-with-data-sources.md#collections).

## <a name="description"></a>Descripción
La función **SaveData** almacena una colección para su uso posterior con un nombre.  

La función **LoadData** vuelve a cargar una colección por el nombre guardado anteriormente con **SaveData**. No se puede utilizar esta función para cargar una colección de otro origen.  

Use estas funciones para mejorar el rendimiento de inicio de la aplicación almacenando en caché los datos de la fórmula **[app. OnStart](../controls/control-screen.md#additional-properties)** en una primera ejecución y volviendo a cargar la memoria caché local en ejecuciones posteriores. También puede usar estas funciones para agregar [funcionalidades sin conexión sencillas](../offline-apps.md) a la aplicación.

No puede usar estas funciones dentro de un explorador, ya sea al crear la aplicación en PowerApps Studio o al ejecutar la aplicación en el reproductor Web. Para probar la aplicación, ejecútela en PowerApps Mobile en un dispositivo iPhone o Android.

Estas funciones están limitadas por la cantidad de memoria de la aplicación disponible, ya que operan en una colección en memoria. La memoria disponible puede variar según el dispositivo y el sistema operativo, la memoria que usa el reproductor de PowerApps y la complejidad de la aplicación en términos de pantallas y controles. Si almacena más de unos megabytes de datos, pruebe la aplicación con los escenarios esperados en los dispositivos en los que espera que la aplicación se ejecute. Por lo general, debe esperar entre 30 y 70 megabytes de memoria disponible.  

**LoadData** no crea la colección; la función solo rellena una colección existente. Primero tiene que crear la colección con las [columnas](../working-with-tables.md#columns) correctas utilizando **[Recopilar](function-clear-collect-clearcollect.md)** . Los datos cargados se anexarán a la colección; Utilice primero la función **[Clear](function-clear-collect-clearcollect.md)** si desea empezar con una colección vacía.

El almacenamiento está cifrado y se encuentra en una ubicación privada en el dispositivo local, aislado de otros usuarios y otras aplicaciones.

## <a name="syntax"></a>Sintaxis
**SaveData**( *Colección*; *Nombre* )<br>**LoadData**( *Collection*; *Name* [; *IgnoreNonexistentFile* ])

* *Colección*: requerido.  Colección para almacenar o cargar.
* *Nombre*: requerido.  Nombre del almacenamiento. Tiene que usar el mismo nombre para guardar y cargar el mismo conjunto de datos. El espacio de nombres no se comparte con otros usuarios o aplicaciones.
* *IgnoreNonexistentFile*: opcional. Valor booleano (**true**/**false**) que indica si la función **LoadData** debe mostrar o ignorar los errores cuando no encuentre un archivo coincidente. Si especifica **false**, se mostrarán los errores. Si especifica **true**, se omitirán los errores, lo que resulta útil para escenarios sin conexión. **SaveData** puede crear un archivo si el dispositivo está desconectado (es decir, si el estado **Connection.Connected** es **false**).

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **If (Connection. Connected; ClearCollect (LocalTweets; Twitter. SearchTweet ("PowerApps"; {maxResults: 100})); LoadData (LocalTweets; "tweets"; true))** |Si el dispositivo está conectado, cargue la colección LocalTweets del servicio Twitter; si no lo está, cargue la colección de la caché de archivos local. |El contenido se presenta tanto si el dispositivo está conectado como desconectado. |
| **SaveData(LocalTweets; "Tweets")** |Guarde la colección LocalTweets como una caché de archivos local en el dispositivo. |Los datos se guardan localmente para que **LoadData** puede cargarlos en una colección. |

