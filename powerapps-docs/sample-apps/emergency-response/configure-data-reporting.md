---
title: Configuración de datos maestros y visualización de paneles en la aplicación de repuesta ante emergencias hospitalarias | Microsoft Docs
description: Proporciona instrucciones detalladas para que los administradores de TI de hospitales implementen y configuren la aplicación de ejemplo para su organización.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/15/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 5a622a7d945fa78536c3addb75cfa64d327c7c90
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81448282"
---
# <a name="configure-master-data-and-view-dashboards"></a>Configuración de datos maestros y visualización de paneles

En este artículo se proporciona información sobre cómo puede usar la aplicación de administración (aplicación controlada por modelos) para agregar y administrar los datos maestros de la solución y usar el panel de Power BI para ver las métricas y la información clave.

Estas tareas las realizan normalmente los administradores empresariales de la organización.

## <a name="configure-and-manage-master-data-for-your-organization"></a>Configuración y administración de los datos maestros de la organización

Use la aplicación de administración para crear y administrar los datos maestros de su organización. Estos datos son necesarios para que funcione la aplicación Respuesta ante emergencias hospitalarias.

> [!IMPORTANT]
> - Asegúrese de que el administrador de TI ha implementado la solución en su organización y que ha concedido los permisos adecuados para que los administradores empresariales usen la aplicación de administración. Más información: [Implementación de la aplicación de respuesta ante emergencias hospitalarias](deploy-configure.md#deploy-the-hospital-emergency-response-app)
> 
> - También puede importar los datos desde los archivos de datos disponibles en el paquete de implementación. Más información: [Paso 4: Cargar la configuración y los datos maestros de la organización](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

Debe agregar datos maestros en estas entidades en la secuencia siguiente:

1. [Systems](#systems-data) (Sistemas)

1. [Regiones](#regions-data)

1. [Facilities](#facilities-data) (Instalaciones)

1. [Ubicaciones](#locations-data)

1. [Departments](#departments-data) (Departamentos)

Los datos maestros se administran desde el área **Locations** (Ubicaciones) en el panel de navegación izquierdo de la aplicación de administración:

> [!div class="mx-imgBorder"]
> ![locations-area](media/locations-area.png)

Las entidades del área **Hierarchy** (Jerarquía) se muestran en el orden en que se deben rellenar los datos.

> [!NOTE]
> Los datos del triaje se importan durante la implementación de la solución. Más información: [Paso 4: Cargar la configuración y los datos maestros de la organización](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

### <a name="systems-data"></a>Datos de sistemas

La entidad **Systems** (Sistemas) le permite crear y administrar entradas para sistemas hospitalarios. Puede administrar varios sistemas hospitalarios dentro de la misma organización.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación controlada por modelos) con la dirección URL proporcionada por el administrador de TI.

1. Seleccione **Systems** (Sistemas) en el panel izquierdo y luego **Nuevo**:  
    > [!div class="mx-imgBorder"]
    > ![select-systems-new](media/select-systems-new.png)

1. En la página **New System** (Nuevo sistema), especifique los valores adecuados:  
   > [!div class="mx-imgBorder"]
   > ![enter-details-new-system](media/enter-details-new-system.png)

   | **Campo**            | **Descripción**                                    |
   |----------------------|----------------------------------------------------|
   | Nombre del sistema          | Escriba un nombre para el hospital.                     |
   | Descripción          | Escriba una descripción opcional.                      |
   | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de este sistema hospitalario. |
   | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de este sistema hospitalario.   |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Systems** (Sistemas).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="regions-data"></a>Datos de regiones

La entidad **Regions** (Regiones) permite administrar las regiones geográficas de los sistemas hospitalarios.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación controlada por modelos) con la dirección URL proporcionada por el administrador de TI.

1. Seleccione **Regions** (Regiones) en el panel izquierdo y luego **Nuevo**:

1. En la página **New Region** (Nueva región), especifique los valores adecuados:  

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-region](media/enter-details-new-region.png)

    | **Campo**            | **Descripción**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | Sistema               | Seleccione un sistema hospitalario. Esta lista se rellena en función de los datos de **Systems** (Sistemas) que ha creado anteriormente. |
    | Nombre de región          | Escriba el nombre de la región. Por ejemplo, Seattle.                                                              |
    | Descripción          | Escriba una descripción opcional.                                                                            |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de esta región.                                                       |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de esta región.                                                         |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Regions** (Regiones).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="facilities-data"></a>Datos de instalaciones

La entidad **Facilities** (Instalaciones) permite administrar las ubicaciones de los centros hospitalarios dentro de cada región. Por ejemplo, las instalaciones de **Redmond** y **Bellevue** en la región de **Seattle**.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación controlada por modelos) con la dirección URL proporcionada por el administrador de TI.

1. Seleccione **Facilities** (Instalaciones) en el panel izquierdo y luego **Nuevo**:

1. En la página **New Facility** (Nueva instalación), especifique los valores adecuados: 

    > [!div class="mx-imgBorder"] 
    > ![enter-details-new-facility](media/enter-details-new-facility.png)

    | **Campo**            | **Descripción**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Región               | Seleccione una región a la que esté asociada esta instalación. Esta lista se rellena en función de los datos de **Regions** (Regiones) que ha creado anteriormente. |
    | Facility Name (Nombre de la instalación)        | Escriba el nombre de la instalación. Por ejemplo, Bellevue.                                                  |
    | Total Vents (Respiradores totales)          | Escriba el número total de respiradores disponibles en la instalación.                                  |
    | Descripción          | Escriba una descripción opcional.                                                                   |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de esta instalación.                                                     |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de esta instalación.                                                       |
    |Total Beds (Camas totales)      | Calculado automáticamente.|
    |Total Occupied (Totales ocupadas)      | Calculado automáticamente.|
    |Facility Address (Dirección de la instalación)      | Escriba la calle, la ciudad, el país, el estado, el código postal, la latitud y la longitud de la instalación.|

    Si es necesario, escriba la dirección de la instalación.

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Facilities** (Instalaciones).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="locations-data"></a>Datos de ubicaciones

La entidad **Locations** (Ubicaciones) permite administrar ubicaciones específicas dentro de cada instalación hospitalaria.

> [!NOTE]
> Antes de crear un registro de **Locations** (Ubicaciones), asegúrese de que ha importado los datos del triaje mediante el archivo**00 - Acuities Import.xlsx** (Importación de triaje) como se explicó anteriormente en [Paso 4: Cargar la configuración y los datos maestros de la organización](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization). Esto se debe a que la información del triaje es necesaria para crear un registro relativo a la **ubicación**.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación controlada por modelos) con la dirección URL proporcionada por el administrador de TI.

1. Seleccione **Locations** (Ubicaciones) en el panel izquierdo y luego **Nuevo**.

1. En la página **New Location** (Nueva ubicación), especifique los valores adecuados:  
 
    > [!div class="mx-imgBorder"]
    > ![enter-details-new-location](media/enter-details-new-location.png)

    | **Campo**            | **Descripción**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Nombre de la ubicación        | Escriba el nombre de la ubicación.                                                                       |
    | Facility             | Seleccione una instalación. Esta lista se rellena en función de los datos de **Facilities** (Instalaciones) que ha creado anteriormente. |
    | Floor                | Escriba la información de la planta de la instalación.                                                         |
    | Unidad                 | Escriba la información de la unidad de la instalación.                                                           |
    | Occupancy Percentage (Porcentaje de ocupación) | Se calcula automáticamente según los valores de último censo y total de camas.                                         |
    | Acuity (Agudeza)      | Seleccione el registro de triaje asociado a esta ubicación.                                                                                                     |
    | COVID Location (Ubicación de COVID)      | Seleccione si esta ubicación se usa para tratar a pacientes con COVID (**Yes** [Sí] o **No**).                                                                                                      |
    | Total Beds (Camas totales)           | Escriba el número total de camas de la instalación.                                                       |
    | Surge Beds (Camas de ampliación)           | Escriba el número de camas de ampliación en la instalación. Las camas de ampliación son aquellas que se pueden dotar sobrepasando la capacidad de camas admitida en caso de que sea necesario ingresar a los pacientes.                                                      |
    | Blocked beds (Camas bloqueadas)         | Escriba el número de camas bloqueadas de la instalación.                                                     |
    | Last Census (Último censo)          | Se rellena basándose en el último registro del censo que se está creando.                                             |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de esta ubicación.                                                   |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de esta ubicación.                                                     |
    | Location Order (Orden de la ubicación)       | Escriba un número que ordene la ubicación en las listas desplegables de ubicación.                               |
    | Alternate Site Flag (Marca de sitio alternativo)  | Para uso interno.                                                                                     |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Locations** (Ubicaciones).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

Puede ver los datos asociados de una ubicación, como el **censo**, el **seguimiento de COVID** o las **necesidades de equipamiento** abriendo un registro de una ubicación existente y seleccionando las respectivas pestañas. El personal de primera línea especifica los datos asociados mediante [aplicaciones móviles](use.md).

> [!div class="mx-imgBorder"]
> ![location-related-records](media/location-related-records.png)


### <a name="departments-data"></a>Datos de departamentos

La entidad **Departments** (Departamentos) le permite administrar la información de los departamentos de un hospital.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación controlada por modelos) con la dirección URL proporcionada por el administrador de TI.

1. Seleccione **Departments** (Departamentos) en el panel izquierdo y luego **Nuevo**.

1. En la página **New Departments** (Nuevo departamento), especifique los valores adecuados:

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-department](media/enter-details-new-department.png)

    | **Campo**            | **Descripción**                                    |
    |----------------------|----------------------------------------------------|
    | Nombre de departamento      | Escriba el nombre de un departamento.                            |
    | Descripción          | Escriba una descripción opcional.                      |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de este departamento. |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de este departamento.   |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Departments** (Departamentos).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

## <a name="manage-tracking-level-for-mobile-apps"></a>Administración del nivel de seguimiento de aplicaciones móviles

Los trabajadores de primera línea pueden realizar un seguimiento de la información por *ubicación* o *instalación* con las aplicaciones móviles (aplicaciones de lienzo). Este es el nivel de seguimiento predeterminado para cada aplicación móvil: 

|Aplicación  |Nivel de seguimiento predeterminado  |
|--|--|
|COVID tracking (Seguimiento de COVID)|Ubicación|
|Personal|Ubicación|
|Equipment (Equipo)|Ubicación|
|Bed capacity (Capacidad de camas)|Facility|
|Supplies (Suministros)|Facility|
|Staffing needs (Necesidades del personal)|Facility|
|Discharge tracking (Seguimiento de altas)|Facility|

Como administrador, puede cambiar el nivel de seguimiento predeterminado de las aplicaciones móviles.

1. Inicie sesión en la aplicación de administración (aplicación controlada por modelos) con la dirección URL proporcionada por el administrador de TI.

1. En el panel de navegación izquierdo, seleccione **Administración** y luego **Aplicaciones**. 

    > [!div class="mx-imgBorder"]
    > ![config-admin-app-records](media/admin-apps.png)

1. Seleccione una de las aplicaciones de lienzo para abrir el registro.

1. En el registro de la aplicación, seleccione un valor adecuado en el campo de **nivel de seguimiento**.

    > [!div class="mx-imgBorder"]
    > ![app-tracking-level](media/app-tracking-level.png)

    - Si se selecciona **Location** (Ubicación) para una aplicación, los registros creados mediante la aplicación móvil contendrán información sobre la ubicación y la instalación, junto con otros datos. Además, en la aplicación móvil habrá disponible una lista desplegable **Location** (Ubicación) para que los usuarios puedan seleccionar una ubicación para hacer un seguimiento de los datos.

    - Si se selecciona **Facility** (Instalación) para una aplicación, los registros creados mediante la aplicación móvil contendrán solo información sobre la instalación, junto con otros datos.

    - Si no selecciona ningún valor para el campo de **nivel de seguimiento**, se aplica el nivel de seguimiento *predeterminado* a las aplicaciones móviles, como se explicó anteriormente.

1. Seleccione **Guardar** en la esquina inferior derecha para guardar los cambios.

## <a name="view-common-data-service-dashboards"></a>Visualización de paneles de Common Data Service

Los siguientes paneles están disponibles de forma predeterminada en la aplicación del administrador de Respuesta ante emergencias hospitalarias (controlada por modelos):

- **Bed Management** (Administración de camas)

   Muestra la disponibilidad de las camas, el porcentaje de ocupación y el número total de camas en diferentes instalaciones.

- **Equipment and Supply** (Equipos y suministro)

  Muestra el equipo crítico en uso y los suministros disponibles en diferentes instalaciones.

- **Staff Management** (Administración de personal)

  Muestra el número de miembros de trabajadores solicitados, asignados y disponibles en diferentes instalaciones.

- **COVID Patients** (Pacientes COVID)

  Muestra el número de pacientes en investigación y confirmados positivos en COVID-19 en diferentes instalaciones.

- **Discharges** (Altas)

  Muestra el número de pacientes previstos para alta y las altas reales.

También puede crear sus propios paneles además de los paneles disponibles de forma predeterminada.

### <a name="manage-dashboards"></a>Administración de paneles

Para administrar paneles:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y vaya a la aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Paneles** desde el selector de áreas:

    > [!div class="mx-imgBorder"]
    > ![select-dashboards](media/select-dashboards.png)

3. Seleccione un nombre de panel en el panel de navegación izquierdo para ver los gráficos:

    > [!div class="mx-imgBorder"]
    > ![view-charts](media/view-charts.png)

    > [!NOTE]
    > Puede filtrar los datos en la parte inferior de la pantalla y los gráficos de la parte superior se actualizan automáticamente con los valores filtrados.

4. Seleccione la opción de **expandir** para ver un gráfico en modo de pantalla completa:

    > [!div class="mx-imgBorder"]
    > ![select-expand](media/select-expand.png)

### <a name="additional-analysis"></a>Análisis adicional

- **Explorar en profundidad**: Puede seleccionar el área del gráfico para profundizar con atributos (campos) adicionales de una entidad:

    > [!div class="mx-imgBorder"]
    > ![select-chart-area-drill-down](media/select-chart-area-drill-down.png)

- **Actualizar**: Puede actualizar los paneles para reflejar los datos actualizados. Puede actualizar todos los gráficos en un panel específico con **Actualizar todo** o un gráfico seleccionado con **Actualizar**:

    > [!div class="mx-imgBorder"]
    > ![refresh-dashboards](media/refresh-dashboards.png)

- **Ver registros** Seleccione **Más comandos** ( **...** ) y, a continuación, **Ver registros** para ver todos los registros asociados a un gráfico determinado:

    > [!div class="mx-imgBorder"]
    > ![select-more-commands](media/select-more-commands.png)

    > [!NOTE] 
    > Al seleccionar **Ver registros**, verá la vista de la división de entidades entre el gráfico y los registros. Cualquier cambio en los filtros de los registros del lado derecho se refleja con actualizaciones automáticas del gráfico en el lado izquierdo de la pantalla.

Para obtener más información sobre la edición de un panel existente y la actualización de las propiedades de los gráficos, lea [Editar un panel existente](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Creación de paneles

También puede crear sus propios paneles y personalizarlos para adaptarse a sus necesidades. Para crear un panel, seleccione **Nuevo** y luego **Panel de Dynamics 365**.

> [!div class="mx-imgBorder"]
> ![select-new-dynamics-dashboard](media/select-new-dynamics-dashboard.png)

Para obtener más información sobre la creación de un nuevo panel, lea [Crear un panel](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="view-power-bi-dashboard"></a>Visualización del panel de Power BI

Vea los paneles de Power BI para recabar información y tomar decisiones.

### <a name="prerequisites"></a>Requisitos previos

- Licencias de capacidad premium de Power BI o Power BI Pro asignadas a los usuarios que tienen acceso al informe. 

- El administrador de TI debe haber publicado el informe de Power BI y haberle dado permiso para acceder a él. Más información: [Publicación del panel de Power BI](deploy-configure.md#publish-the-power-bi-dashboard) 

### <a name="view-the-dashboard"></a>Visualización del panel

Inicie sesión en [Power BI](https://apps.powerbi.com) para obtener acceso al panel de Power BI y verlo.

> [!div class="mx-imgBorder"]
> ![Visualización del panel de Power BI](media/view-powerbi-dashboard.png)

Puede usar los filtros del lado derecho para filtrar los datos de las ubicaciones de la COVID, así como instalaciones, regiones y sistemas hospitalarios.

#### <a name="system-at-a-glance-page"></a>Página System at a glance (Resumen del sistema) 

La página **Systems at a glance** (Resumen del sistema) es la página predeterminada o la de nivel superior que ofrece una vista general.  

En la página se muestra una vista resumida de lo siguiente: 

- **COVID Patient Information** (Información de pacientes de COVID): muestra el número total de pacientes con COVID, el número de pacientes que han dado positivo en la COVID-19 y el número de pacientes en investigación.

- **Bed Management** (Administración de camas): muestra la disponibilidad de camas, el porcentaje de ocupación, el número de camas de ampliación y el número total de camas. También puede usar la cuadrícula siguiente para ver los números por unidades de cuidados intensivos.

- **Staffing Information** (Información de la plantilla): muestra el número de pacientes en la UCI, el personal de enfermería asignado y la relación entre personal de enfermería y pacientes.  

- **Patient Discharge Information** (Información de altas de pacientes): muestra el número de pacientes de larga estancia totales, el número de pacientes previstos para alta y las altas reales.

- **Equipment Information** (Información sobre el equipamiento): muestra el número total de respiradores, el número de respiradores en uso y los respiradores disponibles. 

- **Supplies Information** (Información sobre suministros): muestra el número de suministros disponibles por días.

> [!NOTE]
> - Al seleccionar el título en cualquiera de las áreas resumidas, irá a la página de detalles correspondiente del área. 
> - También puede realizar otras acciones en los informes, como filtrar y ordenar datos, exportar el informe a PDF y PowerPoint, agregar un resaltado, etc. Para más información sobre las características de los informes de Power BI, consulte [Informes en Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports).
> - Las columnas más recientes o actualizadas por última vez en algunos de estos informes muestran la fecha y la hora en que se actualizaron los datos por última vez. También es fácil identificar lo recientes que son los datos observando el color de los valores de fecha y hora de estas columnas:
>    - Negro: los datos se han actualizado hace menos de 20 horas.
>    - Gris: los datos se han actualizado hace 20-24 horas.
>    - Rojo: los datos se han actualizado hace más de 24 horas. 
 
#### <a name="system-view-page"></a>Página System View (Vista del sistema)

La página **System View** (Vista del sistema) muestra gráficos con la siguiente información del sistema de un hospital:
- Respiradores en uso y respiradores disponibles
- Disponibilidad de camas, camas de cuidados intensivos y porcentaje de ocupación
- Personal total solicitado, número de pacientes (censo) y relación entre personal de enfermería y pacientes
- Suministros disponibles durante un período de tiempo

> [!div class="mx-imgBorder"]
> ![System View (Vista del sistema)](media/report-system-view.png)

#### <a name="location-details-page"></a>Página Location Details (Detalles de la ubicación) 

En la página **System at a glance** (Resumen del sistema), seleccione **i** en la esquina superior derecha. En la página **Location Details** (Detalles de la ubicación) se muestran los datos por ubicación, como el número total de camas, las camas disponibles, las camas de ampliación, los pacientes con COVID, etc. 

> [!div class="mx-imgBorder"]
> ![Location Details (Detalles de la ubicación)](media/report-location-details.png) 

#### <a name="covid-patients-page"></a>Página COVID Patients (Pacientes con COVID) 

En la página se proporciona información detallada sobre los pacientes con COVID, por ejemplo, los pacientes en cada ubicación, la tendencia de los pacientes en el tiempo con las subidas y bajadas del número de pacientes en investigación y el número de pacientes positivos, y se ofrece una idea general de dónde se encuentran los pacientes en el hospital.

> [!div class="mx-imgBorder"]
> ![COVID Patient Details (Detalles de los pacientes con COVID)](media/report-covid-details.png)

#### <a name="bed-management-page"></a>Página Bed Management (Administración de camas) 

En esta página se ofrece información detallada por ubicación, como las camas disponibles totales, las camas disponibles para cuidados intensivos y el porcentaje de ocupación.

> [!div class="mx-imgBorder"]
> ![Bed Management](media/report-bed-details.png) (Administración de camas)

#### <a name="staffing-details-page"></a>Página Staffing details (Detalles del personal)  

En esta página se proporciona información detallada sobre el personal por ubicación, el número de miembros del personal de enfermería asignados, el número total de pacientes y el número de pacientes con COVID. También se muestra la relación miembro del personal de enfermería-paciente y la relación personal de enfermería en UCI-paciente en un período de tiempo.

> [!div class="mx-imgBorder"]
> ![Staff Details (Detalles del personal)](media/report-staff-details.png)

#### <a name="equipment-page"></a>Página Equipment (Equipamiento) 

En la página se proporcionan detalles sobre el equipamiento por ubicación, el número total de respiradores en uso, solapados por el número de pacientes con COVID, y otros elementos, como correas, cargadores y capuchas en uso.

> [!div class="mx-imgBorder"]
> ![Equipment Details (Detalles del equipo)](media/report-equipment-details.png)

#### <a name="discharges-page"></a>Página Discharges (Altas) 

En esta página se proporcionan detalles sobre los pacientes de estancia prolongada, los obstáculos a las altas durante un período y la varianza en cuanto a las altas reales y previstas.

> [!div class="mx-imgBorder"]
> ![Equipment Details (Detalles del equipo)](media/report-discharge-details.png)

#### <a name="supplies-page"></a>Página Supplies (Suministros) 

En la página se proporcionan detalles sobre los suministros por ubicación. También se ofrece un gráfico sobre los días disponibles por suministro e instalación, y el suministro disponible durante un período de tiempo.

> [!div class="mx-imgBorder"]
> ![Equipment Details (Detalles del equipo)](media/report-supplies.png)

## <a name="view-and-manage-app-feedback"></a>Visualización y administración de los comentarios de la aplicación

Todos los comentarios que proporciona el personal de primera línea que utiliza las aplicaciones de lienzo en sus dispositivos móviles se almacenan en la entidad **App Feedback** (Comentarios de la aplicación), y los administradores pueden verlos y administrarlos mediante el área de **administración** del panel de navegación izquierdo de la aplicación de administración.

Para ver y administrar los comentarios de la aplicación:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y vaya a la aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Administración** desde el selector de áreas:

3. Seleccione **App Feedback** (Comentarios de la aplicación) para ver una lista de los comentarios de la aplicación enviados por los usuarios. Puede hacer clic en un registro para ver los detalles y marcarlos como revisados o no.  

    > [!div class="mx-imgBorder"]
    > ![select-app-feedback](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para notificar un problema con la aplicación de ejemplo Respuesta ante emergencias hospitalarias, visite <https://aka.ms/emergency-response-issues>.

- Para ofrecer comentarios sobre la aplicación de ejemplo Respuesta ante emergencias hospitalarias, visite <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Siguiente paso

[Uso de la aplicación móvil de respuesta ante emergencias hospitalarias](use.md)
