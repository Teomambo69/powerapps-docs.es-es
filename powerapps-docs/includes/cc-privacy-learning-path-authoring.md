Al habilitar la creación de la Ruta de aprendizaje para ​​una organización [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], el contenido de la Ruta de aprendizaje (publicado o borrador) creado por los usuarios (con los privilegios correctos de seguridad) se almacenará en [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]. Además, habilitar la característica permite que [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)] capture los siguientes datos asociados ​​con una organización [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]:  
  
-   Lista de organizaciones del inquilino  
  
-   Cliente [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] de los usuarios finales y configuración ​​aplicable del sistema operativo / explorador  
  
-   Datos de uso de los usuarios finales, por ejemplo, tiempo empleado en las Rutas de aprendizaje o clic grabados  
  
-   Datos de los usuarios finales agregados: ubicación, rol de seguridad, idioma del usuario  
  
-   Datos de los usuarios finales agregados: ubicación, rol de seguridad, idioma del usuario  
  
-   Comentarios literales de los usuarios finales  
  
 Un administrador puede habilitar (y deshabilitar posteriormente) la creación de la Ruta de aprendizaje mediante un valor de la pestaña **General** del cuadro de diálogo **Configuración del sistema**.  
  
 En las secciones siguientes se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con la funcionalidad Creación de Ruta de aprendizaje.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **Servicio web**  
  
 El servicio web contiene los controles que el tiempo de ejecución de la Ruta de aprendizaje genera en el cliente. El servicio web también admite la API de diseñador que la creación de la Ruta de aprendizaje utiliza. El servicio almacena los controles en [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 **Compilador (rol de trabajo)**  
  
 El rol de compilador administra la publicación de un control en un grupo de publicación. El compilador usa la cola para almacenar mensajes acerca del trabajo de publicación. Los resultados se almacenan en [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] para almacenar:  
  
-   Controles que se crean usando Ruta de aprendizaje.  
  
-   Creación de Ruta de aprendizaje relacionada con la configuración.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Ruta de aprendizaje utiliza [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] para autenticar el servicio web.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/services/traffic-manager/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Traffic Manager para equilibrar la carga del servicio web a fin de lograr disponibilidad y rendimiento.  
  
 [Azure Storage Queue](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage Queue se usa para coordinar la comunicación entre los roles de compilador y ​​servicio web.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] para almacenar el contenido estático ([!INCLUDE[pn_JavaScript](pn-javascript.md)] del lado de cliente, ​imágenes, contenido CSS).  
  
 [Red de entrega de contenido (CDN) de Azure](https://azure.microsoft.com/services/cdn/)  
  
 La red CDN se utiliza para almacenar en caché el contenido estático del lado del cliente ([!INCLUDE[pn_JavaScript](pn-javascript.md)], imágenes y archivos CSS) y ofrecerlo desde la red CDN global.