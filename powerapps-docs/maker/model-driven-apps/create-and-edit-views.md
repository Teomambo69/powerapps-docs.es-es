---
title: Crear o editar una vista de aplicación controlada por modelos en PowerApps | MicrosoftDocs
description: Aprenda a crear o editar una vista
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-a-model-driven-app-view"></a>Crear o editar una vista de aplicación controlada por modelos

<a name="BKMK_CreatingAndEditingViews"></a>   

 En este tema, creará una nueva vista pública personalizada. También editará una vista existente.  
  
### <a name="create-a-new-view"></a>Crea una vista  
  
1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

    

    > [!IMPORTANT]
    > “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad **Cuenta** que desee y, a continuación, seleccione la pestaña **Vistas**. 

3.  En la barra de herramientas, seleccione **Agregar vista**.  

4.  En el cuadro de diálogo **Ver propiedades**, indique un **Nombre**, como **Cuentas con 25 o más empleados**, opcionalmente una **Descripción** para la vista y, a continuación seleccione **Aceptar**.

    > [!div class="mx-imgBorder"] 
    > ![Ver propiedades](media/view-properties.png)
  
5.  En el panel derecho de tareas comunes, seleccione **Agregar columnas**, en el cuadro **Agregar columnas** seleccione **Número de empleados** y, a continuación seleccione **Aceptar**.  

    > [!div class="mx-imgBorder"] 
    > ![Columna Número de empleados](media/column-no-employees.png)
  
6. En el panel derecho de tareas comunes, seleccione **Editar criterios de filtrado**, en el cuadro de diálogo Editar criterios de filtrado, seleccione **Número de empleados**, seleccione **Es mayor o igual que** y, a continuación, introduzca **25**.  

    > [!div class="mx-imgBorder"] 
    > ![Edite criterios de filtrado](media/edit-filter-criteria.png)

7.  Seleccione **Aceptar** para cerrar el cuadro de diálogo **Editar criterios de filtrado** y, a continuación, seleccione **Guardar y cerrar** en el editor de la vista.  
  
8.  Tenga en cuenta que la vista ahora está disponible en la pestaña **Vistas** en el sitio de PowerApps, lo que permite agregarla a una aplicación.
  
### <a name="edit-a-view"></a>Edite una vista  
  
1.  En la pestaña **Vistas** en el sitio de PowerApps, seleccione la vista **Número de empleados**.
  
2.  Cambie el **Nombre** de la vista a **Número de empleados con 25 o más empleados de Arizona** y, a continuación, seleccione **Aceptar**.  

3.  En el panel derecho de tareas comunes, seleccione **Agregar columnas**, en el cuadro de diálogo **Agregar columnas** seleccione **Dirección 1: ciudad** y, a continuación seleccione **Aceptar**.  

4. En el panel derecho de tareas comunes, seleccione **Edite criterios de filtrado**, en el cuadro de diálogo Editar criterios de filtrado agregue una segunda cláusula de filtro. Seleccione **Dirección 2: estado o provincia**, seleccione **Igual a** y, a continuación, **Arizona**. 

    > [!div class="mx-imgBorder"] 
    > ![Dirección 2: estado o provincia](media/column-address-2-state.png)

5. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Editar criterios de filtrado** y, a continuación, seleccione **Guardar y cerrar** en el editor de la vista.  
  

## <a name="create-a-new-view-from-an-existing-view"></a>Cree una nueva vista a partir de una vista existente  
 Siga el procedimiento para editar una vista, pero en lugar de elegir **Guardar y cerrar**, seleccione **Guardar como** y escriba un nuevo **Nombre** y una **Descripción** de la vista.  
 
### <a name="next-steps"></a>Pasos siguientes
[Elija y configure columnas](choose-and-configure-columns.md)  
  
[Edite criterios de filtrado](edit-filter-criteria.md)  
  
[Configurar la ordenación](configure-sorting.md)  
