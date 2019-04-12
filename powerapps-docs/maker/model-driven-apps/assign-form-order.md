---
title: Asignar el orden de los formularios de una aplicación controlada por modelos en PowerApps | MicrosoftDocs
description: Aprenda a asignar el formulario predeterminado en las aplicaciones
ms.custom: ''
ms.date: 03/07/2019
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
ms.assetid: 914c5694-9c80-4424-be89-9f63256b4811
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="assign-model-driven-app-form-order"></a>Asignar orden de formularios de aplicación controlada por modelos

 Si tiene varios formularios principales, de creación rápida, vista rápida o formularios de tarjetas para una entidad, puede establecer un orden para los formularios. El orden de formularios determine qué formularios disponibles se mostrarán de forma predeterminada. Los formularios principales disponibles se pueden controlar mejor si se asignan roles de seguridad al formulario. Consulte [Controlar el acceso a los formularios](control-access-forms.md) para obtener más información.  
  
 No puede asignar roles de seguridad a formularios de creación rápida, vista rápida o formularios de tarjetas por lo que el único formulario que podrá usar todo el mundo es el que se encuentra en la parte superior del orden de formularios.  
  
## <a name="to-assign-a-form-order"></a>Para asignar un orden de formularios  
  
1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer), expanda la entidad que desee y seleccione **Formularios**.  
  
2.  En la barra de herramientas de la lista de formularios, seleccione **Orden de los formularios**.  

     > [!div class="mx-imgBorder"] 
     > ![Comando de la barra de herramientas Orden de los formularios](media/form-order.png)
  
3.  Elija **Conjunto de formularios principal**, **Formulario de creación rápida establecido**, **Conjunto de formularios de vista rápida** o **Conjunto de formularios de tarjeta**, según el tipo de formularios con el que desee trabajar. Más información: [Tipo de formularios](types-forms.md). 
  
4.  El diálogo **Orden de los formularios** es una lista simple donde puede mover un formulario seleccionado hacia arriba o abajo en el orden de formularios.  
  
5.  Después de establecer el orden deseado, haga clic en **Aceptar** para cerrar el cuadro de diálogo.  

## <a name="next-steps"></a>Pasos siguientes

[Cambiar la navegación en un formulario](use-the-form-editor-legacy.md)
