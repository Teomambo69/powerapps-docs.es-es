---
title: Crear roles web para un portal | MicrosoftDocs
description: Instrucciones para crear roles web para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3e8bb144ad338131cccd1be774e8c3f8000f510b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552897"
---
# <a name="create-web-roles-for-portals"></a>Crear roles web para portales

Una vez configurado un contacto para usar el portal, debe tener uno o varios roles web para realizar cualquier acción especial o tener acceso a cualquier contenido protegido en el portal. Por ejemplo, para tener acceso a una página restringida, el contacto debe estar asignado a un rol al que se limite la lectura de esa página. Para publicar contenido nuevo, el contacto debe colocarse en un rol que tenga permisos de publicación de contenido.

Para crear un rol Web:

1. Abra la [aplicación administración del portal](configure-portal.md).

2. Vaya a **portales** > **roles web**.
    Como alternativa, también puede abrir la página **roles web** desde el panel [compartir](../manage-existing-portals.md#share) . 

3. Seleccione **Nueva**.

4. Escriba los valores adecuados en los campos.

5. Seleccione **Guardar**.

## <a name="attributes-and-relationships"></a>Atributos y relaciones

En la tabla siguiente se explican los atributos de rol Web que usan los portales.

| Nombre                     | Descripción                                                                                                                                                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre                     | Nombre descriptivo del rol Web.                                                                                                                                                                                                            |
| Bsitio                  | El sitio web asociado                                                                                                                                                                                                                          |
| Descripción              | Explicación del propósito del rol Web. Opcional.                                                                                                                                                                                             |
| Rol usuarios autenticados | Booleano. Si se establece en true, será el rol Web predeterminado para los usuarios autenticados (consulte a continuación). Solo debe existir un rol Web con el atributo de rol usuarios autenticados establecido en true para un sitio Web determinado. Este será el rol Web predeterminado para los usuarios autenticados a los que no se ha asignado un rol Web. |
| Rol de usuarios anónimos     | Booleano. Si se establece en true, será el rol Web predeterminado para los usuarios no autenticados (consulte a continuación). Solo debe existir un rol Web con el atributo de rol usuarios anónimos establecido en true para un sitio Web determinado. Este será el rol Web predeterminado para los usuarios no autenticados. El rol usuarios anónimos solo respetará los permisos de entidad.| 
|| 

Ahora que se ha creado el rol Web, podrá configurarlo para satisfacer sus necesidades a través de varios permisos, reglas y asociaciones.

- **Rol Web predeterminado opcional para usuarios autenticados**: al habilitar el **rol usuarios autenticados**, se convertirá en el rol Web predeterminado para todos los usuarios. Este rol se usa normalmente para proporcionar un acceso predeterminado para los usuarios que no están asociados a ningún otro rol. Tenga en cuenta que los usuarios pueden tener varios roles Web, pero solo puede haber un rol Web usuarios autenticados para usuarios autenticados.
- **Rol Web predeterminado opcional para los usuarios no autenticados**: el **rol usuarios anónimos** está pensado para usarse con permisos de entidad. No respetará las demás reglas o permisos. Al habilitar el "rol de usuarios anónimos", se convertirá en el rol Web predeterminado para todos los usuarios. Solo puede haber un rol Web usuarios anónimos para usuarios no autenticados.

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md) <br>
[Control del acceso a la página web para portales](webpage-access-control.md)  
[Agregar seguridad basada en registros mediante el uso de permisos de entidad para portales](assign-entity-permissions.md) <br>
