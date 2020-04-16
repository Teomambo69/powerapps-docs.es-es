---
title: 'Desarrolladores: Introducción a Common Data Service | Microsoft Docs'
description: Descubra cómo los desarrolladores pueden agregar valor mediante Common Data Service en Power Apps.
suite: powerapps
author: JimDaly
manager: ryjones
ms.service: powerapps
ms.date: 08/05/2019
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bfc3415d95e8861cdd2ba4c4835e453c0ddc2720
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156192"
---
# <a name="developers-get-started-with-common-data-service"></a>Desarrolladores: Introducción a Common Data Service

Dónde comenzar depende de los problemas que intenta solucionar. Este manual incluye información sobre una gran variedad de funcionalidades y no es probable que las use todas. Las siguientes secciones incluyen varios ámbitos fundamentales para comenzar.

## <a name="work-with-data-using-web-services"></a>Trabajar con datos utilizando servicios web

Hay dos servicios web distintos que puede usar para trabajar con datos: **API web** y **servicio de la organización**. 

El que debe usar depende del tipo del proyecto en el que trabaje. Más información: [Trabajar con datos mediante código](work-with-data-cds.md).

## <a name="applying-business-logic"></a>Aplicar la lógica de negocios

Las extensiones más comunes creadas mediante código incluyen la automatización de los procesos que se usan en los negocios. Puede encontrar un resumen de las opciones disponibles en [Aplicar la lógica de negocios con código](apply-business-logic-with-code.md). Cada una de estos enfoques se invocan normalmente basándose en eventos que aparecen en el servidor, por tanto entender el [Marco de trabajo de eventos](event-framework.md) es importante.

## <a name="integrate-with-external-data"></a>Integrar con datos externos

Las capacidades de administración de datos en Common Data Service no sólo le permiten trabajar con datos en Common Data Service, sino también interactuar con eficacia con datos externos críticos para su negocio. Más información: 

- [Importar datos](/powerapps/developer/common-data-service/import-data)
- [Sincronizar datos](/powerapps/developer/common-data-service/data-synchronization)
- [Entidades virtuales](/powerapps/developer/common-data-service/virtual-entities/get-started-ve)
- [Integración de Azure](/powerapps/developer/common-data-service/azure-integration)
- [Webhooks](/powerapps/developer/common-data-service/use-webhooks
)

## <a name="common-data-service-entities"></a>Entidades de Common Data Service

Las entidades almacenan datos empresariales con los que trabajará. Es esencial entender lo que son y cómo trabajar con ellas.
Más información:

- [Entidades de Common Data Service](entities.md)
- [Acerca de la referencia de entidades](reference/about-entity-reference.md)

## <a name="work-with-metadata"></a>Trabajar con metadatos

Desarrollar una buena comprensión de los metadatos en el sistema le pueden ayudar a entender cómo funciona la plataforma de Common Data Service. Usará normalmente diseñadores para agregar, actualizar o eliminar el esquema de la entidad que define los metadatos, pero la API web y los servicios web del servicio de la organización proporciona funcionalidades para realizar operaciones CRUD en el esquema de la entidad. Más información: [Trabajar con metadatos mediante código](metadata-services.md). 

## <a name="use-solutions-to-package-and-distribute-extensions"></a>Usar soluciones para empaquetar y distribuir las extensiones

Si va a distribuir extensiones creadas o cualquier personalización de la que dependan, deberá comprender las soluciones. Las soluciones creadas por un usuario son relativamente sencillas de usar y no requieren los conocimientos de un desarrollador. Pero para que un equipo de desarrolladores de sea productivo con soluciones y use los principios de administración del ciclo de vida eficaces de la aplicación requiere un enfoque más avanzado. Más información:

 - [Introducción a soluciones](introduction-solutions.md)
 - [Herramienta SolutionPackager](compress-extract-solution-file-solutionpackager.md)
 - [Herramienta Package Deployer](./package-deployer/create-packages-package-deployer.md)
 - [Publicar la aplicación en AppSource](publish-app-appsource.md)

## <a name="create-client-applications-and-authentication"></a>Crear aplicaciones cliente y autenticación

Al crear las extensiones que se aplican a la lógica empresarial en el servidor no necesitará incluir código para la autenticación. Las únicas veces que deberá autenticar es cuando esté [creando una aplicación cliente](/powerapps/developer/common-data-service/connect-cds). Una aplicación cliente sencilla de la consola es una buena manera de familiarizarse con las API de Common Data Service. Habilitar una forma de conectarse a los datos es un importante paso. La mayoría de los códigos de ejemplo proporcionados incluyen medios para autenticarse. El conector Xrm.Tooling ofrece funcionalidades para simplificar la autenticación. Más información:

- [Autenticación](authentication.md)
- [Crear aplicaciones web mediante autenticación de servidor a servidor (S2S)](/powerapps/developer/common-data-service/build-web-applications-server-server-s2s-authentication)
- [Crear aplicaciones cliente de Windows mediante herramientas XRM](/powerapps/developer/common-data-service/xrm-tooling/build-windows-client-applications-xrm-tools)
