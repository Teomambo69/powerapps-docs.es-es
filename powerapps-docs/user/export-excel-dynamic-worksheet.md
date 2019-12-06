---
title: Exportar a una hoja de cálculo dinámica de Excel en Powerapps controlado por modelos | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733239"
---
# <a name="export-to-an-excel-dynamic-worksheet"></a>Exportar a una hoja de cálculo dinámica de Excel

Exporte los datos de la aplicación a una hoja de cálculo de Office Excel para que los usuarios puedan tener la información más reciente. Imagine que el CEO de su empresa obtiene la información crítica que necesitan sin tener que navegar en una aplicación, sino simplemente abrir el vínculo de Excel en el escritorio. Puede exportar hasta 100.000 registros a la vez.    
  
## <a name="export-data-to-an-excel-dynamic-worksheet"></a>Exportar datos a una hoja de cálculo dinámica de Excel  

No puede exportar datos a una hoja de cálculo dinámica de Excel para todos los tipos de registro. Si no ve la opción, no está disponible para ese registro.  
  
1. Abra una lista de registros de la aplicación y seleccione la flecha situada a la derecha de **exportar a Excel**. 
  
2. Seleccione **hoja de cálculo dinámica**.  
  
3. En el cuadro de diálogo **seleccionar columnas para Excel dinámico** , seleccione la configuración de la columna y, a continuación, seleccione **exportar**.  
  
4. Seleccione **Guardar** y, a continuación, guarde el archivo. xlsx. Anote la ubicación en la que guardó el archivo.  
  
   > [!NOTE]
   > Si va a editar el archivo de datos más adelante, se recomienda que guarde el archivo antes de abrirlo. De lo contrario, podría obtener este mensaje de error: **Excel no puede abrir o guardar más documentos porque no hay suficiente memoria disponible o espacio en disco.**  
   > 
   > Para solucionar el problema:  
   > 
   >    1. Abra Excel y vaya a **archivo** > **Opciones** > centro de **confianza** **configuración centro configuración** > **vista protegida**.  
   >    2. En **vista protegida**, desactive los tres elementos.  
   >    3. Seleccione **Aceptar** > **Aceptar**.  
   >     
   >    Todavía se recomienda encarecidamente guardar y abrir el archivo de datos en lugar de deshabilitar la vista protegida, lo que podría poner el equipo en riesgo.  
  
5. Abra Excel y, a continuación, abra el archivo. xlsx que guardó en el paso anterior.  
  
6. Si ve la advertencia de seguridad **se han deshabilitado las conexiones de datos externos**, seleccione **Habilitar contenido**.  
  
7. Para actualizar los datos del archivo, en la pestaña **datos** , seleccione **actualizar desde Power apps**.  
  
   > [!NOTE]
   > Si tiene un número de teléfono que empieza por **+** o **(por ejemplo, +** 1-123-456-7890), al actualizar la hoja de cálculo dinámica, el campo número de teléfono no mostrará el número correctamente.   
   >
   > Para evitar el problema, use un espacio o paréntesis **()** , de la siguiente forma: + 1 123-456-7890 o + 1 (123)-456-7890.  
  
## <a name="tips"></a>Recomendaciones  
  
- Puede enviar por correo electrónico un archivo de Excel dinámico o almacenarlo como un archivo compartido si los destinatarios están en el mismo dominio que usted. Cuando los destinatarios abren el archivo dinámico, verán los datos que tienen permiso para verlos en la aplicación, por lo que los datos que ven pueden ser diferentes de lo que ve.  
  
- Algunas vistas del sistema, como las cuentas: no hay actividades de campaña en los últimos 3 meses, solo se pueden exportar a una hoja de cálculo de Excel estática.  
  
- En Power Apps, los valores de moneda se exportan a Excel como números. Para dar formato a los datos como moneda después de completar la exportación, vea el tema de ayuda de Excel titulado "Mostrar números como moneda".

- Los valores de fecha y hora que se ven en la aplicación solo se muestran como fecha al exportar el archivo a Excel, pero la celda realmente muestra la fecha y la hora.  
  
- Si va a realizar cambios y vuelve a importar el archivo de datos en la aplicación, recuerde que los campos seguros, calculados y compuestos (como el nombre completo) son de solo lectura y no se pueden importar en la aplicación. Podrá editar estos campos en Excel, pero al importar los datos de nuevo en la aplicación, estos campos no se actualizarán. Si desea actualizar estos campos, como el nombre de un contacto, se recomienda que use esa vista para exportar los datos, actualizarlos en Excel y volver a importarlos en la aplicación para ver si hay cambios.  
 

