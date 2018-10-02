---
title: Crear o editar una aplicación basada en modelos utilizando el diseñador de aplicaciones en PowerApps | MicrosoftDocs
description: Aprender a crear o editar aplicaciones mediante el diseñador de aplicaciones
keywords: ''
ms.date: 05/23/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 2a44229e-44f0-4c4e-ba21-a476210d0a12
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 19
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-create-a-model-driven-app-by-using-the-app-designer"></a>Tutorial: Crear o editar una aplicación controlada por modelos utilizando el diseñador de aplicaciones

En este tutorial aprenderá los aspectos básicos de cómo crear y editar una aplicación controlada por modelos usando el diseñador de aplicaciones basado en mosaicos.

## <a name="prerequisites"></a>Requisitos previos
Compruebe los requisitos siguientes antes de empezar a crear una aplicación:
- Un entorno de PowerApps. Más información: [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment)
- Rol de seguridad de administrador del sistema o de personalizador del sistema. Más información: [Acerca de los roles de seguridad predefinidos](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app#about-predefined-security-roles)
 
<a name="createApp"></a>   
## <a name="create-an-app"></a>Crear una aplicación  

1.  En el sitio de [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) seleccione **Controlado por modelos** (parte inferior izquierda del panel de navegación).  

    ![Modo de diseño controlado por modelos](media/model-driven-switch.png)

    > [!IMPORTANT]
    > “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2. Seleccione **Aplicaciones** y, a continuación, seleccione **Crear una aplicación**.

3. En la página **Crear una nueva aplicación**, especifique los siguientes detalles: 

    - **Nombre**: introduzca un nombre para la aplicación.  
  
    - **Nombre único**: El nombre único se completa automáticamente en función del nombre de la aplicación que especifique. Se prefija con un prefijo del editor. Puede cambiar la parte del nombre único que editable. El nombre único sólo puede contener caracteres del idioma inglés y números.  
  
        > [!NOTE]
        >  El prefijo del editor es el texto que se agrega a cualquier entidad o campo creado para una solución que tiene este editor.   
  
    - **Descripción**: Escriba una breve descripción de qué es o hace la aplicación.  
  
    - **Icono**: De forma predeterminada, la casilla en miniatura **Usar aplicación predeterminada** está activada. Para seleccionar otro recurso web como icono para la aplicación, desactive la casilla y seleccione un icono de la lista desplegable. Este icono se mostrará en la ventana de vista previa de la aplicación.  
  
    - Seleccione el tipo de cliente para el que se usará la aplicación.  
  
        - **Interfaz unificada**: Este es el más reciente cliente del explorador web dinámico que tiene una interfaz similar para PC y dispositivos móviles.  

        - **Web**: este es el cliente de explorador web clásico de Dynamics 365 Customer Engagement.  
    
    - **Sufijo de la dirección URL de la aplicación**: La dirección URL de la aplicación se completa automáticamente en función del nombre de la aplicación que especifique. Aparecerá una vista previa del aspecto que tiene la dirección URL completa. La dirección URL de la aplicación debe ser única.  
  
         Por ejemplo: https://\<org>.crm#.dynamics.com/Apps/\<URL de aplicación>

         Para local: http://\<server>/\<org name>/Apps/\<App URL> 
  
      > [!NOTE]
      >  Si desactiva el campo de **sufijo de dirección URL de la aplicación** y después guarda la aplicación, la dirección URL de la aplicación se generará automáticamente con el identificador de la aplicación.  
  
    - **Usar la solución existente para crear la aplicación**: Seleccione esta opción para crear la aplicación desde una lista de soluciones instaladas. Si selecciona esta opción, **Listo** cambia a **Siguiente** en el encabezado. Si selecciona **Siguiente**, la página **Crear aplicaciones desde una solución existente** se abre. En la lista desplegable **Seleccione solución**, seleccione una solución desde donde desea crear la aplicación. Si está disponible algún mapa del sitio para la solución seleccionada, la lista desplegable **Seleccione mapa de sitio** aparecerá. Seleccione mapa del sitio y, a continuación, seleccione **Listo**.

      > [!NOTE]
      > Al seleccionar **Solución predeterminada** cuando se agrega un mapa del sitio, los componentes que están asociados con ese mapa del sitio se agregan automáticamente a la aplicación.  

      ![Usar la solución existente para crear la página de aplicaciones](media/use-existing-solution-to-create-the-app.png "Usar una solución existente para crear la aplicación") 

    - **Elija una página de bienvenida**: Esta opción permite elegir entre los recursos web disponibles en su organización. Las páginas de bienvenida que cree pueden contener información útil para los usuarios, como vínculos a vídeos, instrucciones de actualización o información de introducción. La página de bienvenida aparece cuando se abre una aplicación. Los usuarios pueden seleccionar **No mostrar esta pantalla de bienvenida la próxima vez** en la página de inicio de sesión para deshabilitar la página para que no aparezca la próxima vez que se inicie la aplicación. Para obtener más información acerca de cómo crear un recurso web, por ejemplo, un archivo HTML que pueda usar como página de bienvenida, consulte: [Crear y editar recursos web para extender la aplicación web](create-edit-web-resources.md).  
      
    Para editar propiedades de la aplicación más adelante, vaya a la pestaña **Propiedades** en el diseñador de aplicaciones. Más información: [Administrar propiedades de aplicaciones](manage-app-properties.md)  
  
     > [!NOTE]
     >  No puede cambiar el nombre único y el sufijo de la dirección URL de la aplicación en la pestaña **Propiedades**.  
  
4. Seleccione **Listo** o&mdash;si seleccionó **Usar una solución existente para crear la aplicación**&mdash;seleccione **Siguiente** para elegir entre las soluciones disponibles que se importaron en la organización.  
  
    Una nueva aplicación se crea y se muestra en estado de borrador. Verá el lienzo del diseñador de aplicaciones para la nueva aplicación. Desde ahí puede agregar componentes, como entidades, vistas y paneles para que su aplicación resulte útil. Más información: [Agregar o editar componentes de la aplicación](add-edit-app-components.md)  
   
<a name="editApp"></a>   
## <a name="edit-an-app"></a>Editar una aplicación  
  
1.  En el sitio de [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) seleccione **Controlado por modelos** (parte inferior izquierda del panel de navegación).  

> [!IMPORTANT]
> “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2. En el panel de navegación de la izquierda seleccione **Aplicaciones**, seleccione una aplicación y, en la barra de herramientas, seleccione **Editar**.   

3. En el diseñador de aplicaciones, agregue o edite componentes de la aplicación, según sea necesario. Más información: [Agregar o editar componentes de la aplicación](add-edit-app-components.md)  
 
  
### <a name="next-steps"></a>Pasos siguientes  
 [Agregar o editar componentes de la aplicación](add-edit-app-components.md)   


