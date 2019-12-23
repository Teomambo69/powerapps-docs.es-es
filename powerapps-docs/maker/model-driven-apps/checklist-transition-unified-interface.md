---
title: 'Lista de comprobación: Transición a la interfaz unificada | MicrosoftDocs'
description: Lista de comprobación para asegurar que se ha preparado para la transición a la interfaz unificada.
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20a64e12abc70e8c1b636ab5412e2a951b5ad612
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869235"
---
# <a name="checklist-unified-interface-transition"></a>Lista de comprobación: Transición a la interfaz unificada

Siga los pasos de este artículo para asegurar de que se ha preparado para la transición a la interfaz unificada. La preparación para la transición a la interfaz unificada dependerá de desea compatibilidad básica o rediseño para aprovechar al máximo nuevas capacidades. Para obtener información más detallada, consulte [Cuaderno de estrategias de la interfaz unificada](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook) y [notas del producto de la experiencia de usuario](https://docs.microsoft.com/powerapps/maker/model-driven-apps/approaching-unified-interface).

Las instrucciones se aplican a las siguientes aplicaciones basadas en modelo en Dynamics 365:

- Dynamics 365 Sales

- Dynamics 365 Customer Service

- Dynamics 365 Field Service

- Dynamics 365 Project Service Automation

## <a name="run-the-power-apps-solution-checker-on-your-solutions"></a>Ejecute al comprobador de soluciones de Power Apps en las soluciones.

El [comprobador de soluciones de Power Apps](https://docs.microsoft.com/powerapps/maker/common-data-service/use-powerapps-checker) realiza una completa verificación de análisis estático de sus soluciones con un conjunto de reglas de prácticas recomendadas para identificar rápidamente patrones problemáticos. Cuando la comprobación se completa, usted recibe un informe detallado que lista los problemas identificados, los componentes y el código afectados y vínculos a la documentación que describe cómo solucionar cada problema.

El comprobador de soluciones analiza estos componentes de la solución:

-   Complementos Common Data Service

-   Actividades de flujo de trabajo personalizadas Common Data Service

-   Recursos web de Common Data Service (HTML y JavaScript)

-   Configuraciones de Common Data Service, como pasos de mensajes de SDK

**Para considerar** 

-   Los posibles problemas detectados por el comprobador de soluciones pueden no aplicarse exclusivamente a la interfaz unificada, tenga en cuenta en qué afectará a transición al revisar los resultados.

-   Como en cualquier revisión de código automatizada, algunos problemas pueden ser falsas alarmas y no significan que su aplicación no se ejecutará en interfaz unificada.

-   La lógica ejecutada en el lado servidor, como complementos, actividades personalizadas de flujo de trabajo, y la configuración de los pasos de mensajes del SDK no debería afectar a la interfaz de usuario por tanto no debería afectar a la transición a la interfaz unificada.

-   Aunque todos los problemas no estén asociados directamente con la interfaz unificada, se recomienda dedicar tiempo a revisarlos para mejorar el estado general de la aplicación.

## <a name="check-third-party-solutions-compatibility-with-unified-interface"></a>Comprobar la compatibilidad de soluciones de terceros con la interfaz unificada


Antes de realizar la transición a la interfaz unificada, es importante asegurarse de que cualquier solución de terceros que se usa en su aplicación funcione en interfaz unificada.

-   Si ha instalado complementos ISV (fabricante independiente de software) a través, de [AppSource](https://appsource.microsoft.com) compruebe si las actualizaciones estén disponibles en el [Centro de administración de Power Platform](https://admin.powerplatform.microsoft.com) seleccionando **Entornos** > [environment_name] > **Administrar soluciones**.

-   Si usa soluciones de terceros que se proporcionaron fuera de AppSource, póngase en contacto con el proveedor (partner o ISV) para obtener una nueva versión que actualice las aplicaciones a la interfaz unificada.

> [!NOTE]
> Si no hay planes de que sus soluciones de terceros se actualicen a una versión compatible con la interfaz unificada, es importante identificar una ruta de acceso para reemplazar estas características con las capacidades nativas de la plataforma o soluciones alternativas compatibles.

## <a name="identify-replacements-for-deprecated-client-api-code-and-features"></a>Identificar sustituciones de código y características de la API cliente obsoleta

En función de las salidas del **Comprobador de soluciones de Power Apps** y la información contenida en [Próximos cambios importantes (funciones obsoletas)](https://docs.microsoft.com/power-platform/important-changes-coming) en API y características de clientes obsoletas, debe comprender bien las personalizaciones y características que deben corregirse o ser reemplazadas en el proyecto de la interfaz unificada.

Estas son algunas de las áreas más comunes que requieren atención:

-   **API de cliente**: Se documentan los métodos recomendados de sustitución [aquí](https://docs.microsoft.com/power-platform/important-changes-coming#some-client-apis-are-deprecated).

-   **Diálogos de proceso**: Las sustituciones recomendadas para diálogos se documentan [aquí](https://docs.microsoft.com/flow/replace-dialogs).

-   **Flujos de tareas**: Considere el uso de [Flujos de proceso de negocio](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-flow/business-process-immersive-experiences) para reemplazar los flujos de tarea.

-   **Programación de servicios**: Considere el uso de [Universal Resource Scheduling](https://docs.microsoft.com/dynamics365/common-scheduler/schedule-anything-with-universal-resource-scheduling) para reemplazar la programación de servicios heredada.

> [!NOTE]
> Puede que también considere reemplazar Dynamics 365 for Outlook (complemento COM) con el ligero [Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview).

## <a name="test-your-application-in-unified-interface"></a>Pruebe su aplicación en unificada interfaz

Una de las formas más fáciles de probar la aplicación en interfaz unificada es activar la opción [**Habilitar la interfaz unificada solo**](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) en una copia del entorno de producción. Una vez habilitada la interfaz unificada, deberá poder tener acceso a la aplicación mediante la aplicación **Dynamics 365 – personalizado** y probar los casos de uso relevantes al contexto.

### <a name="test-your-business-and-technical-scenarios"></a>Probar los escenarios de negocio y técnicos

Céntrese en lo que podría verse afectado:

-   **Procesos de negocio** como flujos de proceso de negocio, reglas de negocio

-   **Personalizaciones** como formularios, vistas, botones de la barra de comandos, recursos web, y gráficos

> [!TIP]
> Cuestione la experiencia del usuario al mismo tiempo que realiza estas pruebas iniciales: ¿resulta todos significativo y agrega valor? ¿Qué se debería quitar/mejorar/agregar? Por ejemplo, ¿es relevante la lista actual de vistas? ¿O se fuerzan a mis usuarios a crear sus propias vistas?

### <a name="identify-gaps"></a>Identificar lagunas

-   Cualquier regresión potencial que no detectó el comprobador de soluciones y actualizaciones de soluciones de terceros.

-   Puntos de dificultad de usuario que pueden llevar a optimizaciones (como nueva representación de formularios reorganizando secciones y pestañas) o formación específica.

-   Cualquier otra dependencia del cliente web heredado como el uso del complemento COM de Outlook heredado en vez del ligero Dynamics 365 App for Outlook.

## <a name="define-your-app-strategy-and-settings"></a>Definir estrategia y configuración de la aplicación

En lugar de usar la aplicación **Dynamics 365 – personalizada**, que no está optimizada para la interfaz unificada sino que más bien se ejecuta en modo de compatibilidad, se recomienda aprovechar las aplicaciones de primera parte de Microsoft o crear sus propias aplicaciones.

Las aplicaciones de primera parte de Microsoft Dynamics 365 que ya se han optimizado para la interfaz unificada son las siguientes:

-   Centro de ventas Dynamics 365

-   Centro de servicio al cliente de Dynamics 365

-   Dynamics 365 Marketing

-   Dynamics 365 Field Service (versión 8.x y posterior)

-   Dynamics 365 Project Service Automation (versión 3.x y posterior)

### <a name="what-are-model-driven-apps"></a>¿Qué son las aplicaciones basadas en modelo?

Las **aplicaciones basadas en modelo** son un tipo de aplicación que puede crear mediante Power Apps y que le ayuda a proporcionar experiencia adaptada a los usuarios en función del rol en la organización. Por ejemplo, un comercial puede tener una experiencia completamente diferente que un representante de servicio al cliente con distintas aplicaciones basadas en modelo aunque usan datos del mismo entorno. Se pueden crear varias aplicaciones basadas en modelo en un entorno de Common Data Service. Más información: [¿Qué son las aplicaciones basadas en modelo?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

Las aplicaciones de primera parte de Dynamics 365 que aparecen en la lista anterior son ejemplos de aplicaciones basadas en modelo.

### <a name="how-to-define-your-app-strategy"></a>¿Cómo definir la estrategia de la aplicación?

Debe plantearse las preguntas siguientes:

1.  ¿Puede que dividir usuarios en varios grupos con procesos de negocio específicos?

2.  ¿Estos grupos tienen distintos requisitos de lo que deben ver y hacer?

3.  ¿Tiene dificultades en tener diferentes experiencias de usuario sin usar aplicaciones?

Si ha respondido ”Sí” a estas preguntas, considere tener varias aplicaciones.

Esta es la oportunidad de repensar la experiencia en el contexto de los procesos de negocio para cada grupo o rol.

### <a name="out-of-the-box-apps-for-example-sales-hub-or-customized-apps"></a>¿Aplicaciones predefinidas (por ejemplo, Centro de ventas) o aplicaciones personalizadas?

-   Depende de lo adaptada que desea que sea la experiencia.

-   Si tiene pocas personalizaciones o desea beneficiarse de actualizaciones de aplicaciones de primera parte, considere el uso de aplicaciones nativas.

-   Si desea más control sobre la experiencia y actualizaciones de aplicaciones y personalizaciones estándar, cree su propia aplicación.

### <a name="once-you-have-defined-your-app-strategy-what-should-be-the-next-steps"></a>Una vez que haya definido su estrategia de aplicaciones, ¿cuáles deberían ser los siguientes pasos?

1.  Personalice las aplicaciones de destino e incluya sólo lo que necesitarán los usuarios. Menos es mejor. Reduzca el exceso para permitir a los usuarios trabajar eficazmente.

2.  Disocie los roles de seguridad de aplicaciones no usadas.

## <a name="review-your-apps-settings-and-user-experience-fundamentals"></a>Revise la configuración de aplicaciones y los conceptos básicos de la experiencia de usuario

### <a name="app-settings"></a>Configuración de la aplicación

-   Incluya todas las entidades requeridas en la aplicación, incluso si no están en el mapa del sitio.  
    
-   Proporcione el privilegio **Lectura** para **Aplicación basada en modelo** en la pestaña **Personalización** del cuadro **Rol de seguridad**.

-   Habilite el modo **Solo interfaz unificada** si los usuarios no necesitan usar el cliente web heredado. Puede seguir teniendo acceso a características de administración seleccionando **Configuración** > **Configuración avanzada**.

-   Crear una dirección URL de aplicaciones más simple Por ejemplo: https://\*.crm.dynamics.com/apps/MyApp*

-   Intente limitar el número de aplicaciones a las que un usuario tiene acceso.  
    
    > [!TIP]
    > Cuando **Usar interfaz unificada solo** se ajusta como **Sí** y cuando los usuarios solo tienen acceso a una aplicación, se les redirige automáticamente a la aplicación cuando tienen acceso a la dirección URL de la raíz (https://\*.crm.dynamics.com)*

### <a name="optimize-navigation-sitemap"></a>Optimizar navegación (mapa del sitio)

-   Defina un **área** principal con las **subáreas** más usadas (panel, entidades, etc.) organizadas en **grupos**

-   Cree una o varias áreas adicionales para las características menos usadas (configuración, valores, etc.). La idea es ayudar a los usuarios centrarse solo en lo que es importante para realizar su trabajo.

### <a name="update-icons"></a>Actualizar iconos

-   La transición a la interfaz unificada es una buena posibilidad para actualizar iconos.

-   Recomendamos el formato **SVG**, ya que se representa bien independientemente de la resolución de pantalla.

    > [!TIP]
    > Ejemplo de formato de icono SVG:  
    > Ancho y alto: 16px; Relleno: 0px; Fondo: transparente; Color de icono: \#FF000000  
    Para evitar problemas de representación, abra el archivo SVG con un editor (por ejemplo, Bloc de notas) y quite el relleno="\#000000"

## <a name="enrich-your-app-with-unified-interface-exclusive-features"></a>Enriquezca la aplicación con las características exclusivas de la interfaz unificada

-   Cree una **Página de bienvenida** que los usuarios vean a cuando tienen acceso a la aplicación. Ésta es una buena oportunidad de guiar a los usuarios en los primeros pasos.

-   Utilice **controles personalizados** existentes para mejorar la utilidad de la mayoría de los tipos de campos, especialmente en el móvil. Por ejemplo, reemplace una calificación de campo de 0 a 5 con estrellas, sustituya una vista de citas con una vista de calendario, sustituya una vista de subcuadrícula con formularios de tarjeta.

-   Aproveche **Paneles de referencia** en los formularios para empaquetar varias vistas, vistas rápidas y la característica de búsqueda de KB en un solo lugar.

-   Aproveche el [Power Apps Component Framework](https://docs.microsoft.com/powerapps/developer/component-framework/overview) para agregar aún más controles personalizados. Puede obtener algunos de la comunidad o de partners e ISV.

-   Inserte [aplicaciones de lienzo](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started) en los formularios para ampliar fácilmente su aplicación. La extensión con poco o ningún código de su aplicación sin necesidad de desarrollar recursos web HTML/JS personalizados.

-   Inserte informes y ventanas de **Power BI** en formularios: consolide datos a través de varios sistemas en una vista única.

-   Considere aprovechar **Paneles interactivos** para configurar un área de trabajo integral que permita el filtrado global a través de los componentes del panel.

-   Configure **Tareas guiadas y paneles de ayuda personalizados** para que los usuarios obtengan rápidamente ayuda e instrucciones.

## <a name="conduct-user-acceptance-testing"></a>Realice pruebas de aceptación de usuario

Es muy importante que sus aplicaciones, escenarios empresariales, y escenarios técnicas sean probados por los usuarios profesionales en interfaz unificada en condiciones que sean similares al entorno de producción. Estos usuarios pueden actuar como partidarios de la empresa para ayudar a escalar conocimiento a través del negocio.

La prueba ayudará a identificar los elementos restantes que se deben abordar antes de realizar la transición de todos los usuarios a la interfaz unificada.

## <a name="update-user-training-materials"></a>Actualizar materiales de aprendizaje de usuarios

Lleve a cabo una revisión de los materiales de aprendizaje existentes y planificados para garantizar que tienen las últimas capturas de pantalla y reflejar los cambios que haya realizado en el flujo de usuario.

## <a name="check-your-transition-date"></a>Compruebe la fecha de transición

El 1 de octubre de 2020 [el cliente web heredado dejará de estar disponible](https://docs.microsoft.com/power-platform/important-changes-coming#legacy-web-client-is-deprecated).
Asegúrese de migrar por adelantado para asegurarse de que hay tiempo para posibles problemas que se deban abordar.
