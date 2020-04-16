---
title: Trabajar con datos de Dynamics 365 en la solución de Azure(Common Data Service) | Microsoft Docs
description: El pluggin ServeceBusPlugin contiene la lógica de negocios para registrar el contexto del mensaje de ejecución de Dynamics 365 al Azure Service Bus. Para utilizar este pluggin necesita registrar un punto final de la solución Azure Servic Bus y un paso para el pluggin. El paso define qué combinación de mensaje y entidad procesada por el núcleo de la operación Dynamisc 365 debe activar el pluggin para ejecutarse. El  Service Bus Plugin solo puede registrarse para ejecutarse asincrónicamente.
keywords: ''
ms.date: 06/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 1ef66369-71c9-3b89-ac1a-09d523ca737b
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5c1a5660f8befdbbbb19cc81003ead880903b384
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154972"
---
# <a name="work-with-common-data-service-data-in-your-azure-solution"></a>Trabajar con datos de Common Data Service en la solución de Azure

Se proporciona un complemento interno llamado `ServiceBusPlugin` con Common Data Service (CDS). El complemento contiene la lógica de negocios para registrar el contexto de ejecución de mensaje de CDS al Azure Service Bus. Para utilizar este pluggin necesita registrar un punto final de la solución Azure Servic Bus y un paso para el pluggin. El paso define qué combinación de mensaje y entidad procesada por la operación de CDS básica debe activar el complemento para ejecutarse. El `ServiceBusPlugin` solo puede registrarse para ejecutarse asincrónicamente. Para obtener más información sobre cómo usar la herramienta, consulte [Tutorial: registro de un pluggin en Azure-aware con la herramienta de registro de pluggins](walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool.md).  
  
 Además, puede escribir un complemento personalizado que incluya las líneas de código necesarias para registrar en el bus de servicio. El complemento se registra de una forma similar, pero debe estar registrado en el espacio aislado y se ejecuta en confianza parcial. Para obtener más información sobre cómo escribir un complemento personalizado que puede publicar en el Azure Service Bus, consulte [Escribir un complemento personalizado con Azure](write-custom-azure-aware-plugin.md).  
  
 También puede escribir una actividad personalizada de flujo de trabajo que pueda registrar el contexto de la ejecución en el bus de servicio e incluir esta actividad en los flujos de trabajo. El código de ejemplo para una actividad de flujo de trabajo personalizado con Azure se proporciona en el tema [Ejemplo: Actividad de flujo de trabajo personalizado con Azure](/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity) 
  
### <a name="see-also"></a>Vea también  
[Escribir un complemento](write-plug-in.md)<br/>
[Canalización de ejecución del evento](event-framework.md#event-execution-pipeline)<br/> 
[Entidad ServiceEndpoint](reference/entities/serviceendpoint.md)<br/>