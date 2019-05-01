---
ms.openlocfilehash: 509ad3f5b1b94378b2c6fd7661510b7aef0e3a23
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61582966"
---
Al habilitar Creación de ruta de aprendizaje para una organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], el contenido de Ruta de aprendizaje (publicado o en borrador) que crearon los usuarios (con los privilegios de seguridad adecuados) se almacenará en [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]. Además, habilitar la característica permite que [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)] capture los siguientes datos asociados con una organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]:  
  
-   Lista de organizaciones en el inquilino  
  
-   Configuración del explorador/SO aplicable y del cliente de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] del usuario final  
  
-   Datos de uso de los usuarios finales, como el tiempo dedicado a las rutas de aprendizaje o los clics registrados  
  
-   Datos agregados de usuario final, como ubicación, rol de seguridad, idioma del usuario  
  
-   Datos agregados de usuario final, como ubicación, rol de seguridad, idioma del usuario  
  
-   Comentarios textuales de los usuarios finales  
  
 Un administrador puede habilitar (y posteriormente, deshabilitar) la característica Creación de ruta de aprendizaje a través de una configuración en la pestaña **General** del cuadro de diálogo **Configuración del sistema**.  
  
 En las próximas secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con la funcionalidad Creación de ruta de aprendizaje.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Cloud Services](https://azure.microsoft.com/en-us/services/cloud-services/)  
  
 **Servicio web**  
  
 El servicio web se encarga de los controles que se presentan en el cliente en entorno de ejecución de Ruta de aprendizaje. El servicio web también admite Designer API, que también la usa la característica Creación de ruta de aprendizaje. El servicio almacena los controles en [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 **Compilador (rol de trabajo)**  
  
 El rol de compilador administra la publicación de un control en un grupo de publicación. El compilador usa la cola para almacenar mensajes sobre el trabajo de publicación. Los resultados se almacenan en [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 [Azure SQL Database](https://azure.microsoft.com/en-us/services/sql-database/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] para almacenar:  
  
-   Controles que sean mediante Ruta de aprendizaje.  
  
-   Creación de ruta de aprendizaje relacionada con la configuración.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] para autenticar el servicio web.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/en-us/services/traffic-manager/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Traffic Manager para equilibrar la carga del servicio web para obtener disponibilidad y rendimiento.  
  
 [Azure Storage Queue](https://azure.microsoft.com/en-us/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage Queue se usa para coordinar la comunicación entre los roles de servicio web y de compilador.  
  
 [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] para almacenar el contenido estático (contenido CSS, imágenes, [!INCLUDE[pn_JavaScript](pn-javascript.md)] del lado cliente).  
  
 [Azure Content Delivery Network (CDN)](https://azure.microsoft.com/en-us/services/cdn/)  
  
 CDN se usa para almacenar en caché el contenido estático del lado cliente ([!INCLUDE[pn_JavaScript](pn-javascript.md)], imágenes y archivos CSS), para usarlo desde la red CDN global.