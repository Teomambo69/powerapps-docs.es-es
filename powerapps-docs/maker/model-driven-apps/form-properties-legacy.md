---
title: Propiedades del formulario de aplicación basado en modelos en PowerApps | Microsoft Docs
description: Descripción de las propiedades del formulario principal
Keywords: Main form properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 4ed30bb7-dca1-4de8-80f3-842152ea921a
ms.openlocfilehash: 4aec7fd8a117257d4f21ac2f692643785fd21791
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701381"
---
# <a name="model-driven-app-form-properties"></a>Propiedades del formulario de aplicación basado en modelos 

Puede acceder a **Propiedades del formulario** en el Explorador de soluciones. En **Componentes**, expanda **Entidades**, expanda la entidad que desee y, a continuación, seleccione **Formularios**. En la lista de formularios, abra el formulario de tipo **Principal**. A continuación, en la pestaña **Inicio**, seleccione **Propiedades del formulario**.

![form-properties](media/form-properties.png)

En la tabla siguiente se enumeran las propiedades del formulario:  
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Eventos**|**Bibliotecas de formulario**|Administre qué recursos web de JavaScript están disponibles en el formulario y el orden en el que se cargarán.|  
||**Controladores de eventos**|Configure qué funciones de JavaScript de las bibliotecas de formularios se ejecutarán para los eventos de formulario `OnLoad` y `OnSave` y el orden en el que se podrán ejecutar.|  
|**Mostrar**|**Nombre de formulario**|Escriba un nombre que sea significativo para los usuarios. Este nombre se mostrará a los usuarios cuando usen el formulario. Si pueden usar varios formularios configurados para la entidad, usarán este nombre para diferenciar entre los formularios disponibles.|  
||**Description**|Escriba una descripción que explique de qué modo este formulario es diferente de otros formularios principales. Esta descripción solo se muestra en la lista de formularios de una entidad en el Explorador de soluciones.|  
||**Asistente de formulario**|Active la casilla si quiere habilitar el asistente de formulario o ver el formulario expandido de forma predeterminada.|
||**Navegación de páginas**|Puede elegir no mostrar elementos de navegación.<br /><br /> En los formularios de entidades actualizadas, esto significa que el valor de nombre principal del registro actualmente visualizado no aparecerá en la barra de navegación para permitir la navegación a las vistas asociadas.<br /><br /> En formularios que usan la presentación clásica, no se mostrarán las opciones de navegación para elegir las vistas asociadas en el lado izquierdo del formulario.|  
||**Imagen**|Cuando una entidad tiene un campo de imagen y está establecida la opción **Imagen principal** de las entidades, esta configuración permitirá mostrar el campo de imagen en el encabezado de este formulario.<br /><br /> Para más información sobre las opciones de entidad, consulte [Enable or disable entity options](../common-data-service/edit-entities.md#enable-or-disable-entity-options) (Habilitación o deshabilitación de las opciones de entidad).|  ||**Mostrar**|**Establezca un ancho máximo (en píxeles)** para limitar el ancho del formulario. El valor predeterminado es 1900.|  
||**Mostrar**|Escriba aquí el ancho máximo que desea para el formulario, en píxeles.|
|**Parámetros**|**Parámetros**|Cada formulario se puede abrir con código mediante una dirección URL. La dirección URL también puede contener datos que pueden pasarse al formulario mediante una cadena de consulta que se anexa a la dirección URL. Las cadenas de consulta tienen el aspecto de este ejemplo:<br />`?p_firstName=Jim&p_lastName=Daly`<br /><br /> Como medida de seguridad, los formularios no aceptarán ningún parámetro de cadena de consulta desconocido. Use esta lista de parámetros para especificar los parámetros que debe aceptar este formulario para admitir código que pase los datos a los formularios mediante una cadena de consulta.<br /><br /> Se comprobarán el nombre y el tipo de los datos y el formulario no se abrirá si se pasan a él parámetros de cadena de consulta no válidos.<br /><br />**Nota:** El nombre no puede comenzar con un carácter de subrayado (_) o crm\_. Debe comenzar con caracteres alfanuméricos, seguidos de un carácter de subrayado (\_). Por ejemplo, parámetro_1 o 1_parámetro. El nombre no puede contener guiones (-), dos puntos (:), punto y coma (;), comas (,) o puntos (.). <br /><br />|  
|**Dependencias que no son de eventos**|**Campos dependientes**|Cada controlador de eventos tiene una propiedad **Campos dependientes** similar, por lo que cualquier campo que requiera el script se puede registrar. Cualquiera que intente quitar los campos dependientes no podrá hacerlo.<br /><br /> Algunos scripts funcionan en el formulario, pero no están configurados en un controlador de eventos. Los scripts que se inician desde la barra de comandos no tienen un lugar donde se puedan registrar los campos dependientes. Esta propiedad de formulario proporciona ese lugar.|  

## <a name="next-steps"></a>Pasos siguientes

[Use el formulario principal y sus componentes](use-main-form-and-components.md)