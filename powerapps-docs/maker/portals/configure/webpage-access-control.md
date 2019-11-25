---
title: Controlar el acceso a páginas web para un portal | MicrosoftDocs
description: Instrucciones para crear reglas de control de acceso a una página web para un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761100"
---
# <a name="control-webpage-access-for-portals"></a>Controlar el acceso a páginas web para los portales

Las reglas de control de acceso a páginas web son reglas que usted crea para el sitio, para controlar las acciones de publicación que un rol web puede realizar en las páginas del sitio web así como controlar qué páginas están visibles para qué roles web. La entidad de acceso a páginas web tiene los siguientes atributos:


|    Nombre     |                                                                                                                                                                  Descripción                                                                                                                                                                   |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Nombre     |                                                                                                                                                        Un nombre descriptivo para la regla.                                                                                                                                                        |
|   Sitio web   |                                                                                                           El sitio web al que se aplica esta regla; debe coincidir con el sitio web de la página al que se aplica esta regla. Página web Filtros.                                                                                                           |
|  Página web   |                            La página web a la que se aplica esta regla. La regla afectará no solo a la página sino a todas las páginas secundarias de la página, por consiguiente haciendo que este atributo seleccione la rama del sitio web al que se aplicará la regla. Si una regla se aplica a la página principal, se aplicará al portal completo.                            |
|    Derecho    |                                                                                                                                    [Conceder cambio](#grant-change) o [Restringir lectura](#restrict-read) a continuación.                                                                                                                                     |
|    Ámbito    | <ul><li><strong>Todo el contenido</strong>: Todo el contenido descendiente se incluye en la validación de seguridad.</li><li><strong>Excluir archivos web secundarios directos</strong>: todos los archivos web secundarios relacionados directamente con esta página web quedarán excluidos de la validación de seguridad. Esto no excluye los descendientes secundarios.</li></ul>La opción Todo el contenido se encuentra seleccionada de forma predeterminada. |
| Descripción |                                                                                                                                                     (Opcional) Agregue una descripción de la regla.                                                                                                                                                      |

Después de crear una nueva regla de control de acceso, asóciela a una página. Esto afectará a la página que tenga asignada la regla y a todas las páginas secundarias&mdash;es decir, la rama completa de la página web.

Hay dos tipos de reglas de control de acceso: Conceder cambio y Restringir lectura.

## <a name="grant-change"></a>Conceder cambio

Conceder cambio permite al usuario en un rol web asociado a la regla publicar cambios de contenido para esta página y todas las páginas secundarias de esta página. Conceder cambio tiene prioridad sobre restringir lectura. Por ejemplo, podría tener una sección de noticias del sitio que quiere que los usuarios puedan editar en el rol web editor de noticias. Estos usuarios pueden no tener acceso al sitio completo, y sin duda no pueden modificar el sitio completo, pero en esta rama tienen autoridad completa de publicación de contenido. Crearía un control de acceso a páginas web llamado conceder publicación de noticias a editores de noticias.

A continuación, establecería el derecho como conceder cambio y la página web como la página principal de toda la rama de novedades del sitio. Después asignaría este rol web a los contactos que desee designar como editores de noticias. Tenga en cuenta que un usuario puede tener muchos roles web.

Una regla Conceder cambio siempre debe estar presente en cualquier portal para el que desee habilitar la edición del lado frontal. Esta regla se aplicará a la página principal del sitio, convirtiéndola así en la regla predeterminada para el sitio completo. Esta regla se asociará con un rol web que deberá representar el rol administrativo del sitio. Se asignará este rol a los usuarios a los que se conceden derechos de publicación de contenido del lado frontal.

## <a name="restrict-read"></a>Restringir lectura
Se usa la regla Restringir lectura para limitar la vista de una página (y sus páginas secundarias) y su contenido a usuarios específicos. Mientras que conceder cambio es una regla permisiva (concede la capacidad de hacer algo a los usuarios), la regla Restringir lectura es una regla restrictiva, ya que restringe una acción a un conjunto limitado de usuarios. Por ejemplo, podría tener una sección del sitio destinada a que la utilicen los empleados solo. Puede restringir la lectura de esta rama únicamente a aquellas personas con el rol web empleado. Se crearía una nueva regla llamada restringir lectura a empleados solo.

A continuación se establecería el derecho como restringir lectura y la página como la página en la parte superior de la rama que será de solo lectura para los empleados. Después asociaría esta regla con el rol web de empleado y asignaría usuarios a este rol.

> [!Note]
> Si se aplica el derecho de **Restringir lectura** a la página "principal" raíz de una página web y se selecciona **Excluir archivos web secundarios directos** como el **Ámbito**, todos los usuarios podrán acceder a los archivos web secundarios directos de la página principal.

### <a name="see-also"></a>Vea también

[Crear roles web para portales](create-web-roles.md)  
[Agregar seguridad basada en registros utilizando los permisos de entidad para portales](assign-entity-permissions.md)
