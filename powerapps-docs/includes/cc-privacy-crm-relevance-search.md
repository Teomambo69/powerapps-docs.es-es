Al habilitar la característica Búsqueda por relevancia, los datos de las entidades y los atributos participantes de su instancia [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] empezarán a sincronizarse y finalmente se almacenarán en un índice de búsqueda [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 La Búsqueda por relevancia no está habilitada de forma predeterminada. El administrador del sistema debe habilitar la funcionalidad en una instancia [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]. Una vez habilitada la Búsqueda por relevancia, los administradores y personalizadores del sistema tienen control total sobre los datos que se sincronizarán con el índice de búsqueda [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Los personalizadores del sistema pueden usar el cuadro de diálogo **Configurar la búsqueda por relevancia** en las **Herramientas de personalización** para habilitar a determinadas entidades para la búsqueda y después configurar Vistas de búsqueda rápida en las entidades habilitadas para seleccionar los atributos que se pueden buscar. Los cambios en los datos se sincronizan continuamente entre [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] y la búsqueda de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] a través de una conexión segura.  Los datos de configuración están cifrados y los secretos necesarios se almacenan en [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
 En las próximas secciones se detallan los componentes y servicios de Azure que tienen que ver con la funcionalidad Búsqueda por relevancia.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Servicios Azure Search](https://azure.microsoft.com/services/search/)  
  
 Se usa un índice de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search para ofrecer resultados de la búsqueda de alta calidad con tiempos de respuesta breves.  La búsqueda de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] añade capacidades de búsqueda potentes y sofisticadas de última generación a [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)].  Este es un servicio de búsqueda dedicado externo a [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] proporcionado por [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]. Todos los índices de búsqueda nuevos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] están cifrados en reposo.  Si optó por recibir antes del 24 de enero de 2018, tendrá que indexar los datos; para ello, deberá optar por no recibir Búsqueda por relevancia, esperar una hora y volver a optar por recibir.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 Búsqueda por relevancia usa [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] para almacenar:  
  
-   Datos de configuración relacionados con la organización y el índice correspondiente  
  
-   Metadatos relativos con el servicio y los índices de búsqueda  
  
-   Punteros a datos y metadatos del sistema cuando la sincronización cambia  
  
-   Datos de autorización para habilitar la seguridad mejorada del nivel de fila  
  
[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/)  
  
El componente [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] se usa para el intercambio de mensajes entre [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] y [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y para mantener los elementos de trabajo administrados por el proceso de sincronización. Cada mensaje almacena información, como el identificador de la organización y el nombre de la entidad, que se utiliza para sincronizar los datos.  
  
[Azure Service Fabric Cluster](https://azure.microsoft.com/services/service-fabric/)  
  
El procesamiento y la indexación de datos se controlan en los microservicios implementados en las máquinas virtuales administradas a través del tiempo de ejecución de Service Fabric. Las API de búsqueda y el proceso de sincronización de datos también se hospedan en clúster de Service Fabric.  
  
Service Fabric nació tras varios años de experiencia de Microsoft ofreciendo servicios en la nube críticos y está probado en producción desde hace más de cinco años. Es la tecnología básica sobre la que ejecutamos nuestra infraestructura central de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y proporciona servicios entre los que se incluyen [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] y [!INCLUDE[pn_cortana](pn-cortana.md)], que se pueden escalar para procesar más de 500 millones de evaluaciones por segundo.  
  
[Conjuntos de escalado de máquinas virtuales de Azure](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
Los conjuntos de escalado de máquinas virtuales de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] son elásticos y se han diseñado para admitir cargas de trabajo de hiperescalado horizontal. Los clústeres de [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] se ejecutan en conjuntos de escalado de máquinas virtuales. Los microservicios para el procesamiento y la indexación de datos se hospedan en conjuntos de escalado y se administran con el tiempo de ejecución de Service Fabric.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] se usa para la administración segura de certificados, claves y otros secretos que se emplean en el proceso de búsqueda.  
  
[Azure Storage (Blob Storage)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
Los cambios en los datos de clientes se almacenan durante un máximo de 2 días en [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)].  Estos blobs se cifran con la última característica de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK, que ofrece funcionalidad de cifrado simétrico y asimétrico, e integración con [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]. A partir de la [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)], los documentos de Notas y Archivos adjuntos de mensajes de correo electrónico y citas también se sincronizan con Blob Storage.  
  
[Azure Active Directory Service](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] se usa para la autenticación entre [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] y los servicios de [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)].  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer se usa para distribuir el tráfico entrante entre las instancias de servicio en buen estado de los servicios en la nube o las máquinas virtuales que se han definido en un conjunto de carga equilibrada. Búsqueda por relevancia lo usa para equilibrar la carga de los puntos de conexión en una implementación.  
  
[Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
Las máquinas virtuales del clúster de Service Fabric que se ejecutan en una o varias subredes están conectadas mediante [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Network. Las directivas de seguridad, la configuración DNS, las tablas de enrutamiento y las direcciones IP están controladas completamente dentro de esta red virtual. Los grupos de seguridad de la red se aprovechan para aplicar las reglas de seguridad en esta red virtual. Estas reglas permiten o deniegan el tráfico de red a máquinas virtuales en la red virtual.