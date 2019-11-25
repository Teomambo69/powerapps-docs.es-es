---
title: Prácticas de creación de aplicaciones de Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: e2dd81bca0ab5805d88f5db0aff9a1f83c8d87ac
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749571"
---
# <a name="common-data-service-supported-and-unsupported-app-building-practices"></a>Prácticas de creación de aplicaciones compatibles e incompatibles con Common Data Service

<!--
The way your organization works is unique. Some organizations have well-defined business processes that they apply using PowerApps apps. Others aren’t happy with their current business processes and use PowerApps to apply new data and processes to their business. Whatever situation you find yourself in, you’ll find a lot of customization capabilities in PowerApps so that it can work for your organization.  
  
 Of course you’re eager to get started, but please take a few minutes to read the content in this section. This will introduce you to important terms, give you some background about why things are done a certain way, and help you avoid potential problems in the future.  

## What is metadata and why should you care?  
 In the past, you may have customized business applications by editing the source code. This created complications because each organization had unique changes and it was very difficult, or extremely expensive, to upgrade. Then application developers started exposing application programming interfaces (APIs) so that other developers could interact with the application and add their own logic without touching the source code. This was moderately better because it means developers can extend the application without changing it. But it still requires a developer to write code.  -->
  
 Las aplicaciones empresariales modernas usan una arquitectura controlada por metadatos para que la gente pueda crear aplicaciones sin escribir código. Metadatos significa "datos acerca de datos" y define la estructura de los datos almacenados en Common Data Service. Con estos metadatos, una aplicación sabe los cambios en la estructura de datos, lo que habilita la aplicación para adaptarse a los cambios en la estructura de datos. Al saber los metadatos, se pueden incluir capacidades adicionales vinculadas a los metadatos.  

Cambiar los componentes de Common Data Service, como entidades, vistas, campos, gráficos, y paneles para crear aplicaciones que funcionan del modo que desee se denomina *personalización*.  
 
Al crear y personalizar sus aplicaciones mediante las herramientas de PowerApps, está agregando o actualizando los metadatos o los datos que usan las características que dependen de los metadatos. Puesto que conocemos las clases de datos usados para crear aplicaciones, podemos tener en cuenta estos datos y agregar nuevas características a su entorno de Common Data Service sin interrumpir sus aplicaciones. <!-- This way you should always be able to apply an update rollup or upgrade to the latest version and enjoy the best new features.  -->

<!--  
> **Customize or Configure?**   
> Most people say they want to customize the application, so we use the word “customize” to describe changing the system to make it work the way you want. Some people prefer to use the word “configure” because it suggests that no code was required to make changes. Call it whatever you like, we just want to make it clear that you don’t need to be a developer to customize or create PowerApps apps.  -->
  
No es necesario que sea un desarrollador para crear y personalizar aplicaciones de PowerApps. Sin embargo, PowerApps proporcionan un conjunto de servicios web y API que permiten a los desarrolladores escribir código. Cuando el código se escribe mediante métodos compatibles puede esperar que siga funcionando cuando se actualiza el entorno de Common Data Service.  
  
<a name="BKMK_SupportedCust"></a>   
## <a name="what-kinds-of-customizations-are-supported"></a>¿Que tipos de personalizaciones se admiten?  
 Contamos con poder realizar la mayoría de la creación y personalización de aplicaciones mediante las herramientas disponibles de PowerApps. Si las herramientas de personalización no satisfacen sus necesidades, puede instalar una solución de un tercero o contratar a un desarrollador para la codificación de las aplicaciones. Si necesita invertir en una solución que requiere código, debe asegurarse de que el código se escribió con solo API admitidas. Esto ayuda a proteger su inversión en ambas aplicaciones y cualquier solución que obtenga.  
  
 Los programadores que extiendan PowerApps tienen la responsabilidad de seguir las reglas y recomendaciones documentadas [aquí](/powerapps/developer/common-data-service/best-practices/). Microsoft admite solo las API y prácticas documentadas en el SDK. Puede encontrar algo en Internet que describa cómo puede resolver un problema, pero si no usa las API documentadas en el SDK, no es compatible con Microsoft. Antes de que haga que un desarrollador aplique un cambio debe comprobar si usa métodos compatibles.  
  
 Si los programadores usan API y recomendaciones descritas en el SDK podemos estar seguros de comprobar si los cambios que realizamos en Common Data Service tienen potencial para cancelar las personalizaciones existentes. Nuestro objetivo es que las personalizaciones de código escritas con métodos compatibles continuarán funcionando cuando las nuevas versiones o actualizaciones de Common Data Service se publiquen. Es beneficioso porque puede actualizar a las nuevas versiones con las características mejoradas sin contar con programadores que cambien el código cada vez.  
  
 Si detectamos que un cambio en una nueva versión de Common Data Service provocará que una personalización compatible se cancele, documentaremos cómo afecta e indicaremos cómo cambiar el código para corregirlo.  
  
<a name="BKMK_Unsupported"></a>   
## <a name="what-kinds-of-customizations-arent-supported"></a>¿Que tipos de personalizaciones no se admiten?  
 Solo con que determinadas API y prácticas de programación no sean compatibles con Microsoft no significa que no funcionen. <!--  “Unsupported by Microsoft” means exactly what it says: you can’t get support about these APIs or programming practices from Microsoft. We don’t test them and we don’t know if something we change will break them. We can’t predict what will happen if someone changes code in our application.  -->    El programador que usa API y prácticas de programación no admitidas asume la responsabilidad de dar soporte a su código. Deberán probar el código para asegurarse de que funciona.  
  
 Si elige usar personalizaciones no compatibles en el entorno de Common Data Service debe asegurarse de documentar lo que hace y de tener una estrategia para quitar las personalizaciones antes ponerse en contacto con el soporte técnico de Microsoft. Si necesita ayuda con personalizaciones no admitidas, póngase en contacto con el programador o la organización que las preparó.  
  
<a name="BKMK_CommonUnsupportedCustomizations"></a>   
### <a name="common-unsupported-customization-practices"></a>Prácticas de personalización comunes no admitidas  
 La siguiente es una lista de prácticas de personalización habituales que no son compatibles. No se trata de una lista completa. Más información: [Extensiones compatibles para Dynamics 365: Personalizaciones no admitidas](https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions#Unsupported). 
 
**Interactuar con los elementos de Document Object Model (DOM) de la aplicación web mediante JavaScript**  
 Cualquier biblioteca de JavaScript usada en cualquier lugar de la aplicación solo debe interactuar con API documentadas. Cuando los desarrolladores de JavaScript trabajan con aplicaciones que acceden con frecuencia a elementos DOM mediante nombres específicos. Puesto que las aplicaciones PowerApps son aplicaciones web, estas técnicas funcionan, pero es probable que se cancelen durante una actualización porque los nombres de los elementos a los que hacen referencia están sujetos a modificaciones en cualquier momento. Nos reservamos la derecha de realizar los cambios necesarios en la aplicación, lo que frecuentemente implica cambiar cómo se genera a la página. Agregar cualquier cambio que dependa de la estructura actual de la página significa que deberá invertir en probar y quizás en cambiar el código personalizado en estos scripts cada vez que aplique una actualización a la aplicación.  
  
 jQuery es una biblioteca muy común usada por los desarrolladores de JavaScript. El mayor beneficio de usar jQuery es que facilita a los desarrolladores el acceso y la creación de elementos DOM, que es exactamente lo que no se admite en las páginas de la aplicación Common Data Service. jQuery se recomienda cuando los desarrolladores están creando interfaces de usuario personalizadas con recursos web HTML, pero en las páginas de la aplicación PowerApps, las API admitidas no requieren el uso de jQuery.  
  
 **Usar objetos internos no documentados o métodos mediante JavaScript**  
Common Data Service usa muchos objetos JavaScript dentro de las páginas. Un desarrollador de JavaScript puede descubrir estos objetos depurando una página y luego accediendo y reutilizando estos objetos. Nos reservamos el derecho de realizar los cambios necesarios en estos objetos, incluido eliminarlos o cambiar los nombres de los métodos. Si un script hace referencia a estos objetos, el script se interrumpirá si no se encuentran.  <a name="BKMK_Metadata"></a>   
 
<a name="BKMK_CombineCustomizations"></a>   
## <a name="combine-customization-capabilities"></a>Combinar las capacidades de personalización  
 Los temas de estas secciones describen las capacidades de personalización individuales con bastante profundidad. Pero es importante tener presente que las soluciones para satisfacer sus requisitos empresariales con frecuencia usarán una de las capacidades junto con una o varias otras funciones.  
  
<a name="BKMK_ChooseTheRightCustomization"></a>   
### <a name="choose-the-right-customization-capability-for-the-job"></a>Elegir la característica de personalización correcta para el trabajo  
 Con todas las diferentes funciones de personalización disponibles en PowerApps es fácil familiarizarse con una de ellas e intentar utilizarla para resolver cada problema. Al evaluar los problemas empresariales que desee resolver, piense en el resultado final que desea lograr y revise el procedimiento para ver cómo puede conseguirlo.  
 
<a name="BKMK_changesinperformance"></a>   
## <a name="changes-that-affect-common-data-service-environment-performance"></a>Cambios que afectan al rendimiento del entorno de Common Data Service  
 La importación de soluciones y la aplicación de personalizaciones que cambian metadatos puede afectar al rendimiento del entorno de Common Data Service. Las acciones que pueden interferir en el funcionamiento normal del sistema incluyen:  
  
-   Agregar, eliminar, o cambiar entidades, claves alternativas, atributos, o relaciones.   
-   Importar soluciones
  
-   Publicando personalizaciones 
  
Si está aplicando estos cambios a un sistema de producción, se recomienda programar estas operaciones cuando sea menos posible perturbador para los usuarios.   
  
  
## <a name="next-steps"></a>Pasos siguientes  
[¿Qué son las aplicaciones controladas por modelos en PowerApps?](../../maker/model-driven-apps/model-driven-app-overview.md)

