Al utilizar el servicio de exportación de datos, cuando se activa un perfil de exportación de datos desde [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], los datos de las entidades agregadas al perfil se envían a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. La sincronización inicial incluye todos los datos asociados con las entidades agregadas al perfil de exportación, pero la sincronización incluye solo los cambios nuevos, que se envían continuamente al servicio de exportación de datos. Los datos enviados al servicio de exportación de datos se almacenan temporalmente en [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] y en Almacenamiento de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], se procesan en [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] y, por último, se sincronizan (insertan, actualizan o eliminan) en la base de datos de destino especificada en su suscripción de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Una vez que se hayan sincronizado los datos, se eliminan de [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] y de Almacenamiento de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Si se produce un error durante la sincronización de datos, los datos mínimos correspondientes a un tipo de entidad, el identificador de registro y la marca de tiempo de la sincronización se almacenan en Almacenamiento de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para permitir descargar una lista de registros no actualizados.  
  
 Un administrador puede desactivar el perfil de exportación de datos en cualquier momento para detener la sincronización de datos. Además, un administrador puede eliminar el perfil de exportación para quitar los registros de errores y puede desinstalar la solución Servicio de exportación de datos para dejar de usar el servicio de exportación de datos.  
  
 La sincronización de datos se produce de forma continua entre [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y el servicio de exportación de datos de forma segura. Los datos se cifran mientras se intercambian de forma continua entre [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y el servicio de exportación de datos.  
  
 En las próximas secciones se detallan los componentes y servicios de Azure relacionados con el servicio de exportación de datos.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 Proporciona la API y el cálculo de las máquinas virtuales de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para procesar las notificaciones de sincronización de registros recibidas de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y luego las procesa para insertar, actualizar o eliminar datos de registros en la base de datos de destino. Los microservicios que se implementan en las máquinas virtuales administradas por el tiempo de ejecución de [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] gestionan todos los servicios de cálculo relacionados con la sincronización de datos.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 Proporciona el bus de mensajes en el que [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] inserta los mensajes de notificación de sincronización procesados por los nodos de cálculo en [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]. Cada mensaje almacena información, como el registro y el identificador de la organización, para la que se van a sincronizar los datos. Los datos de Azure Service Bus no están cifrados en reposo y solo son accesibles para el Servicio de exportación de datos.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Los datos se almacenan temporalmente en [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] en caso de que los datos de la notificación de sincronización de registros sean demasiado grandes para almacenarlos en un mensaje, o si se produce un error transitorio al procesar la notificación de sincronización. Estos blobs se cifran con la última característica del SDK de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage, que ofrece soporte al cifrado simétrico y asimétrico e integración con [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] almacena las métricas de sincronización de datos y de configuración del perfil de exportación de datos.