---
ms.openlocfilehash: e9b0446c2fb09cad33f5a3ae4bb69103f7d07d70
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61586634"
---
Al utilizar el servicio de exportación de datos, cuando se activa un perfil de exportación de datos desde [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], los datos de las entidades agregadas al perfil se envían a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. La sincronización inicial incluye todos los datos asociados con las entidades agregadas al perfil de exportación, pero a partir de entonces la sincronización solo incluye nuevos cambios, que se envían continuamente al servicio de exportación de datos. Los datos enviados al servicio de exportación de datos se almacenan temporalmente en [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] y [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage, se procesan en [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] y finalmente se sincronizan (insertan, actualizan o eliminan) con la base de datos de destino especificada en la suscripción [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Cuando se hayan sincronizado los datos, se eliminan de [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] y [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage. Si se produce un error durante la sincronización de datos, los datos mínimos correspondientes al tipo de entidad, al identificador de registro y a la hora de sincronización se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage para permitir la descarga de una lista de registros que no se actualizaron.  
  
 Un administrador puede desactivar el perfil de exportación de datos en cualquier momento para detener la sincronización de datos. Además, un administrador puede eliminar el perfil de exportación para eliminar los registros que hayan producido un error y puede desinstalar la solución del servicio de exportación de datos para dejar de utilizar dicho servicio.  
  
 La sincronización de datos ocurre continuamente entre [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y el servicio de exportación de datos de una manera segura. Los datos se cifran a medida que se intercambian continuamente entre [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y el servicio de exportación de datos.  
  
 En las siguientes secciones se detallan los componentes y servicios de Azure que intervienen en el servicio de exportación de datos.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 Esto proporciona la API y procesa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] máquinas virtuales para procesar las notificaciones de sincronización de registros recibidas de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y luego procesarlas para insertar, actualizar o eliminar datos de registros en la base de datos de destino. Los microservicios que se implementan en máquinas virtuales administradas por el entorno de tiempo de ejecución de [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] administran todos los servicios de proceso relacionados con la sincronización de datos.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 Esto proporciona el bus de mensajes en el que [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] inserta los mensajes de notificación de sincronización que procesan los nodos de proceso en [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]. Cada mensaje almacena información, como el identificador y el registro de la organización, para la cual se pueden sincronizar los datos. Los datos de Azure Service Bus no se cifran en reposo, pero solo están disponible para el servicio de exportación de datos.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Los datos se almacenan temporalmente en [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)], en caso de que los datos de la notificación de sincronización de registros sean demasiado grandes para almacenarlos en un mensaje o se encuentre un error transitorio para procesar la notificación de sincronización. Estos blobs se cifran mediante el aprovechamiento de la característica más reciente del SDK de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage, que ofrece cifrado simétrico y asimétrico, e integración con [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] almacena la configuración del perfil de exportación de datos y las métricas de sincronización de datos.