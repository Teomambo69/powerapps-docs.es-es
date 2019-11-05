---
title: Administrar vínculos Web | MicrosoftDocs
description: Instrucciones para administrar vínculos Web.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5d0ead5104765ab71848ffcf8c4aaff801a58a20
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551793"
---
# <a name="manage-web-links"></a>Administrar vínculos Web

Un vínculo Web puede vincular a cualquier dirección URL o puede vincularse a otra página web dentro del mismo sitio Web. Cuando un vínculo Web se encuentra en una página web, el estado de seguridad y publicación de la página web también se aplica al vínculo Web. Los vínculos Web siempre forman parte de un conjunto de vínculos Web. Un conjunto de vínculos Web es un grupo de vínculos, como una navegación principal o un grupo de vínculos de pie de página. Los conjuntos de vínculos Web permiten el uso interno, independientemente de la ubicación del mapa del sitio, y los vínculos externos que se agrupan y ordenan.

## <a name="manage-web-links-in-powerapps-portals"></a>Administrar vínculos Web en portales de PowerApps

Una vez que se han importado las personalizaciones del portal en el entorno de Common Data Service, los vínculos Web se pueden administrar desde un conjunto de vínculos Web.

1. Abra la [aplicación administración del portal](configure-portal.md).

2. Vaya a **portales** > **conjuntos de vínculos Web**.

3. Para crear un nuevo conjunto de vínculos Web, seleccione **nuevo**.

4. Para editar un conjunto de vínculos Web existente, seleccione el nombre del conjunto de vínculos Web.

5. Escriba los valores adecuados en los campos.

6. Si crea un nuevo conjunto de vínculos Web, seleccione **Guardar** para guardar el registro de forma que pueda agregar vínculos Web.

7. Vaya a la pestaña **vínculos** .

8. Para crear un nuevo vínculo Web, seleccione **nuevo vínculo Web**.

    ![Agregar vínculo Web](../media/add-web-link.png "Agregar vínculo Web")

9. Para editar un vínculo Web existente, seleccione el nombre del vínculo Web.

9. Escriba los valores adecuados en los campos.

6. Guarde los cambios.

## <a name="web-link-set-attributes-and-relationships"></a>Atributos y relaciones del conjunto de vínculos Web

En la tabla siguiente se explican muchas de las propiedades de conjunto de vínculos Web estándar que utilizan los portales. Es importante tener en cuenta que la plantilla de página utilizada controla el modo en que muchas de las propiedades orientadas a contenido y de presentación se representan.

| Nombre    | Descripción                                                                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre    | Nombre descriptivo del conjunto de vínculos Web. Este valor suele describir la colocación del conjunto en la plantilla de página, como la navegación principal. Este campo es obligatorio.                   |
| Bsitio | Sitio web al que pertenece la entidad. Este campo es obligatorio.                                                                                                                             |
| Título   | Título opcional para el conjunto de vínculos Web. Este valor se puede usar en el portal si forma parte de la plantilla de página. Podría ser algo parecido a nuestros asociados y mostrarse en una barra lateral.    |
| Copiar    | Una descripción opcional del conjunto de vínculos Web. Este valor se puede usar en el portal si forma parte de la plantilla de página. Podría describir algo parecido a nuestros asociados en una barra lateral. |
||

## <a name="web-link-attributes-and-relationships"></a>Atributos y relaciones de vínculos Web

En la tabla siguiente se explican muchas de las propiedades de vínculo Web estándar que utilizan los portales. Es importante tener en cuenta que la plantilla de página utilizada controla el modo en que muchas de las propiedades orientadas a contenido y de presentación se representan.


|           Nombre           |                                                                                                               Descripción                                                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Nombre           |                                                          Título del vínculo Web. Este valor se usará como título del vínculo Web en la mayoría de las plantillas. Este campo es obligatorio.                                                           |
|       Conjunto de vínculos Web       |                                                                                  Conjunto de vínculos Web al que pertenece la entidad. Este campo es obligatorio.                                                                                  |
|     Vínculo Web primario      |                                      Vínculo Web primario de la entidad, en un conjunto de vínculos Web multinivel. Si no se especifica ningún vínculo Web primario, la entidad se encuentra en el nivel superior/raíz del conjunto de vínculos Web.                                      |
|           del           |                                                                                          Una página web opcional del mismo sitio web al que se va a vincular.                                                                                          |
|        Dirección URL externa      |                                                                                Dirección URL opcional a la que se va a vincular. Este valor puede ser cualquier dirección URL con el formato correcto.                                                                                |
|       Descripción        |                                                              Un resumen opcional para el vínculo Web. Este valor se puede usar en el portal si forma parte de la plantilla de página.                                                              |
|     Estado de publicación     | Estado actual del flujo de trabajo de publicación del vínculo Web, que puede determinar si el vínculo Web está visible en el sitio. El uso más común de esta característica es proporcionar un control publicado o borrador sobre el contenido. Este campo es obligatorio. |
|    Vínculo de seguimiento de robots    |                                                           Indica si los indizadores de búsqueda deben seguir o no el contenido del vínculo. Este campo es obligatorio.                                                            |
|      Mostrar orden       |                                                  Un valor entero que indica el orden en el que se colocará el vínculo Web, en relación con otros vínculos Web dentro del mismo conjunto de vínculos Web.                                                  |
| Mostrar vínculos secundarios de la página |  En una plantilla que admita conjuntos de vínculos Web multinivel, genere vínculos secundarios para esta entidad mediante el proveedor del mapa del sitio del portal. Tenga en cuenta que esta opción solo es válida para los vínculos Web que hacen referencia a páginas internas y no a direcciones URL externas.  |
|    Abrir en nueva ventana    |                                                                            Indica si al seleccionar el vínculo se cargará el vínculo en una nueva ventana del explorador.                                                                             |
| Deshabilitar validación de página  |                                                                       Indica si también se va a aplicar la seguridad de una página web vinculada al vínculo Web.                                                                       |
|        URL de imagen         |                                                   Una dirección URL opcional a una imagen. La imagen vinculada se puede usar en el portal si forma parte de la plantilla de página; por ejemplo, como un icono.                                                   |
|       Alto de la imagen       |                                                                                      Un alto opcional para la imagen de la propiedad de dirección URL de la imagen.                                                                                      |
|       Ancho de la imagen        |                                                                                      Un ancho opcional para la imagen de la propiedad dirección URL de la imagen.                                                                                       |
|      Texto alternativo de imagen      |                                                                                   Una descripción opcional de la imagen de la propiedad dirección URL de la imagen.                                                                                    |
|    Mostrar solo la imagen    |                                                   Indica que la plantilla debe presentar solo un vínculo de imagen para este vínculo Web, en lugar de la imagen y el nombre del vínculo juntos.                                                    |
|                          |                                                                                                                                                                                                                                         |

> [!Note]
> - Cuando un vínculo Web se encuentra en una página web, el estado de seguridad y publicación de la página web también se aplica al vínculo Web. Esta validación se puede deshabilitar con la opción deshabilitar validación de página. 
>   - Se puede conceder a los usuarios con permisos de administración de contenido la posibilidad de usar el modo de vista previa, lo que permite a estos usuarios ver (vista previa) el contenido no publicado.

### <a name="see-also"></a>Vea también

[Personalización del contenido mediante fragmentos de código](customize-content-snippets.md)
