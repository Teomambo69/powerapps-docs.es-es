---
title: Configurar los pasos de un formulario web para un portal | MicrosoftDocs
description: Instrucciones para crear un paso de formulario web para un formulario web en un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761099"
---
# <a name="define-web-form-steps-for-portals"></a>Definir pasos de formulario web para portales

El paso de formulario web proporciona la lógica de flujo de la experiencia del usuario del formulario, como pasos y rama condicional. También proporcionó detalles acerca de la representación de un formulario y comportamiento adicional.

> [!NOTE]
> Los formularios web mantienen el historial de los pasos que un usuario ha visitado en un objeto de una entidad Sesión de formularios web. Si se han modificado los pasos de formulario web, los datos del historial creados previamente podrían estar ahora desfasados. En el momento que se cambian los pasos, se recomienda eliminar todos los registros de Sesión de formularios web para eliminar la falta de coincidencia entre la secuencia de pasos iniciado registrados en el historial y la secuencia actual.

Cada formulario web se presentará en el portal en uno o varios pasos. Estos pasos comparten algunos propiedades comunes, descritas a continuación. Cada paso contiene un puntero (una búsqueda) al siguiente paso, con la excepción de los pasos de terminal. Los pasos de terminal no tienen una próxima vez y, por tanto, son el último paso del formulario web (debido a ramas condicionales, puede haber múltiples pasos de terminal)

![Pasos para crear un formulario web](../media/web-form-creation-steps.png "Pasos para crear un formulario web")  

| Nombre     | Descripción                                    |
|----------|------------------------------------------------|
| Nombre     | Un título usado para referencia.                    |
| Formulario web | El formulario web asociado con el paso actual. |
|Tipo|Uno de los siguientes:<br>[Tipo de paso Cargar formulario/Cargar pestaña](load-form-step.md): muestra propiedades de formularios. <ul><li>[Tipo de paso Cargar formulario/Cargar pestaña](load-form-step.md): muestra propiedades de pestañas.</li><li>[Tipo de paso condicional](add-conditional-step.md): muestra propiedades para especificar expresiones que se evaluarán para ramas condicionales. </li><li>[Tipo del paso de redireccionamiento](add-redirect-step.md): muestra los valores adecuados para configurar una redirección de sitio web.</li></ul><br>Para obtener más detalles sobre los valores de estos tipos de paso de formulario web, consulte las secciones correspondientes a continuación.<br>**Nota**: El primer paso no puede ser de tipo "Condición".|
| Paso siguiente                  | El paso que seguirá el paso actual. Será en blanco para un formulario de un solo paso.                                                                                                            |
| Nombre lógico de entidad de destino | El nombre lógico de la entidad asociada al formulario.                                                                                                                                               |
| Se permite mover anterior    | Indica si el usuario tiene una opción para desplazarse hasta el paso anterior en un formulario web de varios pasos. El valor predeterminado es true. Desactive para impedir que el usuario pueda desplazarse al paso anterior. |
||

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Definir entidad](entity-forms.md)  
[Tipo de paso Cargar formulario/Cargar pestaña](load-form-step.md)  
[Tipo del paso de redireccionamiento](add-redirect-step.md)  
[Tipo de paso condicional](add-conditional-step.md)  
[Agregar JavaScript personalizado](add-custom-javascript.md)  

