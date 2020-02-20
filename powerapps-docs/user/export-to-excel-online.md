---
title: Exportación de datos a Excel Online en una aplicación basada en modelos | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544796"
---
# <a name="export-your-data-to-excel-online"></a>Exportación de datos a Excel Online 

Para realizar rápidamente un análisis ad hoc de los datos que están en la aplicación, puede exportar esos datos a Excel Online.
  
Cuando haga cambios en los datos en Excel Online, puede guardar esa información actualizada en la aplicación. Recuerde mantener el formato existente de las celdas de Excel para evitar problemas durante la importación. Cualquier información que se agregue a la hoja de cálculo (como gráficos o colores) no se guardará.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
- Esta característica requiere que tenga una suscripción a Office 365 o una suscripción a un servicio en línea como SharePoint Online o Exchange Online.
  
- Necesita una cuenta de Microsoft.    
  
## <a name="open-app-data-in-excel-online"></a>Abrir datos de la aplicación en Excel Online  

La opción para abrir datos en Excel Online no está disponible en todos los tipos de registro. Si no la ve, quiere decir que no está disponible para ese registro.  
  
> [!NOTE]
> Los datos actualizados de una aplicación no se reflejarán inmediatamente en Excel Online si la misma vista se abrió en los últimos dos minutos en Excel Online. Transcurrido ese tiempo, los datos actualizados sí deben aparecer en Excel Online.
  
Para abrir una lista de registros de una aplicación, seleccione el menú **Exportar a Excel** en la barra de comandos y, después, seleccione **Abrir en Excel Online**. 

> [!div class="mx-imgBorder"] 
> ![Exportar a Excel Online](media/exportexcelonline.png "Export to Excel Online")  

  
## <a name="save-your-data-and-import-it-back-to-the-app"></a>Guardar los datos e importarlos de nuevo a la aplicación  
  
1. Cuando haya terminado de realizar los cambios, seleccione **Guardar**.  
  
   > [!NOTE]
   > - Los datos seleccionados para el análisis *ad hoc* con Excel Online se almacenan de forma temporal. Ninguna de las adiciones que se haga (como gráficos, cálculos y columnas) se guardará en la aplicación desde el análisis ad hoc en Excel Online.  
   > 
   > - Si se hacen muchos cambios, es posible que el archivo no pueda importarse. Si tiene que realizar muchos cambios en los datos y volver a importarlos a la aplicación, se recomienda exportar la hoja de cálculo a Excel en su lugar.  
   > 
   > - Por su diseño, Excel Online no permite usar las opciones **Archivo** > **Guardar como**. Si lo hace, aparecerá un mensaje de error **No se puede guardar el libro**.   
2. En el cuadro de diálogo **Datos enviados para la importación**, seleccione **Cerrar**.  
  

  

 
