---
title: Trabajar con datos de Dynamics 365 en la solución de Azure (Common Data Service para aplicaciones) | Microsoft Docs
description: El pluggin ServeceBusPlugin contiene la lógica de negocios para registrar el contexto del mensaje de ejecución de Dynamics 365 al Azure Service Bus. Para utilizar este pluggin necesita registrar un punto final de la solución Azure Servic Bus y un paso para el pluggin. El paso define qué combinación de mensaje y entidad procesada por el núcleo de la operación Dynamisc 365 debe activar el pluggin para ejecutarse. El  Service Bus Plugin solo puede registrarse para ejecutarse asincrónicamente.
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 1ef66369-71c9-3b89-ac1a-09d523ca737b
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="work-with-common-data-service-for-apps-data-in-your-azure-solution"></a>Trabajar con datos de Common Data Service para aplicaciones en la solución de Azure

Un complemento interno denominado ServiceBusPlugin se proporciona con Common Data Service para aplicaciones de Dynamics 365 (online). El complemento contiene la lógica de negocios para registrar el contexto de ejecución de mensaje de Dynamics 365 al Azure Service Bus. Para utilizar este pluggin necesita registrar un punto final de la solución Azure Servic Bus y un paso para el pluggin. El paso define qué combinación de mensaje y entidad procesada por el núcleo de la operación Dynamisc 365 debe activar el pluggin para ejecutarse. El  Service Bus Plugin solo puede registrarse para ejecutarse asincrónicamente. Para obtener más información sobre cómo usar la herramienta, consulte [Tutorial: registro de un pluggin en Azure-aware con la herramienta de registro de pluggins](walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool.md).  
  
 Además, puede escribir un complemento personalizado que incluya las líneas de código necesarias para registrar en el bus de servicio. El complemento se registra de una forma similar, pero debe estar registrado en el espacio aislado y se ejecuta en confianza parcial. Para obtener más información sobre cómo escribir un complemento personalizado que puede publicar en el Azure Service Bus, consulte [Escribir un complemento personalizado con Azure](write-custom-azure-aware-plugin.md).  
  
 También puede escribir una actividad personalizada de flujo de trabajo que pueda registrar el contexto de la ejecución en el bus de servicio e incluir esta actividad en los flujos de trabajo. El código de ejemplo para una actividad de flujo de trabajo personalizado con Azure se proporciona en el tema [Ejemplo: Actividad de flujo de trabajo personalizado con Azure](/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity) 
  
### <a name="see-also"></a>Vea también  
[Escribir un complemento](write-plug-in.md)<br/>
[Canalización de ejecución del evento](event-framework.md#event-execution-pipeline)<br/> 
[Entidad ServiceEndpoint](reference/entities/serviceendpoint.md)<br/>