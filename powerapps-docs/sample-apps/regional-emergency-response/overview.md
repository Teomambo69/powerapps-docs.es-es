---
title: Información general sobre la solución de supervisión y respuesta ante emergencias del gobierno regional para Power Platform | Microsoft Docs
description: Proporciona información general sobre la solución de supervisión y respuesta ante emergencias del gobierno regional para los gobiernos estatales y locales.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: e91dadf24010ebf1fcffbbe7000f3d622238abc5
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342039"
---
# <a name="regional-governmentemergency-response-and-monitoring---power-platform-solution-for-state-and-local-governments"></a>Supervisión y respuesta ante emergencias del gobierno regional: solución de Power Platform para los gobiernos estatales y locales.

La solución de supervisión y respuesta ante emergencias del gobierno regional proporciona un conjunto de capacidades que permite a los gobiernos estatales y locales recopilar y visualizar datos del sistema de salud de todas las organizaciones de padres y hospitales asociados en su red o región para establecer consciencia de la situación durante las respuestas de emergencia. Los datos incluyen información sobre camas disponibles, suministros, equipos, pacientes de la COVID-19 y personal.

Los principales componentes de la solución de supervisión y respuesta ante emergencias del gobierno regional son:

- **Aplicación web para administradores de organizaciones regionales**: use la aplicación para administrar los datos maestros de cada organización médica principal en el estado o región, donde cada organización médica principal tiene uno o más sistemas hospitalarios que notifican los datos a la organización médica regional. El administrador de la organización regional puede agregar y administrar usuarios administradores para cada organización matriz, a fin de que esta última pueda usar un portal web para notificar los datos para su organización médica.

- **Portal web para administradores y usuarios de la organización matriz**: los administradores de la organización matriz pueden usar el portal web para agregar y administrar rápidamente usuarios en su organización y, además, agregar y administrar datos maestros para sus sistemas hospitalarios, incluidas las regiones y las instalaciones. El portal web también lo utilizan los trabajadores sanitarios para ver, agregar y administrar rápidamente datos relacionados con la capacidad de camas, el personal, el equipo, los suministros y los pacientes de COVID-19.

- **Paneles de control para responsables de toma de decisiones sanitarias**: use paneles para ver rápidamente datos y métricas importantes que lo ayudarán a tomar decisiones de manera eficiente.
    - Los administradores de las organizaciones regionales pueden ver el panel en su inquilino de Power BI.
    - Los usuarios de la organización principal pueden ver el panel en el portal web.

## <a name="demo-quick-overview"></a>Demostración: vista general rápida

Vea un resumen de la solución.

<br/>

> [!VIDEO https://www.youtube.com/embed/4WaniuC7pWs]

## <a name="licensing-requirements"></a>Requisitos de licencia

- Plan de Power Apps y capacidad del portal de Power Apps
- Licencia Premium o Pro de Power BI

Póngase en contacto con el representante de cuentas de Microsoft local para plantearle dudas relacionadas con las licencias según sus requisitos.

Vea también: 
- [Información general de licencias para Power Platform](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- [Power Apps para la Administración pública de Estados Unidos](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI para la Administración pública de Estados Unidos](https://docs.microsoft.com/power-bi/service-govus-overview)

## <a name="start-here"></a>Empiece aquí

|Tarea | Público objetivo|Vea|
|--|--|--|
|Descargar e implementar la solución de ejemplo y configurar los usuarios y la seguridad|Administración de TI de la organización regional|[Implementar la solución de supervisión y respuesta de emergencia de la administración pública regional](deploy.md)|
|Actualizar la solución de ejemplo (para organizaciones con una instalación de la solución)|Administración de TI de la organización regional|[Actualizar la solución Supervisión y respuesta ante emergencias del gobierno regional](upgrade.md)|
|Usar la aplicación de administración para configurar datos maestros, crear y administrar usuarios del portal y ver el panel|Administración empresarial de la organización regional|[Uso de la aplicación y panel de administración](configure.md)|
|Use el portal para agregar o administrar usuarios de portales para sus hospitales, configurar y administrar datos maestros para sus hospitales y ver el panel de control para obtener información y métricas.|Administración empresarial de la organización principal|[Administrar el portal de supervisión y respuesta ante emergencias del gobierno regional](portals-admin-reporting.md)|
|Use el portal para ver y agregar rápidamente datos de capacidad de camas, personal, equipo, suministros y pacientes de COVID-19.|Trabajadores sanitarios|[Usar el portal de supervisión y respuesta ante emergencias del gobierno regional](portals-user.md)|


## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-issues>.

- Para comentar la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-feedback>.


### <a name="disclaimer"></a>Declinación de responsabilidades

Esta aplicación es un ejemplo y se puede usar con Microsoft Power Platform únicamente para la difusión de información de referencia. Esta aplicación no está destinada ni está disponible para su uso como dispositivo médico, soporte clínico, herramienta de diagnóstico u otra tecnología destinada a ser utilizada en el diagnóstico, cura, mitigación, tratamiento o prevención de enfermedades u otras afecciones, y sin licencia o Microsoft concede el derecho de utilizar esta aplicación para tales fines. Esta aplicación no está diseñada como sustituto del asesoramiento, el diagnóstico, el tratamiento o el juicio médico, ni pretende serlo, y no debe usarse como tal. El cliente asume el único riesgo y responsabilidad por el uso de esta aplicación. Microsoft no garantiza que la aplicación o los materiales proporcionados en relación con la misma sean suficientes para fines médicos o cumplan con los requisitos médicos o de salud de cualquier persona. Los datos de ejemplo incluidos en esta aplicación son ficticios y se usan únicamente con fines ilustrativos. No se pretende establecer ni inferir ninguna asociación real.
