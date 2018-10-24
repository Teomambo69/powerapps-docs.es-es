---
title: Configuración del control de notas de una aplicación controlada por modelos para acceder a información sobre las publicaciones en PowerApps | Microsoft Docs
ms.custom: ''
ms.date: 05/06/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 014f0c2516813b7cbcaa8e44a188455b07056c71
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712263"
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>Configuración del control de notas de una aplicación controlada por modelos para acceder a información sobre las publicaciones

 En los formularios de PowerApps para ciertas entidades de sistema que usan los [formularios actualizados](main-form-presentations.md#updated-forms), el control de notas proporciona la capacidad de acceder a información sobre **Publicaciones**, **Actividades** y **Notas**. Para las entidades personalizadas en las que habilitó las notas y las actividades, solo verá **Notas** y **Actividades**. Para incluir **Publicaciones**, debe habilitarlas para la entidad personalizada.  
  
## <a name="enable-posts-for-a-custom-entity"></a>Habilitación de publicaciones para una entidad personalizada  
  
1.  Vaya a **[Configuración](advanced-navigation.md#settings)** > **Configuración de fuentes de actividades**. 
  
2.  Abra el registro de la entidad personalizada.  
  
3.  Asegúrese de que la opción **Enable walls for this type of record form** (Habilitar los muros para este tipo de formulario de registro) está seleccionada y guarde el registro.  
  
4.  En la barra de comandos, seleccione **Activar**.  
  
5.  Si necesita habilitar muros, debe publicar la entidad.  
  
 De manera predeterminada, para las entidades del sistema el control de notas está colocado en una sección del panel social en el centro de una pestaña de tres columnas en la parte superior del formulario. Puede aparecer en un formulario solo una vez. Puede mover o quitar el control de notas. Para volver a agregarlo, use el botón **Notas** del grupo **Control** de la pestaña **Insertar**.  
  
 En la tabla siguiente se describen las propiedades para el control de notas.  
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Mostrar**|**Etiqueta**|**Requerido**: aunque la etiqueta no aparece de manera predeterminada, se requiere una etiqueta.|  
||**Mostrar etiqueta en el formulario**|Puede elegir mostrar la etiqueta.|  
||**Bloquear el campo en el formulario**|Esto evitará que las notas se quiten accidentalmente del formulario.|  
||**Pestaña predeterminada**|Seleccione la pestaña que se debe mostrar de manera predeterminada. Las opciones son:<br /><br /> - **Actividades**<br />- **Publicaciones**<br />- **Notas**|  
|**Formato**|**Seleccione el número de columnas que ocupa el control**|Cuando la sección que contiene el control de notas tiene más de una columna, puede establecer que el campo ocupe hasta el número de columnas que tiene la sección.|  
||**Número de filas**|Para controlar qué tan alto será el control de notas, seleccione el número de filas que el control ocupa.|  
||**Automatically expand to use available space** (Expandir automáticamente para usar el espacio disponible)|En lugar de establecer el alto mediante un número de filas, puede permitir que el alto del control de notas se expanda al espacio disponible.|  
  
## <a name="next-steps"></a>Pasos siguientes
[Apertura del editor de formularios](open-form-editor.md)
