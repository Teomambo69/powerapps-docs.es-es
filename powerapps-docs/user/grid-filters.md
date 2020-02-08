---
title: Filtrar datos en cuadrículas | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 02/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2cfe55db19b5d8a7aeed86169a188455686cf81b
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051987"
---
# <a name="use-grid-filters"></a>Usar filtros de cuadrícula 

Las cuadrículas de la interfaz unificada se han mejorado para aumentar la cantidad de datos que se pueden ver en la pantalla. Ahora puede elegir entre muchas opciones de filtrado diferentes para una columna; el tipo de datos de la columna determina qué opciones de filtro están disponibles. Por ejemplo, la columna **nombre completo** de la cuadrícula **contactos** tiene distintas opciones de filtro que la columna **tipo de actividad** de la cuadrícula **actividades** .


   > [!div class="mx-imgBorder"]
   > ![Filtrado de cuadrículas](media/filter-options.png "Filtrado de cuadrículas")
   

## <a name="grid-and-filter-navigation"></a>Navegación por la cuadrícula y el filtro

Al filtrar los datos en una cuadrícula, la página de cuadrícula principal recuerda el filtro, el criterio de ordenación y el estado de la página cuando se desplaza fuera y después vuelve a la página. Esto funciona igual cuando se filtran los datos en la búsqueda rápida, el filtrado de columnas, el número de página, etc. 

   > [!div class="mx-imgBorder"]
   > ![Al navegar de nuevo a la página se abre en el mismo estado](media/grid-remember-state-on-back-navigate.gif "Al navegar de nuevo a la página se abre en el mismo estado")

La barra de saltos de página usa el primer campo ordenado. Si no se ha realizado ningún cambio en el criterio de ordenación, la barra de saltos utiliza el campo principal.

   > [!div class="mx-imgBorder"]
   > ![Seleccionar un filtro en la barra de saltos](media/jumpbar-filter-on-sorted-column.gif "Seleccionar un filtro en la barra de saltos")
  
Al seleccionar el icono de jerarquía, navega a la vista de jerarquía.

   > [!div class="mx-imgBorder"]
   > ![Icono de jerarquía](media/grid-row-hierarchy-icon.png "Icono Jerarquía")

También puede abrir campos principales y de búsqueda en una nueva pestaña o ventana.

   > [!div class="mx-imgBorder"]
   > ![Abrir en una nueva ventana](media/newtab.png "[Abrir en una nueva ventana")
   
   
### <a name="known-issue"></a>Problema conocido

Si cambia el formato de presentación predeterminado de número, moneda, hora o fecha y, a continuación, filtra los datos en una cuadrícula, el filtro no mostrará el formato de visualización seleccionado. Los filtros se seguirán mostrando en el formato predeterminado del sistema y, en algunos casos, es posible que el filtrado no funcione. 

Para solucionar el problema, establezca el formato de presentación de número, moneda, hora y fecha de nuevo en la configuración predeterminada. 

1. En la esquina superior derecha, seleccione el icono de engranaje ![icono de engranaje](media/selection-rule-gear-button.png)y, después, seleccione **configuración de personalización**.

2. En la pestaña **formatos** , cambie el valor de número, moneda, hora y fecha de nuevo a la configuración predeterminada.

    > [!div class="mx-imgBorder"] 
    > ![Configuración de formato](media/default-format.png "configuración de formato")
    
    
  Estamos trabajando en el problema. Vuelva a comprobar la disponibilidad. 



## <a name="preview-new-grid-filters-and-search-option"></a>Vista previa: nuevos filtros de cuadrícula y opción de búsqueda

Esta sección es para las características de acceso temprano. Puede participar pronto para habilitar estas características en su entorno. Esto le permitirá probar estas características y después adoptarlas en sus entornos. Para obtener información sobre cómo habilitar estas características, consulte [participación en las actualizaciones de la versión 1 de 2020](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).


   > [!NOTE]
   > No cambie el formato de presentación predeterminado de hora, número, moneda, hora o fecha, ya que esto provoca un problema. Para obtener más información, consulte [problema conocido](https://docs.microsoft.com/powerapps/user/grid-filters#known-issue).

### <a name="lookup-field-column"></a>Columna de campo de búsqueda

Al filtrar por una columna de búsqueda, puede seleccionar en una lista de registros para filtrar por, en lugar de escribirlos manualmente en los datos. Por ejemplo, en una columna principal de búsqueda de **contactos** , puede seleccionar el nombre de contacto en la lista de registros por los que desea filtrar.

   > [!div class="mx-imgBorder"]
   > ![Filtrado de búsqueda](media/lookup-filter.png "Filtrado de búsqueda")

### <a name="date-filter"></a>Filtro de fechas

El filtro de **fecha** sólido incluye muchos valores distintos entre los que elegir, por ejemplo, **en** para buscar por una fecha exacta o el **siguiente año fiscal X** o **en el período fiscal** para buscar por año o trimestre.

   > [!div class="mx-imgBorder"]
   > ![Filtrado de fechas](media/date-filter.png "Filtrado de fechas")

### <a name="filter-the-list-of-activities"></a>Filtrar la lista de actividades

Puede filtrar la lista de actividades para ver solo las que le interesan. Por ejemplo, puede limitar aún más las actividades que ve en una vista mediante el filtro tipo de actividad. El filtro tipo de actividad permite filtrar las actividades en función del tipo, como correo electrónico, tarea, llamada de teléfono, etc.


   > [!div class="mx-imgBorder"]
   > ![Filtro de actividades](media/activity_filter.png "Filtro de actividades")


#### <a name="known-issue"></a>Problema conocido

Si cambia el formato de presentación predeterminado de número, moneda, hora o fecha y, a continuación, filtra los datos en una cuadrícula, el filtro no mostrará el formato de visualización seleccionado. Los filtros se seguirán mostrando en el formato predeterminado del sistema y, en algunos casos, es posible que el filtrado no funcione. 

Para solucionar el problema, establezca el formato de presentación de número, moneda, hora y fecha de nuevo en la configuración predeterminada. 

1. En la esquina superior derecha, seleccione el icono de engranaje ![icono de engranaje](media/selection-rule-gear-button.png)y, después, seleccione **configuración de personalización**.

2. En la pestaña **formatos** , cambie el valor de número, moneda, hora y fecha de nuevo a la configuración predeterminada.

    > [!div class="mx-imgBorder"] 
    > ![Configuración de formato](media/default-format.png "configuración de formato")
    
    
Estamos trabajando en el problema. Vuelva a comprobar la disponibilidad. 
  
### <a name="use-search-on-a-grid"></a>Usar la búsqueda en una cuadrícula

Cuando se usa la opción **Buscar esta vista** en una página de cuadrícula, el sistema busca los datos en la vista en la que se encuentra actualmente. En el ejemplo siguiente, realizará una búsqueda en la cuadrícula **contactos** .

1. Vaya a la cuadrícula **contactos** y, a continuación, seleccione **mis contactos activos** en la lista de vistas.

    > [!div class="mx-imgBorder"]
    > ![Mi vista de contacto activa](media/myactive-contacts-view.png "Mi vista de contactos activa")

2. Seleccione **Buscar en esta vista** para buscar datos en la vista en la que se encuentra.

    > [!div class="mx-imgBorder"]
    > ![Vista de búsqueda](media/search-view.png "Buscar en esta vista")

El sistema busca los datos en la vista **mis contactos activos** y muestra los resultados de la búsqueda mediante el mismo conjunto de columnas que se usan en la vista actual.

   > [!div class="mx-imgBorder"]
   > ![Vista de búsqueda](media/search-view2.png "Resultados de la búsqueda del comando Buscar esta vista")


#### <a name="use-the-quick-find-search-experience"></a>Usar la experiencia de búsqueda rápida

Para volver a la experiencia de búsqueda de búsqueda rápida anterior que usa la definición de vista de búsqueda rápida de una entidad para realizar búsquedas, necesitará permisos de administrador.

1. En la esquina superior derecha, seleccione el icono de engranaje ![icono de engranaje](media/selection-rule-gear-button.png)y, a continuación, seleccione **Configuración avanzada**.

2. Vaya a **configuración** > **Administración** > **configuración del sistema**.

3. En la pestaña **General** , en **configurar búsqueda rápida**, seleccione **sí** para **usar la vista de búsqueda rápida de una entidad para buscar en cuadrículas y subcuadrículas**.



