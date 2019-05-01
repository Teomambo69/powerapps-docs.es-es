---
ms.openlocfilehash: 864bb7bde775f88cdf43ba5c453bd1ff02f81b85
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61585234"
---
Al habilitar Análisis de relaciones, una característica de Inteligencia integrada, los datos de cliente de[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], incluida información de identificación del usuario, se enviará y almacenará en [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)], un servicio que se ejecuta en Azure, con el fin de calcular los KPI de relación entre usuarios y clientes de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. Los datos también se almacenarán temporalmente en [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] y se procesarán para una salida adicional, como las tendencias y el estado de las relaciones, y luego esa información se devuelve a [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] y, posteriormente, a [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 Un administrador puede habilitar la característica Análisis de relaciones al instalarla como una solución en la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]. Además, un administrador posteriormente puede deshabilitar la característica si desinstala esta solución de la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 Al habilitar los datos de [!INCLUDE[pn_Exchange](pn-exchange.md)] como un origen de datos, enviará datos de cliente de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], incluida información de identificación del usuario final, desde [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] hasta [!INCLUDE[pn_Exchange_Online](pn-exchange-online.md)] con el fin de recopilar datos adicionales, los que se usarán para cálculos de KPI y para crear otros análisis.  Para habilitar completamente esta característica, deberá lograr que el administrador de [!INCLUDE[pn_Office_365](pn-office-365.md)] [!INCLUDE[pn_Exchange](pn-exchange.md)] también esté de acuerdo con una declaración de consentimiento independiente en la aplicación [!INCLUDE[pn_Exchange](pn-exchange.md)].  Una vez que ambos administradores hayan dado su consentimiento a través de los productos aplicables, [!INCLUDE[pn_Exchange](pn-exchange.md)] proporcionará metadatos de reuniones y correo electrónico, los que se almacenarán en [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] y se usarán para mejorar los cálculos de KPI y, posiblemente, otros análisis según lo decida el administrador de [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]. Deshabilitar los datos de [!INCLUDE[pn_Exchange](pn-exchange.md)] como origen de datos en la configuración de Análisis de relaciones no quitará los datos de [!INCLUDE[pn_Exchange](pn-exchange.md)] de [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)].  La eliminación de los datos de [!INCLUDE[pn_Exchange](pn-exchange.md)] en [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] SOLO se puede realizar directamente desde [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)].  
  
 En las siguientes secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que participan en Análisis de relaciones.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]**  
  
 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)], un servicio que se ejecuta en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], almacena datos de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], incluida información de identificación personal sobre los clientes, con el fin de calcular la salida de la característica Análisis de relaciones. La versión preliminar de [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] está sujeta a los [términos de uso complementarios para las características en vista previa (GB)](http://go.microsoft.com/fwlink/p/?LinkId=511446).  
  
 [Obtenga más información sobre la versión preliminar de Customer Insights](https://azure.microsoft.com/en-us/services/customer-insights/).  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] se usa para almacenar temporalmente datos de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], incluida información de identificación personal sobre los clientes, con el fin de calcular la salida de la característica Análisis de relaciones.