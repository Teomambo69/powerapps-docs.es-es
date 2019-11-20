La característica Ayude a mejorar [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] envía información de uso de [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)], como detalles del sistema operativo, detalles del explorador, información específica de la aplicación de [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] y la versión de [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] del equipo en el que se instala el cliente. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] envía la información a [!INCLUDE[cc_Microsoft](cc-microsoft.md)] a través de una conexión segura con Información de la organización y se almacena en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table Storage.
  
> [!NOTE]
>  Información de la organización proporciona al administrador del sistema de una organización de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] una descripción general de cómo se utiliza la organización. El administrador del sistema puede ver los usuarios más activos, el número de solicitudes SDK que se han iniciado y el número que ven los usuarios del SDK.
  
 A continuación se muestra una lista de los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con la funcionalidad de Ayude a mejorar Unified Service Desk.  
  
> [!NOTE]
>  Para obtener más información acerca de otras ofertas de servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], consulte el [Centro de confianza de Microsoft Azure](https://azure.microsoft.com/support/trust-center/).  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/) API de REST de datos de OrgInsights (rol web)  
  
 Este rol web acepta solicitudes de los gráficos que muestran datos en Información de la organización. La API lee datos agregados de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Tables y los devuelve.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)  
  
 El Agente de supervisión (que se ejecuta en todos los equipos del grupo de escalado) recopila datos de telemetría sin procesar de una organización de [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]; estos datos se cargan en formato Bond (formato binario) en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage.  
  
 [Azure Table Storage](https://azure.microsoft.com/services/storage/tables/)  
  
 Los datos de telemetría sin procesar de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage se agregan y almacenan en Azure Table Storage, que Cloud Service lee.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 La información de la organización usa [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] Service para autenticar los servicios web.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 El Agente de supervisión crea y pone en cola los mensajes siempre que carga datos en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. La canalización de CMA selecciona estos mensajes en los datos agregados cargados.