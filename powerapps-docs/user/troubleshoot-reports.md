---
title: Solución de problemas de datos que no se muestran en un informe | Microsoft Docs
description: Solución de problemas de datos que no se muestran en un informe
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
ms.openlocfilehash: 1156aa8fb5fbc3ae51c21b8aa41606df6dbc2e86
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420775"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>Solución de problemas de datos que no se muestran en un informe

Hay varias razones por las que es posible que los datos que espera que aparezcan en un informe no lo hagan:  
  
- **Permisos de seguridad insuficientes**. Si no tiene permiso en Common Data Service para ver un registro, no aparecerá en el informe.  
  
- **No se han especificado los datos.** Puede que la persona que ha escrito los datos haya dejado algún campo vacío.  
  
- **Los datos no coinciden con los criterios del informe.** Muchos informes incluyen un filtro predeterminado que muestra solo los registros activos, o bien puede que haya seleccionado criterios que no tienen ningún registro coincidente. Pruebe a cambiar el filtro del informe. Para obtener más información, vea [Edición del filtro predeterminado de un informe](edit-report-filter.md).  
  
- **Es posible que esté viendo una copia del informe almacenada en caché.** De forma predeterminada, los datos de los informes de Common Data Service se extraen de la base de datos cada vez que ejecuta un informe. Con todo, es posible que el administrador del sistema haya cambiado un informe para que se ejecute desde la memoria caché. Si los datos que ha escrito recientemente no se incluyen en el informe, es posible que tenga una versión anterior del informe de la memoria caché. Para actualizar el informe, seleccione el botón **Actualizar** en la barra de herramientas del informe.  
  
- **Es posible que no tenga permiso para leer los registros de un subinforme.** Si no tiene permiso para leer los tipos de registro que se incluyen en un subinforme, recibirá un mensaje de error en el que se indica que no se pudo mostrar el subinforme.  
  
- **La configuración de privacidad de Microsoft Internet Explorer puede bloquear las cookies necesarias.** En el caso de los informes de gráficos, si en lugar de ver el gráfico, ve una letra X roja, es posible que la configuración de privacidad esté bloqueando una cookie necesaria para controlar el gráfico. Para solucionar este problema, en el explorador, habilite las cookies del servidor que ejecuta Reporting Services.  
  

### <a name="see-also"></a>Vea también
[Trabajo con los informes](work-with-reports.md) 

[Creación de un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Adición de un informe existente](add-existing-report.md)

[Edición del filtro de informe](edit-report-filter.md)

