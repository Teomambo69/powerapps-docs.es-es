---
title: Propiedades de formularios de aplicaciones controladas por modelos en Power Apps | MicrosoftDocs
description: Comprender las propiedades de formularios principales
Keywords: Propiedades de formulario principal; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 4ed30bb7-dca1-4de8-80f3-842152ea921a
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b9b638c63e14d57cddfa36e6d2134b440b76898a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868047"
---
# <a name="model-driven-app-form-properties"></a>Propiedades de formularios de aplicaciones controladas por modelos 

Puede acceder a **Propiedades de formularios** en el explorador de soluciones. En **Componentes**, expanda **Entidades**, expanda la entidad que desea y luego seleccione **Formularios**. En la lista de formularios, abra el formulario de tipo **Principal**. A continuación, en la pestaña **Inicio**, seleccione **Propiedades del formulario**.

![form-properties](media/form-properties.png)

La tabla siguiente enumera las propiedades de formularios:  
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Eventos**|**Bibliotecas de formularios**|Administre los recursos web de JavaScript que estarán disponibles en el formulario y el orden en que se cargarán.|  
||**Controladores de eventos**.|Configure las funciones de JavaScript de las bibliotecas de formularios que se ejecutarán para los eventos de formulario `OnLoad` y `OnSave`, y el orden en que se ejecutarán.|  
|**Mostrar**|**Nombre del formulario**|Escriba un nombre descriptivo para las personas. Este nombre se mostrará a las personas cuando usen el formulario. Si pueden usar formularios múltiples configurados para la entidad, usarán este nombre para diferenciar los formularios disponibles.|  
||**Descripción**|Escriba una descripción que explique las diferencias de este formulario respecto de otros formularios principales. Esta descripción se muestra solo en la lista de formularios de una entidad en el explorador de soluciones.|  
||**Asistente de formulario**|Seleccione la casilla si desea habilitar el asistente de formularios o ver el formulario ampliado de forma predeterminada.|
||**Navegación de páginas**|Puede elegir no mostrar los elementos de navegación.<br /><br /> En los formularios de entidades actualizadas esto significa que el valor del nombre principal del registro que se muestra actualmente no aparecerá en la barra de navegación para permitir la navegación a las vistas asociadas.<br /><br /> En formularios con la presentación clásica, las opciones de navegación para elegir las vistas asociadas en el lado izquierdo del formulario no se mostrarán.|  
||**Imagen**|Cuando una entidad tiene un campo de imagen y se establece la opción **Imagen principal** de las entidades, este valor habilitará el campo de imagen en el encabezado de este formulario.<br /><br /> Consulte [Habilitar o deshabilitar opciones de entidad](../common-data-service/edit-entities.md#enable-or-disable-entity-options) para obtener más información acerca de las opciones de la entidad.|  ||**Presentación**|**Establezca el ancho máximo (en píxeles)** para limitar el ancho del formulario. El valor predeterminado es 1900.|  
||**Presentación**|Escriba en píxeles el ancho máximo que desea para el formulario aquí.|
|**Parámetros**|**Parámetros**|Todos los formularios se pueden abrir con código mediante una dirección URL. La dirección URL también puede contener datos que se pueden transferir al formulario mediante una cadena de consulta anexada a la dirección URL. Las cadenas de consulta se parecen a este ejemplo:<br />`?p_firstName=Jim&p_lastName=Daly`<br /><br /> Como medida de seguridad, los formularios no aceptarán parámetros de cadena de consulta desconocidos. Use esta lista de parámetros para especificar parámetros que este formulario debe aceptar para admitir el código que transferirá los datos a los formularios con una cadena de consulta.<br /><br /> Se comprobarán el nombre y el tipo de datos, y el formulario no se abrirá si se le transfieren parámetros de cadena de consulta no válidos.<br /><br />**Nota:** El nombre no puede comenzar con un guion bajo (_) o crm\_. Debe empezar con caracteres alfanuméricos seguidos de un guion bajo (\_). Por ejemplo, parameter_1 o 1_parameter. El nombre no puede contener guiones (-), dos puntos (:), punto y coma (;), comas (,) o puntos (.). <br /><br />|  
|**Dependencias que no son de eventos**|**Campos dependientes**|Cada controlador de eventos tiene una propiedad **Campos dependientes** similar para registrar cualquier campo que sea necesario para el script. Si alguien intenta eliminar los campos dependientes, no podrá hacerlo.<br /><br /> Algunos scripts funcionan en el formulario pero no se configuran en un controlador de eventos. Los scripts que se inician desde la barra de comandos no tienen un lugar donde los campos dependientes puedan registrarse. Esta propiedad de formulario proporciona un lugar para que los campos dependientes de dichos scripts puedan registrarse.|  

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
