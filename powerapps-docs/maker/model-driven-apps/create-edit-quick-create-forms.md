---
title: Crear o editar formularios de creación rápida de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Aprenda a crear o editar un formulario de creación rápida.
ms.custom: ''
ms.date: 05/23/2018
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
ms.assetid: 68ca9059-cc5a-45e7-88bd-cc57186bbb48
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-quick-create-forms-for-a-streamlined-data-entry-experience"></a>Crear o editar formularios de creación rápida de aplicaciones controladas por modelos para lograr una experiencia optimizada de entrada de datos

En este tema, creará y editará un formulario de creación rápida.

 Con los formularios de creación rápida, la aplicación puede tener una experiencia simplificada de entrada de datos totalmente compatibles con la lógica definida por scripts de formulario y reglas de negocio. En una aplicación controlada por modelos de PowerApps, los formularios de creación rápida aparecen al seleccionar el botón **Crear** en la barra de navegación o al elegir **+ Nuevo** al crear un registro nuevo desde una búsqueda o subcuadrícula.
  
 Las aplicaciones móviles de Dynamics 365 Customer Engagement utilizan formularios de creación rápida para crear registros nuevos. Si una entidad ya tiene un formulario de creación rápida configurado, las aplicaciones móviles usan ese formulario. Si una entidad no tiene configurado un formulario de creación rápida, PowerApps genera un formulario de creación rápida para crear registros en las aplicaciones móviles basadas en la definición del formulario principal.  
  
<a name="BKMK_QuickCreateFormEntities"></a>   
## <a name="entities-with-quick-create-forms"></a>Entidades con formularios de creación rápida  
 De forma predeterminada, solo las siguientes entidades del sistema tienen formularios de creación rápida.  
  
|||||  
|-|-|-|-|  
|Cuenta|Respuesta de campaña|Caso|Competidor|  
|Contacto|Cliente potencial|Oportunidad||  
  
Aunque puede crear formularios de creación rápida para entidades de actividad del sistema, a excepción de la entidad Cita, estas no admiten formularios de creación rápida. Con el lanzamiento de Microsoft Dynamics 365, versión 9.0, la entidad Cita incluye un formulario de creación rápida para utilizar con la Interfaz unificada. Actualmente, la opción de deshabilitar el formulario de creación rápida para la entidad Cita no se admite. Cualquiera de las otras [entidades actualizadas](create-design-forms.md) y todas las entidades personalizadas se pueden habilitar para admitir estos formularios seleccionando **Permitir creación rápida** en la definición de la entidad y creando un formulario de creación rápida para la entidad. 

Puede habilitar entidades de actividad personalizadas para admitir formularios de creación rápida y puede crear formularios de creación rápida para esas entidades. Sin embargo, el formulario de creación rápida para entidades de actividad personalizadas no se usará cuando los usuarios seleccionen **Crear** en la barra de navegación. Estos formularios de creación rápida se pueden usar solo cuando los usuarios agregan un nuevo registro para un subcuadrícula que muestra esa entidad de actividad personalizada específica.  
  
<a name="BKMK_CreateQuickCreate"></a>   
## <a name="create-a-quick-create-form"></a>Crear un formulario de creación rápida  
 Aunque puede definir varios formularios de creación rápida, solo uno puede usarlo todo el mundo. El formulario que todo el mundo usará se establece mediante el pedido de formulario. Los formularios de creación rápida no se pueden asignar a los roles de seguridad y no proporcionan al usuario la capacidad de cambiar formularios.  
  
> [!NOTE]
>  La entidad debe tener la opción **Permitir creación rápida** habilitada para que el formulario de creación rápida se muestre. 
  
### <a name="how-to-create-a-quick-create-form"></a>Cómo crear un formulario de creación rápida  
  
1.  En el sitio de [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) seleccione **Controlado por modelos** (parte inferior izquierda del panel de navegación).  

     ![Modo de diseño controlado por modelos](media/model-driven-switch.png)

> [!IMPORTANT]
> “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).     
  
2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  

3.  En la barra de herramientas seleccione **Agregar formulario** > **Formulario de creación rápida**.  
  
4.  En el diseñador de formularios arrastre los campos que desee del **Explorador de campos** a las secciones del formulario.  
  
5.  Cuando haya terminado, seleccione **Guardar**.  
  
6.  Seleccione **Publicar** para ver el nuevo formulario en la aplicación.  
  
<a name="BKMK_EditQuickCreate"></a>   
## <a name="edit-a-quick-create-form"></a>Editar un formulario de creación rápida  
 Aunque los formularios de creación rápida admiten scripts de formulario y reglas de negocio, su objetivo es diferente del de los formularios principales y no admiten todas las capacidades de los formularios principales. Los formularios de creación rápida siempre tienen una sección con tres columnas. No puede agregar más secciones o columnas.  
  
 Los siguientes controles no se pueden agregar a formularios de creación rápida:  
  
-   Subcuadrículas  
  
-   Formularios de vista rápida  
  
-   Recursos web  
  
-   iFrames  
  
-   Notas  
  
-   Mapas de Bing  
  
Si agrega un campo compuesto a un formulario de creación rápida, este se mostrará como un campo separado.  
  
### <a name="to-edit-a-quick-create-form"></a>Para editar un formulario de creación rápida  
  
1.  En el sitio de [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) seleccione **Controlado por modelos** (parte inferior izquierda del panel de navegación).  

> [!IMPORTANT]
> “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).    
  
2. Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.    

3. En la lista de formularios, seleccione uno cuyo **Tipo** sea **Creación rápida**.  
  
3.  Arrastre los campos que desee del **Explorador de campos** a las secciones del formulario.  
  
     Consulte [Configurar controladores de eventos](configure-event-handlers-legacy.md) para obtener información sobre la edición de controladores de eventos de scripts de formularios.  
  
4.  Cuando haya terminado, seleccione **Guardar**.  
  
5.  Seleccione **Publicar** para ver el formulario modificado en la aplicación.  
  
### <a name="next-steps"></a>Pasos siguientes  
[Información general de la interfaz de usuario del editor de formularios](form-editor-user-interface-legacy.md)
