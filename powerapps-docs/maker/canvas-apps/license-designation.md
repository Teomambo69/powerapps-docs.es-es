---
title: Designación de licencia para una aplicación | Microsoft Docs
description: Explica cómo comprobar la designación de la licencia de la aplicación seleccionada.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/24/2020
ms.author: alaug
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 495325949776b066ed30d629fb031730e4463179
ms.sourcegitcommit: be9b8c0f5c7c7e9992e93fa0d03e961b4ac7e3ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2020
ms.locfileid: "80375002"
---
# <a name="how-to-check-license-designation-for-an-app"></a>Comprobación de la designación de la licencia para una aplicación

A partir del 2019 de octubre, se reclasifican varios conectores de estándar a Premium.

[Preguntas más frecuentes sobre licencias de Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) describe los conectores reclasificados. A las aplicaciones que usan estos conectores antes de la reclasificación se les ha concedido un período de tiempo extendido que permite a los usuarios sin una licencia Premium acceder a estas aplicaciones.

En la tabla siguiente se describen las designaciones y la licencia que debe tener un usuario final para tener acceso a una aplicación.

| **Repetición** | **Definición**
|-|-|
| Estándar | Una aplicación que solo usa conectores estándar. Un usuario final debe tener un plan de Power apps para Office 365, por plan de aplicación o un plan por usuario para acceder a esta aplicación.
| Extendido | Una aplicación permitió usar conectores promocionados a Premium el 1 de octubre de 2019. Un usuario final debe tener un plan de Power apps para Office 365, por plan de aplicación o por plan de usuario.  [Preguntas más frecuentes sobre licencias de Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) describe qué conectores se promovieron a Premium el 1 de octubre de 2019.
| Premium | Una aplicación que usa al menos un conector Premium, un conector personalizado o una puerta de enlace local. Un usuario final debe tener un plan por aplicación o un plan de usuario para tener acceso a él.

## <a name="check-app-license-designation-from-app-settings"></a>Comprobar la designación de la licencia de la aplicación en la configuración de la aplicación

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **aplicaciones** en el lado izquierdo.

1. Seleccione una aplicación de la lista de aplicaciones. Puede usar la opción de **configuración** de Top o, usar los **comandos más** ( **...** ) y, después, la **configuración** del menú desplegable:

    ![Opción de configuración](media/license-designation/app-settings.png)

1. Seleccione **configuración** para ver la información de designación de licencia:

    ![Designación de licencia de la configuración](media/license-designation/settings-license-designation.png)

## <a name="check-app-license-designation-from-app-details"></a>Comprobar la designación de la licencia de la aplicación en detalles de la aplicación

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **aplicaciones** en el lado izquierdo.

1. Seleccione una aplicación de la lista de aplicaciones. Puede usar la opción de **detalles** de la parte superior o, usar los **comandos más** ( **...** ) y, después, los **detalles** del menú desplegable:

    ![Detalles de la aplicación](media/license-designation/app-details.png)

1. Seleccionar **detalles**:

    ![Designación de la aplicación en detalles](media/license-designation/app-details-page.png)

## <a name="pass-assignment"></a>Asignación de paso

Para obtener información sobre la asignación de Pass, lea [Power apps por planes de aplicaciones](https://docs.microsoft.com/power-platform/admin/about-powerapps-perapp#step-three-set-up-apps-to-use-per-app-plans).

## <a name="next-steps"></a>Pasos siguientes

- [Preguntas más frecuentes sobre licencias de Power apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq)

### <a name="see-also"></a>Vea también

- [Editar una aplicación](edit-app.md)
- [Delete an app](delete-app.md) (Eliminar una aplicación)
