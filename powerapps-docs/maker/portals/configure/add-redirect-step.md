---
title: Configuración de un tipo de paso de redirección para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar un paso de redirección para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cf76cccfd247bdcfb4ee32e99682d2b9e95e139
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553518"
---
# <a name="add-a-redirect-step-type"></a>Agregar un tipo de paso de redireccionamiento

El tipo de paso de redireccionamiento permite que se redirija la sesión del explorador del usuario a otra página del portal o a una dirección URL externa. Esto resulta útil para dirigir el flujo sin problemas.

| Nombre                                                            | Descripción                                                                                                                                                                                  |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dirección URL externa                                                    | Requiere en la operación correcta establecida en redirigir. Especifique una dirección URL a un recurso externo en la Web.                                                                                                       |
| o página web                                                     | Requiere en la operación correcta establecida en redirigir. Seleccione una página web del sitio web actual.                                                                                                             |
| Anexar cadena de consulta existente                                    | Requiere en la operación correcta establecida en redirigir. Cuando se activa esta opción, los parámetros de cadena de consulta existentes se agregarán a la dirección URL de destino antes de la redirección.                                                 |
| Anexar el ID. de registro a la cadena de consulta                                | Requiere en la operación correcta establecida en redirigir. Cuando se comprueba, el ID. del registro creado se anexa a la cadena de consulta de la dirección URL a la que se redirige.                                               |
| Nombre de parámetro de cadena de consulta de ID. de registro                           | Requiere en la operación correcta establecida en redirigir. Nombre del parámetro de identificador en la cadena de consulta de la dirección URL a la que se redirige.                                                                        |
| Anexar cadena de consulta personalizada                                      | Requiere en la operación correcta establecida en redirigir. Una cadena personalizada que se puede anexar a la cadena de consulta existente de la dirección URL de redireccionamiento.                                                                  |
| Anexar el valor del atributo a la cadena de consulta: nombre del parámetro         | Requiere en la operación correcta establecida en redirigir. Nombre que se va a asignar al parámetro que se correlaciona con el valor de atributo de la entidad de destino que se anexa a la cadena de consulta de la dirección URL de redireccionamiento. |
| Anexar el valor del atributo a la cadena de consulta: nombre lógico del atributo | Requiere en la operación correcta establecida en redirigir. Nombre lógico de un atributo de la entidad de destino para obtener el valor que se va a anexar a la cadena de consulta de la dirección URL de redireccionamiento.                            |

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Pasos de Web Form para portales](web-form-steps.md)  
[Tipo de paso cargar formulario/pestaña carga](load-form-step.md)  
[Tipo de paso condicional](add-conditional-step.md)  
[Agregar JavaScript personalizado](add-custom-javascript.md)  

