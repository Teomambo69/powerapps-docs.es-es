---
title: Inicio rápido para usar un entorno existente para validar la antigua aplicación de cliente web heredada con la interfaz unificada | MicrosoftDocs
description: Aprenda a planear y ejecutar la transición del cliente web heredado a la interfaz unificada
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
ms.assetid: ''
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 75175b34b158be75165c6bcdae5826060fb47f38
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884384"
---
# <a name="quick-start-for-using-an-existing-environment-to-validate-your-legacy-web-client-app-with-the-unified-interface"></a>Inicio rápido para usar un entorno existente para validar la antigua aplicación de cliente web heredada con la interfaz unificada
Este tema de inicio rápido muestra cómo usar un entorno existente para crear una aplicación de interfaz unificada basada en la configuración actual o la configuración predeterminada. Esto le permite explorar y comprobar la interfaz unificada mientras ejecuta aplicaciones de cliente web heredadas existentes paralelamente. Un usuario a continuación puede cambiar entre entornos para obtener una vista lado a lado. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3JzyI]

Para obtener instrucciones similares que le muestran cómo crear un nuevo entorno de espacio aislado para aislar la prueba y ver sólo la experiencia de la interfaz unificada, consulte [Inicio rápido para realizar la transición de la aplicación de cliente web heredada de aplicaciones de Dynamics 365 a la interfaz unificada](transition-web-app.md).

> [!IMPORTANT]
>  Para entornos con aplicaciones de Dynamics 365 Field Service o Dynamics 365 Project Service Automation, consulte [aplicaciones de Dynamics 365](transition-web-app.md#dynamics-365-apps).

## <a name="prerequisites"></a>Requisitos previos 
- Una aplicación de cliente web de Dynamics 365 Sales o Service heredada. 
- Aunque no es necesario, se recomienda el uso de un entorno de no producción para probar la aplicación. Más información: [Administrar instancias de espacio aislado](/dynamics365/customer-engagement/admin/manage-sandbox-instances) 

## <a name="overview"></a>Información general 
Este tema es para clientes existentes que usan aplicaciones de cliente web heredadas que necesitan planear y ejecutar la transición a la interfaz unificada. Para configurar un entorno paralelo, cree una nueva aplicación basada en la solución predeterminada tal como se encuentra hoy. Esto se puede hacer en el entorno actual de espacio aislado de desarrollo sin que se vea afectado el trabajo existente.

Después de completar los pasos de este artículo, los usuarios con el rol adecuado pueden ver la nueva aplicación en la lista de aplicaciones desplegable de Dynamics 365 o en la página principal de Dynamics 365 (https://home.dynamics.com).

![Lista de aplicaciones](media/app-list.png)

Una vez que complete las tareas descritas en este tema en el entorno de desarrollo mediante una solución, puede importar la solución en el entorno de prueba, lo que permite que un grupo mayor de usuarios profesionales prueben y comparen la aplicación en un entorno familiar. 

Siga los procesos de administración del ciclo de vida de la aplicación (ALM) y operaciones de desarrollo. Recomendamos realizar todos los pasos descritos en un contexto de la solución. Una vez que pruebe y valide la aplicación en el entorno de desarrollo, puede seguir probando la aplicación iniciándola como programa piloto para más usuarios, como en un entorno de producción. Si tiene aplicación basada en modelo y el mapa del sitio en una solución podrá exportar la aplicación desde el entorno donde creó esta nueva aplicación siguiendo los procesos existentes hacia delante en la canalización de entorno. 

## <a name="process-for-validating-your-legacy-web-client-app-in-an-existing-environment"></a>Proceso para validar la aplicación de cliente web heredada en un entorno existente
 
El proceso para validar la aplicación de cliente web heredada en un entorno existente incluye tres pasos:  

1.  Crear una solución nueva que se base en la solución predeterminada
2.  Crear una nueva aplicación basada en modelo 
3.  Configurar las propiedades de la aplicación  

Si ha cambiado recientemente el modo **Usar solo la interfaz unificada** a **Activado** en el entorno de desarrollo, siguiendo las instrucciones del tema [Inicio rápido para realizar la transición de la aplicación de cliente web heredada de aplicaciones de Dynamics 365 a la interfaz unificada](transition-web-app.md), deberá volver a **Desactivarlo** para poder ejecutar las antiguas del cliente web heredadas existentes.

### <a name="create-a-new-solution-thats-based-on-the-default-solution"></a>Crear una solución nueva que se base en la solución predeterminada
1. Iniciar sesión en el [portal de creador de Power Apps](https://make.powerapps.com).   
2. Seleccione la lista de entornos, seleccione el entorno que desee.  
3. En el panel de navegación izquierdo, seleccione **Soluciones**. 
4. En la barra de menú, seleccione **Nueva solución**. 
5. En el panel **Nueva solución**, especifique las propiedades siguientes: 
   - **Nombre**. Escriba un nombre para la solución. Por ejemplo, *Aplicación de la interfaz unificada*. 
   - **Editor**. Seleccione el editor que usa la organización. Asegúrese de seguir la gobernanza de personalización para las personalizaciones existentes. Esto asegurará que los nombres de esquema para la aplicación basada en modelo y su mapa del sitio son coherentes con los estándares existentes. 
   - **Versión**. Esto debe establecerse siguiendo los estándares y la gobernanza existentes para soluciones. 
6. Seleccione **Crear**.  
7. La nueva solución se crea en la lista de soluciones. Selecciónela para abrir la solución e ir a la siguiente sección. 

### <a name="create-a-new-model-driven-app-in-the-new-solution"></a>Crear una nueva aplicación basada en modelo en la nueva solución
En este paso creará una nueva aplicación que aproveche las personalizaciones existentes de modo que pueda experimentarlas en la interfaz unificada. Puede crear la aplicación en el contenedor de la nueva solución, que creó en la sección anterior.  

1. En la barra de menú seleccione **Nuevo**, señale a **Aplicación** y, a continuación seleccione **Aplicación basada en modelo**.
2. En la página **Crear una nueva aplicación**, especifique las propiedades siguientes: 
   - **Nombre**. Escriba el nombre que desee para la aplicación. Por ejemplo, *Nombre de la aplicación* + *Nuevo* o *Prueba de la interfaz unificada*. 
   - **Nombre único**. Este comienza con el prefijo de la solución y la versión simplificada del nombre de la aplicación que ha especificado. Puede realizar cambios o dejarlo tal como aparece.  
   - **Descripción**. Agregue una descripción para la aplicación, como *Con fines de prueba de la nueva interfaz unificada de nuestra solución*.  
3. Seleccione **Usar solución existente para crear la aplicación** y, a continuación seleccione **Siguiente**. 
4. En el lista **Seleccionar solución**, seleccione **Solución predeterminada**, en la lista **Seleccionar mapa del sitio**, seleccione **Mapa del sitio** y luego seleccione **Hecho**.  

   > [!div class="mx-imgBorder"] 
   > ![Seleccionar una solución existente](media/select-existing-solution.png "Seleccionar una solución existente")

5. El Diseñador de aplicaciones se abre, mostrando todos los componentes de la aplicación que estaban en la solución predeterminada. Seleccione **Publish**.  
6. Después de que el proceso de publicación se complete, seleccione **Reproducir**.  

Una nueva ventana se abre en el explorador con la nueva aplicación basada en modelo que contiene todas las entidades, mapa de sitio y personalizaciones de mapa del sitio que estaban en su aplicación predeterminada de Dynamics 365.  

> [!div class="mx-imgBorder"] 
> ![Nueva aplicación de la interfaz unificada](media/new-unified-interface-app.png "Nueva aplicación de la interfaz unificada")

Recuerde que cuando vuelva a la pestaña del explorador con el área **Soluciones** del portal del creador de Power Apps, la nueva aplicación basada en modelo y una extensión de cliente del mapa del sitio con nombre similar forman parte de la solución que ha creado.  

> [!div class="mx-imgBorder"] 
> ![Activos de solución](media/solution-assets.png "Activos de solución")

En este paso ha creado una nueva aplicación basada en modelo en una solución, que puede importar en sus entornos de prueba o de evaluación. Puede comenzar ahora a experimentar la nueva aplicación, pero antes de ello, en el siguiente paso configurará un par de ajustes para la nueva aplicación. Si hace esto podrá compartirla con otros usuarios.

### <a name="configure-app-properties"></a>Configurar las propiedades de la aplicación
Las tareas necesarias para configurar las propiedades de la aplicación basada en modelo son: 

- Asignar roles de usuario a la nueva aplicación para permitir a usuarios no administradores el acceso para usar la aplicación.  
- Personalizar una dirección URL descriptiva para que los usuarios pueden compartir, incluir en favoritos o recordar fácilmente un acceso directo a la nueva aplicación. 


1. Navegue a *dirección URL del entorno URL*/**aplicaciones**. La dirección URL será similar a esto: https://*YourEnvironment*.crm.dynamics.com/apps. Al hacerlo se abre una lista de todas las aplicaciones del entorno. 
2. Busque la nueva aplicación basada en modelo que ha creado.  
3. En la ventana de la aplicación, seleccione los puntos suspensivos y después seleccione **Administrar roles**.   

   > [!div class="mx-imgBorder"] 
   > ![Administrar roles](media/select-app-ellipsis.png "Administrar roles")

4. El área de roles disponibles aparece en el panel derecho. Seleccione los roles según sea necesario para dar acceso a los usuarios no administradores a la aplicación. 

    > [!IMPORTANT]
    > Asegúrese de que se concede a todos los usuarios al menos un rol de seguridad que contenga el acceso de **Lectura** al privilegio **Aplicación basada en modelo**. Este privilegio se puede encontrar en la pestaña Personalización del rol de seguridad. Los usuarios sin este privilegio reciben un error al abrir cualquier aplicación basada en modelo.  Observe que los roles de seguridad Administrador del sistema y Personalizador del sistema ya tienen este privilegio habilitado. 
 
   > [!div class="mx-imgBorder"] 
   > ![Privilegio de aplicación basada en modelo](media/model-driven-app-privilege.png "Privilegio de aplicación basada en modelo")

5. Opcionalmente, en el panel **Administrar roles** puede expandir el **Sufijo de la URL de aplicación** para personalizar la dirección URL descriptiva para la aplicación basada en modelo. Tenga en cuenta que puede especificar casi todo. Por ejemplo, escriba *nuevo* para que la vista previa muestre la dirección URL *https://YourEnvironment.crm.dynamics.com/apps/new*.   

   > [!div class="mx-imgBorder"] 
   > ![Sufijo de la URL de aplicación](media/app-url-suffix.png "Sufijo de la URL de aplicación")

   Esta se convierte en la dirección URL descriptiva para usar y compartir para que los usuarios puedan iniciar directamente en la experiencia de la interfaz unificada. Los usuarios pueden marcar como favorito este vínculo para su comodidad. 

6. Seleccione **Guardar**. 

Ahora los usuarios con el rol adecuado pueden ver la nueva aplicación en la lista de aplicaciones desplegable de Dynamics 365 o en la página principal de Dynamics 365 (https://home.dynamics.com). 
  
   ![Lista de aplicaciones](media/app-list.png "Lista de aplicaciones")

Puesto que el modo **Usar solo la interfaz unificada** está definida como **Activada**, cuando los usuarios naveguen a la dirección URL raíz del entorno, seguirán aterrizando en la aplicación **Dynamics 365 – personalizados** predeterminada como antes. Esto es lo esperado si desea continuar admitiendo aplicaciones del cliente web heredadas existentes mientras prueba y trabaja en las aplicaciones de la interfaz unificada.  

## <a name="compare-your-new-app-to-the-default-dynamics-365-app"></a>Compare la nueva aplicación con la aplicación de Dynamics 365 predeterminada  
Ahora está listo para iniciar la aplicación. Puede comparar la nueva aplicación de la interfaz unificada con la aplicación personalizada de Dynamics 365 usando los mismos datos, los roles de usuario, reglas de negocio, flujos de trabajo, complementos, etc., porque se encuentran en el mismo entorno. Esto le permite educar a la organización para que sepan que todos los principales básicos siguen ahí y, a la vez, comenzar a explorar las nuevas mejoras de la interfaz unificada.  

> [!TIP]
> Si desea mostrar las aplicaciones lado a lado en un monitor, puede presionar las teclas Windows y flecha izquierda (o la tecla de flecha derecha) a la vez para dividir las ventanas del explorador en el mismo monitor. 

> [!NOTE]
> Si sigue creando personalizaciones en el mapa del sitio predeterminado, como cambios en la navegación o personalizaciones más profundas de la cinta de opciones para botones y acciones, deberá repetir el proceso creando otra aplicación basada en modelo o efectuar las mismas personalizaciones en el nuevo mapa del sitio relacionado con su aplicación basada en modelo.  

## <a name="validate-your-new-app"></a>Validar la nueva aplicación  
Con su aplicación mostrando la interfaz unificada, puede empezar a validar la aplicación, procesos y personalizaciones para identificar qué apariencia tendrá la transición. Se recomienda probar todos los casos de uso, pero puede empezar con los más críticos o agruparlos en patrones lógicos de diseño. Puesto que la interfaz unificada se basa en diseño dinámico, se recomienda realizar siempre pruebas con distintos dispositivos que tienen diferentes resoluciones de pantalla. Al probar la aplicación podrá comprobar que las personalizaciones son compatibles con la interfaz unificada y si existen características que necesiten un rediseño o les falta funcionalidad.  

> [!IMPORTANT]
> La versión actual de Common Data Service y aplicaciones basadas en modelo en Dynamics 365 incluye aún varias características obsoletas. Debe comprobar si la aplicación tiene características obsoletas y reemplazarlas según sea necesario con nuevas capacidades. Más información: [Próximos cambios importantes (funciones obsoletas)](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

> [!TIP]
> La herramienta Comprobador de Power Apps ayuda a comprobar la calidad de los componentes de la solución.  Más información: [Use el comprobador de soluciones para validar sus aplicaciones basadas en modelos en Power Apps](../common-data-service/use-powerapps-checker.md)

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
