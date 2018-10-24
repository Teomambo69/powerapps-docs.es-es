---
title: Propiedades de campos especiales de aplicaciones basadas en modelos para formularios principales en PowerApps | Microsoft Docs
description: Información sobre las propiedades de campos especiales para formularios principales
Keywords: Main forms; Special field properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 6ad7e43c-b6a1-48c4-9dfb-ed830142a841
ms.openlocfilehash: 0c4e67b14816ae6eaf100221ac0ac29269000f9b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698334"
---
# <a name="overview-of-model-driven-app-special-field-properties"></a>Información general sobre las propiedades de campos especiales de aplicaciones basadas en modelos

 Todos los campos tienen las propiedades enumeradas en [Propiedades de campo común](common-field-properties-legacy.md), pero algunos campos tienen propiedades adicionales, por ejemplo, este campo de derecho que se puede abrir desde el formulario principal de la entidad de caso.  

![special-properties-dialog](media/special-properties.png)
  
<a name="BKMK_LookupFieldProperties"></a>  
 
## <a name="lookup-field-properties"></a>Propiedades del campo de búsqueda  
  
> [!NOTE]
>  Las opciones descritas en la tabla siguiente están disponibles solo para los campos de búsqueda de una sola entidad.  
  
|Sección|Propiedad|Descripción|  
|-------------|--------------|-----------------|  
|**Filtrado de registros relacionados**|**Mostrar solo los registros de ubicación**|Cuando esta opción está habilitada, los registros que se muestran cuando los usuarios buscan un registro tendrá aplicado un filtrado adicional. Esto ayuda a proporcionar búsquedas más pertinentes al establecer el valor de la búsqueda.<br /><br /> De forma predeterminada, esta opción está desactivada.<br /><br /> Las combinaciones de relaciones que son posibles cuando se filtran los registros relacionados se muestran en la tabla siguiente a esta.*<br /><br /> La primera lista se rellena con todas las relaciones posibles que se pueden usar para filtrar esta búsqueda. Seleccione una.<br /><br /> La segunda lista se rellena después con todas las relaciones que conectan la entidad relacionada (seleccionada en la primera lista) con la entidad de destino. Seleccione una.<br /><br /> Seleccione la casilla **Allow users to turn off filter** (Permitir a los usuarios que desactiven el filtro) para ofrecer a los usuarios la opción de desactivar el filtro que defina aquí.<br /><br /> Cuando los usuarios seleccionan la opción **Look Up More Records** (Buscar más registros) al configurar el valor para realizar una búsqueda, verán este cuadro de diálogo.<br /><br /> ![look-up-more-records](media/crm-ua-v-8-1-look-up-more-records.png) <br /><br /> Si selecciona la opción **Allow users to turn off filter** (Permitir a los usuarios que desactiven el filtro) al configurar el campo de búsqueda, los usuarios verán la casilla para desactivar el filtro.  Esto les permite ver un conjunto más amplio de registros. Si desea asegurarse de que los usuarios solo vean un conjunto limitado de registros definido por este filtro, desactive la casilla **Allow users to turn off filter** (Permitir a los usuarios que desactiven el filtro).|  
|**Propiedades adicionales**|**Mostrar cuadro de búsqueda en el cuadro de diálogo de búsqueda**|Puede elegir no mostrar el cuadro de búsqueda en el cuadro de diálogo de búsqueda.|  
||**Vista predeterminada**|Esta vista se usa para filtrar los resultados de la búsqueda en línea y establecer la vista predeterminada que se muestra en el cuadro de diálogo de búsqueda cuando los usuarios seleccionan la opción **Look Up More Records** (Buscar más registros).<br /><br /> La vista predeterminada también controla qué campos se incluyen en la búsqueda en línea.<br /><br /> Para las búsquedas que solo permiten la selección de un tipo de entidad única, los campos que aparecen en la búsqueda en línea se establecen como los dos primeros campos incluidos en la vista predeterminada. En este ejemplo, **Main Phone** (Teléfono principal) y **Email** (Correo electrónico) son las dos primeras columnas de la vista predeterminada configuradas para una búsqueda de la cuenta.<br /><br /> Para las búsquedas del sistema que permiten varios tipos de entidad, se muestran las dos primeras columnas de la vista de búsqueda de entidad.|  
||**Selector de vista**|Puede elegir entre tres opciones:<br /><br /> -   **Desactivar**: no permitir a los usuarios elegir una vista diferente.<br />-   **Mostrar todas las vistas**: todas las vistas están disponibles.<br />-   **Mostrar vistas seleccionadas**: al elegir esta opción, puede usar la tecla CTRL y el cursor para elegir qué vistas se van a mostrar. No se puede anular la selección de la vista de búsqueda para la entidad.|  
  
 **\*Combinaciones de relaciones posibles**  
  
|Primera relación de la lista|Segunda relación de la lista|¿Disponible?|  
|-----------------------------|------------------------------|----------------|  
|N:1|1:N|Sí|  
|N:1|N:1|Sí|  
|N:1|N:N|Sí|  
|1:N|1:N|Sí|  
|1:N|N:1|No|  
|1:N|N:N|No|  
|N:N|1:N|Sí|  
|N:N|N:1|No|  
|N:N|N:N|No|  
  
<a name="BKMK_TwoOptionProperties"></a>   

### <a name="two-option-field-properties"></a>Propiedades de campos de dos opciones  
 En la pestaña de formato, los campos de dos opciones tienen las siguientes posibilidades de formato:  
  
- **Dos botones de radio**: dos controles con etiquetas. Solo se puede seleccionar uno.  
  
- **Casilla**: una sola casilla para configurar el valor true; de lo contrario, false.  
  
- **Lista**: una lista desplegable que contiene los dos valores.  
  
<a name="BKMK_MultipleLinesOfTextProperties"></a>   

### <a name="multiple-lines-of-text-field-properties"></a>Propiedades de campo de varias líneas de texto  
 Los campos de varias líneas de texto y de una línea de texto que usan el formato `Text Area` tienen una propiedad **Diseño de filas**. Con esta propiedad, puede especificar un valor para **Número de filas** o seleccione **Automatically expand to use available space** (Expandir automáticamente para usar el espacio disponible).  

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario principal y sus componentes](use-main-form-and-components.md)
