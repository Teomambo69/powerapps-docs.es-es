---
title: Elegir y configurar columnas en vistas de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Aprenda a seleccionar y configurar vistas para la aplicación
keywords: ''
ms.date: 06/11/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 31bfcf18-58c3-491c-91b5-f9b0f5424852
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 25
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-choose-and-configure-columns-in-model-driven-app-views"></a>Tutorial: Elegir y configurar columnas en vistas de aplicaciones controladas por modelos

<a name="BKMK_ChooseAndConfigureColumns"></a>   

 Junto con los criterios de filtro, las columnas visibles en una vista de PowerApps son muy importantes para el valor proporcionado por la vista. En este tutorial, creará o editará vistas realizando las siguientes tareas:  

-   [Abrir el editor de vistas](choose-and-configure-columns.md#open-the-view-editor)  
   
-   [Agregar columnas](choose-and-configure-columns.md#BKMK_AddColumns)  
  
-   [Quitar columnas](choose-and-configure-columns.md#BKMK_RemoveColumns)  
  
-   [Cambiar el ancho de columna](choose-and-configure-columns.md#BKMK_ChangeColumnWidth)  
  
-   [Mueva una columna](choose-and-configure-columns.md#BKMK_MoveAColumns)  
  
-   [Habilite o deshabilite presencia para una columna](choose-and-configure-columns.md#BKMK_EnableOrDisablePresence)  
  
-   [Agregue columnas de búsqueda](choose-and-configure-columns.md#BKMK_AddFindColumns)  

### <a name="open-the-view-editor"></a>Abrir el editor de vistas

1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**. 

    > [!div class="mx-imgBorder"] 
    > ![Vistas](media/available-views.png)

3. Seleccione una vista existente para abrirla o, en la barra de herramientas, seleccione **Agregar vista**. 

<a name="BKMK_AddColumns"></a>   
### <a name="add-columns"></a>Agregar columnas  
 Puede incluir las columnas de la entidad actual o de cualquier entidad relacionada que tenga una relación de entidad 1:N con la entidad actual.  
  
 Por ejemplo, es posible que desee mostrar el propietario de una entidad propiedad del usuario en una columna. Puede elegir el campo **Propietario** de la entidad actual para mostrar el nombre del propietario. Esto aparecerá como un vínculo para abrir el registro **Usuario** de la persona que es el propietario. En este caso, también tendrá la opción de [habilitar o inhabilitar la presencia de una columna](choose-and-configure-columns.md#BKMK_EnableOrDisablePresence).  
  
 Si desea que muestre el número de teléfono del propietario del registro, debe seleccionar **Usuario propietario (usuario)** en el cuadro desplegable **Tipo de registro** y luego seleccione el campo **Teléfono principal**.  
  
#### <a name="add-columns-to-views"></a>Agregue columnas a vistas  
  
1.  Mientras crea y editar vistas, seleccione **Agregar columnas**. 

    > [!div class="mx-imgBorder"] 
    > ![Editor de vistas - Agregar columnas](media/view-editor.png)

    Se abre el cuadro de diálogo **Agregar columnas**.

    > [!div class="mx-imgBorder"] 
    > ![Agregar columnas](media/add-columns.png)
  
2.  Seleccione el **Tipo de registro** si desea incluir campos de entidades relacionadas.  
  
3.  Puede seleccionar varios campos, incluso de entidades relacionadas.  
  
4.  Cuando haya seleccionado los campos que desea, seleccione **Aceptar** para cerrar el cuadro de diálogo **Agregar columnas**.  
  
 Al agregar columnas, se incrementará el ancho de la vista. Si el ancho de la vista supera el espacio disponible para mostrarlo en la página, las barras horizontales de navegación permitirán desplazarse y ver las columnas ocultas.  
  
> [!TIP]
>  Si la vista filtra los datos de un determinado campo para mostrar únicamente los registros con determinado valor, no incluya esa columna en la vista. Por ejemplo, si solo muestra registros activos, no incluya la columna de estado en la vista. En su lugar, asigne un nombre a la vista para indicar que todos los registros que se muestran en la vista están activos.  
  
> [!NOTE]
>  Al agregar columnas a las vistas de búsqueda para entidades actualizadas, solo las primeras tres columnas se mostrarán.  
  
<a name="BKMK_RemoveColumns"></a>   
### <a name="remove-columns"></a>Quitar columnas  
  
1.  Cuando esté creando y editando vistas, elija la columna que desee quitar.  
  
2.  En el área **Tareas comunes**, seleccione **Quitar**.  
  
3.  En el mensaje de confirmación, seleccione **Aceptar**.  
  
<a name="BKMK_ChangeColumnWidth"></a>   
### <a name="change-column-width"></a>Cambiar el ancho de columna  
  
1.  Cuando esté creando y editando vistas, elija la columna que desee cambiar.  
  
2.  En el área **Tareas comunes**, seleccione **Cambiar propiedades**.  
  
3.  En el cuadro de diálogo **Cambiar propiedades de columna**, elija una opción para establecer el ancho de columna y, a continuación, seleccione **Aceptar**.  
  
<a name="BKMK_MoveAColumns"></a>   
### <a name="move-a-column"></a>Mueva una columna  
  
1.  Cuando esté creando y editando vistas, elija la columna que desee mover.  
  
2.  En el área **Tareas comunes**, desplace la columna hacia la derecha o izquierda con las teclas de flecha.  
  
<a name="BKMK_EnableOrDisablePresence"></a>   
### <a name="enable-or-disable-presence-for-a-column"></a>Habilite o deshabilite presencia para una columna  
 Cuando se cumplen las siguientes condiciones, los usuarios pueden ver un control de presencia en línea de Skype Empresarial en listas que muestra si la persona está disponible y permite interactuar con ella por mensajería instantánea:  
  
-   Las personas usan Edge o Internet Explorer.  
  
-   Las personas tienen Skype Empresarial instalado.  
  
-   Las personas tienen Microsoft ActiveX habilitado en Internet Explorer.  
  
-   Su organización ha habilitado la presencia para el sistema en la configuración del sistema.  
  
 El control de presencia y el valor para habilitarlo solo están disponibles para columnas que muestran campos principales para entidades habilitadas para correo electrónico (usuarios, contactos, oportunidades, clientes potenciales o entidades personalizadas).  
  
#### <a name="enable-or-disable-skype-for-business-presence-for-a-column"></a>Habilitar o deshabilitar la presencia de Skype Empresarial para una columna  
  
1.  Cuando esté creando y editando vistas, elija la columna que desee cambiar.  
  
2.  En el área **Tareas comunes**, seleccione **Cambiar propiedades**.  
  
3.  En el cuadro de diálogo **Cambiar propiedades de columna**, active o desactive **Habilitar presencia para esta columna** y, a continuación, seleccione **Aceptar**.  
  
<a name="BKMK_AddFindColumns"></a>   
### <a name="add-find-columns"></a>Agregue columnas de búsqueda  
 Las columnas de búsqueda son las columnas en las que busca la aplicación cuando los usuarios usan el cuadro de texto **buscar registros** mostrado para listas o siempre que existe la posibilidad de buscar registros para una entidad en la aplicación, como cuando los usuarios buscan un registro para un campo de búsqueda.  
  
1.  Abra una vista de **Búsqueda rápida**. Para obtener información sobre las vistas de búsqueda rápida, consulte [Tipos de vistas](create-edit-views.md#types-of-views).  
  
2.  Seleccione **Agregar columnas de búsqueda** para abrir el cuadro de diálogo.  
  
3.  Seleccione los campos que contienen los datos que desea buscar.  
  
4.  Seleccione **Aceptar** para cerrar el cuadro de diálogo **Agregar columnas de búsqueda**.  

## <a name="community-tools"></a>Herramientas de la Comunidad

El **Replicador de diseños de vista** y el **Diseñador de vistas** son herramientas que proporciona la comunidad de XrmToolbox para Dynamics 365 Customer Engagement. Consulte el tema [herramientas para desarrolladores](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) para comunidad de herramientas desarrolladas.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft Dynamics y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com). 

## <a name="next-steps"></a>Pasos siguientes
[Creación o edición de vistas](create-edit-views.md)
