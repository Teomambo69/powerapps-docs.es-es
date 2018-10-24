---
title: Propiedades de campo común de aplicación basada en modelos en PowerApps | Microsoft Docs
description: Obtenga información sobre las propiedades de campo común del formulario principal de Dynamics 365 for Customer Engagement.
Keywords: Main form; Common field properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 2b91ee28-7f09-435e-9fae-5225aa698e22
ms.openlocfilehash: 74e67dd4299d06a54d5ec85765e4e5d03710b432
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699294"
---
# <a name="model-driven-app-common-field-properties"></a>Propiedades de campo común de aplicación basada en modelos

 Los campos de un formulario muestran los controles que se usan para ver o editar datos de un registro de entidad. Se puede aplicar formato a los campos para que ocupen hasta cuatro columnas dentro de una sección.  

Puede acceder a **Propiedades de campo común** en el Explorador de soluciones. En **Componentes**, expanda **Entidades**, expanda la entidad que desee y, a continuación, seleccione **Formularios**. En la lista de formularios, abra el formulario de tipo **Principal**. Después, haga doble clic en uno de los campos para ver las propiedades de campo común.

![common-field-properties](media/common-field-properties.png)
  
En la tabla siguiente se describen las propiedades que tienen todos los campos. Determinados tipos de campos tienen propiedades especiales. Estos métodos se describen en las [propiedades de campos especiales](special-field-properties-legacy.md).  
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Mostrar**|**Etiqueta**|**Requerido**: de forma predeterminada, la etiqueta coincidirá con el nombre para mostrar del campo. Puede reemplazar ese nombre para el formulario escribiendo aquí una etiqueta diferente.|  
||**Mostrar etiqueta en el formulario**|Puede elegir no mostrar la etiqueta.|  
||**Comportamiento del campo**|Especifique el comportamiento a nivel de campo mediante las casillas.|  
||**Bloqueo**|Esto evitará que los campos se quiten accidentalmente del formulario. Esto evitará que cualquier configuración aplicada al campo, como los controladores de eventos, se borre en caso de que se elimine el campo. Para quitar el campo, el personalizador primero debe borrar esta configuración.|  
||**Visibilidad**|Mostrar el campo es opcional y se puede controlar mediante scripts. Más información: [Opciones de visibilidad](visibility-options-legacy.md)|  
||**Disponibilidad**|Elija si desea que la pestaña esté disponible en el teléfono.|
|**Formato**|**Seleccione el número de columnas que ocupa el control**|Cuando la sección que contiene los campos tiene más de una columna, puede establecer el campo para ocupar hasta el número de columnas que tiene la sección.|  
|**Detalles**|**Nombre para mostrar**, **Nombre** y **Descripción**|Estos campos de solo lectura son solo para referencia. Haga clic en el botón **Editar** para acceder de forma cómoda a la definición del campo si desea editarla.<br /><br /> Cada instancia de un campo del formulario tiene una propiedad de nombre para que se pueda hacer referencia a ella en los scripts de formulario, pero es la aplicación la que se encarga de administrar este nombre. La primera instancia del campo es el nombre del campo especificado cuando se creó. Más información: [Creación y edición de campos](../common-data-service/create-edit-fields.md)<br /><br /> Por cada hora adicional que un campo está incluido en un formulario, el nombre anexa un número que empieza con 1 hasta el final. Por tanto, si el nombre del campo es "new_cost", la primera instancia es "new_cost", la segunda es "new_cost1", y así sucesivamente para cada instancia del campo del formulario.<br /><br />**Nota:** El valor **Descripción** del campo proporciona texto con información sobre herramientas para el campo cuando el usuario coloca el cursor sobre él.|  
|**Eventos**|**Bibliotecas de formulario**|Especifique todos los recursos web de JavaScript que se usarán en el controlador de eventos `OnChange` del campo.<br /><br />|  
||**Controladores de eventos**|Configure las funciones de las bibliotecas de formulario a las que se debe llamar para el evento `OnChange` del campo. Más información: [Configuración de controladores de eventos](configure-event-handlers-legacy.md)|  
|**Reglas de negocio**|**Reglas de negocio**|Visualice y administre cualquier regla de negocio que haga referencia a este campo. Más información: [Crear reglas de negocio y recomendaciones](create-business-rules-recommendations-apply-logic-form.md)|  
|**Controles**|**Controles**|Agregue controles y especifique su disponibilidad en la Web, teléfonos y tabletas.|  

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario principal y sus componentes](use-main-form-and-components.md)
