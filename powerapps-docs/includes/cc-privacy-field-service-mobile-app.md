Al instalar y usar la aplicación móvil de [!INCLUDE[pn_fieldservice_mobile_app_long](pn-fieldservice-mobile-app-long.md)] en un dispositivo móvil, los usuarios autorizan la transmisión del id. de su organización, el id. de usuario final y el id. del dispositivo a Microsoft y a Resco.net, Inc. con el fin de prestar los servicios y comprobar que el software cuenta con la licencia requerida.  
&nbsp;<br />
Si los usuarios utilizan la aplicación móvil de [!INCLUDE[pn_fieldservice_mobile_app_long](pn-fieldservice-mobile-app-long.md)] para conectar [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] con los Servicios de [!include[](../includes/tn-glympse.md)], al instalar o usar el software autorizan la transmisión de los datos del cliente a [!include[](../includes/tn-glympse.md)] con el fin de habilitar los servicios basados en la ubicación en tiempo real. Esta característica requiere que un usuario o un administrador autorizado integre y configure la cuenta de [!include[](../includes/tn-glympse.md)] de la organización para trabajar con [!include[](../includes/pn-dynamics-crm.md)]. El uso de los Servicios de [!include[](../includes/tn-glympse.md)] está sujeto a los términos y a la declaración de privacidad vigentes para su cuenta de [!include[](../includes/tn-glympse.md)].  
&nbsp;<br />
Si los usuarios utilizan la aplicación para conectarse a [!include[](../includes/pn-microsoft-dynamics.md)] CRM (en línea) o a [!include[](../includes/pn-crm-online.md)], al instalar la aplicación, los usuarios autorizan la transmisión del id. de su organización, el id. de usuario final y el id. del dispositivo a Microsoft con el fin de habilitar las conexiones a través de varios dispositivos o de mejorar [!include[](../includes/pn-microsoft-dynamics.md)] CRM (en línea), [!include[](../includes/pn-crm-online.md)] o la aplicación.  
&nbsp;<br />
**Datos de ubicación.** Si los usuarios solicitan y habilitan características o servicios basados en la ubicación en la aplicación, esta podrá recopilar y usar los datos precisos sobre su ubicación. Los datos de ubicación precisos pueden ser datos del sistema de posición global (GPS) y datos que identifiquen los repetidores de telefonía móvil cercanos y los puntos de conexión Wi-Fi. La aplicación puede enviar los datos de ubicación a [!include[](../includes/pn-microsoft-dynamics.md)] CRM o a [!include[](../includes/pn-dynamics-crm.md)]. La aplicación puede enviar los datos de ubicación a [!include[](../includes/pn-bing-maps.md)] y a otros servicios de mapas de terceros, como Google Maps y [!include[](../includes/tn-apple.md)] Maps, un usuario designado en el teléfono del usuario para procesar los datos de ubicación del usuario en la aplicación. Los usuarios pueden deshabilitar las características o los servicios basados en la ubicación o deshabilitar el acceso de la aplicación a la ubicación del usuario desactivando el servicio de ubicación o desactivando el acceso de la aplicación al servicio de ubicación. El uso que hacen los usuarios de [!include[](../includes/pn-bing-maps.md)] se rige por las [!include[](../includes/pn-bing-maps.md)] Condiciones de uso de usuario final disponibles en [https://go.microsoft.com/?linkid=9710837](https://go.microsoft.com/?linkid=9710837) y por la [!include[](../includes/pn-bing-maps.md)] Declaración de privacidad disponible en [https://go.microsoft.com/fwlink/?LinkID=248686](https://go.microsoft.com/fwlink/?LinkID=248686). El uso que los usuarios hacen de estos servicios de mapas de terceros y la información que proporcionan en ellos están regulados por las condiciones de usuario final y las declaraciones de privacidad de esos servicios. Los usuarios deben leer atentamente esas otras condiciones de usuario final y declaraciones de privacidad.  
&nbsp;<br />
La aplicación puede incluir vínculos a otros servicios de Microsoft y de terceros, cuyas prácticas de privacidad y seguridad pueden diferir de las de [!include[](../includes/pn-microsoft-dynamics.md)] CRM o [!include[](../includes/pn-dynamics-crm.md)].  SI LOS USUARIOS ENVÍAN DATOS A OTROS SERVICIOS DE MICROSOFT O DE TERCEROS, ESOS DATOS ESTÁN REGULADOS POR SUS RESPECTIVAS DECLARACIONES DE PRIVACIDAD. Para eliminar cualquier posible duda, los datos que se comparten fuera de [!include[](../includes/pn-microsoft-dynamics.md)] CRM o de [!include[](../includes/pn-dynamics-crm.md)] no están cubiertos por los acuerdos de los usuarios de [!include[](../includes/pn-microsoft-dynamics.md)] CRM o de [!include[](../includes/pn-dynamics-crm.md)] ni por el Centro de confianza de [!include[](../includes/pn-microsoft-dynamics.md)] correspondiente. Microsoft anima a los usuarios a leer esas otras declaraciones de privacidad.  
&nbsp;<br />
Al habilitar la aplicación móvil de [!INCLUDE[pn_fieldservice_mobile_app_long](pn-fieldservice-mobile-app-long.md)] en un dispositivo móvil con las características de ubicación habilitadas, los datos de ubicación en tiempo real se enviarán a [!INCLUDE[pn_bing_maps](pn-bing-maps.md)] y se almacenarán en [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. Durante la instalación o el uso de la aplicación Field Service Mobile se pedirá a los usuarios que proporcionen permiso para el flujo de datos de ubicación en tiempo real. Para deshabilitar el flujo de datos de ubicación en tiempo real del dispositivo, el usuario debe deshabilitar las características de ubicación del dispositivo o desinstalar la aplicación.  
&nbsp;<br />
Los datos de ubicación en tiempo real enviados por la aplicación Field Service Mobile se utilizan para permitir los escenarios siguientes:  

 -  Para mostrar la ubicación de los clientes de un usuario. Los datos sobre la ubicación actual del usuario se pasan al proveedor de mapas como contexto para el mapa representado por el proveedor y mostrado en la aplicación Field Service Mobile.  

 -  Para crear y actualizar la programación de un usuario. Los datos sobre la ubicación actual del usuario se pasan a las funciones de Field Service de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] para crear y actualizar la programación de un usuario. Por ejemplo, para asignar una tarea al técnico más cercano.  
  
Además, al habilitar la aplicación Field Service Mobile en un dispositivo móvil, la información de uso de la aplicación móvil, como los errores de la aplicación, se enviará a Microsoft a través de una conexión segura a Información de la organización y se almacenará en el Almacenamiento de tablas de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
**Nota:** La Información de la organización proporciona al administrador del sistema de una organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] una descripción general de cómo se utiliza la organización. El administrador del sistema puede ver los usuarios más activos, el número de solicitudes SDK que se han iniciado y el número que ven los usuarios del SDK.  
  
A continuación se muestra una lista de los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con la funcionalidad Ayude a mejorar [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)].  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
**API de REST de datos de OrgInsights (rol web)**  
  
Este rol web acepta solicitudes de los gráficos que muestran datos en Información de la organización. La API lee datos agregados de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Tables y los devuelve.  
  
[Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)  
  
El Agente de supervisión (que se ejecuta en todos los equipos del grupo de escalado) recopila datos de telemetría sin procesar de la organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y los carga en formato Bond (formato binario) en [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)].  
  
[Azure Table Storage](https://azure.microsoft.com/services/storage/tables/)  
  
Los datos de telemetría sin procesar de [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] se agregan y almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table Storage, que Cloud Service lee.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
Información de la organización usa [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] Service para autenticar los servicios web.  
  
[Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
El Agente de supervisión crea y pone en cola los mensajes siempre que carga datos en [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]. La canalización de CMA selecciona estos mensajes para agregar los datos cargados.