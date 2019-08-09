---
title: Trabajar con datos de eventos de Dynamics 365 en la solución del Centro de eventos de Azure (Common Data Service) | Microsoft Docs
description: Trabajar con datos de eventos en la solución del Centro de eventos de Azure
keywords: ''
ms.date: 05/08/2019
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: a3732c49-7f47-d87c-5062-585ef28ab511
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: pehecke
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="work-with-common-data-service-event-data-in-your-azure-event-hub-solution"></a>Trabajar con datos de eventos de Common Data Service en la solución del Centro de eventos de Azure

Azure Event Hub es un servicio de publicación-suscripción muy escalable que puede ingerir millones de eventos por segundo y enviarlos a varias aplicaciones. La interfaz Common Data Service-Azure permite publicar datos de eventos en el Azure Service Bus y ponerlos a disposición de los suscriptores de la solución del centro de eventos. La siguiente información describe las tareas generales que se deben realizar para enviar datos de eventos de Azure a una solución del centro de eventos.  
  
> [!NOTE]
> Se necesitan una suscripción de Azure y una licencia del centro de eventos para el acceso a los centros de eventos.
  
## <a name="1-create-an-event-hub"></a>1. Crear un centro de eventos  
 Puede crear un centro de eventos en Azure mediante la API de programación o interactivamente usando el [portal clásico Azure](https://manage.windowsazure.com). En cualquier caso, después de crear su centro de eventos debe obtener una copia de la cadena de conexión del centro de eventos y proporcionar esa cadena al registrar el extremo de servicio de Azure detallado en la siguiente sección.  
  
 Para obtener más información sobre la creación centros de eventos consulte [Documentación de Event Hubs](https://azure.microsoft.com/documentation/services/event-hubs/).  
  
## <a name="2-register-an-endpoint"></a>2. Registrar un extremo  
 Registrar un extremo de servicio para un centro de eventos es similar a registrar cualquier otro tipo de contrato admitido como colas o temas. Use la herramienta de registro de complementos, proporcionada en la descarga del SDK, para registrar el extremo de servicio.  Al rellenar el formulario de registro especifique un tipo de contrato de **Centro de eventos**. Para el formato del cuerpo del mensaje, puede elegir **XML** o **JSON**. Además, sólo se permite autorización SAS y debe proporcionar la cadena de conexión obtenida cuando se creó el centro de eventos. Más información: [Tutorial: Configurar Microsoft Azure (SAS) para la integración con Common Data Service](walkthrough-configure-azure-sas-integration.md).  
  
## <a name="3-register-code"></a>3. Registrar código  
 Dynamics 365 necesita conocer la operación exacta (combinación de entidad/mensaje) que, cuando se procesan, hará que el complemento basado en Azure se ejecute. Puesto que está creando un centro de eventos, esta operación estaría relacionada con el procesamiento de datos de eventos de Azure en concreto. Debe registrar un paso para el complemento basado en Azure en la canalización de ejecución de eventos de Azure.  Para obtener más información sobre cómo usar la herramienta, consulte [Tutorial: registro de un complemento con Azure con la herramienta de registro de complementos](walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool.md).  
  
 Si usa una actividad de flujo de trabajo personalizada basada en Azure en lugar de un complemento, registre el ensamblado de la actividad con la herramienta de registro de complementos y incorpore esa actividad en un flujo de trabajo. Para obtener más información, consulte [Ejemplo: Actividad de flujo de trabajo personalizado con Azure](/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity).
  
## <a name="4-start-listening"></a>4. Empezar la escucha  
 Inicie la aplicación de la solución de centro de servicios Azure escuchando el extremo de servicio.  
  
## <a name="5-trigger"></a>5. Desencadenador  
 Realice una operación en Azure que haga que el complemento o el flujo de trabajo que contiene la actividad de flujo de trabajo personalizada se ejecute. Ésta es la misma operación (combinación de entidad/mensaje) para la que registró el paso de complemento de la sección anterior de este tema. Puede realizar la operación prevista con la aplicación web o del código de aplicación accediendo a los servicios web de Azure.  
  
## <a name="6-verification"></a>6. Comprobación  
 Puede comprobar el trabajo del sistema relacionado en la aplicación web de Azure y buscar un estado de **Correcto**. Si encuentra un estado de **Incorrecto**, use la información de estado para identificar la causa posible de errores. Puede volver a comprobar la configuración de ambos sistemas o depurar código de aplicación para buscar y para solucionar el problema, según la naturaleza de los errores.  
  
### <a name="see-also"></a>Vea también  
 [Integración de Azure con Common Data Service](azure-integration.md)
