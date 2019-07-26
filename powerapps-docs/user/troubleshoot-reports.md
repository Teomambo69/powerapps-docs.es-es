---
title: Solucionar problemas de datos que no se muestran en un informe | Microsoft Docs
description: Solucionar problemas de datos que no se muestran en un informe
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420775"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>Solucionar problemas de datos que no se muestran en un informe

Hay varias razones posibles por las que los datos que espera que aparezcan en un informe no aparecen:  
  
- **Permisos de seguridad**insuficientes. Si no tiene permiso en Common Data Service para ver un registro, no aparecerá en el informe.  
  
- **No se especifican los datos.** La persona que escribe los datos puede haber dejado campos vacíos.  
  
- **Los datos no coinciden con los criterios del informe.** Muchos informes incluyen un filtro predeterminado que muestra solo los registros activos, o bien puede haber seleccionado criterios que no tienen ningún registro coincidente. Intente cambiar el filtro del informe. Para obtener más información, vea [editar el filtro predeterminado de un informe](edit-report-filter.md) .  
  
- **Es posible que esté viendo una copia almacenada en caché del informe.** De forma predeterminada, los datos de Common Data Service informes se extraen de la base de datos cada vez que se ejecuta un informe. Sin embargo, es posible que el administrador del sistema haya cambiado un informe para que se ejecute desde la memoria caché. Si los datos que ha escrito recientemente no se incluyen en el informe, es posible que tenga una versión anterior del informe de la memoria caché. Para actualizar el informe, en la barra de herramientas de informe, seleccione el botón **Actualizar** .  
  
- **Es posible que no tenga permiso para leer registros en un subinforme.** Si no tiene permiso para leer los tipos de registro que se incluyen en un subinforme, recibirá un mensaje de error que indica que no se pudo mostrar el subinforme.  
  
- **La configuración de privacidad de Microsoft Internet Explorer puede bloquear las cookies necesarias.** En el caso de los informes de gráficos, si en lugar de ver el gráfico, verá una letra roja X, es posible que la configuración de privacidad esté bloqueando una cookie necesaria para el control de gráfico. Para corregir este problema, en el explorador, habilite las cookies para el servidor que ejecuta Reporting Services.  
  

### <a name="see-also"></a>Vea también
[Trabajar con informes](work-with-reports.md) 

[Crear un informe mediante el Asistente para informes](create-report-with-wizard.md)

[Agregar un informe existente](add-existing-report.md)

[Editar filtro de informe](edit-report-filter.md)

