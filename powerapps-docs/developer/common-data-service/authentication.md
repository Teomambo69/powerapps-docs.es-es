---
title: Autenticación con servicios web de Common Data Service (Common Data Service) | Microsoft Docs
description: Introduce opciones de autenticación que dependen del marco de software que use.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 59351fbc8afa450a0de88e5e38ca9bcf812fee2b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749401"
---
# <a name="authentication-with-common-data-service-web-services"></a>Autenticación con servicios web de Common Data Service

Al crear aplicaciones cliente que usan servicios web de Common Data Service necesita autenticarse para tener acceso a datos. Cómo se autentica depende del marco de software que usa y del servicio web con el que desea conectarse.

## <a name="net-framework-applications"></a>Aplicaciones de .NET Framework

Si su aplicación cliente usa .NET Framework, tiene dos opciones:

- OAuth
- Office 365

### <a name="oauth"></a>OAuth

OAuth es el medio preferido para autenticarse porque proporciona acceso a *ambos* servicios web de OData RESTful (servicio de detección de API web y servicio de detección global de OData) así como a los servicios web de SOAP (Servicio de organización y de detección). 

OAuth también se requiere para admitir: 
 - Configuraciones de Azure Active Directory para acceso condicional, como la autenticación bifactorial (2FA).
 - Uso de secretos de cliente para habilitar escenarios de autenticación entre servidores.
 - Uso compartido de recursos de origen cruzado (CORS) para conectar una Aplicación de una sola página (SPA).

Más información: [Uso de OAuth con Common Data Service](authenticate-oauth.md)

### <a name="office-365"></a>Office 365

La autenticación de Office 365 requiere el uso de ensamblados de SDK de .NET Framework con los servicios web de SOAP únicamente.

El uso de la autenticación de Office 365 no requiere que registre sus aplicaciones igual que OAuth. Debe proporcionar simplemente un nombre principal de usuario (UPN) y una contraseña para un usuario válido.

Más información: [Autenticación con las aplicaciones de .NET Framework](authenticate-dot-net-framework.md)

## <a name="all-other-software-frameworks"></a>El resto de los marcos de software

Si usa elementos distintos de .NET Framework, debe autenticarse mediante el uso de OAuth y debe usar los servicios web de OData RESTful (servicio de detección de API web y de detección global de OData).

Más información:  [Uso de OAuth con Common Data Service](authenticate-oauth.md)
