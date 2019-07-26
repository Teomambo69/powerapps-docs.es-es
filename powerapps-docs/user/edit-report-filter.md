---
title: Editar el filtro predeterminado de un informe | Microsoft Docs
description: Edición del filtro predeterminado de un informe
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
ms.openlocfilehash: 53e4f2fc61bb72b4c3fc6fed188b513641c2034d
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420223"
---
# <a name="edit-the-default-filter-of-a-report"></a>Edición del filtro predeterminado de un informe

Cuando un informe es un informe de SQL Server Reporting Services, está habilitado para la prefiltrado y tiene un filtro predeterminado, puede cambiar el filtro predeterminado para mostrar los datos que espera ver en el informe. Este filtro se utiliza cada vez que un usuario ejecuta el informe.

1. En el panel de navegación izquierdo, seleccione el área informes.
2. Elija un informe y, en la barra commbar, seleccione **Editar filtro predeterminado**.

     > [!div class="mx-imgBorder"]
     > ![Editar filtro de informe predeterminado](media/edit_filter.png "Editar filtro de informe predeterminado")
  
3. Modifique los criterios de filtro.  
  
   Los criterios se agrupan por tipos de registros que se pueden usar en el filtro, como **cuentas** o **contactos**.  
  
   ### <a name="to-edit-an-existing-row"></a>Para editar una fila existente
   1. Seleccione el operador relacional consulta y seleccione un operador o seleccione el valor subrayado y escriba un nuevo valor.  
  
   2. Seleccione el operador relacional consulta y seleccione un operador.  
  
   Para agregar una fila de criterios:  

   1.  Seleccione **seleccionar**y especifique el campo por el que desea filtrar.  

   2.  Seleccione el operador relacional consulta y seleccione un operador.  

   3.  Seleccione **escribir valor**y escriba un valor por el que filtrar. En el caso de algunos valores, puede seleccionar el botón de puntos suspensivos de botón de ![puntos suspensivos](media/ellipsis-button.png "") **de botón de un campo** para abrir el cuadro de diálogo seleccionar **valores** y seleccionar el valor que desee.  

   ### <a name="to-group-criteria"></a>Para agrupar criterios
   Debe seleccionar dos o más filas para el mismo tipo de registro. Sin embargo, no se pueden agrupar las filas con valores de campo de diferentes tipos de registros, como los tipos de registro de **cuentas** y de **contactos** .  

   1.  Para cada fila que desee agrupar, en el modo detallado, seleccione el botón de **menú opciones** para esa fila y, a continuación, elija **seleccionar fila**.  

   2.  En la barra de herramientas del filtro, seleccione **Grupo** , o **grupo o**.  

   3.  Para quitar una fila de un grupo, seleccione el botón de **menú opciones** de esa fila y, a continuación, seleccione **eliminar**.  

   4.  Para seleccionar un grupo, seleccione el botón de **menú opciones** para ese grupo y, a continuación, seleccione **Seleccionar grupo**.  

   5.  Para agregar una cláusula de criterios a un grupo, seleccione el botón de **menú opciones** para ese grupo, seleccione **Agregar cláusula**y, a continuación, seleccione el campo, el operador relacional de consulta y el valor.  

   6.  Para anular la selección de un grupo que se ha seleccionado previamente, seleccione el botón de **menú opciones** para ese grupo y, a continuación, seleccione anular **la selección del grupo**.  

   7.  Para desagrupar un grupo, seleccione el botón de **menú opciones** para ese grupo y, a continuación, seleccione Desagrupar.  

   8.  Para cambiar un **grupo y** un grupo a un grupo **o** grupo, o un **grupo o** grupo a un grupo **y** grupo, seleccione el botón de **menú opciones** para ese grupo y, a continuación, seleccione **cambiar a o** o **cambiar a y**.  

   > [!TIP]
   > - Para borrar todos los criterios y volver a empezar, en la barra de herramientas del filtro, seleccione **Borrar**y, a continuación, seleccione **confirmar**.  
   > - Para eliminar una fila, seleccione el botón de **menú opciones** de esa fila y, a continuación, seleccione **eliminar**.  
  
4. Cuando haya terminado, seleccione **Guardar filtro predeterminado**.



### <a name="see-also"></a>Vea también
[Trabajar con informes](work-with-reports.md) 

[Crear un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Agregar un informe existente](add-existing-report.md)

[Solucionar problemas de datos que no se muestran en un informe](troubleshoot-reports.md)

