---
title: Capas de las soluciones | MicrosoftDocs
description: Aprenda a usar capas de las soluciones
keywords: ''
ms.date: 03/13/2020
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
ms.openlocfilehash: 9c9e95e477e2ccb0bce9eac2256221486412f584
ms.sourcegitcommit: 6fce86edacd9bfe49f8114a2a69bc18302cd01f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "3260704"
---
# <a name="solution-layers"></a>Capas de las soluciones

Existen soluciones administradas y no administradas en diferentes niveles dentro de un entorno de Common Data Service. En Common Data Service, hay dos niveles de capas distintas:  
- Capa no gestionada. Todas las soluciones no administradas importadas y las personalizaciones no administradas existen en esta capa. La capa no administrada es una sola capa.  
- Capas administradas. Todas las soluciones administradas importadas y la solución del sistema existen en este nivel. Cuando se instalan varias soluciones administradas, la última que se instala aparece sobre la solución administrada instalada anteriormente. Esto significa que la segunda solución instalada puede personalizar la que se ha instalado antes. Cuando dos soluciones administradas tienen definiciones en conflicto, el comportamiento del tiempo de ejecución es "El último gana" o se implementa una lógica de fusión.  Si desinstala una solución administrada, la solución administrada siguiente toma efecto. Si desinstala todas las soluciones administradas, el comportamiento predeterminado definido en la solución del sistema se aplica. En la base de la del nivel de capas administradas se encuentra la capa del sistema. La capa del sistema contiene las entidades y componentes necesarios para que la plataforma funcione. 

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
5. Seleccione la pestaña **Etiquetas localizadas** para mostrar información de los componentes que tienen campos de etiqueta en la capa de solución. El idioma base y cualquier texto de traducción importado se muestran como se indica en la columna **Id. de idioma**. Si no existen etiquetas, la pestaña no se muestra.  
   > [!div class="mx-imgBorder"] 
   > ![Etiquetas localizadas de capa de solución](media/localized-labels.png "Etiquetas localizadas de capa de solución")

    Seleccione una etiqueta para ver todas sus capas.

### <a name="see-also"></a>Vea también
[Traducir texto localizable para aplicaciones controladas por modelos](../model-driven-apps/translate-localizable-text.md) <br />
[Información general de las soluciones](solutions-overview.md)
