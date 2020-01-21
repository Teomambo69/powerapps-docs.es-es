---
title: Actualizar soluciones | MicrosoftDocs
description: Aprenda a actualizar una solución en Power Apps
ms.custom: ''
ms.date: 09/30/2019
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
ms.openlocfilehash: 534c4d986cec688723e6d3351135bca2692d020f
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914403"
---
# <a name="update-solutions"></a>Actualizar soluciones  

Hay ocasiones en las que podría desear instalar una actualización de una solución administrada existente. El proceso es similar a instalar una nueva solución administrada, salvo en que obtendrá algunas opciones diferentes. Si va a actualizar una solución que ha obtenido de otra persona, debe obtener instrucciones del editor de soluciones sobre las opciones que debe elegir.  
  
1.  Seleccione **Soluciones** en la barra de navegación izquierda.
  
2.  En el menún de la lista de soluciones, seleccione **Importar**.  
  
3.  En el cuadro de diálogo **Importar solución**, en el paso **Seleccionar paquete de solución**, seleccione **Elegir archivo** y busque el archivo comprimido (.zip o .cab) que contiene la solución que desea actualizar.

4.  Seleccione **Siguiente**.  
  
5.  Vea la información de la solución y seleccione **Siguiente**. Esta página mostrará una barra amarilla que indica que **Este paquete de solución contiene una actualización para una solución que ya está instalada**.  
  
6.  Tendrá las siguientes opciones:  
  
    - **Mantener personalizaciones (recomendado)**  
  
         Al seleccionar esta opción se mantendrán las personalizaciones no administradas realizadas en los componentes, pero algunas de las actualizaciones incluidas en esta solución no surtirán efecto.  
  
    - **Sobrescribir personalizaciones**  
  
         Al seleccionar esta opción se sobrescriben las personalizaciones no administradas realizadas anteriormente en los componentes incluidos en esta solución. Todas las actualizaciones incluidas en esta solución surtirán efecto.  
  
     Elija la opción correcta y seleccione **Siguiente**.  
  
7.  Es posible que tenga que esperar unos momentos mientras la importación se completa. Vea los resultados y, a continuación, seleccione **Cerrar**.  
  
 Si importó cambios que requieren publicación, debe publicar las personalizaciones antes de que estén disponibles. 
  
 Los editores de soluciones pueden pedirle que exporte las personalizaciones no administradas existentes, que actualice su solución administrada mediante la opción para sobrescribir personalizaciones y que vuelva a importar las personalizaciones no administradas. Esto le permitirá asegurarse de que se han aplicado los cambios que están esperando mientras se mantienen las personalizaciones.  
  
<a name="BKMK_ExportSolutions"></a>   

### <a name="see-also"></a>Vea también
[Exportar soluciones](export-solutions.md) <br />
[Distribuir soluciones y revisiones](use-segmented-solutions-patches-simplify-updates.md) <br />
[Importar soluciones](import-update-export-solutions.md)