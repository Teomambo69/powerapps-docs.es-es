Al habilitar la característica Voz del cliente para Dynamics 365, cuando publique una encuesta desde esta aplicación, la definición de la encuesta se enviará a Azure y se almacenará en Azure Storage. Cuando un encuestado envía una encuesta (abriendo el vínculo de invitación a la encuesta que se le ha enviado por correo electrónico), sus respuestas se almacenan temporalmente en Azure Service Bus y, después, se recuperan y almacenan en Dynamics 365. Una vez que se han almacenado las respuestas en Dynamics 365, se eliminan en Azure.  
  
 Tenga en cuenta que, cuando se muestra una encuesta a un encuestado, es posible que se incluyan datos de Dynamics 365 como el nombre del cliente, el nombre del producto, el número del caso, etc. (dentro de elementos de la encuesta, como preguntas, respuestas, etc.). Cuando se genera un vínculo de invitación a una encuesta, estos datos de Dynamics 365 se envían desde Dynamics 365 y se almacenan en Azure SQL Database a cambio de un identificador que se usa en el vínculo de invitación a la encuesta. Este identificador se emplea para mostrar los datos de Dynamics 365 en la encuesta después de esta se abra mediante el vínculo de invitación. Los identificadores incluidos en el vínculo de la encuesta que se envía por correo electrónico a un encuestado se almacenan en el sistema de correo electrónico del encuestado.  
  
 Un administrador puede habilitar la característica Voz del cliente para Dynamics 365 instalándola como una solución en la organización de Dynamics 365. Además, un administrador puede deshabilitar la característica después desinstalando esta solución de la organización de Dynamics 365.  
  
 En las secciones siguientes, se detallan los componentes y servicios de Azure que tienen que ver con la funcionalidad Voz del cliente para Dynamics 365.  
  
 Nota: Para obtener más información sobre otras ofertas de servicios de Azure, visite el Centro de confianza de Microsoft Azure ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)).  
  
 **Cloud Services** ([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **Servicio del diseñador (rol web)**  
  
 Proporciona varios servicios web para la comunicación entre una organización de Dynamics 365 y los componentes multiempresa de Azure de Voz del cliente para Dynamics 365.  Por ejemplo, la encuestas se publican y almacenan en Azure Blob Storage.  Las respuestas de la encuesta se recuperan de una cola de Azure Service Bus y se devuelven para almacenarlos en la organización de Dynamics 365.  Todas las solicitudes se autentican con Azure Active Directory.  
  
 **Tiempo de ejecución de la encuesta (rol web)**  
  
 Esta es la aplicación web que presenta las encuestas a los encuestados.  Las respuestas de encuesta enviadas se almacenan temporalmente en una cola de Azure Service Bus hasta que un servicio asincrónico de Dynamics 365 las recupera para procesarlas.  
  
 **Procesador de respuestas (rol de trabajo)**  
  
 Este rol de trabajo es responsable de procesar las encuestas completadas sin procesar para obtener respuestas de encuesta válidas que se pueden crear en Dynamics 365.  
  
 **Procesador de inserción (rol de trabajo)**   Este rol de trabajo es responsable de procesar las respuestas de encuesta válidas y actualizarlas como registros de entidad de Dynamics 365. 
 
 **Azure Key Vault** ([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 Todos los servicios en la nube almacenan datos de configuración en Azure Key Vault.  Los datos de las organizaciones (inquilinos) se almacenan en SQL Azure.  
  
 **Azure SQL Database** ([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Voz del cliente para Dynamics 365 usa SQL Azure para almacenar lo siguiente:  
  
-   Datos canalizados  
  
-   Metadatos de encuestas  
  
-   Datos de la organización (inquilino)  
  
 **Azure Blob Storage** ([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 Las definiciones de encuestas y las respuestas parcialmente completadas (guardadas) se almacenan en Azure Blob Storage.  
  
 **Azure Content Delivery Network (CDN)** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 La solución Voz del cliente para Dynamics 365 utiliza Azure Content Delivery Network para entregar contenido estático al entorno de ejecución de la encuesta; por ejemplo, imágenes (incluidas imágenes cargadas como logotipos de clientes), JavaScript y CSS.  
  
 **Azure Active Directory** ([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 La solución Voz del cliente para Dynamics 365 utiliza el servicio Azure Active Directory para autenticar servicios web.  
  
 **Azure Service Bus** ([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 Los mensajes que se crean cuando se muestra o envía una encuesta se almacenan temporalmente en una cola de Azure Service Bus de una organización (inquilino) hasta que el rol de trabajo de Azure inserta las respuestas de la encuesta en la instancia de Dynamics 365 de una organización y las almacena como registros de entidad de Dynamics 365.
