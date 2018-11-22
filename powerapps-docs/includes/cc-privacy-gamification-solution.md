Al instalar y habilitar la solución [!INCLUDE[pn_gamification](pn-gamification.md)], los identificadores de la cuenta del usuario que la habilita (como nombre de pila, apellido y dirección de correo electrónico) se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para permitir la autorización con el servicio [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], que se hospeda en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Esto se aplica a todos los usuarios habilitados en el servicio [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] por su administrador. La solución [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] envía datos de indicadores de rendimiento clave (KPI), configurados por un administrador, al servicio [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y esos datos se guardan tanto en Blob Storage como en almacenamiento estructurado de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  El avatar, los galardones personalizados y el logotipo de la compañía de cada usuario se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], pero la información no se devuelve a [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Tenga en cuenta que los administradores y usuarios autorizados pueden aprovechar los datos de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)], como llamadas de teléfono, oportunidades e ingresos contabilizados, para configurar KPI con el fin de usarlos en juegos. El servicio [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] no inicia ninguna llamada a [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y solo responde a los datos, como juegos donde se usan los KPI, que vuelven a [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Un administrador puede permitir también que las secuencias de TV de [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] sean públicas. Los administradores de juegos que configuran secuencias de TV de [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] y habilitan el streaming público permitirán que cualquiera que tenga el vínculo de la secuencia pueda verla en Internet.  
  
Después, un administrador puede quitar la funcionalidad de [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] desinstalando esta solución de la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
En las secciones siguientes, se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)].  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **Servicio del diseñador (rol web)**  
  
Proporciona varios servicios web para la comunicación entre una organización de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y los componentes multiempresa de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]. Por ejemplo, los detalles de ludificación almacenados en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Storage.  Los cálculos de los juegos utilizan una cola de [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] y se devuelven para puntuarlos y mostrarlos en el servicio.  Las imágenes de clientes y usuarios cargadas se almacenan en [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]. Todas las solicitudes se autentican con [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)].  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
Todos los servicios almacenan los datos de configuración en [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] utiliza SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para almacenar lo siguiente:  
  
- Datos de KPI  
  
- Cálculos de juegos  
  
- Datos de la organización (inquilino)  
  
[Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
Los avatares, logotipos de compañías y otras imágenes cargadas por los clientes se almacenan en [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)].  
  
[Azure Content Delivery Network (CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] utiliza [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network para entregar contenido estático al entorno de ejecución; por ejemplo, imágenes (incluidas las imágenes cargadas, como logotipos de clientes), [!INCLUDE[pn_JavaScript](pn-javascript.md)] y CSS.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] utiliza [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] para autenticar a los usuarios y determinar si cumplen los requisitos para usar la plataforma.