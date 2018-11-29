---
title: 'Desarrolladores: Introducción a Common Data Service para aplicaciones | Microsoft Docs'
description: Descubra cómo los desarrolladores pueden agregar valor mediante Common Data Service para aplicaciones en PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="developers-get-started-with-common-data-service-for-apps"></a>Desarrolladores: Introducción a Common Data Service para aplicaciones

Hay muchos aspectos referentes a cómo los desarrolladores pueden contribuir a crear aplicaciones que usan Common Data Service (CDS) para aplicaciones. Aunque sea posible crear una aplicación con un código mediante CDS para aplicaciones como el origen de datos, la mayoría de los proyectos utilizarán aplicaciones basadas en modelos o aplicaciones de lienzo para generar la experiencia que usan las personas. 

## <a name="working-with-model-driven-apps"></a>Trabajar con aplicaciones basadas en modelos

Las aplicaciones basadas en modelos se crean mediante CDS for Apps. Una aplicación basada en modelos solo puede conectarse al entorno de CDS for Apps y todos los datos que definen una aplicación basada en modelos se almacenan en de CDS for Apps.

Las aplicaciones basadas en modelos comparten el método de distribución de personalizaciones y extensiones que usa CDS for Apps: soluciones. Puede obtener más información acerca de soluciones en [Introducción a soluciones](introduction-solutions.md)

Las aplicaciones basadas en modelos también tienen varios puntos para que los desarrolladores escriban código para ampliar. Para obtener información sobre lo que pueden hacer los desarrolladores con las aplicaciones basadas en modelos, consulte [Información general para desarrolladores sobre aplicaciones basadas en modelos](../model-driven-apps/overview.md)

## <a name="understand-when-to-write-code"></a>Comprender cuándo hay que escribir código

Dado que CDS for Apps incluye muchas funcionalidades para que los usuarios configuren la lógica empresarial personalizada sin escribir código, los escenarios más comunes para que los desarrolladores contribuyan tienen que ver con rellenar espacios donde puede que las características existentes no proporcionen la funcionalidad que necesita para cumplir requisitos. Afortunadamente, CDS for Apps proporciona muchos puntos para que los desarrolladores amplíen la funcionalidad común con código.

Para un desarrollador que ayude en proyectos es importante entender lo que se puede hacer sin necesidad de escribir código. Debe familiarizarse con estas funcionalidades. Más información: [Qué es Common Data Service para aplicaciones](../../maker/common-data-service/data-platform-intro.md)

## <a name="where-to-begin"></a>¿Dónde empezar?

Donde comenzar depende de los problemas que intenta solucionar. Este manual incluye contenido sobre una gran variedad de funcionalidades y no es probable que las use todas. A continuación se incluye varios ámbitos fundamentales para comenzar.

> [Trabajar con datos utilizando servicios web](#work-with-data-using-web-services)<br/>
> [Aplicar la lógica de negocios](#applying-business-logic)<br/>
> [Entidades de CDS for Apps](#cds-for-apps-entities)<br/>
> [Trabajar con metadatos](#work-with-metadata)<br/>
> [Usar soluciones para empaquetar y distribuir las extensiones](#use-solutions-to-package-and-distribute-extensions)<br/>
> [Crear aplicaciones cliente y autenticación](#create-client-applications-and-authentication)<br/>
> [Contenido para implementaciones locales](#content-for-on-premises-deployments)<br/>

### <a name="work-with-data-using-web-services"></a>Trabajar con datos utilizando servicios web

Hay dos servicios web diferentes que puede usar para trabajar con datos. El que debe usar depende del tipo del proyecto en el que trabaje. Más información: [Trabajar con datos mediante código](work-with-data-cds.md).

### <a name="applying-business-logic"></a>Aplicar la lógica de negocios

Las extensiones más comunes creadas mediante código incluyen la automatización de los procesos que se usan en los negocios. Puede encontrar un resumen de las opciones disponibles en [Aplicar la lógica de negocios con código](apply-business-logic-with-code.md). Cada una de estos enfoques se invocan normalmente basándose en eventos que aparecen en el servidor, por tanto entender el [Marco de trabajo de eventos](event-framework.md) es importante.

### <a name="cds-for-apps-entities"></a>Entidades de CDS for Apps

Las entidades almacenan datos empresariales con los que trabajará. Es esencial entender lo que son y cómo trabajar con ellas.
Más información:

- [Entidades de Common Data Service para aplicaciones](entities.md)
- [Acerca de la referencia de entidades](reference/about-entity-reference.md)

### <a name="work-with-metadata"></a>Trabajar con metadatos

Desarrollar una buena comprensión de los metadatos en el sistema le pueden ayudar a entender cómo funciona la plataforma de CDS for Apps. Usará normalmente diseñadores para agregar, actualizar o eliminar el esquema de la entidad que define los metadatos, pero la API web y los servicios web del servicio de la organización proporciona funcionalidades para realizar operaciones CRUD en el esquema de la entidad. Más información: [Trabajar con metadatos mediante código](metadata-services.md). 

### <a name="use-solutions-to-package-and-distribute-extensions"></a>Usar soluciones para empaquetar y distribuir las extensiones

Si va a distribuir extensiones creadas o cualquier personalización de la que dependan, deberá comprender las soluciones. Las soluciones creadas por un usuario son relativamente sencillas de usar y no requieren los conocimientos de un desarrollador. Pero para que un equipo de desarrolladores de sea productivo con soluciones y use los principios de administración del ciclo de vida eficaces de la aplicación requiere un enfoque más avanzado. Más información:

 - [Introducción a soluciones](introduction-solutions.md)
 - [Herramienta SolutionPackager toolSolutionPackager](compress-extract-solution-file-solutionpackager.md)
 - [Herramienta Package Deployer](./package-deployer/create-packages-package-deployer.md)
 - [Publicar la aplicación en AppSource](publish-app-appsource.md)

### <a name="create-client-applications-and-authentication"></a>Crear aplicaciones cliente y autenticación

Al crear las extensiones que se aplican a la lógica empresarial en el servidor no necesitará incluir código para la autenticación. Las únicas veces que deberá autenticar es cuando esté creando una aplicación cliente. Una aplicación cliente sencilla de la consola es una buena manera de familiarizarse con las API de CDS for Apps. Habilitar una forma de conectarse a los datos es un importante paso. La mayoría de los códigos de ejemplo proporcionados incluyen medios para autenticarse. El conector Xrm.Tooling ofrece funcionalidades para simplificar la autenticación. Más información:

- [Autenticación](authentication.md)
- [Crear aplicaciones cliente](connect-cds.md)
- [Tutorial: Crear una aplicación de la consola con el servicio de la organización](org-service/quick-start-org-service-console-app.md)
- [Tutorial: Ejemplo de API Web (C#)](webapi/quick-start-console-app-csharp.md)
- [Ejemplo: inicio rápido para la API de útiles de XMR](xrm-tooling/sample-quick-start-xrm-tooling-api.md)

## <a name="content-for-on-premises-deployments"></a>Contenido para implementaciones locales

CDS for Apps no está disponible para las implementaciones locales en estos momentos. El contenido de este manual no incluye información sobre las opciones que solo están disponibles para implementaciones local o implementaciones con conexión a Internet (IFD). Para obtener más información relacionada con estas opciones, consulte [Kit de desarrollo de software para Microsoft Dynamics 365 (online) y Dynamics 365 (on-premises)](https://msdn.microsoft.com/library/hh547453.aspx).