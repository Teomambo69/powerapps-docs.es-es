---
title: Cambio del prefijo del editor de soluciones | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
ms.openlocfilehash: 5881dd6742dd441d135768d3a96fd36dbef9e700
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701933"
---
# <a name="change-the-solution-publisher-prefix"></a>Cambio del prefijo del editor de soluciones

Todas las personalizaciones que realicen son parte de una solución. Cada solución tiene un editor. De forma predeterminada, la solución con la que trabajará en PowerApps será la **solución predeterminada de Common Data Services** que está asociada con el **editor predeterminado de CDS**.

El prefijo de personalización predeterminado se asignará aleatoriamente a este editor, por ejemplo, podría ser `cr8a3`. Esto significa que el nombre de cada nuevo elemento de metadatos creado para su organización tendrá este prefijo ya anexado a los nombres usados para identificar de forma exclusiva los elementos. Si crea una entidad llamada **Animal**, el nombre único usado por CDS for Apps será `cr8a3_animal`. Lo mismo puede decirse de los nuevos campos (atributos), relaciones u opciones del conjunto de opciones.

A menos que vaya a distribuir su solución para que se instale junto con los elementos de metadatos que se crearon para otro editor de soluciones, no es realmente importante cuál sea el prefijo de personalización. No es visible para la mayoría de los usuarios que usan las aplicaciones. Pero se expone a los desarrolladores y otro personal técnico que realizan cosas como crear informes. Proporciona una forma rápida de comprender qué solución agregó el elemento.

Por este motivo, a muchos usuarios les gusta cambiar el prefijo del editor de soluciones para que sea más significativo, en especial al ver elementos de metadatos que los incluyen importados de otras soluciones. 

> [!NOTE]
> Si cambia el prefijo del editor de soluciones, debe hacerlo antes de crear un elemento de metadatos. No puede cambiar los nombres de los elementos de metadatos.
> Al cambiar el valor del prefijo de personalización, asegúrese de presionar TAB para pasar al siguiente campo. El **prefijo de valor de opción** generará automáticamente un número basado en el prefijo de personalización. Este número se usa al agregar las opciones a conjuntos de opciones y proporciona un indicador de qué solución se usó para agregar la opción. 

## <a name="change-the-solution-publisher-prefix-for-the-cds-default-publisher"></a>Cambio del prefijo del editor de soluciones predeterminado de CDS  

 1. En el portal de PowerApps, seleccione **Basado en modelos** en la esquina inferior izquierda.
 2. Haga clic en **Avanzado** en el panel de navegación izquierdo para abrir la solución predeterminada **Common Data Services**.
 3. En el Explorador de soluciones, seleccione el área **Información** en el panel de navegación izquierdo.
 4. Haga clic en el vínculo **Editor** para abrir el formulario **CDS Default Publisher** (Editor predeterminado de CDS).
 5. Edite el valor del campo **Prefijo** y use el prefijo de personalización que prefiera.
 6. Haga clic en **Guardar y cerrar**.
  
## <a name="change-the-solution-publisher-prefix-for-any-publisher"></a>Cambio del prefijo de un editor de soluciones

Las personas que distribuyen sus soluciones normalmente trabajarán en una solución que creen en lugar de hacerlo en la **solución predeterminada de Common Data Services**. El prefijo de personalización se establece normalmente al crear la solución. Puede cambiar el prefijo de personalización de otra solución no administrada con la que trabaje mediante estos pasos: 

 1. En el portal de PowerApps, seleccione **Basado en modelos** en la esquina inferior izquierda.
 2. Haga clic en **Avanzado** en el panel de navegación izquierdo para abrir la solución predeterminada **Common Data Services**.
 3. Edite la dirección URL de la página para quitar todo lo que hay después de `dynamics.com` y volver a cargar la página.
 4. Vaya a **Configuración** > **Personalización** > **Personalizaciones**. 
 5. Haga clic en **Editores**. Ahora puede ver una lista de editores disponibles.
 6. Haga clic en el editor que quiere editar para abrir el formulario del editor.
 7. Edite el valor del campo **Prefijo** y use el prefijo de personalización que prefiera.
 6. Haga clic en **Guardar y cerrar**.
  