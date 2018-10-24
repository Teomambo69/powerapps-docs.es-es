---
title: Consulta y visualización de datos jerárquicos con PowerApps | Microsoft Docs
description: Información sobre cómo consultar y visualizar datos relacionados jerárquicamente
ms.custom: ''
ms.date: 06/20/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: ec45f43266c1920d05301c92bdd67838b40b7734
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699269"
---
# <a name="query-and-visualize-hierarchically-related-data"></a>Consulta y visualización de datos relacionados jerárquicamente

Puede obtener valiosas perspectivas de negocio mediante la visualización de datos relacionados jerárquicamente. Las funcionalidades de modelado y visualización jerárquicos ofrecen una serie de ventajas:  
  
-   Ver y explorar información jerárquica compleja.  
  
-   Ver indicadores clave de rendimiento (KPI) en la vista contextual de una jerarquía.  
  
-   Analizar visualmente la información clave en la Web y las tabletas.  
  
Para algunas entidades, como cuenta y usuario, se proporcionan las visualizaciones. Otras entidades, incluidas las entidades personalizadas, pueden habilitarse para una jerarquía y puede crear las visualizaciones para ellas. Según sus necesidades, puede elegir entre una vista de árbol, que muestra la jerarquía completa, o una vista en mosaico, que representa una parte menor de la jerarquía. Ambas vistas se muestran lado a lado. Puede explorar una jerarquía expandiendo y contrayendo un árbol de jerarquía. Los mismos valores jerárquicos de visualización se establecen una vez, pero, se aplican a clientes web y móviles. En tabletas, las representaciones visuales se muestran en un formato modificado conveniente para el factor de forma más pequeño. Los componentes personalizables necesarios para la visualización jerárquica son compatibles con las soluciones, por consiguiente, se pueden transportar entre organizaciones como cualquier otra personalización. Puede configurar los atributos que se muestran en la visualización personalizando un formulario rápido mediante el editor de formularios. No hay ningún requisito para escribir código.  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>Datos jerárquicos de consulta  
 Con Common Data Service para aplicaciones, las estructuras de datos jerárquicas son compatibles con las relaciones de autorreferencia uno a varios (1:N) de los registros relacionados. En el pasado, para ver los datos jerárquicos, tenía que consultar de forma iterativa los registros relacionados. En la actualidad, puede consultar los datos relacionados como una jerarquía en un solo paso. Podrá consultar los registros con la lógica **En** y **No en**. Los operadores jerárquicos **En** y **No en** se exponen en el editor de flujo de trabajo y en la búsqueda avanzada. Para más información sobre cómo usar estos operadores, vea [Configurar pasos de flujo de trabajo](/flow/configure-workflow-steps). Para más información sobre la búsqueda avanzada, vea [Crear, editar o guardar búsquedas avanzadas](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  
  
 Los ejemplos siguientes ilustran varios escenarios para consultar las jerarquías:  
  
 Consultar jerarquía de cuenta  
  
 ![Consultar las cuentas en la jerarquía de cuentas](media/query-accounts.png "Consultar las cuentas en la jerarquía de cuentas")  
  
 Consultar jerarquía de cuenta, incluidas las actividades relacionadas  
  
 ![Consultar actividades relacionadas con la cuenta](media/query-account-related-activities.png "Consultar actividades relacionadas con la cuenta")  
  
 Consultar jerarquía de cuenta, incluidas las oportunidades relacionadas  
  
 ![Consultar oportunidades relacionadas con la cuenta](media/query-account-related-opportunities.png "Consultar oportunidades relacionadas con la cuenta")  
  
 Para consultar los datos como una jerarquía, debe establecer una de las relaciones de autorreferencia uno a varios (1:N) de la entidad como jerárquica. Para activar la jerarquía:  
  
1.  Abra el [Explorador de soluciones](../model-driven-apps/advanced-navigation.md#solution-explorer). 
  
2.  Seleccione la entidad que desee, seleccione **Relaciones 1:N** y después seleccione una relación (1:N). 

3.  En la **Definición de relación**, establezca **Jerárquica** en **Sí**.  
  
> [!NOTE]
> - No se pueden personalizar algunas de las relaciones sencillas (1:N). Esto impedirá establecer esas relaciones como jerárquicas.  
> - Puede especificar una relación jerárquica para las relaciones de autorreferencia del sistema. Esto incluye las relaciones 1:N de autorreferencia del tipo de sistema, como la relación "contact_master_contact".  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>Visualizar datos jerárquicos  
 Las entidades del sistema que tienen las visualizaciones disponibles de fábrica incluyen `Account`, `Position`, `Product` y `User`. En la vista de cuadrícula de estas entidades, puede ver el icono que muestra el gráfico de jerarquía a la izquierda del nombre del registro. El icono de jerarquía no está presente para todos los registros de forma predeterminada. El icono se muestra para los registros que tienen un registro primario, un registro secundario o ambos.  
  
 ![Cuentas activas](media/cust-hs-active-account.png "Cuentas activas")  
  
 Si selecciona el icono de jerarquía, puede ver la jerarquía, con la vista de árbol a la izquierda y la vista de mosaico a la derecha, como se indica a continuación:  
  
 ![Vista de mosaico y árbol de cuentas](media/hierachy-security-accounts-tile-view.png "Vista de mosaico y árbol de cuentas")  
  
 Hay más entidades preestablecidas del sistema que pueden habilitarse para una jerarquía. Estas entidades incluyen `Case`, `Contact`, `Opportunity`, `Order`, `Quote`, `Campaign` y `Team`. Todas las entidades personalizadas pueden habilitarse para una jerarquía.  
  
> [!TIP]
>  Si una entidad puede habilitarse para una jerarquía:  
>  En el Explorador de soluciones, expanda la entidad que desee. Verá el componente de entidad denominado **Configuración de jerarquía**. Las entidades que no se pueden habilitar para una jerarquía no tienen este componente, a excepción de la entidad de zona de ventas de Dynamics 365 Customer Engagement. Aunque **Configuración de jerarquía** aparece para la entidad de zona de ventas, la entidad no se puede habilitar para una jerarquía.  
  
 Cosas más importantes para recordar al crear visualizaciones:  
  
-   Solo se puede configurar como jerárquica una relación que hace referencia a sí misma (1:N) por entidad. En esta relación, la entidad primaria y la entidad relacionada deben ser del mismo tipo, como account_parent_account o new_new_widget_new_widget.  
  
-   En la actualidad, una jerarquía o una visualización se basa en una entidad solo. Puede describir la jerarquía de cuenta mostrando cuentas en varios niveles, pero no puede mostrar cuentas y contactos en la misma visualización de la jerarquía.  
  
-   El número máximo de campos que se pueden mostrar en un mosaico es cuatro. Si desea agregar más campos al formulario rápido que se usa para la vista de mosaico, solo se mostrarán los cuatro primeros campos.  
  
### <a name="visualization-example"></a>Ejemplo de visualización  
 Miremos un ejemplo de crear la visualización para una entidad personalizada. Hemos creado una entidad personalizada llamada new_Widget, hemos creado una relación que hace referencia a sí misma (1:N) **new_new_widget_new_widget** y la hemos marcado como jerárquica, como se indica aquí.  
  
 ![Definición de la relación del widget](media/widget-relationship-definition.png "Definición de la relación del widget")  
  
 A continuación, en la vista de cuadrícula **Configuración de la jerarquía** seleccionamos la relación jerárquica **new_new_widget_new_widget**. En el formulario, completamos los atributos requeridos. Si aún no ha marcado la relación (1:N) como jerárquica, el vínculo del formulario le devolverá al formulario de definición de la relación, donde puede marcar la relación como jerárquica.  
  
 Para **Formulario de vista rápida**, creamos un formulario rápido llamado **Formulario de mosaico de jerarquía del widget**. En este formulario, agregamos cuatro campos para mostrar en cada mosaico.  
  
 ![Creación de formulario rápido para el widget](media/create-quickf-orm.png "Creación de formulario rápido para el widget")  
  
 Después de completar la configuración, creamos dos registros: Widget estándar y Widget premium. Después de marcar el widget premium como elemento principal del widget estándar mediante el campo de búsqueda, la vista de cuadrícula de new_Widget mostró los iconos de la jerarquía, como se indica a continuación:  
  
 ![Cuadrícula de jerarquía del widget](media/widget-hierarchy-grid.png "Cuadrícula de jerarquía del widget")  
  
> [!TIP]
>  Los iconos de la jerarquía no aparecen en la vista de cuadrícula del registro hasta que los registros se emparejen en la relación primaria-secundaria.  
  
 Si elige el icono de jerarquía, se mostrará la jerarquía new_Widget, con la vista de árbol a la izquierda y la vista de mosaico a la derecha, mostrando dos registros. Cada mosaico contiene cuatro campos que proporcionamos en **Formulario de mosaico de jerarquía del widget**.  
  
 ![Vistas de mosaicos y árbol del widget](media/widget-tree-tiles.png "Vistas de mosaicos y árbol del widget")  
  
## <a name="see-also"></a>Vea también  
 [Vídeo: Modelado de seguridad jerárquico](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)   
 [Vídeo: Visualización de la jerarquía](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
