---
ms.openlocfilehash: dff813dcdf6d025ba47e29699e2047f79cf85600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225487"
---
Al habilitar Búsqueda por relevancia, los datos de entidades que participan y los atributos de su instancia de [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] comenzarán a sincronizarse a almacenarse en un índice de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search.  
  
 La funcionalidad Búsqueda por relevancia no está habilitada de forma predeterminada. El administrador del sistema debe habilitar la funcionalidad dentro de una instancia de [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]. Después de habilitar Búsqueda por relevancia, los administradores y personalizadores del sistema tienen control total sobre los datos que se sincronizarán con el índice de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search.  
  
 Los personalizadores del sistema pueden utilizar el cuadro de diálogo **Configurar la búsqueda por relevancia** de **Herramientas de personalización** con el fin de habilitar entidades específicas para la búsqueda y, a continuación, configurar las vistas de búsqueda rápida en entidades habilitadas para seleccionar los atributos que se pueden buscar. Los cambios en los datos se sincronizan continuamente entre [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] y [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search a través de una conexión segura.  Los datos de configuración se cifran y los secretos necesarios se almacenan en [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
 En las siguientes secciones se detallan los componentes y servicios de Azure que intervienen con la funcionalidad de búsqueda relevante.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Search Service](https://azure.microsoft.com/services/search/)  
  
 Un índice de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search se utiliza para proporcionar resultados de la búsqueda de alta calidad con tiempos de respuesta breves.  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search agrega funcionalidades de búsqueda eficaces y sofisticadas de próxima generación a [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)].  Se trata de un servicio de búsqueda dedicada externo a [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] que proporciona [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]. Todos los índices de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search se cifran en reposo.  Si se ha suscrito antes del 24 de enero de 2018, deberá volver a indexar los datos excluyendo Búsqueda por relevancia, esperar una hora y volver a suscribirse.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 La funcionalidad Búsqueda por relevancia usa [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] para almacenar lo siguiente:  
  
-   Datos de configuración relacionados con la organización y el índice correspondiente  
  
-   Metadatos relacionados con el servicio de búsqueda y los índices  
  
-   Punteros a los metadatos del sistema y los datos al sincronizar los cambios  
  
-   Datos de autorización para habilitar la seguridad mejorada de nivel de fila  
  
[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/)  
  
El componente [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] se utiliza para el intercambio de mensajes entre [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] y [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], así como para mantener los elementos de trabajo que administra el proceso de sincronización. Cada mensaje almacena información, como el nombre de la entidad y el identificador de la organización, que se utiliza para sincronizar los datos.  
  
[Clúster de Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
El procesamiento y la indexación de datos se controla en microservicios implementados en máquinas virtuales que administra el entorno de ejecución de Service Fabric. Las API de búsqueda y el proceso de sincronización de datos también están hospedados en el clúster de Service Fabric.  
  
Service Fabric ha nacido de años de experiencia en Microsoft que proporciona servicios en la nube críticos y ahora se ha comprobado en producción durante más de cinco años. Es la tecnología base sobre la que se ejecuta la infraestructura principal de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y sustenta servicios como [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)], y [!INCLUDE[pn_cortana](pn-cortana.md)], que se puede escalar para procesar más de 500 millones de evaluaciones por segundo.  
  
[Azure Virtual Machine Scale Sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Machine Scale Sets es un servicio de conjuntos elásticos de escalado de máquinas virtuales diseñado para admitir cargas de trabajo de hiperescalado horizontal. El clúster de [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] se ejecuta en conjuntos de escalado de máquinas virtuales. Los microservicios para el procesamiento y la indexación de datos se hospedan en los conjuntos de escalado y los administra el entorno de ejecución de Service Fabric.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] se usa para la administración segura de certificados, claves y otros secretos usados en el proceso de búsqueda.  
  
[Azure Storage (Blob Storage)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
Los cambios realizados en los datos del cliente se almacenan hasta 2 días en [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)].  Estos blobs se cifran con la característica más reciente del SDK de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage, que ofrece cifrado simétrico y asimétrico, e integración con [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]. Con la [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)], los documentos de las notas y los datos adjuntos de mensajes de correo electrónico y citas también se sincronizan con Blob Storage.  
  
[Servicio Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] se usa para la autenticación entre el [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] y los servicios de [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)].  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer se usa para distribuir el tráfico entrante entre las instancias de servicio de mantenimiento de los servicios en la nube o las máquinas virtuales que se han definido en un conjunto de carga equilibrada. La funcionalidad de búsqueda por relevancia lo usa para equilibrar la carga de los puntos de conexión en una implementación.  
  
[Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
Las máquinas virtuales del clúster de Service Fabric que se ejecutan en una o varias subredes están conectadas mediante [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Network. Las directivas de seguridad, la configuración DNS, las tablas de enrutamiento y las direcciones IP están controladas completamente dentro de esta red virtual. Los grupos de seguridad de la red se utilizan para aplicar las reglas de seguridad en esta red virtual. Estas reglas permiten o deniegan el tráfico de red a máquinas virtuales en la red virtual.