---
title: Presentación de la barra de comandos o de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Los datos que definen comandos en Common Data Service se pueden mostrar en varias formas según el cliente y las diferencias en cómo se tratan algunas entidades. Necesita tener en cuenta estos factores cuando cambia comandos de la cinta de opciones o define nuevos.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 5b1d7633-ab0d-94ec-166f-f5bc1af2a657
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="command-bar-or-ribbon-presentation"></a>Presentación de la barra de comandos o la cinta de opciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/command-bar-ribbon-presentation -->

Los datos que definen comandos en Common Data Service se pueden mostrar en varias formas según el cliente y las diferencias en cómo se tratan algunas entidades. Necesita tener en cuenta estos factores cuando cambia comandos de la cinta de opciones o define nuevos.
  
<a name="BKMK_DifferentPresentations"></a>   
## <a name="different-presentations-of-commands"></a>Diferentes presentaciones de comandos  
 Hay tres formas distintas de mostrar datos de comandos.  
  
### <a name="updated-user-experience"></a>Experiencia actualizada de usuario  
 Es la presentación de la barra de comandos en toda la aplicación y para los formularios de entidades que tienen la experiencia actualizada de usuario.  
  
 ![Barra de comandos de cuentas](media/customization-account-grid-command-bar.PNG "Barra de comandos de cuentas en Dynamics 365")
  
 En esta experiencia, sólo se muestran los primeros siete comandos y todos los comandos restantes están disponibles en el menú emergente.  
  
 Las reglas de habilitación ocultarán comandos que no deben usarse.  
  
 Las subcuadrículas tiene un número limitado de controles. Solo están disponibles controles para permitir agregar registros, eliminar registros o abrir una vista de la cuadrícula. Pero estos comandos siguen estando definidos por los datos de la cinta definen y se pueden personalizar.  
  
 ![Subcuadrícula de contacto](media/customization-contract-subgrid.PNG "Subcuadrícula de contacto en Dynamics 365")  
  
 Para realizar más acciones de la lista de registros mostrados en una subcuadrícula, seleccione la opción para abrir una vista de la cuadrícula.  
  
 Para obtener más información sobre el comportamiento de los controles de subcuadrícula y cómo se pueden personalizar, consulte [Cintas de opciones de subcuadrícula](/dynamics365/customer-engagement/developer/customize-dev/ribbons-available-microsoft-dynamics-365#BKMK_SubGridRibbons).  
  
### <a name="classic-user-experience"></a>Experiencia clásica de usuario  
 Es la presentación utilizando la cinta de opciones. Se usa para listas dentro del cliente de Outlook y para los formularios de entidades que no usan actualizará la experiencia actualizada de usuario.  
  
 ![Cinta de opciones de artículo](media/customization-article-ribbon.PNG "Cinta de opciones de artículo en Dynamics 365")  
  
 En esta experiencia, hay pestañas disponibles y los grupos pueden definir la escalabilidad para mostrar todos los comandos disponibles en una pestaña cuando cambie el ancho de la pantalla.  
  
 Las reglas de habilitación pueden deshabilitar los comandos que no deben usarse de forma que sigan visibles.  
  
 Los comandos de la subcuadrícula se muestran en una pestaña contextual Herramientas de lista en la parte superior de la página cuando se selecciona la subcuadrícula.  
  
 ![Cinta de opciones de la subcuadrícula Comentarios de artículo](media/customization-article-comments-subgrid-ribbon.PNG "Cinta de opciones de la subcuadrícula Comentarios de artículo en Dynamics 365")  
  
<a name="BKMK_CRMForTablets"></a>   
### <a name="dynamics-365-for-tablets"></a>Dynamics 365 for tablets  
 Dynamics 365 for tablets muestra los comandos de forma optimizada para la experiencia táctil. Las comandos aparecen en la barra de comandos en la parte inferior derecha de la pantalla en orden de derecha a izquierda.  
  
 ![Comandos de formulario de cuenta para Dynamics 365 for tablets](media/customization-nobile-app-account-form-command.PNG "Comandos de formulario de cuenta para Dynamics 365 for tablets")  
  
> [!NOTE]
>  Los iconos configurados para comandos no se mostrarán y las etiquetas que sean demasiado largas se truncarán.  
> 
> Dynamics 365 for tablets no admite agregar elementos dinámicos a elementos `<FlyoutAnchor>` o `<SplitButton>` en tiempo de ejecución.  
  
 Los comandos de la subcuadrícula se muestran cuando el usuario pulsa y presiona el control de subcuadrícula. Estos comandos se muestran en la parte inferior izquierda de la pantalla en orden de izquierda a derecha.  
  
 ![Comandos de la subcuadrícula de actividad en Dynamics 365 for tablets](media/customization-mobile-app-activity-subgrid.PNG "Comandos de la subcuadrícula de actividad en Dynamics 365 for tablets")  
  
<a name="BKMK_CommandData"></a>   
## <a name="command-data"></a>Datos de comandos  
 A pesar de estas presentaciones tan diferentes, los datos que definen los comandos de las entidades son coherentes independientemente de cómo se muestran los comandos. Contiene definiciones de las pestañas y los grupos con escalabilidad, pero las partes visibles de estos contenedores de los controles se muestran únicamente en la interfaz clásica de usuario.  
  
 En la experiencia actualizada de usuario y Dynamics 365 for tablets, las pestañas y los grupos siguen actuando como contenedores de los controles, pero no hay ninguna indicación visual de estos contenedores y no se aplica escalabilidad.  
  
<a name="BKMK_FilteringCommands"></a>   
## <a name="filtering-commands-based-on-presentation-and-client"></a>Filtrado de comandos en función de la presentación y el cliente  
  
> [!IMPORTANT]
>  Es necesario incluir algún tipo de regla para filtrar la presentación de los comandos a menos que desee que el comando esté disponible para todos los clientes y presentaciones.  
  
 Con esta versión hay un nuevo elemento que se puede usar en las reglas de presentación y habilitación para adaptar los comandos que muestra con la presentación.  
  
 `<CommandClientTypeRule>` contiene un atributo de `Type` que se evaluará en función de la presentación. Las siguientes opciones válidas corresponden a la presentación:  
  
- `Refresh`: Experiencia actualizada de usuario  
  
- `Legacy`: Experiencia clásica de usuario  
  
- `Modern`: Dynamics 365 for tablets  
  
  Use este elemento mientras define comandos para controlar si se muestran en las distintas presentaciones.  
  
  También hay un elemento preexistente de `<CrmClientTypeRule>`, pero el atributo de `Type` del elemento solo puede distinguir entre clientes `Web` y de `Outlook`. Esta regla evaluará el cliente de Dynamics 365 for tablets para tabletas como cliente web.  
  
### <a name="see-also"></a>Vea también  
 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Cintas de opciones disponibles](/dynamics365/customer-engagement/developer/customize-dev/ribbons-available-microsoft-dynamics-365)   
 [Exportar definiciones de cinta de opciones](export-ribbon-definitions.md)   
 [Guía para programadores para realizar personalizaciones](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)
