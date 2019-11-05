---
title: Colocar los nodos secundarios mediante accesos directos para un portal | MicrosoftDocs
description: Instrucciones para colocar los nodos secundarios mediante accesos directos para los portales.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e004b0f4f37a57e37d8f847ad7221e6a50d549ed
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551586"
---
# <a name="place-child-nodes-by-using-shortcuts-for-portals"></a>Colocar nodos secundarios mediante accesos directos para portales
Use accesos directos para colocar los nodos secundarios en el mapa del sitio del portal que simplemente señalen a otros nodos que existen en el mapa del sitio o a direcciones URL externas a su portal. En otras palabras, las páginas web, los eventos y los foros se pueden considerar como nodos "sólidos" del mapa del sitio del portal: se agregan a su mapa de sitio y, al navegar a ellos, verá el contenido real de esos nodos directamente. Por otro lado, los accesos directos se pueden considerar nodos intangibles: también se agregan al mapa del sitio (a diferencia de los vínculos Web, que no son), pero cuando se navega a ellos, se ve el contenido del nodo "sólido" de destino al que apunta el acceso directo, y ese contenido es representado por la plantilla de página para ese nodo.

## <a name="manage-shortcuts"></a>Administrar accesos directos

La creación, edición y eliminación de accesos directos se pueden realizar en los portales de PowerApps.

1. Abra la [aplicación administración del portal](configure-portal.md).

2. Vaya a **portales** &gt; **accesos directos**. 

3. Para crear un acceso directo, seleccione **nuevo**. 

4. Para editar un acceso directo existente, seleccione el acceso directo existente en la cuadrícula. 

5. Escriba los valores de los campos proporcionados. 

6. Seleccione **guardar & cerrar**

### <a name="attributes-and-relationships"></a>Atributos y relaciones

| Nombre                               | Descripción                                                                                                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre                               | Un nombre descriptivo para el acceso directo. Solo para uso interno.                                                                                                                                  |
| Bsitio                            | Sitio web al que pertenece el acceso directo.                                                                                                                                                    |
| Página primaria                        | La página web principal de la entidad de acceso directo del mapa del sitio. El acceso directo se agregará al mapa del sitio como un elemento secundario de esta página.                                                                 |
| Dirección URL externa                       | Destino del acceso directo a una dirección URL de un recurso fuera de la organización.                                                                                                                  |
| Página Web                           | Destino del acceso directo a una página web interna.                                                                                                                                               |
| Archivo Web                           | Destino del acceso directo a un archivo Web.                                                                                                                                                        |
| ceso                              | Destino del acceso directo a un evento.                                                                                                                                                          |
| Enhance                              | Destino del acceso directo a un foro.                                                                                                                                                           |
| Título                              | Título del acceso directo. Este es el nombre que aparecerá en las áreas del mapa del sitio y de la vista de navegación secundaria. Si se deja en blanco, se mostrará el título (o nombre) de la entidad de destino. |
| Descripción                        | Una descripción que aparecerá en las vistas de navegación secundarias. Opcional.                                                                                                                                        |
| Mostrar orden                      | El orden de edición en el lado del servidor que aparecerá en el mapa del sitio y en las vistas de navegación secundarias, con respecto a otros nodos del mapa del sitio.                                                      |
| Deshabilitar la validación del destino de acceso directo | Si no está activada, la seguridad del acceso directo se basará en el destino. De lo contrario, se basará en el elemento primario. Para obtener más información, consulte Seguridad a continuación.                                   |
||

> [!Note]
> Un acceso directo solo debe tener **uno** de los campos ' destino ' (dirección URL externa, Página Web, encuesta, archivo Web, evento, foro) asignado a un valor y un acceso directo solo tendrá un destino. Por ejemplo, un acceso directo no apunta a una página web y una encuesta, o a una dirección URL externa y un archivo Web. Si existe más de un atributo de destino para un acceso directo, el acceso directo solo tomará el primero y omitirá todos los demás. El orden de prioridad para el que se elegirá el destino se refleja en el formulario de acceso directo principal. Por lo tanto, comprobará primero si existe una dirección URL externa para el acceso directo y, si la hay, el destino del acceso directo será la dirección URL externa y se omitirán todos los demás atributos de destino. Si no hay ninguna dirección URL externa, el acceso directo comprobará la página web y, a continuación, el foro de sondeo, archivo Web, evento y Finally. 

## <a name="secure-shortcuts"></a>Métodos abreviados seguros

La seguridad de los accesos directos se puede basar en la página primaria del acceso directo o en el destino del acceso directo. Esto determinará si el acceso directo será visible en el mapa del sitio. Naturalmente, si la seguridad se basa en el elemento primario, el acceso de escritura del destino del acceso directo seguirá determinando si la edición en paralelo funcionará después de que se haya utilizado el acceso directo para navegar al destino del acceso directo. Por lo tanto, la seguridad de acceso directo solo afecta a los derechos de navegación y edición para la edición frontal de los accesos directos. El método de seguridad utilizado es específico del acceso directo. Si deja el valor booleano **deshabilitar la validación del destino de acceso directo** no seleccionada, la seguridad del acceso directo se basará en el destino. de lo contrario, se basará en el elemento primario.

## <a name="navigate-with-shortcuts"></a>Navegación con accesos directos

Una vez creada la entidad de acceso directo, aparecerá en el sitio Web. En el ejemplo anterior, el sitio básico tiene dos páginas adicionales, la página uno y la página dos. La página dos es un elemento secundario de la página uno, que es un elemento secundario de la Página principal. Además, hay un acceso directo que es un elemento secundario de la Página principal que apunta a la página dos. 
