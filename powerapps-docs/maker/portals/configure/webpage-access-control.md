---
title: Controlar el acceso a la página web para un portal | MicrosoftDocs
description: Instrucciones para crear reglas de control de acceso de páginas web para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5046f136d62a4a44618f66f60f72ab5166274264
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551080"
---
# <a name="control-webpage-access-for-portals"></a>Control del acceso a la página web para portales

Las reglas de control de acceso de las páginas web son reglas que se crean para el sitio con el fin de controlar las acciones de publicación que puede realizar un rol Web en las páginas del sitio web y controlar qué páginas son visibles para los roles Web. La entidad acceso a la página web tiene los siguientes atributos:


|    Nombre     |                                                                                                                                                                  Descripción                                                                                                                                                                   |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Nombre     |                                                                                                                                                        Un nombre descriptivo para la regla.                                                                                                                                                        |
|   Bsitio   |                                                                                                           El sitio web al que se aplica esta regla; debe coincidir con el sitio web de la página a la que se aplica esta regla. Página Web de filtros.                                                                                                           |
|  Página Web   |                            La página web a la que se aplica esta regla. La regla no solo afectará a la página sino a todas las páginas secundarias, por lo que este atributo selecciona la rama del sitio web al que se aplicará la regla. Si se aplica una regla a la Página principal, se aplicará a todo el portal.                            |
|    Right    |                                                                                                                                    [Conceda el cambio](#grant-change) o [restrinja la lectura](#restrict-read) a continuación.                                                                                                                                     |
|    Ámbito    | <ul><li><strong>Todo el contenido</strong>: todo el contenido descendiente se incluye en la validación de seguridad.</li><li><strong>Excluir archivos Web secundarios directos</strong>: todos los archivos Web secundarios relacionados directamente con esta página web se excluyen de la validación de seguridad. Esto no excluye los descendientes de los secundarios.</li></ul>De forma predeterminada, se selecciona todo el contenido. |
| Descripción |                                                                                                                                                     Opta Una descripción de la regla.                                                                                                                                                      |

Después de crear una nueva regla de control de acceso, asóciela a una página. Esto hará que afecte a la página a la que se asigna la regla y a todas las páginas secundarias&mdash;en otras palabras, toda la rama del sitio Web.

Hay dos tipos de reglas de control de acceso: Grant Change y Restrict Read.

## <a name="grant-change"></a>Conceder cambio

Grant Change permite a un usuario de un rol Web asociado a la regla publicar cambios de contenido para esta página y todas las páginas secundarias de esta página. Grant Change tiene prioridad sobre Restrict Read. Por ejemplo, es posible que tenga una sección de noticias del sitio que desee que sea editable por los usuarios en el rol Web editor de noticias. Es posible que estos usuarios no tengan acceso a todo el sitio y, en realidad, no puedan editar todo el sitio, pero dentro de esta rama tienen una entidad de publicación de contenido completa. Crearía una regla de control de acceso de página web denominada conceder publicación de noticias a los editores de noticias.

A continuación, debe establecer el derecho para conceder el cambio y la página web en la página primaria de la rama de noticias completa del sitio. A continuación, asignaría este rol Web a los contactos que quieras designar como editores de noticias. Tenga en cuenta que un usuario puede tener muchos roles Web.

Una regla de cambio de concesión siempre debe estar presente en cualquier portal en el que desee habilitar la edición frontal. Esta regla se aplicará a la Página principal del sitio, lo que la convierte en la regla predeterminada para todo el sitio. Esta regla se asociará a un rol Web que represente el rol administrativo para el sitio. A los usuarios a los que se les asignarán derechos de publicación de contenido front-end se les asignará este rol.

## <a name="restrict-read"></a>Restringir lectura
La regla restringir lectura se usa para limitar la visualización de una página (y sus páginas secundarias) y su contenido a usuarios específicos. Mientras que Grant Change es una regla permisiva (concede la posibilidad de hacer algo a sus usuarios), restringir la lectura es una regla restrictiva, ya que restringe una acción a un conjunto limitado de usuarios. Por ejemplo, podría tener una sección del sitio pensada para que la usen únicamente los empleados. Puede restringir la lectura de esta rama solo a personas del rol Web de empleado. Debe crear una nueva regla denominada restringir lectura solo a los empleados.

A continuación, debe establecer el derecho para restringir la lectura y la página a la página en la parte superior de la rama que solo van a ser leídas por los empleados. A continuación, asociaría esta regla con el rol Web de empleado y, a continuación, asignaría usuarios a este rol.

> [!Note]
> Si aplica el derecho **restringir lectura** a la página raíz "Inicio" de un sitio web y selecciona **excluir los archivos Web secundarios directos** como **ámbito**, todos los usuarios podrán acceder a los archivos Web secundarios directos de la Página principal.

### <a name="see-also"></a>Vea también

[Crear roles web para portales](create-web-roles.md)  
[Agregar seguridad basada en registros mediante permisos de entidad para portales](assign-entity-permissions.md)
