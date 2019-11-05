---
title: Configuración de los pasos de un formulario web para un portal | MicrosoftDocs
description: Instrucciones para crear un paso de formulario Web Forms para un formulario Web Forms en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c81cddb771c98ccecf2be206ab45a8271ff3559d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551241"
---
# <a name="define-web-form-steps-for-portals"></a>Definir pasos de formularios Web para portales

El paso del formulario web proporciona la lógica de flujo de la experiencia del usuario del formulario, como pasos y bifurcación condicional. También se proporcionan detalles sobre la representación de un formulario y el comportamiento adicional.

> [!NOTE]
> Los formularios Web Forms conservan el historial de los pasos que ha visitado un usuario en un objeto de una entidad de sesión de formularios Web Forms. Si los pasos de un formulario web se han modificado, los datos del historial creados anteriormente podrían estar ahora obsoletos. En cualquier momento, se recomienda que elimine todos los registros de la sesión de formularios Web Forms para eliminar la coincidencia de errores entre la secuencia de los pasos registrados en el historial y la secuencia actual.

Cada formulario web se presentará en el portal con uno o varios pasos. Estos pasos comparten algunas propiedades comunes, que se describen a continuación. Cada paso contiene un puntero (una búsqueda) al paso siguiente, con la excepción de los pasos de terminal. Los pasos de terminal no tienen una próxima vez y, por tanto, son el último paso del formulario web (debido a la bifurcación condicional, puede haber varios pasos de terminal)

![Pasos para crear un formulario Web Forms](../media/web-form-creation-steps.png "Pasos para crear un formulario Web Forms")  

| Nombre     | Descripción                                    |
|----------|------------------------------------------------|
| Nombre     | Título que se usa como referencia.                    |
| Formulario web | Formulario web asociado al paso actual. |
|Tipo|Una de las siguientes opciones:<br>[Tipo de paso cargar formulario/pestaña carga](load-form-step.md): muestra las propiedades de los formularios. <ul><li>[Tipo de paso cargar formulario/pestaña carga](load-form-step.md): muestra las propiedades de las pestañas.</li><li>[Tipo de paso condicional](add-conditional-step.md): muestra las propiedades para especificar las expresiones que se van a evaluar para la bifurcación condicional. </li><li>[Tipo de paso de redirección](add-redirect-step.md): muestra la configuración adecuada para configurar el redireccionamiento de un sitio Web.</li></ul><br>Para obtener más detalles sobre la configuración de estos tipos de paso de formularios Web Forms, consulte las secciones correspondientes a continuación.<br>**Nota**: el primer paso no puede ser de tipo "Condition".|
| Paso siguiente                  | El paso que va a seguir el paso actual. Estará en blanco para una única forma de un solo paso.                                                                                                            |
| Nombre lógico de la entidad de destino | Nombre lógico de la entidad asociada al formulario.                                                                                                                                               |
| Desplazamiento anterior permitido    | Indica si se proporciona al usuario una opción para ir al paso anterior en un formulario web de varios pasos. El valor predeterminado es true. Desactive esta casilla para evitar que el usuario pueda pasar al paso anterior. |
||

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Definir entidad](entity-forms.md)  
[Tipo de paso cargar formulario/pestaña carga](load-form-step.md)  
[Tipo de paso de redirección](add-redirect-step.md)  
[Tipo de paso condicional](add-conditional-step.md)  
[Agregar JavaScript personalizado](add-custom-javascript.md)  

