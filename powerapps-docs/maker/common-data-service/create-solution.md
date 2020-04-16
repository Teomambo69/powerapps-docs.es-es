---
title: Cree una solución | MicrosoftDocs
description: Aprenda cómo crear soluciones
ms.custom: ''
ms.date: 03/20/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e21a4876-08b4-417a-a644-c577a27c5cf1
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 59c041d7fe74e1a1dbbce9f1516057d324447478
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162215"
---
# <a name="create-a-solution"></a>Crear una solución

Para ubicar y trabajar solo con los componentes que ha personalizado, cree una solución y realice toda su personalización allí. Luego, recuerde siempre trabajar en el contexto de la solución personalizada a medida que agrega, edita y crea componentes. Esto facilita la exportación de su solución para importarla a otro entorno o como copia de seguridad.   
  
Para obtener más información sobre conceptos de una solución, consulte [Trabajar con soluciones](solutions-overview.md).  
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y seleccione **Soluciones** en el panel de navegación de la izquierda. 
  
2.  Elija **Nueva solución** y rellene los campos requeridos para la solución.
  
    |Campo|Descripción|  
    |-----------|-----------------|  
    |**Nombre para mostrar**|Nombre que se muestra en la lista de soluciones. Puede cambiarlo más adelante.|  
    |**Nombre**|Nombre único de la solución. Este se genera con el valor especificado en el campo Nombre para mostrar. Puede modificarlo antes de guardar la solución, pero no podrá hacerlo una vez haya guardado la solución.|  
    |**Editor**|Puede seleccionar el editor predeterminado o crear un nuevo editor. Le recomendamos que cree un editor para que su organización lo use de manera consistente en todos los entornos en los que usará la solución. Más información: [Información general del editor de soluciones](change-solution-publisher-prefix.md) |  
    |**Versión**|Escriba un número para la versión de la solución. Solo es importante si exporta la solución. El número de versión se incluirá en el nombre de archivo cuando exporte la solución.|  
  
3.  Seleccione **Guardar**.  
  
 Después de guardar la solución, puede ser conveniente agregar información a los campos que no son necesarios. Estos pasos son opcionales. Use el campo **Descripción** para describir la solución y elija un recurso web HTML como **Página de configuración** de la solución. La página de configuración la usan normalmente los ISV que distribuyen soluciones. Si se ha configurado, un nuevo nodo **Configuración** aparece bajo el nodo **Información** para mostrar este recurso web. Los desarrolladores usarán esta página para incluir instrucciones o controles para permitir definir los datos de configuración o iniciar su solución.  
  
<a name="BKMK_AddSolutionComponents"></a>   

## <a name="add-solution-components"></a>Agregar componentes de la solución  
 Una vez que haya creado la solución, no contendrá ningún componente de la solución. Puede crear nuevos componentes de la solución o usar el botón **Agregar existente** en el menú de lista para agregar todos los componentes de la solución pertenecientes a la solución predeterminada.  
  
 Al hacerlo, es posible que se muestre un diálogo **Faltan componentes necesarios**.  
   
 ![Cuadro de diálogo Agregar componentes necesarios](media/crm-itpro-cust-addrequiredcomponents.PNG "Cuadro de diálogo Agregar componentes necesarios")  
  
 Este diálogo le alerta de que un componente de la solución tiene dependencias de otros componentes de la solución. Si selecciona **No, no incluir los componentes necesarios**, la solución puede generar errores si se importa en otra organización donde no existen todos los componentes necesarios. Si la importación de la solución es correcta, el comportamiento en la otra solución puede no ser idéntico al de la organización original, porque los componentes están configurados de forma distinta a los de la solución de origen.  
  
Cuando selecciona componentes de la entidad, le recomendamos que utilice la segmentación de la solución para que solo incluya los componentes de la entidad que son nuevos o actualizados cuando distribuye las actualizaciones de la solución. Con la segmentación de soluciones, puede trabajar en una solución con activos seleccionados de la entidad, como campos de la entidad, formularios y vistas, en lugar de entidades completas con todos los activos. Más información: [Usar soluciones segmentadas](use-segmented-solutions-patches-simplify-updates.md)
  
 Si no se piensa exportar la solución, o si solo pretende exportarla como una solución no administrada e importarla nuevamente en la misma organización, no es necesario incluir componentes necesarios. Si alguna vez exporta la solución, verá otra advertencia indicando que faltan algunos componentes necesarios. Si va a importar solo esta solución nuevamente en la misma organización, puede ignorar esta advertencia. Los pasos para modificar la navegación de la aplicación o la cinta sin usar una herramienta de edición de terceros prevén que exportará la solución nuevamente en la misma organización.  

<!-- >
> [!IMPORTANT]
>  If you plan to include appointments in solutions, we strongly recommend that you don’t include only appointments and only recurring appointments in separate solutions. If you install and uninstall separate solutions with different appointment types, you’ll encounter a SQL Server error and you’ll have to re-create the appointments.  -->

## <a name="publish-changes"></a>Publicar cambios 

 Determinadas personalizaciones que realizan cambios en la interfaz de usuario requieren que se publiquen antes de que los usuarios puedan usarlas en la aplicación. 
 
### <a name="publish-your-customizations"></a>Publique las personalizaciones

1.  Seleccione **Soluciones** en la barra de navegación izquierda.

2.  Seleccione la solución que desea publicar para abrirla.

3.  En la lista de comandos, seleccione **Publicar todas las personalizaciones**.  

![Publicar todas las personalizaciones](media/publish-all-customizations.PNG "Publicar todas las personalizaciones")  
  
> [!IMPORTANT]
>  La preparación de personalizaciones puede tardar tiempo. Si aparece un mensaje que indica que la página del explorador ha dejado de responder, espere a que responda y no la cierre.  

### <a name="see-also"></a>Vea también
 [Usar soluciones](use-solution-explorer.md)
