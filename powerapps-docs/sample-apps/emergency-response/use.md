---
title: Usar la aplicación Hospital Emergency Response | Microsoft Docs
description: Recorrido por diferentes aplicaciones y componentes para los usuarios de la plantilla de aplicación de muestra de Hospital Emergency Response
author: pankajarora-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/05/2020
ms.author: tapanm
ms.reviewer: pankar
searchScope:
- PowerApps
ms.openlocfilehash: fcb4d780d5b9a1f888f66270a5a4f65a2d83dba6
ms.sourcegitcommit: 604b6ea4be80c9dc9c2e21e24a497b69f683f2f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "3229183"
---
# <a name="use-the-hospital-emergency-response-app"></a>Usar la aplicación Hospital Emergency Response

El personal del hospital tiene el desafío de cumplir con un aumento en el número de pacientes mientras gestiona la cadena de suministro durante una emergencia. Al usar la aplicación móvil Hospital Emergency Response, los trabajadores de primera línea pueden ver y agregar rápidamente datos para respiradores, personal, altas pendientes y pacientes relacionados con COVID-19.

## <a name="prerequisites"></a>Requisitos previos

Para comenzar con la aplicación, debe descargar Power Apps Mobile en su dispositivo utilizando la tienda de aplicaciones del dispositivo.

- **Descargar** [**Power Apps Mobile**](https://powerapps.microsoft.com/downloads)
    - Para dispositivos **Apple** con iOS como iPhone e iPad, use el [**App store**](https://aka.ms/powerappsios)
    - Para dispositivos **Android**, use [**Google Play**](https://aka.ms/powerappsandroid)
- Asegúrese de que su organización haya implementado y configurado la aplicación Hospital Emergency Response como se explica en [Implemente y configure la aplicación](deploy-configure.md).

Después de instalar Power Apps Mobile, abra la aplicación desde su dispositivo e inicie sesión con su cuenta de empresa Azure Active Directory. Puede ver todas las aplicaciones compartidas por su organización una vez que inicie sesión. Para más información, vea [Iniciar sesión en Power Apps en dispositivo móvil](https://docs.microsoft.com/powerapps/user/run-app-client#open-power-apps-and-sign-in).

## <a name="demo-use-the-hospital-emergency-response-app"></a>Demostración: Usar la aplicación Hospital Emergency Response

Vea cómo usar la aplicación Hospital Emergency Response.

<br/>

> [!VIDEO https://www.youtube.com/embed/H1u6SYt3UsQ]

## <a name="hospital-emergency-response-app"></a>Aplicación Hospital Emergency Response

![Aplicación Hospital Emergency Response](media/use/app-launcher.png)

La aplicación móvil Hospital Emergency Response tiene una estructura modular con diferentes aplicaciones según corresponda a su función. Abra la aplicación móvil Hospital Emergency Response desde Power Apps Mobile, seleccione su **Sistema hospitalario**, **Región, Instalaciones** y seleccione **Siguiente** para empezar.

> [!NOTE]
> Cuando inicie la aplicación móvil Hospital Emergency Response o cualquiera de sus componentes por *primera vez*, se le pedirá su consentimiento para permitir que la aplicación lea su perfil de *Office 365 Users* y su *Ubicación*. Debes elegir **Permitir** antes de que pueda comenzar a usar la aplicación seleccionada. Para obtener más información, consulte [dar consentimiento](https://docs.microsoft.com/powerapps/user/run-app-client#give-consent).

## <a name="app-components"></a>Componentes de aplicación

![Componentes de la aplicación móvil Hospital Emergency Response](media/use/app-components.png)

La aplicación de solución de muestra Hospital Emergency Response consta de varias aplicaciones para mejorar la experiencia del usuario. Dependiendo de su rol, puede ver uno o más componentes en la **Aplicación Hospital Emergency Response**.

- **Personal + equipamiento**
    <br> Recopile el estado de las RN y el equipamiento crítico por ubicación en esa instalación.

- **Suministros**
    <br> Rastree los suministros clave para seguir, administrar y pronosticar el inventario de manera más efectiva. 

- **Necesidades del personal**
    <br> Recopile solicitudes de personal por departamento, rol y urgencia.

- **Estadísticas de COVID-19**
    <br> Obtenga información sobre cuántos pacientes están bajo investigación de COVID-19 y cuántos dieron positivo.

- **Planificación de alta**
    <br> Recopile el estado y las proyecciones sobre las altas de pacientes.

## <a name="staff--equipment"></a>Personal + equipamiento

![Personal + equipamiento](media/use/staff-equipment.png)

Envíe un inventario específico de ubicación para enfermeras registradas, pacientes y equipos. La lista de áreas consta de todas las ubicaciones específicas de la instalación elegida en la **Aplicación Hospital Emergency Response**. Seleccione la ubicación de las opciones disponibles para actualizar otros campos.

Después de seleccionar un área, introduzca los valores requeridos para los campos para guardar los registros en la base de datos de la solución. No tiene que introducir valores para cada campo en la pantalla. Introduzca un número para el campo que necesita guardar en la base de datos de la solución.

Por ejemplo, si necesita agregar el número de enfermeras registradas solicitadas como 3, introduzca 3 en el campo **Enfermeras registradas de servicio - Solicitadas** y seleccione **Enviar**. Si también necesita actualizar los respiradores en uso como 6, introduzca 3 en el campo **Enfermeras registradas de servicio - Solicitadas**, luego introduzca 6 en **Respiraderos** en **Equipos en uso** y seleccione **Enviar**.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo.

Después de enviar los datos, tiene la opción de volver a la aplicación **Personal + equipamiento** para crear otro registro utilizando el botón **Seguir otro**. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response**.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre de opción**               | **Descripción**                                                                                   |
|-------------------------------|---------------------------------------------------------------------------------------------------|
| Ubicación                      | El nombre y tipo de la habitación, sala o cualquier otra ubicación especializada dentro de la instalación seleccionada. |
| Número de pacientes            | Número total actual de pacientes en la ubicación seleccionada.                                        |
| **Enfermeras registradas de servicio** |                                                                                                   |
| *Partners*                    | Número de enfermeras registradas asociadas presentes en la ubicación seleccionada.                             |
| *Solicitado*                   | Número de enfermeras registradas solicitadas en la ubicación seleccionada.                                  |
| *Asignado*                    | Número de enfermeras registradas asignadas a la ubicación seleccionada.                                    |
| *Sin asignar*                  | Número de enfermeras registradas no asignadas a ninguna tarea en la ubicación seleccionada.                    |
| **Equipamiento en uso**          |                                                                                                   |
| *Respiradores*                 | Número de respiradores en uso en la ubicación seleccionada.                                            |
| *Capuchas de PAPR*                  | Número de campanas de respiración con purificador de aire con motor en uso en la ubicación seleccionada.                 |
| *Cinturones PAPR*                  | Número de cinturones de respiración con purificador de aire con motor en uso en la ubicación seleccionada.                 |
| *Cargadores PAPR*               | Número de cargadores de respiración con purificador de aire con motor en uso en la ubicación seleccionada.              |


## <a name="supplies"></a>Suministros

![Suministros](media/use/supplies.png)

Vea el inventario de suministros con la aplicación **Suministros**. Puede actualizar las cantidades de componentes de suministro en todo el inventario de las instalaciones y la tasa de consumo diario desde esta aplicación.

> [!NOTE]
> Introduzca valores en ambos campos, **En stock** y **Usado en las últimas 24 horas**, antes de seleccionar **Enviar**.

Seleccione **Atrás** arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response** tras enviar.

### <a name="fields-and-description"></a>Campos y descripción

La lista de elementos de la aplicación de suministros puede ser diferente según los requisitos de su organización. Consulte los recursos de su organización para obtener descripciones de los nombres de los suministros.

Los administradores de TI pueden agregar o actualizar la lista de elementos de la aplicación de suministros utilizando la aplicación basada en modelos para Power Apps. Para obtener más información, consulte [guía de configuración](deploy-configure.md).

> [!NOTE]
> Los valores de los artículos del inventario de suministros deben estar en formato numérico.

## <a name="staffing-needs"></a>Necesidades del personal

![Necesidades del personal](media/use/staffing-needs.png)

Recopila solicitudes de mano de obra para la instalación seleccionada. Antes de poder enviar la solicitud de grupo de trabajo para una instalación, asegúrese de que los campos marcados como *obligatorio* (*) están rellenados.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response** tras enviar.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**           | **Descripción**                                                                            |
|--------------------------|--------------------------------------------------------------------------------------------|
| Departamento               | Nombre del departamento que solicita la solicitud de trabajo. Este campo es *obligatorio*.             |
| Ubicación del departamento      | Ubicación del departamento.                                                                |
| Tipo de solicitud             | Tipo de solicitud de mano de obra, como clínica y no clínica. Este campo es *obligatorio*. |
| Rol necesario              | Rol del trabajo solicitado, como una niñera o una enfermera registrada.                          |
| Necesario ahora o el próximo turno | Seleccione un turno para la mano de obra solicitada, el turno actual o un turno próximo.                |
| Cuántos                 | Cuántos recursos se necesitan, en formato numérico.                |
| Detalles                  | Describa detalles adicionales o comentarios para la solicitud de mano de obra.                        |

## <a name="covid-19-stats"></a>Estadísticas de COVID-19

![Estadísticas de COVID-19](media/use/covid19-stats.png)

Envíe detalles específicos de COVID-19 utilizando la aplicación  **Estadísticas de COVID-19**. Puede actualizar el número de pacientes específicos de la ubicación bajo investigación y los pacientes que resultaron positivos.

También puede agregar otra ubicación usando el botón **+ Agregar otra ubicación** para enviar estadísticas para más de una ubicación.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo.

Después de enviar los datos, tiene la opción de volver a la aplicación **Estadísticas COVID-19** para crear otro registro utilizando el botón **Seguir otro**. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response**.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**  | **Descripción**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Ubicación        | El nombre y tipo de la habitación, sala o cualquier otra ubicación especializada dentro de la instalación seleccionada.  |
| PUIs            | Número de pacientes bajo investigación.                                                            |
| Positivo        | Número de pacientes positivos con COVID-19.                                                         |

## <a name="discharge-planning"></a>Planificación de alta

![Alta](media/use/discharge.png)

Envíe la información del alta y el estado del paciente con el número total utilizando la aplicación  **Planificación de alta**. Puede actualizar los detalles de altas de las últimas 24 horas, las barreras de altas actuales y la separación de las altas.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response** tras enviar.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**            | **Descripción**                                                    |
|---------------------------|--------------------------------------------------------------------|
| Autorización             | Número de pacientes en proceso de autorización.                   |
| Equipo médico duradero | Número de pacientes que usan el equipo médico duradero.            |
| Tutela              | Número de pacientes bajo tutela.                             |
| Hogar + Servicios comunitarios | Número de pacientes que utilizan los servicios del hogar o la comunidad.               |
| Ubicación                 | Número de ubicaciones necesarias.                                       |
| Instalaciones de enfermería especializada  | Número de instalaciones de enfermería especializada.                              |
| **Altas**            |                                                                    |
| Últimas 24 h                 | Número de pacientes que se espera que sean dados de alta en las últimas 24 horas.  |
| Probable en las próximas 24 h          | Número de pacientes que se dados de altas en las últimas 24 horas.                    |

## <a name="other-options"></a>Otras opciones

Esta sección explica otras acciones que puede realizar con los componentes de la aplicación móvil Hospital Emergency Response.

### <a name="end-shift---sign-out"></a>Fin de turno: cerrar sesión

Puede cerrar sesión desde la aplicación usando el ícono de perfil en el lado superior izquierdo de la pantalla.  

![Cerrar sesión](media/use/sign-out.png)

Seleccione el botón **Fin de turno** para finalizar su sesión y cerrar sesión.

> [!NOTE]
> *Fin de turno* puede no estar disponible si su Administrador de TI ha deshabilitado el uso compartido de dispositivos.

### <a name="provide-feedback"></a>Proporcionar comentarios

Puede compartir sus comentarios con la opción **Proporcionar comentarios** desde cualquier componente de la aplicación móvil de Emergency Response. Para compartir sus comentarios, seleccione su perfil desde la esquina superior izquierda y luego seleccione el botón **Proporcionar comentarios**:

![Proporcionar comentarios](media/use/give-feedback.png)

Cuando selecciona **Proporcionar comentarios**, tiene opciones para compartir un elogio, una idea o informar de un problema con la aplicación.

### <a name="switch-facility"></a>Cambiar de instalación

![Cambiar de instalación](media/use/switch-facility.png)

Cambie de instalación en cualquier momento seleccionando el nombre de la instalación en la parte superior derecha de la pantalla. Después de seleccionar el nombre de la ubicación, accederá a la pantalla de la **Aplicación Hospital Emergency Response** donde puede seleccionar un hospital, región o instalación diferente.

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-issues>.

- Para comentarios sobre la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-feedback>.


