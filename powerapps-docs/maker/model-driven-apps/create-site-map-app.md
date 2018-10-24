---
title: Creación de un mapa del sitio para aplicaciones basadas en modelos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo crear un mapa del sitio de la aplicación.
keywords: ''
ms.date: 05/29/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 2461bd71-6cb4-46b7-8d1f-6a0aa3dca809
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 18
topic-status: Drafting
ms.openlocfilehash: 2c3f1f4f22df6ed8b4824f1942e3fd202362ea9d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39700630"
---
# <a name="tutorial-create-a-model-driven-app-site-map-for-an-app-using-the-site-map-designer"></a>Tutorial: Crear un mapa del sitio para una aplicación basada en modelos con el diseñador de mapas del sitio

En este tutorial realizará varias tareas del mapa del sitio, como crear un nuevo mapa del sitio y agregar un área, un grupo y una subárea.

Los mapas del sitio definen la navegación para su aplicación. Cree un mapa del sitio para su aplicación con facilidad usando el diseñador de mapas del sitio basado en ventanas. Use el diseñador para arrastrar componentes al lienzo de diseño, realizar una vista previa del trabajo y publicar inmediatamente el mapa del sitio. Los personalizadores del sistema o cualquier usuario con los privilegios necesarios pueden crear rápidamente mapas del sitio para aplicaciones.  
  
El diseñador de mapas del sitio además le permite definir los títulos de áreas, subáreas o grupos en los idiomas admitidos por el entorno.  
  
Un mapa del sitio predeterminado está disponible. Puede editar este mapa del sitio o configurar mapas del sitio para nuevas aplicaciones mediante el diseñador de mapas del sitio. El diseñador de mapas del sitio está integrado con el diseñador de aplicaciones.  

## <a name="prerequisites"></a>Requisitos previos
Compruebe que tiene el rol de seguridad de Administrador del sistema o de Personalizador del sistema o permisos equivalentes.  Concretamente, cualquier usuario con los siguientes privilegios también puede crear aplicaciones:  
-   Privilegios de Crear, Leer y Escribir para la entidad Aplicación  
-   Privilegios de Leer y Escribir para la entidad Personalizaciones  
-   Privilegios de Leer para la entidad Solución

Puede ver o establecer estos privilegios en la pestaña **Personalización** de un rol de seguridad.
  
## <a name="create-a-site-map-for-an-app"></a>Creación de un mapa del sitio para una aplicación  
  
1. En el lienzo del diseñador de aplicaciones, en el área **Mapa del sitio**, seleccione **Abrir el diseñador del mapa del sitio** ![Botón Abrir el diseñador del mapa del sitio](media/dynamics365-open-designer.PNG "Botón Abrir el diseñador del mapa del sitio").  
  
     El diseñador del mapa del sitio abre un lienzo relleno previamente con un área, un grupo y una subárea. Seleccione la ventana de área, grupo o subárea para modificar sus propiedades.  
  
    > [!NOTE]
    >  Al seleccionar **Abrir el diseñador del mapa del sitio** ![Botón Abrir el diseñador del mapa del sitio](media/dynamics365-open-designer.PNG "Botón Abrir el diseñador del mapa del sitio") desde el lienzo del diseñador de aplicaciones, se crea automáticamente un nuevo mapa del sitio (si no hay un mapa del sitio existente) y se asigna al mapa del sitio el mismo nombre que el nombre de la aplicación y el mismo nombre único que el nombre único de la aplicación. 

   ![Seleccionar mapa del sitio](media/app-designer-sitemap-location.png "Seleccionar un mapa del sitio") 
  
2.  [Agregar un área al mapa del sitio](create-site-map-app.md#bkmk_AddArea).  
  
3.  [Agregar un grupo al mapa del sitio](create-site-map-app.md#bkmk_AddGroup).  
  
4.  [Agregar una subárea a un grupo en el mapa del sitio](create-site-map-app.md#bkmk_AddSubarea).  
  
5.  Seleccione **Guardar**.  
  
    > [!NOTE]
    >  El nuevo mapa del sitio se asocia con la aplicación al volver al diseñador de la aplicación y hacer clic en seleccionar **Guardar**. Cuando se configura un mapa del sitio, **Configurado** aparece en la ventana del mapa del sitio; de lo contrario, **No se ha configurado** aparece en la ventana.  Si abre el diseñador del mapa del sitio desde el diseñador de la aplicación y configura un nuevo mapa del sitio, pero cierra el explorador antes de asociar el mapa del sitio a la aplicación, el mapa del sitio se asociará automáticamente con la aplicación la próxima vez que abra el diseñador de la aplicación, en función del nombre único de la aplicación.  
  
6.  Haga clic en **Publicar**.  
  
## <a name="edit-the-default-site-map"></a>Edición del mapa del sitio predeterminado 

 El entorno incluye un mapa del sitio predeterminado.  
  
1. Abra el Explorador de soluciones.  
  
2. En la ventana solución, en la lista **Componentes** seleccione **Extensiones de cliente**.  

3. En la barra de herramientas del componente, seleccione **Agregar existente** > **Mapa del sitio**.

4. En la lista de componentes de la solución, seleccione el mapa del sitio llamado **Mapa del sitio** y, a continuación, seleccione **Aceptar**.
  
5.  Haga doble clic para seleccionar el mapa del sitio que agregó que tiene el nombre para mostrar **Mapa del sitio** y está en estado **Administrado**. También puede seleccionar el mapa del sitio y, en la barra de herramientas, seleccione **Editar**.  
  
     El mapa del sitio se abre en el diseñador del mapa del sitio.  
  
6.  [Agregar un área al mapa del sitio](create-site-map-app.md#bkmk_AddArea).  
  
7.  [Agregar un grupo al mapa del sitio](create-site-map-app.md#bkmk_AddGroup).  
  
8.  [Agregar una subárea a un grupo en el mapa del sitio](create-site-map-app.md#bkmk_AddSubarea).  
  
9. Seleccione **Guardar**.  
  
10. Haga clic en **Publicar**.  
  
<a name="bkmk_AddArea"></a>   
## <a name="add-an-area-to-the-site-map"></a>Agregar un área al mapa del sitio  
  
1.  Seleccione **Agregar** ![Botón Agregar del diseñador](media/dynamics365-designer-addbutton.PNG "Botón Agregar del diseñador") en el lienzo del diseñador del mapa del sitio y, a continuación, seleccione **Área**.  
  
     O bien  
  
     En la pestaña **Componentes**, arrastre la ventana **Área** para vaciar el cuadro en el lienzo. Verá el cuadro vacío cuando mueva la ventana a la ubicación correcta en el lienzo.  
  
2.  Seleccione el área que acaba de agregar. Verá la pestaña **Propiedades** resaltada en el panel derecho del lienzo.  
  
3.  Agregue o edite las propiedades del área.  
  
     En **General**, haga lo siguiente:  
  
    - **Ventana**: escriba el título del área en el idioma base de la organización.  
  
    - **Icono**: está seleccionado un icono de aplicación predeterminado. Seleccione otro icono para el área de la lista de recursos web disponibles en la solución.  
  
    - **Identificador**: se genera un identificador único automáticamente, pero puede escribir otro diferente si lo desea. Se recomienda usar el identificador proporcionado porque, si el identificador que especifica no es único, los usuarios podrían recibir un error cuando utilicen la aplicación o usted podría recibir un error al importar una solución que contenga este mapa del sitio.  
  
    - **Mostrar grupos**: seleccione esta casilla para mostrar grupos de subáreas en el panel de navegación.  
  
     En **Avanzado**, haga lo siguiente:  
  
    - **Más ventanas**: si su organización usa varios idiomas, seleccione un idioma (configuración regional) para el título, escriba el título y, a continuación, seleccione el botón **Agregar** ![Botón Agregar del diseñador del mapa del sitio](media/add-icon-sitemap-designer.png "Botón Agregar del diseñador del mapa del sitio"). Puede crear, editar o eliminar títulos para tantos idiomas como use la organización. Sin embargo, puede tener solo un título por idioma.  
  
    - **Más descripción**: Si su organización usa varios idiomas, seleccione un idioma para la descripción, escriba la descripción y, a continuación, seleccione el botón **Agregar** ![Botón Agregar del diseñador del mapa del sitio](media/add-icon-sitemap-designer.png "Botón Agregar del diseñador del mapa del sitio"). Puede crear, editar o eliminar descripciones para tantos idiomas como use la organización. Sin embargo, puede tener solo una descripción por idioma.  
  
    - **Dirección URL**: escriba la dirección URL para presentar la carpeta de Dynamics 365 para Outlook que representa el área.  
  
<a name="bkmk_AddGroup"></a>   
## <a name="add-a-group-to-the-site-map"></a>Agregar un grupo al mapa del sitio  
  
1.  En el lienzo del diseñador del mapa del sitio, seleccione el área a la que desea agregar el grupo.  
2.  Seleccione **Agregar** ![Botón Agregar en el diseñador](media/dynamics365-designer-addbutton.PNG "Botón Agregar en el diseñador") y, a continuación, seleccione **Grupo**.  
  
     O bien  
  
     En la pestaña **Componentes**, arrastre la ventana **Grupo** a un cuadro vacío del **Área** en el lienzo. Verá el cuadro vacío cuando mueva la ventana a la ubicación correcta en el lienzo.  
  
3.  Seleccione el grupo que acaba de agregar.  
  
4.  En la pestaña **Propiedades**, agregue o edite las propiedades del grupo:  
  
     En **General**, haga lo siguiente:  
  
    - **Ventana**: escriba el título del grupo en el idioma base de la organización.  
  
    - **Identificador**: se genera automáticamente un identificador único. Escriba otro diferente si es necesario. Se recomienda usar el identificador automático porque si el identificador que especifica no es único, podría recibir un error cuando importa una solución que contenga este mapa del sitio.  
  
     En **Avanzado**, haga lo siguiente:  
  
    - **Más ventanas**: si su organización usa varios idiomas, seleccione un idioma (configuración regional) para el título, escriba el título del grupo y, a continuación, seleccione el botón **Agregar** ![Botón Agregar del diseñador del mapa del sitio](media/add-icon-sitemap-designer.png "Botón Agregar del diseñador del mapa del sitio"). Puede crear, editar o eliminar títulos para tantos idiomas como use la organización. Sin embargo, puede tener solo un título por idioma.  
  
    - **Más descripciones**: si su organización usa varios idiomas, seleccione un idioma para la descripción, escriba la descripción del grupo y, a continuación, seleccione el botón **Agregar** ![Botón Agregar del diseñador del mapa del sitio](media/add-icon-sitemap-designer.png "Botón Agregar del diseñador del mapa del sitio"). Puede crear, editar o eliminar descripciones para tantos idiomas como use la organización. Sin embargo, puede tener solo una descripción por idioma.  
  
    - **Dirección URL**: escriba la dirección URL para presentar la carpeta de Dynamics 365 para Outlook que representa el grupo.  
  
    - **Establecer como perfil**: seleccione esta casilla para indicar si este grupo representa un perfil de usuario seleccionable para el área de trabajo. El grupo establecido como perfil seleccionable por el usuario para a estar disponible como opciones en sus opciones personales. Esto solo se aplica a grupos dentro del área de **Área de trabajo**.  
  
<a name="bkmk_AddSubarea"></a>   
## <a name="add-a-subarea-to-a-group-in-the-site-map"></a>Agregar una subárea a un grupo en el mapa del sitio  
  
1.  Seleccione **Agregar** ![Botón Agregar del diseñador](media/dynamics365-designer-addbutton.PNG "Botón Agregar del diseñador") en el lienzo del diseñador del mapa del sitio y, a continuación, seleccione **Subárea**.  
  
     O bien  
  
     En la pestaña **Componentes**, arrastre la ventana **Subárea** a un cuadro vacío de la sección **Grupo** en el lienzo. Verá el cuadro vacío cuando mueva la ventana a la ubicación correcta en el lienzo.  
  
2.  Seleccione la subárea que acaba de agregar.  
  
3.  En la pestaña **Propiedades**, agregue o edite las propiedades de la subárea:  
  
     En **General**, haga lo siguiente:  
  
    - **Tipo**: seleccione si la subárea que agrega es un panel, una entidad, un recurso web, o una dirección URL.  
  
    - **Entidad**: seleccione la entidad a la que pertenece la subárea. Este campo se deshabilita si el tipo de subárea es distinto de **Entidad** en la lista desplegable **Tipo**.  
  
    - **Dirección URL**: especifique una dirección URL para la página principal de la aplicación para mostrar cuando se seleccione este subárea. Este campo se deshabilita si se ha seleccionado **Entidad** en la lista desplegable **Tipo**.  
  
    - **Panel predeterminado**: seleccione el panel predeterminado para mostrar para esta subárea. Este campo se deshabilita si aún no ha seleccionado **Panel** en la lista desplegable **Tipo**.  
  
    - **Ventana**: escriba el título de la subárea en el idioma base de la organización.  
  
    - **Icono**: está seleccionado un icono de aplicación predeterminado. Seleccione otro icono para la subárea de la lista de recursos web disponibles en la solución.  
  
    - **ID**. Se genera automáticamente un identificador único. Escriba otro identificador único si es necesario.  
  
    - **Paso de parámetros**. Seleccione esta casilla para pasar información acerca del contexto de la organización y de idioma a la dirección URL. Esta casilla solo está marcada cuando el tipo de subárea es un recurso web o una subárea basada en dirección URL.  
  
     En **Avanzado**, haga lo siguiente:  
 
    - **Privilegios**: esto define si una subárea se muestra en función de los privilegios disponibles en cualquier rol de seguridad que se asigne al usuario. Seleccione el nombre de la entidad para comprobar los privilegios y, a continuación, seleccione las casillas para asignar privilegios. 
  
    - **Más ventanas**: si su organización usa varios idiomas, seleccione un idioma para el título, escriba el título de la subárea y, a continuación, seleccione el botón **Agregar**. Puede crear, editar o eliminar títulos para tantos idiomas como use la organización. Sin embargo, puede tener solo un título por idioma.  
  
    - **Más descripciones**: si su organización usa varios idiomas, seleccione un idioma para la descripción, escriba la descripción de la subárea y, a continuación, seleccione el botón **Agregar**. Puede crear, editar o eliminar descripciones para tantos idiomas como use la organización. Sin embargo, puede tener solo una descripción por idioma.  
  
    - **SKU**: seleccione las versiones de Dynamics 365 Customer Engagement que muestran esta subárea.  
  
    - **Cliente**: seleccione el tipo de cliente que muestra esta subárea.  
  
    - **Acceso directo a Outlook**: seleccione el icono para mostrar Dynamics 365 para Outlook.  
  
    - **Disponibilidad sin conexión**: seleccione esta casilla para hacer que esta subárea esté disponible para los usuarios cuando estén sin conexión en Dynamics 365 para Outlook.  
  
## <a name="organize-areas-groups-and-subareas"></a>Organizar áreas, grupos y subáreas  
 Puede organizar sus áreas, grupos y subáreas, arrastrándolos a nuevas posiciones. Un cuadro contenedor aparece donde puede colocar las ventanas. Estas son algunas cosas que puede hacer:  
  
-   Mover una subárea a una nueva posición en el mismo grupo o a otro grupo en la misma área.  
  
-   Mover una subárea a una nueva posición en un grupo bajo un área diferente.  
  
-   Mover un grupo a una nueva posición dentro de la misma área.  
  
-   Mover un grupo a una nueva posición en otra área.  
  
-   Mover un área una nueva posición.  
  
## <a name="clone-a-component-in-a-site-map"></a>Clonar un componente en un mapa del sitio  
 Para realizar una copia de un componente existente, seleccione el componente y, en la barra de herramientas, seleccione **Clonar**.  Todos los detalles del componente clonado son iguales a los del componente base excepto el identificador y el título. El identificador se genera aleatoriamente. 
  
 Al clonar un área, el área clonada se agrega a la derecha del área seleccionada actualmente. Al clonar un grupo, el grupo clonado se agrega a la derecha del grupo seleccionado actualmente. Al clonar una subárea, la subárea clonada se agrega bajo la subárea seleccionada actualmente.  
  
## <a name="delete-an-area-group-or-subarea-from-a-site-map"></a>Eliminar un área, un grupo o una subárea de un mapa del sitio  
 Para eliminar un componente del mapa del sitio, seleccione la ventana del componente y en la barra de herramientas, seleccione **Eliminar**. Cuando se elimina un área, también se eliminan todos los grupos y las subáreas del área. De forma similar, cuando se elimina un grupo, se eliminan el grupo y las subáreas que contiene.  
  
## <a name="clients-supported"></a>Clientes compatibles  
 En la tabla siguiente se explican los clientes compatibles para diferentes mapas del sitio.  
 
|Mapas del sitio|Clientes compatibles|  
|---------------|-----------------------|  
|Nuevas aplicaciones| Interfaz unificada y aplicación web de Dynamics 365 Customer Engagement |  
|Mapa del sitio para la aplicación personalizada de Dynamics 365 | Aplicación web de Dynamics 365 Customer Engagement y Dynamics 365 para Outlook |  
|Aplicaciones de negocio predeterminadas (Sales, Sales Hub, Customer Service, Customer Service Hub, Field Service, Project Service Automation)| Aplicación web de Dynamics 365 Customer Engagement e Interfaz unificada|  
 
  
### <a name="next-steps"></a>Pasos siguientes  
 [Creación o edición de aplicaciones](create-edit-app.md)   
 [Agregar o editar componentes de la aplicación](add-edit-app-components.md)
