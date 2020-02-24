---
title: Importar soluciones | MicrosoftDocs
description: Aprenda cómo importar una solución en Power Apps
ms.custom: ''
ms.date: 01/30/2020
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
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 504e66801c122810da12810d9b19e5069136f7d6
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017641"
---
# <a name="import-solutions"></a>Importar soluciones 

 Puede importar soluciones manualmente usando los pasos siguientes. Importe únicamente las soluciones que se obtengan de una fuente de confianza. Es posible que las personalizaciones incluyan un código que puede enviar datos a orígenes externos.   
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y seleccione **Soluciones** en el panel de navegación de la izquierda.  
  
2.  Seleccione **Importar** en la barra de comandos.  

    > [!div class="mx-imgBorder"]  
    > ![Importar solución](media/solution-import.png "Importar solución") 
  
3.  En la página **Seleccionar paquete de solución**, seleccione **Examinar** para buscar el archivo comprimido (.zip o .cab) que contiene la solución que desea importar. 
  
4.  Seleccione **Siguiente**.  
  
5.  Información sobre cómo se muestra la solución. Seleccione **importar**.  
  
6. Es posible que tenga que esperar unos momentos mientras la importación se completa. Vea los resultados y, a continuación, seleccione **Cerrar**.  
  
 Si importó cambios que requieren publicación, debe publicar las personalizaciones antes de que estén disponibles. 
  
 Si la importación no es correcta, verá un informe que mostrará los errores o advertencias capturados. Seleccione **Descargar archivo de registro** para capturar detalles sobre la causa del error de importación. La causa más común para que una importación falle es que la solución no contenía algunos componentes requeridos.  
  
 Cuando descargue el archivo de registro, encontrará un archivo XML que puede abrir mediante Office Excel para ver el contenido.  
  
> [!NOTE]
>  No se puede editar un conjunto de reglas de enrutamiento activo. Por tanto, si importa una solución que incluye un conjunto activo de reglas de enrutamiento a un entorno donde la regla ya existe con el mismo identificador, la importación generará un error. Más información: [Crear reglas para enrutar casos automáticamente](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

### <a name="see-also"></a>Vea también
[Actualizar soluciones](update-solutions.md) <br />
[Exportar soluciones](export-solutions.md)

