---
title: Importar soluciones | MicrosoftDocs
description: Aprenda cómo importar una solución en Power Apps
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
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0eb65eb9ac1240769ba0cc885cb9c2e30a8f83f9
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909482"
---
# <a name="import-solutions"></a>Importar soluciones 

 Puede importar soluciones manualmente usando los pasos siguientes. Importe únicamente las soluciones que se obtengan de una fuente de confianza. Es posible que las personalizaciones incluyan un código que puede enviar datos a orígenes externos.   
  
1.  Seleccione **Soluciones** en la barra de navegación izquierda.  
  
2.  En el menún de la lista de soluciones, seleccione **Importar**.  

    > [!div class="mx-imgBorder"]  
    > ![Importar solución](media/solution-import.png "Importar solución") 
  
3.  En el cuadro de diálogo **Importar solución**, en el paso **Seleccionar paquete de solución**, seleccione **Elegir archivo** y busque el archivo comprimido (.zip o .cab) que contiene la solución que desea importar. 
  
4.  Seleccione **Siguiente**.  
  
5.  Ver información acerca de la solución. Seleccione **importar**.  
  
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

