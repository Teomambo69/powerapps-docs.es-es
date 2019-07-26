---
ms.openlocfilehash: 80997689e9d4ebca8eb4809cc3e94dab549482b5
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224723"
---
Al habilitar la característica Text Analytics, permite a las características dependientes de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] que utilicen Text Analytics API de Cognitive Services de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para proporcionar conclusiones cognitivas avanzadas. Estas características dependientes son las siguientes:  
  
-   Sugerencias de conocimiento  
  
-   Análisis de temas de casos  
  
-   Sugerencias de casos similares  
  
 Un administrador puede habilitar la característica Text Analytics en la pestaña **Configuración** > **Administración** > **Configuración del sistema** > **Versión preliminar** de la organización [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 Al habilitar la característica Text Analytics, cuando configure las sugerencias de conocimiento basadas en los análisis de textos en [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], el caso y los datos de las entidades relacionadas se envían a Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer palabras clave o frases. No se almacena ningún dato en Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Solo los campos configurados en la configuración del artículo de conocimientos se envían a Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer los términos. El administrador o el personalizador puede desactivar la configuración del artículo del conocimiento para detener las llamadas de la API a Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Además, el personalizador puede detener el uso de las sugerencias basadas en Text Analytics volviendo a las sugerencias basadas en el campo en la configuración del formulario de la entidad Caso.  
  
 Al habilitar la característica Text Analytics, al configurar los análisis de textos de casos en [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], dicho caso y los datos de las entidades relacionadas se envían a Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para determinar el tema. No se almacena ningún dato en Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Solo los campos configurados en la configuración del modelo de tema se envían a Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer los temas. El administrador o el personalizador puede desactivar el Modelo de tema para detener las llamadas de Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Al habilitar la característica Text Analytics, al configurar las sugerencias de casos similares en [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], si la opción Análisis avanzado de textos está habilitada en Regla de similitud, dicho caso y los datos de las entidades relacionadas se envían a Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para extraer palabras clave y frases. Solo los campos de texto configurados en Regla de similitud se envían a Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. No se almacena ningún dato en Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. El administrador o el personalizador puede desactivar la Regla de similitud para detener las llamadas de Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 En las siguientes secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] relacionados con las características basadas en Text Analytics.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Aplicación de API de Azure](https://azure.microsoft.com/services/app-service/api/)  
  
 La aplicación de API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] desencadena los trabajos web que leen los datos de la organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y envían dichos datos a Text Analytics API para realizar un análisis de temas. La aplicación de API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] usa los trabajos web para realizar el procesamiento de datos real en segundo plano y escribir la salida de datos en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. Los datos se almacenan temporalmente en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. Por último, una vez determinado el tema, se eliminan los datos de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage.  
  
 [Azure Scheduler](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Scheduler se utiliza para desencadenar un trabajo web de forma programada para realizar análisis de temas. Con Scheduler solo se comparte la programación de compilación del modelo de tema.  
  
 [Azure Table](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] se usa para comunicar la versión del modelo y el contexto de la organización entre la aplicación de API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] y el trabajo web.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Los trabajos web almacenan datos temporalmente en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage y los eliminan una vez que la ejecución de la canalización de la aplicación lógica ha terminado.  
  
 [Azure Text Analytics API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api)  
  
 Text Analytics API de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] se envía en función de los campos que se configuran en la búsqueda de conocimientos activa, en la configuración del modelo de tema o en la configuración de la regla de similitud. Por ejemplo, los campos de la entidad Caso, como título y descripción, además del campo Descripción en notas y actividades relacionadas, se configuran en la configuración Campo de búsqueda de conocimiento.  
  
 Búsqueda por relevancia en [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]  
  
 Puede usar la funcionalidad Búsqueda por relevancia, si se ha habilitado por un administrador, para buscar registros similares para los casos. Los campos de correspondencia de texto y de correspondencia exacta que se usan en la regla de similitud, se usan para llamar la API de Búsqueda por relevancia. Consulte el contenido técnico de Búsqueda por relevancia de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] para obtener detalles sobre la manipulación de datos.