Al habilitar la característica Ruta de aprendizaje, permite que el contenido html estático, las imágenes y los scripts se almacenen en Red de entrega de contenido (red CDN) de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Además, todo el contenido dinámico que se muestra se almacenará en Caché en Redis de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], que se usa para el almacenamiento previo en caché desde la base de datos SQL de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Un administrador puede habilitar y deshabilitar el uso de la característica Ruta de aprendizaje dentro de una instancia de [!INCLUDE[pn_crm_online_shortest](pn-crm-online-shortest.md)] mediante Habilitar la ayuda guiada en la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 En las próximas secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con la funcionalidad Ruta de aprendizaje.  
  
> [!NOTE]
>  Para obtener más información acerca de otras ofertas de servicios de Azure, consulta el [Centro de confianza de Microsoft Azure](https://azure.microsoft.com/support/trust-center/).  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **Tiempo de ejecución de Ruta de aprendizaje (rol web)**  
  
 Esta es la aplicación web que presenta el contenido a los usuarios.  
  
 **Servicio Ruta de aprendizaje (rol de trabajo)**  
  
 El rol de trabajo es responsable de procesar los datos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Database y almacenarlos en caché en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 Ruta de aprendizaje usa SQL Database para almacenar:  
  
-   Contenido  
  
-   Metadatos de contenido  
  
-   Metadatos del sistema  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Tanto el código HTML como las imágenes, [!INCLUDE[pn_JavaScript](pn-javascript.md)] y CSS se almacenan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage.  
  
 [Red de entrega de contenido (CDN) de Azure](https://azure.microsoft.com/services/cdn/)  
  
 Ruta de aprendizaje usa la Red de entrega de contenido de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para presentar contenido estático al tiempo de ejecución de la encuesta, como HTML, imágenes, [!INCLUDE[pn_JavaScript](pn-javascript.md)] y CSS.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] Service para autenticar servicios web específicamente para el diseñador. Actualmente, el diseñador no se expone a los clientes y asociados. Por tanto, la autenticación solo se realiza dentro del dominio de [!INCLUDE[cc_Microsoft](cc-microsoft.md)].  
  
 [Azure Redis Cache](https://azure.microsoft.com/services/cache/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache para almacenar en caché contenido dinámico que presentamos a los usuarios.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/services/traffic-manager/)  
  
 Ruta de aprendizaje usa Traffic Manager para mejorar la disponibilidad de las aplicaciones importantes al supervisar los sitios y servicios externos o de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y remitir automáticamente a los usuarios a una nueva ubicación si se produce algún error.  
  
 [Azure Resource Manager](https://azure.microsoft.com/features/resource-manager/)  
  
 Ruta de aprendizaje usa [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Resource Manager para implementar CDN, Redis Cache, SQL Database y Cloud Services como grupos de recursos para que estén en un estado coherente y se puedan implementar repetidamente.