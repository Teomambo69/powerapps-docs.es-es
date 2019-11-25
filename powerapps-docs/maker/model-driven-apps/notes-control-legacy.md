---
title: Configurar el control de notas de una aplicación controlada por modelos para acceder a información sobre las publicaciones en PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 05/06/2018
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
ms.assetid: f10cdf1c-3540-439c-a171-27a10e72da45
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bb60588e34e66fc1a0222d18e90d50af672bcc69
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711715"
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>Configurar el control de notas de una aplicación controlada por modelos para acceder a información sobre las publicaciones

 En los formularios de PowerApps de determinadas entidades del sistema que usan los [formularios actualizados](main-form-presentations.md#updated-forms), el control de notas proporciona la capacidad de tener acceso a la información de **Publicaciones**, **Actividades** y **Notas**. Para las entidades personalizadas en las que ha habilitado notas y actividades, verá solo **Notas** y **Actividades**. Para incluir **Publicaciones**, debe habilitarlas para la entidad personalizada.  
  
## <a name="enable-posts-for-a-custom-entity"></a>Habilitar publicaciones para una entidad personalizada  
  
1.  Vaya **[Configuración](advanced-navigation.md#settings)** > .**Configuración de fuentes de actividades** 
  
2.  Abra el registro de la entidad personalizada.  
  
3.  Asegúrese de que la opción **Habilita los muros para este tipo de formulario de registro** está seleccionada y guarde el registro.  
  
4.  En la barra de comandos, seleccione **Activar**.  
  
5.  Si necesita habilitar muros, debe publicar la entidad.  
  
 De manera predeterminada, para las entidades del sistema el control notas está colocado en una sección del panel social en el centro de una ficha de tres columnas en la parte superior del formulario. Puede aparecer en un formulario solo una vez. Puede mover o quitar el control notas. Para volver a agregarlo, use el botón **Notas** del grupo **Control** de la ficha **Insertar**.  
  
 En la siguiente tabla se describen las propiedades para el control Notas.  
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Mostrar**|**Etiqueta**|**Requerido**: aunque la etiqueta no aparece de forma predeterminada, se requiere una etiqueta.|  
||**Mostrar etiqueta en el formulario**|También puede elegir mostrar la etiqueta.|  
||**Bloquear el campo en el formulario**|Esto evitará que las notas se quiten accidentalmente del formulario.|  
||**Ficha predeterminada**|Seleccione la ficha que debe mostrarse de forma predeterminada. Las opciones son:<br /><br /> - **Actividades**<br />- **Publicaciones**<br />- **Notas**|  
|**Formato**|**Seleccione el número de columnas que ocupa el control**|Cuando la sección que contiene el control de notas tiene más de una columna, puede establecer que el campo ocupe hasta el número de columnas que tiene la sección.|  
||**Número de filas**|Para controlar el alto del control de notas seleccione el número de filas que ocupa el control.|  
||**Expandir automáticamente para usar el espacio disponible**|En lugar de establecer el alto mediante un número de filas, puede permitir que el alto del control de notas se expanda el espacio disponible.|  
  
## <a name="next-steps"></a>Pasos siguientes
[Abrir el editor de formularios](open-form-editor.md)
