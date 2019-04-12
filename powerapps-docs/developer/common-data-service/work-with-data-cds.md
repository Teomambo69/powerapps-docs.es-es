---
title: Trabajar con datos usando código en Common Data Service (PowerApps) | Microsoft Docs
description: 'Common Data Service proporciona dos servicios web que puede usar para interactuar con datos: API web y servicio de la organización.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
# <a name="work-with-data-using-code-in-common-data-service"></a>Trabajar con datos usando código en Common Data Service

Common Data Service tiene [entidades](entities.md) que se usan para modelar y administrar datos profesionales. Puede usar entidades estándar o crear sus propias entidades personalizadas para almacenar datos. 

## <a name="use-web-services-to-work-with-data"></a>Usar servicios web para trabajar con datos

Common Data Service proporciona dos servicios web que puede usar para interactuar con datos: **API web** y **servicio de la organización**. Elija el que coincida mejor con los requisitos y sus cualificaciones. 

![Organigrama para elegir servicio web](media/whentousewebapi.png)

### <a name="web-api"></a>API web

La API web es un extremo RESTful de OData v4. Use esto para cualquier lenguaje de programación que admita solicitudes HTTP y la autenticación mediante OAuth 2.0.

Más información: [Usar la API web de Common Data Service](webapi/overview.md) 

### <a name="organization-service"></a>Servicio de la organización

Use los ensamblados de SDK de .NET Framework para proyectos que impliquen la escritura de complementos o extensiones de flujo de trabajo. 

Más información: [Usar el servicio de la organización de Common Data Service](org-service/overview.md)

> [!NOTE]
> Utilice ensamblados de Xrm.Tooling si está creando aplicaciones cliente para Windows. Más información: [Crear aplicaciones cliente de Windows mediante las herramientas XRM](xrm-tooling/build-windows-client-applications-xrm-tools.md)
