---
title: Visualizar datos jerárquicos con aplicaciones controladas por modelos | MicrosoftDocs
description: Aprenda cómo consultar y visualizar datos jerárquicos relacionados
ms.custom: ''
ms.date: 09/19/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="visualize-hierarchical-data-with-model-driven-apps"></a>Visualizar datos jerárquicos con aplicaciones controladas por modelos

Cuando una entidad está configurada para tener una relación jerárquica que hace referencia a sí misma, puede configurar visualizaciones usando esa jerarquía. Más información: [Definir y consultar datos relacionados jerárquicamente](../common-data-service/define-query-hierarchical-data.md)

Las entidades que tienen visualizaciones disponibles de forma predeterminada incluyen [Cuenta](/powerapps/developer/common-data-service/reference/entities/account), [Posición](/powerapps/developer/common-data-service/reference/entities/position) y [Usuario](/powerapps/developer/common-data-service/reference/entities/systemuser). En la vista de cuadrícula de estas entidades, puede ver el icono que muestra el gráfico de jerarquía a la izquierda del nombre del registro. El icono de jerarquía no está presente para todos los registros de forma predeterminada. El icono se muestra para los registros que ya están relacionados con la relación jerárquica.  
> [!div class="mx-imgBorder"] 
> ![Botón Ver jerarquía](media/view-hierarchy-button.png)  
  
 Si selecciona el icono de jerarquía, puede ver la jerarquía, con la vista de árbol a la izquierda y la vista de mosaico a la derecha, como se indica a continuación:  
  
> [!div class="mx-imgBorder"] 
> ![Vista de árbol y ventana en jerarquía](media/tree-view-and-tile-view-in-hierarchy.png)  
  
 Hay más entidades que pueden habilitarse para una jerarquía. Estas entidades incluyen [Contacto](/powerapps/developer/common-data-service/reference/entities/contact) y [Equipo](/powerapps/developer/common-data-service/reference/entities/team). Todas las entidades personalizadas pueden habilitarse para una jerarquía.  
  
Cosas más importantes para recordar al crear visualizaciones:  
  
- Solo se pueden configurar como jerárquica una relación que hace referencia a sí misma (1: N) por entidad. En una relación que hace referencia a sí misma la entidad principal y la entidad relacionada deben ser del mismo tipo.  
- Una jerarquía o una visualización se basa en una entidad solo. Puede describir la jerarquía de cuenta mostrando cuentas en varios niveles, pero no puede mostrar cuentas y contactos en la misma visualización de la jerarquía. 
- El número máximo de campos que se pueden mostrar en una ventana es cuatro. Si desea agregar más campos al formulario rápido que se usa para la vista de mosaico, sólo los primeros cuatro campos se mostrarán. 

## <a name="hierarchy-settings"></a>Configuración de jerarquía

Para habilitar las visualizaciones de una jerarquía debe conectar la jerarquía a un formulario de vista rápida. Esto solo se puede hacer usando el explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Los valores de la jerarquía estás asociados a una entidad en el explorador de soluciones. 

1. Mientras [visualiza entidades](../common-data-service/create-edit-entities-solution-explorer.md#view-entities), seleccione **Configuración de la jerarquía**.
2. Si existe un valor existente de la jerarquía puede editarlo. En caso contrario, haga clic en **Nuevo** para crear uno nuevo.
    
    > [!NOTE]
    > Si no existen los valores de la jerarquía, la entidad no es elegible para tener una jerarquía configurada.
    >Solo puede haber un valor de jerarquía 

1. Defina los datos en los campos siguientes:

|Campo|Descripción|
|--|--|
|**Nombre**|*Requerido.* Agregue un nombre único para la configuración de la jerarquía. Suele ser el nombre de la entidad. Este valor incluirá el prefijo de personalización del editor de soluciones.|
|**Formulario de vista rápida predeterminado**|*Requerido.* Elija un formulario de vista rápida existente o elija **Crear nuevo** para abrir el editor de formularios de vista rápida para crear uno nuevo.|
|**Relación jerárquica**|*Requerido.* Si una relación jerárquica ya está definida para la entidad, el valor se establecerá aquí. Si no hay ningún valor, seleccione **Marcar una relación como habilitada para las jerarquías** para abrir un cuadro de diálogo para elegir una de las relaciones que hacen referencia a sí mismas disponibles.|
|**Descripción**|Incluya una descripción del objetivo para esta jerarquía de modo que los usuarios futuros que personalicen el sistema puedan saber por qué se hizo.|
    

Los mismos valores jerárquicos de visualización se establecen una vez, pero, se aplican a clientes web y móviles. En tabletas, las representaciones visuales se muestran en un formato modificado conveniente para el factor de forma más pequeño. Los componentes personalizables necesarios para la visualización jerárquica son compatibles con las soluciones, por consiguiente, se pueden transportar entre organizaciones como cualquier otra personalización. Puede configurar los atributos que se muestran en la visualización personalizando un formulario rápido mediante el editor de formularios.
  
## <a name="visualization-walk-through"></a>Recorrido por la visualización

Miremos un ejemplo de crear la visualización para una entidad personalizada. Hemos creado una entidad personalizada llamada `new_Widget`, hemos creado una relación que hace referencia a sí misma (1:N) `new_new_widget_new_widget` y marcado como jerárquica, como se indica aquí.  
  
![Definición de relación de widget](media/widget-relationship-definition.png)  
  
A continuación, en la vista de cuadrícula **Configuración de la jerarquía** seleccionamos la relación jerárquica `new_new_widget_new_widget`. En el formulario, completamos los atributos requeridos. Si aún no ha marcado la relación (1:N) como jerárquica, el vínculo del formulario le devolverá al formulario de definición de la relación, donde puede marcar la relación como jerárquica.  

> [!IMPORTANT]
> Cada entidad sólo puede tener una relación jerárquica a la vez. Si lo cambia a otra relación que hace referencia a sí misma puede tener consecuencias. Más información: [Definir datos jerárquicos](../common-data-service/define-query-hierarchical-data.md#define-hierarchical-data)

> [!div class="mx-imgBorder"] 
> ![Configuración de jerarquía](media/hierarchy-settings.png)  
  
Para el **Formulario de vista rápida**, creamos un formulario rápido llamado **Formulario de ventana de jerarquía del widget**. En este formulario, agregamos cuatro campos para mostrar en cada ventana.  

> [!div class="mx-imgBorder"] 
> ![Crear formulario rápido para widget](media/create-quickform.png)  
  
Después de completar la configuración, creamos dos registros: *Widget estándar* y *Widget premium*. Después de marcar el Widget premium como elemento principal del Widget estándar mediante el campo de búsqueda, la vista de cuadrícula de `new_Widget` mostró los iconos de la jerarquía, como se indica a continuación:  

> [!div class="mx-imgBorder"] 
> ![Cuadrícula de la jerarquía del widget](media/widget-hierarchy-grid.png)  
  
> [!NOTE]
>  Los iconos de la jerarquía no aparecen en la vista de cuadrícula del registro hasta que los registros se relacionen usando la relación jerárquica.  
  
Si elige el icono de jerarquía, se mostrará la jerarquía `new_Widget`, con la vista de árbol a la izquierda y la vista de ventana a la derecha, mostrando dos registros. Cada ventana contiene cuatro campos que proporcionamos en el **Formulario de ventana de jerarquía del widget**.  

> [!div class="mx-imgBorder"] 
> ![Vistas de mosaicos y árbol del widget](media/widget-tree-tiles.png)  

Según sus necesidades, puede elegir entre una vista de árbol, que muestra la jerarquía completa, o una vista en mosaico, que representa una parte menor de la jerarquía. Ambas vistas se muestran lado a lado. Puede explorar una jerarquía expandiendo y contrayendo un árbol de jerarquía. 

### <a name="see-also"></a>Vea también 

[Definir y consultar datos relacionados jerárquicamente](../common-data-service/define-query-hierarchical-data.md)<br />
[Vídeo: Visualización de la jerarquía](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
