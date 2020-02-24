---
title: Colocar los nodos secundarios mediante accesos directos para un portal | MicrosoftDocs
description: Instrucciones para colocar los nodos secundarios mediante accesos directos de portales.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e438803fa817d1b02a303a6a6e4873f2ba1e295f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980589"
---
# <a name="place-child-nodes-by-using-shortcuts-for-portals"></a>Colocar los nodos secundarios mediante accesos directos para portales
Utilice accesos directos para colocar nodos secundarios en el mapa del sitio del portal que simplemente apuntan a otros nodos que existen en el mapa del sitio, o a direcciones URL externas al portal. Es decir, páginas web, archivos web, eventos, y foros se pueden considerar nodos “sólidos” del mapa del sitio del portal: se agregan al mapa del sitio y cuando se navega a ellos, se ve el contenido real de los nodos directamente. Los accesos directos, por otra parte, se pueden considerar nodos 'intangibles': también se agregan al mapa del sitio (a diferencia de vínculos web, que no), pero cuando usted se desplaza a ellos, ve el contenido del nodo "sólido" de destino al que apunta el acceso directo, y ese contenido es representado por la plantilla de página para ese nodo.

## <a name="manage-shortcuts"></a>Administrar accesos directos

Crear, editar y eliminar accesos directos se puede realizar en portales de Power Apps.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** &gt; **Accesos directos**. 

3. Para crear un acceso directo, seleccione **Nuevo**. 

4. Para editar un acceso directo existente, seleccione el acceso directo existente en la cuadrícula. 

5. Escribir valores para los campos proporcionados. 

6. Seleccione **Guardar y cerrar**.

### <a name="attributes-and-relationships"></a>Atributos y relaciones

| Nombre                               | Descripción                                                                                                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre                               | Un nombre descriptivo para el acceso directo. Solo para uso interno.                                                                                                                                  |
| Sitio web                            | El sitio web al que pertenece el acceso directo.                                                                                                                                                    |
| Página primaria                        | La página web principal de la entidad del acceso directo en el mapa del sitio. El acceso directo se agregará al mapa del sitio como secundario de esta página.                                                                 |
| Dirección URL externa                       | Destino del acceso directo de una dirección URL de un recurso fuera de la organización.                                                                                                                  |
| Página web                           | Destino del acceso directo de una página web interna.                                                                                                                                               |
| Archivo web                           | Destino del acceso directo de un archivo web.                                                                                                                                                        |
| Evento                              | Destino del acceso directo de un evento.                                                                                                                                                          |
| Foro                              | Destino del acceso directo de un foro.                                                                                                                                                           |
| Puesto                              | El título para el acceso directo. Éste es el nombre que aparecerá en el mapa del sitio y las áreas de vista de navegación secundaria. Si se deja en blanco, el título (o nombre) de la entidad de destino se mostrará en su lugar. |
| Descripción                        | Una descripción que aparecerá en vistas de navegación secundarias. Opcional.                                                                                                                                        |
| Orden de visualización                      | El orden editable del lado frontal en el que aparecerá el acceso directo en el mapa del sitio y las vistas de navegación secundaria, en relación con otros nodos del mapa del sitio.                                                      |
| Deshabilitar validación del destino del acceso directo | Si está desactivada, la seguridad del acceso directo se basará en el destino. De lo contrario, se basará en el elemento principal. Para obtener más información, vea Seguridad a continuación.                                   |
||

> [!Note]
> Un acceso directo solo necesita tener **uno** de los campos "destino" (Dirección URL externa, Página web, Encuesta, Archivo web, Evento, Foro) asignado a un valor, y un acceso directo solo tendrá un destino. Por ejemplo, un acceso directo no apunta a una página web y una encuesta, o una dirección URL externa y un archivo web. Si hay más de un atributo de destino para un acceso directo, el acceso directo sólo tomará primero, omitiendo los demás. El orden de prioridad para el que se elegirá el destino se refleja en el formulario de acceso directo principal. Por tanto, primero comprobará si hay una dirección URL externa para el acceso directo, y si existe, el destino del acceso directo será la dirección URL externa y se ignorarán todos los demás atributos de destino. Si no hay una dirección URL externa, el acceso directo comprobará la página web, luego la encuesta, el archivo web, el evento y, por último el foro. 

## <a name="secure-shortcuts"></a>Accesos directos seguros

La seguridad de los accesos directos se puede basar en la página principal del acceso directo, o en el destino del acceso directo. Esto determinará si el acceso directo será visible en el mapa del sitio. Naturalmente, si la seguridad se basa en el primario, el acceso de escritura del destino del acceso directo aún determinará si la edición del lado frontal funcionará una vez que acceso directo se ha usado para desplazarse hasta el destino del acceso directo. Por consiguiente la seguridad del acceso directo sólo afecta a la navegación y a los derechos de edición para la edición del lado frontal de los accesos directos. El método de seguridad usado es específico del acceso directo. Si deja el valor booleano **Deshabilitar validación de destino del acceso directo** sin activar, la seguridad del acceso directo se basará en el destino. En caso contrario, se basará en el elemento principal.

## <a name="navigate-with-shortcuts"></a>Navegar con accesos directos

Una vez que se ha creado la entidad de acceso directo, aparecerá en el sitio web. En el ejemplo anterior, el sitio básico tiene dos páginas adicionales: página uno y página dos. La página dos es un elemento secundario de la página uno, que es un elemento secundario de la página principal. Además, hay un acceso directo que es un elemento secundario de página principal que apunta a la página dos. 
