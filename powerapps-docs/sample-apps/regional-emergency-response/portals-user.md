---
title: Usar el portal de supervisión y respuesta ante emergencias de la administración pública regional | Microsoft Docs
description: Aprenda a usar el portal de supervisión y respuesta ante emergencias de la administración pública regional como trabajador sanitario.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/04/2020
ms.author: tapanm
ms.reviewer: tapanm
searchScope:
- PowerApps
ms.openlocfilehash: 115cf6a5c1c622374de42230e07e09462cc6de41
ms.sourcegitcommit: c424a17b9c658f4571b5ea26ab6fc8a486051d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341772"
---
# <a name="use-the-regional-governmentemergency-response-and-monitoring-portal"></a>Usar el portal de supervisión y respuesta ante emergencias del gobierno regional

El personal del hospital tiene el desafío de cumplir con un aumento en el número de pacientes mientras gestiona la cadena de suministro durante una emergencia. Mediante el uso del portal de supervisión y respuesta ante emergencias de la administración pública regional, los trabajadores de primera línea pueden ver y agregar rápidamente datos relativos a respiradores, personal, altas pendientes y pacientes afectados de COVID-19.

## <a name="portal-at-a-glance"></a>Vista rápida del portal

Navegue hasta el portal de Power Apps para trabajar con personal, equipos, suministros, pacientes y otras áreas. La siguiente sección le guía a través de lo que está accesible y lo puede enviar o actualizar como usuario de atención médica del portal.

![Vista rápida del portal ](media/portal-user-at-glance.png)

Puede usar los últimos dispositivos móviles y navegadores web cuando usa el portal de supervisión y respuesta ante emergencias de la administración pública regional, excepto Apple iPad.

[!include[cc-getting-started](includes/cc-getting-started.md)]

[!include[cc-manage-user-profile](includes/cc-manage-user-profile.md)]

## <a name="portal-components"></a>Componentes del portal

El portal de supervisión y respuesta ante emergencias de la administración pública regional consta de los siguientes componentes:

- **Capacidad de camas**  
  Recopile detalles sobre autorizaciones de camas, capacidad, gravedad, camas con personal y datos de aumento.

- **Personal**  
  Recopile el estado de los enfermeros por ubicación en esa instalación.

- **Equipamiento**  
  Recopile detalles del equipo, como ventiladores y dispositivos NIPPV.

- **Suministros**  
  Recopile suministros clave para controlar, administrar y predecir las existencias del inventario de forma más eficaz. 

- **Estadísticas de COVID-19**  
  Obtenga información sobre cuántos pacientes están bajo investigación de COVID-19 y cuántos dieron positivo.


## <a name="bed-capacity"></a>Capacidad de camas

Seleccione **Capacidad de cama** para actualizar la información del paciente, las camas y la capacidad de personal para la ubicación seleccionada:

![Capacidad de camas](media/portal-user-bed-capacity.png)

### <a name="options-and-description"></a>Opciones y descripción

| **Nombre de opción**                                               | **Descripción**                                                                       |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------|
| Número de camas autorizadas actualmente en uso  | Número de camas autorizadas actualmente en uso en este centro.                            |
| Número de camas de UCI (sala SAITA) actualmente en uso               | Número de camas de UCI en las salas de aislamiento de infección aérea (SAITA) actualmente en uso en estas instalaciones.                                      |
| Número de camas de UCI (sala no SAITA) actualmente en uso           | Número de camas de UCI (no SAITA) actualmente en uso en este centro.                                  |
| Número de camas de cuidados agudos (sala SAITA) actualmente en uso        | Número de camas de cuidados intensivos (SAITA) actualmente en uso en este centro.                               |
| Número de camas de cuidados agudos (sala no SAITA) actualmente en uso    | Número de camas de cuidados intensivos (no SAITA) actualmente en uso en este centro.                           |
| Número de camas de UCI pediátricas (sala SAITA) actualmente en uso               | Número de camas de UCI pediátrica (SAITA) actualmente en uso en este centro.                                      |
| Número de camas de UCI pediátricas (sala no SAITA) actualmente en uso           | Número de camas de UCI pediátrica (no SAITA) actualmente en uso en este centro.                                  |
| Número de camas de cuidados agudos pediátricos (sala SAITA) actualmente en uso        | Número de camas de cuidados intensivos pediátricos (SAITA) actualmente en uso en este centro.                               |
| Número de camas de cuidados agudos pediátricos (sala no SAITA) actualmente en uso    | Número de camas de cuidados intensivos pediátricos (no SAITA) actualmente en uso en este centro.                           |
| ¿Su centro dispone de personal para toda su capacidad de camas autorizadas?    | Yes/No. Si la respuesta es No, puede seleccionar una o más razones entre las siguientes: <br> - Personal <br> - Espacio <br> - EPI <br> - Equipamiento <br> - Volumen bajo de pacientes  |
| ¿Puede aumentar el número de camas por encima de las autorizadas?              | Yes/No. Si la respuesta es No, puede seleccionar una o más razones entre las siguientes: <br> - Personal <br> - Espacio <br> - EPI <br> - Equipamiento <br> - Volumen bajo de pacientes  |
| Número de camas suplementarias actualmente en uso                         | Número de camas suplementarias actualmente en uso en este centro. 
| Número de salas para fallecidos actualmente en uso                                            | Número de salas para fallecidos actualmente en uso en este centro. <br> **Nota**: Solo visible si la *Capacidad mortuoria total* del centro es al menos 1.

### <a name="previous-submissions"></a>Envíos anteriores

Cuando abre **Capacidad de camas** o cualquier otro componente como **Personal**, **Equipo**, **Suministros**o **Estadísticas de COVID-19**, puede ver la fecha y hora del último envío y el remitente.

Si selecciona un campo individual, como *Número de camas autorizadas actualmente en uso* para **Capacidad de camas**, también puede ver el valor anterior enviado para el campo:

![Valor anterior](media/previous-submissions.png)

## <a name="staff"></a>Personal

Envíe detalles específicos del personal, como el ausentismo, y detalles relacionados con las enfermeras registradas, como quienes están *de turno* y las que son *actualmente necesarias* con el formulario de **Personal**:

![Detalles del personal](media/portal-user-staff-details.png)

### <a name="options-and-description"></a>Opciones y descripción

| **Nombre de opción**                               | **Descripción**                                                                |
|-----------------------------------------------|--------------------------------------------------------------------------------|
| Porcentaje de personal sanitario esencial ausente | Absentismo de personal sanitario esencial en formato de porcentaje.                  |
| Número de ED de servicio actualmente                                    | Número de enfermeras registradas actualmente en servicio para el centro seleccionado.                 |
| Número de ED necesarios actualmente                                  | Número de enfermeras necesarias actualmente para el centro seleccionado. |

## <a name="equipment"></a>Equipamiento

Envíe los detalles del equipo, como ventiladores y dispositivos NIPPV:

![Detalles del equipamiento](media/portal-user-equipment-details.png)

### <a name="options-and-description"></a>Opciones y descripción

| **Nombre de opción** | **Descripción**                 |
|-----------------|---------------------------------|
| Ventiladores     | Número de respiradores en uso.   |
| VPPNI (Ventilación con presión positiva no invasiva)          | Número de dispositivos VPPNI (respiradores mecánicos con presión positiva no invasiva) en uso. |

## <a name="supplies"></a>Suministros

Envíe el inventario de suministros en stock y usado en las últimas 24 horas:

![Detalles de suministros](media/portal-user-supplies-details.png)

### <a name="options-and-description"></a>Opciones y descripción

La lista de elementos de la aplicación de suministros puede ser diferente según los requisitos de su organización. Consulte los recursos de su organización para obtener descripciones de los nombres de los suministros.

> [!NOTE]
> Los valores de los artículos del inventario de suministros deben estar en formato numérico. El número de suministro es para un **componente individual**. Por ejemplo, las máscaras N-95 se cuentan por máscara individual, en lugar de contar el número de cuadros que contienen máscaras.

## <a name="covid-19-stats"></a>Estadísticas de COVID-19

Envíe los detalles específicos de COVID-19 mediante el formulario de **estadísticas de COVID-19**.

![Estadísticas](media/portal-user-stats.png)

### <a name="options-and-description"></a>Opciones y descripción

| **Nombre de opción**                                                   | **Descripción**                                                    |
|-------------------------------------------------------------------|--------------------------------------------------------------------|
| Número de pacientes bajo investigación (PBI)                     | Número de pacientes bajo investigación en este centro.                            |
| Número de pacientes con COVID-19 confirmado                        | Número de pacientes con COVID-19 confirmado en este centro.                        |
| Número de pacientes intubados                                      | Número de pacientes intubados en este centro.                                      |
| Número de pacientes con COVID-19 dados de alta en las 24 horas anteriores | Número de pacientes con COVID-19 dados de alta en las 24 horas anteriores en este centro. |

## <a name="general-portal-options"></a>Opciones generales del portal

[!include[cc-general-options](includes/cc-general-options.md)]

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-issues>.

- Para comentar la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-feedback>.
