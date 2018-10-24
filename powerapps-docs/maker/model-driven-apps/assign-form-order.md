---
title: Asignación de orden de formulario de aplicación basado en modelos en PowerApps | Microsoft Docs
description: Aprenda a asignar el formulario predeterminado en la aplicación.
ms.custom: ''
ms.date: 06/22/2018
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
ms.assetid: 914c5694-9c80-4424-be89-9f63256b4811
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 22ed9c144c90c5393b6d9e76692172f0dd067225
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701366"
---
# <a name="assign-model-driven-app-form-order"></a>Asignación de orden de formulario de aplicación basado en modelos

 Cuando tenga varios formularios principales, de creación rápida o móviles para una entidad, puede asignar un orden de formulario. El orden de formulario determina cuál de los formularios disponibles se debe mostrar de forma predeterminada. Los formularios principales o móviles disponibles se pueden controlar aún más si se les asignan roles de seguridad. Para más información, consulte [Controlar el acceso a los formularios](control-access-forms.md).  
  
 Como no se pueden asignar roles de seguridad a formularios de creación rápida, el único formulario que todos usarán es el que se encuentra arriba en el orden de los formularios.  
  
## <a name="to-assign-a-form-order"></a>Asignación de un orden de formulario  
  
1.  Abra el [Explorador de soluciones](advanced-navigation.md#solution-explorer), expanda la entidad que quiera y, a continuación, seleccione **Formularios**.  
  
2.  En la barra de herramientas de la lista de formularios, seleccione **Orden de los formularios**.  

    ![Comando de la barra de herramientas de orden de formulario](media/form-order.png)
  
3.  Elija **Conjunto de formularios principal**, **Formulario de creación rápida establecido**, **Conjunto de formularios de vista rápida** o **Conjunto de formularios móviles**, según el tipo de formulario con el que quiera trabajar. Más información: [Tipo de formularios](types-forms.md). 
  
4.  El cuadro de diálogo **Orden de los formularios** es una lista sencilla donde puede mover hacia arriba o hacia abajo un formulario seleccionado en el orden de formulario.  
  
5.  Después de haber establecido el orden que desea, haga clic en **Aceptar** para cerrar el cuadro de diálogo.  

## <a name="next-steps"></a>Pasos siguientes

[Cambiar la navegación en un formulario](use-the-form-editor-legacy.md)