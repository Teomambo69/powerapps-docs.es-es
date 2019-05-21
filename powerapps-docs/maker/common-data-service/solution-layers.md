---
title: Vea capas de las soluciones | MicrosoftDocs
description: Aprenda a usar capas de las soluciones
keywords: null
ms.date: 04/10/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
  - Dynamics 365 for Customer Engagement Version 9.x
  - powerapps
ms.assetid: null
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="view-solution-layers"></a>Ver capas de las soluciones
Las capas de las soluciones le permiten ver todos los cambios del componente que se producen debido a cambios en la solución a lo largo del tiempo. En una capa de solución, puede explorar para ver los detalles cambiados y sin cambios específicos de la propiedad para un componente. 

Las capas de las soluciones proporcionan las siguientes ventajas: 
-   Permiten ver el orden en el que una solución ha cambiado un componente. 
-   Permiten ver todas las propiedades de un componente en una solución específica incluidos los cambios en el componente. 
-   Se pueden usar para solucionar problemas de dependencias o disposición en capas de la solución mostrando información detallada sobre los cambios para un componente que ha introducido un cambio en la solución.

## <a name="view-the-solution-layers-for-a-component"></a>Ver las capas de las soluciones de un componente
Puede obtener acceso a las capas des las soluciones desde la lista **Componentes** o del cuadro de diálogo **Detalles de la dependencia** en el explorador de soluciones. 

1. Para ver las capas de las soluciones de la lista **Componentes**, [abra el explorador de soluciones](../model-driven-apps/advanced-navigation.md#solution-explorer), en la lista **Componentes** seleccione un componente, como **Cuenta** y, a continuación seleccione **Capas de las soluciones** en la barra de herramientas. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-toolbar.png "Botón Capas de las soluciones.")

2. La página de capas de las soluciones que muestra cada capa para el componente, como la entidad de cuenta que se muestra aquí, con la capa más reciente en la parte superior. Para ver los detalles de una capa de soluciones, selecciónela. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-list.png "Lista de capas de las soluciones")

3. En el cuadro de diálogo **Capas de las soluciones** , la pestaña **Cambiar propiedades** muestra únicamente las propiedades que se modificaron como parte de la capa de la solución específica. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-change-prop.png "Propiedades cambiadas de la capa de las soluciones")

4. Seleccione la pestaña **Todas las propiedades** para ver todas las propiedades, incluidas las propiedades con y sin cambios, para la capa de las soluciones. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-all-prop.png "Todas las propiedades de la capa de las soluciones")

## <a name="see-also"></a>Vea también
[Información general de las soluciones](solutions-overview.md)