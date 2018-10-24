---
title: Procedimientos de creación de aplicaciones de Common Data Service for Apps | Microsoft Docs
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
ms.assetid: e9810433-224b-4bde-851a-e581cf5fb8a4
caps.latest.revision: 21
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1eda4b591a3296001ffa62b16e185b421a197e75
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865050"
---
# <a name="common-data-service-for-apps-supported-and-unsupported-app-building-practices"></a>Procedimientos admitidos y no admitidos en la creación de aplicaciones de Common Data Service for Apps

<!--
The way your organization works is unique. Some organizations have well-defined business processes that they apply using PowerApps apps. Others aren’t happy with their current business processes and use PowerApps to apply new data and processes to their business. Whatever situation you find yourself in, you’ll find a lot of customization capabilities in PowerApps so that it can work for your organization.  
  
 Of course you’re eager to get started, but please take a few minutes to read the content in this section. This will introduce you to important terms, give you some background about why things are done a certain way, and help you avoid potential problems in the future.  

## What is metadata and why should you care?  
 In the past, you may have customized business applications by editing the source code. This created complications because each organization had unique changes and it was very difficult, or extremely expensive, to upgrade. Then application developers started exposing application programming interfaces (APIs) so that other developers could interact with the application and add their own logic without touching the source code. This was moderately better because it means developers can extend the application without changing it. But it still requires a developer to write code.  -->
  
 Las aplicaciones empresariales modernas usan una arquitectura basada en metadatos para que los usuarios puedan crear aplicaciones sin escribir código. Los metadatos significan "datos sobre los datos" y definen la estructura de los datos almacenados en Common Data Service for Apps. Con estos metadatos, una aplicación conoce los cambios en la estructura de datos y esto le permite adaptarse a medida que la estructura de datos cambia. Dado que se conocen los metadatos, se pueden incluir funcionalidades adicionales que están vinculadas a los metadatos.  

Cambiar los componentes de Common Data Service for Apps, como entidades, vistas, campos, gráficos y paneles para compilar aplicaciones que funcionen de la manera deseada se conoce como *personalización*.  
 
Al compilar y personalizar las aplicaciones mediante las herramientas de PowerApps, se agregan o actualizan los metadatos o los datos que usan las características que dependen de los metadatos. Puesto que conocemos los tipos de datos que se usan para crear aplicaciones, podemos tener en cuenta estos datos y agregar nuevas características a su entorno de Common Data Service for Apps sin interrumpir las aplicaciones. <!-- This way you should always be able to apply an update rollup or upgrade to the latest version and enjoy the best new features.  -->

<!--  
> **Customize or Configure?**   
> Most people say they want to customize the application, so we use the word “customize” to describe changing the system to make it work the way you want. Some people prefer to use the word “configure” because it suggests that no code was required to make changes. Call it whatever you like, we just want to make it clear that you don’t need to be a developer to customize or create PowerApps apps.  -->
  
No es necesario ser desarrollador para compilar y personalizar las aplicaciones de PowerApps. Aunque PowerApps ofrece un conjunto de servicios web y API que permiten a los desarrolladores escribir código. Cuando el código se escribe con métodos admitidos, es de esperar que siga funcionando al actualizar el entorno de Common Data Service for Apps.  
  
<a name="BKMK_SupportedCust"></a>   
## <a name="what-kinds-of-customizations-are-supported"></a>¿Qué tipos de personalizaciones se admiten?  
 Esperamos que pueda hacer la mayor parte de la compilación y personalización de aplicaciones con las herramientas de PowerApps disponibles. Si las herramientas de personalización no satisfacen sus necesidades, puede instalar una solución proporcionada por un tercero o contratar un desarrollador que programe la aplicación. Si tiene que invertir en una solución que requiere código, debe asegurarse de que el código se escribe únicamente con las API admitidas. Esto ayuda a proteger su inversión tanto en las aplicaciones como en las soluciones que obtenga.  
  
 Los desarrolladores que deseen extender las aplicaciones de PowerApps tienen la responsabilidad de seguir las reglas y procedimientos recomendados que se documentan en el SDK: [Prácticas recomendadas para desarrollar con Dynamics 365 Customer Engagement](https://docs.microsoft.com/dynamics365/customer-engagement/developer/best-practices-sdk). El SDK documenta las API disponibles para los desarrolladores y ofrece instrucciones sobre cómo optimizar su uso. Microsoft solo admite las API y los procedimientos que se documentan en el SDK. Es posible que en Internet encuentre información que describe cómo resolver un problema, pero si no aprovecha las API documentadas en el SDK, no es compatible con Microsoft. Antes de permitir que un desarrollador aplique un cambio, debe comprobar si usa métodos admitidos.  
  
 Si los desarrolladores usan las API y los procedimientos recomendados descritos en el SDK, podemos comprobar con seguridad si los cambios realizados en Common Data Service for Apps tienen la posibilidad de interrumpir las personalizaciones existentes. Nuestro objetivo es que las personalizaciones de código escritas mediante métodos admitidos sigan funcionando cuando se publican nuevas versiones o actualizaciones de Common Data Service for Apps. La ventaja es que puede actualizarse a nuevas versiones con características mejoradas sin que los desarrolladores tengan que cambiar el código cada vez.  
  
 Si se detecta que un cambio en una nueva versión de Common Data Service for Apps va a hacer que se interrumpa una personalización admitida, documentaremos lo que resulta afectado y cómo los usuarios pueden cambiar el código para resolverlo.  
  
<a name="BKMK_Unsupported"></a>   
## <a name="what-kinds-of-customizations-arent-supported"></a>¿Qué tipos de personalizaciones no se admiten?  
 Solo porque determinadas API y prácticas de programación no se admitan en Microsoft no significa que no funcionen. <!--  “Unsupported by Microsoft” means exactly what it says: you can’t get support about these APIs or programming practices from Microsoft. We don’t test them and we don’t know if something we change will break them. We can’t predict what will happen if someone changes code in our application.  --> Los desarrolladores que usan API y prácticas de programación no admitidas asumen la responsabilidad del soporte técnico de su código. Tienen que probar el código para asegurarse de que funciona.  
  
 Si opta por usar personalizaciones no admitidas en su entorno de Common Data Service for Apps, debe asegurarse de documentar lo que se ha hecho y tener una estrategia para quitar esas personalizaciones antes de ponerse en contacto con el soporte técnico de Microsoft. Si necesita ayuda con personalizaciones no admitidas, póngase en contacto con el desarrollador o la organización que prepara las personalizaciones.  
  
<a name="BKMK_CommonUnsupportedCustomizations"></a>   
### <a name="common-unsupported-customization-practices"></a>Prácticas de personalización comunes no admitidas  
 Esta es una lista de prácticas de personalización comunes que no se admiten. La lista no está completa. Más información: [Extensiones admitidas para Dynamics 365: Personalizaciones no admitidas](https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions#Unsupported). 
 
**Interacción con los elementos de Document Object Model (DOM) de aplicación web con JavaScript**  
 Las bibliotecas de JavaScript usadas en cualquier lugar de la aplicación solo deben interactuar con las API documentadas. Cuando los desarrolladores de JavaScript trabajan con aplicaciones, obtienen acceso frecuente a elementos DOM mediante nombres específicos. Dado que las aplicaciones de PowerApps son aplicaciones web, estas técnicas funcionan, pero es probable que se interrumpan durante una actualización porque los nombres de los elementos a los que hacen referencia estén sujetos a cambios en cualquier momento. Nos reservamos el derecho a realizar los cambios necesarios en la aplicación y esto a menudo significa cambiar la forma en que se construye la página. Agregar los cambios que dependen de la estructura actual de la página significa que deberá invertir en pruebas y, quizás, cambiar el código personalizado en estos scripts cada vez que aplique una actualización a la aplicación.  
  
 jQuery es una biblioteca muy común que usan los desarrolladores de JavaScript. La mayor ventaja de usar jQuery es que simplifica la capacidad de un desarrollador para tener acceso a elementos DOM y crearlos, que es exactamente lo que no admitimos en las páginas de aplicación de Common Data Service for Apps. jQuery se recomienda cuando los desarrolladores crean interfaces de usuario personalizadas con recursos web HTML; aunque en las páginas de aplicación de PowerApps, las API admitidas no requieren el uso de jQuery.  
  
 **Uso de objetos o métodos internos no documentados mediante JavaScript**  
Common Data Service for Apps emplea muchos objetos de JavaScript en las páginas. Un desarrollador de JavaScript puede detectar estos objetos mediante la depuración de una página y, luego, obtener acceso a estos objetos y reutilizarlos. Nos reservamos el derecho a realizar los cambios necesarios en estos objetos, lo que incluye eliminarlos o cambiar los nombres de los métodos. Si un script hace referencia a estos objetos, el script se interrumpirá si no se encuentran dichos objetos.  <a name="BKMK_Metadata"></a>   
 
<a name="BKMK_CombineCustomizations"></a>   
## <a name="combine-customization-capabilities"></a>Combinación de funcionalidades de personalización  
 En los temas que se encuentran en estas secciones se describen las funcionalidades individuales de personalización con una profundidad considerable. Pero es importante tener en cuenta que las soluciones para satisfacer sus requisitos empresariales con frecuencia usarán una de las funcionalidades junto con una o varias otras funcionalidades.  
  
<a name="BKMK_ChooseTheRightCustomization"></a>   
### <a name="choose-the-right-customization-capability-for-the-job"></a>Selección de la funcionalidad de personalización adecuada para el trabajo  
 Con todas las distintas funcionalidades de personalización disponibles en PowerApps, resulta fácil familiarizarse con una de ellas y usarla para resolver todos los problemas. Cuando evalúe los problemas empresariales que quiere resolver, piense en el resultado final que quiere conseguir y, luego, retroceda para saber cómo puede llegar ahí.  
 
<a name="BKMK_changesinperformance"></a>   
## <a name="changes-that-affect-common-data-service-for-apps-environment-performance"></a>Cambios que afectan al rendimiento del entorno de Common Data Service for Apps  
 La importación de soluciones y la aplicación de personalizaciones que cambian los metadatos pueden afectar al rendimiento del entorno de Common Data Service for Apps. Las acciones que pueden interferir con el funcionamiento normal del sistema son:  
  
-   Agregar, quitar o cambiar entidades, claves alternativas, atributos o relaciones.   
-   Importar soluciones
  
-   Publicar personalizaciones 
  
Si va a aplicar estos cambios a un sistema de producción, se recomienda que programe estas operaciones cuando resulte menos perjudicial para los usuarios.   
  
  
## <a name="next-steps"></a>Pasos siguientes  
[¿Cuáles son las aplicaciones controladas por modelos en PowerApps?](../../maker/model-driven-apps/model-driven-app-overview.md)

