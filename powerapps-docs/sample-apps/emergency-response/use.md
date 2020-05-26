---
title: Usar la aplicación móvil Hospital Emergency Response | Microsoft Docs
description: Recorrido por diferentes aplicaciones y componentes para los usuarios de la plantilla de aplicación de muestra de Hospital Emergency Response
author: pankajarora-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/28/2020
ms.author: pankar
ms.reviewer: tapanm
searchScope:
- PowerApps
ms.openlocfilehash: 1aea1458a0bb02915736df1a88ba79bf4252f34c
ms.sourcegitcommit: 08184794f3438c8293b88dbbd16bfe8be4f6c229
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2020
ms.locfileid: "3322129"
---
# <a name="use-the-hospital-emergency-response-mobile-app"></a>Usar la aplicación móvil Hospital Emergency Response

El personal del hospital tiene el desafío de cumplir con un aumento en el número de pacientes mientras gestiona la cadena de suministro durante una emergencia. Al usar la aplicación móvil Hospital Emergency Response, los trabajadores de primera línea pueden ver y agregar rápidamente datos para respiradores, personal, altas pendientes y pacientes relacionados con COVID-19.

## <a name="prerequisites"></a>Requisitos previos

Para comenzar con la aplicación móvil, debe descargar Power Apps Mobile en su dispositivo utilizando la tienda de aplicaciones del dispositivo.

- **Descargar** [**Power Apps Mobile**](https://powerapps.microsoft.com/downloads)
    - Para dispositivos **Apple** con iOS como iPhone e iPad, use el [**App store**](https://aka.ms/powerappsios)
    - Para dispositivos **Android**, use [**Google Play**](https://aka.ms/powerappsandroid)
- Asegúrese de que su organización ha implementado y configurado la aplicación móvil de respuesta a emergencias hospitalarias como se explica en [Implementar y configurar la aplicación](deploy-configure.md).

Después de instalar Power Apps Mobile, abra la aplicación desde su dispositivo e inicie sesión con su cuenta de empresa Azure Active Directory. Puede ver todas las aplicaciones compartidas por su organización una vez que inicie sesión. Para más información, vea [Iniciar sesión en Power Apps en dispositivo móvil](https://docs.microsoft.com/powerapps/user/run-app-client#open-power-apps-and-sign-in).

## <a name="demo-use-the-hospital-emergency-response-mobile-app"></a>Demo: Usar la aplicación móvil Hospital Emergency Response

Vea cómo usar la aplicación móvil de respuesta a emergencias hospitalarias.

<br/>

> [!VIDEO https://www.youtube.com/embed/H1u6SYt3UsQ]

## <a name="hospital-emergency-response-mobile-app"></a>Aplicación móvil Hospital Emergency Response

![Aplicación móvil Hospital Emergency Response](media/use/app-launcher.png)

La aplicación móvil Hospital Emergency Response tiene una estructura modular con diferentes aplicaciones según corresponda a su función. Abra la aplicación móvil Hospital Emergency Response desde Power Apps Mobile, seleccione su **Sistema hospitalario**, **Región, Instalaciones** y seleccione **Siguiente** para empezar.

> [!NOTE]
> Cuando inicie la aplicación móvil Hospital Emergency Response o cualquiera de sus componentes por *primera vez*, se le pedirá su consentimiento para permitir que la aplicación lea su perfil de *Office 365 Users* y su *Ubicación*. Debes elegir **Permitir** antes de que pueda comenzar a usar la aplicación seleccionada. Para obtener más información, consulte [dar consentimiento](https://docs.microsoft.com/powerapps/user/run-app-client#give-consent).

## <a name="app-components"></a>Componentes de aplicación

![Componentes de la aplicación móvil Hospital Emergency Response](media/use/app-components.png)

La aplicación de solución de muestra Hospital Emergency Response consta de varias aplicaciones para mejorar la experiencia del usuario. En función de su rol, es posible que vea uno o más componentes en la **aplicación móvil de respuesta a emergencias hospitalarias**.

- **Capacidad de camas**
    <br> Recopile información sobre la cama, como camas autorizadas, camas de UCI, camas de UCI pediátrica/ cuidados intensivos y otros datos de capacidad de camas.

- **Estadísticas de COVID-19**
    <br> Obtenga información sobre cuántos pacientes están bajo investigación de COVID-19 y cuántos dieron positivo.

- **Equipamiento**
    <br> Realice un seguimiento de la información del equipamiento, como respiradores VPPNI y PAPR.

- **Personal**
    <br> Recopile información sobre el número de pacientes y el estado de ED, como partners, asignados, solicitados y no asignados.

- **Suministros**
    <br> Rastree los suministros clave para seguir, administrar y pronosticar el inventario de manera más efectiva. 

- **Necesidades del personal**
    <br> Recopile solicitudes de personal por departamento, rol y urgencia.

- **Planificación de alta**
    <br> Recopile el estado y las proyecciones sobre las altas de pacientes.

> [!NOTE]
> De forma predeterminada, puede rastrear información en las siguientes aplicaciones en el nivel de *ubicación*: **Estadísticas de COVID-19**, **Equipamiento** y **Personal**. En el resto de las aplicaciones, puede seguir información en el nivel de *instalaciones* por defecto. Su administrador puede cambiar el nivel de seguimiento predeterminado, si es necesario. Más información: [Administrar el nivel de seguimiento de aplicaciones móviles](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

## <a name="bed-capacity"></a>Capacidad de camas

![Capacidad de camas](media/use/bed-capacity.png)

Envíe información relacionada con las camas, como las camas autorizadas, camas de UCI (SAITA/no SAITA), camas de cuidados intensivos (SAITA/no SAITA) y si la instalación seleccionada dispone de personal para toda su capacidad de camas autorizadas.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo.

Después de enviar los datos, seleccione **Inicio** para volver a la **Aplicación Respuesta ante emergencias hospitalarias**.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre de opción**                                               | **Descripción**                                                                       |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------|
| ¿Cuántas camas autorizadas están actualmente en uso en este centro? | Número de camas autorizadas actualmente en uso en este centro.                            |
| N.º de camas de UCI (sala SAITA) en uso               | Número de camas de UCI en la sala de aislamiento de infección aérea (sala SAITA) actualmente en uso.                                      |
| N.º de camas de UCI (sala no SAITA) en uso           | Número de camas de UCI (sala no SAIA) actualmente en uso.                                  |
| N.º de camas de cuidados intensivos (sala SAITA) en uso        | Número de camas de cuidados intensivos (sala SAIA) actualmente en uso.                               |
| N.º de camas de cuidados intensivos (sala no SAITA) en uso    | Número de camas de cuidados intensivos (sala no SAIA) actualmente en uso.                           |
| ¿El centro dispone de personal para toda su capacidad de camas autorizadas?    | Sí/No Si la respuesta es No, tiene la opción de seleccionar todos los motivos que correspondan: <br> - Personal <br> - Espacio <br> - EPI <br> - Equipamiento <br> - Volumen bajo de pacientes |
| ¿Puede aumentar el número de camas por encima de las autorizadas?              | Sí/No Si la respuesta es No, tiene la opción de seleccionar todos los motivos que correspondan: <br> - Personal <br> - Espacio <br> - EPI <br> - Equipamiento <br> - Volumen bajo de pacientes  |
| N.º de camas suplementarias actualmente en uso                         | Número de camas suplementarias actualmente en uso.                                                |
| N.º de camas de UCI pediátricas (SAITA y no SAITA) actualmente en uso | Número de camas de UCI pediátrica (SAITA y no SAITA) actualmente en uso en estas instalaciones. |
| N.º de camas de cuidados intensivos pediátricos (SAITA y no SAITA) actualmente en uso | Número de camas de cuidados intensivos pediátricos (SAITA y no SAITA) actualmente en uso en este centro. |  

## <a name="covid-19-stats"></a>Estadísticas de COVID-19

![Estadísticas de COVID-19](media/use/covid19-stats.png)

Envíe detalles específicos de COVID-19 utilizando la aplicación  **Estadísticas de COVID-19**. Puede actualizar los detalles del paciente específicos de la ubicación, como sospechosos, positivos, intubados y dados de alta.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo.

Después de enviar los datos, tiene la opción de volver a la aplicación **Estadísticas COVID-19** para crear otro registro utilizando el botón **Seguir otro**. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response**.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**  | **Descripción**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Ubicación        | El nombre y tipo de la habitación, sala o cualquier otra ubicación especializada dentro de la instalación seleccionada.  |
| PUIs            | Número de pacientes bajo investigación.                                                            |
| Positivo        | Número de pacientes positivos con COVID-19.                                                         |
| Intubados        | Número de pacientes intubados.                                                         |
| Dados de alta        | Número de pacientes con COVID-19 dados de alta.                                                         |

## <a name="equipment"></a>Equipamiento

![Equipamiento](media/use/equipment.png)

Envíe detalles de equipamiento específicos de la ubicación utilizando la aplicación **Equipamiento**. Puede actualizar la cantidad de equipamiento en uso, como respiradores, VPPN y PAPR.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo.

Después de enviar los datos, tiene la opción de volver a la aplicación **Equipamiento** para crear otro registro utilizando el botón **Seguir otro**. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response**.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre del campo**  | **Descripción**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Ubicación        | El nombre y tipo de la habitación, sala o cualquier otra ubicación especializada dentro de la instalación seleccionada.  |
| Ventiladores            | Número de respiradores en uso.                                                            |
| VPPN        | Número de respiradores mecánicos con presión positiva no invasiva.                                                         |
| Capucha para PAPR        | Número de capuchas para respiradores purificadores (PAPR) de aire forzado en uso.                                                         |
| Cinturones para PAPR (respiradores purificadores de aire forzado)        | Número de cinturones PAPR en uso.                                                         |
| Cargadores para PAPR        | Número de cargadores PAPR en uso.                                                         |

## <a name="staff"></a>Personal

![Personal](media/use/staff.png)

Envíe un inventario específico de ubicación para enfermeras registradas, pacientes y equipos. No tiene que introducir valores para cada campo en la pantalla. Introduzca un número para el campo que necesita guardar en la base de datos de la solución.

Por ejemplo, si necesita agregar el número de enfermeras registradas solicitadas como 3, introduzca 3 en el campo **Enfermeras registradas de servicio - Solicitadas** y seleccione **Enviar**. Si también necesita actualizar **Enfermeras registradas de servicio - Asignadas** en uso como 6, introduzca 3 en el campo **Enfermeras registradas de servicio - Solicitadas**, luego introduzca 6 en **Enfermeras registradas de servicio - Asignadas** y seleccione **Enviar**.

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo.

Después de enviar los datos, tiene la opción de volver a la aplicación **Personal** para crear otro registro utilizando el botón **Seguir otro**. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response**.

### <a name="fields-and-description"></a>Campos y descripción

| **Nombre de opción**               | **Descripción**                                                                                   |
|-------------------------------|---------------------------------------------------------------------------------------------------|
| Ubicación                      | El nombre y tipo de la habitación, sala o cualquier otra ubicación especializada dentro de la instalación seleccionada. |
| Número de pacientes            | Número total actual de pacientes en la ubicación seleccionada.                                        |
| **Enfermeras registradas de servicio** |                                                                                                   |
| *Asociados* <br> Los asociados/ayudantes de ED apoyan al personal de enfermería y pacientes                   | Número de enfermeras registradas asociadas presentes en la ubicación seleccionada.                             |
| *Solicitado* <br> N.º de ED solicitados                  | Número de enfermeras registradas solicitadas en la ubicación seleccionada.                                  |
| *Asignado* <br> N.º de ED con asignación                   | Número de enfermeras registradas asignadas a la ubicación seleccionada.                                    |
| *Sin asignar* <br> N.º de ED sin asignar a ninguna tarea                  | Número de enfermeras registradas no asignadas a ninguna tarea en la ubicación seleccionada.                    |
| **Seguimiento de nivel de instalaciones** |                                                                                                   |
| % del personal sanitario esencial ausente actualmente en este centro                  | Personal de atención esencial actualmente ausente como porcentaje del total para las **instalaciones completas**.                    |

## <a name="supplies"></a>Suministros

![Suministros](media/use/supplies.png)

Recolecte inventario de suministros con la aplicación **Suministros**. Puede actualizar las cantidades de componentes de suministro en todo el inventario de las instalaciones y la tasa de consumo diario desde esta aplicación.

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

## <a name="discharge-planning"></a>Planificación de alta

![Alta](media/use/discharge.png)

Envíe la información del alta y el estado del paciente con el número total utilizando la aplicación  **Planificación de alta**. Puede actualizar los detalles de altas de las últimas 24 horas, las barreras de altas actuales y la separación de las altas. 

Seleccione **Atrás** desde arriba a la izquierda si quiere volver a la **Aplicación Hospital Emergency Response** sin enviar ningún cambio. **Enviar** el botón envía los valores que introdujo. Seleccione **Inicio** para volver a la **Aplicación Hospital Emergency Response** tras enviar.

**Barreras para altas de larga estancia** se actualiza automáticamente con el número total de pacientes que introduce en el formulario por todas las barreras.

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

### <a name="app-feedback"></a>Comentarios sobre la aplicación

Puede compartir sus comentarios con la opción **Comentarios sobre la aplicación** desde cualquier componente de la aplicación móvil de respuesta a emergencias para hospitales. Para compartir sus comentarios, seleccione su perfil en la esquina superior izquierda y luego seleccione el botón **Enviar comentarios**:

![Proporcionar comentarios](media/use/give-feedback.png)

Cuando selecciona **Comentarios sobre la aplicación**, tiene opciones para compartir un elogio, una idea o informar de un problema con la aplicación.

### <a name="switch-facility"></a>Cambiar de instalación

![Cambiar de instalación](media/use/switch-facility.png)

Cambie de instalación en cualquier momento seleccionando el nombre de la instalación en la parte superior derecha de la pantalla. Después de seleccionar el nombre de la ubicación, accederá a la pantalla de la **Aplicación Hospital Emergency Response** donde puede seleccionar un hospital, región o instalación diferente.

## <a name="view-the-mobile-app-in-your-language"></a>Ver la aplicación móvil en su idioma

[!include[cc-lang](includes/cc-lang.md)]

Puede ver la aplicación móvil de respuesta a emergencias para hospitales en uno de los idiomas admitidos en su dispositivo móvil configurando el idioma predeterminado de su dispositivo móvil (Apple o Android) en un idioma compatible. Consulte la documentación de ayuda para su dispositivo móvil respectivo sobre cómo cambiar el idioma predeterminado para su dispositivo.

Si está utilizando las aplicaciones móviles en un navegador en su equipo, seleccione el idioma predeterminado de su navegador para un idioma admitido para la aplicación móvil de respuesta a emergencia para hospitales. Para más información, vaya a [Usar Microsoft Edge en otro idioma](https://support.microsoft.com/help/4532129).

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para notificar un problema con la aplicación móvil de respuesta a emergencia para hospitales, visite <https://aka.ms/emergency-response-issues>.

- Para ofrecer comentarios sobre la aplicación móvil de respuesta a emergencia para hospitales, visite <https://aka.ms/emergency-response-feedback>.
