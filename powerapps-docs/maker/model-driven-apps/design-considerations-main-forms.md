---
title: Consideraciones de diseño para formularios principales de una aplicación controlada por modelos con PowerApps | Microsoft Docs
description: Información sobre cómo diseñar formularios principales
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: a83872f4-9e36-413b-8561-41a1e5ffe5dd
caps.latest.revision: 17
ms.author: matp
manager: kvivek
ms.openlocfilehash: 68915af214b86511f7fba4bbb05ee59f598340b0
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712847"
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>Consideraciones de diseño para formularios principales de una aplicación controlada por modelos

Los formularios principales son la interfaz de usuario primaria donde los usuarios ven e interactúan con sus datos. Los formularios principales brindan la variedad más amplia de opciones y están disponibles para las aplicaciones controladas por modelos, a excepción de Dynamics 365 para teléfonos.  
  
 Uno de los principales objetivos de diseño de los formularios principales es que se diseñan una vez y se implementan en cualquier parte. El mismo formulario principal que diseña para una aplicación controlada por modelos o la aplicación web de involucración del cliente de Dynamics 365 se usa también en Dynamics 365 para Outlook y Dynamics 365 para tabletas. La ventaja de este enfoque es que no es necesario integrar los cambios en varios formularios. Sin embargo, hay varios factores importantes que se deben considerar al diseñar estos formularios.  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>Formularios personalizados para distintos grupos  
 Debido a que puede crear varios formularios principales y asignar roles de seguridad distintos a cada formulario, puede presentar distintos grupos en la organización con un formulario optimizado para el modo en que usan la aplicación. Incluso puede brindar a cada grupo distintas opciones, para que puedan elegir entre formularios diferentes. Más información: [Controlar el acceso a los formularios](control-access-forms.md)  
  
 Puede esperar que los administradores y los responsables de toma de decisiones quieran formularios optimizados para brindar una referencia rápida a los puntos de datos clave. Querrán ver más gráficos que listas y es posible que no realicen una gran cantidad de entradas de datos.  
  
 Es posible que quienes interactúan directamente con los clientes necesiten formularios adaptados a las tareas que realizan con más frecuencia. Puede que quieran formularios que permitan la entrada de datos más eficaz.  
  
 Deberá averiguar lo que quieren y necesitan las personas de su organización. Con frecuencia, se trata de un proceso iterativo donde se recopilan entradas, se prueban distintas cosas y se crean formularios que los usuarios pueden usar. Recuerde que tiene a disposición diversas herramientas y que no todo se debe hacer dentro del formulario. Use reglas de negocio, procesos de flujo de trabajo, cuadros de diálogo y flujos de proceso de negocio con los formularios para proporcionar una solución que funcione para la organización.  
  
 Deberá equilibrar esto con la cantidad de tiempo que quiere dedicar a la administración de formularios. Crear y editar formularios es relativamente sencillo pero, a medida que crea más formularios, debe administrar más.  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>Diferencias en la presentación  
 Si bien no tiene que administrar varios formularios para cada presentación, sí debe tener en cuenta cómo se pueden considerar para el formulario principal las diferencias en la presentación. Las [presentaciones del formulario principal](main-form-presentations.md) describen las distintas maneras en que se puede presentar el formulario principal. Los aspectos primarios que se deben considerar son los siguientes:  
  
- Dynamics 365 para tabletas no admite agregar recursos web de Silverlight, HTML ni de imagen a los formularios.  
  
-   El diseño de los formularios de Dynamics 365 para tabletas se genera automáticamente según el formulario principal. No hay ningún editor de formulario especial para los formularios de Dynamics 365 para tabletas. Deberá comprobar que la presentación del formulario funcione correctamente para ambos clientes.  
  
-   Si tiene scripts no compatibles que interactúan con elementos DOM encontrados en la aplicación web, dichos scripts no funcionará en los formularios de Dynamics 365 para tabletas por no están disponibles los mismos elementos DOM.  
  
- Los formularios del panel de lectura de Dynamics 365 para Outlook no permiten los scripts. La visibilidad de los elementos de formulario depende de la configuración predeterminada y no se pueden cambiar en tiempo de ejecución mediante el uso de scripts.  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>Rendimiento del formulario  
 Sin duda, los formularios que se cargan lentamente o que no responden con rapidez afectan la productividad de la aplicación y su adopción por parte del usuario. En el artículo [Optimizar el rendimiento de los formularios](optimize-form-performance.md), se brinda una serie de recomendaciones que debería tener en cuenta al diseñar formularios, para que las personalizaciones no afecten negativamente el rendimiento del formulario.  
  
### <a name="next-steps"></a>Pasos siguientes 
 [Creación y diseño de formularios](create-design-forms.md)    
 [Creación y edición de formularios de creación rápida](create-edit-quick-create-forms.md)   

 
