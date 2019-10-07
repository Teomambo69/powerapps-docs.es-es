---
title: Funciones Download, Launch y Param | Microsoft Docs
description: Información de referencia, con sintaxis y ejemplos, para las funciones de descarga, Inicio y parámetros de las aplicaciones de Canvas
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c6fb3c5ef002ed0355cc8061603e4f4b1f438e6e
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992499"
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>Funciones de descarga, Inicio y parámetro en aplicaciones de Canvas
Descarga o inicia una página web o una aplicación con parámetros.  

## <a name="description"></a>Descripción
La función **Download** descarga un archivo de la Web al dispositivo local. Se pide al usuario una ubicación para guardar el archivo.  **Download** devuelve la ubicación donde el archivo se almacenó localmente como una cadena.  

La función **Launch** inicia un página web o una aplicación.  Opcionalmente, esta función puede pasar parámetros a la aplicación.

En Internet Explorer y Microsoft Edge, la función **Launch** abre un sitio web o una aplicación solo si su configuración de seguridad es igual o superior a la de la aplicación que contiene la función. Si, por ejemplo, agrega la función de **Inicio** a una aplicación que se ejecutará en la zona de seguridad **sitios de confianza** , asegúrese de que el sitio web o la aplicación que desea que la función abra se encuentra en la zona de sitios de **confianza** o **Intranet local** (no en  **Sitios restringidos**). Más información: [Cambiar la configuración de seguridad y privacidad para Internet Explorer 11](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings).  

La función **Param** recupera un parámetro pasado a la aplicación cuando se inició. Si no se pasó el parámetro con nombre, **Param** devuelve *blank*.

## <a name="syntax"></a>Sintaxis
**Download**( *Address* )

* *Address*: requerido.  La dirección de un recurso web para descargar.

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address*: requerido.  La dirección de una página web o el identificador de una aplicación que se va a iniciar.
* *ParameterName(s)* : valor opcional.  Nombre del parámetro.
* *ParameterValue(s)* : valor opcional.  Valores de parámetro correspondientes para pasar a la aplicación o la página web.

**Param**( *ParameterName* )

* *ParameterName*: requerido.  El nombre del parámetro pasado a la aplicación.

