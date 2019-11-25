---
title: Configurar la integración de Azure (Common Data Service) | Microsoft Docs
description: El tema describe la configuración de la integración de Azure con Common Data Service.
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
ms.openlocfilehash: b030ca4e60d9f51f53706d682146c9acd46d5aa0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749726"
---
# <a name="configure-azure-integration-with-common-data-service"></a>Configurar la integración de Azure con Common Data Service

Puede publicar los datos de solicitud del mensaje de la operación principal actual en aplicaciones hospedadas en la nube que escuchan Azure Service Bus. Para habilitar esta capacidad en Common Data Service, realice las tareas que se detallan en este tema.

## <a name="configure-azure-for-common-data-service-integration"></a>Configurar Azure para la integración de Common Data Service

Como va a usar SAS para la autorización, debe configurar las reglas y los emisores de su solución de Azure para permitir que una aplicación de escucha lea el mensaje de Common Data Service publicado en Azure Service Bus. Además, debe configurar las reglas de bus de servicio para aceptar la notificación del emisor de Common Data Service. El método recomendado para configurar Azure es usar la herramienta de registro de complementos (PRT).

Para las instrucciones de configuración de la autorización, consulte [Tutorial: Configurar Azure (SAS) para su integración con Common Data Service](walkthrough-configure-azure-sas-integration.md).

## <a name="test-configuration"></a>Configuración de pruebas

Después de configurar la integración de Azure, deberá realizar estas tareas adicionales.

1. Escriba y registre una aplicación de escucha con un extremo de soluciones de Azure Service Bus. Para obtener más información, consulte la [Documentación de Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).
1. Registre un complemento basado en Azure o una actividad de flujo de trabajo personalizada basada en Azure con Common Data Service. Más información: [Tutorial: registrar un complemento basado en Azure con la herramienta de registro de complementos](walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool.md).
1. Realice la operación necesaria de Common Data Service que desencadena la ejecución del complemento o de la actividad de flujo de trabajo personalizada.

Si todos los pasos anteriores se realizaron correctamente, se debe enviar un mensaje que contiene el contexto de datos de Common Data Service a una cola o tema de Azure y que finalmente lo recibirá la aplicación de escucha. Puede navegar a la cuadrícula Trabajos del sistema en la aplicación web de Common Data Service y comprobar el estado del trabajo del sistema relacionado para ver si la publicación en Azure Service Bus se realizó correctamente. Si hay errores, la sección de mensaje de trabajo del sistema muestra los detalles del error.

### <a name="see-also"></a>Vea también

[Integración de Azure](azure-integration.md)<br />
[Use complementos para ampliar los procesos de negocio](plug-ins.md)<br />
[Trabajar con datos de Common Data Service en la solución de Azure](work-data-azure-solution.md)<br />
[Escriba una aplicación de escucha para una solución de Azure](write-listener-application-azure-solution.md)<br />
[¿Qué es Azure Service Bus?](/azure/service-bus-messaging/service-bus-messaging-overview)