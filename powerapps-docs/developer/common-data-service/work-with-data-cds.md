---
title: Trabajar con datos con código en Common Data Service (PowerApps) | Microsoft Docs
description: 'Common Data Service proporciona dos servicios web que puede usar para interactuar con datos: API web y servicio de la organización.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3da5976eba337c6b816f7414403876f3470b77ea
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154913"
---
# <a name="work-with-data-using-code-in-common-data-service"></a>Trabajar con datos mediante código en Common Data Service

Common Data Service tiene [entidades](entities.md) que se utilizan para modelar y administrar datos profesionales. Puede usar entidades estándar o crear sus propias entidades personalizadas para almacenar datos. 

## <a name="use-web-services-to-work-with-data"></a>Usar servicios web para trabajar con datos

Common Data Service proporciona dos servicios web que puede usar para interactuar con datos: **API web** y **servicio de la organización**. Elija el que coincida mejor con los requisitos y sus cualificaciones. 

![Organigrama para elegir servicio web](media/whentousewebapi.png)

### <a name="web-api"></a>API web

La API web es un extremo RESTful de OData v4. Use esto para cualquier lenguaje de programación que admita solicitudes HTTP y la autenticación mediante OAuth 2.0.

Más información: [Usar acciones web API de Common Data Service](webapi/overview.md). 

### <a name="organization-service"></a>Servicio de la organización

Use los ensamblados de SDK de .NET Framework para proyectos que impliquen la escritura de complementos o extensiones de flujo de trabajo. 

Más información: [Usar el servicio de organización de Common Data Service](org-service/overview.md)

> [!NOTE]
> Utilice ensamblados de Xrm.Tooling si está creando aplicaciones cliente para Windows. Más información: [Crear aplicaciones cliente de Windows mediante las herramientas XRM](xrm-tooling/build-windows-client-applications-xrm-tools.md)
