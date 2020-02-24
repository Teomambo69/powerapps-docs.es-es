---
title: Crear y ejecutar anuncios en un portal | MicrosoftDocs
description: Instrucciones para crear anuncios basados en texto o imagen y ejecutarlos en varios emplazamientos del sitio.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 8d3c30dce08a09847123612a240a6376999002f8
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979841"
---
# <a name="create-and-run-advertisements-on-a-portal"></a>Crear y ejecutar anuncios en un portal

Cree anuncios basados en texto o imagen y ejecútelos en varios emplazamientos del sitio. Aleatorice anuncios o seleccione anuncios específicos para posiciones específicas. Puede elegir fechas de lanzamiento y expiración para contenido urgente programado. Los anuncios se pueden hipervincular con cualquier destino y abrir en la ventana actual o una nueva ventana. Los anuncios se muestran en el portal mediante dos entidades: la entidad Ubicación de anuncio y la entidad Anuncio asociada. Anuncios pueden emerger de muchas formas: con plantillas de Liquid preelaboradas disponibles en portales mediante plantillas de Liquid/plantillas web de ejemplo o desde la página .aspx deseada mediante acciones MVC.

## <a name="create-a-new-advertisement"></a>Crear un anuncio nuevo

Los anuncios representan el anuncio o la imagen específico que aparecerán en el portal en un momento determinado. La entidad Anuncio se mostrará en la ubicación especificada por la ubicación de anuncio. El anuncio debe estar asociado con una ubicación de anuncio para que aparezca en el portal. Para esta demostración el anuncio Marcador de posición y la ubicación de anuncio Barra lateral inferior de ejemplo predefinidos emergerán en el portal de empresa para exhibir funcionalidad básica y ganar familiaridad antes de crear anuncios más complejos. Puede utilizar cualquiera de los sitios de inicio en lugar del portal de la empresa. Sin embargo, tenga en cuenta que las plantillas de Liquid usadas para esta demostración llaman al nombre de ubicación de anuncio Barra lateral inferior.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Anuncios**.

3. Abra el anuncio **Marcador de posición** asociado al sitio web **Portal de empresa** (esto se puede hacer con el sitio de inicio que prefiera seleccionando **+Nuevo** y creando un anuncio idéntico en el sitio web). 

4. Seleccione el icono **Guardar** en la esquina inferior derecha (o en **Guardar y cerrar** en la esquina superior izquierda si ha creado un nuevo anuncio).

En el formulario del anuncio especifique un **Nombre** para describir el anuncio, el **Sitio web** donde el anuncio se mostrará y un **Estado de publicación**. Opcionalmente puede especificar una plantilla web y una fecha de lanzamiento/vencimiento. Debe proporcionar algún tipo de datos para que se muestre el anuncio. Use la tabla atributos de entidad de anuncio más adelante en este manual para elaborar los detalles del anuncio.


## <a name="create-a-new-advertisement-placements"></a>Crear nuevas ubicaciones de anuncio

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Ubicaciones de anuncios**.

3. Seleccione el campo Plantilla web para seleccionar una plantilla web. Con fines de demostración, se ha elegido la plantilla web Anuncio aleatorio.

4. En la esquina derecha de la cuadrícula Anuncios, seleccione **+** para seleccionar el anuncio creado en el paso anterior.

5. Seleccione el icono **Guardar** en la esquina inferior derecha.

Al crear una nueva ubicación de anuncio especifique un **Nombre** para describir la ubicación del anuncio y el **Sitio web** donde se mostrará la ubicación de anuncio. Las plantillas web de ejemplo que permiten el uso de anuncios como una característica predefinida se mostrarán en la búsqueda del campo Plantilla web en el formulario. Estas plantillas también se pensadas para usar como origen para crear plantillas personalizadas.

> [!div class=mx-imgBorder]
> ![Ver registro de búsqueda](../media/see-lookup-record.png "Ver registro de búsqueda")  

> [!div class=mx-imgBorder]
> ![Configuración inferior de barra lateral](../media/set-sidebar-bottom.png "Configuración inferior de barra lateral")  

> [!div class=mx-imgBorder]
> ![Portal de empresa del anuncio](../media/ad-company-portal.png "Portal de empresa del anuncio")  

> [!NOTE] 
> El anuncio creado anteriormente no se mostrará en la página principal del portal de inicio.

## <a name="using-liquid-templates-to-place-advertisements"></a>Uso de plantillas de Liquid para colocar anuncios

Los administradores de contenido pueden usar Liquid para agregar un anuncio a cualquier área de contenido editable, tal como se describe en [Trabajar con plantillas de Liquid](../liquid/liquid-overview.md) y, más en concreto, [Anuncios](../liquid/liquid-objects.md#ads).

Esta plantilla representa un anuncio por nombre, o un anuncio aleatorio de una ubicación de anuncio. Actualmente el código siguiente no representará varios anuncios en la ubicación de anuncio (es decir un anuncio rotativo). Para representar anuncios múltiples en la ubicación del anuncio, sería necesario crear una API de anuncios de Liquid. Para obtener más información acerca de las plantillas web integradas, consulte [Almacenar contenido de origen usando plantillas web](../liquid/store-content-web-templates.md).

```
{% include 'ad' ad_name:'Name' %}
{% include 'ad' ad_placement_name:'Placement Name' %}
1. {% include 'Random Ad' placement:ads.placements[Sidebar Bottom] %}
```
o 

```
1. {% include 'Ad Template' ad:ads{Retail Ad - Go Greene] %}
```


## <a name="attributes"></a>Atributos

La entidad Anuncio tiene los siguientes atributos:


|        Nombre        |                                                                                                                                                                                                                                             Descripción                                                                                                                                                                                                                                              |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        Nombre        |                                                                                                                                                                                                                                    Un nombre descriptivo para el anuncio                                                                                                                                                                                                                                     |
|      Sitio web       |                                                                                                                                                                                                                                  Sitio web asociado. Requerido.                                                                                                                                                                                                                                   |
|    Plantilla web    |                                                                                                                                                La [plantillas web](../liquid/store-content-web-templates.md) asociadas que se usarán de forma predeterminada para representar el anuncio. Este campo es opcional; si está en blanco el anuncio se representará usando una plantilla predeterminada.                                                                                                                                                |
|    Fecha de publicación    |                                                                                      Controla una fecha o una hora después de las cuales el anuncio será visible en el portal. Si la ubicación del anuncio es rotativa a través de varios anuncios, no aparecerá un anuncio sin publicar. Si no hay anuncios publicados asociados con una ubicación del anuncio, no aparecerá nada. Esto resulta útil para controlar la publicación de contenido urgente.                                                                                      |
|  Fecha de expiración   |                                                                                                                                                                                                             Controla una fecha o una hora antes de las cuales el anuncio será visible en el portal.                                                                                                                                                                                                             |
|  Estado de publicación  |                                                                                                                                                                                                                                    El estado actual de publicación.                                                                                                                                                                                                                                     |
|    URL de redireccionamiento    |                                                                                                                                                                                Cuando se hace clic en el anuncio, el usuario irá a esta dirección URL. **Este campo es opcional.** Si no se asigna ningún valor, no se podrá hacer clic en el anuncio.                                                                                                                                                                                 |
| Abrir en ventana nueva |                                                                                                                                                                                                             Booleano. Si se establece como true, el anuncio abrirá una nueva ventana del explorador cuando se haga clic en él.                                                                                                                                                                                                             |
|       Cargo        |  Una sola línea de texto del anuncio que se puede mostrar en el portal. Si se muestra depende de una propiedad en el control AdPlacement. La utilidad principal de esto es para los anuncios basados en texto o los vínculos simples de una línea que desee colocar en el portal con ubicaciones de anuncios. Si se muestra el título, de forma predeterminada se representará como un hipervínculo que señala a la dirección URL de redireccionamiento. Este comportamiento se pueden editar utilizando una [plantilla web](../liquid/store-content-web-templates.md) personalizada.   |
|        Copia        |                                                                      Un cuerpo del texto de varias líneas u otro contenido web que se mostrará en la ubicación del anuncio. Esto permite utilizar la ubicación de forma similar a fragmentos de contenido, pero es mejor evitar usarlos para que sirvan simplemente como un depósito para albergar contenido (use fragmentos para ello). En su lugar, es mejor usarlos para mostrar la imagen rotativa o contenido textual.                                                                      |
|     URL de imagen      | La dirección URL de la imagen que mostrará el anuncio. Opcional; use este campo si desea que el anuncio se represente como un recurso estático o un archivo web. Puede hacer clic en la imagen y vincularla a la dirección URL de redireccionamiento, si se da una. Si un anuncio tiene una nota asociada con datos adjuntos del archivo de imagen, el anuncio la representará como su imagen. Esta es posiblemente la forma más conveniente de configurar imágenes para anuncios, y liga la imagen directamente con el anuncio. En este caso, el uso del campo de dirección URL de imagen no es necesario. |
|    Ancho de la imagen     |                                                                                                                                                                                    Ancho de la imagen. Este campo no es necesario, pero se recomienda para asegurarse de que el anuncio representado es HTML válido y accesible.                                                                                                                                                                                     |
|    Alto de la imagen    |                                                                                                                                                                                    Altura de la imagen. Este campo no es necesario, pero se recomienda para asegurarse de que el anuncio representado es HTML válido y accesible.                                                                                                                                                                                    |
|   Texto alternativo de la imagen   |                                                                                                                                                                                  Texto alternativo para la imagen. Este campo no es necesario, pero se recomienda para asegurarse de que el anuncio representado es HTML válido y accesible.                                                                                                                                                                                  |

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Acerca de listas de entidades](entity-lists.md)  
[Crear y ejecutar anuncios en un portal](create-run-advertisement.md)  
[Obtener comentarios utilizando sondeos en un portal](gather-feedback-poll.md)  
[Clasifique o vote sobre una página web en un portal](rate-webpage.md)  
[Redireccionar a una nueva dirección URL en un portal](add-redirect-url.md)  

