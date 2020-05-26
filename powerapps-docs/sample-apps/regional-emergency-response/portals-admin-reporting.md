---
title: Administrar el portal de supervisión y respuesta ante emergencias de la administración pública regional | Microsoft Docs
description: Aprenda a configurar el portal de respuesta ante emergencias para hospitales regionales.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: tapanm
ms.reviewer: tapanm
searchScope:
- PowerApps
ms.openlocfilehash: 2933ad47995915d60b864188c87bb6c9e6953407
ms.sourcegitcommit: c424a17b9c658f4571b5ea26ab6fc8a486051d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341904"
---
# <a name="administer-the-regional-governmentemergency-response-and-monitoring-portal"></a>Administrar el portal de supervisión y respuesta ante emergencias del gobierno regional

El personal del hospital tiene el desafío de cumplir con un aumento en el número de pacientes mientras gestiona la cadena de suministro durante una emergencia. Al utilizar el portal de supervisión y respuesta ante emergencias de la administración pública regional, los administradores pueden ver y actualizar rápidamente los datos relacionados con **Usuarios**, **Sistemas**, **Regiones** e **Instalaciones**. Las partes interesadas pueden ver la información publicada a través de los paneles para conocer el estado actual del sistema de atención médica y tomar medidas.

## <a name="portal-at-a-glance"></a>Vista rápida del portal

Navegue al portal de Power Apps para agregar, editar o eliminar **Usuarios**, **Sistemas**, **Regiones** e **Instalaciones**. La siguiente sección le guía a través de lo que está accesible y lo que puede enviar o actualizar como administrador del portal.

![Vista rápida del portal](media/portal-at-glance.png)

Puede usar los últimos dispositivos móviles y navegadores web cuando usa el portal de supervisión y respuesta ante emergencias de la administración pública regional, excepto Apple iPad.

[!include[cc-getting-started](includes/cc-getting-started.md)]

> [!NOTE] 
> Los administradores deben seleccionar **Sistema Hospitalario, Región** e **Instalaciones**, y luego seleccionar **Siguiente** para ver la configuración administrativa y del panel. Cuando utilice el portal solo para acciones administrativas, como la gestión de usuarios o las revisiones del panel, puede seleccionar cualquier ubicación. Sin embargo, si desea utilizar componentes de usuario como **Personal** o **Equipo**, asegúrese de haber seleccionado la ubicación correcta.

[!include[cc-manage-user-profile](includes/cc-manage-user-profile.md)]

## <a name="administrative-tasks"></a>Tareas administrativas

Puede ver todas las opciones administrativas disponibles después de seleccionar **Administración** en la pantalla de inicio:

![Administración del portal](media/portal-admin-screen.png)

### <a name="administrative-tasks-and-description"></a>Tareas administrativas y descripción

| **Nombre de opción** | **Descripción**                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------|
| [Solicitudes de usuario](#user-requests) | Ver, aprobar o rechazar las solicitudes de los usuarios del portal.
| [Usuarios](#users)       | Crear, editar o desactivar usuarios del portal.                                                         |
| [Sistemas](#systems)      | Crear, editar o eliminar sistemas. |
| [Regiones](#regions)      | Crear o eliminar regiones.                              |
| [Instalaciones](#facilities)    | Crear, editar o eliminar centros.                        |

### <a name="user-requests"></a>Solicitudes de usuario

Puede ver, aprobar y rechazar las solicitudes de los usuarios del portal utilizando la opción de tarea administrativa **Solicitudes de usuario**.

Cuando selecciona **Solicitudes de usuario**, puede ver todas las solicitudes de usuario del portal existentes enviadas que están pendientes de revisión:

![Ver solicitudes de usuario del portal](media/view-portal-user-requests.png)

Puede elegir cambiar la vista y ver las solicitudes aprobadas o rechazadas:

![Cambiar la vista de solicitud de usuario del portal](media/portal-user-requests-views.png)

#### <a name="process-pending-requests"></a>Procesar solicitudes pendientes

Para procesar las solicitudes de usuario pendientes del portal, seleccione **Ver detalles** para una solicitud pendiente en la vista **Solicitudes de usuario del portal pendientes**:

![Ver detalles de la solicitud](media/portal-user-requests-view-details.png)

Desde la vista de detalles, puede verificar la información de contacto del usuario, los roles y puede aprobar o rechazar la solicitud. Los roles seleccionados en el formulario son los roles solicitados. Puede agregar o eliminar roles utilizando la casilla de verificación antes de aprobar o rechazar la solicitud:

![Aprobar o rechazar solicitudes de usuario](media/approve-reject-user-request.png)

Para obtener más información acerca de los roles, vaya a [Roles de usuario](#user-roles).

Seleccione **Aprobar solicitud de acceso** para aprobar la solicitud o **Rechazar solicitud de acceso** para rechazarla.

Cuando rechaza una solicitud, debe proporcionar una razón:

![Razón del rechazo](media/decline-request-reason.png)

#### <a name="request-approval-or-decline-emails"></a>Correos de aprobación o rechazo de solicitud

Dependiendo de si aprueba una solicitud de usuario o la rechaza, el solicitante recibe un correo electrónico con el resultado del proceso de solicitud. Para las solicitudes aprobadas, el correo electrónico incluye un código de invitación que el usuario puede canjear al iniciar sesión por primera vez. Para las solicitudes rechazadas, el correo electrónico incluye el motivo de rechazo especificado al rechazar la solicitud.

### <a name="review-approved-requests"></a>Revisar solicitudes aprobadas

Para ver las solicitudes de usuario aprobadas del portal, seleccione **Ver detalles** para una solicitud aprobada en la vista **Solicitudes de usuario del portal aprobadas**:

![Ver solicitudes aprobadas](media/portal-user-requests-view-approved-details.png)

Seleccione **Rechazar solicitud de acceso** para rechazar una solicitud aprobada existente:

![Rechazar una solicitud aprobada](media/decline-approved-request.png)

### <a name="review-declined-requests"></a>Revisar solicitudes rechazadas

Para ver las solicitudes de usuario aprobadas del portal, seleccione **Ver detalles** para una solicitud aprobada en la vista **Solicitudes de usuario del portal aprobadas**:

![Ver solicitudes aprobadas](media/portal-user-requests-view-declined-details.png)

También puede ver la **Razón de rechazo** obligatoria para cada solicitud como comentario proporcionado cuando la solicitud se rechazó anteriormente.

Seleccione **Aprobar solicitud de acceso** para aprobar una solicitud rechazada existente:

![Aprobar una solicitud aprobada](media/approve-declined-request.png)

### <a name="users"></a>Usuarios

Vaya a **Usuarios** para crear nuevos usuarios que puedan administrar el portal, ver los paneles o usar el portal como trabajador sanitario:

![Usuarios](media/portal-admin-add-user.png)

Hay dos vistas disponibles, **Todos los usuarios activos** y **Mis usuarios activos**. La vista **Todos los usuarios activos** muestra todos los usuarios activos de la organización principal seleccionada. La vista **Mis usuarios activos** muestra todos los usuarios activos de la organización principal seleccionada que son creados o aprobados por el administrador de la organización principal que actualmente tiene la sesión iniciada.

Usted también puede [ver detalles de usuario](#view-user-details), [cambiar roles de usuario](#change-role-for-a-user) y [desactivar usuarios](#deactivate-a-user) desde **Usuarios**.

#### <a name="search-user-details"></a>Buscar detalles de usuarios

Ingrese el texto en el cuadro de búsqueda para ver los resultados filtrados de los usuarios buscados. La búsqueda con comodines (**\***) está habilitada y puede buscar los siguientes campos:

- Nombre completo

- Enviar por correo electrónico

- Teléfono móvil

- Organización principal

Puede usar la búsqueda con comodines y términos parciales para ver los resultados, incluidos números de teléfono.

Por ejemplo, si desea buscar un usuario con **Nombre completo** como **Delores Vasquez**, puede usar las siguientes cadenas de ejemplo en la búsqueda:

- Del\*

- \*Del

- Del\*va

Para buscar por **Teléfono móvil**, puede usar texto similar con comodines reemplazando los caracteres por números.

#### <a name="create-user"></a>Crear usuarios

Para crear usuarios, seleccione el botón **Crear usuario** en el formulario **Usuarios**. Luego ingrese los detalles del nuevo usuario en el formulario:

![Crear usuario](media/portal-admin-create-user.png)

Introduzca **nombre**, **apellido**, **correo electrónico** y **teléfono móvil**, y luego seleccione un rol para el usuario.

##### <a name="user-roles"></a>Roles de usuario

El rol del usuario define los componentes que se muestran en el portal:

![Portal con roles](media/portal-with-roles.png)

Los componentes resaltados son visibles para los usuarios con los siguientes roles asignados:

1. [Trabajador sanitario de la organización](#organizational-healthcare-worker)
2. [Visor de informes](#report-viewer)
3. [Administrador de la organización principal](#parent-organization-administrator)

La siguiente sección explica cada uno de los roles con detalles de lo que puede hacer el miembro del rol:

##### <a name="organizational-healthcare-worker"></a>Trabajador sanitario de la organización

Un trabajador sanitario es un empleado de un sistema hospitalario, como una enfermera registrada. El trabajador sanitario trabaja dentro de una o más instalaciones. El trabajador sanitario recopila datos en las siguientes áreas:

- Capacidad de camas

- Personal

- Equipamiento

- Suministros

- Estadísticas de COVID-19

##### <a name="report-viewer"></a>Visor de informes

Un rol de Visor de informes es para los usuarios que pueden ver los paneles disponibles en este portal. Los miembros del rol Visor de informes pueden ver los siguientes paneles:

- Vista rápida del sistema

- Detalles sobre los pacientes con COVID-19

- Detalles de la capacidad de camas

- Detalles del equipamiento

- Detalles de suministros

##### <a name="parent-organization-administrator"></a>Administrador de la organización principal

Un administrador de organización principal puede crear usuarios que pueden acceder a los detalles de la organización utilizando este portal.

Los miembros del rol Administrador de organización principal pueden:

- Crear nuevos usuarios y agregarlos a los roles **Trabajador sanitario de la organización, visor de informes** o **Administrador de la organización principal**.

- Cambiar los metadatos de la organización con:

    - Crear, editar o eliminar **Sistema**

    - Crear o eliminar **Región**

    - Crear, editar o eliminar **Centro**

> [!TIP]
> Seleccione los 3 roles para permitir que un usuario acceda a todos los componentes.

#### <a name="view-user-details"></a>Ver los detalles del usuario

Puede ver los detalles del usuario seleccionando el menú desplegable para el usuario y luego seleccionando **Ver detalles**:

![Ver opciones de usuario](media/portal-user-view-user-options.png)

##### <a name="change-role-for-a-user"></a>Cambiar el rol de un usuario

Puede agregar o quitar roles de usuario desde los detalles del usuario:

![Ver los detalles del usuario](media/portal-user-view-details.png)

#### <a name="deactivate-a-user"></a>Desactivar un usuario

Seleccione **Desactivar** en el menú desplegable del usuario para desactivar una cuenta de usuario:

![Ver opciones de usuario](media/portal-user-view-user-options.png)

El usuario desactivado ya no se muestra en la lista de usuarios en la vista **Usuarios**.

### <a name="systems"></a>Sistemas

Puede agregar, actualizar o eliminar un **Sistema** utilizando el formulario **Sistema**. Cuando selecciona **Sistema**, puede ver todos los **Sistemas hospitalarios** existentes:

![Sistemas](media/portal-add-system.png)

#### <a name="search-existing-systems"></a>Buscar sistemas existentes

Ingrese el texto en el cuadro de búsqueda para buscar el sistema y filtre la lista de sistemas en el formulario. Puede usar la búsqueda con comodines (**\***) combinado con caracteres de texto para los campos **Nombre del sistema** y **Descripción**.

#### <a name="view-system-details"></a>Ver detalles del sistema

Para ver los detalles de un sistema, seleccione el menú desplegable de un sistema y luego seleccione **Ver detalles**:

![Vista del sistema](media/portal-view-system-details.png)

La página Detalles del sistema muestra **Organización principal, Nombre del sistema**, **Descripción** y **Regiones** del sistema:

![Detalles del sistema](media/portal-system-details.png)

Puede actualizar los campos **Nombre del sistema** y **Descripción** del sistema en los respectivos cuadros de texto.

##### <a name="add-region"></a>Agregar región

Utilice el botón **Agregar región** para agregar una región al sistema actual. Cuando selecciona **Agregar región**, puede agregar detalles de la región, como **Nombre de región** y **Descripción**:

![Agregar región](media/portal-admin-add-region.png)

Puede cambiar el **Sistema** en el menú desplegable antes de agregar una región. Sin embargo, es recomendable agregar una región a un sistema viendo primero el sistema al que desea agregar la región. Esto es porque una vez que selecciona **Enviar**, si el sistema que seleccionó es diferente de la página de detalles que ha abierto, no puede ver la región en la sección de regiones.

#### <a name="create-system"></a>Crear sistema

Para crear un sistema, seleccione **Crear**, ingrese *Nombre del sistema* y *Descripción*:

![Crear sistema](media/portal-admin-create-system.png)

#### <a name="delete-system"></a>Eliminar sistema

Para eliminar un sistema, seleccione el menú desplegable y luego seleccione **Eliminar**:

![Eliminar sistema](media/portal-view-system-details.png)

Seleccione **Eliminar** para eliminar un registro de sistema. Se le solicitará que confirme la eliminación antes de que se elimine el sistema:

![Confirmar eliminación](media/portal-delete-system-confirm.png)

### <a name="regions"></a>Regiones

Puede agregar o eliminar una **región** utilizando el formulario **Agregar región**. Cuando selecciona **Agregar región**, puede ver todos los **Sistemas hospitalarios** existentes:

![Agregar región](media/portal-add-region.png)

#### <a name="search-existing-regions"></a>Buscar regiones existentes

Ingrese el texto en el cuadro de búsqueda para buscar la región y filtre la lista de regiones en el formulario. Puede usar la búsqueda con comodines (**\***) combinado con caracteres de texto para los campos **Nombre de región, Sistema** y **Descripción**.

#### <a name="create-region"></a>Crear región

Para crear una región, seleccione el botón **Crear**, seleccione un **Sistema** y luego ingrese **Nombre de región** y **Descripción:**

![Crear región](media/portal-admin-create-region.png)

#### <a name="delete-region"></a>Eliminar región

Para eliminar una región, seleccione el menú desplegable y luego seleccione **Eliminar**:

![Eliminar región](media/portal-admin-delete-region.png)

Se le solicitará que confirme la eliminación antes de que se elimine la región:

![Confirmación de eliminación de región](media/portal-admin-delete-region-confirm.png)

### <a name="facilities"></a>Instalaciones

Puede agregar o eliminar un **Centro** utilizando el formulario **Centros**. Cuando selecciona **Centros**, puede ver todos los **centros** existentes con región, condado y otros detalles:

![Confirmar eliminación](media/portal-admin-add-facility.png)

#### <a name="search-existing-facilities"></a>Buscar centros existentes

Ingrese el texto en el cuadro de búsqueda para buscar el sistema y filtre la lista de centros en el formulario. Puede usar la búsqueda con comodines (**\***) combinada con caracteres de texto para los campos **Nombre de centro**, **Región** y **Nombre de condado**.

#### <a name="create-facility"></a>Crear centro

Para crear un centro, elija el botón **Crear**:

![Crear centro](media/portal-admin-create-facility.png)

##### <a name="options-and-description"></a>Opciones y descripción

| **Nombre de opción**                                | **Descripción**                                                                                                                                                                                            |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre de las instalaciones                                  | Nombre de del centro.                                                                                                                                                                                      |
| Región                                         | Seleccione una región a la que esté asociada esta instalación.                                                                                                                                                          |
| Capacidad total de camas autorizadas                   | Capacidad total de camas autorizadas, en formato de número.                                                                                                                                                             |
| Capacidad total de camas de UCI (sala SAITA)            | Número total de camas de UCI en salas de aislamiento para infecciones de transmisión aérea (SAIA).                                                                                                                                         |
| Capacidad total de camas de cuidados intensivos (sala SAITA)     | Capacidad total de camas para cuidados agudos (SAITA), en formato numérico.                                                                                                                                                   |
| Capacidad total de ventiladores                     | Capacidad total de respiradores, en formato de número.                                                                                                                                                               |
| Lista de suministros | Seleccione [Lista de suministros](#supplies-list-for-a-facility) para elegir artículos de los suministros disponibles disponibles en la instalación. |
| Número de DOH                                     | El número del Departamento de Salud para esta instalación.                                                                                                                                                         |
| Sigue el protocolo droplet                       | Seleccione **Sí**/**No**. Guarda relación con el hecho de que la instalación siga las Precauciones Droplet para pacientes que se sabe o se sospecha que están infectados con patógenos transmitidos por gotas respiratorias, como en los casos COVID-19. |
| Capacidad total de camas suplementarias                      | Capacidad total de camas complementarias, en formato numérico. Las camas supletorias son aquellas que pueden tener personal por encima y más allá de la capacidad de cama con licencia si los pacientes necesitan ser admitidos.                                               |
| Capacidad total de camas de UCI (sala no SAITA)        | Número de camas totales en la UCI (no SAITA).                                                                                                                                                                       |
| Capacidad total de camas de cuidados intensivos (sala no SAITA) | Capacidad total de camas para cuidados agudos (no SAITA), en formato numérico.                                                                                                                                               |
| Capacidad mortuoria total | Capacidad mortuoria total de la instalación. **Nota**: Cuando se establece en al menos 1, el campo *Número de salas para fallecidos actualmente en uso* está disponible para el formulario **Capacidad de camas** del centro.
| Dirección del centro                               | Calle, ciudad, condado, estado y código postal de la ubicación del centro.                                                                                                                                        |

##### <a name="supplies-list-for-a-facility"></a>Lista de suministros para una instalación

Cuando selecciona **Lista de suministros**, puede seleccionar suministro individual y **Guardar** la lista para asociar los suministros disponibles para la instalación:

![Lista de suministros para una instalación](media/portal-admin-add-facility-supplies.png)

#### <a name="delete-facility"></a>Eliminar instalación

Para eliminar una instalación, seleccione el menú desplegable y luego seleccione **Eliminar**:

![Eliminar instalación](media/portal-admin-delete-facility.png)

Se le solicitará que confirme la eliminación antes de que se elimine la instalación:

![Confirmar eliminación de instalación](media/portal-admin-delete-facility-confirm.png)

#### <a name="edit-facility"></a>Editar instalación

Para editar una instalación, seleccione el menú desplegable y luego seleccione **Editar**:

![Editar instalación](media/portal-admin-delete-facility.png)

Actualice los campos y seleccione **Enviar** para guardar los cambios.

## <a name="get-insights"></a>Obtener información

Si es miembro del rol **Visor de informes**, verá la opción para ver **Paneles**:

![Obtener información](media/portal-admin-get-insights.png)

### <a name="dashboards-overview"></a>Información general sobre los paneles

Los paneles están disponibles para la siguiente información:

- [Vista rápida del sistema](#system-at-a-glance)

- [Detalles sobre los pacientes con COVID-19](#covid-19-patient-details)

- [Detalles de la capacidad de camas](#bed-capacity-details)

- [Detalles del equipamiento](#equipment-details)

- [Detalles de suministros](#equipment-details)

- [Cuadro de mandos de calidad de los datos](#data-health-scorecard)

#### <a name="working-with-reports-in-power-bi"></a>Trabajar con informes en Power BI

Antes de comenzar a revisar los paneles disponibles, familiarícese con los conceptos y pautas generales de visualización de informes:

- Seleccionar el ícono de información (i) en cualquiera de las áreas resumidas lo lleva a la página de detalles correspondiente para el área.

- También puede realizar otras acciones en los informes, como filtrar y ordenar datos, exportar el informe a PDF y PowerPoint, agregar un resaltado, etc. Para obtener información detallada sobre las características del informe en Power BI, vea [Informes en Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports).

- Las columnas más recientes o actualizadas en algunos de estos informes muestran la fecha y la hora en que se actualizaron los datos por última vez. También es fácil identificar la frescura al ver el color de los valores de fecha y hora en estas columnas:

- **Negro**: los datos se actualizaron hace menos de 20 horas

- **Gris**: los datos se actualizaron hace 20 - 24 horas

- **Rojo**: los datos se actualizaron hace más de 24 horas

### <a name="system-at-a-glance"></a>Vista rápida del sistema

Vea las estadísticas relacionadas con todo el **Sistema hospitalario** en una sola vista con el panel **Sistema de un vistazo**:

![Panel](media/portal-admin-powerbi-reports.png)

El panel muestra un resumen para lo siguiente:

- **Estadísticas de COVID-19**: vea el resumen de pacientes con COVID-19 en números: pacientes totales, pacientes bajo investigación, pacientes positivos y pacientes intubados.

- **Capacidad de camas**: vea los datos resumidos, con **Disponibilidad** y **Ocupación**, para las categorías de camas autorizadas, supletorias, de UCI y agudos.

- **Disponibilidad de camas por condado**: vea la disponibilidad de camas con el número total de camas, la disponibilidad de camas en UCI/agudos/supletorias y el total de todas las camas disponibles en todos los condados.

- **Suministros**: vea información de suministros con días disponibles para cada uno por separado.

- **Equipo**: vea los números resumidos de los respiradores y equipos disponibles, en uso y necesarios.

### <a name="covid-19-patient-details"></a>Detalles sobre los pacientes con COVID-19

Vea detalles de los pacientes en relación con la COVID-19, como un resumen de sospechosos de COVID, positivos e intubaciones. El panel también muestra detalles por condado en la parte inferior.

También puede ver los condados en el mapa y los condados están codificados por colores para la segregación. Un gráfico en la parte inferior derecha del panel muestra los casos positivos de COVID-19 y los sospechosos con líneas de tiempo que explican las tendencias recientes y pasadas:

![Detalles del paciente](media/portal-admin-powerbi-patients.png)

#### <a name="map"></a>Asignar

Desplácese sobre un condado dentro del mapa para ver los números de casos sospechosos de COVID-19 específicos del condado, así como los casos positivos y el número de intubados:

![Mapa de pacientes](media/portal-admin-powerbi-map.png)

Del mismo modo, puede pasar el cursor sobre el gráfico de línea de tiempo para ver números específicos de fechas en la información sobre herramientas a medida que avanza por las fechas.

### <a name="bed-capacity-details"></a>Detalles de la capacidad de camas

Vea información relacionada con las camas, como la disponibilidad de camas con números de camas autorizadas, para agudos, SAITA/no SAITA, supletorias y de UCI. También puede ver los detalles en formato tabular en la parte inferior con datos de camas por condado y en formato porcentual. El mapa está codificado por colores para los condados, con un color más claro para los números más bajos y aumenta en la oscuridad a medida que aumenta el número. El cuadro en la parte inferior derecha muestra las diferencias de ocupación en función de las fechas para el análisis de tendencias:

![Capacidad de camas](media/portal-admin-powerbi-bed-capacity.png)

#### <a name="map"></a>Asignar

Cuando pasa el cursor sobre el área del mapa y señala un condado, puede ver la información relacionada con el condado:

![Mapa de capacidad de camas](media/portal-admin-powerbi-map1.png)

Del mismo modo, puede pasar el cursor sobre el gráfico de línea de tiempo para ver números específicos de fechas en la información sobre herramientas a medida que avanza por las fechas.

### <a name="equipment-details"></a>Detalles del equipamiento

Vea los detalles de equipos por condado, como la disponibilidad y el consumo de respiradores con el panel **Detalles del equipo**:

![Detalles del equipamiento](media/portal-admin-powerbi-equipment.png)

Puede ver la cantidad total de disponibilidad de equipos en la parte superior izquierda y la tabla detallada en la parte inferior izquierda. El mapa muestra datos de equipos específicos del condado con un color más claro para menos requisitos y más oscuro para más requisitos.

El gráfico de escala de tiempo en la parte inferior derecha muestra información sobre el equipamiento para el análisis de tendencias a lo largo del tiempo:

#### <a name="map"></a>Asignar

Cuando pasa el cursor sobre el área del mapa y señala un condado, puede ver la información relacionada con el condado:

![Mapa de equipamiento](media/portal-admin-powerbi-equipment-map.png)

Del mismo modo, puede pasar el cursor sobre el gráfico de línea de tiempo para ver números específicos de fechas en la información sobre herramientas a medida que avanza por las fechas.

### <a name="supply-details"></a>Detalles del suministro

Vea los detalles de los suministros por condado, como la disponibilidad y el consumo de respiradores con el panel **Detalles de suministros**:

![Detalles del suministro](media/portal-admin-powerbi-supply.png)

Puede ver los detalles de los suministros a la izquierda según el mapa **Sistema de salud** de la derecha y un desglose de suministros en formato gráfico en la parte inferior.

#### <a name="map"></a>Asignar

Cuando pasa el cursor sobre el área del mapa y señala un condado, puede ver la información relacionada con el condado:

![Mapa de suministro](media/portal-admin-powerbi-supply-map.png)

Del mismo modo, puede pasar el cursor sobre el gráfico de línea de tiempo para ver números específicos de fechas en la información sobre herramientas a medida que avanza por las fechas.

### <a name="data-health-scorecard"></a>Cuadro de mandos de calidad de los datos

Vea la higiene de los datos de una instalación seleccionada utilizando el panel **Cuadro de mando de calidad de datos**. Seleccione una instalación de la lista de instalaciones disponibles y luego seleccione **Clic aquí para continuar** para ver el cuadro de mando:

![Seleccionar un centro](media/dashboard-data-health-facility-select.png)

El panel muestra la clasificación de actualización de datos, la actualización de datos en porcentaje y el estado diario en todos los componentes. Un gráfico de fecha muestra la finalización de datos de la instalación seleccionada en comparación con el promedio de todas las instalaciones para un conjunto de datos dado. La información sobre la integridad de los datos en función de las instalaciones también está disponible en formato tabular con una lista de todas las instalaciones de la última semana:

![Cuadro de mandos de calidad de los datos](media/data-health-scorecard-dashboard.png)

## <a name="general-portal-options"></a>Opciones generales del portal

[!include[cc-general-options](includes/cc-general-options.md)]

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-issues>.

- Para comentar la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-feedback>.
