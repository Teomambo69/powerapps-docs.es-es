---
title: Crear y administrar archivos Web en portales de PowerApps | MicrosoftDocs
description: Aprenda a crear y administrar archivos Web en un portal.
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551264"
---
# <a name="create-and-manage-web-files"></a>Crear y administrar archivos Web

Un archivo Web representa un archivo descargable en un sitio web de portales, que se usa para almacenar imágenes, documentos y cualquier otro tipo de archivo.

Para almacenar el contenido real de un archivo determinado, los portales utilizan la característica de datos adjuntos de las notas asociadas a un registro de archivo Web. El archivo adjunto de la nota más reciente asociada al archivo Web se usa como el contenido del archivo. Por lo tanto, el tamaño del contenido del archivo Web que pueden admitir los portales viene determinado por el tamaño de los datos adjuntos de la nota que admite la instalación de Dynamics 365.

## <a name="manage-web-files"></a>Administrar archivos Web

Los archivos Web se pueden crear, editar y eliminar en los portales de PowerApps.

1. Abra la [aplicación administración del portal](configure-portal.md).

2. Vaya a **portales** > **archivos Web**.

3. Para crear un nuevo archivo Web, seleccione **nuevo**.

4. Para editar un archivo Web existente, seleccione el nombre del archivo Web.

5. Escriba los valores adecuados en los campos.

6. Seleccione **Guardar y cerrar**.

### <a name="web-file-attributes"></a>Atributos de archivo Web

En la tabla siguiente se explican muchos de los atributos de archivo Web estándar que utilizan los portales. Es importante tener en cuenta que la manera en la que se representan muchos de los atributos de contenido y de presentación está controlada por la plantilla de página usada y por el desarrollador del portal.

| Nombre                | Descripción               |
|---------------------|-----------------------|
|Nombre |Nombre descriptivo de la entidad. Este valor se usará como el título del archivo en la mayoría de las plantillas (por ejemplo, para los títulos de los vínculos). Este campo es obligatorio.   |
|Bsitio   |Sitio web al que pertenece la entidad. Este campo es obligatorio.   |
|Página primaria   |La página web primaria de la entidad, en la jerarquía de contenido del sitio Web. <br>Aunque no es necesario que un archivo tenga una página primaria, en algunos escenarios, por ejemplo, un archivo puede tener una entrada de blog principal: la configuración recomendada en la mayoría de los casos es proporcionar una página primaria.  |
|Dirección URL parcial   |El segmento de ruta de acceso de dirección URL que se usa para crear la dirección URL del portal de esta página. <br>La página raíz única (Inicio) del sitio web: la página única que no tiene ninguna página primaria asociada: debe tener un valor de dirección URL parcial de/.<br>Los valores de dirección URL parciales se usan como segmentos de ruta de dirección URL. Como tal, no deben contener caracteres de ruta de acceso de dirección URL no válidos, como?, #,!,%. Puesto que las direcciones URL de Adxstudio portales se generan combinando los valores de dirección URL parcial con barras diagonales (/), no suelen contener barras diagonales. La práctica recomendada sería restringir los valores de dirección URL parciales a letras, números, guiones o caracteres de subrayado. Por ejemplo: Press-Release. pdf, Site_Header. png.  |
|Estado de publicación   |Estado actual del flujo de trabajo de publicación del archivo, que puede determinar si el archivo está visible o no en el sitio. El uso más común de esta característica es proporcionar un control publicado o borrador sobre el contenido.<br>Se puede conceder a los usuarios con permisos de administración de contenido la posibilidad de usar el modo de vista previa, lo que permite a estos usuarios ver (vista previa) el contenido no publicado.   |
| Fecha de presentación        | Este atributo es un valor de fecha y hora que se puede usar en una plantilla, solo para fines de presentación. No tiene ninguna implicación funcional, pero puede ser útil para cosas como, por ejemplo, especificar manualmente una fecha Publicada en un documento de versión de prensa.    |
| Fecha de lanzamiento        | Controla una fecha y hora después de la cual el archivo será visible en el portal. Si la fecha y hora actuales es anterior a esta fecha, este archivo no será visible. (La excepción a esto es que se puede conceder a los usuarios con permisos de administración de contenido la posibilidad de usar el modo de vista previa, lo que permite a estos usuarios ver (vista previa) el contenido sin liberar). Esto resulta útil para controlar el lanzamiento de contenido dependiente del tiempo, como noticias o comunicados de prensa. |
| Fecha de expiración     | Controla una fecha y hora antes de la cual el archivo será visible en el portal. Si la fecha y hora actuales son posteriores a esta fecha, este archivo no será visible. (La excepción a esto es que se puede conceder a los usuarios con permisos de administración de contenido la posibilidad de usar el modo de vista previa, lo que permite a estos usuarios ver (vista previa) el contenido caducado).                |
| Resumen             | Una breve descripción del archivo, este valor se usará generalmente para agregar una descripción del archivo a los elementos de navegación del portal que representan un vínculo al archivo.      |
| Oculto desde el mapa del sitio | Controla si el archivo está visible o no contiene parte del mapa del sitio del portal. Si este valor está activado, el archivo seguirá estando disponible en el sitio en su dirección URL y se puede vincular a, pero los elementos de navegación estándar (menús, etc.) no incluirán la página.      |
| Mostrar orden       | Un valor entero que indica el orden en el que se colocará el archivo, en relación con otras entidades con la misma página primaria. Esto controla el orden de los archivos y otras entidades del mapa del sitio cuando, por ejemplo, una lista de vínculos a las entidades secundarias de una página determinada se representa en el portal.      |
| Dirección de BLOB en la nube  | Un valor de texto con el formato `<container>/<filename>`, que indica que el contenido de este archivo se almacena en Azure Blob Storage.        |
| Content-Disposition | Las opciones son insertadas o adjuntas. Si se especifica Inline, el explorador debe intentar representarlo en la ventana del explorador y, si no es posible, pedirá al usuario que descargue o abra el archivo. Si se especifica Attachment, se le pedirá inmediatamente al usuario que descargue o abra el archivo, y que no intente cargarlo en el explorador, ya sea posible o no.                                                                                        |
| Habilitar seguimiento     | Si está habilitada, se registrarán todas las solicitudes de este archivo Web. Si el usuario está autenticado, se creará una entrada de registro de archivo Web con la fecha & hora, la dirección IP y el registro de contacto.      |
|||



