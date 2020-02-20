---
title: Exportación a una hoja de cálculo estática de Excel en una aplicación basada en modelos | Microsoft Docs
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
ms.openlocfilehash: 82d14f70bbdcd9faddc467636db255f0b512830e
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544830"
---
# <a name="export-to-an-excel-static-worksheet"></a>Exportación a una hoja de cálculo estática de Excel

Si quiere presentar información sobre los datos de la aplicación a una persona que no tiene acceso a dicha aplicación, o si tiene datos que no cambian con frecuencia, considere la posibilidad de exportar esos datos de la aplicación a una hoja de cálculo estática de Office Excel.

Se pueden exportar hasta 100 000 registros a la vez. Una aplicación basada en modelos muestra de forma predeterminada un máximo de 50 registros por página. Elija las flechas de **Página** situadas al final de la lista para ver más páginas.  
  
## <a name="export-data-to-an-excel-static-worksheet"></a>Exportación de datos a una hoja de cálculo estática de Excel  
Puede que tenga la opción de exportar datos a una hoja de cálculo estática de Excel en cualquier tipo de registro. Sin embargo, en algunos casos, el formato puede ser heredado, o puede que los datos no se filtren por lo que aparece en la aplicación.  
  
1. Abra una lista de registros de la aplicación, seleccione la flecha situada a la derecha de **Exportar a Excel** y, después, seleccione **Hoja de cálculo estática (solo página)**.  
  
2. Una hoja de cálculo exportada incluye de forma predeterminada los campos que se muestran en la lista, en el mismo orden, clasificación y ancho de campo. Para realizar cambios en las columnas de una vista de búsqueda avanzada, elija **Editar columnas**. 
  
3. Elija **Guardar** y guarde el archivo .xlsx. Anote la ubicación en la que guarde el archivo.  
  
   > [!NOTE]
   > Si va a editar el archivo de datos más adelante, se recomienda guardar el archivo antes de abrirlo. De lo contrario, podría aparecer este mensaje de error: **Excel no puede abrir o guardar más documentos porque el espacio en disco o la memoria son insuficientes.**  
   > 
   > Para solucionar el problema, haga lo siguiente:  
   > 
   > 1. Abra Excel y vaya a **Archivo** > **Opciones** > **Centro de confianza** > **Configuración del Centro de confianza** > **Vista protegida**.  
   > 2.  En **Vista protegida**, desactive los tres elementos.  
   > 3.  Seleccione **Aceptar** > **Aceptar**.  
   > 
   > Seguimos recomendando encarecidamente guardar y abrir el archivo de datos en lugar de deshabilitar la vista protegida, ya que esto podría poner el equipo en riesgo.  


4. Abra Excel y, luego, abra el archivo .xlsx que guardó en el paso anterior.  
  
   Una hoja de cálculo exportada incluye de forma predeterminada los campos que se muestran en la lista, en el mismo orden, clasificación y ancho de campo.  
  
## <a name="tips"></a>Recomendaciones  
  
- Una hoja de cálculo estática exportada se puede enviar por correo electrónico a cualquier persona o almacenarla en un archivo compartido. Cualquier persona que abra el archivo verá todos los datos que hay en él.
  
- No se pueden cambiar las columnas de una vista del sistema, como, por ejemplo, **Todas las cuentas activas**. Debe personalizar la vista (que requiere el rol de seguridad Administrador del sistema o Personalizador del sistema), o bien usar la búsqueda avanzada para crear su propia vista basada en la vista actual.  
    
- En las aplicaciones basadas en modelos, los valores de moneda se exportan a Excel como números. Una vez completada la exportación, vea el tema de la Ayuda de Excel “Mostrar números como moneda” para dar formato de moneda a los datos.
  
- Los valores de fecha y hora que se ven en la aplicación solo se muestran como fecha al exportar el archivo a Excel, pero la celda realmente muestra la fecha y la hora.  
  
- Si va a realizar cambios y a volver a importar el archivo de datos a la aplicación, recuerde que los campos protegidos, calculados y compuestos (como Nombre completo, por ejemplo) son de solo lectura y no se pueden importar a la aplicación. Estos campos se podrán editar en Excel, pero al volver a importar los datos a la aplicación, no se actualizarán. Si quiere actualizar estos campos (como, por ejemplo, el nombre de un contacto), se recomienda usar esa vista para exportar los datos, actualizarlos en Excel y volver a importarlos a la aplicación para ver si hay cambios.  
  

