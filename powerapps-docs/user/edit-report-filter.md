---
title: Edición del filtro predeterminado de un informe | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420223"
---
# <a name="edit-the-default-filter-of-a-report"></a>Edición del filtro predeterminado de un informe

Si se trata de un informe de SQL Server Reporting Services que está habilitado para el filtrado previo y tiene un filtro predeterminado, puede cambiar el filtro predeterminado para mostrar los datos que espera ver en el informe. Este filtro se usa cada vez que un usuario ejecuta el informe.

1. En el panel de navegación izquierdo, seleccione el área de informes.
2. Elija un informe y, en la barra de comandos, seleccione **Editar filtro predeterminado**.

     > [!div class="mx-imgBorder"]
     > ![Edición del filtro de informe predeterminado](media/edit_filter.png "Edit default report filter")
  
3. Modifique los criterios del filtro.  
  
   Los criterios se agrupan por tipos de registros que puede usar en el filtro, como **Cuentas** o **Contactos**.  
  
   ### <a name="to-edit-an-existing-row"></a>Para editar una fila existente
   1. Seleccione el operador relacional de consulta y elija un operador, o bien seleccione el valor subrayado y escriba un nuevo valor.  
  
   2. Seleccione el operador relacional de consulta y elija un operador.  
  
   Para agregar una fila de criterios:  

   1.  Elija **Seleccionar** y especifique el campo por el que quiere filtrar.  

   2.  Seleccione el operador relacional de consulta y elija un operador.  

   3.  Seleccione **Escribir valor** y escriba un valor por el que filtrar. En el caso de algunos valores, puede seleccionar el botón **Seleccione o cambie los valores de este campo** ![Botón de puntos suspensivos](media/ellipsis-button.png "Botón de puntos suspensivos") para abrir el cuadro de diálogo **Seleccionar valores** y seleccionar el valor que quiera.  

   ### <a name="to-group-criteria"></a>Para agrupar criterios
   Debe seleccionar dos o más filas del mismo tipo de registro, pero no puede agrupar filas con valores de campo de diferentes tipos de registros (como **Cuenta** y **Contactos**).  

   1.  Para cada fila que quiera agrupar, en el modo detallado, seleccione el botón **Menú de opciones** de esa fila y después elija **Seleccionar fila**.  

   2.  En la barra de herramientas del filtro, seleccione **Agrupar con Y** o **Agrupar con O**.  

   3.  Para quitar una fila de un grupo, seleccione el botón **Menú de opciones** de la fila y después **Eliminar**.  

   4.  Para seleccionar un grupo, elija el botón **Menú de opciones** de ese grupo y después **Seleccionar grupo**.  

   5.  Para agregar una cláusula de criterios a un grupo, seleccione el botón **Menú de opciones** de ese grupo, elija **Agregar cláusula** y después seleccione el campo, el operador relacional de consulta y el valor.  

   6.  Para anular la selección de un grupo que ha seleccionado previamente, elija el botón **Menú de opciones** de ese grupo y después **Cancelar selección de grupo**.  

   7.  Para desagrupar un grupo, seleccione el botón **Menú de opciones** de ese grupo y después **Desagrupar**.  

   8.  Para cambiar un grupo de **Agrupar con Y** a uno de **Agrupar con O**, o bien un grupo de **Agrupar con O** a uno de **Agrupar con Y**, seleccione el botón **Menú de opciones** de ese grupo y después **Cambiar a O** o **Cambiar a Y**.  

   > [!TIP]
   > - Para borrar todos los criterios y empezar de cero, en la barra de herramientas del filtro, seleccione **Borrar** y luego **Confirmar**.  
   > - Para eliminar una fila, seleccione el botón **Menú de opciones** de la fila y después **Eliminar**.  
  
4. Cuando termine, seleccione **Guardar filtro predeterminado**.



### <a name="see-also"></a>Vea también
[Trabajo con los informes](work-with-reports.md) 

[Creación de un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Adición de un informe existente](add-existing-report.md)

[Solución de problemas de datos que no se muestran en un informe](troubleshoot-reports.md)

