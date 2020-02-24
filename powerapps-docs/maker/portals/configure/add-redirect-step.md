---
title: Configurar un tipo de paso de redireccionamiento para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar un paso de redireccionamiento para un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e82d19a7adb43bcb8fddaeac88a5e238ee96eae1
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979621"
---
# <a name="add-a-redirect-step-type"></a>Agregar un tipo de paso de redireccionamiento

El tipo del paso de redireccionamiento permite redireccionar la sesión del explorador del usuario a otra página del portal o una dirección URL externa. Esto resulta útil para un flujo de direccionamiento integrado.

| Nombre                                                            | Descripción                                                                                                                                                                                  |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dirección URL externa                                                    | Requiere establecer En caso de éxito como Redirigir. Especifique una dirección URL a un recurso externo de la web.                                                                                                       |
| o página web                                                     | Requiere establecer En caso de éxito como Redirigir. Seleccione una página web desde el sitio web actual.                                                                                                             |
| Anexar cadena de consulta existente                                    | Requiere establecer En caso de éxito como Redirigir. Cuando está activada esta opción, los parámetros de cadena de consulta existente se agregarán a la dirección URL de destino antes del redireccionamiento.                                                 |
| Anexar id. de registro a la cadena de consulta                                | Requiere establecer En caso de éxito como Redirigir. Cuando está activada esta opción, el Id. del registro creado se anexa a cadena de consulta de la dirección URL a la que se está realizando el redireccionamiento.                                               |
| Nombre del parámetro de cadena de consulta de id. de registro                           | Requiere establecer En caso de éxito como Redirigir. El nombre del parámetro Id. de la cadena de consulta de la dirección URL a la que se está realizando el redireccionamiento.                                                                        |
| Anexar cadena de consulta personalizada                                      | Requiere establecer En caso de éxito como Redirigir. Una cadena personalizada que se puede anexar a la cadena de consulta existente de la dirección URL de redireccionamiento.                                                                  |
| Anexar valor de atributo a la cadena de consulta: nombre de parámetro         | Requiere establecer En caso de éxito como Redirigir. Un nombre para dar al parámetro que se correlaciona con el valor de atributo de la entidad de destino que se anexa a cadena de consulta de la dirección URL de redireccionamiento. |
| Anexar valor de atributo a la cadena de consulta: nombre lógico de atributo | Requiere establecer En caso de éxito como Redirigir. Un nombre lógico de un atributo en la entidad de destino para obtener el valor que se anexa a cadena de consulta de la dirección URL de redireccionamiento.                            |

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Pasos de formulario web para portales](web-form-steps.md)  
[Tipo de paso Cargar formulario/Cargar pestaña](load-form-step.md)  
[Tipo de paso condicional](add-conditional-step.md)  
[Agregar JavaScript personalizado](add-custom-javascript.md)  

