Al habilitar Dynamics 365 Mobile Offline, los datos de Dynamics 365 (online) se descargan en la base de datos SQL de Azure usando la nube de Azure, en función de las entidades habilitadas para la disponibilidad sin conexión. Cuando un usuario se conecta al Servicio de nube de Azure desde una aplicación móvil con la funcionalidad sin conexión, los datos se descargan desde la base de datos SQL de Azure en una base de datos local del dispositivo móvil. La transferencia de datos entre la base de datos SQL de Azure de la nube de Azure y la aplicación móvil de Dynamics 365 con la funcionalidad sin conexión se realiza a través de una conexión SSL segura. En última instancia, los datos del cliente se almacenan en la base de datos SQL de Azure y en el dispositivo móvil.  
  
 Un administrador determina si se permite o no que los usuarios de una organización trabajen sin conexión con la aplicación Microsoft Dynamics 365 Mobile Offline usando roles de seguridad y personalización de perfiles de Dynamics 365 Mobile. Los administradores de Dynamics 365 pueden configurar las entidades que se descargan mediante la sincronización sin conexión con la configuración Filtros de sincronización del cuadro de diálogo Configuración –Mobile Offline.  
  
 Tenga en cuenta que es el cliente, no Microsoft, el que controla los datos almacenados en el dispositivo del usuario. El administrador tiene control total sobre los datos que se pueden extraer en los niveles de rol de seguridad o entidad de usuario. No obstante, una vez extraídos los datos, habrá dejado el límite de seguridad proporcionado por Dynamics 365 Online.  
  
 A continuación se muestra una lista de los componentes y servicios de Azure relacionados con la funcionalidad de Mobile Offline.  
  
 **Nota:** para obtener más información sobre otras ofertas de servicios de Azure, visite el [Centro de confianza de Microsoft Azure](https://azure.microsoft.com/en-us/support/trust-center/).  
  
 **Cloud Services (rol web)**  
  
 Mobile Offline utiliza dos servicios en la nube: uno para el aprovisionamiento y otro para la sincronización de datos.  
  
 El servicio de aprovisionamiento tiene un único rol web que lee mensajes de la cola de Service Bus (SB) para los diferentes eventos procedentes de Dynamics 365, como el aprovisionamiento o el desaprovisionamiento. A continuación procesa esos mensajes creando o eliminando bases de datos de la organización y enviando elementos de trabajo (mensajes) periódicos de la cola de SB de sincronización de datos. Durante este proceso, lee y escribe datos de configuración del archivo CSCFG o de la API SW de Dynamics 365.  
  
 El servicio de sincronización de datos tiene dos roles web. Uno de ellos mantiene el esquema y los datos de la base de datos provisional sincronizados con los metadatos y los datos de una organización de Dynamics 365, mientras que el otro ejecuta el servidor de sincronización y procesa las solicitudes de sincronización del cliente. El primer rol web procesa los mensajes de la cola de SB de sincronización de datos para diferentes organizaciones y después se pone en contacto con Dynamics 365 para obtener los cambios en los datos y metadatos antes de confirmarlos en la base de datos provisional. También configura el servidor de sincronización con las organizaciones que entran y salen del sistema y sus modelos de cliente. El otro rol web ejecuta el servidor de sincronización (código no administrado) para hospedar los extremos de administración y sincronización. El otro rol web usa el extremo de administración para enviar datos de configuración. Los clientes externos (aplicación Dynamics 365 Mobile) usan el extremo de sincronización para la sincronización de datos. Al igual que el servicio de aprovisionamiento, estos roles leen/escriben datos de configuración del archivo CSCFG o de la API SW de Dynamics 365.  
  
 **Queue**  
  
 Mobile Offline usa las colas de Azure para el intercambio de mensajes entre Dynamics 365 y Azure. Se usa para mantener los elementos de trabajo procesados por los servicios en la nube. Cada mensaje almacena información como el identificador de la organización, el nombre de la entidad para la que se sincronizan datos y la cadena de conexión del extremo OData de la organización.  
  
 **SQL Database**  
  
 Mobile Offline utiliza Azure SQL Storage para almacenar:  
  
-   Datos replicados de organizaciones de Dynamics 365 y para atender solicitudes de sincronización de clientes.  
  
-   Datos de configuración como cadenas de conexión de base de datos de la organización.  
  
 **Storage**  
  
 Mobile Offline utiliza Azure Blob Storage para almacenar registros y seguimientos generados por el servicio en la nube.  
  
 **Active Directory Service**  
  
 Mobile Offline utiliza el Servicio de Azure Active Directory para autenticarse con otros servicios como Dynamics 365, o la API SW o las API de administración de Azure.  
  
 **DNS de Azure**  
  
 Mobile Offline utiliza DNS de Azure para redirigir las solicitudes de cliente, en función de los nombres de organización, a los extremos adecuados del servicio en la nube.  
  
 **Azure Virtual Network**  
  
 Una red virtual (VNet) de Azure es una representación de su propia red en la nube. El equipo de producto de Dynamics 365 puede controlar la configuración de red de Azure y definir los bloques de direcciones DHCP, la configuración DNS, las directivas de seguridad y el enrutamiento.  
  
 **Azure Load Balancer**  
  
 Azure Load Balancer proporciona alta disponibilidad y rendimiento de red a sus aplicaciones. Se trata de un equilibrador de carga de tipo Capa 4 (TCP, UDP) que distribuye el tráfico entrante entre las instancias de servicio en buen estado de los servicios en la nube o las máquinas virtuales definidas en un conjunto de carga equilibrada. Lo usamos para equilibrar la carga de nuestros puntos de conexión en una implementación.