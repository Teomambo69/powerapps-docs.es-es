---
title: Filtrado de datos en cuadrículas | Microsoft Docs
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
ms.openlocfilehash: 3489266ab82600c1d902dcd6ec0383b4ef6b408a
ms.sourcegitcommit: db8005866acab318c2fa894db64df88aaf7e3785
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "77076071"
---
# <a name="use-grid-filters"></a>Uso de filtros de cuadrícula 

Las cuadrículas de la interfaz unificada se han mejorado para aumentar la cantidad de datos que se puede ver en la pantalla. Ahora puede elegir entre muchas opciones de filtrado diferentes para una columna; el tipo de datos de la columna determina las opciones de filtrado disponibles. Por ejemplo, la columna **Nombre completo** de la cuadrícula **Contactos** tiene opciones de filtrado diferentes a las de la columna **Tipo de actividad** de la cuadrícula **Actividades**.


   > [!div class="mx-imgBorder"]
   > ![Filtrado de cuadrícula](media/filter-options.png "Filtrado de cuadrícula")
   

## <a name="grid-and-filter-navigation"></a>Navegación por la cuadrícula y el filtro

Al filtrar los datos de una cuadrícula, la página de cuadrícula principal recuerda el filtro, el criterio de ordenación y el estado de la página cuando se sale y después se vuelve a la página. Esto funciona igual al filtrar datos en la búsqueda rápida, el filtrado de columnas, el número de página, etc. 

   > [!div class="mx-imgBorder"]
   > ![Al ir de nuevo a la página, se abre en el mismo estado](media/grid-remember-state-on-back-navigate.gif "Al ir de nuevo a la página, se abre en el mismo estado")

La barra de salto de la página usa el primer campo ordenado. Si no se ha realizado ningún cambio en el criterio de ordenación, la barra de salto usa el campo principal.

   > [!div class="mx-imgBorder"]
   > ![Selección de un filtro en la barra de salto](media/jumpbar-filter-on-sorted-column.gif "Selección de un filtro en la barra de salto")
  
Al seleccionar el icono de jerarquía, se va a la vista de jerarquía.

   > [!div class="mx-imgBorder"]
   > ![Icono de jerarquía](media/grid-row-hierarchy-icon.png "Icono de jerarquía")

También se pueden abrir campos principales y de búsqueda en una nueva pestaña o ventana.

   > [!div class="mx-imgBorder"]
   > ![Apertura en una nueva ventana](media/newtab.png "Apertura en una nueva ventana")
  

## <a name="preview-new-grid-filters-and-search-option"></a>Versión preliminar: Nuevos filtros de cuadrícula y opción de búsqueda

Esta sección es para características de acceso anticipado. Puede optar por la habilitación anticipada de estas características en el entorno. Esto le permite probar estas características y después adoptarlas en los entornos. Para obtener información sobre cómo habilitar estas características, vea [Participación en actualizaciones de acceso anticipado](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).


   > [!NOTE]
   > No cambie el formato de presentación predeterminado de hora, número, moneda o fecha, ya que esto causa un problema. Para obtener más información, vea [Problema conocido](https://docs.microsoft.com/powerapps/user/grid-filters#known-issue).

### <a name="lookup-field-column"></a>Columna de campo de búsqueda

Al filtrar en una columna de búsqueda, puede seleccionar en una lista de registros por los que filtrar en lugar de escribir los datos a mano. Por ejemplo, en una columna de búsqueda **Contacto principal**, puede seleccionar el nombre del contacto en la lista de registros por los que filtrar.

   > [!div class="mx-imgBorder"]
   > ![Filtrado de búsqueda](media/lookup-filter.png "Filtrado de búsqueda")

### <a name="date-filter"></a>Filtro de fecha

El sólido filtro **Fecha** incluye muchos valores distintos entre los que elegir, por ejemplo, **El** para buscar por una fecha exacta, o **Siguiente ejercicio** o **En el periodo fiscal** para buscar por año o trimestre.

   > [!div class="mx-imgBorder"]
   > ![Filtrado de fecha](media/date-filter.png "Filtrado de fecha")

### <a name="filter-the-list-of-activities"></a>Filtrado de la lista de actividades

Puede filtrar la lista de actividades para ver solo las que le interesan. Por ejemplo, puede limitar aún más las actividades que ve en una vista mediante el filtro Tipo de actividad. El filtro Tipo de actividad permite filtrar las actividades en función del tipo, como correo electrónico, tarea, llamada de teléfono, etc.


   > [!div class="mx-imgBorder"]
   > ![Filtro de actividades](media/activity_filter.png "Filtro de actividades")


### <a name="known-issue"></a>Problema conocido

Si cambia el formato de presentación predeterminado de número, moneda, hora o fecha y luego filtra los datos de una cuadrícula, el filtro no muestra el formato de presentación seleccionado. Los filtros se siguen mostrando en el formato predeterminado del sistema y, en algunos casos, es posible que el filtrado no funcione en absoluto. 

Para solucionar el problema, vuelva a establecer el formato de presentación de número, moneda, hora y fecha en el valor predeterminado. 

1. En la esquina superior derecha, seleccione el icono de engranaje ![Icono de engranaje](media/selection-rule-gear-button.png) y después **Configuración de personalización**.

2. En la pestaña **Formatos**, vuelva a cambiar el valor de número, moneda, hora y fecha al predeterminado.

    > [!div class="mx-imgBorder"] 
    > ![Configuración de formato](media/default-format.png "Configuración de formato")
    
Se está trabajando en este problema, así que vuelva a consultar la información sobre la disponibilidad de una corrección periódicamente.

  
### <a name="use-search-on-a-grid"></a>Uso de la búsqueda en una cuadrícula

Cuando se usa la opción **Buscar en esta vista** en una página de cuadrícula, el sistema busca los datos en la vista en la que se encuentra. En el ejemplo siguiente se realiza una búsqueda en la cuadrícula **Contactos**.

1. Vaya a la cuadrícula **Contactos** y seleccione **Mis contactos activos** en la lista de vistas.

    > [!div class="mx-imgBorder"]
    > ![Vista Mis contactos activos](media/myactive-contacts-view.png "Vista Mis contactos activos")

2. Seleccione **Buscar en esta vista** para buscar datos en la vista en la que se encuentra.

    > [!div class="mx-imgBorder"]
    > ![Búsqueda en vista](media/search-view.png "Buscar en esta vista")

El sistema busca datos en la vista **Mis contactos activos** y muestra los resultados de la búsqueda mediante el mismo conjunto de columnas que se usan en la vista actual.

   > [!div class="mx-imgBorder"]
   > ![Búsqueda en vista](media/search-view2.png "Resultados de búsqueda del comando Buscar en esta vista")


#### <a name="use-the-quick-find-search-experience"></a>Uso de la experiencia de búsqueda rápida

Para volver a la experiencia de búsqueda rápida anterior, que usa la definición de vista de búsqueda rápida de una entidad para realizar búsquedas, necesita permisos de administrador.

1. En la esquina superior derecha, seleccione el icono de engranaje ![Icono de engranaje](media/selection-rule-gear-button.png) y después **Configuración avanzada**.

2. Vaya a **Configuración** > **Administración** > **Configuración del sistema**.

3. En la pestaña **General**, en **Configurar Búsqueda rápida**, seleccione **Sí** para **usar la vista de búsqueda rápida de una entidad para buscar en cuadrículas y subcuadrículas**.



