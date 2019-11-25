---
title: 'Tutorial: Configurar Microsoft Azure (SAS) para integración (Common Data Service) | Microsoft Docs'
description: El tutorial le guiará por el proceso de configuración del emisor de Azure Service Bus, el ámbito y las reglas para permitir que una aplicación de escucha lea los mensajes de Common Data Service para aplicaciones registrados en Azure Service Bus.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: d7b24b11-57f0-ab05-4bec-0b64efee178d
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a6d6e12e07174d67afc3fa1461767eca284c0015
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749654"
---
# <a name="tutorial-configure-azure-sas-for-integration-with-common-data-service"></a>Tutorial: Configurar Azure (SAS) para integración con Common Data Service

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/walkthrough-configure-azure-sas-integration -->

Este tutorial le guiará por el proceso de configuración del emisor de Azure Service Bus, el ámbito y las reglas para permitir que una aplicación de escucha lea los mensajes de Common Data Service para aplicaciones registrados en Azure Service Bus.  
  
> [!NOTE]
>  Este tutorial se aplica a cualquier implementación de Common Data Service cuando se usa autorización SAS para mensajería de Azure. Para obtener más información sobre la autorización de Azure Service Bus, consulte [Autenticación y autorización de Service Bus](https://azure.microsoft.com/documentation/articles/service-bus-authentication-and-authorization/).  
>   
> Debe usar la herramienta de registro de complementos. Para descargar la herramienta de registro de complementos, consulte [Descargar herramientas de NuGet](download-tools-NuGet.md).
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Una cuenta de Azure con una licencia para crear entidades de bus de servicio.
  
-   Un espacio de nombres de bus de servicio configurado por SAS.
  
-   Una entidad de mensajería de bus de servicio configurada por SAS: cola, tema, retransmisión, o centro de eventos.
  
-   La entidad de mensajería debe tener el permiso de directiva `Send` como mínimo. Para un retransmisión bidireccional, la directiva también debe tener el permiso `Listen`.  
-  La cadena de conexión de autorización de la entidad de mensajería. 
  
 ![Definir permisos de directiva de Azure](media/policy-permissions.png "Definir permisos de directiva de Azure")  
  
 Consulte [Crear un bus de servicio espacio de nombres mediante el portal Azure](/azure/service-bus-messaging/service-bus-create-namespace-portal) para obtener instrucciones sobre cómo crear una entidad de espacio de nombres y mensajería de bus de servicio.  
  
## <a name="create-a-service-endpoint"></a>Crear un extremo de servicio

Una [entidad ServiceEndpoint](reference/entities/serviceendpoint.md) contiene datos de configuración que son necesarios para mensajería externa con un extremo de soluciones de Azure Service Bus. Utilizando la herramienta de registro de complementos, puede crear fácilmente una entidad de extremo de servicio en una organización de Common Data Service y configurar el emisor, el ámbito, y las reglas del extremo de bus de servicio.
  
### <a name="register-a-service-endpoint"></a>Registrar un extremo de servicio  
  
1.  Ejecute la herramienta de registro de complementos e inicie sesión en la organización de Common Data Service de destino.  
  
2.  Seleccione **Registrar > Registrar nuevo extremo de servicio**.  
  
3.  Active **Comencemos con la cadena de conexión del portal de bus de servicio de Azure** y pegue la cadena de conexión de la entidad de mensajería de bus de servicio.  
  
 ![Proporcionar cadena de conexión de autorización](media/sas-connection-string.PNG "Proporcionar cadena de conexión de autorización")  
  
4.  Seleccione **Siguiente**.  
  
5.  Cumplimente el formulario **Registro de extremo de servicio** escribiendo los campos **Tipo de designación**, **Formato de mensaje** y, opcionalmente, **Información del usuario enviada** y **Descripción**  
  
 ![Registro del extremo de servicio](media/service-endpoint-registration.PNG "Registro del extremo de servicio")  
  
   Para obtener más información acerca del formato del mensaje, consulte [Escribir un aplicación de agente de escucha para una solución de Azure](write-listener-application-azure-solution.md).  
  
6.  Seleccione **Guardar**.  
  
7.  Después de unos segundos, verá el nuevo extremo de servicio en el lista **Complementos registrados y actividades personalizadas del flujo de trabajo**.  
  
 ![Nuevo extremo de servicio](media/new-service-endpoint.PNG "Nuevo extremo de servicio")  
  
### <a name="see-also"></a>Vea también

[Integración de Azure](azure-integration.md)<br />
[Azure Service Bus](/azure/service-bus-messaging/service-bus-fundamentals-hybrid-solutions.md)
