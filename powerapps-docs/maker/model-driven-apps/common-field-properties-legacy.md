---
title: Propiedades de campos comunes de aplicaciones basadas en modelos en PowerApps | MicrosoftDocs
description: Comprender las propiedades de campo común para formularios principales
Keywords: Formulario principal; Propiedades de campos comunes; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 2b91ee28-7f09-435e-9fae-5225aa698e22
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e30d84206e92162327f1faf0035450ede9c05a8a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701331"
---
# <a name="model-driven-app-common-field-properties"></a>Propiedades de campos comunes de aplicaciones controladas por modelos

 Los campos de un formulario muestran controles que los usuarios utilizan para ver o modificar datos de un registro de entidad. Los campos pueden formatearse para ocupar hasta cuatro columnas en una sección.  

Puede acceder a **Propiedades comunes de los campos** en el explorador de soluciones. En **Componentes**, expanda **Entidades**, expanda la entidad que desea y luego seleccione **Formularios**. En la lista de formularios, abra el formulario de tipo **Principal**. A continuación, haga doble clic en uno de los campos para ver las propiedades comunes de los campos.

![common-field-properties](media/common-field-properties.png)
  
En la siguiente tabla se describen las propiedades que tienen todos los campos. Determinados tipos de campos tienen propiedades especiales. Se describen en [Propiedades de campos especiales](special-field-properties-legacy.md).  
  
|Ficha|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Presentación**|**Etiqueta**|**Requerido**: de forma predeterminada, la etiqueta se corresponderá con el nombre para mostrar del campo. Puede reemplazar ese nombre para el formulario proporcionando otra etiqueta aquí.|  
||**Mostrar etiqueta en el formulario**|También puede elegir no mostrar la etiqueta.|  
||**Comportamiento del campo**|Especifique el comportamiento de nivel de campo mediante las casillas.|  
||**Bloqueo**|Esto evitará que el campo se quite accidentalmente del formulario. Esto evitará que una configuración aplicada al campo, como controladores de eventos, se desactive si se quita el campo. Para quitar este campo que un personalizador necesitaría borrar este valor primero.|  
||**Visibilidad**|Mostrar el campo es opcional y se puede controlar mediante scripts. Más información: [Opciones de visibilidad](visibility-options-legacy.md)|  
||**Disponibilidad**|Elija si desea que la pestaña esté disponible en el teléfono.|
|**Formato**|**Seleccione el número de columnas que ocupa el control**|Cuando la sección que contiene los campos tiene más de una columna puede establecer el campo para ocupar hasta el número de columnas que tiene la sección.|  
|**Detalles**|**Nombre para mostrar**, **Nombre** y **Descripción**|Estos campos de solo lectura son de referencia. Haga clic en el botón **Editar** para acceder cómodamente a la definición del campo si desea editarla.<br /><br /> Cada instancia de un campo en el formulario tiene una propiedad de nombre para que se le pueda hacer referencia en los scripts de formulario, pero este nombre lo administra la aplicación. La primera instancia del campo es el nombre del campo especificado cuando se creó. Más información: [Crear y editar campos](../common-data-service/create-edit-fields.md)<br /><br /> Cada nueva vez que un campo se incluye en un formulario, se agrega al nombre un número empezando por 1 al final. Si el nombre del campo es "new_cost", la primera instancia es "new_cost", la segunda es "new_cost1" y así sucesivamente para cada instancia del campo en el formulario.<br /><br />**Nota:** El valor del campo **Descripción** proporciona un texto de información sobre el campo cuando los usuarios colocan el cursor encima.|  
|**Eventos**|**Bibliotecas de formularios**|Especifique cualquier recurso web de JavaScript que se usará en el controlador de eventos `OnChange` del campo.<br /><br />|  
||**Controladores de eventos**|Configure las funciones de las bibliotecas de formularios que deben llamarse para el evento `OnChange` del campo. Más información: [Configurar controladores de eventos](configure-event-handlers-legacy.md)|  
|**Reglas de negocio**|**Reglas de negocio**|Visualice y administre las reglas de negocio que hacen referencia a este campo. Más información: [Crear reglas de negocio y recomendaciones](create-business-rules-recommendations-apply-logic-form.md)|  
|**Controles**|**Controles**|Agregue controles y especifique su disponibilidad en web, teléfono y tableta.|  

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
