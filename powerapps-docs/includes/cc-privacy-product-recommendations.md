Si se habilita la característica Recomendaciones de productos, al crear un modelo de recomendación desde [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], los datos históricos de transacciones basados en las entidades Datos de la cesta configuradas y el filtro se envían a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], se procesan en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], se almacenan temporalmente en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage y finalmente se envían a la API de recomendaciones de Azure para crear el modelo de aprendizaje automático del equipo. Una vez creado el modelo con la API de recomendaciones de Azure, los datos se eliminan de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage. Tenga en cuenta que solo los id. (id. de la cuenta, id. del producto, id. de la transacción) se enviarán a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para crear el modelo de recomendación.

Un administrador puede habilitar la característica Recomendaciones de productos en **Configuración** &gt; **Administración** &gt; **Configuración del sistema** &gt; pestaña **Vista previa** de la organización de [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]. Los datos se envían a la API de recomendaciones de Azure solo cuando se crea un modelo de recomendación. El administrador del sistema tiene la opción de eliminar el modelo existente para eliminar los datos compartidos con la API de recomendaciones de Azure. Además, el administrador del sistema puede eliminar la conexión a la API de recomendaciones de Azure para dejar de crear modelos de recomendación en el futuro.

Los componentes y los servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con las Recomendaciones de productos se detallan en las siguientes secciones.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Aplicaciones lógicas de Azure](https://azure.microsoft.com/services/app-service/logic/)

Proporciona la canalización de datos orquestada para sincronizar el catálogo de productos y los datos de transacciones con la API de recomendaciones para crear la versión del modelo de recomendación. Esta canalización se ejecuta como servicio multiempresa con varias aplicaciones API para la comunicación entre una organización de Dynamics 365 y la API de recomendaciones. Las aplicaciones lógicas se desencadenan desde [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] con un contexto mínimo, como el identificador de versión de modelo y la dirección URL de la organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. 

[Aplicaciones de API de Azure](https://azure.microsoft.com/services/app-service/api/)

Estas son las aplicaciones web que desencadenan los trabajos web que leen los datos de la organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y envían datos a la API de recomendaciones para crear el modelo de recomendación. Hay 3 aplicaciones de API y los trabajos web correspondientes: una para leer datos de productos, una para leer datos de transacciones y otra para generar un modelo de recomendación. Las aplicaciones de API usan un trabajo web para hacer el procesamiento real de datos en segundo plano y especificar la salida de datos al Almacenamiento de blobs de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Los datos se almacenan temporalmente en el Almacenamiento de blobs [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Por último, una vez creado el modelo se eliminan los datos del Almacenamiento de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].

[Tabla de Azure](https://azure.microsoft.com/services/storage/tables/)

La tabla de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] se usa para comunicar la versión del modelo y el contexto de la organización entre la aplicación de API y un trabajo web.

[Azure Blob Storage](https://azure.microsoft.com/services/storage/) 

Los trabajos web almacenan temporalmente los datos en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage; estos se eliminan una vez que la ejecución de la canalización de la aplicación lógica ha terminado.

[API de recomendaciones de Azure](https://www.microsoft.com/cognitive-services/en-us/recommendations-api) La API de recomendaciones de Azure se envía con los datos mínimos de id. del producto, id. de la transacción e id. de la cuenta para crear el modelo de recomendación. Los datos se almacenarán con el servicio de la API de recomendaciones hasta que exista una versión del modelo correspondiente.
