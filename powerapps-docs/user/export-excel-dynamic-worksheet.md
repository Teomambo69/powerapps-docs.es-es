---
title: Exportación a una hoja de cálculo dinámica de Excel en aplicaciones de Power Apps basadas en modelos | Microsoft Docs
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
ms.openlocfilehash: 99aa4fb38311d51237abba2c56d69e9845ea280f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302872"
---
# <a name="export-to-an-excel-dynamic-worksheet"></a>Exportar a una hoja de cálculo dinámica de Excel

Exporte los datos de la aplicación a una hoja de cálculo de Office Excel para que los usuarios puedan disponer de la información más reciente. Imagine que el CEO de su empresa pueda obtener la información crítica que necesita sin tener que navegar por una aplicación, sino simplemente abriendo un vínculo de Excel en el escritorio. Se pueden exportar hasta 100 000 registros a la vez.    
  
## <a name="export-data-to-an-excel-dynamic-worksheet"></a>Exportación de datos a hojas de cálculo dinámicas de Excel  

No se pueden exportar datos a una hoja de cálculo dinámica de Excel con todos los tipos de registro. Si no ve la opción, quiere decir que no está disponible para ese registro.  
  
1. Abra una lista de registros de la aplicación y seleccione la flecha situada a la derecha de **Exportar a Excel**. 
  
2. Seleccione **Hoja de cálculo dinámica**.  
  
3. En el cuadro de diálogo **Seleccionar columnas para Excel dinámica**, seleccione la configuración de columna y, después, seleccione **Exportar**.  
  
4. Seleccione **Guardar** y luego guarde el archivo .xlsx. Tome nota de la ubicación donde guardó el archivo.  
  
   > [!NOTE]
   > Si va a editar el archivo de datos más adelante, se recomienda guardar el archivo antes de abrirlo. De lo contrario, es posible que reciba este mensaje de error: **Excel no pueden abrir o guardar más documentos porque no hay suficiente memoria o espacio en disco disponible**.  
   > 
   > Para solucionar el problema:  
   > 
   >    1. Abra Excel y vaya a **Archivo** > **Opciones** > **Centro de confianza** **Configuración del Centro de confianza** > **Vista protegida**.  
   >    2. En **Vista protegida**, desactive los tres elementos.  
   >    3. Seleccione **Aceptar** > **Aceptar**.  
   >     
   >    Seguimos recomendando encarecidamente guardar y abrir el archivo de datos en lugar de deshabilitar la vista protegida, ya que esto podría poner el equipo en riesgo.  
  
5. Abra Excel y, luego, abra el archivo .xlsx que guardó en el paso anterior.  
  
6. Si ve la advertencia de seguridad **Se han deshabilitado las conexiones de datos externos**, seleccione **Habilitar contenido**.  
  
7. Para actualizar los datos del archivo, en la pestaña **Datos**, seleccione **Actualizar desde Power Apps**.  
  
   > [!NOTE]
   > Si tiene un número de teléfono que empieza por **+** o por **–** (por ejemplo, +1-123-456-7890), cuando la hoja de cálculo dinámica se actualice, el campo número de teléfono no mostrará el número correctamente.   
   >
   > Para evitar que esto suceda, use un espacio o un paréntesis **()**, así: +1 123-456-7890 o +1 (123)-456-7890.  
  
## <a name="tips"></a>Sugerencias  
  
- Los archivos de Excel dinámicos se pueden enviar por correo electrónico o almacenarse como archivos compartidos si los destinatarios están en el mismo dominio que el suyo. Cuando los destinatarios abran el archivo dinámico, verán los datos que tienen permiso para ver en la aplicación, con lo cual es probable que vean datos distintos a los que usted ve.  
  
- Algunas vistas del sistema, como Cuentas: ninguna actividad de campaña en los 3 últimos meses, solo se pueden exportar a una hoja de cálculo estática de Excel.  
  
- En Power Apps, los valores monetarios se exportan a Excel como números. Para dar formato de moneda a los datos una vez completada la exportación, vea el tema de la Ayuda de Excel "Mostrar números como moneda".

- Los valores de fecha y hora que se ven en la aplicación solo se muestran como fecha al exportar el archivo a Excel, pero la celda realmente muestra la fecha y la hora.  
  
- Si va a realizar cambios y a volver a importar el archivo de datos a la aplicación, recuerde que los campos protegidos, calculados y compuestos (como Nombre completo, por ejemplo) son de solo lectura y no se pueden importar a la aplicación. Estos campos se podrán editar en Excel, pero al volver a importar los datos a la aplicación, no se actualizarán. Si quiere actualizar estos campos (como, por ejemplo, el nombre de un contacto), se recomienda usar esa vista para exportar los datos, actualizarlos en Excel y volver a importarlos a la aplicación para ver si hay cambios.  
 

