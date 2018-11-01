---
title: Utilizar el explorador de soluciones en PowerApps | MicrosoftDocs
description: Aprenda cómo usar el explorador de soluciones para crear o personalizar aplicaciones
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-solution-explorer"></a>Usar el explorador de soluciones

 En el explorador de soluciones se puede navegar por una jerarquía de nodos mediante el panel de navegación en el lado izquierdo como se muestra en la captura de pantalla siguiente:  
  
 ![Solución predeterminada con entidades contraídas](media/crm-itpro-cust-defaultsolutionentitiescollapsed.PNG "Solución predeterminada con entidades contraídas")  
  
> [!NOTE]
>  Use el mouse y el teclado cuando trabaje con las herramientas de personalización en el Explorador de soluciones. Esta parte de la aplicación no está optimizada para el tacto.  
  
 Al seleccionar cada nodo, puede ver una lista de los componentes de la solución. Las acciones disponibles en la barra de comandos cambiarán según el contexto del nodo seleccionado y si la solución es la solución predeterminada o una solución administrada. Con soluciones no administradas que no sean la solución predeterminada, puede usar el comando **Agregar existente** para traer componentes de la solución que todavía no se encuentran en la solución.  
  
Con soluciones administradas no habrá comandos disponibles y verá el mensaje:  

> [!NOTE]
> No puede editar directamente componentes en una solución administrada. Si las propiedades administradas para los componentes de la solución están definidas para permitir personalizaciones, puede editarlas usando una herramienta de diseño de PowerApps o desde otra solución no administrada.    
  
 Necesitará establecer el componente de la solución en la solución predeterminada e intentar modificarlo ahí o agregarlo a otra solución no administrada que ha creado. Es posible que el componente de la solución no sea personalizable. Más información: [Propiedades administradas](solutions-overview.md#managed-properties)
  
 Muchas de las personalizaciones que deseará hacer incluyen las entidades. Puede expandir el nodo **Entidades** para mostrar una lista de todas las entidades del sistema que se pueden personalizar de alguna forma. Puede expandir aún más cada entidad para ver los componentes de soluciones que forman parte de la entidad como se indica con la entidad cuenta en la captura de pantalla siguiente:  
  
 ![Solución predeterminada que muestra la entidad de cuenta expandida](media/crm-itpro-cust-defaultsolution.PNG "Solución predeterminada que muestra la entidad de cuenta expandida")  
  
 Para obtener más información acerca de la personalización de los componentes de la solución individuales que se encuentran en el explorador de soluciones, vea los temas siguientes:  
  
-   Para las personalizaciones de entidad, relaciones de entidades, campos y mensajes, consulte [Metadatos](create-edit-metadata.md)..  
  
-   Para los formularios de entidades, consulte [Formularios](../model-driven-apps/create-design-forms.md).  
  
-   Para los procesos, consulte [Procesos](../model-driven-apps/guide-staff-through-common-tasks-processes.md)..  
  
-   Para las reglas de negocio, consulte [Reglas de negocio](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).  
