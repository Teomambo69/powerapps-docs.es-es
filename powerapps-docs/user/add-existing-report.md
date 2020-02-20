---
title: Adición de un informe desde fuera de Power Apps | Microsoft Docs
description: Adición de un informe desde fuera de Power Apps
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
ms.openlocfilehash: e730d498a4d82518d0f908645e26a541c1e8c6af
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725852"
---
# <a name="add-a-report-from-outside-power-apps"></a>Adición de un informe desde fuera de Power Apps

Si ha creado un informe personalizado fuera del sistema, puede agregarlo fácilmente a Power Apps.

Para obtener información sobre cómo crear un informe personalizado, vea [Guía de informes y análisis](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/get-started-writing-reports).

1. En el panel de navegación izquierdo, seleccione el área de informes. 
2. En la barra de comandos, seleccione **Nuevo**.
  
   **Adición de un archivo creado en otra aplicación**  
  
   1. En la sección **Origen**, en el cuadro **Tipo de informe**, seleccione **Archivo existente**.  
   
     > [!div class="mx-imgBorder"]
     > ![Adición de un informe existente](media/add_existing_report.png "Adición de un informe existente")
  
   2. En el cuadro **Ubicación del archivo**, escriba la ruta de acceso y el nombre del archivo que quiera agregar, o bien elija **Examinar** para buscar el archivo. 
   
      Puede cargar muchos otros tipos de archivo, como un archivo de Excel, pero para que se ejecute como un informe de SQL Server Reporting Services o un informe creado en el Asistente para informes, debe tratarse de un archivo .RDL. Para obtener más información, vea [Entorno de escritura de informes usando SQL Server Data Tools](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools).
  
      O BIEN  
  
   **Adición de un vínculo a una página web**  
  
   1.  En la sección **Origen**, en el cuadro **Tipo de informe**, seleccione **Vincular a página web**.  
  
   2.  En el cuadro **URL de la página web**, escriba la URL de la página web.  
  
3. Especifique las propiedades del informe.
  
   1.  En la sección **Detalles**, especifique el nombre descriptivo y la descripción del informe.  
  
   2.  En el cuadro de texto **Informe primario** se muestra el informe primario del informe actual, de haberlo.  
  
   3. **Categorías**. Elija el botón **Seleccione o cambie los valores de este campo** ![Botón de puntos suspensivos](media/ellipsis-button.png "Botón de puntos suspensivos") y después especifique las categorías que quiera incluir en este informe.  
  
   4. **Tipos de registro relacionados**. Para que el informe aparezca en la lista de informes de una página de tipos de registros específicos, elija el botón **Seleccione o cambie los valores de este campo** ![Botón de puntos suspensivos](media/ellipsis-button.png "Botón de puntos suspensivos") y después seleccione los tipos de registro.  
  
   5. **Mostrar en**. Para especificar dónde deben aparecer los informes, elija el botón **Seleccione o cambie los valores de este campo** ![Botón de puntos suspensivos](media/ellipsis-button.png "Botón de puntos suspensivos") y después seleccione una o varias de las opciones.  
  
        Si no se selecciona ningún valor, los usuarios finales no podrán ver el informe.  
  
4. Elija **Guardar** o **Guardar y cerrar**.  




### <a name="see-also"></a>Vea también
[Trabajo con los informes](work-with-reports.md) 

[Creación de un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Edición del filtro de informe](edit-report-filter.md)

[Solución de problemas de datos que no se muestran en un informe](troubleshoot-reports.md)
