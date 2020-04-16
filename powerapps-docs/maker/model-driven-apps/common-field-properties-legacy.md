---
title: Propiedades de campos comunes de aplicaciones basadas en modelos en Power Apps | MicrosoftDocs
description: Comprender las propiedades de campo común para formularios principales
Keywords: Formulario principal; Propiedades de campos comunes; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 02/25/2020
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
ms.openlocfilehash: 8729292ca14cff762b31ef886ecdc0c90856110e
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136453"
---
# <a name="model-driven-app-common-field-properties"></a>Propiedades de campos comunes de aplicaciones controladas por modelos

Puede ver y editar propiedades comunes de los campos de entidad para una aplicación basada en modelos utilizando el explorador de soluciones de Power Apps o el portal Power Apps. El portal de Power Apps proporciona una forma fácil de crear y de editar campos de entidad con Common Data Service.
El portal permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones.

## <a name="common-field-properties-in-power-apps-portal"></a>Propiedades de campos comunes en un portal Power Apps

1. Desde el [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Datos** > **Entidades** y seleccione la entidad que tiene los campos que desea ver.

2. Seleccione el campo que desea ver.

    > [!div class="mx-imgBorder"]
    > <img src="media/common-field-prop-powerapps.png" alt="Common field properties in Power Apps portal" height="658" width="300">


En la siguiente tabla se describen las propiedades comunes de los campos. Determinados tipos de campos tienen propiedades especiales. Estos se describen en [Crear y editar campos para Common Data Service](../common-data-service/create-edit-field-portal.md).

 |Propiedad|Descripción|
 |--|--|
 |**Nombre para mostrar**|El texto que se muestra para el campo en la interfaz de usuario.|
 |**Nombre**|El nombre único en el entorno. Se generará un nombre para usted basado en el nombre para mostrar que ha especificado, pero puede editarlo antes de guardar. Una vez que un campo se crea el nombre no se puede cambiar, ya que se puede hacer referencia a él en sus aplicaciones o código. El nombre tendrá el prefijo de personalización para su **Editor predeterminado de Common Data Service** antepuesto.|
 |**Tipo de datos**|Controla cómo se almacenan los valores y también cómo se formatean en algunas aplicaciones. Una vez que se guarda un campo, no puede cambiar el tipo de datos excepto convertir campos de texto a campos de numeración automática.|
 |**Obligatorio**| Un registro no se puede guardar sin datos en este campo. |
 |**Búsqueda**| Este campo aparece en Búsqueda avanzada y está disponible cuando se personalizan las vistas. |
 |**Calculado o consolidado**| Úselo para automatizar cálculos manuales. Use valores, fechas o texto.|
 |**Opciones avanzadas**| Agregue una descripción y especifique una longitud máxima y el modo IME para el campo.

Hay muchos diferentes tipos de campos, pero solo puede crear algunos. Para obtener más información sobre todos los tipos de campos, consulte [Tipos de campos y tipos de datos de campo](../common-data-service/types-of-fields.md). Puede establecer opciones adicionales en función de su elección de **Tipo de datos**.

## <a name="common-field-properties-in-solution-explorer"></a>Propiedades de campo común en el explorador de soluciones
 
Los campos de un formulario muestran controles que los usuarios utilizan para ver o modificar datos de un registro de entidad. Los campos pueden formatearse para ocupar hasta cuatro columnas en una sección.  

Puede acceder a **Propiedades comunes de los campos** en el explorador de soluciones. En **Componentes**, expanda **Entidades**, expanda la entidad que desea y luego seleccione **Formularios**. En la lista de formularios, abra el formulario de tipo **Principal**. A continuación, haga doble clic en uno de los campos para ver las propiedades comunes de los campos.

![Propiedades de campo común en el explorador de soluciones](media/common-field-properties.png "Propiedades de campo común en el explorador de soluciones")
  
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
