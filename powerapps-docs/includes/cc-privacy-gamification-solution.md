---
ms.openlocfilehash: 747ea34b784b852261debe91f587d64ee3277804
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61582980"
---
Al instalar y habilitar la solución [!INCLUDE[pn_gamification](pn-gamification.md)], los identificadores de cuenta del usuario (como nombre, apellido y dirección de correo electrónico) se almacenarán en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para permitir la autorización con el servicio [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], que se hospeda en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Esto se aplica a todos los usuarios que estén habilitados en el servicio [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] por su administrador. La solución [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] envía datos de indicadores clave de rendimiento (KPI), configurados por un administrador, al servicio [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y esos datos se almacenan en almacenamiento estructurado y almacenamiento de blobs de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  El avatar, los reconocimientos personalizados y el logotipo de la compañía se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], pero la información no se devuelve a [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Tenga en cuenta que los administradores y los usuarios autorizados pueden aprovechar los datos de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)], como llamadas telefónicas, oportunidades e ingresos contabilizados, para configurar los KPI a fin de usarlos en los juegos. El servicio [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] no inicia ninguna llamada a [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y solo responde a los datos, como los juegos en los que se usan los KPI, que fluyen de vuelta a [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Un administrador también puede permitir que la transmisión por televisión de [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] se convierta en pública. Los administradores de juegos que configuran transmisiones por televisión de [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] y hacen posible el streaming público permitirán que cualquier persona en Internet con el vínculo a la transmisión por televisión pueda verla.  
  
Posteriormente, un administrador puede quitar la funcionalidad [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] desinstalando esta solución de la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
En las siguientes secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que intervienen en [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)].  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **Servicio de diseñador (rol web)**  
  
Proporciona varios servicios web para la comunicación entre una organización de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] y varios componentes de [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] multiinquilino. Por ejemplo, los detalles de ludificación almacenados en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Storage.  Los cálculos de juegos usan la cola de [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] y se devuelven para puntuarse y mostrarse en el servicio.  Las imágenes cargadas de clientes y usuarios se almacenan en [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]. Todas las solicitudes se autentican en [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)].  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
Todos los servicios almacenan los datos de configuración en [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] usa SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para almacenar:  
  
- Datos de KPI  
  
- Cálculos de juegos  
  
- Datos de la organización (inquilino)  
  
[Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
Los avatares, logotipos de empresa y otras imágenes de cliente cargadas se almacenan en [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)].  
  
[Azure Content Delivery Network (CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network para servir contenido estático al entorno de ejecución, como imágenes (incluidas las imágenes cargadas como logotipos de cliente), [!INCLUDE[pn_JavaScript](pn-javascript.md)] y CSS.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] usa [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] para autenticar a los usuarios y determinar su idoneidad para usar la plataforma.