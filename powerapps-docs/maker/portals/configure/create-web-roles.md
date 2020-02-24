---
title: Crear roles web para un portal | MicrosoftDocs
description: Instrucciones para crear roles web para un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ccaf34d6ea0789ae1216ab5a240d85e58f701e41
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977817"
---
# <a name="create-web-roles-for-portals"></a>Crear roles web para portales

Una vez que se ha configurado un contacto para usar en el portal, debe recibir uno o varios roles web para realizar acciones especiales o tener acceso a contenido protegido en el portal. Por ejemplo, para acceder a una página restringida, el contacto debe asignarse a un rol con lectura restringida para esa página. Para publicar contenido nuevo, el contacto se debe colocarse en un rol que reciba permisos de publicación de contenido.

Para crear un rol web:

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Roles web**.
    Como alternativa, también puede abrir la página **Roles web** del panel [Compartir](../manage-existing-portals.md#share). 

3. Seleccione **Nuevo**.

4. Especifique los valores adecuados en los campos.

5. Seleccione **Guardar**.

## <a name="attributes-and-relationships"></a>Atributos y relaciones

La tabla siguiente explica los atributos de rol web que usan los portales.

| Nombre                     | Descripción                                                                                                                                                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre                     | Nombre descriptivo del rol web                                                                                                                                                                                                            |
| Sitio web                  | Sitio web asociado                                                                                                                                                                                                                          |
| Descripción              | Una explicación del objetivo del rol web. Opcional.                                                                                                                                                                                             |
| Rol de usuarios autenticados | Booleano. Si se establece como true, será el rol web predeterminado para usuarios autenticados (consulte a continuación). Sólo un rol web con el atributo Rol de usuarios autenticados establecido como true debe existir para un sitio web determinado. Este será el rol web predeterminado para usuarios autenticados que no se les ha asignado ningún rol web. |
| Rol del usuario anónimo     | Booleano. Si se establece como true, será el rol web predeterminado para usuarios no autenticados (consulte a continuación). Sólo un rol web con el atributo Rol de usuarios anónimos establecido como true debe existir para un sitio web determinado. Será el rol web predeterminado para usuarios no autenticados. El Rol de usuarios anónimos respetará solo Permisos de entidad.| 
|| 

Ahora que se creó el rol web, podrá configurarlo para satisfacer sus necesidades mediante diferentes permisos, reglas y asociaciones.

- **Rol web predeterminado opcional para usuarios autenticados**: Al habilitar **Rol de usuarios autenticados**, se convertirá en el rol web predeterminado para todos los usuarios. Este rol suele utilizarse para proporcionar un acceso predeterminado para los usuarios que no están asociados a otros roles. Tenga en cuenta que los usuarios pueden tener varios roles web, pero sólo puede haber un rol web de usuarios autenticados para los usuarios autenticados.
- **Rol web predeterminado opcional para usuarios no autenticados**: El **Rol de usuarios anónimos** está diseñado para usarse con permisos de la entidad. No respetará ninguna otra regla o permiso. Si habilita el "Rol de usuarios anónimos", se convertirá en el rol web predeterminado de todos los usuarios. Sólo puede haber un rol web de usuarios anónimos para usuarios no autenticados.

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md) <br>
[Controlar el acceso a páginas web para los portales](webpage-access-control.md)  
[Agregar seguridad basada en registros utilizando los permisos de entidad para portales](assign-entity-permissions.md) <br>
