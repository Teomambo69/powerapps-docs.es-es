---
title: Funciones Download, Launch y Param | Microsoft Docs
description: Información de referencia, incluida la sintaxis y ejemplos para las funciones Download, Launch y parámetro en las aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4a53d8c20bd4b7784cb94daa574682c041f104ea
ms.sourcegitcommit: 0267e58b305f9fb0a4b32130fb149cd6e34b3354
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "59993789"
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>Funciones download, Launch y parámetro en las aplicaciones de lienzo
Descarga o inicia una página web o una aplicación con parámetros.  

## <a name="description"></a>Descripción
La función **Download** descarga un archivo de la Web al dispositivo local. Se pide al usuario una ubicación para guardar el archivo.  **Download** devuelve la ubicación donde el archivo se almacenó localmente como una cadena.  

La función **Launch** inicia un página web o una aplicación.  Opcionalmente, esta función puede pasar parámetros a la aplicación.

En Internet Explorer y Microsoft Edge, la **iniciar** función abre un sitio Web o aplicación solo si su configuración de seguridad es iguales o superior a los de la aplicación que contiene la función. Si, por ejemplo, agrega el **iniciar** función a una aplicación que se ejecutará en el **sitios de confianza** seguridad de la zona, asegúrese de que el sitio Web o aplicación que quiere que la función para abrir está en el **confianza sitios** o **intranet Local** zona (no en **sitios restringidos**). Más información: [Cambiar la configuración de seguridad y privacidad de Internet Explorer 11](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings).  

La función **Param** recupera un parámetro pasado a la aplicación cuando se inició. Si no se pasó el parámetro con nombre, **Param** devuelve *blank*.

## <a name="syntax"></a>Sintaxis
**Download**( *Address* )

* *Address*: requerido.  La dirección de un recurso web para descargar.

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address*: requerido.  La dirección de una página web o el identificador de una aplicación que se va a iniciar.
* *ParameterName(s)*: valor opcional.  Nombre del parámetro.
* *ParameterValue(s)*: valor opcional.  Valores de parámetro correspondientes para pasar a la aplicación o la página web.

**Param**( *ParameterName* )

* *ParameterName*: requerido.  El nombre del parámetro pasado a la aplicación.

