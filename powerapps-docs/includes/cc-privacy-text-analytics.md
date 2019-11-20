Al habilitar la característica Análisis de texto, permite a las características dependientes de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] que aprovechen la API de análisis de textos de Cognitive Services de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para proporcionar información avanzada. Estas características dependientes son:  
  
-   Sugerencias de conocimiento  
  
-   Análisis de temas de casos  
  
-   Sugerencias de casos similares  
  
 Un administrador puede habilitar la característica Análisis de textos en **Configuración** > **Administración** > **Configuración del sistema** > pestaña **Vista previa** de la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 Al habilitar la característica Análisis de textos, cuando configure las sugerencias de conocimiento basadas en los análisis de textos en [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], el caso y los datos de las entidades relacionadas se envían a la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer palabras clave o frases. No se almacena ningún dato en la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Solo los campos configurados en la configuración del artículo del conocimiento se envían a la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer los términos. El administrador o el personalizador puede desactivar la configuración del artículo del conocimiento para detener las llamadas de la API a la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Además, el personalizador puede detener el uso de las sugerencias basadas en Análisis de textos volviendo a las sugerencias basadas en el campo en la configuración del Formulario de la entidad Caso.  
  
 Al habilitar la característica Análisis de texto, al configurar los análisis de textos de casos en [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], dicho caso y los datos de las entidades relacionadas se envían a la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para determinar el tema. No se almacena ningún dato en la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Solo los campos configurados en la Configuración del modelo de tema se envían a la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer los temas. El administrador o el personalizador puede desactivar el Modelo de tema para detener las llamadas de la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Al habilitar la característica Análisis de texto, al configurar las sugerencias de casos similares [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], si la opción Análisis avanzado de textos está habilitada en la Regla de similitud, entonces dicho caso y los datos de las entidades relacionadas se envían a la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer palabras clave y frases. Solo los campos de texto configurados en la Regla de similitud se envían a la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. No se almacena ningún dato en la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. El administrador o el personalizador puede desactivar la Regla de similitud para detener las llamadas de la API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 En las siguientes secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con las características basadas en los análisis de textos.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Aplicación de API de Azure](https://azure.microsoft.com/services/app-service/api/)  
  
 La aplicación de API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] desencadena los trabajos web que leen los datos de la organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y envían dichos datos a la API de análisis de textos para realizar un análisis de temas. Las aplicaciones de API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] usan un trabajo web para procesar los datos en segundo plano y especificar la salida de datos al Almacenamiento de blobs de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Los datos se almacenan temporalmente en el Almacenamiento de blobs [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Por último, una vez determinado el tema, se eliminan los datos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage.  
  
 [Azure Scheduler](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Scheduler se utiliza para desencadenar un trabajo web de forma programada para realizar análisis de temas. Con el programador solo se comparte la programación de compilación del modelo de tema.  
  
 [Tabla de Azure](https://azure.microsoft.com/services/storage/)  
  
 La tabla de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] se usa para comunicar la versión del modelo y el contexto de la organización entre la aplicación de API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y el trabajo web.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Los trabajos web almacenan datos temporalmente en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage y los eliminan una vez que la ejecución de la canalización de la aplicación lógica ha terminado.  
  
 [API de análisis de textos de Azure](https://www.microsoft.com/cognitive-services/text-analytics-api)  
  
 La API de análisis de textos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] se envía en función de los campos que se configuran en la búsqueda de conocimiento activa, en la configuración del modelo de tema o en la configuración de la regla de similitud. Por ejemplo, los campos de la entidad Caso, como título y descripción, además del campo Descripción en notas y actividades relacionadas, se configuran en la configuración Campo de búsqueda de conocimiento.  
  
 Búsqueda por relevancia en [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]  
  
 Puede usar Búsqueda por relevancia, si el administrador la ha habilitado para buscar registros similares para casos. Los campos de correspondencia de texto y de correspondencia exacta que se usan en la regla de similitud, se usan para llamar la API de Búsqueda por relevancia. Consulte el contenido técnico de Búsqueda por relevancia de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] para obtener detalles sobre la manipulación de datos.