---
title: Control de temporizador de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Comprenda cómo puede usar el control de temporizador
ms.custom: ''
ms.date: 06/06/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: b2b64771-083b-42f9-a3d5-2218f9d8a713
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 31b7f2b55f10e404841517aada26b0b38df7fbbf
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710835"
---
# <a name="model-driven-app-timer-control-overview"></a>Información general del control de temporizador de aplicaciones controladas por modelos

 Use un control de temporizador con formularios donde los registros deban cumplir un hito específico basado en tiempo. Un control de temporizador muestra a las personas cuánto tiempo hay disponible para completar una acción en la resolución de un registro activo o cuánto tiempo ha pasado desde que finalizó el tiempo para completar la acción. Como mínimo, los controles de temporizador se deben configurar para mostrar el resultado correcto o con error al completar la acción. Además, pueden configurarse para mostrar advertencias cuando las condiciones se acercan al error.  
  
 Se puede agregar un control de temporizador a un formulario para cualquier entidad, pero se usan con más frecuencia para la entidad de caso, especialmente cuando están vinculados a campos que realizan un seguimiento de contratos de nivel de servicio. Puede agregar varios controles de temporizador en el cuerpo de un formulario. No puede agregarlos al encabezado o pie de página.  
  
 Las propiedades **Origen de datos** de control de temporizador usan campos para la entidad.  
  
-   El **Campo de hora del error** usa un campo fecha-hora para establecer la hora.  
  
-   Los tres campos de condición usan uno de los campos **Conjunto de opciones**, **Dos opciones**, **Estado**, o **Razón para el estado** para la entidad.  

Para crear un control de temporizador, en el diseñador de formularios seleccione la pestaña **Insertar** y, a continuación, en la barra de herramientas, seleccione **Temporizador**. 

  > [!div class="mx-imgBorder"] 
  > ![Insertar control de temporizador](media/insert-timer-control.png)

En la página de propiedades del control de temporizador, introduzca o seleccione las propiedades que desee y, a continuación, seleccione **Aceptar**. 

  
<a name="BKMK_TimerControlProperties"></a>   

## <a name="timer-control-properties"></a>Propiedades de los controles de temporizador  
 En la siguiente tabla se describen las propiedades de un control de temporizador.  
  
|Grupo|Nombre|Descripción|  
|-----------|----------|-----------------|  
|Nombre|Nombre|**Requerido**. Un nombre único para el control.|  
||Etiqueta|**Requerido**. La etiqueta que se muestra para el control de temporizador.|  
|Origen de datos|Campo de hora del error|**Requerido**. Seleccione uno de los campos de fecha-hora para la entidad para representar cuándo debe realizarse correctamente un hito.|  
||Condición de éxito|**Requerido**. Seleccione un campo para la entidad para evaluar el resultado correcto del hito, y después elija qué opción indica el resultado correcto.|  
||Condición de advertencia|Seleccione un campo para la entidad para evaluar si el resultado correcto del hito está en peligro para mostrar una advertencia, luego elija qué opción indica que debe mostrarse una advertencia.|  
||Cancelar condición|Seleccione un campo para la entidad para evaluar si la consecución del hito debe cancelarse, después elija qué opción indica que el hito se ha cancelado.|  

## <a name="next-steps"></a>Pasos siguientes

[Información general de la interfaz de usuario del editor de formularios](form-editor-user-interface-legacy.md)
