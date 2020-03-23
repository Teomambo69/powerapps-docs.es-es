---
title: Capas de las soluciones | MicrosoftDocs
description: Aprenda a usar capas de las soluciones
keywords: ''
ms.date: 02/05/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 10ab6feca7843d64d20938561d44748fc6756768
ms.sourcegitcommit: dc379bede57da58b5787eda5437eb94b662e21ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "3028359"
---
# <a name="solution-layers"></a>Capas de las soluciones

Existen soluciones administradas y no administradas en diferentes capas dentro de un entorno de Common Data Service. En Common Data Service, hay dos capas distintas:  
- Capa no gestionada. Todas las soluciones no administradas importadas y las personalizaciones no administradas existen en esta capa. La capa no administrada es una sola capa.  
- Capa administrada. Todas las soluciones administradas importadas y la solución del sistema existen en esta capa. Cuando se instalan varias soluciones administradas, la primera que se instala aparece debajo de la solución administrada instalada más tarde. Esto significa que la segunda solución instalada puede personalizar la que se ha instalado antes. Cuando dos soluciones administradas tienen definiciones en conflicto, la regla general es la "última gana". Si desinstala una solución administrada, la solución administrada siguiente toma efecto. Si desinstala todas las soluciones administradas, el comportamiento predeterminado definido en la solución del sistema se aplica. En la base de la capa administrada se encuentra la capa del sistema. La capa del sistema contiene la solución del sistema, que incluye todas las entidades y componentes estándar. La solución del sistema define lo que se puede y no se puede personalizar mediante propiedades administradas. Los editores de soluciones administradas tienen la misma capacidad de restringir su capacidad de personalización de los componentes de la solución que agregan a su solución. Puede personalizar cualquier componente de la solución que no tenga propiedades administradas que le impidan personalizarlo. Más información: [Establecer propiedades administradas en metadatos de Common Data Service](set-managed-properties-metadata.md) 

![Capas de las soluciones](media/solution-layers.png)

## <a name="solution-merge-behavior"></a>Comportamiento de la combinación de soluciones
Al preparar la solución administrada para la distribución, recuerde que es posible que un entorno tenga varias soluciones instaladas o que admita la instalación de otras soluciones en el futuro. Cree una solución que siga las prácticas recomendadas de manera que su solución no interfiera con otras soluciones.

Los procesos que utiliza Common Data Service para combinar las personalizaciones hacen hincapié en mantener la funcionalidad de la solución. Si bien se hacen todos los esfuerzos necesarios para mantener la presentación, algunas incompatibilidades entre las personalizaciones pueden requerir que la resolución computarizada modifique algunos detalles de la presentación a favor de mantener la funcionalidad de la personalización. Más información: [Comprender cómo se combinan soluciones administradas](../../developer/common-data-service/understand-managed-solutions-merged.md)

## <a name="view-the-solution-layers-for-a-component"></a>Ver las capas de las soluciones de un componente
La característica de capas de las soluciones le permiten ver todos los cambios del componente que se producen debido a cambios en la solución a lo largo del tiempo. En una capa de solución, puede explorar para ver los detalles cambiados y sin cambios específicos de la propiedad para un componente. Puede obtener acceso a las capas des las soluciones desde la lista **Componentes** o del cuadro de diálogo **Detalles de la dependencia** en el explorador de soluciones. 

Característica de capas de la solución: 
-   Permite ver el orden en el que una solución ha cambiado un componente. 
-   Permite ver todas las propiedades de un componente en una solución específica incluidos los cambios en el componente. 
-   Se pueden usar para solucionar problemas de dependencias o disposición en capas de la solución mostrando información detallada sobre los cambios para un componente que ha introducido un cambio en la solución.

1. Para ver las capas de las soluciones de la lista **Componentes**, abra [explorador de soluciones](../model-driven-apps/advanced-navigation.md#solution-explorer). En la lista **Componentes**, seleccione un componente, como **Cuenta** y, a continuación seleccione **Capas de las soluciones** en la barra de herramientas. 

   > [!div class="mx-imgBorder"] 
   > ![Botón Capas de las soluciones](media/solution-layers-toolbar.png "Botón Capas de las soluciones")

2. Se muestra la página de capas de la soluciones. Muestra cada capa para el componente, como la entidad **Cuenta** que se muestra aquí, con la capa más reciente en la parte superior. Para ver los detalles de una capa de soluciones, selecciónela. 

   > [!div class="mx-imgBorder"] 
   > ![Lista de capas de las soluciones](media/solution-layers-list.png "Lista de capas de las soluciones")

3. En el cuadro de diálogo **Capas de las soluciones** , la pestaña **Cambiar propiedades** muestra únicamente las propiedades que se modificaron como parte de la capa de la solución específica. 

   > [!div class="mx-imgBorder"] 
   > ![Propiedades cambiadas de la capa de las soluciones](media/solution-layers-change-prop.png "Propiedades cambiadas de la capa de las soluciones")

4. Seleccione la pestaña **Todas las propiedades** para ver todas las propiedades, incluidas las propiedades con y sin cambios, para la capa de las soluciones. 

   > [!div class="mx-imgBorder"] 
   > ![Todas las propiedades de la capa de las soluciones](media/solution-layers-all-prop.png "Todas las propiedades de la capa de las soluciones")

### <a name="see-also"></a>Vea también
[Información general de las soluciones](solutions-overview.md)
