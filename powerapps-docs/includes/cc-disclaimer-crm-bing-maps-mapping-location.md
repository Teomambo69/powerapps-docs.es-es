---
ms.openlocfilehash: f1c11fd086a91db6dc0d0629549166bbba547dee
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67226506"
---
## <a name="mapping-functions-for-dynamics-365-customer-engagement-plan"></a>Funciones de mapa para el plan de Dynamics 365 Customer Engagement 
 El servicio de campo y la automatización de servicios de proyecto tienen funciones clave que se basan en la ubicación. Por ejemplo, la ubicación de las cuentas de servicio (que definen dónde se llevan a cabo tareas o servicios) o la ubicación de inicio y finalización de recursos (personas que realizan servicios o tareas).  Para que el sistema muestre estos elementos en un mapa o para que calcule las distancias entre los puntos, es necesario usar un servicio de mapas (en este caso, Mapas de Bing).  
  
 Este es el flujo de trabajo hacia y desde el servicio Mapas de Bing:  
  
|Desde Dynamics 365|Resultados de Mapas de Bing|Nota|  
|-----------------------|-----------------------|----------|  
|Dirección (cuenta o recurso)|Latitud y longitud de la dirección (ubicación)|Esto se conoce como "codificación geográfica" de una dirección.|  
|Conjunto de ubicaciones (latitud y longitud)|Distancia entre ubicaciones|Esto puede usarse para encontrar las rutas óptimas de los recursos o para calcular la duración de un viaje.|  
|Conjunto de ubicaciones (latitud y longitud)|Vista de mapa con las ubicaciones como anclajes en el mapa|Esto sirve para ver las cuentas y los recursos en una vista de mapa.|  
  
> [!NOTE]
>  Aparte de los datos mencionados anteriormente, ningún otro dato se envía al servicio Mapas de Bing.
