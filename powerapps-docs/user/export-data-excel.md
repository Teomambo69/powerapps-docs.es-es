---
title: Exportar datos a Excel en Power Apps | MicrosoftDocs
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
- D365CE
ms.openlocfilehash: 1f9368a7630e7b2f94e7b624e0d005f89b919a59
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "3302734"
---
# <a name="export-data-to-excel"></a>Exportar datos a Excel

¿Necesita analizar los datos y convertirlos en elementos procesables que le ayuden a disparar las ventas? Ahora puede hacerlo al exportar los datos a Excel o a Excel Online. Además, el análisis de grandes conjuntos de datos no es un problema, ya que se pueden exportar hasta 100 000 filas de datos.
  
Puede optar por exportar hojas de cálculo estáticas u hojas de cálculo dinámicas, y ambas se pueden volver a importar a la aplicación. Si necesita funciones más avanzadas, puede exportar una tabla dinámica, lo que hace que sea muy sencillo organizar y resumir los datos.  
  
Puede exportar los datos a un archivo de Excel estándar que puede usar en cualquier dispositivo, como un teléfono, una tableta o un equipo de escritorio. Los datos se exportan en el mismo formato que se ve en la aplicación. El texto seguirá siendo texto, los números seguirán siendo números y las fechas seguirán siendo fechas. Sin embargo, cuando se exportan datos desde la aplicación a Excel, algunos formatos de celda pueden alterarse. En la siguiente tabla se resume cómo se van a ver los datos en las aplicaciones y cómo cambia el formato de celda al exportarlos a Excel.  
  
## <a name="cell-format-when-data-is-exported-from-model-driven-apps"></a>Formato de celda cuando los datos se exportan desde aplicaciones basadas en modelos
  
| Formato de datos en las aplicaciones basadas en modelos |                                            Formato de celda en Excel                                             |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Texto, símbolo del valor, teléfono, conjunto de opciones y búsqueda            |                                                       Se muestra como Texto y conjunto de opciones se convierte en lista desplegable                                                       |
|                                 Correo electrónico, Dirección URL                                 |                                                                        Se muestra como General                                                                         |
|                                   Número                                   |                                                             Se muestra como número sin separador de grupo.                                                             |
|                                  Moneda                                  |                                                         Se muestra como número y no incluye el signo de dólar ($).                                                         |
|                          Solo fecha, fecha y hora                          |                                                                       Se muestran como solo fecha.                                                                        |
|                       Campos calculados y acumulados                        | Editables en Excel pero no se pueden importar de nuevo en Power Apps |
|                               Campos protegidos                               | Editables en Excel pero no se pueden importar de nuevo en Power Apps |
  
## <a name="see-which-type-of-export-works-best-for-you"></a>Saber qué tipo de exportación es la más conveniente en su caso  
  
|                                                                                                               Tarea                                                                                                                |                                              Más información                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
|   Realizar un análisis *ad hoc* o de *hipótesis* sin modificar los datos de la aplicación También puede editar rápidamente varios registros de forma masiva.   | [Exportar a Excel Online](export-to-excel-online.md) |
|                                                                   Obtener una instantánea de los datos en la fecha y la hora actuales o si quiere compartirlos con otros usuarios                                                                    |           [Exportar a una hoja de cálculo estática de Excel](export-excel-static-worksheet.md)           |
| Obtener la información más actualizada y poder actualizarla en Excel, y ver si coincide con lo que ve en la aplicación en cualquier momento |          [Exportar a una hoja de cálculo dinámica de Excel](export-excel-dynamic-worksheet.md)          |
|                                                                      Ver datos de la aplicación en una tabla dinámica                                                                      |                 [Exportar a una tabla dinámica de Excel](export-excel-pivottable.md)                 |



Cuando se exportan datos a Excel (formato .xlsx) y luego se agregan o modifican columnas, los datos no se podrán volver a importar a Dynamics 365. Esto no es posible con el formato de archivo .xlsx.  
  
Si usa Excel 2010, es posible que aparezca este mensaje de error al exportar datos desde el área Cuentas: 
 
`The file is corrupt and cannot be opened.`  
  
Este mensaje de error se debe a una configuración de Excel. Para solucionar el problema, haga lo siguiente:  
  
1. Abra Excel 2010.  
  
2. Vaya a **Archivo** > **Opciones**.  
  
3. Vaya a **Centro de confianza** > **Configuración del Centro de confianza**.  
  
4. Seleccione **Vista protegida** y desactive las casillas de las dos primeras opciones.  
  
5. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  

