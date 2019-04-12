---
title: Usar el servicio de la organización Common Data Service (Common Data Service) | Microsoft Docs
description: Lea cómo puede usar el servicio de organización de Common Data Service para trabajar con datos y metadatos.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-the-common-data-service-organization-service"></a>Usar el servicio de organización de Common Data Service

El servicio de organización es uno de dos servicios web que puede usar para trabajar con datos y metadatos en Common Data Service. El otro es la [API web](../webapi/overview.md).

El servicio de organización está optimizado para su uso con .NET Framework y los ensamblados de SDK del paquete de NuGet [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/) proporcionan las clases para la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService> necesarias para trabajar con datos y metadatos mediante este servicio. 

Algunas funciones de extensión, como los complementos y las extensiones de flujo de trabajo, dependen de .NET Framework y de las clases definidas en estos ensamblados, por lo que el servicio de organización es la única opción al usar estos métodos para ampliar Common Data Service.

## <a name="organization-service-assemblies"></a>Ensamblados del servicio de organización

Es útil reconocer que el servicio de organización es lo que define la plataforma. El servicio de organización define las operaciones admitidas como mensajes. Cada mensaje tiene un nombre. Estos mensajes corresponden a los eventos emitidos por el marco de trabajo de eventos. Más información: [Marco de trabajo de eventos](../event-framework.md)

Los ensamblados de .NET para el servicio de organización usan actualmente un extremo de SOAP. Los ensamblados se diseñaron de forma que estuvieran estrechamente relacionados con los servicios de plataforma subyacentes basados en la interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Sin embargo, no son los mismos componentes y no se deben confundir. 

El extremo de SOAP para el servicio de organización se introdujo en 2011 y hemos anunciado que está en desuso. Esto significa que seguirá funcionando y recibiendo soporte hasta que lo quitemos. También hemos anunciado que actualizaremos los ensamblados del SDK de .NET de modo que sigan funcionando cuando hayamos quitado el extremo de SOAP. Esto significa que estarán disponibles ensamblados del SDK actualizados antes de que se quite el extremo de SOAP y que en el futuro se pedirá a los desarrolladores que actualicen el código para usar estos nuevos ensamblados.

## <a name="using-the-organization-service-without-assemblies"></a>Usar el servicio de organización sin ensamblados

Los desarrolladores pueden usar el extremo de SOAP del servicio de organización sin usar los ensamblados del SDK de .NET, creando (por ejemplo) un proxy de servicio web mediante el WSDL expuesto por el servicio, pero la naturaleza RESTful de la API web la convierte en una alternativa superior.
