---
title: Funciones Download, Launch y Parámetro | Microsoft Docs
description: Información de referencia de las funciones Download, Launch y Parámetro de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: f2af4fef413aa5502c57e7158d9efdddd36757c9
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39021881"
---
# <a name="download-launch-and-param-functions-in-powerapps"></a>Funciones Download, Launch y Parámetro en PowerApps
Descarga o inicia una página web o una aplicación con parámetros.  

## <a name="description"></a>Descripción
La función **Download** descarga un archivo de la Web al dispositivo local.  Se pide al usuario una ubicación para guardar el archivo.  **Download** devuelve la ubicación donde el archivo se almacenó localmente como una cadena.  

La función **Launch** inicia un página web o una aplicación.  Opcionalmente, esta función puede pasar parámetros a la aplicación.  

La función **Param** recupera un parámetro pasado a la aplicación cuando se inició.  Si no se pasó el parámetro con nombre, **Param** devuelve *en blanco*.

## <a name="syntax"></a>Sintaxis
**Download**( *Address* )

* *Address*: requerido.  La dirección de un recurso web para descargar.

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address*: requerido.  La dirección de una página web o el identificador de una aplicación que se va a iniciar.
* *ParameterName(s)*: valor opcional.  Nombre del parámetro.
* *ParameterValue(s)*: valor opcional.  Valores de parámetro correspondientes para pasar a la aplicación o la página web.

**Param**( *ParameterName* )

* *ParameterName*: requerido.  El nombre del parámetro pasado a la aplicación.

