---
title: Actualizar una solución | MicrosoftDocs
description: Obtener información sobre cómo actualizar una solución en Power Apps
ms.custom: ''
ms.date: 03/18/2020
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0bebbc9eeead8fb4f02c4bf958c33b79c0d9cc1c
ms.sourcegitcommit: 48414442a10210d49911c3eda8b49f68db85f684
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2020
ms.locfileid: "3151194"
---
# <a name="upgrade-or-update-a-solution"></a>Actualizar una solución  
Hay ocasiones en las que podría necesitar instalar una actualización de una solución administrada existente. Para actualizar la solución, siga estos pasos: 

1.  Abra la solución no administrada en su entorno de desarrollo y cree nuevos o agregue y elimine los componentes existentes que desee. 
2.  Incremente el número de versión cuando exporte la solución como solución administrada. Más información: [Comprender los números de versión para las actualizaciones](#understanding-version-numbers-for-updates) 

    > [!div class="mx-imgBorder"] 
    > ![Versión de solución de actualización](media/update-solution-version.png)
3. [Aplicar la actualización o actualización en el entorno de destino](#apply-the-upgrade-or-update-in-the-target-environment)

## <a name="apply-the-upgrade-or-update-in-the-target-environment"></a>Aplicar la actualización o actualización en el entorno de destino
El proceso para importar una solución actualizada es similar a instalar una nueva solución administrada, salvo en que obtendrá algunas opciones diferentes. Si va a actualizar una solución que ha obtenido de otra persona, debe obtener instrucciones del editor de soluciones sobre las opciones que debe elegir.  

1. Iniciar sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione el entorno de destino que desee y luego seleccione **Soluciones** desde la navegación izquierda.  

2. Seleccione **Importar** en la barra de comandos.  

3. En la página **Seleccionar paquete de solución**, seleccione **Examinar** para buscar el archivo comprimido (.zip o .cab) que contiene la solución que desea actualizar.  

4. Seleccione **Siguiente**.  

5. Puede ver la información de la solución antes de elegir **Siguiente**. Esta página mostrará una barra amarilla que muestra **Este paquete de solución contiene una actualización para una solución que ya está instalada**.  

6. Seleccione entre las siguientes opciones de acción de la solución:  
   - **Actualización acumulativa (recomendada)** Esta opción actualiza la solución a la última versión y resume todas las revisiones anteriores en un solo paso.  Se eliminarán los componentes asociados a la versión de solución anterior que no se encuentre en la versión de solución más reciente. Esta opción es la recomendada ya que garantizará que su estado de configuración resultante es coherente con la solución de importación, incluida la eliminación de los componentes que ya no forman parte de la solución.
        
   - **Fase de actualización acumulativa** Esta opción actualiza la solución a la versión superior, pero aplaza la eliminación de la versión anterior y de cualquier parche relacionado hasta que se aplique una actualización de la solución más adelante.  Esta opción solo se debe seleccionar si desea tener las soluciones tanto nuevas como actualizadas instaladas en el sistema en paralelo de modo que pueda hacer migración de datos antes de completar la actualización de la solución. Esto eliminará la solución antigua y los componentes no incluidos en la nueva solución.
        
   - **Actualización (no recomendada)** Esta opción reemplaza su solución con esta versión.  Los componentes que no están en la solución más reciente no se eliminarán y permanecerán en el sistema.  No se recomienda esta opción ya que el entorno de destino será distinto en la configuración del entorno de origen y podría causar problemas difíciles de reproducirse y de diagnosticar.
        
7. Seleccione una de las opciones de personalización siguientes:

   - **Mantener personalizaciones (recomendado)**  

        Al seleccionar esta opción se mantendrán las personalizaciones no administradas realizadas en los componentes, pero algunas de las actualizaciones incluidas en esta solución no surtirán efecto.  

   - **Sobrescribir personalizaciones (no recomendado)**  

        Al seleccionar esta opción se sobrescribirán las personalizaciones no administradas realizadas anteriormente en los componentes incluidos en esta solución. Esta opción no afecta a los componentes que admiten comportamiento de combinación (formularios, mapa de sitio, cinta de opciones, módulos de aplicación).  Los componentes que tienen otras soluciones administradas además de la solución existente que está reemplazando continuarán en la parte superior y no se verán afectados por esta opción.  

8. Decida si habilita la siguiente opción para publicar acciones de importación:
   - **Habilite los pasos de procesamiento de mensajes de SDK que se incluyen en la solución.**  
        Al seleccionar esta opción, habilitará los complemento y flujos de trabajo que se incluyen en la solución.
        
9. Seleccione **Siguiente**.  

10. Es posible que tenga que esperar unos momentos mientras la importación de la solución se completa. Si es correcta, puede ver los resultados y seleccione **Cerrar**.  

   Si importó cambios que requieren publicación, debe publicar las personalizaciones para que estén disponibles. 

**Finalización de la actualización de la solución** Si elige preparar para la actualización, o si el sistema tiene un problema para completar una actualización, verá que tiene la solución original aún instalada en el sistema, así como una nueva solución que tiene el mismo nombre de la solución que la solución base añadida con el sufijo \_Upgrade.  Para completar la actualización, seleccione la solución base en la lista de soluciones y seleccione **Aplicar actualización de la solución**.  Esto desinstalará todas las revisiones anteriores y la solución base. A continuación, cambie el nombre de la solución \_Upgrade para que tenga el mismo nombre que la solución base anterior.  Se eliminarán como parte de este proceso los componentes que se encuentren en la solución original y revisiones que no estén presentes en la solución \_Upgrade.

## <a name="understanding-version-numbers-for-updates"></a>Comprender los números de versión para las actualizaciones
La versión de una solución tiene el siguiente formato: primaria.secundaria.compilación.revisión. Una actualización debe tener un número de compilación o de revisión más alto que la solución primaria. Por ejemplo, para una versión de solución base 3.1.5.7, una pequeña actualización podría ser una versión 3.1.5.8 o una actualización un poco más significativa podría tener la versión 3.1.7.0. Una actualización sustancialmente más significativa podría ser la versión 3.2.0.0.


### <a name="see-also"></a>Vea también
[Agregar componentes de la solución](create-solution.md#add-solution-components) <br />
[Exportar soluciones](export-solutions.md) <br />
[Importar soluciones](import-update-export-solutions.md)