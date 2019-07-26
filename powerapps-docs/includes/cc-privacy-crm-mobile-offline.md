---
ms.openlocfilehash: 787ff9592604f9a9bce1929e4d429a39da5ec48a
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456824"
---
Cuando se habilita Dynamics 365 Mobile Offline, los datos de Dynamics 365 (en línea) se descargan a la base de datos SQL Azure mediante Azure Cloud, en función de las entidades que están habilitadas para la disponibilidad sin conexión. Cuando un usuario se conecta a Azure Cloud Services desde una aplicación móvil con la funcionalidad sin conexión, los datos se descargan desde la base de datos SQL Azure a una base de datos local en el dispositivo móvil. La transferencia de datos entre la base de datos SQL Azure en Azure Cloud y la aplicación móvil de Dynamics 365 con la funcionalidad sin conexión se realiza a través de una conexión SSL segura. En última instancia, los datos del cliente se almacena en la base de datos SQL Azure y en el dispositivo móvil.  
  
 Un administrador determina si los usuarios de una organización tienen permitido o no entrar en modo sin conexión con la aplicación Microsoft Dynamics 365 Mobile Offline al usar roles de seguridad y la personalización de perfiles de Dynamics 365 Mobile. Los administradores de Dynamics 365 pueden configurar qué entidades se descargan a través de la sincronización sin conexión mediante el uso de la configuración Sync Filters (Filtros de sincronización) en el cuadro de diálogo Setting –Mobile Offline (Configuración –Mobile Offline).  
  
 Tenga en cuenta que es el cliente, y no Microsoft, quien controla los datos almacenados en el dispositivo del usuario. El administrador tiene el control total de los datos que se pueden extraer en los niveles de entidad o en el rol de seguridad del usuario. Sin embargo, una vez que se extraen los datos, habrán salido del límite de seguridad que proporciona Dynamics 365 Online.  
  
 A continuación, se proporciona una lista de los componentes y servicios de Azure que participan en la funcionalidad de Mobile Offline.  
  
 **Nota:** Para obtener más información sobre las ofertas de servicio de Azure adicionales, visite el [Centro de confianza de Azure](https://azure.microsoft.com/support/trust-center/).  
  
 **Cloud Services (rol web)**  
  
 Mobile Offline usa dos servicios en la nube, uno para el aprovisionamiento y otro para la sincronización de datos.  
  
 El servicio de aprovisionamiento tiene un rol web único que lee los mensajes de la cola de Service Bus (SB) para distintos eventos que provienen de Dynamics 365, como aprovisionamiento o desaprovisionamiento. Luego procesa esos mensajes mediante la creación o eliminación de las bases de datos de la organización y el envío de elementos de trabajo (mensajes) recurrentes en la cola de SB de sincronización de datos. Durante este proceso, lee o escribe los datos de configuración ya sea desde el archivo CSCFG o desde Dynamics 365 SW API.  
  
 El servicio de sincronización de datos tiene dos roles web. Uno mantiene el esquema y los datos de la base de datos provisional en sincronización con los datos y metadatos de una organización de Dynamics 365, mientras que el otro rol web es para ejecutar el servidor de sincronización y procesar las solicitudes de sincronización del cliente. El primer rol web procesa los mensajes provenientes de la cola de SB de sincronización de datos para distintas organizaciones y luego se pone en contacto con Dynamics 365 para obtener los cambios de datos y metadatos antes de confirmarlos en la base de datos provisional. También hace el trabajo de configurar el servidor de sincronización con las organizaciones que entran y salen del sistema y sus modelos de cliente. El otro rol web ejecuta el servidor de sincronización (código no administrado) para hospedar los puntos de conexión de administración y sincronización. El otro rol web usa el punto de conexión de administración para enviar los datos de configuración. El punto de conexión de sincronización lo usan los clientes externos (Dynamics 365 Mobile Application) para sincronizar los datos. Del mismo modo que el servicio de aprovisionamiento, ambos roles leen o escriben los datos de configuración ya sea desde el archivo CSCFG o desde Dynamics 365 SW API.  
  
 **Cola**  
  
 Mobile Offline usa Azure Queue para intercambiar mensajes entre Dynamics 365 y Azure. Se usa para mantener los elementos de trabajo que los servicios en la nube procesan. Cada mensaje almacena información como el identificador de la organización, el nombre de la entidad para la que se sincronizan los datos y la cadena de conexión para el punto de conexión OData de la organización.  
  
 **SQL Database**  
  
 Mobile Offline usa Azure SQL Storage para almacenar lo siguiente:  
  
-   Datos replicados desde organizaciones de Dynamics 365 y para responder las solicitudes de sincronización de los clientes.  
  
-   Datos de configuración, como las cadenas de conexión de base de datos de la organización.  
  
 **Storage**  
  
 Mobile Offline usa Azure Blob Storage para almacenar registros y seguimientos que genera el servicio en la nube.  
  
 **Active Directory Service**  
  
 Mobile Offline usa Azure Active Directory Service para la autenticación con otros servicios, como Dynamics 365, SW API o las Azure Management API.  
  
 **Azure DNS**  
  
 Mobile Offline usa Azure DNS para redirigir las solicitudes de cliente en función, en función de los nombres de organización, a los puntos de conexión de servicio en la nube correctos.  
  
 **Azure Virtual Network**  
  
 Una red virtual (VNet) de Azure es una representación de su propia red en la nube. El equipo de producto de Dynamics 365 puede controlar la configuración de la red de Azure y definir los bloques de direcciones DHCP, la configuración de DNS, las directivas de seguridad y el enrutamiento.  
  
 **Azure Load Balancer**  
  
 Azure Load Balancer ofrece alta disponibilidad y rendimiento de la red para sus aplicaciones. Se trata de un equilibrador de carga tipo capa 4 (TCP, UDP) que distribuye el tráfico entrante entre las instancias de servicio de mantenimiento de los servicios en la nube o en las máquinas virtuales que se definieron en un conjunto de equilibradores de carga. Se usa para equilibrar la carga de los puntos de conexión en una implementación.