---
title: Propiedades de campos especiales de aplicaciones controladas por modelos para formularios principales en PowerApps | MicrosoftDocs
description: Comprender las propiedades de campo especial para formularios principales
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="overview-of-model-driven-app-special-field-properties"></a>Información general sobre propiedades de campos especiales de aplicaciones controladas por modelos

 Todos los campos tienen las propiedades enumeradas en [Propiedades comunes de los campos](common-field-properties-legacy.md), pero determinados campos tienen propiedades adicionales, como este campo de derecho que se puede abrir desde el formulario principal de la entidad de caso.  

![special-properties-dialog](media/special-properties.png)
  
<a name="BKMK_LookupFieldProperties"></a>  
 
## <a name="lookup-field-properties"></a>Propiedades de los campos de búsqueda  
  
> [!NOTE]
>  Las opciones descritas en la tabla de abajo solo están disponible para los campos de búsqueda de una sola entidad.  
  
|Sección|Propiedad|Descripción|  
|-------------|--------------|-----------------|  
|**Filtrado de registros relacionados**|**Mostrar solo los registros donde**|Si esta característica está habilitada, los registros que se muestran cuando los usuarios buscan un registro tendrán filtros adicionales aplicados. Esto ayuda a realizar búsquedas más relevantes al establecer el valor de búsqueda.<br /><br /> De forma predeterminada, está desactivada.<br /><br /> En la tabla siguiente a esta se indican las combinaciones de relaciones posibles para filtrar registros relacionados.*<br /><br /> La primera lista se llena con todas las relaciones posibles que se pueden usar para filtrar esta búsqueda. Seleccione uno.<br /><br /> A continuación, se llena la segunda lista con todas las relaciones que conectan la entidad relacionada (seleccionada en la primera lista) con la entidad de destino. Seleccione uno.<br /><br /> Active la casilla de verificación **Permitir a los usuarios desactivar el filtro** que permite a los usuarios desactivar el filtro que defina aquí.<br /><br /> Cuando los usuarios seleccionan la opción **Buscar más registros** mientras establecen el valor para una búsqueda, ven este cuadro de diálogo.<br /><br /> ![look-up-more-records](media/crm-ua-v-8-1-look-up-more-records.png) <br /><br /> Si ha seleccionado la opción **Permitir a los usuarios desactivar el filtro** mientras configura el campo de búsqueda, los usuarios verán la casilla para desactivar el filtro.  De esta manera, pueden ver un intervalo mayor de registros. Si desea asegurarse de que los usuarios vean únicamente un intervalo limitado de registros definidos por este filtro, desactive la casilla **Permitir a los usuarios desactivar el filtro**.|  
|**Propiedades adicionales**|**Mostrar el cuadro de búsqueda en el diálogo de búsqueda**|Puede elegir que no se muestre el cuadro de búsqueda en el cuadro de diálogo de búsqueda.|  
||**Vista predeterminada**|Esta vista se usa para filtrar los resultados de la búsqueda en línea y establecer la vista predeterminada que se muestra en el cuadro de diálogo de búsqueda cuando los usuarios seleccionan la opción **Buscar más registros**.<br /><br /> La vista predeterminada también controla los campos que se incluyen en búsqueda en línea.<br /><br /> Para búsquedas que solo permiten la selección de un tipo único de entidad, los campos mostrados en la búsqueda en línea están configurados para ser los primeros dos campos incluidos en la vista predeterminada. En este ejemplo, **Número de centralita** y **Correo electrónico** son las primeras dos columnas de la vista predeterminada configurada para una búsqueda de cuenta.<br /><br /> Para búsquedas del sistema que permiten varios tipos de entidades, se muestran las primeras dos columnas de la vista de búsqueda de entidad.|  
||**Selector de vista**|Puede elegir entre tres opciones:<br /><br /> -   **Desactivado**: no permite que los usuarios seleccionen una vista diferente.<br />-   **Mostrar todas las vistas**: están disponibles todas las vistas.<br />-   **Mostrar las vistas seleccionadas**: al elegir esta opción, puede usar la tecla Ctrl y el cursor para elegir las vistas que deben mostrarse. La vista de búsqueda de la entidad no se puede deseleccionar.|  
  
 **\*Combinaciones de relaciones posibles**  
  
|Relación de la primera lista|Relación de la segunda lista|¿Está disponible?|  
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

### <a name="two-option-field-properties"></a>Propiedades de los campos de dos opciones  
 En la pestaña de formato, los campos de dos opciones tienen las siguientes opciones de formato:  
  
- **Dos botones de opción**: dos controles etiquetados con las etiquetas. Solo se puede seleccionar uno.  
  
- **Casilla de verificación**: una sola casilla de verificación para establecer el valor true o, de lo contrario, false.  
  
- **Lista**: una lista desplegable que incluye ambos valores.  
  
<a name="BKMK_MultipleLinesOfTextProperties"></a>   

### <a name="multiple-lines-of-text-field-properties"></a>Propiedades de los campos de varias líneas de texto  
 Los campos de varias líneas de texto y de una sola de línea de texto que usan el formato `Text Area` tienen una propiedad **Diseño de filas** . Con esta propiedad puede especificar un valor de **Número de filas** o seleccionar **Expandir automáticamente para usar el espacio disponible**.  

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
