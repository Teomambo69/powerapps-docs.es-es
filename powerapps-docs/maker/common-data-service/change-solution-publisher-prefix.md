---
title: Cambiar el prefijo del editor de soluciones | MicrosoftDocs
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="change-the-solution-publisher-prefix"></a>Cambiar el prefijo del editor de soluciones

Cada personalización creada es parte de una solución. Cada solución tiene un editor. De forma predeterminada, la solución con la que trabajará en PowerApps será la **Solución predeterminada de Common Data Services** que está asociado con el **Editor predeterminados de CDS**.

El prefijo de personalización predeterminado se asignará aleatoriamente para este editor, por ejemplo, podría ser `cr8a3`. Esto significa que el nombre de cada nuevo elemento de metadatos creado para su organización tendrá que anexarse a los nombres usados para identificar los elementos. Si crea una nueva entidad denominada **Animal**, el nombre único usado por CDS para aplicaciones sería `cr8a3_animal`. Lo mismo se aplica a los nuevos campos (atributos), relaciones u opciones de conjuntos de opciones.

A menos que vaya a distribuir la solución para instalarla junto con los elementos de metadatos que se crearon para otro editor de soluciones, no es realmente importante cuál es el prefijo de personalización. No es visible para la mayoría de las personas que usan sus aplicaciones. Pero se expone a los desarrolladores y a otras personas técnicas que hacen cosas como crear informes. Proporciona una forma rápida de entender qué solución se agregó al elemento.

Por este motivo, a mucha gente le gusta cambiar el prefijo del editor de soluciones para que sea más significativo, especialmente para ver elementos de metadatos que incluyen los importados de otras soluciones. 

> [!NOTE]
> Si cambia el prefijo del editor de soluciones, debe hacerlo antes de crear nuevos elementos de metadatos. Puede cambiar los nombres de los elementos de metadatos.
> Cuando cambie el valor del prefijo de personalización, asegúrese de pulsar en el campo siguiente. La opción **Prefijo de valor de opción** generará automáticamente un número según el prefijo de personalización. Este número se usa al agregar opciones de conjuntos de opciones y ofrece un mensaje de la solución usada para agregar la opción. 

## <a name="change-the-solution-publisher-prefix-for-the-cds-default-publisher"></a>Cambiar el prefijo del editor de soluciones del editor predeterminado de CDS  

 1. En el portal PowerApps, seleccione **Aplicaciones basadas en modelos** en la esquina inferior izquierda.
 2. Haga clic en **Avanzadas** en la navegación izquierda para abrir la **Solución predeterminada de Common Data Services**
 3. En el explorador de soluciones, seleccione el área **Información** en la navegación izquierda.
 4. Haga clic en el vínculo **Editor** para abrir el formulario **Editor predeterminados de CDS**.
 5. Edite el valor del campo **Prefijo** con el prefijo de personalización que desee.
 6. Haga clic en **Guardar y cerrar**.
  
## <a name="change-the-solution-publisher-prefix-for-any-publisher"></a>Cambiar el prefijo del editor de soluciones de cualquier editor

Las personas que distribuyen sus soluciones trabajarán normalmente en una solución que se creen en lugar de en la **Solución predeterminada de Common Data Services**. El prefijo de personalización suele establecerse cuando crean la solución. Puede cambiar el prefijo de personalización para otra solución no administrada con la que trabaja siguiendo estos pasos: 

 1. En el portal PowerApps, seleccione **Aplicaciones basadas en modelos** en la esquina inferior izquierda.
 2. Haga clic en **Avanzadas** en la navegación izquierda para abrir la **Solución predeterminada de Common Data Services**
 3. Edite la dirección URL de la página para quitar todos después `dynamics.com` y volver a cargar la página.
 4. Navegue a **Configuración** > **Personalización** > **Personalizaciones**. 
 5. Haga clic en **Editores**. Ahora puede ver una lista de editores disponibles.
 6. Haga clic en el editor que desee editar para abrir el formulario del editor.
 7. Edite el valor del campo **Prefijo** con el prefijo de personalización que desee.
 6. Haga clic en **Guardar y cerrar**.
  
