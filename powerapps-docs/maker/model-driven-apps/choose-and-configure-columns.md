---
title: Elegir y configurar columnas en vistas de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Aprenda a seleccionar y configurar vistas para la aplicación
keywords: ''
ms.date: 11/27/2018
ms.service: powerapps
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

# <a name="choose-and-configure-columns-in-model-driven-app-views"></a>Elegir y configurar columnas en vistas de aplicaciones controladas por modelos

<a name="BKMK_ChooseAndConfigureColumns"></a>   

 Junto con los criterios de filtro, las columnas visibles en una vista de PowerApps son muy importantes para el valor proporcionado por la vista. En este tema, creará o editará vistas realizando las siguientes tareas:  

-   [Abrir el editor de vistas](choose-and-configure-columns.md#open-the-view-editor)  
   
-   [Agregar columnas](choose-and-configure-columns.md#BKMK_AddColumns)  
  
-   [Quitar columnas](choose-and-configure-columns.md#BKMK_RemoveColumns)  
  
-   [Cambiar el ancho de columna](choose-and-configure-columns.md#BKMK_ChangeColumnWidth)  
  
-   [Mueva una columna](choose-and-configure-columns.md#BKMK_MoveAColumns)  
    
  > [!IMPORTANT]
  > La versión más reciente del diseñador de vistas está funcionando actualmente en vista previa. Algunas características como habilitar o deshabilitar la presencia de una columna y agregar una columna de búsqueda aún no se admiten. Para realizar estas tareas [abra la vista en el diseñador clásico de vistas](/dynamics365/customer-engagement/customize/create-and-edit-views#open-the-classic-view-designer).
  >  -   [Habilite o deshabilite presencia para una columna](/dynamics365/customer-engagement/customize/choose-and-configure-columns#BKMK_EnableOrDisablePresence)  
  >
  >  -   [Agregue columnas de búsqueda](/dynamics365/customer-engagement/customize/choose-and-configure-columns#BKMK_AddFindColumns) 



### <a name="open-the-view-editor"></a>Abrir el editor de vistas

1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**. 

    > [!div class="mx-imgBorder"] 
    > ![Vistas](media/available-views.png)

3. Seleccione una vista existente para abrirla o, en la barra de herramientas, seleccione **Agregar vista**. 

<a name="BKMK_AddColumns"></a>   
### <a name="add-columns"></a>Agregar columnas  
 Puede incluir las columnas de la entidad actual o de cualquier entidad relacionada que tenga una relación de entidad 1:N con la entidad actual.  
  
 Por ejemplo, es posible que desee mostrar el propietario de una entidad propiedad del usuario en una columna. Puede elegir el campo **Propietario** de la entidad actual para mostrar el nombre del propietario. Esto aparecerá como un vínculo para abrir el registro **Usuario** de la persona que es el propietario.  
  
 Si desea que muestre el número de teléfono del propietario del registro, debe seleccionar **Usuario propietario (usuario)** en el cuadro desplegable **Tipo de registro** y luego seleccione el campo **Teléfono principal**.  
  
#### <a name="add-columns-to-views"></a>Agregue columnas a vistas  
  
1.  Mientras crea y edita las vistas, asegúrese que el panel **Campos** está abierto. Si no es así, seleccione **Agregar campos** en la barra de herramientas. 

    > [!div class="mx-imgBorder"] 
    > ![Editor de vistas - Agregar columnas](media/fields-drawer-view-designer.png)

2.  Seleccione los campos que desee agregar al diseñador de vistas. Esto agrega el campo como una columna en la mano derecha de la vista.

3.  Seleccione la pestaña **Relacionado** para ver las entidades relacionadas y los campos correspondientes.
  
 Al agregar columnas, se incrementará el ancho de la vista. Si el ancho de la vista supera el espacio disponible para mostrarlo en la página, las barras horizontales de navegación permitirán desplazarse y ver las columnas ocultas.  
  
> [!TIP]
>  Si la vista filtra los datos de un determinado campo para mostrar únicamente los registros con determinado valor, no incluya esa columna en la vista. Por ejemplo, si solo muestra registros activos, no incluya la columna de estado en la vista. En su lugar, asigne un nombre a la vista para indicar que todos los registros que se muestran en la vista están activos.  
  
> [!NOTE]
>  Al agregar columnas a las vistas de búsqueda para entidades actualizadas, solo las primeras tres columnas se mostrarán.  
  
<a name="BKMK_RemoveColumns"></a>   
### <a name="remove-columns"></a>Quitar columnas  
  
1.  Seleccione el encabezado de la columna que desee quitar.  
  
2.  En el menú desplegable, seleccione **Quitar**.  
  
<a name="BKMK_ChangeColumnWidth"></a>   
### <a name="change-column-width"></a>Cambiar el ancho de columna  
  
1.  Pase el puntero por el área entre las columnas de la vista.  
  
2.  Una línea aparece y el cursor se convierte en una flecha doble.  
  
3.  Arrastre la columna hasta el ancho adecuado.  
  
<a name="BKMK_MoveAColumns"></a>   
### <a name="move-a-column"></a>Mueva una columna  
  
Haga clic en el encabezado de columna y arrástrelo a la ubicación correcta.
  
> [!TIP]
>   También puede seleccionar el encabezado de la columna que desea mover y desde el desplegable seleccione **Mover a la derecha** o **Mover a la izquierda**.  


  
## <a name="next-steps"></a>Pasos siguientes
[Creación o edición de vistas](create-edit-views.md)
