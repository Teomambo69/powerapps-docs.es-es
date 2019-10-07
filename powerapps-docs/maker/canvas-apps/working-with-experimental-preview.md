---
title: Descripción de las características experimentales y de versión preliminar | Microsoft Docs
description: Pruebe y empiece a adoptar nuevas características.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/20/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d6e5572a70ce747fb77b69fe52147d8f068934fb
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71988075"
---
# <a name="understand-experimental-and-preview-features-in-powerapps"></a>Descripción de las características experimentales y de versión preliminar de PowerApps

Con cada versión, se realizan cambios y agregan características para transformar PowerApps en la mejor herramienta para satisfacer sus necesidades. Hacemos que avance el producto.  

Nos tomamos muy en serio la compatibilidad con versiones anteriores. Sin embargo, con cualquier cambio o mejora, es posible que causemos un efecto secundario no deseado y la aplicación podría no funcionar exactamente igual a como lo hacía antes.

Para ayudar a equilibrar las mejoras y el impacto en las aplicaciones existentes, sometemos a las características más grandes a una progresión de fases. En este artículo se describe este proceso y cómo puede controlar su exposición a las características que están en desarrollo.

## <a name="feature-roll-out-stages"></a>Fases de puesta en servicio de características

Las características pasan por tres fases en el proceso para convertirse en partes oficiales del producto:

1. **Experimental**:  Esta característica es un trabajo en curso. No empiece a depender de ella aún, podría sufrir cambios significativos.
1. **Vista previa**:  Esta característica está casi terminada y es estable. Ahora se comienzan a migrar aplicaciones existentes a ella.
1. **Enviado**:  Esta característica se realiza. Todas las aplicaciones tienen esta característica habilitada y no se puede desactivar esta función.

En cada fase, el número de personas que usan la característica aumenta, lo que nos ayuda a validar si la característica es lo que necesita y que no estamos incluyendo efectos secundarios no deseados.

**Sus comentarios son esenciales para este proceso.**  Envíenos sus comentarios en el [foro de la comunidad de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).

¿Cuánto tiempo pasa una característica en cada fase? Esto varía para cada característica. Nos centramos en muchos factores, como el número de aplicaciones que usan la característica, el número de problemas notificados y la urgencia con la que se necesita. Las características pueden permanecer en una fase desde unas semanas a muchos meses.

Esta tabla puede ayudarle a decidir cuándo debe empezar a usarlas: 

| Fase | ¿Cuándo debo usarlo? | ¿Puedo usarla con confianza? | ¿Está habilitada de forma predeterminada para las nuevas aplicaciones? | 
|----|----|----|-----|------|
| **Experimental** | Si es un usuario pionero, ve algo útil para usted y quiere ayudar a probar la característica. | No.  Las características experimentales pueden cambiar radicalmente o desaparecer por completo en cualquier momento. | No. Debe solicitar explícitamente su participación en el uso de la característica.  |  
| **Versión preliminar** | Las nuevas aplicaciones incluyen automáticamente esta característica.  Se comienza a habilitar y probar en las aplicaciones existentes porque con el tiempo esta característica también estará disponible para ellas. | Sí. Esta característica está en camino de convertirse en parte permanente del producto.  | Sí. Es posible que quiera desactivarla si surge un problema.  Informe de los problemas, esta es la razón principal por la cual la característica está en versión preliminar. | 
| **Enviada** (ya no aparece en **Configuración avanzada**) | Todas las aplicaciones tienen esta característica. | Sí. | Sí.  La mayoría no se puede deshabilitar.  |  

Hacia el final de la versión preliminar, se puede habilitar la característica para todas las aplicaciones al mismo tiempo y se marca para su **validación final**.  Este cambio le ofrece a la mayoría de los usuarios una última oportunidad para probar la característica mientras siguen pudiendo desactivarla. Los comentarios oportunos son fundamentales durante este período, ya que, en la fase siguiente, se distribuye por completo la característica y no se puede desactivar.

En la transición final a **enviado**, podemos quitar el modificador de vista previa en las aplicaciones para las que la característica ya está activada, con lo que la característica se activa de manera permanente. Este cambio se aplicará a la mayoría de las aplicaciones porque la característica estará activada de forma predeterminada antes de ese punto. En el caso de las aplicaciones en las que la característica está desactivada, el conmutador de vista previa seguirá estando disponible para que pueda activarla, probarla con la característica y desactivarla dentro de la misma sesión de PowerApps Studio. Sin embargo, si guarda la aplicación cuando el conmutador está activado, no estará disponible cuando se vuelva a cargar la aplicación, por lo que no podrá volver a activar la característica. En ese momento, puede [restaurar la aplicación a una versión anterior](restore-an-app.md) para devolver la aplicación a un estado anterior a la habilitación de la característica.

## <a name="documentation"></a>Documentación

¿Dónde se puede encontrar información sobre estas características?  Las características en versión preliminar se tratan como características terminadas y se puede obtener más información acerca de ellas como lo haría con cualquier otra característica del producto: 
- [Documentación de PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started). Le proporcionaremos los conceptos básicos sobre la nueva característica: sus ventajas, cómo empezar a usarla e información de referencia.
- [Foro de la comunidad de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).  Otros explorarán la nueva característica con usted. Aprenda de sus experiencias y comparta las suyas.
- [Blog de PowerApps](https://powerapps.microsoft.com/blog/).  A menudo, pero no siempre, una entrada de blog acompaña a una nueva característica.

Las características experimentales son diferentes.  Son proyectos en desarrollo y no considera que estén terminadas. La breve descripción disponible en el panel **Configuración de la aplicación** (ver abajo) podría ser la única información acerca de ellas. Las características experimentales no aparecen normalmente en la documentación. El foro de la comunidad probablemente es la mejor fuente de información.  En algunos casos, una entrada de blog temprana describe la característica.  Si no encuentra suficiente información, pregunte en los foros o espere a que la característica pase a la fase de versión preliminar.

## <a name="controlling-which-features-are-enabled"></a>Controlar qué características están habilitadas

Las características experimentales y en versión preliminar se muestran en la **Configuración avanzada** de la aplicación.  En la aplicación, seleccione el menú **Archivo**, seleccione **Configuración de la aplicación** y después seleccione **Configuración avanzada**. Desplácese hacia abajo hasta las secciones **Características en versión preliminar** y **Características experimentales**:

![](media/working-with-experimental/advanced-settings.png)

Cada característica tiene un interruptor.  **Desactivada** significa que la característica está deshabilitada.  Tener todos los interruptores desactivados es la forma prevista y más segura para ejecutar la aplicación.

En algunos casos, es posible que deba cerrar y volver a abrir la aplicación después de cambiar una configuración.  La descripción de la característica debería indicar cuándo debe realizar este paso.

En la parte superior del panel **Configuración avanzada** puede encontrar la configuración de las características con distribución completa que no están en fase experimental o de versión preliminar y de las que puede depender por completo. 

Esta configuración es específica para cada aplicación, por lo que un interruptor solo afecta a la aplicación que está abierta actualmente. Si crea una aplicación, estos interruptores vuelven a sus valores predeterminados para esa aplicación.
