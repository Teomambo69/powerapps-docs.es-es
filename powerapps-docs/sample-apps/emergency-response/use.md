---
title: Uso de la aplicación de respuesta ante emergencias | Microsoft Docs
description: Tutorial sobre las diferentes aplicaciones y componentes para los usuarios de la plantilla de aplicación de ejemplo de respuesta ante emergencias
author: tapanm-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/26/2020
ms.author: tapanm
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 3c15cbbd69323b716dbd1d034cc1fd107fc28306
ms.sourcegitcommit: ebc78dbc80b1e249f6c4d43e2516e5411ca01cb6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "80296605"
---
# <a name="use-the-emergency-response-app"></a>Uso de la aplicación de respuesta ante emergencias

El personal de los hospitales tiene que hacer frente al desafío que representa el incremento del número de pacientes sin descuidar la administración de la cadena de suministro durante una emergencia. Mediante el uso de la aplicación móvil de respuesta ante emergencias, los trabajadores de primera línea pueden ver y agregar rápidamente datos relativos a respiradores, personal, altas pendientes y pacientes afectados de COVID-19.

## <a name="prerequisites"></a>Requisitos previos

Para empezar a trabajar con la aplicación, debe descargar la aplicación Power Apps Mobile en el dispositivo mediante la tienda de aplicaciones correspondiente.

- **Descarga** de la aplicación [**Power Apps Mobile**](https://powerapps.microsoft.com/downloads)
- En el caso de dispositivos **Apple** con iOS como iPhone y iPad, hay que usar la [**App Store**](https://aka.ms/powerappsios).
- Para dispositivos **Android**, la aplicación se encuentra en [**Google Play**](https://aka.ms/powerappsandroid).

Después de instalar Power Apps Mobile, abra la aplicación desde el dispositivo e inicie sesión con la cuenta de Azure Active Directory de su empresa. Una vez iniciada la sesión, puede ver todas las aplicaciones compartidas por su organización. Para obtener más información, vea [Abrir Power Apps e iniciar sesión](https://docs.microsoft.com/powerapps/user/run-app-client#open-power-apps-and-sign-in).

## <a name="demo-use-the-emergency-response-app"></a>Demostración: uso de la aplicación de respuesta ante emergencias

Vea cómo usar la aplicación de respuesta ante emergencias.

<br/>

> [!VIDEO https://www.youtube.com/embed/H1u6SYt3UsQ]

## <a name="app-launcher"></a>Iniciador de aplicaciones

![Iniciador de aplicaciones](media/use/app-launcher.png)

La aplicación móvil de respuesta ante emergencias tiene una estructura modular con aplicaciones diferentes, según corresponda a su rol. Abra la aplicación móvil de respuesta ante emergencias desde Power Apps Mobile, y seleccione los campos correspondientes a **Hospital system** (Sistema hospitalario) y **Region, Facility** (Región, instalación) y seleccione **Siguiente**.

> [!NOTE]
> Al abrir el iniciador de la aplicación móvil de respuesta ante emergencias o cualquiera de sus componentes por *primera vez*, se le pedirá su consentimiento para permitir que la aplicación lea su perfil de *usuario de Office 365* y la *ubicación*. Debe seleccionar **Permitir** para poder empezar a usar la aplicación seleccionada. Para más información, consulte [Dar consentimiento](https://docs.microsoft.com/powerapps/user/run-app-client#give-consent).

## <a name="app-components"></a>Componentes de la aplicación

![Componentes de la aplicación móvil de respuesta ante emergencias](media/use/app-components.png)

La aplicación de solución de ejemplo de respuesta ante emergencias consta de varias aplicaciones para mejorar la experiencia del usuario. En función de su rol, puede ver una o varias aplicaciones en el **Iniciador de aplicaciones** para la aplicación móvil de respuesta ante emergencias.

- **Staff + equipment**
     (Personal y equipamiento)<br> Recopile el estado de los equipos críticos y enfermeros por ubicación en esa instalación.

- **Supplies**
     (Suministros)<br> Realice un seguimiento de los suministros clave para controlar, administrar y predecir las existencias del inventario de forma más eficaz. 

- **Staffing needs**
     (Necesidades del personal)<br> Recopile solicitudes de personal por departamento, rol y urgencia.

- **COVID-19 stats**
     (Estadísticas de COVID-19)<br> Recopile el estado de cuántos pacientes son sospechosos de padecer COVID-19 y cuántos han dado positivo en la prueba.

- **Discharge planning**
     (Planeación de altas)<br> Recopile el estado y las proyecciones de altas de los pacientes.

## <a name="staff--equipment"></a>Staff + equipment (Personal y equipamiento)

![Staff + equipment (Personal y equipamiento)](media/use/staff-equipment.png)

Envíe un inventario específico de la ubicación relativo a enfermeros, pacientes y equipos. La lista de áreas consta de todas las ubicaciones específicas de las instalaciones seleccionadas en el **Iniciador de aplicaciones**. Seleccione la ubicación en las opciones disponibles para actualizar otros campos.

Después de seleccionar un área, escriba los valores necesarios para que los campos guarden los registros en la base de datos de la solución. No es necesario especificar valores para cada campo de la pantalla. Escriba un número para el campo que tenga que guardar en la base de datos de la solución.

Por ejemplo, si el número de enfermeros tiene que ser 3, escriba 3 en **Registered nurses on duty - Requested** (Enfermeros en servicio - Solicitado) y seleccione **Send** (Enviar). Si también necesita actualizar los respiradores en uso para que sean 6, escriba 3 en **Registered nurses on duty - Requested** (Enfermeros en servicio - Solicitado), seleccione 6 en **Vents** (Respiradores) en **Equipment in use** (Equipamiento en uso) y seleccione **Send** (Enviar).

Seleccione **Atrás** en la parte superior izquierda si desea volver al **Iniciador de aplicaciones** sin enviar ningún cambio. El botón **Enviar** envía los valores especificados.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre de la opción**               | **Descripción**                                                                                   |
|-------------------------------|---------------------------------------------------------------------------------------------------|
| Ubicación                      | El nombre y el tipo de la habitación, el pabellón o cualquier otra ubicación especializada dentro de la instalación seleccionada. |
| Number of patients (Número de pacientes)            | Número total actual de pacientes en la ubicación seleccionada.                                        |
| **Registered nurses on duty** (Enfermeros en servicio) |                                                                                                   |
| *Asociados*                    | Número de enfermeros asociados presentes en la ubicación seleccionada.                             |
| *Requested* (Solicitado)                   | Número de enfermeros solicitados para la ubicación seleccionada.                                  |
| *Assigned* (Asignado)                    | Número de enfermeros asignados a la ubicación seleccionada.                                    |
| *Unassigned* (Sin asignar)                  | Número de enfermeros sin asignar a ninguna tarea en la ubicación seleccionada.                    |
| **Equipment in use** (Equipo en uso)          |                                                                                                   |
| *Vents* (Respiradores)                       | Número de respiradores en uso en la ubicación seleccionada.                                            |
| *PAPR hoods* (Capuchas respiradoras)                  | Número de capuchas respiradoras a batería para purificar el aire en uso en la ubicación seleccionada.                 |
| *PAPR belts* (Cinturones respiradores)                  | Número de cinturones respiradores a batería para purificar el aire en uso en la ubicación seleccionada.                 |
| *PAPR chargers* (Cargadores de respiradores)               | Número de cargadores de respiradores a batería para purificar el aire en uso en la ubicación seleccionada.              |

## <a name="supplies"></a>Supplies (Suministros)

![Supplies (Suministros)](media/use/supplies.png)

Vea el inventario de suministros con la aplicación **Supplies** (Suministros). Puede actualizar las cantidades de los componentes de suministros en todo el inventario de instalaciones y la tasa de evolución diaria desde esta aplicación.

> [!NOTE]
> Escriba los valores en ambos campos: **In stock** (En existencias) y **Used past 24 hr** (Utilizado en las últimas 24 h) antes de enviar.

Seleccione **Atrás** en la parte superior izquierda si desea volver al **Iniciador de aplicaciones** sin enviar ningún cambio. El botón **Enviar** envía los valores especificados.

### <a name="fields-and-description"></a>Campos y descripción

La lista de elementos de la aplicación de suministros puede variar en función de los requisitos de su organización. Consulte los recursos de la organización para obtener descripciones de los nombres de suministro.

Los administradores de TI pueden agregar o actualizar la lista de elementos de la aplicación de suministros mediante la aplicación controlada por modelos para Power Apps. Para más información, vea la [guía de configuración](deploy-configure.md).

**Nota**: Los valores de elemento de inventario de suministro deben estar en formato de número.

## <a name="staffing-needs"></a>Staffing needs (Necesidades del personal)

![Staffing needs (Necesidades del personal)](media/use/staffing-needs.png)

Recopila las solicitudes del grupo de trabajo de la instalación seleccionada. Antes de poder enviar la solicitud del grupo de trabajo para una instalación, asegúrese de que los campos marcados como *obligatorios* contengan valores.

Seleccione **Atrás** en la parte superior izquierda si desea volver al **Iniciador de aplicaciones** sin enviar ningún cambio. El botón **Enviar** envía los valores especificados.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**           | **Descripción**                                                                            |
|--------------------------|--------------------------------------------------------------------------------------------|
| Departamento               | Nombre del departamento que solicita un trabajador. Este campo es *obligatorio*.             |
| Department location (Ubicación del departamento)                 | Ubicación del departamento.                                                                |
| Tipo de solicitud             | Tipo de solicitud de puesto de trabajo: clínico o no clínico. Este campo es *obligatorio*. |
| Role needed (Rol necesario)              | Rol del puesto solicitado; por ejemplo, cuidador o enfermero.                          |
| Needed now or next shift (Necesario ahora o en el turno siguiente) | Seleccione un turno para el puesto solicitado: el turno actual o un turno próximo.                |
| Cantidad | Cantidad necesaria en formato de número.                |
| Detalles                  | Describa detalles adicionales o comentarios para la solicitud del grupo de trabajo.                        |

## <a name="covid-19-stats"></a>COVID-19 stats (Estadísticas de COVID-19)

![COVID-19 stats (Estadísticas de COVID-19)](media/use/covid19-stats.png)

Envíe los detalles específicos de COVID-19 mediante la aplicación **COVID-19 stats** (Estadísticas de COVID-19). Puede actualizar el número específico de pacientes en investigación y los pacientes positivos.

También puede agregar otra ubicación mediante el botón **+ Add another location** (+Agregar otra ubicación) para enviar estadísticas de más de una ubicación.

Seleccione **Atrás** en la parte superior izquierda si desea volver al **Iniciador de aplicaciones** sin enviar ningún cambio. El botón **Enviar** envía los valores especificados.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**  | **Descripción**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Ubicación        | El nombre y el tipo de la habitación, el pabellón o cualquier otra ubicación especializada dentro de la instalación seleccionada.  |
| PUI (pacientes investigados)            | Número de pacientes en investigación.                                                            |
| Positivo        | Número de pacientes positivos en COVID-19.                                                         |

## <a name="discharge-planning"></a>Discharge planning (Planeación de altas)

![Altas](media/use/discharge.png)

Envíe información de altas y el estado de los pacientes con el número total mediante la aplicación  **Discharge planning** (Planeación de altas). Puede actualizar los detalles de las altas de las últimas 24 horas, las dificultades para las altas y el desglose de las altas.

Seleccione **Atrás** en la parte superior izquierda si desea volver al **Iniciador de aplicaciones** sin enviar ningún cambio. El botón **Enviar** envía los valores especificados.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**            | **Descripción**                                                    |
|---------------------------|--------------------------------------------------------------------|
| Authorization             | Número de pacientes en el proceso de autorización.                   |
| Durable medical equipment (Equipo médico duradero) | Número de pacientes que usan el equipo medico duradero.            |
| Guardianship (Tutela)              | Número de pacientes en tutela.                             |
| Home + Community Services (Servicios domésticos y comunitarios) | Número de pacientes que usan servicios domésticos y comunitarios.               |
| Ubicación                 | Número de disposiciones necesarias.                                       |
| Skilled Nursing Facility (Instalación de enfermería especializada)  | Número de instalaciones de enfermería especializadas.                              |
| **Altas**            |                                                                    |
| Past 24 h (Últimas 24 h)                 | Número de pacientes con el alta prevista en las últimas 24 h.  |
| Likely next 24 h (Probables en las próximas 24 h)          | Número de pacientes dados de alta en las últimas 24 h.                    |
## <a name="other-options"></a>Otras opciones

En esta sección se explican otras acciones que puede realizar con los componentes de la aplicación móvil de respuesta ante emergencia.

### <a name="end-shift---sign-out"></a>Fin de turno - cierre de sesión

Puede cerrar la sesión desde la aplicación con el icono de perfil que se encuentra en la parte superior izquierda de la pantalla.  

![Cierre de sesión](media/use/sign-out.png)

> [!NOTE]
> Es posible que el *cierre de sesión* no esté disponible si el administrador de TI ha deshabilitado el uso compartido de dispositivos.

### <a name="give-feedback"></a>Enviar comentarios

![Enviar comentarios](media/use/give-feedback.png)

Puede enviar comentarios con la opción **App feedback** (Comentarios de la aplicación) desde cualquier componente de aplicación móvil de respuesta ante emergencias. Al seleccionar **App feedback** (Comentarios de la aplicación), se le presentan opciones para elogiar algo, plantear una idea o notificar un problema con la aplicación.

### <a name="switch-facility"></a>Cambio de instalación

![Cambio de instalación](media/use/switch-facility.png)

Cambie la instalación en cualquier momento seleccionando el nombre de la instalación en la parte superior derecha de la pantalla. Después de seleccionar el nombre de la ubicación, se le dirigirá a la pantalla del **Iniciador de aplicaciones** donde puede seleccionar otro hospital, región o instalación.

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para notificar un problema con la aplicación de ejemplo de respuesta ante emergencias, visite <https://aka.ms/emergency-response-issues>.

- Para ofrecer comentarios sobre la aplicación de ejemplo de respuesta ante emergencias, visite <https://aka.ms/emergency-response-feedback>.


