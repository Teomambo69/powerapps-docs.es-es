Al instalar [!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)], cuando se proporciona la información de suscripción de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], se implementarán los recursos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] necesarios (listados a continuación) y la instancia de [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] enviará datos (como comandos y registros) a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para habilitar los escenarios habilitados para IoT que registran dispositivos y, después, envían y reciben comandos de dichos dispositivos registrados. Un administrador puede desinstalar Connected Field Service para quitar la funcionalidad y después navegar al portal de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para administrar cualquier servicio de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionado que ya no se necesite.  
  
 En las próximas secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que tienen que ver con la funcionalidad Connected Field Service.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Cola de Service Bus](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 Proporciona una cola para los mensajes entrantes y salientes (comandos) que fluyen entre [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Cuando se envía una alerta de IoT a [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], o se envía un comando de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] a IoT Hub, se pondrá en cola aquí.  
  
 [Logic Apps](https://azure.microsoft.com/services/logic-apps/)  
  
 Proporciona un servicio de orquestación que usa un conector de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y un conector de cola. Los ​​​conectores de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] se usan para generar entidades específicas de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y los conectores de cola se usan para hacer el sondeo de la cola.  
  
 [Stream Analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 Proporciona un motor de procesamiento de eventos completamente administrado en tiempo real que ayuda a desbloquear un conocimiento más profundo de los datos. Stream Analytics facilita la configuración de cálculos analíticos en tiempo real de las transmisiones de datos de dispositivos, sensores, sitios web, medios sociales, aplicaciones, sistemas de la infraestructura y otros. Funciona como un embudo para enviar alertas selectivas de IoT a [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [IoT Hub](https://azure.microsoft.com/services/iot-hub/)  
  
 Connected Field Services usa el IoT Hub para administrar el estado de los dispositivos y activos registrados. Además, IoT Hub envía los comandos y las notificaciones a los dispositivos conectados, y hace el seguimiento de la entrega de los mensajes con acuse de recibo. Los mensajes de los dispositivo se envían de forma duradera para adaptarse a los dispositivos conectados ​intermitentemente.  
  
 **Simulador**  
  
 Se trata de una aplicación web de prueba para emular el dispositivo que envía o recibe comandos del IoT Hub.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 Connected Field Service usa SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para almacenar mensajes de latido de dispositivos para que PowerBI los use posteriormente para mostrar el estado de los dispositivos en [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Las consultas que utilizará Stream Analytics se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage.