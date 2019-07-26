---
title: Exportar a una tabla dinámica de Excel en PowerApp controlado por modelos | MicrosoftDocs
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
ms.openlocfilehash: 90cf377f10a99dbcece1e5f556cb50e678099744
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544991"
---
# <a name="export-to-an-excel-pivottable"></a>Exportar a una tabla dinámica de Excel


Puede exportar los datos de la aplicación a una tabla dinámica de Office Excel para ver los patrones y las tendencias de los datos. Una tabla dinámica de Excel es una excelente manera de resumir, analizar, explorar y presentar los datos de la aplicación. Puede exportar hasta 100.000 registros a la vez.  
  

## <a name="export-data-to-an-excel-pivottable"></a>Exportar datos a una tabla dinámica de Excel  
La opción para exportar datos a una tabla dinámica de Excel no está disponible en todos los tipos de registro. Si no ve la opción, no está disponible para ese registro.  
  
1. Abra una lista de registros de la aplicación, seleccione la flecha situada a la derecha de **exportar a Excel**y, a continuación, seleccione **tabla dinámica**dinámica.  
  
2. En el cuadro de diálogo **seleccionar columnas para Excel dinámico** , seleccione la configuración de la columna y, a continuación, seleccione **exportar**.  
  
   De forma predeterminada, la **lista de campos de tabla dinámica** solo incluye los campos que se muestran en la lista **seleccionar columnas para Excel dinámicas** .  
  
3. Seleccione **Guardar** y, a continuación, guarde el archivo. xlsx. Anote la ubicación en la que guardó el archivo.  
  
   > [!NOTE]
   > Si va a editar el archivo de datos más adelante, se recomienda que guarde el archivo antes de abrirlo. De lo contrario, podría obtener este mensaje de error: **Excel no puede abrir o guardar más documentos porque no hay suficiente memoria disponible o espacio en disco.**  
   > 
   > Para solucionar el problema:  
   > 
   > 1. Abra Excel y vaya a **File** > **Options** > **Trust Center**.  
   > 2. Seleccione **configuración del centro de confianza** y, a continuación, **vista protegida**.  
   > 3. En **vista protegida**, desactive las casillas de los tres elementos.  
   > 4. Seleccione **Aceptar** > **Aceptar**.  
   > 
   > Todavía se recomienda encarecidamente guardar y abrir el archivo de datos en lugar de deshabilitar la vista protegida, lo que podría poner el equipo en riesgo.  
  
4. Abra Excel y, a continuación, abra el archivo. xlsx que guardó en el paso anterior.  
  
5. Si ve la advertencia de seguridad **se han deshabilitado las conexiones de datos externos**, seleccione **Habilitar contenido**.  
  
6. Para actualizar los datos del archivo, en la pestaña **datos** , seleccione **actualizar desde PowerApps**.  
  
7. Arrastre los campos de la lista de campos de la tabla dinámica a la tabla dinámica. Para obtener más información, vea la ayuda de Excel.  
  
## <a name="tips"></a>Recomendaciones  
  
- En PowerApps, los valores de moneda se exportan a Excel como números. Después de completar la exportación, vea el tema de ayuda de Excel "Mostrar números como moneda" para dar formato de moneda a los datos.
  
- Los valores de fecha y hora que se ven en la aplicación solo se muestran como fecha al exportar el archivo a Excel, pero la celda realmente muestra la fecha y la hora.  
  
- Si va a realizar cambios y vuelve a importar el archivo de datos en la aplicación, recuerde que los campos seguros, calculados y compuestos (como el nombre completo) son de solo lectura y no se pueden importar en la aplicación. Podrá editar estos campos en Excel, pero al importar los datos de nuevo en la aplicación, estos campos no se actualizarán. Si desea actualizar estos campos, como el nombre de un contacto, se recomienda que use esa vista para exportar los datos, actualizarlos en Excel y volver a importarlos en la aplicación para los cambios.  
  
 
