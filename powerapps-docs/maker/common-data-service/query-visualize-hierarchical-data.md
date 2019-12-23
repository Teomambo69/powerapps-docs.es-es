---
title: Consulte y visualice datos jerárquicos con Power Apps | MicrosoftDocs
description: Aprenda cómo consultar y visualizar datos jerárquicos relacionados
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d3d0a6123927b6901a0ff2a27d981333847a8d9d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2870048"
---
# <a name="query-and-visualize-hierarchically-related-data"></a>Consultar y visualizar datos relacionados jerárquicamente

Puede obtener valiosas perspectivas profesionales visualizando los datos relacionados jerárquicamente. Las funciones de visualización y modelado jerárquico tienen varias ventajas:  
  
-   Vea y explore información jerárquica compleja.  
  
-   Vea indicadores clave de rendimiento (KPIs) en la vista contextual de una jerarquía.  
  
-   Analice visualmente información clave en la web y las tabletas.  
  
Para algunas entidades, como cuenta y usuario, las visualizaciones se suministran predefinidas. Otras entidades, incluidas las entidades personalizadas, pueden habilitarse para una jerarquía y puede crear las visualizaciones para ellas. Según sus necesidades, puede elegir entre una vista de árbol, que muestra la jerarquía completa, o una vista en mosaico, que representa una parte menor de la jerarquía. Ambas vistas se muestran lado a lado. Puede explorar una jerarquía expandiendo y contrayendo un árbol de jerarquía. Los mismos valores jerárquicos de visualización se establecen una vez, pero, se aplican a clientes web y móviles. En tabletas, las representaciones visuales se muestran en un formato modificado conveniente para el factor de forma más pequeño. Los componentes personalizables necesarios para la visualización jerárquica son compatibles con las soluciones, por consiguiente, se pueden transportar entre organizaciones como cualquier otra personalización. Puede configurar los atributos que se muestran en la visualización personalizando un formulario rápido mediante el editor de formularios. No hay requisito de escribir código.  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>Consultar datos jerárquicos  
 Con Common Data Service, las estructuras jerárquicas de datos son compatibles con relaciones que hacen referencia a sí mismas de registros relacionados. En el pasado, para ver datos jerárquicos era necesario consultar iterativamente los registros relacionados. Actualmente, puede consultar los datos relacionados como una jerarquía, en un paso. Podrá consultar los registros de entidad, usando la lógica de **Bajo** y **No menor que**. Los operadores jerárquicos **Bajo** y **No menor que** aparecen en Búsqueda avanzada y el editor de flujo de trabajo. Para obtener más información acerca de cómo utilizar estos operadores, consulte [Configurar pasos del flujo de trabajo](/flow/configure-workflow-steps). Para obtener más información sobre Búsqueda avanzada, consulte [Crear, editar o guardar la búsqueda de Búsqueda avanzada](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)..  
  
 Los siguientes ejemplos muestran los distintos escenarios para consultar jerarquías:  
  
 Consultar jerarquía de cuenta  
  
 ![Consultar cuentas en la jerarquía de cuentas](media/query-accounts.png "Consultar cuentas en la jerarquía de cuentas")  
  
 Consultar jerarquía de cuenta, incluidas actividades relacionadas  
  
 ![Consultar actividades relacionadas de la cuenta](media/query-account-related-activities.png "Consultar actividades relacionadas de la cuenta")  
  
 Consultar jerarquía de cuenta, incluidas oportunidades relacionadas  
  
 ![Consultar oportunidades relacionadas de la cuenta](media/query-account-related-opportunities.png "Consultar oportunidades relacionadas de la cuenta")  
  
 Para consultar los datos como jerarquía, debe habilitar como jerárquica una de las relaciones que hacen referencia a sí mismas de uno a varios o de varios a uno de la entidad. Para activar la jerarquía:  
  

1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4.  Seleccione una relación que hace referencia a sí misma.

5.  En el panel de detalles de la relación, marque **Jerárquico**.  
  
> [!NOTE]
> - Algunas de las relaciones predefinidas no se pueden personalizar. Esto evitará que configure esas relaciones como jerárquicas.  
> - Puede especificar una relación jerárquica para las relaciones que hacen referencia a sí mismas del sistema. Esto incluye las relaciones que hacen referencia a sí mismas de tipo sistema, como la relación "contact_master_contact".  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>Visualice datos jerárquicos  
 Las entidades del sistema que tienen visualizaciones disponibles predefinidas son: `Account`, `Position`, `Product` y `User`. En la vista de cuadrícula de estas entidades, puede ver el icono que muestra el gráfico de jerarquía a la izquierda del nombre del registro. El icono de jerarquía no está presente para todos los registros de forma predeterminada. El icono se muestra para los registros que tienen un registro primario, un registro secundario o ambos.  
 
 > [!div class="mx-imgBorder"] 
 > ![Cuentas activas](media/cust-hs-active-account.png "Cuentas activas")  
  
 Si selecciona el icono de jerarquía, puede ver la jerarquía, con la vista de árbol a la izquierda y la vista de mosaico a la derecha, como se indica a continuación:  
  
> [!div class="mx-imgBorder"] 
> ![Árbol de cuenta y vista de ventanas](media/hierachy-security-accounts-tile-view.png "Árbol de cuenta y vista de ventanas")  
  
 Algunas otras entidades del sistema predefinidas se pueden habilitar para una jerarquía. Estas entidades incluyen `Case`, `Contact`, `Opportunity`, `Order`, `Quote`, `Campaign`, y `Team`. Todas las entidades personalizadas pueden habilitarse para una jerarquía.  
  
> [!TIP]
>  Si una entidad pueden habilitarse para una jerarquía:  
>  En el explorador de soluciones, expanda la entidad que desee. Verá el componente de la entidad denominado **Configuración de jerarquía**. Las entidades que no se pueden habilitar para una jerarquía no tienen este componente, con la excepción de la entidad Zona de ventas de Dynamics 365. Aunque **Configuración de la jerarquía** se muestra para la entidad Zona de ventas, la entidad no se puede habilitar para una jerarquía.  
  
 Cosas más importantes para recordar al crear visualizaciones:  
  
-   Solo se pueden configurar como jerárquica una relación que hace referencia a sí misma (1: N) por entidad. En esta relación la entidad principal y la entidad relacionada deben ser del mismo tipo, por ejemplo, account_parent_account o Widget_new_Widget_new_Widget.  
  
-   Actualmente, una jerarquía o una visualización se basa en una entidad solo. Puede describir la jerarquía de cuenta mostrando cuentas en varios niveles, pero no puede mostrar cuentas y contactos en la misma visualización de la jerarquía.  
  
-   El número máximo de campos que se pueden mostrar en un mosaico es cuatro. Si desea agregar más campos al formulario rápido que se usa para la vista de mosaico, sólo los primeros cuatro campos se mostrarán.  
  
### <a name="visualization-example"></a>Ejemplo de visualización  
 Miremos un ejemplo de crear la visualización para una entidad personalizada. Hemos creado una entidad personalizada llamada new_Widget, hemos creado una relación que hace referencia a sí misma y marcado como jerárquica, como se indica aquí.  
 
> [!div class="mx-imgBorder"] 
> ![Definición de relación de widget](media/widget-relationship-definition.png "Definición de relación de widget")  
   
 A continuación, en la vista de cuadrícula **Configuración de la jerarquía** seleccionamos la relación jerárquica **Widget_new_Widget_new_Widget**. En el formulario, completamos los atributos requeridos. Si aún no ha marcado la relación como jerárquica, el vínculo del formulario le devolverá al editor de entidades clásico, donde también puede marcar la relación como jerárquica.  
  
 Para el **Formulario de vista rápida**, creamos un formulario rápido llamado **Formulario de ventana de jerarquía del widget**. En este formulario, agregamos cuatro campos para mostrar en cada ventana.  
  
> [!div class="mx-imgBorder"] 
> ![Crear formulario rápido para widget](media/create-quickf-orm.png "Crear formulario rápido para widget")  
  
 Después de completar la configuración, creamos dos registros: Widget estándar y Widget premium. Después de convertir el Widget premium en un elemento principal del Widget estándar mediante el campo de búsqueda, la vista de cuadrícula de new_Widget mostró los iconos de la jerarquía, como se indica a continuación:  
  
> [!div class="mx-imgBorder"] 
> ![Cuadrícula de la jerarquía del widget](media/widget-hierarchy-grid.png "Cuadrícula de la jerarquía del widget")  
  
> [!TIP]
>  Los iconos de la jerarquía no aparecen en la vista de cuadrícula del registro hasta que los registros se emparejen en el elemento principal - relación secundaria.  
  
 Si elige el icono de jerarquía, se mostrará la jerarquía new_Widget, con la vista de árbol a la izquierda y la vista de mosaico a la derecha, mostrando dos registros. Cada ventana contiene cuatro campos que proporcionamos en el **Formulario de ventana de jerarquía del widget**.  
 
 > [!div class="mx-imgBorder"] 
 > ![Vistas de mosaicos y árbol del widget](media/widget-tree-tiles.png "Vistas de mosaicos y árbol del widget")  
  
## <a name="see-also"></a>Vea también  
 [Vídeo: Modelos de seguridad jerárquica](https://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)   
 [Vídeo: Visualización de la jerarquía](https://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
