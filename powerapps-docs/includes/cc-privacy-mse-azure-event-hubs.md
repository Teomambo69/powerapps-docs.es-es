---
ms.openlocfilehash: 29226cfe8ab5c0ad01b785cfdaeec2e12a230dd7
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225341"
---
Al habilitar la conexión de Social Engagement con [Azure Event Hubs](https://azure.microsoft.com/documentation/articles/event-hubs-overview/), permitirá que los datos sociales se transmitan a centros de eventos mediante reglas de automatización. Azure Event Hubs almacena los datos sociales transmitidos desde Social Engagement durante un [período de tiempo configurado previamente](https://azure.microsoft.com/documentation/articles/event-hubs-availability-and-support-faq/), y cualquier aplicación que puede escuchar en el centro de eventos podrá acceder a estos datos, almacenarlos o procesarlos.  
  
 Tenga en cuenta que los datos sociales enviados desde Social Engagement incluyen información relativa a la publicación social (autor y texto), así como información enriquecida como idioma, ubicación, opiniones, etiquetas, etc. Para obtener información detallada sobre el contenido de una publicación social enviada a centros de eventos, vea la [definición de esquema JSON](http://go.microsoft.com/fwlink/p/?LinkId=786643).