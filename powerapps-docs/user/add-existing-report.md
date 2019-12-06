---
title: Agregar un informe desde fuera de las aplicaciones avanzadas | Microsoft Docs
description: Agregar un informe desde fuera de las aplicaciones avanzadas
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725852"
---
# <a name="add-a-report-from-outside-power-apps"></a>Agregar un informe desde fuera de las aplicaciones avanzadas

Si ha creado un informe personalizado fuera del sistema, puede agregarlo fácilmente a Power apps.

Para obtener información sobre cómo crear un informe personalizado, consulte la [Guía de informes y análisis](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/get-started-writing-reports).

1. En el panel de navegación izquierdo, seleccione el área informes. 
2. En la barra de comandos, seleccione **nuevo**.
  
   **Agregar un archivo creado en otra aplicación**  
  
   1. En la sección **origen** , en el cuadro **tipo de informe** , seleccione **archivo existente**.  
   
     > [!div class="mx-imgBorder"]
     > ![Agregar un informe existente](media/add_existing_report.png "Agregar un informe existente")
  
   2. En el cuadro **Ubicación del archivo** , escriba la ruta de acceso y el nombre del archivo que desea agregar, o elija **examinar** para buscar el archivo. 
   
      Puede cargar muchos otros tipos de archivo, como un archivo de Excel, pero para que se ejecute como un informe SQL Server Reporting Services informe o un asistente para informes creado, el archivo debe ser un. Archivo RDL. Para obtener más información, vea [entorno de escritura de informes mediante SQL Server Data Tools](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools).
  
      O bien  
  
   **Agregar un vínculo a una página web**  
  
   1.  En la sección **origen** , en el cuadro **tipo de informe** , seleccione **vincular a página web**.  
  
   2.  En el cuadro **dirección URL de la página web** , escriba la dirección URL de la Página Web.  
  
3. Especifique las propiedades del informe.
  
   1.  En la sección de **detalles** , especifique un nombre descriptivo y una descripción para el informe.  
  
   2.  El cuadro de texto **Informe primario** muestra el informe primario del informe actual, si existe.  
  
   3. **Categorías**. Elija el botón de ![botón de puntos suspensivos](media/ellipsis-button.png "Botón de puntos suspensivos") del **campo seleccionar o cambiar los valores para este campo** y, a continuación, especifique las categorías que desea incluir en este informe.  
  
   4. **Tipos de registro relacionados**. Para que el informe se muestre en la lista de informes de una página para tipos de registros específicos, elija el botón de ![puntos suspensivos](media/ellipsis-button.png "Botón de puntos suspensivos") **de seleccionar o cambiar los valores de este campo** y, a continuación, seleccione tipos de registro.  
  
   5. **Mostrar en**. Para especificar dónde deben estar visibles los informes, elija el botón de ![puntos suspensivos](media/ellipsis-button.png "Botón de puntos suspensivos") **de seleccionar o cambiar los valores de este campo** y, a continuación, seleccione una o varias de las opciones.  
  
        Si no se selecciona ningún valor, el informe no será visible para los usuarios finales.  
  
4. Elija **Guardar** o **Guardar y cerrar**.  




### <a name="see-also"></a>Vea también
[Trabajar con informes](work-with-reports.md) 

[Crear un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Editar filtro de informe](edit-report-filter.md)

[Solucionar problemas de datos que no se muestran en un informe](troubleshoot-reports.md)
