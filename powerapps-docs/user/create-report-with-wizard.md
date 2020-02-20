---
title: Creación de un informe mediante el Asistente para informes | Microsoft Docs
description: Creación de un informe mediante el Asistente para informes en Power Apps
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8c7bde8d3aa5406a7ddcc5ecb2df4c2c7db7051e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733269"
---
# <a name="create-a-report-using-the-report-wizard"></a>Creación de los informes mediante el Asistente para informes


Use el Asistente para informes para crear informes con gráficos y tablas que le permitan analizar fácilmente los datos. 

Todos los informes que se crean mediante el Asistente para informes están basados en Fetch. Tenga en cuenta que todos los informes generados con el Asistente para informes se imprimen en modo horizontal.

## <a name="create-a-new-report"></a>Creación de un informe nuevo.

1. En el panel de navegación izquierdo, seleccione el área de informes.  
2. En la barra de comandos, seleccione **Nuevo**.

    > [!div class="mx-imgBorder"]
    > ![Creación de un informe](media/newreport.png "Creación de un informe nuevo.")
  
3. Aparecerá la pantalla **Informe: nuevo informe**. En **Tipo de informe**, deje la selección predeterminada **Informe del Asistente para informes** y seleccione el botón **Asistente para informes**. 

    > [!div class="mx-imgBorder"]
    > ![Asistente para informes](media/report_wizard.png "Pantalla del Asistente para informes")
  
4. En la siguiente pantalla, deje las selecciones predeterminadas y luego seleccione **Siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![Asistente para informes](media/report_wizard_1.png "Pantalla del Asistente para informes")
   
4. En la pantalla **Propiedades del informe**, escriba el nombre del informe, elija el registro que quiera incluir en el informe y después seleccione **Siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![Pantalla de propiedades del informe](media/report_wizard_2.png "Pantalla de propiedades del informe")
  
5.  En la pantalla **Seleccionar registros para incluir en el informe**, elija los filtros para determinar qué registros se incluyen en el informe. Por ejemplo, si solo quiere ver los resultados de los registros modificados en los últimos 60 días, puede establecer ese filtro en esta pantalla. Si no quiere filtrar los datos, seleccione **Borrar**.

    > [!div class="mx-imgBorder"]
    > ![Seleccionar registros para incluir en el informe*](media/report_wizard_3.png "Seleccionar registros para incluir en el informe")
  
6. En la pantalla **Campos de diseño**, elija el diseño del informe. Seleccione **Haga clic aquí para agregar una agrupación** y elija cómo quiere agrupar los datos.

    > [!div class="mx-imgBorder"]
    > ![Campos de diseño](media/report_wizard_4.png "Campos de diseño")

7. Seleccione el **tipo de registro** y la **columna** de los datos que quiera que se agrupen en el informe. Cuando haya terminado con las selecciones, elija **Aceptar**.

    > [!div class="mx-imgBorder"]
    > ![Pantalla de adición de grupo](media/report_wizard_5.png "Pantalla de adición de grupo")
  
8. Seleccione **Haga clic aquí para agregar una columna** en las columnas de datos relacionados con el tipo de registro que ha elegido en el paso anterior.  

    > [!div class="mx-imgBorder"]
    > ![Pantalla de adición de grupo](media/report_wizard_6.png "Pantalla de adición de grupo")

9. En la pantalla **Agregar columna**, elija los datos que quiera que se muestren en la columna y luego seleccione **Aceptar**. 

    > [!div class="mx-imgBorder"]
    > ![Pantalla de adición de columna](media/report_wizard_7.png "Pantalla de adición de columna")
  
10. Repita el paso anterior con todas las columnas adicionales que quiera agregar. Cuando haya terminado, en la pantalla **Campos de diseño**, seleccione **Siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![Pantalla de adición de más columnas](media/report_wizard_8.png "Pantalla de adición de más columnas")
  
11. En la pantalla **Dar formato al informe**, elija qué formato quiere aplicar y después seleccione **Siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![Dar formato al informe](media/report_wizard_9.png "Pantalla para dar formato al informe")

12. Revise el resumen del informe, seleccione **Siguiente** y, después, **Finalizar**. Ya puede ver este informe en la lista de informes del sistema.

    > [!div class="mx-imgBorder"]
    > ![Visualización del informe](media/report_wizard_10.png "Visualización del informe")

### <a name="see-also"></a>Vea también
[Trabajo con los informes](work-with-reports.md) 

[Adición de un informe existente](add-existing-report.md)

[Edición del filtro de informe](edit-report-filter.md)

[Solución de problemas de datos que no se muestran en un informe](troubleshoot-reports.md)


