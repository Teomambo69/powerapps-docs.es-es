---
title: Exportación a una tabla dinámica de Excel en una aplicación de Power Apps basada en modelos | Microsoft Docs
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
ms.openlocfilehash: b14e24e7048e4f91de13f582914ffb621d3c7899
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725795"
---
# <a name="export-to-an-excel-pivottable"></a>Exportar a una tabla dinámica de Excel


Los datos de la aplicación se pueden exportar a una tabla dinámica de Office Excel para ver patrones y tendencias en los datos. Una tabla dinámica de Excel es una excelente manera de resumir, analizar, explorar y presentar los datos de la aplicación. Se pueden exportar hasta 100 000 registros a la vez.  
  

## <a name="export-data-to-an-excel-pivottable"></a>Exportación de datos a una tabla dinámica de Excel  
La opción para exportar datos a una tabla dinámica de Excel no está disponible en todos los tipos de registro. Si no ve la opción, quiere decir que no está disponible para ese registro.  
  
1. Abra una lista de registros de la aplicación, seleccione la flecha situada a la derecha de **Exportar a Excel** y, después, seleccione **Tabla dinámica**.  
  
2. En el cuadro de diálogo **Seleccionar columnas para tabla dinámica de Excel**, seleccione la configuración de columna y, después, seleccione **Exportar**.  
  
   La **Lista de campos de tabla dinámica** solo incluye de forma predeterminada los campos que figuran en la lista **Seleccionar columnas para tabla dinámica de Excel**.  
  
3. Seleccione **Guardar** y guarde el archivo .xlsx. Anote la ubicación en la que guarde el archivo.  
  
   > [!NOTE]
   > Si va a editar el archivo de datos más adelante, se recomienda guardar el archivo antes de abrirlo. De lo contrario, podría aparecer este mensaje de error: **Excel no puede abrir o guardar más documentos porque el espacio en disco o la memoria son insuficientes.**  
   > 
   > Para solucionar el problema:  
   > 
   > 1. Abra Excel y vaya a **Archivo** > **Opciones** > **Centro de confianza**.  
   > 2. Seleccione **Configuración del Centro de confianza** y, después, seleccione **Vista protegida**.  
   > 3. En **Vista protegida**, desactive las casillas de los tres elementos.  
   > 4. Seleccione **Aceptar** > **Aceptar**.  
   > 
   > Seguimos recomendando encarecidamente guardar y abrir el archivo de datos en lugar de deshabilitar la vista protegida, ya que esto podría poner el equipo en riesgo.  
  
4. Abra Excel y, luego, abra el archivo .xlsx que guardó en el paso anterior.  
  
5. Si aparece la advertencia de seguridad **Se han deshabilitado las conexiones de datos externos**, seleccione **Habilitar contenido**.  
  
6. Para actualizar los datos del archivo, seleccione **Actualizar desde Power Apps** en la pestaña **Datos**.  
  
7. Arrastre campos desde la lista de campos de tabla dinámica a la tabla dinámica. Para obtener más información, vea la Ayuda de Excel.  
  
## <a name="tips"></a>Recomendaciones  
  
- En Power Apps, los valores de moneda se exportan a Excel como números. Una vez completada la exportación, vea el tema de la Ayuda de Excel "Mostrar números como moneda" para dar formato de moneda a los datos.
  
- Los valores de fecha y hora que se ven en la aplicación solo se muestran como fecha al exportar el archivo a Excel, pero la celda realmente muestra la fecha y la hora.  
  
- Si va a realizar cambios y a volver a importar el archivo de datos a la aplicación, recuerde que los campos protegidos, calculados y compuestos (como Nombre completo, por ejemplo) son de solo lectura y no se pueden importar a la aplicación. Estos campos se podrán editar en Excel, pero al volver a importar los datos a la aplicación, no se actualizarán. Si quiere actualizar estos campos (como, por ejemplo, el nombre de un contacto), se recomienda usar esa vista para exportar los datos, actualizarlos en Excel y volver a importarlos a la aplicación para ver si hay cambios.  
  
 
