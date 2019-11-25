---
title: Consideraciones de diseño para formularios principales de aplicaciones controladas por modelos con PowerApps | MicrosoftDocs
description: Aprenda a diseñar formularios principales
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0af7158c1734c0a73fc6658ee15f865e3d516676
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703707"
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>Consideraciones de diseño para formularios principales de aplicaciones controladas por modelos

Los formularios principales son la interfaz de usuario principal donde los usuarios ven y interactúan con los datos. Los formularios principales proporcionan el rango de opciones más amplio y están disponibles para aplicaciones controladas por modelos, a excepción de Dynamics 365 for phones.  
  
 Uno de los objetivos principales del diseño de formularios principales es que se diseñan una vez y se implementan en cualquier ubicación. El mismo formulario principal que diseña para una aplicación basada en modelos también se usa en Dynamics 365 for Outlook y Dynamics 365 para tabletas. La ventaja de este método es que no es necesario integrar cambios en formularios diferentes. No obstante, existen varios factores importantes a considerar en el diseño de estos formularios.  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>Formularios personalizados para distintos grupos  
 Debido a la posibilidad de crear varios formularios principales y asignar distintos roles de seguridad a cada formulario, puede presentar a los grupos distintos de su organización un formulario optimizado según el uso que hagan de la aplicación. Incluso puede proporcionar a cada grupo distintas opciones de modo que tengan diferentes formularios para elegir. Más información: [Controlar el acceso a los formularios](control-access-forms.md)  
  
 Puede prever que los administradores y responsables de la toma de decisiones deseen formularios optimizados para proporcionar una referencia rápida a los puntos de datos principales. Podrán ver gráficos más que las listas y es posible que no introduzcan una gran cantidad de datos.  
  
 Las personas que interactúan directamente con los clientes pueden necesitar formularios adaptados a las tareas que realizan con más frecuencia. Es posible que deseen que los formularios permitan una entrada de datos más eficaz.  
  
 Necesitará averiguar las personas de su organización que los desean y necesitan. Este suele ser un proceso repetitivo donde se recopila la entrada, se intentan distintas acciones y se compilan formularios para los usuarios. Tenga en cuenta que tiene una variedad de herramientas disponibles y que no todo se tiene que realizar en el formulario. Use las reglas de negocio, los procesos de flujo de trabajo, los diálogos y los flujos de procesos de negocio así como los formularios para proporcionar una solución que funcione para su organización.  
  
 Tendrá que equilibrar esto con el tiempo que desee invertir administrando formularios. Crear y editar formularios es relativamente fácil, pero si crea más formularios, tiene que administrar más formularios.  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>Diferencias de presentación  
 Aunque no es necesario administrar formularios múltiples para cada presentación, debe considerar la forma que tomarán de las diferencias en la presentación en el formulario principal. [Presentaciones de formularios principales](main-form-presentations.md) describe las distintas formas en que se puede presentar el formulario principal. Los factores principales a tener en cuenta son:  
  
- Dynamics 365 for tablets no permite agregar recursos web de imagen, HTML o Silverlight a formularios.  
  
-   El diseño de formularios de Dynamics 365 for tablets se genera automáticamente en función del formulario principal. No hay ningún editor de formularios especial para formularios de Dynamics 365 for tablets. Debe comprobar que la presentación de formularios funcione correctamente para los clientes.  
  
-   Si tiene scripts incompatibles que interactúan con los elementos DOM encontrados en la aplicación web, dichos scripts no funcionarán en los formularios de Dynamics 365 for tablets porque los mismos elementos DOM no están disponibles.  
  
- Los formularios del panel de lectura de Dynamics 365 for Outlook no permiten el uso de scripts. La visibilidad de elementos de formulario depende de la configuración predeterminada y no se puede cambiar en tiempo de ejecución mediante scripts.  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>Rendimiento de los formularios  
 Los formularios que se cargan lentamente o que no responden rápidamente afectarán a la productividad y la adopción por parte del usuario de la aplicación. [Optimizar el rendimiento del formulario](optimize-form-performance.md) ofrece varias recomendaciones que debe tener en cuenta al diseñar formularios para que las personalizaciones no afecten negativamente al rendimiento del formulario.  
  
### <a name="next-steps"></a>Pasos siguientes 
 [Crear y diseñar formularios](create-design-forms.md)    
 [Crear y editar formularios de creación rápida](create-edit-quick-create-forms.md)   

 
