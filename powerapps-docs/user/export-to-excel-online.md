---
title: Exportar los datos a Excel online en una aplicación controlada por modelos | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 6cb8fe650db464f41c63af87c3fcb34bb2203cf2
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544796"
---
# <a name="export-your-data-to-excel-online"></a>Exportar los datos a Excel online 

Puede realizar rápidamente un análisis ad hoc de los datos que se encuentra en la aplicación mediante la exportación de los datos de la aplicación a Excel online.
  
Cuando realice cambios en los datos en Excel online, puede guardar la información actualizada en la aplicación. Recuerde mantener el formato existente de las celdas de Excel para evitar problemas durante la importación. Cualquier información que se agregue a la hoja de cálculo, como gráficos, gráficos o colores, no se guardará.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
- Esta característica requiere que tenga una suscripción a Office 365 o una suscripción a un servicio en línea como SharePoint Online o Exchange Online.
  
- Necesita una cuenta de Microsoft.    
  
## <a name="open-app-data-in-excel-online"></a>Abrir datos de la aplicación en Excel online  

La opción para abrir datos en Excel online no está disponible en todos los tipos de registro. Si no ve la opción, no está disponible para ese registro.  
  
> [!NOTE]
> Los datos actualizados en una aplicación no se reflejarán inmediatamente en Excel online si la misma vista se abrió en los últimos dos minutos en Excel online. Después de ese período de tiempo, los datos actualizados deben mostrarse en Excel online.
  
Para abrir una lista de registros en una aplicación, en la barra de comandos Seleccione el menú **exportar a Excel** y, a continuación, seleccione **abrir en Excel online**. 

> [!div class="mx-imgBorder"] 
> ![Exportar a Excel online](media/exportexcelonline.png "Exportar a Excel online")  

  
## <a name="save-your-data-and-import-it-back-to-the-app"></a>Guardar los datos e importarlos de nuevo a la aplicación  
  
1. Cuando haya terminado de realizar los cambios, seleccione **Guardar**.  
  
   > [!NOTE]
   > - Los datos para el análisis *ad hoc* con Excel online se almacenan de forma temporal. Cualquier adición, como gráficos, cálculos y columnas, no se guardará en la aplicación desde el análisis ad hoc en Excel online.  
   > 
   > - Es posible que se produzca un error en la importación de archivos si realiza muchos cambios. Si tiene que realizar muchos cambios en los datos y volver a importarlos en la aplicación, se recomienda que exporte la hoja de cálculo en Excel en su lugar.  
   > 
   > - Por diseño, no se puede guardar un **archivo** > **como** en Excel online. Si lo hace, obtendrá un mensaje de error **no se puede guardar el libro** .   
2. En el cuadro de diálogo **datos enviados para importar** , seleccione **cerrar**.  
  

  

 
