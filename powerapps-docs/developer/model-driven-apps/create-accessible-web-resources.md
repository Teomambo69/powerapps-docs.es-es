---
title: Crear recursos web accesibles (aplicaciones basadas en modelos) | Microsoft Docs
description: El tema presenta instrucciones generales y vínculos a varios recursos que pueden ayudarle a diseñar elementos de la interfaz de usuario para recursos web que sean accesibles a las personas con discapacidades.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 307269ac-674c-5b8a-fee7-767f060af15f
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5bdae4cf6754fb99f0045b17aaf1a81ab3e7e726
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753612"
---
# <a name="create-accessible-web-resources"></a>Crear recursos web accesibles

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/create-accessible-web-resources -->


Al incluir recursos web que proporcionen elementos de la interfaz de usuario en la solución, asegúrese de incluir los requisitos que permiten a las personas con discapacidades usar los recursos web.  
  
 Los elementos de la interfaz de usuario de las aplicaciones siguen estándares y prácticas recomendadas que permiten ofrecer una funcionalidad equivalente a todos los usuarios. Las personas con discapacidades pueden confiar en el uso de tecnología de asistencia (AT) como los lectores de pantalla o diversos dispositivos de entrada alternativos para interactuar con las aplicaciones.  
  
 Este tema presenta instrucciones generales y vínculos a varios recursos que pueden ayudarle a diseñar elementos de la interfaz de usuario para recursos web que sean accesibles a las personas con discapacidades.  
  
<a name="BKMK_AT"></a>   
## <a name="assistive-technology"></a>Tecnología de asistencia  
 Existen diversas aplicaciones de tecnología de asistencia (AT), como los lectores de pantalla, los terminales Braille y el software de reconocimiento de voz. Estas aplicaciones actúan como intermediario con los elementos de la interfaz de usuario para que las personas que usen la aplicación de AT puedan usar su programa.  
  
 Para las aplicaciones de Windows, las clases de automatización de la interfaz de usuario de Microsoft (UIA) proporcionan acceso mediante programación a los elementos de la interfaz de usuario. Estas clases admiten tanto las pruebas automatizadas como AT. Las aplicaciones AT pueden usar las propiedades y los elementos definidos por el desarrollador y que se exponen mediante UIA. Un desarrollador de aplicaciones de windows tiene un control considerable sobre el modo en que los elementos de la interfaz de usuario se exponen mediante UIA.  
  
 Para las aplicaciones web, determinados elementos HTML se exponen a través de Document Object Model (DOM). El explorador convierte los elementos DOM en objetos UIA con propiedades y eventos que AT puede usar para permitir al usuario usar la aplicación web. El desarrollador tiene un control limitado sobre el modo en que un explorador que utiliza UIA expone los elementos de la interfaz de usuario.  
  
<a name="BKMK_HTMLWebResources"></a>   
## <a name="accessible-html-web-resources"></a>Recursos web HTML accesibles  
 El código HTML de los recursos web lo procesa el explorador y lo pone a disposición de las aplicaciones AT.  
  
 Lo primero que hay que tener en cuenta es asegurarse de que el HTML sigue los patrones de uso esperados. Por ejemplo, puede definir un elemento HTML `div` con un evento de clic para que funcione exactamente como un elemento HTML `button`. Sin embargo, el explorador no esperará que un elemento `div` se use como botón y no expondrá las mismas propiedades y eventos a una aplicación AT.  
  
 Es importante que use los elementos HTML correctos para los tipos de interacciones que los usuarios realizarán con los recursos web. Esto se conoce como [HTML semántico](https://docs.microsoft.com/microsoft-edge/accessibility).  
  
 Sin embargo, el HTML semántico tiene sus limitaciones. Las aplicaciones web modernas normalmente incluyen controles personalizados que están compuestos por muchos elementos HTML que funcionan juntos. El contenido de las páginas que se actualiza frecuentemente de forma dinámica mediante JavaScript asincrónico resulta confuso para las aplicaciones AT que solo esperan HTML semántico. La tecnología [Accessible Rich Internet Applications (ARIA)](https://docs.microsoft.com/microsoft-edge/accessibility) proporciona una solución al ampliar HTML con atributos adicionales que comunican la semántica personalizada.  
  
 ARIA proporciona un conjunto de atributos extendidos estándar que se pueden aplicar a elementos HTML que se usan en un control, o "widget". Estos atributos describen el rol que el elemento HTML desempeña en el control. La tecnología ARIA también ofrece capacidades para mejorar la experiencia de navegación y poner en conocimiento del usuario los elementos que se pueden actualizar dinámicamente. La práctica recomendada consiste en situar ARIA en un nivel por encima del HTML semántico.  
  
 Además de incluir el soporte para AT, hay otros requisitos que tiene que tener en cuenta. Por ejemplo, ¿cómo se ajusta la interfaz de usuario cuando el usuario aumenta el tamaño del texto? ¿Requiere la interfaz de usuario que el usuario pueda distinguir colores para realizar tareas? ¿Pueden realizarse todas las acciones con el teclado? Para obtener más información, vea [Introducción a la accesibilidad web](https://docs.microsoft.com/previous-versions/windows/apps/hh452681(v=win.10)).
  
<a name="BKMK_SilverlightWebResources"></a>   
## <a name="accessible-silverlight-web-resources"></a>Recursos web de Silverlight accesibles  
 Los recursos web Silverlight se hospedan en un formulario o un recurso web HTML y la interfaz de usuario es representada por un complemento del explorador Silverlight. Silverlight es un subconjunto de Windows Presentation Framework (WPF) y por tanto el acceso mediante programación y AT se exponen utilizando UIA similar a las aplicaciones de ventanas de WPF. Para obtener más información, vea [Accesibilidad de Silverlight para desarrolladores](https://docs.microsoft.com/previous-versions/windows/).  
  
<a name="BKMK_AccessiblityTestingTools"></a>   
## <a name="accessibility-testing-tools"></a>Herramientas de pruebas de accesibilidad  
 La siguiente lista proporciona algunas herramientas de pruebas de accesibilidad disponibles públicamente:  
  
 [Visual Studio Accessibility Checker](https://msdn.microsoft.com/library/ms228004)  <!--TODO No relevant microsoft docs link-->
 Si usa Visual Studio para editar archivos de recursos web en HTML, descubrirá que existen herramientas integradas para comprobar si hay problemas relacionados con la accesibilidad. En el menú **Herramientas**, seleccione **Comprobar accesibilidad** para ver un informe que proporciona instrucciones sobre problemas relacionados con la accesibilidad.  
  
 [UI Accessibility Checker](https://acccheck.codeplex.com/)  
 UI Accessibility Checker (o AccChecker) permite a los evaluadores detectar fácilmente problemas de accesibilidad con Microsoft Active Accessibility (MSAA) y otras implementaciones de interfaz de usuario (UI) para Windows. AccChecker nació cuando se constató que las herramientas existentes de la API de automatización de Windows, como Inspect, proporcionaban información detallada sobre la implementación, pero no información acerca de si la implementación es correcta o no.  
  
 [Inspect (Inspect.exe)](https://docs.microsoft.com/windows/desktop/WinAuto/inspect-objects)  
 Inspect (Inspect.exe) es una herramienta basada en Windows que permite seleccionar cualquier elemento de la interfaz de usuario y ver los datos de accesibilidad del mismo. Puede ver propiedades de automatización de la interfaz de usuario de Microsoft y controlar patrones además de las propiedades de Microsoft Active Accessibility. Inspect también le permite probar la estructura de navegación de los elementos de automatización en el árbol de automatización de la interfaz de usuario y los objetos accesibles de la jerarquía de Microsoft Active Accessibility.  
  
 [Accessible Event Watcher (AccEvent.exe)](https://docs.microsoft.com/windows/desktop/WinAuto/accessible-event-watcher)  
 La herramienta Accessible Event Watcher (AccEvent) permite a los desarrolladores y los evaluadores validar que los elementos de la interfaz de usuario de una aplicación generan los eventos apropiados de automatización de la interfaz de usuario de Microsoft y de Microsoft Active Accessibility cuando se producen cambios en la interfaz de usuario. Los cambios en la interfaz de usuario se pueden producir cuando cambia el foco o si se invoca o selecciona un elemento de la interfaz de usuario, o se produce un cambio de estado o en una de sus propiedades.
  
<a name="BKMK_AdditionalResources"></a>   
## <a name="additional-resources"></a>Recursos adicionales  
 Los recursos siguientes proporcionan un punto de partida para definir los requisitos para crear recursos web accesibles:  
  
-   [CRM, accesibilidad y 508](https://blogs.msdn.com/b/devkeydet/archive/2013/01/29/crm-accessibility-and-508.aspx)  
  
-   [Introducción a la accesibilidad web](https://docs.microsoft.com/previous-versions/windows/apps/hh452681(v=win.10))  
  
-   [Accesibilidad en Visual Studio y ASP.NET](https://msdn.microsoft.com/library/ms228004)  <!--TODO No relevant microsoft docs link-->
  
-   [Accesibilidad de Silverlight para desarrolladores](https://docs.microsoft.com/previous-versions/windows/)  
  
-   [Información general sobre accesibilidad](https://developer.microsoft.com/windows/accessible-apps)  
  
-   [Accesibilidad - W3C](https://www.w3.org/standards/webdesign/accessibility)  
  
-   [Web Content Accessibility Guidelines (WCAG) 2.0](https://www.w3.org/TR/WCAG20/)  
  
### <a name="see-also"></a>Vea también  
 [Recursos web de página web (HTML)](webpage-html-web-resources.md)   
 [Recursos web de Silverlight (XAP)](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)<br/>   <!--TODO No relevant topic in powerapps repo-->
 [Recursos web](web-resources.md)
