---
title: Obtener comentarios utilizando sondeos en un portal | MicrosoftDocs
description: Instrucciones para crear sondeos sobre un portal y recopilar comentarios con ellas.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3278c20c83dfcb0a5088183bf279a6e07118f855
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875877"
---
# <a name="gather-feedback-by-using-polls-on-a-portal"></a>Obtener comentarios utilizando sondeos en un portal

Los sondeos proporcionan a las audiencias web una forma rápida y fácil de expresar su opinión sobre temas específicos e inmediatamente y automáticamente ver los comentarios mediante sus votos.

Utilice la capacidad de sondeos de los portales para preguntar a su audiencia sobre temas de interés y permitirles que den respuestas individuales o de opción múltiple. En cualquier caso, sus respuestas inmediatamente se almacenan y se asocian con el registro de contacto aplicable para su inmediata revisión o generación de informes agregados. Puede usar los sondeos como sencillas herramientas de investigación de mercados y, si actualiza o rota los sondeos dinámicamente, mantendrá el sitio web con aspecto actual e interesante.

Puede colocar los sondeos en el portal mediante el control PollPlacement. Este control funciona de forma muy similar al control AdPlacement. Si hay sondeos asociados con la entidad de Ubicación de sondeo que está representando el control PollPlacement, se representarán esos sondeos. Si hay más de un sondeo para una ubicación dada, la ubicación presentará aleatoriamente uno de los sondeos especificados.

> [!Note]
> Los usuarios pueden votar de forma anónima. Los votos duplicados no se permiten. Se puede realizar un seguimiento de la información básica sobre envíos y los usuarios que inicien sesión en el sitio web tendrán sus envíos vinculados a la entidad de contacto que hace seguimiento de ese usuario en Common Data Service.

## <a name="add-a-poll-to-the-page"></a>Agregar un sondeo a la página

Los administradores de contenido pueden usar [Etiquetas de plantilla](../liquid/liquid-overview.md) para agregar un sondeo a cualquier área de contenido editable:  

`{% include 'Random Poll' placement:polls.placements[Sidebar] %}`

o

`{% include 'Poll Template' ad:ads[Wireframe Development] %}`

> [!Note]
> Las plantillas web de ejemplo se configuran en los sitios web de inicio. Puede usar la plantilla Sondeo aleatorio para mostrar un sondeo aleatorio de una entidad de ubicación de sondeo específica o puede usar la Plantilla de sondeo para presentar un sondeo específico. Puede editar estas plantillas o seguir su ejemplo y crear las suyas propias empleando [Sondeos](../liquid/liquid-objects.md#polls). 

## <a name="create-a-poll-placement"></a>Crear una ubicación de sondeo

Para crear una nueva región de ubicación de sondeo:

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Ubicaciones de sondeos**.

3. Seleccione **Nuevo**.

4. Seleccione el **sitio web**, dé a la ubicación un nombre y&mdash;opcionalmente&mdash;seleccione las [plantillas web](../liquid/store-content-web-templates.md) que controlarán cómo se representa.

5. Una vez que se ha creado la ubicación; debe asociar uno o más sondeos con esta ubicación En la pestaña **Sondeos** de la entidad de ubicación de sondeo, seleccione **Agregar sondeo existente**. 

6. En el cuadro de búsqueda resultante, seleccione un registro de sondeo existente o cree un nuevo sondeo seleccionando **Nuevo sondeo**.
  

## <a name="polls"></a>Sondeos

Un sondeo es una pregunta simple de sí/no o de múltiples opciones que es posible mostrar en el portal a través de ubicaciones de sondeo. Hay muchas opciones personalizables para mostrar los sondeos disponibles para desarrolladores, pero, para administradores de contenido, agregar sondeos al sitio web es tan sencillo como elegir una pregunta y una serie de respuestas posibles (opciones de sondeo). Un sondeo debe tener opciones relacionadas para funcionar y debe estar asociado con una ubicación de sondeo para que se represente en el portal.

Una nueva encuesta se puede crear de estas dos maneras: 
- Yendo a la sección **Sondeos** en la área **Portales**.
- Seleccionando el botón **Nuevo** en la ventana **Buscar registros** mientras agrega un sondeo a una ubicación de sondeo.

## <a name="poll-attributes"></a>Atributos de sondeo

| Nombre                | Descripción                                                                                                                                                                                                                                                                                                                                  |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre                | Nombre descriptivo del sondeo.                                                                                                                                                                                                                                                                                                            |
| Sitio web             | Las [plantillas web](../liquid/store-content-web-templates.md) asociadas.                                                                                                                                                                                                                                                                |  
| Plantilla web        | Las [plantillas web](../liquid/store-content-web-templates.md) asociadas que se usarán de forma predeterminada para representar el sondeo. Este campo es opcional; si está en blanco, el sondeo se representará usando una plantilla predeterminada.                                                                                                                     |  
| Pregunta            | Ésta es la pregunta real que se formula en el sondeo. Las opciones de sondeo asociadas son las respuestas posibles que se pueden seleccionar para este sondeo.                                                                                                                                                                                             |
| Etiqueta del botón Enviar | El texto que se usará para el botón de envío.                                                                                                                                                                                                                                                                                       |
| Fecha de publicación        | Controla la fecha y hora después de las cuales el sondeo será visible en el portal. Si la ubicación del sondeo es rotativa a través de varios sondeos, no se mostrará un sondeo sin publicar. Si no hay sondeos publicados asociados con una ubicación de sondeo, no aparecerá nada. Esto resulta útil para controlar la publicación de contenido urgente.         |
| Fecha de expiración     | Controla la fecha y una hora antes de las cuales el sondeo será visible en el portal.                                                                                                                                                                                                                                                                  |
| Fecha de cierre de votación   | Hasta esta fecha, los usuarios que aún no han votado en un sondeo pueden votar.|

> [!Note] 
> - Cuando un usuario ha votado en un sondeo, verá un resumen de resultados actuales para el sondeo. Estos resultados también se mostrarán para un soldeo que ha superado su fecha de cierre, pero para el que el usuario no ha votado aún. Esto permite continuar revelando los resultados de sondeos cuando ya no desea que se pueda seguir votando en ellos. 
> - La diferencia entre la fecha de cierre de voto y la fecha de vencimiento es que una vez superada la fecha de vencimiento, el sondeo dejará de aparecer en la ubicación de sondeo (no se realizará un ciclo). La fecha de cierre de voto determina sólo la fecha a partir de la cual los usuarios no pueden votar en el sondeo.

Ahora que se ha creado el sondeo, debe asociar una o más opciones de sondeo con este sondeo. En la pestaña **Opciones** del sondeo, seleccione **Nueva opción de sondeo**.

> [!div class=mx-imgBorder]
> ![Agregar opciones de sondeo](../media/add-poll-options.png "Agregar opciones de sondeo")  

## <a name="poll-options"></a>Opciones de sondeo

Un sondeo es una pregunta que se presenta al usuario. Un sondeo tiene dos o más respuestas posibles que según determina el autor de contenido. Estas respuestas se representan mediante opciones de sondeo, que deben asociarse con el sondeo en cuestión. Una nueva opción de sondeo se crea a través la ventana **Buscar registros** cuando se agregan opciones de sondeo a un sondeo, como se describió anteriormente.

## <a name="poll-option-attributes"></a>Atributos de opción de sondeo

| Nombre          | Descripción                                                                |
|---------------|----------------------------------------------------------------------------|
| Nombre          | Nombre descriptivo de la opción de sondeo.                                  |
| Sondeo          | El sondeo con el que está asociada la opción.                               |
| Respuesta        | El texto que se mostrará como opción de voto disponible en el sondeo.                    |
| Votos         | El número de votos que la opción de sondeo ha recibido (solo lectura).              |
| Orden de visualización | Un valor numérico que determinará el orden de visualización de las opciones de sondeo. |

## <a name="poll-submissions"></a>Envíos de sondeo

Cuando un usuario visite el sitio web tendrá la oportunidad de votar en el sondeo que se muestra en la página.

> [!div class=mx-imgBorder]
> ![Enviar un sondeo](../media/submit-poll.png "Enviar un sondeo")  

Los usuarios pueden votar solo una vez, después, si el sondeo se muestra, verán los resultados para ese sondeo.

> [!div class=mx-imgBorder]
> ![Votos de sondeo](../media/poll-votes.png "Votos de sondeo")  

Los detalles de los resultados de la votación del sondeo se almacenan en Common Data Service como registros de envíos de sondeo. La entidad de envío de sondeo contiene la siguiente información:

| Nombre        | Descripción                                                                                   |
|-------------|-----------------------------------------------------------------------------------------------|
| Nombre        | Muestra el nombre del votante si el usuario ha iniciado sesión; si no, registra el Id. anónimo. |
| Sondeo        | El sondeo asociado.                                                                          |
| Opción de sondeo | La opción de sondeo que el usuario seleccionó.                                                       |
| Contacto     | El registro de contacto asociado del votante si el usuario ha iniciado sesión                           |
| Id. de visitante  | El Id. anónimo del votante si el usuario es anónimo.                                       |

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Acerca de listas de entidades](entity-lists.md)  
[Crear y ejecutar anuncios en un portal](create-run-advertisement.md)  
[Clasifique o vote sobre una página web en un portal](rate-webpage.md)  
[Redireccionar a una nueva dirección URL en un portal](add-redirect-url.md)  

