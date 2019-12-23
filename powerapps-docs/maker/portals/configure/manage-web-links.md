---
title: Administrar vínculos web en un portal | MicrosoftDocs
description: Instrucciones para administrar vínculos web.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: d8e2421545247f72b5b164e08b4ac210466048c1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866859"
---
# <a name="manage-web-links"></a>Administrar vínculos web

Un vínculo web puede vincular cualquier dirección URL o puede vincularse a otra página web dentro del mismo sitio web. Cuando un vínculo web se establece con una página web, la seguridad y el estado de publicación de la página web se aplicará también al vínculo web. Los vínculos web siempre forman parte de un conjunto de vínculos web. Un conjunto de vínculos web es un grupo de vínculos como una navegación principal o un grupo de vínculos de pie de página. Los conjuntos de vínculos web permiten que los vínculos internos, independientemente de su ubicación en el mapa del sitio, y externos se agrupen y ordenen.

## <a name="manage-web-links-in-power-apps-portals"></a>Administrar vínculos web en portales Power Apps

Una vez que las personalizaciones del portal se hayan importado en su entorno de Common Data Service, los vínculos web se pueden administrar desde un conjunto de vínculos web.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Conjuntos de vínculos web**.

3. Para crear un nuevo conjunto de vínculos web, seleccione **Nuevo**.

4. Para editar un conjunto de vínculos web existente, seleccione el nombre de conjunto de vínculos web.

5. Especifique los valores adecuados en los campos.

6. Si crea un nuevo conjunto de vínculos web, seleccione **Guardar** para guardar el registro de manera que pueda agregar vínculos web.

7. Vaya a la pestaña **Vínculos**.

8. Para crear un nuevo vínculo web, seleccione **Nuevo vínculo web**.

    ![Agregar vínculo web](../media/add-web-link.png "agregar vínculo web")

9. Para editar un vínculo web existente, seleccione el nombre del vínculo web.

9. Especifique los valores adecuados en los campos.

6. Guarde los cambios.

## <a name="web-link-set-attributes-and-relationships"></a>Atributos y relaciones de conjuntos de vínculos web

La tabla siguiente explica muchos de las propiedades de conjuntos de vínculos web estándar que usan los portales. Es importante observar que la forma en que se representan muchos de las propiedades orientadas a contenido/visualización está administrada por la plantilla de página web utilizada.

| Nombre    | Descripción                                                                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre    | Nombre descriptivo del conjunto de vínculos web. Este valor describe normalmente la ubicación del conjunto en la plantilla de página como Navegación principal. Este campo es obligatorio.                   |
| Sitio web | Sitio web al que pertenece la entidad. Este campo es obligatorio.                                                                                                                             |
| Puesto   | Título opcional para el conjunto de vínculos web. Este valor se puede usar en el portal si es parte de la plantilla de página. Podría ser algo como Nuestros asociados y aparecer en una barra lateral.    |
| Copiar    | Descripción opcional para el conjunto de vínculos web. Este valor se puede usar en el portal si es parte de la plantilla de página. Podría describir algo más como Nuestros asociados en una barra lateral. |
||

## <a name="web-link-attributes-and-relationships"></a>Atributos y relaciones de vínculos web

La tabla siguiente explica muchos de las propiedades de vínculos web estándar que usan los portales. Es importante observar que la forma en que se representan muchos de las propiedades orientadas a contenido/visualización está administrada por la plantilla de página web utilizada.


|           Nombre           |                                                                                                               Descripción                                                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Nombre           |                                                          El título para el vínculo web. Esta valor se usará como título del vínculo web en la mayoría de las plantillas. Este campo es obligatorio.                                                           |
|       Conjunto de vínculos web       |                                                                                  El conjunto de vínculos web al que pertenece la entidad. Este campo es obligatorio.                                                                                  |
|     Vínculo web principal      |                                      El vínculo web principal de la entidad, en un conjunto de vínculos web de varios niveles. Si no se especifica un vínculo web primario, la entidad está en el nivel superior/raíz del conjunto de vínculos web.                                      |
|           Página           |                                                                                          Una página web opcional del mismo sitio web con el que establecer un vínculo.                                                                                          |
|        Dirección URL externa      |                                                                                Una dirección URL opcional con la que vincular. Esta configuración puede ser cualquier dirección URL con formato correcto.                                                                                |
|       Descripción        |                                                              Resumen opcional para el vínculo web. Este valor se puede usar en el portal si es parte de la plantilla de página.                                                              |
|     Estado de publicación     | El estado actual de flujo de trabajo de publicación del vínculo web, que puede dictar si el vínculo web es visible en la ubicación. El uso más común de esta característica es proporcionar control de publicado/borrador sobre contenido. Este campo es obligatorio. |
|    Vínculo de seguimiento de robots    |                                                           Indica si los indizadores de búsqueda deben realizar el seguimiento e indizar el contenido del vínculo. Este campo es obligatorio.                                                            |
|      Orden de visualización       |                                                  Un valor de entero que indica el orden en que el vínculo web se colocará en relación con otros vínculos web en el mismo conjunto de vínculos web.                                                  |
| Mostrar vínculos secundarios de página |  En una plantilla que admite conjuntos de vínculos web de varios niveles, genere vínculos secundarios para esta entidad usando el proveedor del mapa del sitio del portal. Tenga en cuenta que esta opción solo es válida para los vínculos web que hacen referencia a páginas internas, no a direcciones URL externas.  |
|    Abrir en ventana nueva    |                                                                            Indica si al seleccionar el vínculo se cargará el vínculo en una nueva ventana del explorador.                                                                             |
| Deshabilitar validación de página  |                                                                       Indica si la seguridad de una página web vinculada se aplicará también al vínculo web.                                                                       |
|        URL de imagen         |                                                   Una dirección URL opcional de una imagen. La imagen vinculada se puede usar en el portal si forma parte de la plantilla de página; por ejemplo, como icono.                                                   |
|       Alto de la imagen       |                                                                                      Una altura opcional de la imagen de propiedad URL de imagen.                                                                                      |
|       Ancho de la imagen        |                                                                                      Una anchura opcional de la imagen de propiedad URL de imagen.                                                                                       |
|      Texto alternativo de la imagen      |                                                                                   Una descripción opcional de la imagen de propiedad URL de imagen.                                                                                    |
|    Mostrar solo imagen    |                                                   Indica que la plantilla solo debe representar un vínculo de imagen para este vínculo web, en lugar de la imagen y el nombre del vínculo juntos.                                                    |
|                          |                                                                                                                                                                                                                                         |

> [!Note]
> - Cuando un vínculo web se establece con una página web, la seguridad y el estado de publicación de la página web se aplicará también al vínculo web. Esta validación se puede deshabilitar con la opción Deshabilitar validación de página. 
>   - A los usuarios con los permisos de administración de contenido se les puede conceder la capacidad de usar el modo de vista previa, que permite que a estos usuarios ver (obtener una vista previa) contenido sin publicar.

### <a name="see-also"></a>Vea también

[Personalizar contenido utilizando fragmentos de contenido](customize-content-snippets.md)
