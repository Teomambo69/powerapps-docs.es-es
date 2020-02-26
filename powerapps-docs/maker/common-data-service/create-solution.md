---
title: Cree una solución | MicrosoftDocs
description: Aprenda cómo crear soluciones
ms.custom: ''
ms.date: 10/30/2018
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
ms.openlocfilehash: 25ea1db66e61d3e0b03090a0a91f35bd90d7b649
ms.sourcegitcommit: b746aad895b152259680f5179dcee0281c951d0a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "2948852"
---
# <a name="create-a-solution"></a>Crear una solución

Puesto que la solución predeterminada contiene todos los componentes de soluciones, puede ser más fácil para usted ubicar solo los componentes de la solución que ha personalizado si crea una solución independiente y realiza toda la personalización ahí. Esto también ayuda exportar una copia de seguridad de la solución como un archivo más pequeño. Si elige realizar esta acción, debe recordar siempre agregar los componentes de la solución que edite para esta solución. Cuando crea nuevos componentes de la solución, debe crearlos siempre en el contexto de esta solución. De esta forma el prefijo de personalización del editor de soluciones se aplica de forma coherente. Después de crear los componentes de la solución en la solución, o de agregar componentes de la solución existentes a esa solución, también puede modificarlos en la solución predeterminada si lo desea.  
  
 Para obtener más información sobre conceptos de una solución, consulte [Trabajar con soluciones](solutions-overview.md).  
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y seleccione **Soluciones** en el panel de navegación de la izquierda. 
  
2.  Elija **Nueva solución** y rellene los campos requeridos para la solución.
  
    |Campo|Descripción|  
    |-----------|-----------------|  
    |**Nombre para mostrar**|Nombre que se muestra en la lista de soluciones. Puede cambiarlo más adelante.|  
    |**Nombre**|Nombre único de la solución. Este se genera con el valor especificado en el campo Nombre para mostrar. Puede modificarlo antes de guardar la solución, pero no podrá hacerlo una vez haya guardado la solución.|  
    |**Editor**|Puede seleccionar el editor predeterminado o crear un nuevo editor. Le recomendamos que cree un editor para que su organización lo use de manera consistente en todos los entornos en los que usará la solución. Más información: [Cambiar el prefijo del editor de soluciones de cualquier editor](change-solution-publisher-prefix.md#change-the-solution-publisher-prefix-for-any-publisher) |  
    |**Versión**|Escriba un número para la versión de la solución. Solo es importante si exporta la solución. El número de versión se incluirá en el nombre de archivo cuando exporte la solución.|  
  
3.  Seleccione **Guardar**.  
  
 Después de guardar la solución, puede ser conveniente agregar información a los campos que no son necesarios. Estos pasos son opcionales. Use el campo **Descripción** para describir la solución y elija un recurso web HTML como **Página de configuración** de la solución. La página de configuración la usan normalmente los ISV que distribuyen soluciones. Si se ha configurado, un nuevo nodo **Configuración** aparece bajo el nodo **Información** para mostrar este recurso web. Los desarrolladores usarán esta página para incluir instrucciones o controles para permitir definir los datos de configuración o iniciar su solución.  
  
<a name="BKMK_AddSolutionComponents"></a>   

## <a name="add-solution-components"></a>Agregar componentes de la solución  
 Una vez que haya creado la solución, no contendrá ningún componente de la solución. Puede crear nuevos componentes de la solución o usar el botón **Agregar existente** en el menú de lista para agregar todos los componentes de la solución pertenecientes a la solución predeterminada.  
  
 Al hacerlo, es posible que se muestre un diálogo **Faltan componentes necesarios**.  
   
 ![Cuadro de diálogo Agregar componentes necesarios](media/crm-itpro-cust-addrequiredcomponents.PNG "Cuadro de diálogo Agregar componentes necesarios")  
  
 Este diálogo le alerta de que un componente de la solución tiene dependencias de otros componentes de la solución. Si selecciona **No, no incluir los componentes necesarios**, la solución puede generar errores si se importa en otra organización donde no existen todos los componentes necesarios. Si la importación de la solución es correcta, el comportamiento en la otra solución puede no ser idéntico al de la organización original, porque los componentes están configurados de forma distinta a los de la solución de origen.  
  
 Normalmente, es más seguro incluir los componentes necesarios si tiene previsto exportar la solución a otra organización. Si no agrega estos componentes cuando agrega un componente de la solución individual, puede volver más tarde, seleccionar el componente de la solución que ha agregado y elija **Agregar componentes necesarios** en el menú.  
  
 Si no se piensa exportar la solución, o si solo pretende exportarla como una solución no administrada e importarla nuevamente en la misma organización, no es necesario incluir componentes necesarios. Si alguna vez exporta la solución, verá otra advertencia indicando que faltan algunos componentes necesarios. Si va a importar solo esta solución nuevamente en la misma organización, puede ignorar esta advertencia. Los pasos para modificar la navegación de la aplicación o la cinta sin usar una herramienta de edición de terceros prevén que exportará la solución nuevamente en la misma organización.  

> [!IMPORTANT]
>  Si piensa incluir citas en soluciones, se recomienda no incluir solo citas y solo citas periódicas en soluciones independientes. Si instala y desinstala soluciones independientes con tipos de citas diferentes, se mostrará un error de SQL Server y tendrá que volver a crear las citas. 

## <a name="see-also"></a>Vea también
 [Usar soluciones](use-solution-explorer.md)
