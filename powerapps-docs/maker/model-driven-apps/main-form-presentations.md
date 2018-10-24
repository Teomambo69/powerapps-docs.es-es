---
title: Presentaciones de formularios principales de aplicaciones basadas en modelos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo aparecen los formularios principales cuando se muestran en distintos dispositivos.
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
ms.assetid: da3ac59a-5413-46cb-b355-1987e42e3853
caps.latest.revision: 35
ms.author: matp
manager: kvivek
ms.openlocfilehash: b8dee40f6dbeba62128434b3eb122add9cb0b373
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698941"
---
# <a name="how-model-driven-app-main-forms-appear-on-different-devices"></a>Cómo aparecen los formularios principales de aplicaciones basadas en modelos en distintos dispositivos

El formulario principal se usa en todos los clientes de aplicación basada en modelos. Este formulario proporciona una experiencia de usuario coherente si alguien usa un explorador web, Dynamics 365 para teléfonos, Dynamics 365 para tabletas o Dynamics 365 para Outlook.  
  
<a name="BKMK_MainFormPresentations"></a>   
## <a name="main-forms"></a>Formularios principales  
 Cualquier formulario principal que exista para una entidad se puede presentar de forma diferente en función de los factores de la siguiente tabla. Cuando diseñe un formulario principal, considere cómo funciona en cada presentación distinta.  
  
|Presentación|Descripción|  
|------------------|-----------------|  
|**Actualizado**|Para las [Entidades actualizadas y entidades clásicas](create-design-forms.md#updated-versus-classic-entities) y cualquier entidad personalizada de Dynamics 365 (en línea) y Dynamics 365 local, el formulario actualizado proporciona una nueva experiencia de usuario. Estos formularios tienen el novísimo diseño de la barra de comandos y permiten usar características adicionales como el guardado automático y los flujos de procesos de negocio.|  
|**Dynamics 365 para tabletas**| Dynamics 365 para tabletas muestra el contenido del formulario principal de una forma optimizada para tabletas.|  
|**Dynamics 365 para teléfonos**| Dynamics 365 para teléfonos muestra el contenido del formulario principal de una forma optimizada para teléfonos.|  
|**Clásico**|Estos formularios son para las entidades que no se han actualizado. Usan la cinta de opciones en lugar de la barra de comandos y el panel de navegación del lado izquierdo del formulario.<br /><br /> Estos formularios tienen un diseño de dos columnas.|  
  
<a name="BKMK_MainFormComponentsForUpdatedEntities"></a>   
## <a name="updated-forms"></a>Formularios actualizados  
 Este diagrama representa componentes comunes que se encuentran en formularios de entidad actualizados.  
  
 ![Diagrama que muestra la estructura del formulario de entidad actualizado en Dynamics 365](media/updated-form-diagram.png "Diagrama que muestra la estructura del formulario de entidad actualizado en Dynamics 365")  
  
 Para las entidades actualizadas, el diseño del formulario funciona con una gran variedad de visualizaciones y tamaños de ventana. A medida que el ancho de la ventana disminuye, las columnas de la pestaña bajan para que pueda desplazarse y trabajar con ellas en lugar de comprimirse o requerir que se desplace a la derecha.  
  
 En la tabla siguiente se resumen los componentes disponibles en el formulario principal para las entidades actualizadas.  
  
|Componente|Resumen|  
|---------------|-------------|  
|**Barra de navegación**|Usa los datos del mapa del sitio para proporcionar la capacidad de desplazarse a diferentes áreas de la aplicación.<br /><br /> El panel de navegación usado en los formularios clásicos no se incluye en el formulario actualizado. En el contexto de un registro, la barra de navegación proporciona acceso a las vistas de registros relacionados. En lugar de navegar hasta los registros relacionados con el panel de navegación o mediante la barra de navegación, si agrega subcuadrículas configuradas para mostrar registros de entidad relacionados útiles mejorará la experiencia para la mayoría de los usuarios.|  
|**Barra de comandos**|Usa los datos definidos para que las cintas de opciones ofrezcan comandos pertinentes para el registro.<br /><br /> Se muestran los cinco primeros comandos seguidos de puntos suspensivos (![botón Más comandos](media/not-available.gif "botón Más comandos")), lo que proporciona un menú de control flotante para elegir comandos adicionales.|  
|**Imagen**|Cuando una entidad tiene un campo de imagen y la opción **Imagen principal** de la entidad está definida en **Imagen predeterminada**, se puede mostrar una imagen en el encabezado cuando el formulario se configura para mostrar la imagen.|  
|**Encabezado**|Los campos colocados en el encabezado siguen siendo visibles cuando los usuarios bajan por el cuerpo del formulario.<br /><br /> Hasta cuatro campos se pueden incluir en el encabezado. No se permiten varias líneas de texto, recursos web o iFrames en el encabezado. El encabezado y el pie de página comparten algunas propiedades con las secciones.|  
|**Control de proceso**|Cuando una entidad tiene flujos de proceso de negocio activos, el control de proceso aparece debajo del encabezado. Más información: [Flujos de proceso de negocio](/flow/business-process-flows-overview)|  
|**Cuerpo**|El cuerpo es la parte desplazable del formulario que contiene las pestañas.|  
|**Pestañas**|En el cuerpo del formulario, las pestañas proporcionan separación horizontal. Las pestañas tienen una etiqueta que puede mostrarse. Si se muestra la etiqueta, las pestañas se pueden expandir o contraer para mostrar u ocultar su contenido seleccionando la etiqueta.<br /><br /> Las pestañas contienen hasta tres columnas, y el ancho de cada columna se puede establecer en un porcentaje del ancho total. Al crear una pestaña, cada columna se rellena previamente con una sección.|  
|**Secciones**|Una sección ocupa el espacio disponible en una columna de la pestaña. Las secciones tienen una etiqueta que puede mostrarse, y una línea se puede mostrar debajo de la etiqueta.<br /><br /> Las secciones pueden tener hasta cuatro columnas e incluyen opciones para visualizar como se mostrarán las etiquetas de los campos en la sección.|  
|**Campos**|Los campos muestran controles que los usuarios utilizan para ver o modificar datos del registro de una entidad. Se puede aplicar formato a los campos para que ocupen hasta cuatro columnas dentro de una sección.|  
|**Espaciador**|Un espaciador permite agregar un campo vacío a una columna de sección.|  
|**Subcuadrículas**|Las subcuadrículas permiten la presentación de una lista dentro del formulario. La capacidad de mostrar gráficos con una subcuadrícula no está disponible en formularios de entidades actualizadas.|  
|**Formulario de vista rápida**|Un formulario de vista rápida muestra datos de un registro al que hace referencia un campo de búsqueda en el formulario. La entidad que es el destino de la búsqueda debe tener un formulario de vista rápida para que se pueda agregar uno al formulario. Más información: [Crear y editar formularios de vista rápida](create-edit-quick-view-forms.md)|  
|**Recursos web**|Es posible agregar recursos HTML y web de Microsoft Silverlight a los formularios principales, pero no se mostrarán cuando se utilice Dynamics 365 para teléfonos y Dynamics 365 para tabletas.|  
|**iFrame**|Un marco flotante que configura para mostrar una página web de otro sitio web. **Importante:**  <ul><li>Cuando la página mostrada en un iFrame está en otro dominio, los exploradores aplican un nivel alto de seguridad. Esto puede complicar los requisitos para que el contenido de un iFrame interactúe con los datos del formulario.</li><li>No se puede mostrar un formulario de entidad en un iFrame insertado en otro formulario de entidad. 
|**Mapas de Bing**|Cuando el control se encuentra en un formulario de una entidad actualizada y el valor de configuración del sistema **Habilitar Mapas de Bing** está habilitado con una clave válida de Mapas de Bing, este control se puede usar una vez en un formulario para mostrar la ubicación de una de las direcciones de una entidad actualizada. Más información: [Configurar mapas de Bing](configure-bing-maps-legacy.md)|  
|**Pie de página**|Cualquier número de campos, recursos web o iFrames se puede agregar al pie de página. Los campos son de solo lectura cuando se muestran en el pie de página. El encabezado y el pie de página comparten algunas propiedades con las secciones.|  
|**Barra de estado**|La barra de estado muestra el campo de estado del registro, un área de notificación y un botón Guardar.|  
  
<a name="BKMK_CRMforTabletsPresentation"></a>   
## <a name="dynamics-365-for-phones-and-tablets-forms"></a>Formularios de Dynamics 365 para teléfonos y tabletas  
 La mayoría de las entidades del sistema y las entidades personalizadas se encuentran disponibles para Dynamics 365 para teléfonos y tabletas. El formulario principal de estas entidades se transforma en una presentación optimizada para teléfonos o tabletas.  
  
<a name="BKMK_EntitiesEnabledForCRMForTablets"></a>   
### <a name="entities-enabled-for-dynamics-365-for-phones-and-tablets"></a>Entidades habilitadas de Dynamics 365 para teléfonos y tabletas  
 Solo las entidades que están habilitadas para Dynamics 365 para teléfonos y Dynamics 365 para tabletas utilizan esta presentación del formulario principal. Más información: [Entidades mostradas en Dynamics 365 para teléfonos y Dynamics 365 para tabletas](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_CustomEntity)  
  
### <a name="form-design"></a>Diseño de formularios  
 Dynamics 365 para teléfonos y tabletas toma muchos de los elementos del formulario principal y los muestra de forma optimizada para teléfonos y tabletas. Los siguientes diagramas muestran la redistribución desde la aplicación web a las aplicaciones para tableta y teléfono.  
  
 **Aplicación web**  
  
 ![Redistribución de formulario de Dynamics 365 desde la aplicación web](media/custon-reflow-web-app.png "Redistribución de formulario de Dynamics 365 desde la aplicación web")  
  
 **Aplicación para tabletas**  
  
 ![Redistribución de formulario de Dynamics 365 en la aplicación para tableta](media/reflow-tablet-app.png "Redistribución de formulario de Dynamics 365 en la aplicación para tableta")  
  
 **Aplicación para teléfonos**  
  
 ![Redistribución de formulario de Dynamics 365 en la aplicación para teléfono](media/custon-reflow-phone-app.png "Redistribución de formulario de Dynamics 365 en la aplicación para teléfono")  
  
 Los elementos de formulario se transforman en un diseño panorámico amplio en Dynamics 365 para tabletas, donde los usuarios pueden pasar el dedo por la pantalla para cambiar los elementos visibles en una ventana gráfica. En Dynamics 365 para teléfonos, los usuarios deslizan la pantalla para ver otra columna o panel de elementos, y el control de proceso aparece sobre cada columna.  
  
### <a name="view-port-element"></a>Elemento de la ventana gráfica  
 Los siguientes elementos están siempre visibles dentro de la ventana gráfica en el contexto de un formulario:  
  
 **Barra de navegación**  
 La barra de navegación es una presentación del mapa del sitio optimizada para el funcionamiento táctil. Más información: [Cambiar opciones de navegación](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_NavigationOptions)  
  
 **Inicio**  
 El botón Inicio lleva a los usuarios al panel que es la página de inicio de Dynamics 365 para teléfonos y Dynamics 365 para tabletas.  
  
 **Control de proceso**  
 Si la entidad tiene un proceso de negocio habilitado, aparecerá en la esquina superior derecha junto al control de búsqueda en Dynamics 365 para tabletas, y en la parte superior de la pantalla en Dynamics 365 para teléfonos.  
  
 **Buscar**  
 Los usuarios pueden pulsar el control de búsqueda para abrir la pantalla para buscar registros.  
  
 **Barra de comandos**  
 De forma predeterminada, algunos de los comandos que aparecen en la aplicación ejecutándose en un explorador web no aparecen en las aplicaciones de Dynamics 365 para teléfonos y Dynamics 365 para tabletas. Al igual que la aplicación web, la barra de comandos es contextual, por lo que los comandos disponibles cambian en función de lo que se visualice o seleccione. Más información: [Cambiar comandos](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_ChangeCommands)  
  
### <a name="form-elements"></a>Elementos de formulario  
 Los elementos de formulario mostrados se toman del formulario principal y aparecen como una serie de paneles que los usuarios ven en la ventana gráfica.  
  
 En Dynamics 365 para tabletas, el primer panel muestra la información de contacto de las relaciones existentes para el registro. En Dynamics 365 para teléfonos, el primer panel también muestra campos de encabezado del formulario sobre las ventanas de relación.  
  
 ![Panel de relaciones de Dynamics 365 para tabletas](media/mobile-app-form-relationships.png "Panel de relaciones de Dynamics 365 para tabletas")  
  
 Para los formularios Contacto y Usuario, el elemento muestra una tarjeta de comunicación correspondiente al registro. La tarjeta de comunicación proporciona botones para iniciar la comunicación con el contacto. Para otras entidades, aparece una tarjeta de comunicación si hay un formulario de vista rápida Contacto insertado en el formulario principal.  
  
 Puede mostrar ventanas adicionales de acuerdo con las relaciones de las entidades, pero no es posible personalizar las ventanas de las siguiente entidades:  
  
|Entidad|Ventanas|  
|------------|-----------|  
|Cuenta|Owner|  
|Contacto|Nombre de la empresa, propietario|  
|Lead|Owner|  
|Opportunity|Cuenta, propietario|  
  
 Puede personalizar las ventanas restantes con el editor de formularios. El orden es fijo, pero puede establecer qué elementos son visibles en el panel de relaciones.  
  
 En Dynamics 365 para tabletas, el segundo panel comienza con el nombre de la primera pestaña del formulario. Todos los campos que están incluidos en el encabezado se incluyen; posteriormente, se agrega el contenido de la primera pestaña. En Dynamics 365 para teléfonos, los encabezados aparecen en la primera columna.  
  
 ![Primer panel del formulario de CRM para tabletas](media/mobile-app-form-first-panel.png "Primer panel del formulario de CRM para tabletas")  
  
 Si hay un flujo de proceso activo para el formulario, la tercera pestaña muestra las tareas de la fase actual del proceso en Dynamics 365 para tabletas. En Dynamics 365 para teléfonos, el control de proceso flota sobre los paneles, se expande sobre el panel actual del usuario cuando se selecciona y siempre es visible y permite actuar.  
  
 Los paneles restantes del formulario incluyen el contenido de las pestañas del formulario. Las subcuadrículas encontradas se muestran como un panel diferente.  
  
 El formulario de Dynamics 365 para teléfonos y Dynamics 365 para tabletas siempre muestra las etiquetas de pestañas y subcuadrículas. La configuración de **Mostrar etiqueta en el formulario** no se aplica.  
  
> [!NOTE]
>  Para optimizar el rendimiento de los dispositivos móviles, el número de objetos está limitado a 5 pestañas o 75 campos y 10 subcuadrículas.  
  
 Los formularios para Dynamics 365 para teléfonos y Dynamics 365 para tabletas no admiten lo siguiente:  
   
-   Mapas de Bing  
  
-   Yammer
  
-   Fuentes de actividades  
  
-   Temas  
  
 Además, las imágenes de la entidad son visibles en las vistas de lista y tarjetas de contacto, pero no dentro del formulario real.  
  
<a name="BKMK_MultipleForms"></a>   
### <a name="multiple-forms"></a>Varios formularios  
 Dynamics 365 para teléfonos y Dynamics 365 para tabletas admiten varios formularios, pero no proporcionan a los usuarios ningún método para cambiar entre formularios si pueden acceder a más de uno. Los usuarios verán el primer formulario del pedido de formularios al que tengan acceso.  
  
 Por ejemplo, si tiene los siguientes formularios principales para la entidad de oportunidad y ha asignado los siguientes roles de seguridad a cada uno, verá el pedido de formularios indicado en la tabla siguiente.  
  
|Pedido de formularios|Nombre del formulario|Roles de seguridad|  
|----------------|---------------|--------------------|  
|1|**Primer formulario de ventas**|Comercial|  
|2|**Segundo formulario de ventas**|Comercial y jefe de ventas|  
|3|**Tercer formulario de ventas**|Jefe de ventas|  
|4|**Cuarto formulario de ventas**|Vicepresidente de ventas|  
  
-   Los usuarios con el rol de comercial siempre verán el **primer formulario de ventas**.  
  
-   Los usuarios con el rol de jefe de ventas siempre verán el **segundo formulario de ventas**.  
  
-   Los usuarios con el rol de vicepresidente de ventas siempre verán el **cuarto formulario de ventas**.  
  
<a name="BKMK_ClassicPresentation"></a>   
## <a name="classic-forms"></a>Formularios clásicos  
 En el siguiente diagrama se muestran los componentes principales del formulario usados en la presentación clásica.  
  
 ![Principales elementos de formulario](media/elements.png "Principales elementos de formulario")  
  
 Los formularios de entidades actualizadas han heredado muchos componentes de los formularios clásicos, aunque hay diferencias significativas.  
  
 Los formularios que usan la presentación clásica no incluyen la barra de navegación, y la cinta de opciones se usa en lugar de la barra de comandos. Estos formularios no admiten las imágenes de entidad, el control de proceso, los formularios de vista rápida, el guardado automático ni los mapas de Bing. Los campos del encabezado no se pueden editar.  
  
 El Asistente de formulario se expone para determinadas entidades, como `Article`.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear y diseñar formularios](create-design-forms.md)   

 
