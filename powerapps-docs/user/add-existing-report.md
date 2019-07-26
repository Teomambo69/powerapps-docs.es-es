---
title: Agregar un informe desde fuera de PowerApps | Microsoft Docs
description: Agregar un informe desde fuera de PowerApps
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
ms.openlocfilehash: 24faa77b454cf3324e4b7277c94c6cd364aec9a9
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420177"
---
# <a name="add-a-report-from-outside-powerapps"></a>Agregar un informe desde fuera de PowerApps

Si ha creado un informe personalizado fuera del sistema, puede agregarlo fácilmente a PowerApps.

Para obtener información sobre cómo crear un informe personalizado, consulte la [Guía de informes y análisis](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/analytics/get-started-writing-reports).

1. En el panel de navegación izquierdo, seleccione el área informes. 
2. En la barra de comandos, seleccione **nuevo**.
  
   **Agregar un archivo creado en otra aplicación**  
  
   1. En la sección **origen** , en el cuadro **tipo de informe** , seleccione **archivo existente**.  
   
     > [!div class="mx-imgBorder"]
     > ![Agregar un informe existente](media/add_existing_report.png "Agregar un informe existente")
  
   2. En el cuadro **Ubicación del archivo** , escriba la ruta de acceso y el nombre del archivo que desea agregar, o elija **examinar** para buscar el archivo. 
   
      Puede cargar muchos otros tipos de archivo, como un archivo de Excel, pero para que se ejecute como un informe SQL Server Reporting Services informe o un asistente para informes creado, el archivo debe ser un. Archivo RDL. Para obtener más información, vea [entorno de escritura de informes mediante SQL Server Data Tools](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools).
  
      O BIEN  
  
   **Agregar un vínculo a una página web**  
  
   1.  En la sección **origen** , en el cuadro **tipo de informe** , seleccione vincular **a página web**.  
  
   2.  En el cuadro **dirección URL de la página web** , escriba la dirección URL de la Página Web.  
  
3. Especifique las propiedades del informe.
  
   1.  En la sección de **detalles** , especifique un nombre descriptivo y una descripción para el informe.  
  
   2.  El cuadro de texto **Informe primario** muestra el informe primario del informe actual, si existe.  
  
   3. **Categorías**. Elija el botón de botón de puntos(media/ellipsis-button.png "suspensivos") del ![botón]de puntos suspensivos **para este campo** y, a continuación, especifique las categorías que desea incluir en este informe.  
  
   4. **Tipos de registro relacionados**. Para que el informe aparezca en la lista de informes en una página para tipos de registros específicos, elija el botón de puntos suspensivos del botón de puntos ![](media/ellipsis-button.png "suspensivos") de los puntos suspensivos **para este campo** y, a continuación, seleccione tipos de registro.  
  
   5. **Mostrar en**. Para especificar dónde deben estar visibles los informes, elija el botón de puntos suspensivos de los puntos suspensivos del ![botón](media/ellipsis-button.png "") **seleccionar o cambiar los valores de este campo** y, a continuación, seleccione una o varias de las opciones.  
  
        Si no se selecciona ningún valor, el informe no será visible para los usuarios finales.  
  
4. Elija **Guardar** o **Guardar y cerrar**.  




### <a name="see-also"></a>Vea también
[Trabajar con informes](work-with-reports.md) 

[Crear un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Editar filtro de informe](edit-report-filter.md)

[Solucionar problemas de datos que no se muestran en un informe](troubleshoot-reports.md)
