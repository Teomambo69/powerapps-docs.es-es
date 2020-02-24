---
title: Usar soluciones en Power Apps | MicrosoftDocs
description: Aprenda cómo usar soluciones para crear o personalizar aplicaciones
ms.custom: ''
ms.date: 10/28/2019
ms.reviewer: tapanm
ms.service: powerapps
ms.topic: article
author: caburk
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: caburk
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c926e0fb48791879ea88c19212b30c79731cb3be
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "3004900"
---
# <a name="use-solutions-in-power-apps"></a>Usar soluciones en Power Apps

 En Power Apps, puede ver una lista de soluciones seleccionando **Soluciones** en la navegación izquierda. A continuación puede seleccionar una solución para ver todos sus componentes. 
 
> [!div class="mx-imgBorder"]  
> ![Solución de demostración con todos los componentes](media/solution-all-items-list.PNG "Solución de demostración con todos los componentes")  
 
> [!NOTE]
>  La experiencia de soluciones solo está disponibles con conexión y para entornos de la versión 9.1.0.267 y posteriores. Para comprobar la versión, vaya a …[Centro de administración de Power Apps](https://admin.powerapps.com/)> **Entornos** > seleccione el entorno > pestaña **Detalles**. Para los entornos de una versión anterior, la selección de una solución lo abrirá en la experiencia clásica.  
 
 Puede examinar todos los componentes de una solución desplazándose a través de los elementos. Si hay más de 100 elementos en la lista puede seleccionar **Cargar los siguientes 100 elementos** para ver más. 
 
> [!div class="mx-imgBorder"]  
> ![Cargar más componentes](media/load-more.PNG "Cargar más componentes")  

 ## <a name="search-and-filter-in-a-solution"></a>Buscar y filtrar en una solución
 
 También puede buscar un componente específico por su nombre. 
 
> [!div class="mx-imgBorder"]  
> ![Busque componente](media/solution-search-box.png "Busque componente")  
 
 O bien filtre todos los elementos de la lista por tipo de componente.
  
> [!div class="mx-imgBorder"]  
> ![Filtrar componente por tipo](media/solution-filter.PNG "Filtrar componente por tipo")  
 
 ## <a name="contextual-commands"></a>Comandos contextuales
 
 Cuando selecciona cada componente, las acciones disponibles en la barra de comandos cambiarán según el tipo del componente seleccionado y si la solución es predeterminada o administrada. 
 
> [!div class="mx-imgBorder"]  
> ![Comandos específicos de componentes](media/component-commands.png "Comandos específicos de componentes")  
 
 Cuando no seleccione ningún componente, la barra de comandos mostrará las acciones aplicadas a la propia solución. 
 
> [!div class="mx-imgBorder"]  
> ![Comandos específicos de solución](media/solution-commands.PNG "Comandos específicos de solución")  
 
 ## <a name="create-components-in-a-solution"></a>Crear componentes en una solución
 Con soluciones que son no administradas o la predeterminada, puede usar el comando **Nuevo** para crear diferentes tipos de componentes. Esto le llevará a crear un experiencia diferente según el tipo de componente que elija. Cuando termine de crear el componente, se agregará a la solución. 
 
> [!div class="mx-imgBorder"]  
> ![Crea un nuevo componente en una solución](media/solution-new-component.PNG "Crea un nuevo componente en una solución")  
 
 ## <a name="add-an-existing-component-to-a-solution"></a>Agregar un componente existente a una solución
 
 Con soluciones que no sean administradas o la predeterminada, puede usar el comando **Agregar existente** para traer componentes que todavía no se encuentran en la solución.  
 
> [!div class="mx-imgBorder"]  
> ![Agregar un componente existente a una solución](media/solution-add-existing-component.PNG "Agregar un componente existente a una solución")  
  
 Con soluciones que son administradas solo algunos comandos están disponibles y verá el mensaje que se muestra a continuación. Deberá agregarlo a otra solución no administrada que ha creado para personalizar el componente. El componente puede no ser personalizable. Más información: [Propiedades administradas](solutions-overview.md#managed-properties)

> [!div class="mx-imgBorder"]  
> ![Solución administrada](media/managed-solution.PNG "Solución administrada")  

 Muchas de las personalizaciones que deseará hacer incluyen las entidades. Puede usar el filtro **Entidad** para mostrar una lista de todas las entidades de la solución actual que se pueden personalizar de alguna forma. Cuando profundiza en una entidad puede ver los componentes que forman parte de la entidad como se indica con la entidad Cuenta en la captura de pantalla siguiente. 
   
> [!div class="mx-imgBorder"]  
> ![Solución de demostración que muestra la entidad de cuenta expandida](media/solution-entity-account.png "Solución de demostración que muestra la entidad de cuenta expandida")  

## <a name="classic-solution-explorer"></a>Explorador de soluciones clásico

En Power Apps, puede ver el explorador de soluciones clásico seleccionando **Soluciones** en el panel de navegación de la izquierda y, a continuación seleccionando **Cambiar a clásica** en la barra de comandos. El explorador de soluciones clásico es el que anteriormente estaba disponible en el área **Configuración > Personalizaciones avanzadas** en Power Apps. 

## <a name="known-limitations"></a>Limitaciones conocidas

Las siguientes limitaciones se aplican al uso de aplicaciones de lienzo, flujos y conectores personalizados en soluciones. 

- Los flujos desencadenados por botones de aplicaciones de lienzo no se admiten en soluciones. Cree la aplicación y el flujo fuera de una solución, y exporte el archivo .msapp para migrar aplicaciones de lienzo con un flujo desencadenado por un botón insertado. 
- Si una aplicación de lienzo se empaqueta en una solución administrada, no puede editarse y volver a publicarse en el entorno de destino. Use soluciones no administradas si las aplicaciones requieren edición en el entorno de destino. 
- Las conexiones requieren autenticación y consentimiento, que requiere una sesión de usuario interactiva y por tanto no se pueden transportar mediante soluciones. Después de importar la solución, juegue la aplicación para autenticar conexiones. También puede crear las conexiones en el entorno de destino antes de importar la solución. 
-   Las aplicaciones de lienzo compartidas como copropietario con grupo de seguridad Azure Active Directory (AAD) no se pueden agregar a soluciones. Deje de comaprtir la aplicación antes de agregarla a una solución.
-   Las aplicaciones de lienzo no se mostrarán en el explorador de soluciones clásico. Use la experiencia moderna.
-   El acceso a la aplicación de lienzo (CRUD y seguridad) se administra completamente en Power Apps y no en la base de datos de Common Data Service ().
- Las operaciones de base de datos como copia de seguridad, restauración, y copia no son compatibles con las aplicaciones de lienzo y flujos. Estas operaciones pueden dañar a aplicaciones de lienzo y flujos.
- Al eliminar una solución administrada no se revertirá a la versión de otra aplicación de lienzo. En su lugar, todas las versiones de la aplicación se eliminan.
- Cuando se importa una solución que contiene un flujo no se crearán o asociarán conexiones necesarias. El flujo se debe editar para corregir las conexiones.
  - Si usa soluciones administradas, se crea una personalización activa en la capa no administrada. Por tanto las actualizaciones posteriores de la solución al flujo no se reflejarán. 
- Los flujos creados a partir de soluciones no se mostrarán en la lista "Flujos de equipo”. Se debe acceder a ellos a través de una solución. 
- Los flujos desencadenados por botón no están disponibles en soluciones.
- Los flujos desencadenados desde aplicaciones de Microsoft 365 como Excel no están disponibles en soluciones.
- Los flujos que conectan con SharePoint no están disponibles en soluciones.
- Los flujos en soluciones no admiten la autenticación delegada. Por ejemplo, el acceso a un flujo no se concede automáticamente en función del acceso a la lista de SharePoint de la que se creó el flujo.
- Los conectores externos creados fuera de soluciones no se pueden agregar a soluciones en este momento.


 Para obtener más información acerca de los componentes individuales de una solución, vea los temas siguientes:  
  
-   Para las personalizaciones de entidad, relaciones de entidades, campos y mensajes, consulte [Metadatos](create-edit-metadata.md)..  
  
-   Para los formularios de entidades, consulte [Formularios](../model-driven-apps/create-design-forms.md).  
  
-   Para los procesos, consulte [Procesos](../model-driven-apps/guide-staff-through-common-tasks-processes.md)..  
  
-   Para las reglas de negocio, consulte [Reglas de negocio](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).  
