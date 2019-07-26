---
ms.openlocfilehash: fa4a17c2a3131f49f8a702388bdb405661855c10
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "61550028"
---
Al aceptar los términos y condiciones de la administración de eventos, se activa la característica de integración de seminarios web. La característica de integración de seminarios web aprovecha un proveedor de seminarios web asociado para realizar un evento o una sesión como un seminario web. Para usar el servicio de cualquier proveedor de seminario web, debe tener una cuenta con ellos. El único servicio de proveedor de seminario web asociado que se proporciona para uso inmediato es ON24. Cuando se usa la característica de integración de seminarios web, los datos esenciales para proporcionar y ejecutar el seminario web se procesarán y almacenarán en [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] y, luego, se enviarán a ON24. Tales datos incluirían los datos de registro de los participantes en el seminario web como sus nombres, correos electrónicos y nombres de empresa. Además, ON24 enviará métricas de seminario web, como la duración de la visualización del seminario web a [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] mediante [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)].

No es necesario activar la característica de seminario web para usar el resto de la solución de administración de eventos. El administrador puede desactivar la característica de integración de seminarios web mediante la eliminación de las credenciales en la configuración de seminarios web.

Los componentes y servicios de [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)] que se usan en la característica de integración de seminarios web son:

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [¿Qué es Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis))
  - Proporciona la clave de cifrado para cifrar o descifrar las credenciales de cuenta de ON24 del cliente.
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Información general de Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview))
  - Procesa y envía datos de registro y credenciales de cuenta de seminario web a ON24.
  - Recupera las métricas de seminario web de On24 en [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]; almacena las credenciales de la cuenta de ON24 del cliente (cifrado personalizado).