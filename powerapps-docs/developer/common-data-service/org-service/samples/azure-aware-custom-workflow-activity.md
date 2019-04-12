---
title: Actividad de flujo de trabajo personalizada compatible con Azure (Common Data Service) | Microsoft Docs
description: Este ejemplo obtiene el contexto de datos de la operación de Dynamics 365 Customer Engagement actual y lo publica en Azure Service Bus.
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
# <a name="sample-azure-aware-custom-workflow-activity"></a>Ejemplo: actividad personalizada de flujo de trabajo basada en Azure

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity -->

Este ejemplo obtiene el contexto de datos de la operación actual y lo publica en Azure Service Bus. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Azurecustomworkflowactivity).

## <a name="requirements"></a>Requisitos

Debe configurar Common Data Service para conectarse con Azure antes de registrar y ejecutar este ejemplo de actividad de flujo de trabajo personalizado. Más información: [Configurar la integración de Microsoft Azure con Common Data Service](../../configure-azure-integration.md).

Tenga en cuenta el argumento de `Input id` requerido en el código. Cuando agregue esta actividad a un flujo de trabajo, debe proporcionar el GUID de un extremo de servicio de Azure.

Al registrar esta actividad de flujo de trabajo personalizada con Common Data Service, debe registrarla en el espacio aislado (confianza parcial).

## <a name="how-to-run-samples"></a>Cómo ejecutar ejemplos

1. Descargar o clonar el informe de [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local.
2. Registrar la actividad de flujo de trabajo.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo escribir una actividad de flujo de trabajo personalizada que puede publicar el contexto de datos de la operación actual de Common Data Service a Azure Service Bus. La publicación del contexto de datos se realiza a través del método de <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService.Execute(Microsoft.Xrm.Sdk.EntityReference,Microsoft.Xrm.Sdk.IExecutionContext)>.
