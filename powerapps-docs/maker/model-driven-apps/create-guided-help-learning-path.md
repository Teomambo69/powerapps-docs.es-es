---
title: Crear su propia ayuda guiada (Ruta de aprendizaje) (aplicaciones basadas en modelo) | MicrosoftDocs
description: ''
keywords: ''
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 8ee3c432-5f76-4086-b9cc-6cd467ae056b
author: Mattp123
ms.author: matp
manager: kvivek
topic-status: Drafting
search.audienceType:
- customizer
search.app:
- PowerApps
ms.openlocfilehash: b9c0f192f96d9ce967d1b8e56266aadeb64646c9
ms.sourcegitcommit: 7411b4cf9e30e71052fe932dfd3276e969854af4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "2768307"
---
# <a name="create-guided-help-learning-path-for-your-app"></a>Crear ayuda guiada (Ruta de aprendizaje) para la aplicación

Use la Ruta de aprendizaje para dar a los usuarios una experiencia de Ayuda personalizada dentro de la aplicación que está adaptada a su entorno y al uso y flujo de trabajo específicos de su organización. 

> [!IMPORTANT]
> Ruta de aprendizaje sólo está disponible con aplicaciones del cliente web heredadas. Use páginas de ayuda personalizadas para aplicaciones de la interfaz unificada. Más información: [Crear ayuda guiada para la aplicación de la Interfaz unificada](../common-data-service/create-custom-help-pages.md)

La Ruta de aprendizaje facilita el aprendizaje y adopción de aplicaciones y de procesos de organización, garantiza que los datos se introducen e interpretan de manera consistente, y reduce los errores y las llamadas de soporte generadas por los usuarios. [Vea un vídeo corto (1:50) sobre Ruta de aprendizaje](https://community.dynamics.com/crm/b/crmvideos/archive/2016/05/09/introducing-learning-path-for-dynamics-crm).  

<a name="CustomHelp"></a>   

## <a name="how-is-learning-path-different-from-customizable-help"></a>¿En qué se diferencia la Ruta de aprendizaje de la Ayuda personalizable?  
 La Ayuda personalizable permite reemplazar la Ayuda de aplicaciones [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] predeterminada y dirige a los usuarios de la organización a otra dirección URL para la Ayuda. O puede reemplazar la Ayuda para una entidad muy personalizada que puede describir mejor el flujo de trabajo. 

 La Ruta de aprendizaje permite agregar Ayuda personalizable que los usuarios ven en la aplicación cuando abren una página, realizan una acción o seleccionan el botón Ayuda (?).   

 Para obtener más información sobre Ayuda personalizable, consulte [Personalizar la experiencia de la Ayuda](https://technet.microsoft.com/library/dn832079.aspx).  

<a name="Avail"></a>   
## <a name="prerequisites"></a>Requisitos previos  

 Para crear contenido de Ruta de aprendizaje, debe:  

- Estar usando PowerApps o [!INCLUDE[pn_crm_online_shortest](../../includes/pn-crm-online-shortest.md)].  

- Han optado por recibir la Ruta de aprendizaje. Este valor está activado de forma predeterminada, pero puede haberse desactivado.  

   Para asegurarse de que la Ruta de aprendizaje está activada: en la barra de navegación, vaya a **Configuración** ![Icono Configuración](media/optionsbutton.png "Icono Configuración") > **Optar por recibir la ruta de aprendizaje**.  

   Más información: [Modificador encendido/apagado para Ruta de aprendizaje (ayuda guiada)](/dynamics365/customer-engagement/admin/on-off-switch-for-learning-path-guided-help).  

- Tener el rol Personalizador del sistema o Administrador del sistema u otro rol que tenga el privilegio de creación de la Ruta de aprendizaje.  

- Habilitar la creación de la Ruta de aprendizaje Esto crea el grupo de seguridad Autores de la Ruta de aprendizaje de [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)].  

- Hágase miembro del grupo de seguridad Autores de la Ruta de aprendizaje de [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)].  

  Puede crear contenido de la Ruta de aprendizaje para los módulos de aplicación web y los módulos de aplicación de Interfaz unificada. Esto incluye [!include[](../../includes/pn-dyn-365-tablets.md)].  

<a name="TurnOnLP"></a>   
## <a name="turn-on-learning-path-for-your-organization"></a>Activar la Ruta de aprendizaje para la organización  
 La Ruta de aprendizaje es una característica opcional que se puede activar o desactivar para su organización. Puede mostrar el contenido de Ruta de aprendizaje incluido con [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)], crear su propio contenido de Ruta de aprendizaje para los usuarios, o ambos.  

1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) o [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] con una cuenta de administrador.  

2. Vaya a **Configuración** y, luego, **Administración** en **Sistema**. Más información: [Configuración](/powerapps/maker/model-driven-apps/advanced-navigation#settings)

3. En la página **Administración**, seleccione **Configuración del sistema**.  

4. En la pestaña **General**, en **Establecer la URL de la Ayuda personalizada**, seleccione **Sí** en **Habilitar Ruta de aprendizaje** y **Habilitar la creación de la ruta de aprendizaje**.  

    Puede habilitar Ruta de aprendizaje o Ayuda personalizable pero no ambas al mismo tiempo. Confirme que **Usar la Ayuda personalizada para entidades personalizables** y **Anexar los parámetros a la URL** están establecidos en **No**.  

     ![Diálogo Configuración del sistema con las opciones que permiten seleccionar y habilitar la herramienta Creación de Ruta de aprendizaje](media/lp-system-settings.png "Cuadro de diálogo Configuración del sistema con las opciones que permiten seleccionar y habilitar la herramienta Creación de Ruta de aprendizaje")  

5. Seleccione **Aceptar**.  

<a name="ReqsAuth"></a>   
## <a name="add-a-user-to-the-office-365-learning-path-authors-security-group"></a>Agregar un usuario al grupo de seguridad Autores de la ruta de aprendizaje de Office 365  
 Si usted no es miembro del grupo de seguridad Autores de [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)], verá el siguiente mensaje de error al abrir la biblioteca de contenido de la Ruta de aprendizaje.  

 ![Mensaje de error que indica que el usuario no es miembro del grupo de seguridad de Ruta de aprendizaje](media/lp-o365-security-group.png "Mensaje de error que indica que el usuario no es miembro del grupo de seguridad de Ruta de aprendizaje")  

#### <a name="add-a-user"></a>Agregar un usuario  

1. Vaya al portal de administración del inquilino de [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)] seleccionando **Navegar a otras aplicaciones** en la esquina superior izquierda de la página cuando inicie sesión en [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] y luego seleccione **Administración**.  

    Es posible que deba volver a escribir la contraseña.  

2. En el **Centro de administración**, seleccione **Grupos**.  

3. En la página **Grupos**, seleccione el grupo de seguridad **Autores de Ruta de aprendizaje**.  

4. Haga clic en **Editar** en la fila **Integrantes** para agregar usuarios al grupo.  

5. Seleccione **+ Agregar integrantes**y, a continuación especifique o busque los usuarios que desee agregar al grupo.  

6. Seleccione **Guardar** cuando haya terminado de agregar usuarios.  

> [!NOTE]
>  Otra forma de asignar el grupo a una cuenta de usuario es seleccionando **Usuarios** > **Usuarios activos**, seleccionando el usuario que desee agregar y, a continuación haciendo clic en **Editar** junto a **Pertenencia al grupo** para seleccionar los grupos a los que agregar el usuario.  

<a name="MultipleOrgs"></a>   
## <a name="how-does-learning-path-work-with-multiple-organizations"></a>¿Cómo funciona la Ruta de aprendizaje con varias organizaciones?  
 Al publicar contenido de la Ruta de aprendizaje, puede usar Entornos de publicación para controlar en qué organizaciones asociadas al inquilino se publica su contenido. Para publicar diferente contenido para organizaciones diferentes, cree varios entornos de publicación y agregue cada organización a uno o más de ellas.  

<a name="SecurityRoles"></a>   
## <a name="learning-path-and-common-data-service-security-roles"></a>Ruta de aprendizaje y roles de seguridad de Common Data Service 
 
 Common Data Service usa roles de seguridad para determinar qué contenido de la Ruta de aprendizaje se muestra cuando un usuario selecciona el botón Ayuda, se desplaza a una página o realiza una acción definida en Common Data Service.  

 Los roles que se usan en la Ruta de aprendizaje son los mismos usados en su organización de Common Data Service para seguridad y acceso a los datos, pero puede crear contenido de la Ruta de aprendizaje para todos y cada uno de los roles de seguridad de Common Data Service.  Normalmente, conviene que los roles de seguridad del diseñador de la Ruta de aprendizaje coincidan con el entorno de Common Data Service. Sin embargo, puede simplificar la interfaz de usuario en el diseñador ocultando algunos roles de seguridad de Common Data Service del diseñador. Si más tarde decide que desea usar un rol de seguridad que eliminó de la Ruta de aprendizaje, puede sincronizar los roles entre la Ruta de aprendizaje y Common Data Service.  

 Si la organización tiene varias unidades de negocio, los roles de seguridad pueden tener relaciones primarias y secundarias. Solo los roles de seguridad de la unidad de negocio raíz se sincronizan.  

 Para obtener más información acerca de los roles de seguridad, consulte: [Roles de seguridad y privilegios](/dynamics365/customer-engagement/admin/security-roles-privileges).  

<a name="Precedence"></a>   
### <a name="learning-path-role-precedence"></a>Prioridad de los roles de Ruta de aprendizaje  
 Si a un usuario de la organización se le asigna más de un rol de seguridad, la prioridad se usa para determinar que rol de seguridad asignado se usa para mostrar contenido de la Ruta de aprendizaje. Si el contenido de la Ruta de aprendizaje está asociado a un rol de seguridad, cualquier usuario asignado a ese rol verá contenido de la Ruta de aprendizaje, incluso si se le asigna un rol de seguridad con una prioridad mayor que no está asociada al contenido de la Ruta de aprendizaje.  

 Cada rol incluido en la Ruta de aprendizaje tiene un valor numérico. El primer rol en la lista tiene la prioridad más alta y los roles posteriores tienen prioridad más baja. Cuando se asigna a un usuario un rol que desencadena la visualización de contenido de la Ruta de aprendizaje, el usuario verá ese contenido incluso se le hubiera asignado un rol con una prioridad más baja que no esté asociada al contenido. Por ejemplo, si a un usuario se le asigna un rol con una prioridad 1 y un rol con prioridad 20, el usuario verá contenido de la Ruta de aprendizaje definido solo para el rol con prioridad 1.  

 Si crea contenido diferente para distintos roles en la misma página o pantalla de aplicaciones basadas en modelo, los usuarios verán el contenido asociado al rol con prioridad más alta.  

<a name="ManageRoles"></a>   
### <a name="manage-security-roles-and-precedence"></a>Administrar roles de seguridad y prioridad  
 Puede controlar qué roles de seguridad están disponibles en el diseñador de Ruta de aprendizaje y establecer el orden de los roles para determinar la prioridad cuando se ejecuta la Ruta de aprendizaje. Si un usuario tiene dos roles, y hay contenido diferente publicado para un contexto determinado para cada uno de estos roles, el usuario verá el contenido para el rol que aparece más alto en la lista.  

<a name="ConfigureRoles"></a>   
#### <a name="configure-security-roles"></a>Configurar roles de seguridad  

1. Inicie sesión en PowerApps con una cuenta que tenga permisos de creación de la Ruta de aprendizaje.  

2. Abra la **Biblioteca de contenido**.  

3. Seleccione **Configuración** en la parte superior de la pantalla.  

4. Para sincronizar los roles de seguridad con su Common Data Service, seleccione **Sincronizar roles**.  

5. Para establecer el orden de prioridad de los roles usados con la Ruta de aprendizaje, use las flechas arriba o abajo para mover un rol en la lista.  

    La prioridad se determina por el orden de los roles mencionados en esta página.  

6. Para impedir que se use un rol con la Ruta de aprendizaje, haga clic en el botón **Eliminar** junto al rol.  

   > [!NOTE]
   >  Esto no elimina el rol de [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]. Elimina el rol del diseñador de la Ruta de aprendizaje para definir cómo se muestra el contenido a los usuarios. Puede restablecer siempre un rol oculto seleccionando **Sincronizar roles**.  

7. Cuando termine de realizar cambios, seleccione **Guardar**.  

8. Seleccione **Atrás** para volver a la biblioteca de contenido.  

<a name="MobileApp"></a>   
## <a name="create-learning-path-controls-for-includepn_dyn_365_tabletsincludespn-dyn-365-tabletsmd"></a>Crear controles de Ruta de aprendizaje para [!INCLUDE[pn_dyn_365_tablets](../../includes/pn-dyn-365-tablets.md)]  
 Puede crear controles de la Ruta de aprendizaje para [!INCLUDE[pn_dyn_365_tablets](../../includes/pn-dyn-365-tablets.md)] de la misma forma que crea controles para el cliente web. Para ello debe usar el simulador de aplicaciones móviles en un explorador web de modo que tenga acceso a la interfaz de usuario móvil para anclar los controles de Ruta de aprendizaje. Este simulador se debe usar únicamente con este fin.  


### <a name="display-the-mobile-app-interface-simulator-in-a-web-browser"></a>Mostrar el simulador de la interfaz de aplicación móvil en un explorador web  

1. Inicie sesión en [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)].  

2. Copie el nombre del servidor para su organización de Common Data Service desde la dirección URL que aparece en el explorador, como *<https://contososales.crm.dynamics.com/>*.  

    Asegúrese de incluir la barra diagonal (/) después de .com.  

3. Determine el nombre único de la organización (también denominada instancia) para la que desea crear controles de la Ruta de aprendizaje. Para obtener el nombre único, en el mapa del sitio, seleccione **Configuración** > **Personalizaciones** y, a continuación, en la página **Personalización**, seleccione **Recursos de desarrollador**. Copie el valor del campo **Nombre único** que se muestra en la sección **Referencia de la instancia**.  

   ![Nombre de organización de Dynamics mostrado en el panel de información de usuario](media/lp-org-name.png "Nombre de organización de Dynamics mostrado en el panel de información de usuario")  

4. Anexe lo siguiente a la primera parte de la dirección URL de la organización, reemplazando \<org name> por el nombre único de su organización determinado en el paso anterior:  

    nga/main.htm?org=*\<org name>*  

    La dirección URL debe tener un aspecto similar al siguiente: https://contososales.crm.dynamics.com/nga/main.htm?org=orgb557e46a  

5. Anexe lo siguiente a la dirección URL del paso anterior, reemplazando \<server name> por el nombre de servidor del primer paso en este procedimiento:  

    &server=*\<server name>*  

    La dirección URL debe tener un aspecto similar al siguiente: https://contososales.crm.dynamics.com/nga/main.htm?org=orgb557e46a&server=https://contososales.crm.dynamics.com/.  

6. Abra una nueva pestaña o ventana del explorador y copie la dirección URL completa que haya creado, péguela en la nueva pestaña o ventana del explorador, y seleccione Entrar.  

    La primera vez que se conecte a la interfaz de aplicaciones móviles, se muestra una pantalla de bienvenida mientras que el sistema procesa los metadatos y descarga personalizaciones. Una vez que ha finalizado, se muestra el área de trabajo.  

   > [!NOTE]
   >  Al conectarse a la versión de la aplicación móvil de la interfaz, se usarán las credenciales desde el inicio de sesión a la interfaz web para autenticarle. Deberá dejar la interfaz web abierta para evitar errores de acceso denegado al abrir la interfaz de la aplicación móvil.  

7. Cierre el área de trabajo para mostrar la página principal para la interfaz de la aplicación móvil en su explorador. A continuación puede abrir la biblioteca de contenido para crear o editar los controles de Ruta de aprendizaje. Más información: [Biblioteca de contenido](#ContentLibrary)  


<a name="ContentLibrary"></a>   
## <a name="content-library"></a>Biblioteca de contenido  
 La biblioteca de contenido muestra todas el contenido creado y disponible para su organización, así como los comandos para crear, administrar e interactuar con controles. Para crear o editar controles de la Ruta de aprendizaje, conéctese primero con la interfaz del cliente para la que desea crear controles y, a continuación abra la biblioteca de contenido.  

**Para abrir la biblioteca de contenido desde la interfaz del cliente web predeterminada, realice una de estas acciones:**  

-   En una barra lateral, seleccione el botón **Biblioteca de contenido**.  

     ![El icono Contenido de la biblioteca mostrado en una barra lateral de Ruta de aprendizaje](media/lp-sidebar-cl-icon.png "El icono Contenido de la biblioteca mostrado en una barra lateral de Ruta de aprendizaje")  

-   Seleccione la ventana **Aprendizaje** del mapa del sitio y, a continuación, **Biblioteca de contenido**.  

     ![Icono de Biblioteca de contenido en el mapa del sitio de aplicaciones basadas en modelo](media/lp-sitemap-content-library.png "Icono de Biblioteca de contenido en el mapa del sitio de aplicaciones basadas en modelo")  

**Para abrir la biblioteca de contenido desde el simulador de la interfaz de la aplicación móvil:**  

1.  Seleccione el botón de puntos suspensivos en un círculo (...) en la esquina inferior derecha de la pantalla.  

    ![Botón de puntos suspensivos para mostrar iconos de Ruta de aprendizaje](media/lp-cl-ellipses.png "Botón de puntos suspensivos para mostrar iconos de Ruta de aprendizaje")  

2.  Seleccione **Biblioteca de contenido de Ruta de aprendizaje**.  

    ![Botones de Ruta de aprendizaje que se muestra en la interfaz de aplicaciones móviles](media/lp-mobile-lp-button.png "Botones de Ruta de aprendizaje que se muestra en la interfaz de aplicaciones móviles")  



> [!NOTE]
>  Si no ve todas estas columnas en la biblioteca del contenido, puede que sea porque el zoom de vista del explorador se establece por encima del 100%. Para ver todas las columnas, establezca el zoom al 100% o menos.  

 La biblioteca de contenido incluye las columnas descritas en la tabla siguiente:  

|Columna|Descripción|  
|------------|-----------------|  
|**Nombre**|El nombre que usó al crear la tarea guiada o la barra lateral. Un símbolo rojo de candado junto al nombre indica que el contenido está protegido actualmente. Puede pasar el mouse sobre el icono para ver qué usuario ha protegido el contenido.<br /><br /> ![El icono de candado rojo indica que el contenido está desprotegido.](media/lp-cl-checked-out.png "REl icono de candado rojo indica que el contenido está desprotegido.")<br /><br /> Un asterisco rojo situado junto al nombre indica contenido recién protegido.<br /><br /> ![Asterisco rojo que indica contenido recién protegido](media/lp-cl-new-check-in.png "RAsterisco rojo que indica contenido recién protegido")|  
|**Título**|El título que proporcionó cuando agregó contenido a la tarea guiada o la barra lateral. Los títulos para las barras laterales y tareas guiadas se muestran en barras laterales cuando se agregan como vínculos, o cuando se devuelven como resultados de la búsqueda.|  
|**Escriba**|Un símbolo que indica el tipo de contenido: barra lateral o tarea guiada|  
|**Factor de formulario**|Símbolos que representan el factor de forma seleccionado para este contenido cuando se creó, **Escritorio** o **Tableta**.<br /><br /> La columna **Factor de forma** no se muestra cuando usa la biblioteca de contenido cuando está conectado al simulador de la interfaz de la aplicación móvil o el centro de servicio interactivo.|  
|**Etiquetas**|Muestra cualquier etiqueta aplicada a este contenido. Puede agregar etiquetas en el cuadro de diálogo **Opciones avanzadas**. Use etiquetas para filtrar contenido que aparece en la biblioteca.|  
|**Versión de aplicación**|La versión de la aplicación en la que se creó el control.|  
|**Autor**|Nombre de la persona que creó el control.|  
|**Idiomas**|Un valor numérico que representa el número de idiomas al que se ha traducido el control.<br /><br /> Esta columna|  
|**Estado**|Muestra **Publicado** si el contenido está publicado actualmente; si no, el estado es **Borrador**.|  
|**Habilitada**|Muestra si el contenido está habilitado o deshabilitado.  Sólo el contenido habilitado se muestra a los usuarios.|  
|**Última publicación**|La fecha más reciente en que se publicó el contenido.|  

<a name="ContentTypes"></a>   
## <a name="learning-path-content-types-guided-tasks-and-sidebars"></a>Tipos de contenido de Ruta de aprendizaje: tareas guiadas y barras laterales  
 Puede crear dos tipos de contenido en la Ruta de aprendizaje: tareas guiadas y barras laterales.  

<a name="GT"></a>   
### <a name="guided-tasks"></a>Tareas guiadas  
 Una tarea guiada suele ser una serie de pasos, aunque también puede ser un solo paso. Un usuario puede iniciar una tarea guiada seleccionando un vínculo de una barra lateral, navegando a una página o seleccionando un vínculo de una página para la que se ha creado contenido. En cada paso, el usuario selecciona el botón **Siguiente** o completa una acción definida para pasar al paso siguiente, o para llevar a cabo la tarea guiada.  

 Las tareas guiadas son útiles para guiar a los usuarios con tareas comunes o nuevas. También se pueden usar para asegurarse de que las tareas se realizan de manera coherente en la organización, o que los datos se introducen de una forma específica para admitir procesos o el flujo de trabajo de la organización. Puede incluir vínculos, vídeos, y otra información en tareas guiadas para ayudar a los usuarios a familiarizarse y a obtener más información sobre la parte de la interfaz de usuario a la que el paso hace referencia.  

<a name="Sidebar"></a>   
### <a name="sidebars"></a>Barras laterales  
 Una barra lateral se muestra cuando un usuario selecciona el botón Ayuda, se desplaza a una página, o selecciona un vínculo o un botón de una página para la que usted ha creado contenido. También puede crear barras laterales de inicio que se muestran cuando el usuario abre la página o la pantalla, o selecciona el icono Inicio en una barra lateral.  

 ![Icono Inicio en una barra lateral](media/sidebar-home.png "Icono Inicio en una barra lateral")  

 También puede definir las barras laterales de error que aparecen cuando hay un problema que muestra la barra lateral prevista. Puede incluir vínculos, vídeos, y otra información en barras laterales para ayudar a los usuarios a familiarizarse y a obtener más información sobre la página o el formulario mostrado, o acciones que pueden realizar en la página o el formulario.  

<a name="CreateGT"></a>   
## <a name="create-a-guided-task"></a>Crear una tarea guiada  

 Hay dos pasos para crear una tarea guiada:  

1.  Defina cómo se desencadena la tarea, y asigne los roles a los que el contenido se aplica.  

2.  Use el editor de flujo para agregar pasos que los usuarios verán mientras recorren la tarea guiada.  

### <a name="define-the-triggers-and-roles"></a>Definir los desencadenadores y los roles  

1. Vaya a la página para la que desea crear una tarea guiada.  

2. Abra la Biblioteca de contenido. Consulte [Biblioteca de contenido](#ContentLibrary) para conocer el procedimiento.  

3. En la Biblioteca de contenido, seleccione **Tarea guiada**.  

    ![Vincular para crear una nueva tarea guiada en Biblioteca de contenido de Ruta de aprendizaje](media/lp-content-library-gt.png "Vincular para crear una nueva tarea guiada en Biblioteca de contenido de Ruta de aprendizaje")  

4. Especifique un nombre y seleccione los otros valores para la tarea guiada. Use esta tabla para referencia.  


   |              Configuración               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |    **Deshabilite esta tarea guiada**    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Active esta casilla para deshabilitar la tarea guiada. Cuando está deshabilitada, no se muestra a los usuarios.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   | **Definir como tarea guiada de error** |                                                                                                                                                                                                                                                                                                                                                                                                                       Seleccione esta casilla si desea mostrar esta tarea guiada solo cuando hay un error con otras tareas guiadas, como la falta de privilegios o cualquier problema que impida que se muestren otras tareas guiadas asociadas a la página.                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |              **Nombre**              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        El nombre para la tarea guiada que se muestra en la biblioteca de contenido.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |             **Cliente**             |                                                                                                                                                                               El valor del cliente se establece automáticamente para la plataforma en la que está creando contenido. **Advertencia:** Si edita un control existente cuando está conectado a una interfaz distinta de aquella en la que se creó el control, el valor del cliente se actualizará con el tipo de cliente actual. Esto hará que el control se rompa y no funcione en el cliente para el que se creó originalmente el control. <br /><br /> Si está creando controles para la interfaz web, aparece **Cliente web**.<br /><br /> Si está conectado al simulador de la interfaz de la aplicación móvil, se muestra **Aplicaciones móviles**.<br /><br /> Si está conectado el centro de servicio interactivo, aparece **Centro de servicio interactivo** .                                                                                                                                                                               |
   |          **Factor de forma**           |                                                                                                                                                                       El factor de forma mostrado depende de la interfaz para la que está creando contenido. Si usa la interfaz del cliente web, se muestran **Escritorio** y **Tableta**. Cuando está seleccionada para el cliente web, **Tableta** hace referencia a los exploradores que se ejecutan en dispositivos de tableta, no a la aplicación móvil.<br /><br /> Si está creando controles para la interfaz de la aplicación móvil, aparece **Tableta**. Esto hace referencia a dispositivos que ejecutan la aplicación móvil de [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)], pero solo se admite en tabletas.<br /><br /> Si usa el centro de servicio interactivo, aparece **Escritorio**. **Importante:**  La Ruta de aprendizaje no se admite en [!INCLUDE[pn_crm_shortest](../../includes/pn-dyn-365-phones.md)].                                                                                                                                                                        |
   |     **La tarea guiada se abre cuando**     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Seleccione si desea que la tarea guiada aparezca cuando **Se carga la página** o cuando **Se hace clic en el vínculo** en una barra lateral.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |        **Fase del ciclo de vida**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Este ajuste es solo para uso interno.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |   **Rol de seguridad de Common Data Service**   |                                                                                                                                                                                                                                                                                                                                                                                                  Seleccione el rol o roles de seguridad para los que desea mostrar la tarea guiada. Puede seleccionar todos los roles que desee. Si a un usuario se le asigna más de un rol, la tarea guiada aparecerá solamente para el rol con la mayor prioridad, como se describió anteriormente en este tema.                                                                                                                                                                                                                                                                                                                                                                                                   |
   |             **Estado**             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Muestra el estado de la tarea guiada. El estado será **Borrador** hasta que la publique.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |        **Opciones avanzadas**        | Esta opción está disponible después guardar la tarea guiada. Están disponibles los siguientes valores en **Opciones avanzadas**:<ul><li>**Realizar esta tarea guiada incorrecta**: seleccione esta casilla si desea mostrar esta Tarea guiada solo cuando hay un error con otras tareas guiadas.</li><li>**Idiomas compatibles**: Seleccione los idiomas para esta tarea guiada, y para la importación y la exportación.</li><li>**Autor**: Cambie el autor definido para esta tarea guiada.</li><li>**Etiquetas**: Agregue o elimine etiquetas aplicadas a esta tarea guiada. Use etiquetas para facilitar la búsqueda de contenido en la biblioteca contenido, o clasificar su contenido.</li></ul><br />También puede establecer los valores siguientes en **Publicar información**:<ul><li>**Versión de aplicación**: Establezca la versión de [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] asociada el contenido.</li><li>**Versión**: Establezca la versión del contenido que cree.</li><li>**Grupo de creación**: Establezca en el grupo de creación para el contenido que cree.</li><li>**Grupos de publicación**: Seleccione el grupo o grupos de publicación para este contenido.</li></ul> |


5. Cuando haya terminado, seleccione **Guardar** para empezar a usar el Editor de flujo.  

### <a name="add-steps-with-the-flow-editor"></a>Agregue pasos con el Editor de flujo  

1. Agregue el título donde se muestra *Título de tarea guiada*. Este es el título que los usuarios verán.  

2. Seleccione si se mostrarán o no controles de Id. fijos únicamente. Los controles registrados se resaltan en verde, y los no registrados en azul cuando arrastra la ventana para anclarla a la interfaz de usuario. Si ancla un paso a un control sin un Id. fijo, puede verse afectado por una actualización futura de [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]. Las actualizaciones no afectarán a los controles de Id. fijos.  

3. Seleccione **Agregar nuevo paso** y elija el tipo de paso que desee usar para el primer paso de la tarea guiada.  

   |Tipo de botón|Descripción|  
   |-----------------|-----------------|  
   |**Paso con botón Siguiente**|Este paso tiene un botón Siguiente que puede servir para navegar al siguiente paso del flujo. Si ésta es el último paso del flujo, el botón Siguiente no aparecerá. Arrastre la ventana para anclar el paso donde desea que se muestre en la aplicación.|  
   |**Paso con acción del usuario**|Este paso no tiene un botón Siguiente. Se pide al usuario que seleccione el elemento de la UI en el que está anclado el paso. Si se produce redireccionamiento de página o cualquier cambio de estado de la UI como resultado de este clic, asegúrese de anclar el siguiente paso en el estado de la UI cambiada. Arrastre la ventana para anclar el paso donde desea que se muestre en la aplicación.<br /><br /> Ancle este tipo de paso a un control de la UI seleccionable, como un botón o un vínculo.|  
   |**Acción del usuario con botón Siguiente**|Este paso tiene un botón Siguiente. Seleccionar el botón Siguiente tiene el mismo efecto que seleccionar elemento de la UI en el que está anclado el paso. Si se produce redireccionamiento de página o cualquier cambio de estado de la UI como resultado de este clic, asegúrese de anclar el siguiente paso en el estado de la UI cambiada. Arrastre la ventana para anclar el paso donde desea que se muestre en la aplicación.|  
   |**Paso de aprendizaje**|Este paso tiene un botón personalizable como acción de fin. Este paso sólo puede estar al final de un flujo de tarea guiada. Puede usarlo para vincularlo a una barra lateral de Ruta de aprendizaje. Arrastre la ventana para anclar el paso donde desea que se muestre en la aplicación.|  

   > [!NOTE]
   >  Si ya ha planeado la tarea guiada y sabe qué pasos desea agregar, ahora puede agregarlos todos. Cada paso que agregue aparecerá en el editor de flujo en el orden que lo agregó. Puede reorganizar pasos después de agregarlos arrastrándolos arriba o abajo en la lista.  

4. Seleccione el tipo de paso que desee agregar y, a continuación arrastre la ventana a la interfaz de usuario para anclarla un control. Puede requerir varios intentos acostumbrarse a colocar el paso donde desea.  

   > [!NOTE]
   >  Puede mantener la ventana por un máximo de 15 segundos. Si no la ancla en 15 segundos, la ventana seguirá sin estar anclada y el puntero del mouse cambiará de nuevo a cursor normal.  

   ![Editor de flujos de tareas guiadas](media/lp-gt-flow-editor.png "Editor de flujos de tareas guiadas")  

5. Cuando haya colocado el paso donde desee, suelte el botón del mouse para anclarla al control. El paso aparecerá en la ubicación seleccionada. Para mover el paso, use el botón **Arrastrarme** en el panel junto al paso.  

   ![Icono Arrastrarme en una burbuja de tarea guiada](media/lp-gt-bubble-drag-me.png "Icono Arrastrarme en una burbuja de tarea guiada")  

6. Agregue contenido al paso usando los controles presentados junto a ella. Están disponibles las siguientes opciones de configuración:  

   - **Tipo de contenido**: Agregue texto o un vídeo al paso. Seleccione **Editar** para ver más valores. Puede cambiar tamaño de fuente, color y estilo del texto, y agregar una miniatura para vídeo.  

   - **Ubicación**: Especifique la ubicación del paso en el control al que lo ancló. Las selecciones incluyen: Posición automática (seleccionada de forma predeterminada), Superior izquierda, Superior derecha, Inferior izquierda, Inferior derecha, Izquierda superior, Izquierda inferior, Derecha superior y Derecha inferior.  

   - **Copiar**: Cree una copia del paso con contenido idéntico anclada en la misma ubicación e insértela en el flujo de tareas guiadas directamente después del paso original.  

7. Seleccione **Guardar** cuando termine de colocar y agregar contenido al paso, y cierre el paso mediante el botón Cerrar en la esquina superior derecha del paso, o seleccione la flecha en la esquina superior izquierda de la pantalla para volver al editor de flujo.  

   > [!NOTE]
   >  Siempre podrá editar el paso más tarde, por tanto, no se preocupe si accidentalmente lo cierra antes de tenerlo como desea.  

8. Para agregar o editar el siguiente paso de la tarea guiada, seleccione el icono ![Icono de contenido adicional para volver al editor de flujo](media/lp-chevron.png "Icono de contenido adicional para volver al editor de flujo") en la esquina superior izquierda de la pantalla para mostrar el editor de flujo.  

9. Agregue cualquier paso adicional que desee incluir en la tarea guiada, asegurándose de guardar cada paso cuando haya terminado de agregar contenido.  

    > [!NOTE]
    >  Si reubica un paso o lo copia con el botón **Copiar** en la barra de herramientas, los cambios sin guardar en ese paso se perderán. Asegúrese de guardar los cambios con frecuencia.  

10. Cuando haya terminado de agregar pasos a la tarea guiada, seleccione **Guardar**.  

11. Seleccione **Vista previa** para probar la tarea guiada y ver cómo aparecerá a los usuarios.  

    > [!NOTE]
    >  Para publicar la tarea guiada, deberá realizar una vista previa primero. Al cerrar un paso o usar la flecha en la esquina superior izquierda de la pantalla durante el modo de vista previa, verá los botones **Proteger** y **Publicar** en el diseñador de la Ruta de aprendizaje.  

12. Si está satisfecho con los cambios, protéjalos y publique la tarea guiada, o publíquela más tarde desde la biblioteca del contenido.  

<a name="CreateSidebar"></a>   
## <a name="create-a-sidebar"></a>Crear una barra lateral  

 Hay dos pasos para crear una barra lateral:  

1.  Establezca las propiedades de la barra lateral y asigne los roles a los que se aplica.  

2.  Agregue contenido a la barra lateral (texto, imágenes, vínculos y botones).  

### <a name="set-the-sidebar-properties-and-roles"></a>Establecer propiedades y roles de la barra lateral  

1. Vaya a la página para la que desea crear una barra lateral.  

2. Abra la Biblioteca de contenido. Consulte [Biblioteca de contenido](#ContentLibrary) para conocer el procedimiento.  

3. En la Biblioteca de contenido, seleccione **Barra lateral**.  

   ![Vincular para crear una nueva barra lateral en Biblioteca de contenido de Ruta de aprendizaje](media/lp-content-library-sb.png "Vincular para crear una nueva barra lateral en Biblioteca de contenido de Ruta de aprendizaje")  

4. Especifique un nombre y luego seleccione los otros valores para la barra lateral. Use esta tabla para referencia.  


   |             Configuración             |                                                                                                                                                                                                                                                                                                                                                        Descripción                                                                                                                                                                                                                                                                                                                                                        |
   |---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |           **Deshabilitar**           |                                                                                                                                                                                                                                                                                                                                       Active esta casilla para deshabilitar la barra lateral.                                                                                                                                                                                                                                                                                                                                       |
   | **Definir como barra lateral de error**  |                                                                                                                                                                                                                                         Seleccione esta casilla si desea mostrar esta barra lateral solo cuando hay un error con otra barra lateral, como la falta de privilegios u otro problema que impida que se muestren otras barras laterales asociadas a la página.                                                                                                                                                                                                                                          |
   |   **Convertir en barra lateral de inicio**    |                                                                                                                                                                                                                                                                         La barra lateral de Inicio se muestra cuando un usuario selecciona el botón Inicio o si no hay una barra lateral en la página y el usuario selecciona Ayuda. Cada página puede tener únicamente una barra lateral de inicio.                                                                                                                                                                                                                                                                         |
   |            **Nombre**             |                                                                                                                                                                                                                                                                                                                                    El nombre que se muestra en la biblioteca de contenido.                                                                                                                                                                                                                                                                                                                                     |
   |           **Cliente**            | El valor del cliente se establece automáticamente para la plataforma en la que está creando contenido. **Advertencia:** Si edita un control existente cuando está conectado a una interfaz distinta de aquella en la que se creó el control, el valor del cliente se actualizará con el tipo de cliente actual. Esto hará que el control se rompa y no funcione en el cliente para el que se creó originalmente el control. <br /><br /> Si está creando controles para la interfaz web, aparece **Cliente web**.<br /><br /> Si está conectado al simulador de la interfaz de la aplicación móvil, se muestra **Aplicaciones móviles**.<br /><br /> Si está conectado el centro de servicio interactivo, aparece **Centro de servicio interactivo** . |
   |         **Factor de forma**         |                                                  El factor de forma mostrado depende de la interfaz para la que está creando contenido. Si usa la interfaz del cliente web, se muestran **Escritorio** y **Tableta**. Cuando está seleccionada para el cliente web, **Tableta** hace referencia a los exploradores que se ejecutan en dispositivos de tableta, no a la aplicación móvil.<br /><br /> Si está creando controles para la interfaz de la aplicación móvil, aparece **Tableta**. Esto hace referencia a dispositivos que ejecutan la aplicación móvil de [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)], pero solo se admite en tabletas.<br /><br /> Si usa el centro de servicio interactivo, aparece **Escritorio**.                                                  |
   |     **La barra lateral se abre cuando**      |                                                                                                                                                                                                                                                                                               Seleccione si desea que la barra lateral aparezca cuando se cargue la página o cuando un usuario seleccione un vínculo o un botón de la página.                                                                                                                                                                                                                                                                                               |
   |       **Fase del ciclo de vida**       |                                                                                                                                                                                                                                                                                                                                              Esto es solo para uso interno.                                                                                                                                                                                                                                                                                                                                               |
   | **Rol de seguridad de Common Data Service** |                                                                                                                                                                                                                  Seleccione el rol o roles de seguridad para los que desea mostrar la barra lateral. Puede seleccionar todos los roles que desee. Si a un usuario se le asigna más de un rol, la barra lateral aparecerá solamente para el rol con la mayor prioridad, como se describió anteriormente en este tema.                                                                                                                                                                                                                   |
   |          **Plantilla**           |                                                                                                                                                                                                                                                                                       Seleccione la plantilla que va a usar la nueva barra lateral, **Una sola columna** o **Dos columnas**. La plantilla predeterminada es una barra lateral de una sola columna.                                                                                                                                                                                                                                                                                        |
   |           **Estado**            |                                                                                                                                                                                                                                                                                                              Muestra el estado de la barra lateral. El estado será **Borrador** hasta que publique la barra lateral.                                                                                                                                                                                                                                                                                                              |
   |      **Opciones avanzadas**       |                                                                         Esta opción no está disponible hasta que guarde la barra lateral. Están disponibles los siguientes valores en **Opciones avanzadas**:<ul><li>**Deshabilitar encabezado de la barra lateral**</li><li>**Deshabilitar título de la barra lateral**</li><li>**Deshabilitar pie de página de la barra lateral**</li><li>**Autor**: Cambie el autor definido para la barra lateral.</li><li>**Etiquetas**: Agregue o elimine etiquetas aplicadas a esta barra lateral. Use etiquetas para facilitar la búsqueda de contenido en la biblioteca contenido, o clasificar su contenido.</li><li>**Idiomas compatibles**: Seleccione los idiomas para esta barra lateral, y para la importación y la exportación.</li></ul>                                                                         |


5. Cuando haya terminado, seleccione **Guardar** para comenzar a agregar contenido a la barra lateral en el diseñador.  

<a name="SidebarContent"></a>   

### <a name="add-content-to-your-sidebar"></a>Agregar contenido a la barra lateral  

1.  Una vez guardado el nombre y las propiedades de la barra lateral en la biblioteca de contenido, el diseñador se abre.  

2.  Escriba un título para la barra lateral.  

3.  Agregue el contenido que desea mostrar a los usuarios cuando se muestra la barra lateral.  

4.  Para agregar una nueva sección, seleccione **Agregar sección**.  

5.  Para eliminar una sección de la plantilla, seleccione la sección que desee eliminar y, a continuación seleccione el botón **Eliminar**.  

6.  Cuando haya terminado de modificar el contenido en la barra lateral, seleccione **Guardar** para guardar los cambios, y luego cierre la barra lateral con el botón **Cerrar** en la esquina superior derecha para volver a la biblioteca de contenido.  

7.  Seleccione **Administrar** en la parte superior de la página y, después, **Proteger** para guardar los cambios y ponerlos a disposición de otros usuarios que crean contenido.  

### <a name="add-links-to-your-sidebar"></a>Agregar vínculos a la barra lateral  
 Cuando crea una barra lateral, hay varias opciones para agregar vínculos a ella. Puede establecer un vínculo a otra tarea guiada o barra lateral de la Ruta de aprendizaje, a otra página en [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)], o a una página web. Incluso puede buscar temas de ayuda y aprendizaje para vincular cuando se crea una barra lateral. Una vez establecidas las propiedades y los roles de la barra lateral y de estar listo para agregar contenido, siga estos pasos para agregar vínculos a una sección de la barra lateral que ha creado.  

1. En la sección a la que desea agregar vínculos, seleccione el icono **Lista de vínculos**.  

   ![Icono Lista de vínculos seleccionado en una barra lateral de Ruta de aprendizaje](media/lp-sidebar-links.png "Icono Lista de vínculos seleccionado en una barra lateral de Ruta de aprendizaje")  

2. Agregue un título de sección y, a continuación seleccione **+ Agregar vínculo**.  

   ![Cuadro Agregar vínculo destacado en una sección de una barra lateral de Ruta de aprendizaje](media/lp-sidebar-addlink.png "Cuadro Agregar vínculo destacado en una sección de una barra lateral de Ruta de aprendizaje")  

3. Seleccione el tipo de vínculo que desea agregar y luego, seleccione **Siguiente**. Puede elegir entre las siguientes opciones:  

   - **Tarea guiada**: crea un vínculo con una tarea guiada de la Ruta de aprendizaje existente. Esto puede resultar útil para proporcionar la información acerca de una tarea en la barra lateral y, a continuación, vincularla a una tarea guiada que lleva a un usuario a través de la tarea en la interfaz de [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)].  

   - **Barra lateral**: Crea un vínculo a una barra lateral de Ruta de aprendizaje existente. Puede usar un vínculo con una barra lateral para  

   - **Página de la aplicación**  

   - **Página web**  

<a name="Videos"></a>   
## <a name="use-videos-in-your-learning-path-controls"></a>Utilizar vídeos en los controles de Ruta de aprendizaje  
 Solo los vídeos hospedados en YouTube son compatibles con los controles de la Ruta de aprendizaje. Si planea usar vídeos en los controles de la Ruta de aprendizaje, deberá tener una cuenta y un canal de YouTube para cargar vídeos. No puede vincular a vídeos de un canal establecido como privado, pero puede vincular a vídeos si su canal está establecido como público u oculto. También puede configurar el canal de modo que varias personas puedan administrar el contenido de vídeos de la organización.  

 Cuando agrega vídeos a los controles, puede insertar el vídeo en el control. Si desea que los usuarios vean los vídeos en una nueva pestaña o ventana del explorador puede agregar una sección de texto a la barra lateral y luego agregar un vínculo al vídeo en la sección de texto.  

 Cuando inserta vídeos que se muestran en una barra lateral o una tarea guiada, usará el vínculo que obtiene de YouTube. La Ruta de aprendizaje actualizará automáticamente el vínculo para insertar el vídeo y ajustarlo a la barra lateral o la ventana de la tarea guiada. Un usuario puede seleccionar **Pantalla completa** para ver el vídeo en modo de pantalla completa. Si un usuario hace pausa en la reproducción o cuando finaliza la reproducción, YouTube puede automáticamente mostrar vínculos a otros vídeos en los que el usuario puede estar interesado. Puede evitar que esto suceda modificando el vínculo en el control para incluir **?rel=0** al final.  

 Por ejemplo, cuando se crea y carga un vídeo en el canal, se copia la dirección URL del vídeo proporcionada por YouTube, que es **https://youtu.be/4TrYMB4pjyw**. Para insertar este vídeo en un control, especifique esa dirección URL en el campo **Escribir URL del vídeo** para el control.  

 Al guardar el control, Ruta de aprendizaje cambia la dirección URL a **https://www.youtube.com/embed/4TrYMB4pjyw**. Para desactivar la visualización de vínculos a otros vídeos cuando se pausa el vídeo o termina de reproducirse, edite la dirección URL para anexar **?rel=0** al final de manera que la dirección URL sea similar a la siguiente: **https://www.youtube.com/embed/4TrYMB4pjyw?rel=0**.  

Para obtener más información acerca de cómo utilizar YouTube: [Centro de ayuda de YouTube](https://go.microsoft.com/fwlink/?linkid=847120)  

<a name="PublishLP"></a>   
## <a name="publish-learning-path-content"></a>Publicar contenido de la ruta de aprendizaje  
 Los usuarios solo verán contenido de la Ruta de aprendizaje que cree después de que publicarlo. Solo puede publicar contenido protegido.  

1.  Abra la Biblioteca de contenido.  

2.  Active la casilla justo a cada tarea guiada o barra lateral que desee publicar. Asegúrese de que el control que desee publicar está protegido.  

3.  Seleccione **Publicar** en la parte superior de la página, y después **Publicar**.  

4.  En la página **Publicar controles**, seleccione los entornos de publicación en los que desea publicar el contenido y, a continuación, seleccione **Publicar**.  

<a name="PublishingGroup"></a>   
### <a name="about-publishing-groups"></a>Acerca de los grupos de publicación  
 El contenido de la Ruta de aprendizaje se publica en un grupo de publicación. Cuando activa la Ruta de aprendizaje para su organización, se creará un grupo de publicación con el mismo nombre que el nombre de la organización. Puede crear grupos de publicación adicionales según sea necesario. Puede agregar varias organizaciones a un grupo de publicación y una organización puede ser miembro de varios grupos de publicación de modo que pueda personalizar contenido y publicarlo fácilmente en distintas organizaciones.  

<a name="CreatePG"></a>   
### <a name="create-a-publishing-group"></a>Crear un grupo de publicación  

1.  Abra la Biblioteca de contenido.  

2.  Seleccione **Configuración** en la parte superior de la pantalla.  

3.  Seleccione **Configuración de publicación**.  

4.  En la página **Configuración de publicación**, seleccione **Nuevo PG**.  

5.  Introduzca un nombre y una descripción opcional.  

6.  Seleccione las organizaciones que desea incluir en el grupo de publicación. Verá sólo las organizaciones para las que tiene permisos.  

7.  Seleccione **Guardar** y, a continuación, **Aceptar**.  

<a name="ExportandImport"></a>   
## <a name="export-and-import-learning-path-content"></a>Exportar e importar contenido de Ruta de aprendizaje  
 Puede exportar el contenido que crea, para compartir con un autor de otra organización, o para realizar las copias de seguridad. La característica de exportación crea un archivo comprimido .zip que contiene archivos .json usados para su contenido en la Ruta de aprendizaje. Habrá una carpeta en el archivo .zip para cada barra lateral o tarea guiada de la Ruta de aprendizaje seleccionada.  

<a name="ExportProc"></a>   
### <a name="export-your-learning-path-content"></a>Exportar contenido de Ruta de aprendizaje  

1.  En la biblioteca de contenido, seleccione la casilla situada junto al contenido que desea exportar.  

     Puede exportar contenido sin protegerlo.  

2.  Seleccione **Administrar** en la parte superior de la página, y después **Exportar**.  

3.  Seleccione la opción que desea usar para guardar el archivo .zip generado, y luego seleccione un nombre de archivo y una ubicación.  

    > [!NOTE]
    >  El nombre de archivo predeterminado para el archivo .zip es el mismo cada vez que exporta, por lo que conviene usar un nombre único para evitar sobrescribir los archivos exportados anteriormente.  

### <a name="import-your-learning-path-content"></a>Importar contenido de Ruta de aprendizaje  

1.  En la biblioteca del contenido, seleccione **Administrar** y después **Importar**.  

2.  Seleccione **Examinar** para elegir el archivo exportado previamente que desea importar, o arrastre el archivo al cuadro **Arrastre aquí los controles** del diálogo.  

    > [!CAUTION]
    >  Al importar un control, sobrescribirá y reemplazará las versiones del mismo control que ya están en la biblioteca, incluso si el control existente es más reciente.  

3.  Confirme que el nombre de archivo mostrado corresponde al archivo que desea importar y, a continuación, seleccione **Importar**.  

4.  En el cuadro de diálogo de confirmación, seleccione **Aceptar**.  

<a name="Localize"></a>   
## <a name="localize-learning-path-controls"></a>Localizar controles de la ruta de aprendizaje  
 Puede buscar el contenido en los controles que crea en Ruta de aprendizaje para se muestren a los usuarios en el idioma que han seleccionado para [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]. Para buscar los controles, puede exportarlos simplemente, buscar las cadenas que se muestran a los usuarios, y luego importar el control que incluye contenido localizado. Puede importar el control en la misma organización o en otra organización según lo desee. Puede buscar el mismo control en varios idiomas y después importar sólo los idiomas específicos en las organizaciones específicas que admiten al usuario con ese idioma seleccionado. La compatibilidad de localización en Ruta de aprendizaje sigue el estándar Formato de archivo de intercambio de localización XML (XLIFF) 2.0 de OASIS. Hay herramientas y tutoriales libremente disponibles para trabajar con este formato común. Más información: [XLIFF Versión 2.0](https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.html).  

 Para obtener más información sobre la configuración de idioma de [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)], consulte [Configurar opciones personales](/dynamics365/customer-engagement/basics/set-personal-options).  

1.  Seleccione el control que desea localizar en la Biblioteca de contenido.  

2.  Seleccione **Localizar**y, después, **Exportar**.  

    ![Botón Exportar en el menú Localización de Ruta de aprendizaje](media/lp-localize-export.png "Botón Exportar en el menú Localización de Ruta de aprendizaje")  

3.  Seleccione la opción que desea usar para guardar el archivo .zip generado, y luego seleccione un nombre de archivo y una ubicación.  

    > [!NOTE]
    >  El nombre de archivo predeterminado para el archivo .zip es el mismo cada vez que exporta, por lo que conviene usar un nombre único para evitar sobrescribir los archivos exportados anteriormente.  

4.  Después de localizar el contenido, en la Biblioteca de contenido seleccione **Localizar** y después **Importar**.  

5.  Seleccione **Examinar** para elegir el archivo exportado previamente que desea importar, o arrastre el archivo al cuadro **Arrastre aquí los controles** del diálogo.  

    > [!CAUTION]
    >  Al importar un control, sobrescribirá y reemplazará las versiones del mismo control que ya están en la biblioteca, incluso si el control existente es más reciente.  

6.  Confirme que el nombre de archivo mostrado corresponde al archivo que desea importar y, a continuación, seleccione **Importar**.  

7.  En el cuadro de diálogo de confirmación, seleccione **Aceptar**.  

8.  Publique el control localizado en los entornos de publicación deseados para poner el control localizado a disposición de los usuarios. El contenido localizado se mostrará automáticamente a los usuarios que han seleccionado el mismo idioma para su interfaz de usuario.  



## <a name="includepn_crm_shortestincludespn-crm-shortestmd-apps-data-center-mapping-to-includepn-azure-shortestincludespn-azure-shortestmd-regions"></a>Asignación de centro de datos de aplicaciones [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] a regiones de [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]
La siguiente tabla enumera las regiones de centros de datos de aplicaciones [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] y las correspondientes regiones de [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] desde las que estará disponible la Ruta de aprendizaje.


| [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] centro de datos | [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] región |
|------------------------------------------------------------------------|------------------------------------------------------------------------|
|                          Asia-Pacífico (APAC)                           |                               Asia oriental                                |
|                              Canadá (CAN)                              |                             Canadá Central                             |
|       Europa, Oriente Medio, África y Gran Bretaña (EMEA, GBR)       |                              Europa Occidental                               |
|                              India (IND)                               |                             Centro de la India                              |
|                              Japón (JPN)                               |                               Japón oriental                               |
|                          Norteamérica (NAM)                           |                                Este de EE. UU.                                 |
|                             Oceanía (OCE)                              |                             Australia oriental                             |
|                          Sudamérica (SAM)                           |                              Sur de Brasil                              |

## <a name="privacy-notice"></a>Aviso de privacidad  
[!INCLUDE[cc_privacy_learning_path_authoring](../../includes/cc-privacy-learning-path-authoring.md)]

### <a name="see-also"></a>Vea también  
 [Modificador encendido/apagado para Ruta de aprendizaje (ayuda guiada)](/dynamics365/customer-engagement/admin/on-off-switch-for-learning-path-guided-help)
