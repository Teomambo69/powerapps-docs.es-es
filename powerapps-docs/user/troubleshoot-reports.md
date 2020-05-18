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
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "3302412"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>Solución de problemas de datos que no se muestran en un informe

Hay varias razones posibles para que no aparezcan en un informe los datos que se esperaban:  
  
- **Permisos de seguridad insuficientes**. Si no tiene permiso en Common Data Service para ver un registro, éste no aparecerá en el informe.  
  
- **No se especificaron datos.** La persona que especificó los datos puede haber dejado campos vacíos.  
  
- **Los datos no cumplen los criterios del informe.** Muchos informes incluyen un filtro predeterminado que muestra solo los registros activos, o bien puede que haya seleccionado criterios que no tienen ningún registro coincidente. Pruebe a cambiar el filtro del informe. Para obtener más información, vea [Edición del filtro predeterminado de un informe](edit-report-filter.md).  
  
- **Puede estar viendo una copia en caché del informe.** De forma predeterminada, los datos en informes de Common Data Service se extraen de la base de datos cada vez que se ejecuta un informe. Sin embargo, el administrador del sistema puede haber cambiado un informe para que se ejecute desde la memoria caché. Si los datos que ha especificado recientemente no están incluidos en el informe, puede tener una versión antigua del informe procedente de la memoria caché. Para actualizar el informe, seleccione el botón **Actualizar** en la barra de herramientas del informe.  
  
- **Es posible que no tenga permiso para leer registros en un subinforme.** Si no tiene permiso para leer los tipos de registro incluidos en un subinforme, recibirá un mensaje de error en el que se indica que el subinforme no pudo mostrarse.  
  
- **Su configuración de privacidad de Internet Explorer puede bloquear las cookies necesarias.** En los informes gráficos, si en lugar de ver el gráfico ve una letra X roja, es posible que su configuración de privacidad esté bloqueando una cookie necesaria para el control de gráficos. Para solucionar ese problema, en el explorador, habilite las cookies para el servidor en el que se ejecuta Reporting Services.  
  

### <a name="see-also"></a>Vea también
[Trabajo con los informes](work-with-reports.md) 

[Creación de un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Adición de un informe existente](add-existing-report.md)

[Edición del filtro de informe](edit-report-filter.md)

