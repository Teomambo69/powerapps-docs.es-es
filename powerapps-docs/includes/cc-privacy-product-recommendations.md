---
ms.openlocfilehash: 1cdcb40245aae9a23ecb6d3392e412f8a60b95ba
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212310"
---
Al habilitar la característica Recomendaciones de producto, si compila un modelo de recomendación desde [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], los datos de transacción históricos basados en las entidades de datos de la cesta configuradas y su filtro se enviarán a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], se procesarán en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], se almacenarán temporalmente en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage y se enviarán finalmente a Azure Recommendations API para compilar el modelo de aprendizaje automático. Una vez compilado el modelo con Azure Recommendations API, los datos se eliminan de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage. Tenga en cuenta que solo se envían los identificadores (identificador de cuenta, identificador de producto e identificador de transacción) a [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] para compilar el modelo de recomendación.

Un administrador puede habilitar la característica Recomendaciones de producto en la pestaña **Configuración** &gt; **Administración** &gt; **Configuración del sistema** &gt; **Versión preliminar** de la organización [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]. Los datos se envían a Azure Recommendations API solo cuando se compila un modelo de recomendación. El administrador del sistema tiene la opción de eliminar el modelo existente para eliminar los datos compartidos con Azure Recommendations API. Además, el administrador del sistema puede eliminar la conexión a Azure Recommendations API para detener la compilación de cualquier modelo de recomendación en el futuro.

En las siguientes secciones se detallan los componentes y servicios de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que intervienen en las recomendaciones de producto.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure Logic Apps](https://azure.microsoft.com/services/app-service/logic/)

Este servicio proporciona la canalización de datos orquestada para sincronizar el catálogo de productos y los datos de transacciones con Recommendations API a fin de compilar la versión del modelo de recomendación. Esta canalización se ejecuta como un servicio multiinquilino con varias aplicaciones de API para la comunicación entre una organización de Dynamics 365 y Recommendations API. Las aplicaciones lógicas se desencadenan desde [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] con un contexto mínimo, como el identificador de versión de modelo y la dirección URL de la organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. 

[Azure API Apps](https://azure.microsoft.com/services/app-service/api/)

Son las aplicaciones web que desencadenan los trabajos web que leen los datos de la organización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] y envían los datos a Recommendations API para compilar el modelo de recomendación. Hay tres aplicaciones de API y los trabajos web correspondientes: una para la lectura de datos de productos, otra para la lectura de datos de transacción y una última para la compilación de un modelo de recomendación. Las aplicaciones de API usan los trabajos web para realizar el procesamiento de datos reales en segundo plano y escribir la salida de datos en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. Los datos se almacenan temporalmente en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. Por último, los datos se eliminan de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage una vez que se ha compilado el modelo.

[Azure Table](https://azure.microsoft.com/services/storage/tables/)

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table se usa para comunicar la versión del modelo y el contexto de la organización entre la aplicación de API y el trabajo web.

[Azure Blob Storage](https://azure.microsoft.com/services/storage/) 

Los trabajos web almacenan los datos temporalmente en [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage y se eliminan una vez que la canalización de aplicación lógica ha terminado de ejecutarse.

[Azure Recommendations API](https://www.microsoft.com/cognitive-services/en-us/recommendations-api) Azure Recommendations API se envía con unos datos mínimos (identificadores de producto, identificadores de transacción e identificadores de cuenta) para compilar el modelo de recomendación. Los datos se almacenan con el servicio Recommendations API hasta que existe la versión correspondiente del modelo.
