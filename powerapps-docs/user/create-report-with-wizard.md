---
title: Crear un informe mediante el Asistente para informes | Microsoft Docs
description: Crear un informe mediante el Asistente para informes en Power apps
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733269"
---
# <a name="create-a-report-using-the-report-wizard"></a>Creación de los informes mediante el Asistente para informes


Use el Asistente para informes para crear informes con gráficos y tablas que le permitan analizar fácilmente los datos. 

Todos los informes que se crean mediante el Asistente para informes son informes basados en Fetch. Tenga en cuenta que todos los informes generados con el Asistente para informes se imprimen en modo horizontal.

## <a name="create-a-new-report"></a>Crear un informe nuevo

1. En el panel de navegación izquierdo, seleccione el área informes.  
2. En la barra de comandos, seleccione **nuevo**.

    > [!div class="mx-imgBorder"]
    > ![Crear un nuevo informe](media/newreport.png "Crear un informe nuevo")
  
3. Un **Informe:** aparecerá la pantalla nuevo informe. En **tipo de informe** , deje la selección predeterminada en, **Informe del Asistente para informes** y seleccione el botón **Asistente para informes** . 

    > [!div class="mx-imgBorder"]
    > ![Asistente para informes](media/report_wizard.png "Pantalla del Asistente para informes")
  
4. En la siguiente pantalla, deje las selecciones predeterminadas y, a continuación, seleccione **siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![Asistente para informes](media/report_wizard_1.png "Pantalla del Asistente para informes")
   
4. En la pantalla **propiedades del informe** , escriba un nombre para el informe y, a continuación, elija el registro que desea incluir en el informe y, a continuación, seleccione **siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![Pantalla propiedades del informe](media/report_wizard_2.png "Pantalla propiedades del informe")
  
5.  En la pantalla **seleccionar los registros que se van a incluir en el informe** , elija los filtros para determinar qué registros se incluyen en el informe. Por ejemplo, si solo desea ver los resultados de los registros modificados en los últimos 60 días, puede establecer ese filtro en esta pantalla. Si no desea filtrar los datos, seleccione **Borrar**.

    > [!div class="mx-imgBorder"]
    > ![Seleccionar los registros que se van a incluir en el informe *](media/report_wizard_3.png "Seleccionar los registros que se van a incluir en el informe")
  
6. En la pantalla **diseñar campos** , elija el diseño del informe. Seleccione **haga clic aquí para agregar una agrupación** y elija cómo desea agrupar los datos.

    > [!div class="mx-imgBorder"]
    > ![Disposición de los campos](media/report_wizard_4.png "Disposición de los campos")

7. Seleccione el **tipo de registro** y la **columna** de los datos que desea que se agrupen en el informe. Cuando haya terminado de realizar las selecciones, haga clic en **Aceptar**.

    > [!div class="mx-imgBorder"]
    > ![pantalla de agrupación de DD](media/report_wizard_5.png "Agregar pantalla de agrupación")
  
8. Seleccione **haga clic aquí para agregar una columna** a las columnas de datos relacionadas con el tipo de registro que eligió en el paso anterior.  

    > [!div class="mx-imgBorder"]
    > ![Agregar pantalla de agrupación](media/report_wizard_6.png "Agregar pantalla de agrupación")

9. En la pantalla **Agregar columna** , elija los datos que desea que aparezcan para la columna y, a continuación, seleccione **Aceptar**. 

    > [!div class="mx-imgBorder"]
    > ![pantalla agregar columna](media/report_wizard_7.png "Pantalla agregar columna")
  
10. Repita el paso anterior para las columnas adicionales que desee agregar. Cuando haya terminado, en la pantalla **diseñar campos** , seleccione **siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![pantalla agregar más columna](media/report_wizard_8.png "Pantalla agregar más columna")
  
11. En la pantalla **formato de informe** , elija cómo desea dar formato a un informe y, a continuación, seleccione **siguiente**.
 
    > [!div class="mx-imgBorder"]
    > ![Formato de informe](media/report_wizard_9.png "Pantalla de formato de informe")

12. Revise el resumen del informe y seleccione **siguiente** y, a continuación, seleccione **Finalizar**. Ahora puede ver este informe en la lista de informes del sistema.

    > [!div class="mx-imgBorder"]
    > ![Ver el informe](media/report_wizard_10.png "Ver el informe")

### <a name="see-also"></a>Vea también
[Trabajar con informes](work-with-reports.md) 

[Agregar un informe existente](add-existing-report.md)

[Editar filtro de informe](edit-report-filter.md)

[Solucionar problemas de datos que no se muestran en un informe](troubleshoot-reports.md)


