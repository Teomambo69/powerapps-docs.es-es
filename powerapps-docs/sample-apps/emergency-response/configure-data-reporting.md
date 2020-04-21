---
title: Configurar datos maestros y ver paneles en la aplicación Hospital Emergency Response | Microsoft Docs
description: Proporciona proporciona instrucciones detalladas para que los administradores de TI del hospital implementen y configuren la aplicación de muestra para su organización.
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
ms.locfileid: "3265425"
---
# <a name="configure-master-data-and-view-dashboards"></a>Configurar datos maestros y ver paneles

Este artículo proporciona información sobre cómo puede usar la aplicación de administración (aplicación basada en modelos) para agregar y administrar datos maestros para su solución y usar el panel de control de Power BI para ver información clave y métricas.

Estas tareas generalmente las realizan los administradores de negocios de su organización.

## <a name="configure-and-manage-master-data-for-your-organization"></a>Configurar y administrar datos maestros para su organización

Use la aplicación de administración para crear y administrar datos maestros para su organización. Estos datos son necesarios para que la aplicación Hospital Emergency Response funcione.

> [!IMPORTANT]
> - Asegúrese de que su administrador de TI haya implementado la solución en su organización y haya otorgado los permisos adecuados para que los administradores de empresas utilicen la aplicación de administración. Más información: [Implementar la aplicación Hospital Emergency Response](deploy-configure.md#deploy-the-hospital-emergency-response-app)
> 
> - También puede importar sus datos de los archivos de datos disponibles en el paquete de implementación. Más información: [Paso 4: Cargar la configuración y los datos maestros para su organización](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

Debe agregar datos maestros en estas entidades en la siguiente secuencia:

1. [Sistemas](#systems-data)

1. [Regiones](#regions-data)

1. [Instalaciones](#facilities-data)

1. [Ubicaciones](#locations-data)

1. [Departamentos](#departments-data)

Los datos maestros se gestionan desde el área **Ubicaciones** en la navegación izquierda en la aplicación de administración:

> [!div class="mx-imgBorder"]
> ![área ubicaciones](media/locations-area.png)

Las entidades bajo el área **Jerarquía** se enumeran en el orden en que debe completar los datos.

> [!NOTE]
> Los datos de gravedades se importan durante la implementación de la solución. Más información: [Paso 4: Cargar la configuración y los datos maestros para su organización](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

### <a name="systems-data"></a>Datos del sistema

La entidad **Sistemas** le permite crear y administrar entradas para Hospital Systems. Esto le permite administrar múltiples sistemas hospitalarios dentro de la misma organización.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación basada en modelos) utilizando la URL proporcionada por su administrador de TI.

1. Seleccione **Sistemas** en el panel izquierdo y seleccione **Nuevo**:  
    > [!div class="mx-imgBorder"]
    > ![seleccionar-sistemas-nuevo](media/select-systems-new.png)

1. En la página **Sistema nuevo**, especifique los valores apropiados:  
   > [!div class="mx-imgBorder"]
   > ![introducir-detalles-sistema-nuevo](media/enter-details-new-system.png)

   | **Campo**            | **Descripción**                                    |
   |----------------------|----------------------------------------------------|
   | Nombre del sistema          | Escriba un nombre para su Hospital.                     |
   | Descripción          | Escriba una descripción opcional.                      |
   | Fecha de datos efectiva | Escriba la fecha y hora de inicio de este sistema hospitalario. |
   | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de este sistema hospitalario.   |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Sistemas**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="regions-data"></a>Datos de regiones

La entidad **Regiones** le permite administrar las regiones geográficas de sus sistemas hospitalarios.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación basada en modelos) utilizando la URL proporcionada por su administrador de TI.

1. Seleccione **Regiones** en el panel izquierdo y seleccione **Nuevo**.

1. En la página **Región nueva**, especifique los valores apropiados:  

    > [!div class="mx-imgBorder"]
    > ![introducir-detalles-región-nueva](media/enter-details-new-region.png)

    | **Campo**            | **Descripción**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | Sistema               | Seleccionar un sistema hospitalario. Esta lista se llena en función de los datos de **Sistemas** que ha creado anteriormente. |
    | Nombre de región          | Escriba el nombre de la región. Por ejemplo, Seattle.                                                              |
    | Descripción          | Escriba una descripción opcional.                                                                            |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de esta región.                                                       |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de esta región.                                                         |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Regiones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="facilities-data"></a>Datos de instalaciones

La entidad **Instalaciones** le permite administrar las ubicaciones de los hospitales dentro de cada región. Por ejemplo, las instalaciones **Redmond** y **Bellevue** dentro de la región **Seattle**.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación basada en modelos) utilizando la URL proporcionada por su administrador de TI.

1. Seleccione **Instalaciones** en el panel izquierdo y seleccione **Nuevo**.

1. En la página **Instalaciones nuevas**, especifique los valores apropiados: 

    > [!div class="mx-imgBorder"] 
    > ![introducir-detalles-instalaciones-nuevas](media/enter-details-new-facility.png)

    | **Campo**            | **Descripción**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Región               | Seleccione una región a la que esté asociada esta instalación. Esta lista se llena en función de los datos de **Regiones** que ha creado anteriormente. |
    | Nombre de las instalaciones        | Escriba el nombre de las instalaciones. Por ejemplo, Bellevue.                                                  |
    | Respiradores totales          | Escriba el número total de respiradores disponibles en las instalaciones.                                  |
    | Descripción          | Escriba una descripción opcional.                                                                   |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de estas instalaciones.                                                     |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de estas instalaciones.                                                       |
    |Camas totales      | Se calcula automáticamente.|
    |Total ocupado      | Se calcula automáticamente.|
    |Dirección del centro      | Escriba la calle, ciudad, condado, estado, código postal, latitud y longitud de la instalación.|

    Si es necesario, introduzca la dirección de las instalaciones.

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Instalaciones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="locations-data"></a>Datos de ubicaciones

La entidad **Ubicaciones** le permite administrar ubicaciones específicas de cada instalación hospitalaria.

> [!NOTE]
> Antes de crear un registro **Ubicaciones**, asegúrese de haber importado los datos de acuidad utilizando el archivo **00 - Acuities Import.xlsx** como se explicó anteriormente en [Paso 4: Cargue la configuración y los datos maestros para su organización](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization). Esto se debe a que se requiere información de acuidad para crear un registro **Ubicación**.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación basada en modelos) utilizando la URL proporcionada por su administrador de TI.

1. Seleccione **Ubicaciones** en el panel izquierdo y seleccione **Nuevo**.

1. En la página **Ubicación nueva**, especifique los valores apropiados:  
 
    > [!div class="mx-imgBorder"]
    > ![introducir-detalles-ubicación-nueva](media/enter-details-new-location.png)

    | **Campo**            | **Descripción**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Nombre de la ubicación        | Escriba el nombre de la ubicación.                                                                       |
    | Instalación             | Seleccione unas instalaciones. Esta lista se llena en función de los datos de **Instalaciones** que ha creado anteriormente. |
    | Suelo                | Escriba la información del piso para la instalación.                                                         |
    | Unidad                 | Escriba la información de unidad para las instalaciones.                                                           |
    | Porcentaje de ocupación | Se calcula automáticamente en función del último censo y los valores totales de camas.                                         |
    | Acuidad      | Seleccione el registro de acuidad asociado con esta ubicación.                                                                                                     |
    | Ubicación COVID      | Seleccione si esta ubicación se usa para tratar pacientes con COVID (**Sí** o **No**).                                                                                                      |
    | Camas totales           | Escriba el número total de camas en las instalaciones.                                                       |
    | Camas supletorias           | Escriba el número de camas supletorias en las instalaciones. Las camas supletorias son aquellas que pueden tener personal por encima y más allá de la capacidad de cama con licencia si los pacientes necesitan ser admitidos.                                                      |
    | Camas bloqueadas         | Escriba el número de camas bloqueadas en las instalaciones.                                                     |
    | Último censo          | Poblaciones basadas en el último registro censal que se creó.                                             |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de esta ubicación.                                                   |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de esta ubicación.                                                     |
    | Orden de ubicación       | Escriba un número que clasifique la ubicación en las listas desplegables de ubicación.                               |
    | Indicador de sitio alternativo  | Para uso interno.                                                                                     |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Ubicaciones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

Puede ver los datos asociados a una ubicación, como los de **Censo**, **Seguimiento de COVID** o **Necesidades de equipo**, abriendo un registro de ubicación existente y seleccionando las pestañas correspondientes. El personal de primera línea introduce los datos asociados utilizando [aplicaciones móviles](use.md).

> [!div class="mx-imgBorder"]
> ![registros relacionados con la ubicación](media/location-related-records.png)


### <a name="departments-data"></a>Datos de departamentos

La entidad **Departamentos** le permite administrar la información de los departamentos de un hospital.

Para crear un registro:

1. Inicie sesión en la aplicación de administración (aplicación basada en modelos) utilizando la URL proporcionada por su administrador de TI.

1. Seleccione **Departamentos** en el panel izquierdo y seleccione **Nuevo**.

1. En la página **Departamento nuevo**, especifique los valores apropiados:

    > [!div class="mx-imgBorder"]
    > ![introducir-detalles-departamento-nuevo](media/enter-details-new-department.png)

    | **Campo**            | **Descripción**                                    |
    |----------------------|----------------------------------------------------|
    | Nombre del departamento      | Escriba un nombre del departamento.                            |
    | Descripción          | Escriba una descripción opcional.                      |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de este departamento. |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de este departamento.   |

1. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Departamentos**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

## <a name="manage-tracking-level-for-mobile-apps"></a>Administrar el nivel de seguimiento de aplicaciones móviles

Los trabajadores de primera línea pueden rastrear la información por *ubicación* o *instalaciones* utilizando las aplicaciones móviles (aplicaciones de lienzo). Aquí está el nivel de seguimiento predeterminado de cada aplicación móvil: 

|App  |Nivel de seguimiento predeterminado  |
|--|--|
|Seguimiento de COVID|Ubicación|
|Personal|Ubicación|
|Equipamiento|Ubicación|
|Capacidad de camas|Instalación|
|Suministros|Instalación|
|Necesidades del personal|Instalación|
|Seguimiento de altas|Instalación|

Como administrador, puede cambiar el nivel de seguimiento predeterminado de las aplicaciones móviles.

1. Inicie sesión en la aplicación de administración (aplicación basada en modelos) utilizando la URL proporcionada por su administrador de TI.

1. En la navegación izquierda, seleccione el área **Administración** y luego seleccione **Aplicaciones**. 

    > [!div class="mx-imgBorder"]
    > ![config-admin-app-records](media/admin-apps.png)

1. Seleccione una de las aplicaciones de lienzo para abrir el registro.

1. En el registro de la aplicación, seleccione un valor apropiado en el campo **Nivel de seguimiento**.

    > [!div class="mx-imgBorder"]
    > ![app-tracking-level](media/app-tracking-level.png)

    - Si se selecciona **Ubicación** para una aplicación, los registros creados con la aplicación móvil contendrán información de ubicación e instalación junto con otros datos. Además, un menú desplegable **Ubicación** estará disponible en la aplicación móvil para que los usuarios seleccionen una ubicación para seguir los datos.

    - Si se selecciona **Instalaciones** para una aplicación, los registros creados con la aplicación móvil contendrán solo información de las instalaciones junto con otros datos.

    - Si no selecciona ningún valor para el campo **Nivel de seguimiento**, el nivel de seguimiento *predeterminado*, como se explicó anteriormente, se aplica a las aplicaciones móviles.

1. Seleccione **Guardar** en la esquina inferior derecha para guardar sus cambios.

## <a name="view-common-data-service-dashboards"></a>Ver paneles de Common Data Service

Los siguientes paneles están disponibles de forma predeterminada en la aplicación de administración de Hospital Emergency Response (basada en modelo):

- **Administración de camas**

   Muestra la disponibilidad de camas, el porcentaje de ocupación y el número total de camas en diferentes instalaciones.

- **Equipamiento y suministro**

  Muestra equipos críticos en uso y suministros disponibles en diferentes instalaciones.

- **Administración de personal**

  Muestra el número de miembros del personal solicitados, asignados y disponibles en diferentes instalaciones.

- **Pacientes con COVID**

  Muestra el número de pacientes bajo investigación y que dieron positivo de COVID-19 en diferentes instalaciones.

- **Altas**

  Muestra el número de pacientes previstos para el alta y el alta real.

También puede crear sus propios paneles además de los paneles disponibles de forma predeterminada.

### <a name="manage-dashboards"></a>Administrar paneles

Para administrar paneles:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y navegue hasta su aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Paneles** en el selector de área:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-paneles](media/select-dashboards.png)

3. Seleccione un nombre de panel en la navegación izquierda para ver los gráficos:

    > [!div class="mx-imgBorder"]
    > ![ver-gráficos](media/view-charts.png)

    > [!NOTE]
    > Puede filtrar datos en la parte inferior de la pantalla y los gráficos en la parte superior se actualizan automáticamente con valores filtrados.

4. Seleccione la opción **Expandir** para ver un gráfico en modo de pantalla completa:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-expandir](media/select-expand.png)

### <a name="additional-analysis"></a>Análisis adicional

- **Explorar en profundidad**: puede seleccionar el área del gráfico para explorar en profundidad aún más con atributos adicionales (campos) para una entidad:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-área-gráfico-explorar-en-profundidad](media/select-chart-area-drill-down.png)

- **Actualizar**: puede actualizar los paneles para reflejar los datos actualizados. Puede actualizar todos los gráficos en un tablero específico con **Actualizar todo** o un gráfico seleccionado con **Actualizar**:

    > [!div class="mx-imgBorder"]
    > ![actualizar-paneles](media/refresh-dashboards.png)

- **Ver registros**: seleccione **Más comandos** (**...**) y después **Ver registros** para ver todos los registros asociados a un gráfico dado:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-más-comandos](media/select-more-commands.png)

    > [!NOTE] 
    > Cuando seleccione **Ver registros**, verá la vista de la entidad dividida entre el gráfico y los registros. Cualquier cambio en los filtros para registros en el lado derecho se refleja con actualizaciones automáticas en el gráfico en el lado izquierdo de la pantalla.

Para obtener más información sobre cómo editar un panel existente y actualizar las propiedades de los gráficos, lea [editar un panel existente](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Crear paneles nuevos

También puede crear sus propios paneles y personalizarlos para satisfacer sus necesidades. Para crear un panel nuevo, seleccione **Nuevo** y luego seleccione **Panel de Dynamics 365**:

> [!div class="mx-imgBorder"]
> ![seleccionar-nuevo-panel-dynamics](media/select-new-dynamics-dashboard.png)

Para más información acerca de cómo crear un panel nuevo, lea [crear un panel nuevo](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="view-power-bi-dashboard"></a>Ver el panel de Power BI

Vea los paneles de Power BI para obtener información y tomar decisiones.

### <a name="prerequisites"></a>Requisitos previos

- Power BI capacidad Premium o licencias Power BI profesionales asignadas a usuarios que acceden al informe. 

- Su administrador de TI debe haber publicado el informe de Power BI y otorgarle permisos para acceder a él. Más información: [Publicar el panel de Power BI](deploy-configure.md#publish-the-power-bi-dashboard) 

### <a name="view-the-dashboard"></a>Ver el panel

Inicie sesión en [Power BI](https://apps.powerbi.com) para acceder y ver el panel de Power BI.

> [!div class="mx-imgBorder"]
> ![Ver el panel de Power BI](media/view-powerbi-dashboard.png)

Puede usar los filtros en el lado derecho para filtrar datos para ubicaciones, instalaciones, regiones y sistemas hospitalarios de COVID.

#### <a name="system-at-a-glance-page"></a>Página Sistema de un vistazo 

La **página Sistemas de un vistazo** es la predeterminada o de nivel superior que proporciona una vista general.  

La página muestra una vista resumida de lo siguiente: 

- **Información sobre pacientes de COVID**: muestra el número total de pacientes con COVID, el número de pacientes que resultaron positivos por COVID-19 y el número de pacientes bajo investigación (PUI).

- **Administración de camas**: muestra la disponibilidad de camas, el porcentaje de ocupación, el número de camas supletorias y el número total de camas. También puede usar la cuadrícula a continuación para ver los números por unidades agudas.

- **Información de personal**: muestra el número de pacientes en la UCI, las enfermeras asignadas y la relación enfermera/paciente.  

- **Información de alta del paciente** : muestra el número total de pacientes de estadía prolongada, el número de pacientes previstos para el alta y el alta real.

- **Informacion del equipo**: muestra el número total de respiradores, el número de respiradores en uso y los respiradores disponibles. 

- **Información de suministros**: muestra el número de suministros disponibles por días.

> [!NOTE]
> - Al seleccionar el título en cualquiera de las áreas resumidas, accede a la página de detalles correspondiente para el área. 
> - También puede realizar otras acciones en informes como filtrar y ordenar datos, exportar el informe a PDF y PowerPoint, agregar un foco de atención, etc. Para obtener información detallada sobre las características del informe en Power BI, vea [Informes en Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports)
> - Las columnas más recientes o actualizadas en algunos de estos informes muestran la fecha y la hora en que se actualizaron los datos por última vez. También es fácil identificar la frescura al ver el color de los valores de fecha y hora en estas columnas:
>    - Negro: los datos se actualizaron hace menos de 20 horas
>    - Gris: los datos se actualizaron hace 20 - 24 horas
>    - Rojo: los datos se actualizaron hace más de 24 horas 
 
#### <a name="system-view-page"></a>Página Vista del sistema

La página **Vista del sistema** muestra gráficos con la siguiente información para un sistema hospitalario:
- Respiradores en uso y respiradores disponibles
- Disponibilidad de camas y camas de cuidados intensivos y porcentaje de ocupación
- Total de personal solicitado, número de pacientes (censo) y relación enfermera/paciente
- Suministros disponibles durante un período de tiempo

> [!div class="mx-imgBorder"]
> ![Vista del sistema](media/report-system-view.png)

#### <a name="location-details-page"></a>Página de detalles de ubicación 

En la página **Sistema de un vistazo**, seleccione **yo** en la esquina superior derecha. La página **Detalles de ubicación** muestra datos por ubicación, como el número total de camas, camas disponibles, camas supletorias, pacientes con COVID, etc. 

> [!div class="mx-imgBorder"]
> ![Detalles de ubicación](media/report-location-details.png) 

#### <a name="covid-patients-page"></a>Página Pacientes con COVID 

La página proporciona información detallada sobre los pacientes con COVID, como los pacientes en cada ubicación, la tendencia del paciente a lo largo del tiempo, con los picos y valles para el número de pacientes bajo investigación (PUI), y la cantidad de pacientes positivos, así como una idea de dónde se encuentran los pacientes dentro del hospital.

> [!div class="mx-imgBorder"]
> ![Detalles del paciente COVID](media/report-covid-details.png)

#### <a name="bed-management-page"></a>Página de gestión de camas 

La página proporciona información detallada por ubicación, como el total de camas disponibles, camas de cuidados intensivos disponibles y porcentaje de ocupación.

> [!div class="mx-imgBorder"]
> ![Administración de camas](media/report-bed-details.png)

#### <a name="staffing-details-page"></a>Página de detalles de personal  

La página proporciona detalles sobre el personal por ubicación, número de enfermeras asignadas, número total de pacientes y número de pacientes con COVID. También muestra la relación enfermera / paciente y la relación UCI enfermera / paciente durante un período de tiempo.

> [!div class="mx-imgBorder"]
> ![Detalles del personal](media/report-staff-details.png)

#### <a name="equipment-page"></a>Página de equipamiento 

La página proporciona detalles sobre el equipamiento por ubicación, el número total de respiradores en uso, superpuestos por el número de pacientes con COVID y otros equipamientos, como cinturones, cargadores y capuchas en uso.

> [!div class="mx-imgBorder"]
> ![Detalles del equipamiento](media/report-equipment-details.png)

#### <a name="discharges-page"></a>Página de altas 

La página proporciona detalles sobre los pacientes a largo plazo, los impedimentos para el alta durante un período y la variación en términos de altas reales y anticipadas.

> [!div class="mx-imgBorder"]
> ![Detalles del equipamiento](media/report-discharge-details.png)

#### <a name="supplies-page"></a>Página de suministros 

La página proporciona detalles sobre los suministros por ubicación. También proporciona un cuadro sobre los días disponibles por suministro e instalación, y el suministro disponible durante un período de tiempo.

> [!div class="mx-imgBorder"]
> ![Detalles del equipamiento](media/report-supplies.png)

## <a name="view-and-manage-app-feedback"></a>Ver y administrar comentarios de la aplicación

Todos los comentarios proporcionados por el personal de primera línea que utilizan aplicaciones de lienzo en sus dispositivos móviles se almacenan en la entidad **Comentarios sobre la aplicación** y los administradores pueden ver y administrar esto usando el área **Administración** en el panel de navegación izquierdo en la aplicación de administración.

Para ver y administrar comentarios de la aplicación:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y navegue hasta su aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Administración** en el selector de área.

3. Seleccione **Comentarios sobre la aplicación** para ver una lista de comentarios de aplicaciones enviados por los usuarios. Puede hacer clic en un registro para ver los detalles y marcarlos como revisados o no.  

    > [!div class="mx-imgBorder"]
    > ![seleccionar-comentario-aplicación](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-issues>.

- Para comentarios sobre la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Paso siguiente

[Usar la aplicación móvil Hospital Emergency Response](use.md)
