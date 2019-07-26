---
title: Exportar a una hoja de cálculo estática de Excel en una aplicación controlada por modelos | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544830"
---
# <a name="export-to-an-excel-static-worksheet"></a>Exportar a una hoja de cálculo estática de Excel

Si quiere presentar información sobre los datos de la aplicación a una persona que no tiene acceso a la aplicación, o tiene datos que no cambian con frecuencia, considere la posibilidad de exportar los datos de la aplicación a una hoja de cálculo estática de Office Excel.

Puede exportar hasta 100.000 registros a la vez. De forma predeterminada, una aplicación controlada por modelos muestra hasta 50 registros por página. Elija las flechas de la **Página** en la parte inferior de la lista para ver las páginas adicionales.  
  
## <a name="export-data-to-an-excel-static-worksheet"></a>Exportar datos a una hoja de cálculo estática de Excel  
Es posible que tenga la opción de exportar datos a una hoja de cálculo estática de Excel en todos los tipos de registro. Sin embargo, en algunos casos, el formato puede ser heredado o puede que los datos no se filtren por lo que se ve en la aplicación.  
  
1. Abra una lista de registros de la aplicación, seleccione la flecha situada a la derecha de **exportar a Excel**y, a continuación, elija **hoja de cálculo estática (solo página)** .  
  
2. De forma predeterminada, una hoja de cálculo exportada incluye los campos que se muestran en la lista, con el mismo orden de campo, ordenación y ancho de campo. Para realizar cambios en las columnas de una vista de búsqueda avanzada, elija **Editar columnas**. 
  
3. Elija **Guardar** y, a continuación, guarde el archivo. xlsx. Anote la ubicación en la que guardó el archivo.  
  
   > [!NOTE]
   > Si va a editar el archivo de datos más adelante, se recomienda que guarde el archivo antes de abrirlo. De lo contrario, podría obtener este mensaje de error: **Excel no puede abrir o guardar más documentos porque no hay suficiente memoria disponible o espacio en disco.**  
   > 
   > Para solucionar el problema, haga lo siguiente:  
   > 
   > 1. Abra Excel y vaya a **archivo** > **Opciones** > **Centro** > de confianza**configuración centro configuración** > **vista protegida**.  
   > 2.  En **vista protegida**, desactive los tres elementos.  
   > 3.  Seleccione **Aceptar** > **Aceptar**.  
   > 
   > Todavía se recomienda encarecidamente guardar y abrir el archivo de datos en lugar de deshabilitar la vista protegida, lo que podría poner el equipo en riesgo.  


4. Abra Excel y, a continuación, abra el archivo. xlsx que guardó en el paso anterior.  
  
   De forma predeterminada, una hoja de cálculo exportada incluye los campos que se muestran en la lista, con el mismo orden de campo, ordenación y ancho de campo.  
  
## <a name="tips"></a>Recomendaciones  
  
- Puede enviar por correo electrónico una hoja de cálculo de exportación estática a cualquier persona o almacenarla en un archivo compartido. Cualquier persona que abra el archivo verá todos los datos en el archivo.
  
- No se pueden cambiar las columnas de una vista del sistema, como **todas las cuentas activas**. Debe personalizar la vista, que requiere el rol de seguridad Administrador del sistema o Personalizador del sistema, o bien usar búsqueda avanzada para crear su propia vista basada en la vista actual.  
    
- En las aplicaciones controladas por modelos, los valores de moneda se exportan a Excel como números. Después ha completado la exportación, vea el tema de ayuda de Excel "Mostrar números como moneda" para dar formato de moneda a los datos.
  
- Los valores de fecha y hora que se ven en la aplicación solo se muestran como fecha al exportar el archivo a Excel, pero la celda realmente muestra la fecha y la hora.  
  
- Si va a realizar cambios y vuelve a importar el archivo de datos en la aplicación, recuerde que los campos seguros, calculados y compuestos (como el nombre completo) son de solo lectura y no se pueden importar en la aplicación. Podrá editar estos campos en Excel, pero al importar los datos de nuevo en la aplicación, estos campos no se actualizarán. Si desea actualizar estos campos, como el nombre de un contacto, se recomienda que use esa vista para exportar los datos, actualizarlos en Excel y volver a importarlos en la aplicación para ver si hay cambios.  
  

