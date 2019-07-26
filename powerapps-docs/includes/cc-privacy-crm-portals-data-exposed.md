---
ms.openlocfilehash: ac90bfc27e03047cf422c44c83f550608d67b57e
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212849"
---
Al habilitar las funcionalidades del portal de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], los datos de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], como el nombre del cliente, el nombre del producto, el número del caso o cualquier dato de entidad personalizada, se pueden exponer a través de un portal de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] externo. Todos los datos expuestos a través del portal se almacenan en memoria en Microsoft [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Web Apps para el almacenamiento en caché y también como archivos en la unidad de disco duro local para habilitar la funcionalidad de búsqueda del portal.

Un administrador de inquilinos habilita portales de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] configurándolos con [!INCLUDE[pn_dyn_365_admin_center](../includes/pn-dyn-365-admin-center.md)], que también instala un paquete (con soluciones y datos) en la instancia [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] seleccionada. Un administrador de inquilinos o un usuario de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] configurado como Administrador del portal puede especificar los datos que se expondrán a través del portal. Para deshabilitar posteriormente las funcionalidades del portal, un administrador de inquilinos puede cancelar la suscripción al complemento del portal con [!INCLUDE[pn_Office_365](pn-office-365.md)].

Los componentes y servicios importantes de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con las funcionalidades del portal son los siguientes:
- [Web Apps de Azure](https://azure.microsoft.com/services/app-service/web/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Web Apps se usan para hospedar el portal [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]en.
- [Traffic Manager de Azure](https://azure.microsoft.com/services/traffic-manager/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Traffic Manager se usa para garantizar la alta disponibilidad del servicio mediante el enrutamiento del usuario al Web Apps que está en funcionamiento. 
- [Azure Service Bus](https://azure.microsoft.com/services/service-bus/): [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)](Temas/suscripciones) se usa para la invalidación de la memoria caché de los portales. [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] almacena temporalmente los mensajes, que se desencadenan cuando se modifica un registro relacionado con el portal en [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], y se pasan a las aplicaciones web para realizar la invalidación de caché. 
- [Azure Key Vault](https://azure.microsoft.com/services/key-vault/): Todos los servicios almacenan los datos de configuración en [!INCLUDE[pn_azure_key_vault](pn_azure_key_vault.md)].
- [Azure Storage](https://azure.microsoft.com/services/storage/): Los datos relacionados con la organización, el inquilino y el portal se [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] almacenan en el almacenamiento.
- [Azure Active Directory](https://azure.microsoft.com/services/active-directory/): Todos los servicios web usan [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] para autenticarse.
