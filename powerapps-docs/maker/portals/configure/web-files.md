---
title: Creación y administración de archivos web en portales de PowerApps | MicrosoftDocs
description: Aprenda a crear y administrar archivos web en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dc67db92ac502611b0c10b5d387b100e8aa43da7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761118"
---
# <a name="create-and-manage-web-files"></a>Crear y administrar archivos web

Un archivo web representa un archivo descargable en un sitio web del portal que se usa para almacenar imágenes, documentos y cualquier otro tipo de archivo.

Para almacenar el contenido real de un archivo determinado, los portales usan la característica de datos adjuntos de las notas asociadas a un registro de archivo web. El archivo adjunto de la más nueva nota asociada al archivo web se usa como el contenido del archivo. Por lo tanto, el tamaño del contenido del archivo web que pueden admitir los portales está determinado por el tamaño de los datos adjuntos de nota que admita la instalación de Dynamics 365.

## <a name="manage-web-files"></a>Administrar archivos web

Se pueden crear, editar y eliminar archivos web desde portales de PowerApps.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Archivos web**.

3. Para crear un nuevo archivo web, seleccione **Nuevo**.

4. Para editar un archivo web existente, seleccione el nombre del archivo web.

5. Especifique los valores adecuados en los campos.

6. Seleccione **Guardar y cerrar**.

### <a name="web-file-attributes"></a>Atributos del archivo web

La tabla siguiente explica muchos de los atributos del archivo web estándar que usan los portales. Es importante observar que la forma en que se representan muchos de los atributos orientados a contenido/visualización está administrada por la plantilla de página web utilizada y, por tanto, por el desarrollador del portal.

| Nombre                | Descripción               |
|---------------------|-----------------------|
|Nombre |Nombre descriptivo de la entidad. Esta valor se usará como título del archivo en la mayoría de las plantillas (por ejemplo, en títulos de vínculos). Este campo es obligatorio.   |
|Sitio web   |Sitio web al que pertenece la entidad. Este campo es obligatorio.   |
|Página primaria   |La página web principal de la entidad, en la jerarquía de contenido del sitio web. <br>Mientras que un archivo no es necesario para disponer de una página principal (en algunos escenarios, por ejemplo, un archivo puede tener una publicación de blog principal), proporcionar una página principal es la configuración recomendada en la mayoría de los casos.  |
|Dirección URL parcial   |El segmento de dirección URL utilizado para crear la dirección URL de portal de esta página. <br>La página raíz única (principal) del sitio web, la página única que no tiene ninguna página primaria asociada, debe tener un valor de URL parcial de /.<br>Se usan valores de dirección URL parciales como segmentos de la dirección URL. Por tanto, no deben contener caracteres no válidos para dirección URL, como ?, #, !, %. Dado que las direcciones URL de Adxstudio Portals se generan combinando valores de dirección URL parciales con barras diagonales (/), tampoco deben contener normalmente las barras diagonales. La práctica recomendada sería restringir valores parciales de la dirección URL a letras, números y guiones o caracteres de subrayado. Por ejemplo: press-release.pdf, Site_Header.png.  |
|Estado de publicación   |El estado actual de flujo de trabajo de publicación del archivo, que puede dictar si el archivo es visible en la ubicación. El uso más común de esta característica es proporcionar control de publicado/borrador sobre contenido.<br>A los usuarios con los permisos de administración de contenido se les puede conceder la capacidad de usar el modo de vista previa, que permite que a estos usuarios ver (obtener una vista previa) contenido sin publicar.   |
| Mostrar fecha        | Este atributo es un valor de fecha y hora que puede usar una plantilla, básicamente con fines de mostrar. No tiene ningún implicación funcional, pero puede resultar útil para elementos como, por ejemplo, especificar manualmente una fecha de publicación en un documento de comunicado de prensa.    |
| Fecha de publicación        | Controla una fecha y una hora después de las cuales el archivo será visible en el portal. Si la fecha y hora actuales son anteriores a esta fecha, este archivo no estará visible. (La excepción a esto es que los a los usuarios con los permisos de administración de contenido se les puede conceder la capacidad de usar el modo de vista previa, que permite que a estos usuarios ver (obtener una vista previa) contenido no publicado). Esto resulta útil para controlar la emisión de contenido urgente, como noticias o comunicados de prensa. |
| Fecha de expiración     | Controla una fecha y una hora antes de las cuales el archivo será visible en el portal. Si la fecha y hora actuales son posteriores a esta fecha, este archivo no estará visible. (La excepción a esto es que los a los usuarios con los permisos de administración de contenido se les puede conceder la capacidad de usar el modo de vista previa, que permite que a estos usuarios ver (obtener una vista previa) contenido expirado.)                |
| Resumen             | Una breve descripción para el archivo, este valor se usará normalmente para agregar una descripción del archivo a elementos de navegación del portal que representen un vínculo al archivo.      |
| Oculto para el mapa del sitio | Controla si el archivo que está visible tiene parte del mapa del sitio del portal. Si este valor está activado, el archivo seguirá estando disponible en el sitio en su dirección URL, y se puede vincular con él, pero los elementos de navegación estándar (menús, etc.) no incluirán la página.      |
| Orden de visualización       | Un valor de entero que indica el orden en que el archivo se colocará en relación con otras entidades con la misma página principal. De esta forma controla el orden de archivos y otras entidades del mapa del sitio cuando, por ejemplo, una lista de vínculos a las entidades secundarias de una página dada se representa en el portal.      |
| Dirección de blob en la nube  | Un valor de texto con el formato `<container>/<filename>`, indicando que el contenido de este archivo se almacena en Almacenamiento de blobs de Azure.        |
| Disposición de contenido | Las opciones son en línea o datos adjuntos. Si especifica en línea, el explorador deberá intentar representarlo en la ventana del explorador y si no puede, pedirá al usuario que descargue o abra el archivo. Si se especifican datos adjuntos, inmediatamente pedirá al usuario que descargue o abra el archivo, y no intentará cargarlo en el explorador, tanto si puede como si no.                                                                                        |
| Habilitar seguimiento     | Si está activada, cada solicitud para este archivo web se registrará. Un registro de archivo web se creará con la fecha y hora, dirección IP, y el registro de contacto si se autentica el usuario.      |
|||



