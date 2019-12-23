---
title: Crear y administrar estados de publicación en portales de Power Apps | MicrosoftDocs
description: Aprenda a crear y administrar estados de publicación en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5ba33887a0b99cc3ddf1eb118ca506a9b740d015
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883943"
---
# <a name="create-and-manage-publishing-states"></a>Crear y administrar estados de publicación

Los estados de publicación permiten definir un ciclo de vida de contenida en el sitio web de los portales. A nivel básico, un estado de publicación puede determinar si una entidad asociada debe considerarse visible/publicada en un portal. En configuraciones más complejas, pueden definir un proceso de varias fases para la revisión de contenido y la publicación, con restricciones de seguridad en cada fase.

Los estados de publicación pueden usarse con [páginas web](web-page.md), [archivos web](web-files.md), [vínculos web](manage-web-links.md), foros y anuncios.

De forma predeterminada, hay dos estados de publicación disponibles: Borrador y Publicado. Borrador especifica el contenido que no debe estar visible a los usuarios de autores sin contenido, mientras que Publicado especifica el contenido que debe ser visible a todos los usuarios del portal (excepto otras restricciones de seguridad). Puede modificar la configuración predeterminada para cumplir con sus requisitos específicos, si lo desea, agregando nuevos estados o cambiando el nombre de ellos.

## <a name="manage-publishing-states"></a>Administrar estados de publicación

Los estados de publicación se pueden crear, editar y eliminar en los portales.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Páginas web**.

3. Seleccione el sitio web para administrar estados de publicación.

4. Vaya a la pestaña **Estados de publicación**. Se muestra la lista de estados de publicación disponibles.

    > [!div class=mx-imgBorder]
    > ![Administrar estados de publicación](../media/publishing-states.png "Administrar estados de publicación")

5. Para agregar un nuevo estado de publicación, seleccione **Nuevo estado de publicación**.

6. Para editar un estado de publicación existente, seleccione el nombre de estado de publicación.

7. En la ventana Estado de publicación, especifique los valores apropiados en los campos.

8. Seleccione **Guardar y cerrar**.


### <a name="publishing-state-attributes"></a>Atributos de estado de publicación

|Nombre|Descripción|
|-----|--------|
|Nombre|El nombre descriptivo del estado. Este campo es obligatorio.|
|Sitio web|Sitio web al que pertenece el estado. Este campo es obligatorio.|
|Es predeterminada|Si se activa, designa este estado como el estado predeterminado para el sitio web. Esto determinará el estado predeterminado seleccionado al crear nuevas entidades a través de la interfaz de edición delantera del portal.<br>**Nota**: Solo un estado de publicación en un sitio web determinado debe marcarse como estado predeterminado.|
|Está visible|Si está activado, designa que las entidades asociadas a este estado se considerarán visibles (o publicadas) en el portal.<br>Mientras una entidad asociada con un estado no visible no aparecerá en el portal, una entidad asociada a un estado visible puede no aparecer debido a permisos de seguridad, fechas de caducidad u otras reglas de visibilidad.<br>A los usuarios con los permisos de administración de contenido se les puede conceder la capacidad de usar el modo de vista previa, que permite que a estos usuarios ver (obtener una vista previa) contenido sin publicar.|
|Orden de visualización|Un valor entero que indica el orden en el que se colocará el estado, en las listas desplegables y menús para la selección de un estado de publicación: que se encuentra principalmente en las interfaces de edición delanteras del portal.|
|||

## <a name="publishing-state-transition-rules"></a>Reglas de transición del estado de publicación

Las reglas de transición del estado de publicación permiten realizar un control granular a través del que los roles web tienen derecho a hacer que el contenido cambie en el portal en términos de estado de publicación.

Para ser preciso, las reglas de transición de estado de publicación rigen las transacciones entre los estados de publicación (Borrador o Publicado). Cuando un usuario intenta cambiar el estado de publicación de un elemento de uno a otro, si existe una regla para esta transición, el proveedor de seguridad validará que el rol web para el usuario que inició sesión tenga permiso para realizar esta transición.

Si el usuario que inició sesión que está intentando realizar el cambio se encuentra en algunos de los roles que ha asignado a la regla, la transición será correcta. Si un usuario no dispone de permisos para realizar un cambio de una regla a otra, la edición delantera no les permitirá realizar ese cambio. También puede crear la regla y, a medida que crea roles web, agregar la regla a otros roles web. Una regla puede asociarse a cualquier número de roles web y viceversa.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Reglas de transición del estado de publicación**.

3. Para crear una nueva regla, seleccione **Nuevo**.

4. Para editar una regla existente, seleccione el nombre de regla.

5. En la ventana Regla de transición del estado de publicación, especifique los valores correspondientes en los campos.

6. Seleccione **Guardar** para poder continuar agregando roles web en ella.

    > [!div class=mx-imgBorder]
    > ![Crear regla de transición del estado publicación](../media/publishing-state-transition-rule.png "Crear regla de transición del estado publicación")

7. Sobre las pestaña **Roles web**, seleccione **Agregar rol web existente**. En el panel **Buscar registros**, busque y agregue los roles web apropiados.

8. Seleccione **Guardar**.

## <a name="state-based-control-rules"></a>Reglas de control basadas en estados

Las [reglas de control de acceso de página web](webpage-access-control.md) se pueden vincular a los estados de publicación para permitir o denegar el derecho a ver o modificar contenido basado en la rama del sitio web y el estado de publicación del contenido de esa rama. Para lograrlo, asocie una regla de control de acceso de la página web con un estado de publicación. Una vez que se asocie a un estado de publicación, la regla solo se aplicará a las páginas web cuando ese estado de publicación esté activo.

Por ejemplo, supongamos que quería que alguien con el rol de publicación de contenido pudiera modificar el contenido de la página, pero solo cuando esa página esté en el modo Borrador.  Esto garantizaría que los cambios en la página no se realizan mientras la página esté "en vivo" y permitiría que se realizara un proceso de aprobación en los cambios pendientes.

Para ello, debería crear una regla con el permiso de concesión de cambio y aplicarla a la rama en cuestión (en la página principal si la regla se va a aplicar a todo el sitio). A continuación, podría asociar esta regla al estado Borrador.

> [!div class=mx-imgBorder]
> ![Crear reglas de control basadas en estados](../media/state-based-control-rule.png "Crear reglas de control basadas en estados")

A continuación, puede asociar esta regla al rol web adecuado, por ejemplo, a la publicación de contenido. Asumiendo que este rol web no está asociado a una regla más permisiva (es decir, una regla que concede cambios independientemente del estado de publicación), los usuarios con el rol web de publicación de contenido podrán modificar las páginas en el estado Borrador, pero no podrán modificarlas en el estado Publicado..
