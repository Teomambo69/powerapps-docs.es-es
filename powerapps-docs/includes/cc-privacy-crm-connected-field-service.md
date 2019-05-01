---
ms.openlocfilehash: ce9db35844f46e9779055ec30dcba0f9459c3a16
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61583491"
---
Al instalar [!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)], cuando proporcione la información de su suscripción [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], se implementarán los recursos [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] necesarios (enumerados a continuación) y su instancia [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] enviará datos (como comandos y registros) a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para habilitar escenarios compatibles con IoT que registren dispositivos y luego envíen y reciban comandos a los dispositivos registrados. Un administrador puede desinstalar el servicio de campo conectado para eliminar la funcionalidad y después ir a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Portal para administrar cualquier servicio relacionado [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que ya no sea necesario.  
  
 En las siguientes secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que intervienen con la funcionalidad de servicio de campo conectado.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Cola de Service Bus](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 Esto proporciona una cola para los mensajes (comandos) entrantes y salientes que fluyen entre [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Cuando se envía una alerta de IoT a [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] o se envía un comando desde [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] al centro de IoT, se pondrá en cola aquí.  
  
 [Logic Apps](https://azure.microsoft.com/services/logic-apps/)  
  
 Esto proporciona un servicio de orquestación que utiliza un conector [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y un conector de cola. Los conectores [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] se utilizan para construir entidades específicas para [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y los conectores de cola se utilizan para sondear la cola.  
  
 [Stream analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 Esto proporciona un motor de procesamiento de eventos en tiempo real totalmente administrado que ayuda a obtener información detallada de los datos. Stream Analytics facilita la configuración de cálculos analíticos en tiempo real sobre la transmisión de datos desde dispositivos, sensores, sitios web, redes sociales, aplicaciones, sistemas de infraestructura y mucho más. Funciona como un embudo para enviar alertas de IoT selectivas a [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [IoT Hub](https://azure.microsoft.com/services/iot-hub/)  
  
 Los servicios de campo conectados utilizan IoT Hub para administrar el estado de los dispositivos y recursos registrados. Además, IoT Hub envía comandos y notificaciones a los dispositivos conectados y realice un seguimiento de la entrega de los mensajes con acuses de recibo. Los mensajes de dispositivo se envían de una forma duradera para hospedar dispositivos conectados intermitentemente.  
  
 **Simulador**  
  
 Esta es una aplicación web de prueba para emular el dispositivo que envía o recibe comandos desde el centro de IoT.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 Servicio de campo conectado que utiliza SQL de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para almacenar los mensajes de latido de dispositivo para su uso posterior en Power BI para mostrar el estado de los dispositivos de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Las consultas que Stream Analytics va a utilizar se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage.