---
title: Exportar datos a Excel en Power apps | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680636"
---
# <a name="export-data-to-excel"></a>Exportar datos a Excel

¿Necesita analizar los datos y convertirlos en elementos procesables que le ayuden a impulsar más ventas? Ahora puede hacerlo al exportar los datos a Excel o Excel online. Además, el análisis de grandes conjuntos de datos no es un problema, ya que puede exportar hasta 100.000 filas de datos.
  
Puede optar por exportar las hojas de cálculo estáticas o las hojas de cálculo dinámicas, que puede volver a importar en la aplicación. Si necesita funciones más avanzadas, puede exportar una tabla dinámica dinámica, lo que facilita la organización y el Resumen de los datos.  
  
Puede exportar datos a un archivo de Excel estándar que puede usar en cualquier dispositivo, como el teléfono, la tableta o el equipo de escritorio. Los datos se exportan en el mismo formato que se ve en la aplicación. El texto seguirá siendo texto, los números permanecerán en números y las fechas permanecerán en las fechas. Sin embargo, cuando se exportan datos de la aplicación a Excel, algunos formatos de celda pueden cambiar. En la tabla siguiente se resume cómo verá los datos en las aplicaciones y cómo cambia el formato de celda al exportar los datos a Excel.  
  
## <a name="cell-format-when-data-is-exported-from-model-driven-apps"></a>Formato de celda cuando los datos se exportan desde aplicaciones controladas por modelos
  
| Formato de datos en las aplicaciones controladas por modelos |                                            Formato de celda en Excel                                             |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Texto, símbolo de marca de graduación, teléfono, conjunto de opciones y búsqueda            |                                                       Muestra como texto y conjunto de opciones se convierte en una lista desplegable                                                       |
|                                 Correo electrónico, URL                                 |                                                                        Muestra como general                                                                         |
|                                   Número                                   |                                                             Muestra como número sin separador de grupos                                                             |
|                                  Divisa                                  |                                                         Muestra como número y no incluye el signo de dólar ($)                                                         |
|                          Solo fecha, fecha y hora                          |                                                                       Solo se muestra como fecha                                                                        |
|                       Campos calculados y acumulados                        | Editable en Excel, pero no se puede importar a Power apps |
|                               Campos protegidos                               | Editable en Excel, pero no se puede importar a Power apps |
  
## <a name="see-which-type-of-export-works-best-for-you"></a>Vea qué tipo de exportación funciona mejor para usted  
  
|                                                                                                               Task                                                                                                                |                                              Más información                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
|   Realice un análisis *ad hoc* o *What if* sin modificar los datos de la aplicación. O bien, realizar una edición en masa rápida en varios registros.   | [Exportar a Excel online](export-to-excel-online.md) |
|                                                                   Obtenga una instantánea de los datos en los datos y la hora actuales, o bien si desea compartirlo con otros usuarios.                                                                    |           [Exportar a una hoja de cálculo estática de Excel](export-excel-static-worksheet.md)           |
| Obtenga la información más actualizada y podrá actualizarla en Excel y coincidir con lo que ve en la aplicación en cualquier momento. |          [Exportar a una hoja de cálculo dinámica de Excel](export-excel-dynamic-worksheet.md)          |
|                                                                      Ver datos de la aplicación en una tabla dinámica.                                                                      |                 [Exportar a una tabla dinámica de Excel](export-excel-pivottable.md)                 |



Cuando se exportan datos en Excel (formato. xlsx) y, después, se agregan o modifican columnas, no se pueden volver a importar los datos en Dynamics 365. Esto no se admite para el formato de archivo. xlsx.  
  
Si utiliza Excel 2010, es posible que reciba este mensaje de error al exportar datos desde el área cuentas: 
 
`The file is corrupt and cannot be opened.`  
  
El mensaje de error se produce debido a un valor de configuración de en Excel. Para solucionar el problema, haga lo siguiente:  
  
1. Abra Excel 2010.  
  
2. Vaya a **archivo** > **Opciones**.  
  
3. Vaya al **centro de confianza** > **configuración del centro de confianza**.  
  
4. Seleccione **vista protegida** y, a continuación, desactive las casillas de las dos primeras opciones.  
  
5. Seleccione **Aceptar** y, a continuación, cierre el cuadro de diálogo **Opciones** .  
  

