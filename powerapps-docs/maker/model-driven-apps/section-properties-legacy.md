---
title: Propiedades de las secciones para formularios principales de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Comprender las propiedades de sección para un formulario principal
Keywords: Formulario principal; propiedades de sección; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 2d3af6e9-e8a4-4129-b708-383b2740c015
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 45764a992215c697361f77da656182bdbb0e7783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755023"
---
# <a name="model-driven-app-form-section-properties"></a>Propiedades de sección para formularios principales de aplicaciones controladas por modelos

 Una sección en un formulario ocupa el espacio disponible en una columna de la ficha. Las secciones tienen una etiqueta que se puede mostrarse y una línea se puede mostrar debajo de la etiqueta.  
  
 Las secciones pueden tener hasta 4 columnas e incluyen las opciones para mostrar cómo las etiquetas de los campos de la sección se muestran.  
  
 Los encabezados y pies de página son similares a las secciones pero no se pueden quitar. Si no contienen nada no se mostrarán. 

Puede acceder a las **Propiedades de sección** desde el sitio de PowerApps. 
1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 

3.  En la lista de formularios, abra el formulario de tipo **Principal**. A continuación, haga doble clic en una de las secciones para ver las propiedades de la sección. 

    ![section-properties](media/section-properties.png)
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Presentación**|**Nombre**|**Requerido**: nombre único de la sección que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado.|  
||**Etiqueta**|**Requerido**: etiqueta localizable de la sección visible para los usuarios.|  
||**Muestra la etiqueta de esta sección en el formulario**|Las secciones a menudo se usan sin etiquetas para controlar el formato de los campos que contienen.|  
||**Mostrar una línea en la parte superior de la sección**|Una línea en la parte superior de la sección puede ayudar al dividir el diseño del formulario.|  
||**Ancho de la etiqueta de campo**|**Requerido**: defina un valor entre 50 y 250 para especificar el espacio permitido para las etiquetas de campo.<br /><br /> Los elementos de encabezados y pies de página de también tienen esta propiedad.|  
||**Visibilidad**|Mostrar la sección es opcional y se puede controlar mediante scripts. Más información: [Opciones de visibilidad](visibility-options-legacy.md)|  
||**Disponibilidad**|Elija si desea que la pestaña esté disponible en el teléfono.|  
||**Bloquear la sección en el formulario**|Esto evitará que la sección se quite accidentalmente y que los usuarios quiten el contenido.<br /><br /> Al quitar una sección no solo se quita la sección, sino también cualquier campo que contenga.<br /><br /> Alguien que desea quitar esta sección necesitaría cambiar esta configuración antes de eliminarla.|  
|**Formato**<br /><br /> Los componentes de encabezados y pies de página de también tienen esta propiedad.|**Diseño**|Especifique hasta cuatro columnas para incluir en la sección.|  
||**Alineación de etiqueta de campo**|Las etiquetas de los campos dentro de la sección se pueden alinear a izquierda, derecha o centradas.|  
||**Posición de etiqueta de campo**|Las etiquetas de los campos de la sección pueden colocarse en el lateral o la parte superior de los campos.|  


También se puede agregar un nuevo tipo de sección llamado **Panel de referencia**. Un panel de referencia es una sección de una sola columna. Puede insertar subcuadrículas, control de vista rápida o un control de búsqueda en la Knowledge Base dentro de una sección del panel de referencia. Cada control que agregó en el panel de referencia aparece como una pestaña vertical en el panel en tiempo de ejecución. Puede arrastrar y soltar los distintos controles en la sección del panel de referencia. La pestaña predeterminada en tiempo de ejecución es el primer control agregado en el panel de referencia. Las otras pestañas aparecen en el orden en el cual se agregan en el editor de formularios. Para eliminar una pestaña, use la tecla Eliminar del teclado.  
  
Cuando se inserta un panel de referencia, se agrega de forma predeterminada como última sección en la pestaña. Puede agregar un solo panel referencia por formulario.  
  
> [!IMPORTANT]
>  De forma predeterminada, la sección del panel de referencia está bloqueada en estos formularios estándar: casos, cuentas y contactos. Para quitarla o cambiarla, debe desbloquearla. 

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
