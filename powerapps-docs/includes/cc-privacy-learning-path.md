---
ms.openlocfilehash: 3840a097743111f6ae89e65426a366207f8364d9
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61582959"
---
Al habilitar la característica Ruta de aprendizaje, permite que el contenido HTML estático, las imágenes y los scripts se almacenen en Content Delivery Network de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Además, todo el contenido dinámico que se muestra se almacenará en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache, que se usa para el almacenamiento previo en caché desde [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Database.  
  
 Un administrador puede habilitar y deshabilitar el uso de la característica Ruta de aprendizaje dentro de una instancia de [!INCLUDE[pn_crm_online_shortest](pn-crm-online-shortest.md)] mediante Habilitar la ayuda guiada en la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 En las próximas secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con la funcionalidad Ruta de aprendizaje.  
  
> [!NOTE]
>  Para obtener más información sobre las ofertas de servicio de Azure adicionales, visite el [Centro de confianza de Azure](https://azure.microsoft.com/en-us/support/trust-center/).  
  
 [Cloud Services](https://azure.microsoft.com/en-us/services/cloud-services/)  
  
 **Tiempo de ejecución de Ruta de aprendizaje (rol web)**  
  
 Esta es la aplicación web que presenta el contenido a los usuarios.  
  
 **Servicio Ruta de aprendizaje (rol de trabajo)**  
  
 El rol de trabajo es responsable de procesar los datos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Database y almacenarlos en caché en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache.  
  
 [Azure SQL Database](https://azure.microsoft.com/en-us/services/sql-database/)  
  
 Ruta de aprendizaje usa SQL Database para almacenar lo siguiente:  
  
-   Contenido  
  
-   Metadatos de contenido  
  
-   Metadatos del sistema  
  
 [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/)  
  
 Tanto el código HTML como las imágenes, [!INCLUDE[pn_JavaScript](pn-javascript.md)] y CSS se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage.  
  
 [Azure Content Delivery Network (CDN)](https://azure.microsoft.com/en-us/services/cdn/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network para presentar contenido estático al tiempo de ejecución de la encuesta, como HTML, imágenes, [!INCLUDE[pn_JavaScript](pn-javascript.md)] y CSS.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] Service para autenticar servicios web específicamente para el diseñador. Actualmente, el diseñador no se expone a los clientes y asociados. Por tanto, la autenticación solo se realiza dentro del dominio de [!INCLUDE[cc_Microsoft](cc-microsoft.md)].  
  
 [Azure Redis Cache](https://azure.microsoft.com/en-us/services/cache/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache para almacenar en caché contenido dinámico que presentamos a los usuarios.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/en-us/services/traffic-manager/)  
  
 Ruta de aprendizaje usa Traffic Manager para mejorar la disponibilidad de las aplicaciones importantes al supervisar los sitios y servicios externos o de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y remitir automáticamente a los usuarios a una nueva ubicación si se produce algún error.  
  
 [Azure Resource Manager](https://azure.microsoft.com/en-us/features/resource-manager/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Resource Manager para implementar CDN, Redis Cache, SQL Database y Cloud Services como grupos de recursos para que estén en un estado coherente y se puedan implementar repetidamente.