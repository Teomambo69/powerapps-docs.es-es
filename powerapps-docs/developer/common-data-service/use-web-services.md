---
title: Uso de servicios web de Common Data Service for Apps | Microsoft Docs
description: Obtenga información sobre cómo los desarrolladores pueden usar servicios web de Common Data Service for App.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/26/2018
ms.author: jdaly
ms.openlocfilehash: 7f89a74b37ebf322137d680e165c007cd8fa6d26
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="use-common-data-service-for-apps-web-services"></a>Uso de servicios web de Common Data Service for Apps

Common Data Service for App proporciona dos servicios web que se pueden usar para interactuar con los datos. Elija el que mejor coincida con el requisito y sus habilidades. Más información: [Elegir su estilo de desarrollo para Dynamics 365 Customer Engagement (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/choose-development-style).

## <a name="web-api"></a>API web
La API web es un punto de conexión RESTful de OData v4. Úsela para cualquier lenguaje de programación que admita solicitudes HTTP y autenticación mediante OAuth 2.0.

Más información: [Utilizar la API web de Dynamics 365 Customer Engagement (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api).

## <a name="organization-service"></a>Servicio de organización

El servicio de organización es una parte fundamental de la plataforma Common Data Service for Apps. Es un servicio de Windows Communication Foundation (WCF) y actualmente solo expone un punto de conexión SOAP. Los desarrolladores de .NET pueden usar los ensamblados del SDK para realizar operaciones de datos. En un complemento, el servicio de organización a través de los ensamblados del SDK es la única opción.
> [!NOTE]
> Los desarrolladores pueden usar el punto de conexión SOAP del servicio de organización sin usar los ensamblados del SDK de .NET, pero la naturaleza RESTful de la API web la convierte en una alternativa muy superior.

Más información: [Usar el Servicio de la organización de Dynamics 365 (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service)

## <a name="about-the-web-services-and-the-platform"></a>Acerca de los servicios web y la plataforma

Es útil reconocer que el servicio de organización es lo que define la plataforma. La API web proporciona una experiencia de programación de RESTful pero, en última instancia, todas las operaciones de datos pasan a través del servicio de organización subyacente. 

El servicio de organización define las operaciones admitidas como mensajes. Cada mensaje tiene un nombre. En los ensamblados del SDK, cada mensaje tiene un *&lt;nombre de mensaje&gt;*`Request` y una clase *&lt;nombre de mensaje&gt;*`Response` correspondientes. En la [interfaz IOrganizationService](/dotnet/api/microsoft.xrm.sdk.iorganizationservice) de `Microsoft.Xrm.Sdk.dll` se definen varios métodos auxiliares para operaciones CRUD comunes, así como un [método Execute](/dotnet/api/microsoft.xrm.sdk.iorganizationservice.execute) que se puede usar para invocar los mensajes. Todos los mensajes usan la [clase OrganizationRequest](/dotnet/api/microsoft.xrm.sdk.organizationrequest) subyacente.

La API web proporciona las mismas operaciones que el servicio de organización pero las presenta en un estilo de RESTful mediante el protocolo OData v4. OData v4 proporciona operaciones con nombre mediante *funciones* o *acciones*. Casi todos los mensajes disponibles en el servicio de organización se exponen como una función o acción con nombre correspondiente. Los mensajes que corresponden a las operaciones CRUD no están disponibles en la API web porque, como servicio RESTful, tienen implementaciones que usan los métodos GET, POST, PATCH y DELETE de HTTP.

Los ensamblados del SDK de .NET para el punto de conexión SOAP del servicio de organización se diseñaron para crear modelos muy similares a los servicios de plataforma subyacentes en función de la [interfaz IOrganizationService ](/dotnet/api/microsoft.xrm.sdk.iorganizationservice). Pero no son los mismos componentes y no deben confundirse entre ellos. 

El punto de conexión SOAP para el servicio de organización se introdujo en 2011 y hemos anunciado que está en desuso. Esto significa que seguirá funcionando y se admitirá hasta que se elimine. También hemos anunciado que se actualizarán los ensamblados del SDK de .NET para que sigan funcionando después de que se elimine el punto de conexión SOAP. Esto significa que habrá ensamblados del SDK actualizados disponibles antes de que se elimine el punto de conexión SOAP y que los desarrolladores tendrán que actualizar el código para usar estos ensamblados nuevos en algún momento en el futuro.

## <a name="discovery-services"></a>Servicios de detección

Todos los usuarios de Common Data Service for Apps pueden tener acceso a varias instancias de Common Data Service for Apps. Los servicios de detección permiten escribir código para proporcionar a los usuarios una lista de las instancias a las que se pueden conectar en función de la cuenta Microsoft que usen. Cada instancia incluye una dirección URL que después pueden usar para conectarse a la instancia que elijan. 

Se tiene acceso a un servicio de detección a través de la API web o el servicio de organización.

- Para la API web, vea: [Descubrir la dirección URL para la organización utilizando la API web (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)
- Para el servicio de organización, vea: [Descubrir la dirección URL para la organización utilizando el servicio de la organización (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)

## <a name="use-custom-actions"></a>Usar acciones personalizadas

Una de las opciones declarativas disponibles para los procesos consiste en crear una *acción personalizada*. Básicamente, una acción personalizada crea un mensaje en el servicio de organización. Las acciones personalizadas se pueden usar para combinar un conjunto de operaciones en una operación reutilizable con nombre. Por ejemplo, es posible crear un mensaje denominado *new_Escalate* que combine un conjunto estándar de operaciones que intervienen en la notificación a los usuarios adecuados cuando un cliente importante está experimentando un problema grave.

Cuando se define una acción personalizada, se elige la firma de la operación mediante la definición de los parámetros de entrada y las propiedades que se van a incluir en los resultados que se devuelven. Después, las acciones personalizadas se pueden invocar desde un proceso declarativo mediante el diseñador o mediante código. 

El valor único de las acciones personalizadas es que las operaciones específicas que contienen pueden modificarse por alguien que no sea un desarrollador y que use el diseñador sin afectar a otros procesos o al código que lo llama.  Esto es así si la firma de la acción no cambia. Si se necesitan otros parámetros de entrada o propiedades de salida, se debe crear otra acción personalizada para evitar la interrupción de los procesos o el código que use una ya existente.

Cuando se define una acción personalizada en un entorno, una nueva acción de OData v4 está disponible mediante la API web y, en el servicio de organización, la acción personalizada se puede invocar directamente con la [clase OrganizationRequest](/dotnet/api/microsoft.xrm.sdk.organizationrequest) o con una clase fuertemente tipada generada mediante la *herramienta de generación de código (CrmSvcUtil.exe)*.

Más información: 
- [Información general sobre las acciones (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/actions)
- [Crear acciones propias (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/create-own-actions)
- [Usar acciones de la API web (Guía para desarrolladores de Dynamics 365 Customer Engagement) > Usar una acción personalizada](/dynamics365/customer-engagement/developer/webapi/use-web-api-actions#use-a-custom-action)

## <a name="metadata-services"></a>Servicios de metadatos

La API web y el servicio de organización incluyen funciones para realizar operaciones CRUD en el esquema de la entidad. Aunque estas operaciones se pueden realizar mediante código, generalmente se usarán diseñadores para agregar, actualizar o eliminar elementos de esquema personalizados. Los usuarios deben tener privilegios de administrador para aplicar cambios de esquema, pero todos los usuarios pueden leer los metadatos.

Un uso más común de los servicios de metadatos es para recuperar metadatos sobre el entorno en el que se está ejecutando la extensión. Dado que todos los entornos pueden ser diferentes y los metadatos de esquema contienen gran parte de la información sobre cómo esté configurado el entorno, es posible que se necesite recuperar esta información para permitir que las extensiones se adapten a otras personalizaciones que están en vigor en ese entorno.

Algunos ejemplos:
- Se puede cambiar el número de opciones disponibles en un atributo optionset. En lugar de integrar los valores como parte del código en el entorno, tenga en cuenta si existen otras opciones. Se puede consultar el sistema para determinar si el entorno actual tiene otras opciones.
- Se puede cambiar el nombre para mostrar de una entidad. El nombre para mostrar predeterminado para la entidad de cuenta es *Account*. Esto se podría cambiar a *Company*. Si se quiere mostrar un mensaje a un usuario y hacer referencia al nombre de una entidad, esto no se debe integrar como parte del código sino usar en su lugar el valor que coincida con lo que el usuario está acostumbrado a ver y el nombre para mostrar recuperado de los metadatos de entidad.

Desarrollar un entendimiento funcional correcto de los metadatos del sistema puede ayudar a entender cómo funciona la plataforma Common Data Service for Apps. En los diseñadores disponibles para modificar los metadatos no se pueden mostrar todos los detalles encontrados en los metadatos. Se puede instalar una aplicación controlada por modelos denominada *Explorador de metadatos* que permite ver todas las entidades ocultas y las propiedades de metadatos que se encuentran en el sistema. 

Más información: [Exploración de los metadatos de su organización (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/browse-your-metadata)

Para obtener más información sobre cómo trabajar con metadatos mediante programación, vea:
- [Utilizar la API web con metadatos (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/webapi/use-web-api-metadata)
- [Usar el servicio de la organización con metadatos de Dynamics 365 (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)
 
### <a name="see-also"></a>Vea también

[Common Data Service for Apps Developer Overview](overview.md) (Introducción para desarrolladores de Common Data Service for Apps)

