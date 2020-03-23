---
title: Tutorial para la transición de su aplicación de cliente web heredada a la interfaz unificada | MicrosoftDocs
description: Aprenda a realizar la transición de la aplicación del cliente web heredado a la interfaz unificada
ms.custom: ''
ms.date: 09/11/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 14c4c18c-927c-4ea2-ba66-0531285a99a7
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8db8442c7cb5a53d1c836f814e6d7b1d5e58a84a
ms.sourcegitcommit: 4f2e9e8f9bd3204ca9eee9e2a46f797c957c55ec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "3029694"
---
# <a name="quick-start-for-transitioning-your-legacy-web-client-application-to-unified-interface"></a>Tutorial para la transición de su aplicación de cliente web heredada a la interfaz unificada

El marco de la interfaz unificada también usa principios de diseño web dinámicos para ofrecer una experiencia de visualización e interacción óptima para cualquier tamaño de pantalla, dispositivo u orientación. Este tema de inicio rápido explica cómo realizar la transición de su aplicación de cliente web heredada a la interfaz unificada con un nuevo entorno de no producción. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3JwWU]

Para usar un entorno de no producción existente para realizar la transición de su aplicación de cliente web, consulte [Inicio rápido para utilizar un entorno existente para validar la aplicación de cliente web heredada con la interfaz unificada](transition-web-app-existing.md). 
## <a name="prerequisites"></a>Requisitos previos
- Una aplicación del cliente web heredada. 
- Aunque no es necesario, se recomienda un entorno de no producción para probar la aplicación y asegurarse de que no afecta a la implementación o ciclos de desarrollo actuales. Más información: [Administrar instancias de espacio aislado](/dynamics365/admin/manage-sandbox-instances)

## <a name="prepare-the-environment"></a>Preparar el entorno
Primero, seleccione un entorno de no producción y habilite el modo **Usar solo la interfaz unificada**, que usará la interfaz unificada para todas las aplicaciones basadas en modelo del entorno. Esto también incluye cualquier módulo de aplicación de Dynamics 365 configurado originalmente para el cliente web heredado.

1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Entorno** y luego seleccione un entorno de espacio aislado. 

2. Seleccione **Configuración** > **Comportamiento** y después active **Usar solo la interfaz unificada**.

   > [!div class="mx-imgBorder"] 
   > ![Ajuste Usar solo la interfaz unificada](media/use-unified-interface-only-pac.png)


> [!NOTE]
> Si necesita devolver el entorno a su estado anterior, puede alternar el ajuste de la interfaz unificada para revertir a la interfaz original. Más información: [Habilitar solo la interfaz unificada](/dynamics365/customer-engagement/admin/enable-unified-interface-only)

## <a name="run-and-validate-your-application-in-the-unified-interface"></a>Ejecute y valide la aplicación en la interfaz unificada
Ejecute sus aplicaciones que eran originalmente aplicaciones del cliente web. Tenga en cuenta que, una vez que se active **Usar solo la interfaz unificada**, todas las aplicaciones disponibles en el entorno usan la interfaz unificada incluso si la aplicación estaba configurada originalmente para el cliente web.

Para ejecutar la aplicación, inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Aplicaciones** y luego seleccione la aplicación que desea ejecutar. Como alternativa, puede ir directamente a la página **Mis aplicaciones**, como *https://contoso.crm.dynamics.com/apps/*.

### <a name="validate-your-app-processes-and-customizations"></a>Valide la aplicación, procesos, y personalizaciones 
Se recomienda probar todos los casos de uso. Puede empezar con los casos de uso más críticos o agruparlos en patrones lógicos de diseño. Puesto que la interfaz unificada se basa en diseño dinámico, se recomienda realizar pruebas con distintos dispositivos que tienen diferentes resoluciones de pantalla. Al probar la aplicación podrá comprobar que las personalizaciones son compatibles con la interfaz unificada y si existen características que necesiten un rediseño o les falta funcionalidad. Cree un plan para revisar estos elementos y envíe sus preguntas y sus comentarios al foro de la comunidad. 

> [!IMPORTANT]
> La versión actual de Common Data Service y aplicaciones basadas en modelo en Dynamics 365 incluye aún varias características obsoletas. Debe comprobar si la aplicación tiene características obsoletas y reemplazarlas según sea necesario con nuevas capacidades. Más información: [Próximos cambios importantes (funciones obsoletas)](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

### <a name="dynamics-365-apps"></a>Aplicación de Dynamics 365
Si usa aplicaciones de Dynamics 365 Field Service o Dynamics 365 Project Service Automation y desea probar la interfaz unificada, debe configurar un nuevo entorno de espacio aislado y realizar una copia del entorno de producción para actualizar a Field Service versión más reciente y Project Service Automation versión antes de validar estas aplicaciones en la interfaz unificada. Para ello, siga estos pasos:

1. Cree un nuevo entorno de espacio aislado desde el [Power Platform Centro de administración](https://admin.powerplatform.microsoft.com/environments) o el [Centro de administración de Dynamics 365](https://port.crm.dynamics.com/). Más información: [Agregar una instancia a la suscripción](/dynamics365/customer-engagement/admin/add-instance-subscription)

2. Copie el entorno de producción que tiene las aplicaciones de Dynamics 365 Field Service o Dynamics 365 Project Service Automation al nuevo entorno de espacio aislado. Para ello, en el Centro de administración de Power Platform abra el entorno de producción y, a continuación seleccione **Copiar**.

    > [!div class="mx-imgBorder"] 
    > ![Copiar entorno](media/ppac-copy-environment.png "Copiar entorno")

3. En la página **Copiar entorno**, seleccione **Todo**, seleccione el nuevo entorno de espacio aislado de la lista **Seleccionar entorno para sobrescribir** y después seleccione **Copiar**. 

    > [!div class="mx-imgBorder"] 
    > ![Sobrescribir entorno](media/ppac-copy-overwrite.png "Sobrescribir entorno")

4. Se abre el cuadro de diálogo **Sobrescribir entorno**. Asegúrese de que ha seleccionado el entorno correcto y de que tiene las opciones correspondientes seleccionadas y, a continuación seleccione **Confirmar**. 

5. Cuando la copia se realiza correctamente, aparece un aviso de confirmación. 

6. En la barra de menú, seleccione **Administrar soluciones** para abrir el área **Soluciones**. 

    > [!div class="mx-imgBorder"] 
    > ![Administrar soluciones](media/ppac-manage-solutions.png "Administrar soluciones")

    > [!IMPORTANT]
    > Si habilita **modo de administración**, debe deshabilitarlo para poder ver el área **Soluciones**. Más información: [Modo de administración](/power-platform/admin/sandbox-environments#administration-mode)

7. Busque la solución de Field Service o Project Service Automation y selecciónela. La opción **Actualizar** debe estar disponible. Selecciónela para actualizar la solución. 

    > [!div class="mx-imgBorder"] 
    > ![Actualizar solución](media/ppac-upgrade-solution.png "Actualizar solución")
    
> [!NOTE]
> Las últimas versiones de Field Service y Project Service Automation en la interfaz unificada están disponibles de forma predeterminada para las instancias recién creadas. Si desea actualizar un entorno existente con versiones instaladas anteriormente, debe solicitar la actualización poniéndose en contacto con [Soporte al cliente de Microsoft](https://go.microsoft.com/fwlink/?LinkId=853505). 

Más información: [últimas versiones de Dynamics 365 for Field Service](/dynamics365/customer-engagement/field-service/version-history#latest-versions) y [página principal de actualización de Dynamics 365 for Project Service Automation](/dynamics365/customer-engagement/project-service/upgrade-psa-home-page)

## <a name="next-steps"></a>Pasos siguientes
En función de sus hallazgos, el equipo o el asociado de implementación puede estimar la cantidad de esfuerzo necesario para realizar la transición de su aplicación en la interfaz unificada y también identificar mejoras potenciales en la facilidad de uso. Con muchas características y capacidades nuevas disponibles en la interfaz unificada hay oportunidad para aumentar el valor de los usuarios de la aplicación. 

La transición a la interfaz unificada es una gran oportunidad para crear una interfaz de usuario moderna y revisar los procesos existentes para comprobar que siguen siendo válidos o si necesitan mejoras. Este es también un buen momento para considerar si su aplicación refleja los requisitos empresariales y si la aplicación existente se puede extender a diversas aplicaciones para los distintos equipos y roles.
Más información: [Diseñar aplicaciones basadas en modelo mediante el diseñador de aplicaciones](design-custom-business-apps-using-app-designer.md)  

### <a name="see-also"></a>Vea también
<!-- Unified Interface transition community (link tbd) <br />  -->
[Cuaderno de estrategias de la interfaz unificada](unified-interface-playbook.md) <br />
[Aproximación a la experiencia de usuario y transición a la interfaz unificada](approaching-unified-interface.md) <br />
[Acerca de la interfaz unificada](/dynamics365/customer-engagement/admin/about-unified-interface) <br />
[¿Qué son las aplicaciones controladas por modelos en Power Apps?](model-driven-app-overview.md) <br />
[Actualizar aplicaciones a la interfaz unificada](/dynamics365/customer-engagement/admin/update-apps-to-unified-interface) <br />
[Configurar paneles de experiencia interactiva de aplicaciones controladas por modelos](configure-interactive-experience-dashboards.md) <br />
[Usar controles personalizados para visualizaciones de datos de aplicaciones controladas por modelos](use-custom-controls-data-visualizations.md) <br />
[Información general sobre Power Apps component framework](/powerapps/developer/component-framework/overview) <br />
[Interfaz unificada para todos](/power-platform-release-plan/2019wave2/microsoft-powerapps/unified-interface-app-everybody)

