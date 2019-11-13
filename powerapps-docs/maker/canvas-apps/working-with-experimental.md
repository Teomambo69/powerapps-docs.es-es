---
redirect_url: working-with-experimental-preview
title: Descripción de las características experimentales, de vista previa y experimental | Microsoft Docs
description: Pruebe y empiece a adoptar nuevas características.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/08/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a09d3a36f5db048aa077e8801a77915ccfb2bcf2
ms.sourcegitcommit: 249d710ec06c078eb71faa6d5eb48494c8435abd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73962558"
---
# <a name="understand-experimental-preview-and-deprecated-features-in-powerapps"></a>Descripción de las características experimentales, de vista previa y en desuso en PowerApps

Con cada versión, se realizan cambios y agregan características para transformar PowerApps en la mejor herramienta para satisfacer sus necesidades. Hacemos que avance el producto.  

Nos tomamos muy en serio la compatibilidad con versiones anteriores. Sin embargo, con cualquier cambio o mejora, es posible que causemos un efecto secundario no deseado y la aplicación podría no funcionar exactamente igual a como lo hacía antes.

Para ayudar a equilibrar las mejoras y el impacto en las aplicaciones existentes, sometemos a las características más grandes a una progresión de fases. En este artículo se describe este proceso y cómo puede controlar su exposición a las características que están en desarrollo.

## <a name="feature-roll-out-stages"></a>Fases de puesta en servicio de características

Las características pasan por tres fases en el proceso para convertirse en partes oficiales del producto:

1. **Experimental**: esta característica es un proyecto en desarrollo. No empiece a depender de ella aún, podría sufrir cambios significativos.
1. **Versión preliminar**: esta característica está casi lista y es estable. Ahora se comienzan a migrar aplicaciones existentes a ella.
1. **Enviada**: esta característica está completada. Todas las aplicaciones tienen esta característica habilitada y no se puede desactivar esta función.

En cada fase, el número de personas que usan la característica aumenta, lo que nos ayuda a validar que la característica es lo que necesita y que no se presentan efectos secundarios imprevistos.

**Sus comentarios son esenciales para este proceso.**  Envíenos sus comentarios en el [foro de la comunidad de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).

¿Cuánto tiempo pasa una característica en cada fase? Esto varía para cada característica. Nos centramos en muchos factores, como el número de aplicaciones que usan la característica, el número de problemas notificados y la urgencia con la que se necesita. Las características pueden permanecer en una fase desde unas semanas a muchos meses.  También se pueden omitir algunas fases si no creemos que le resulte útil.

Esta tabla puede ayudarle a decidir cuándo debe empezar a usarlas: 

| Fase | ¿Cuándo debo usarlo? | ¿Puedo usarla con confianza?  ¿Está habilitada de forma predeterminada para las nuevas aplicaciones? | 
|----|----|----|
| **Experimental** | Si es un usuario pionero, ve algo útil para usted y quiere ayudar a probar la característica. | No. Las características experimentales pueden cambiar radicalmente o desaparecer por completo en cualquier momento. Por esta razón, la característica no está habilitada de forma predeterminada y debe optar explícitamente a usarla. |  
| **Versión preliminar** | Las nuevas aplicaciones incluyen automáticamente esta característica, pero todavía se puede desactivar.  Se comienza a habilitar y probar en las aplicaciones existentes porque con el tiempo esta característica también estará disponible para ellas.  |Sí.  Esta característica está en camino de convertirse en parte permanente del producto. Es posible que quiera desactivarla si surge un problema.  Informe de los problemas, esta es la razón principal por la cual la característica está en versión preliminar.  | 
| **Vista previa (validación de&nbsp;final)** | En el caso de algunas características que podrían tener un gran impacto, podemos tomar el paso adicional más allá de la **vista previa** de forzar el cambio de características una vez para las aplicaciones existentes cuando se abren en el estudio.  En caso de que se produzca un problema, la característica todavía se puede desactivar y sus comentarios son fundamentales antes de llevar a cabo el siguiente paso. | Sí. Puede usar esta característica con confianza, lo que está muy cerca de ser permanente. Es posible que quiera desactivarla si surge un problema.  Informe de los problemas encontrados. |
| Se **incluye** en&nbsp;nuevas aplicaciones de&nbsp; | Todas las aplicaciones nuevas tienen esta característica activada y no se puede desactivar.  En el caso de las aplicaciones existentes en las que la característica está desactivada, la característica se seguirá mostrando como una característica de vista previa hasta que se active.  Si está activado y el conmutador deja de estar disponible, puede [restaurar la aplicación a una versión anterior](restore-an-app.md) para volver a un estado anterior a la habilitación de la característica. | Sí. |
| Se **incluye** para&nbsp;todas&nbsp;aplicaciones | Todas las aplicaciones tienen esta característica y no se pueden deshabilitar. | Sí. | 

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

## <a name="feature-deprecation"></a>Desuso de características

A veces es necesario retirar una característica.  A menudo, esto se produce cuando hay una nueva forma de realizar una tarea.  También se eliminan las características poco populares, ya que todas las características requieren cierta sobrecarga para mantenerse al día de los cambios en el producto.

El desuso de las características también pasa por las fases.  Las características son únicas y no todas las características se utilizarán en todas las fases.

| Fase | ¿Cuándo debo usarlo? | ¿Puedo usarla con confianza?  ¿Está habilitada de forma predeterminada para las nuevas aplicaciones? | 
|----|----|----|
| **En desuso** | Las aplicaciones existentes pueden seguir usando esta característica durante un tiempo limitado. Todavía puede activar la característica para las nuevas aplicaciones.  Es el momento de evaluar alternativas.  | Sí, todavía puede usar la característica con confianza. Pero estará disponible pronto. Por esta razón, debe optar explícitamente por usar la característica en nuevas aplicaciones y no se recomienda.  |
| **Obsoleto (última&nbsp;ADVERTENCIA)** | En el caso de algunas características que podrían tener un gran impacto, es posible que se tarde el paso más en **desuso** de forzar la desactivación de la característica una vez para las aplicaciones existentes la próxima vez que se abran en el estudio.  En caso de que se produzca un problema, la característica se puede volver a activar, y sus comentarios son fundamentales antes de llevar a cabo el siguiente paso.|  No.  La característica está a punto de quitarse de forma permanente. Debe optar explícitamente a usar la característica y no se recomienda. |
| Se **quitó** para&nbsp;nuevas aplicaciones de&nbsp; | Todas las aplicaciones nuevas tienen esta característica desactivada y no se puede habilitar.  En el caso de las aplicaciones existentes en las que la característica está activada, la característica seguirá apareciendo como una característica desusada hasta que esté desactivada.  Si está desactivado y el modificador de características deja de estar disponible, puede [restaurar la aplicación a una versión anterior](restore-an-app.md) para volver a un estado anterior a la deshabilitación de la característica. | No.  La característica está a punto de quitarse de forma permanente. La característica ya no está disponible para las nuevas aplicaciones. |
| Se **quitó** para&nbsp;todas&nbsp;aplicaciones | La característica no está disponible para todas las aplicaciones. | No. |  

