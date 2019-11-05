---
title: Crear y administrar plantillas de página en portales de PowerApps | MicrosoftDocs
description: Aprenda a crear y administrar plantillas de página en portales de PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ef4f61e7b9165d8d2c4abbc70c0bce65957665ab
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551701"
---
# <a name="create-and-manage-page-templates"></a>Crear y administrar plantillas de página

Mientras que las páginas web son nodos del mapa del sitio del portal que representan contenido accesible para los usuarios del portal, las plantillas de página representan las páginas. aspx reales que proporcionan un medio para mantener una apariencia coherente en todo el sitio Web. Las plantillas de página se crean mediante páginas de ASP.NET, páginas maestras, hojas de estilos en cascada (CSS), controles de usuario y controles de servidor.

Al crear una nueva página web para el sitio, ya sea a través de la publicación en el lado frontal o a través de la interfaz del portal, debe seleccionar una plantilla de página que presentará el contenido de la página a los usuarios del portal.

La diferencia entre las páginas web y las plantillas de página es posible que se entienda mejor como la diferencia entre una dirección URL exacta y una página. aspx real que actúa como un plano para mostrar el contenido. Cada página web representa una dirección URL específica en el sitio, a la que los usuarios pueden navegar. Cuando un usuario navega a una dirección URL, se muestra el contenido asociado a esa dirección URL. Sin embargo, una página web no contiene información sobre cómo se muestra el contenido.  Esto viene determinado por la plantilla de página, que es la página. aspx real que genera el código HTML que el usuario ve.

Al crear una nueva página web, debe elegir una plantilla de página de una lista de plantillas existentes. En cada uno de los portales de inicio se incluyen varias plantillas de página. Al usar estos portales como base para su propio sitio web, estas plantillas serán útiles como un medio básico para demostrar la funcionalidad del portal. Sin embargo, se necesitará un programador del portal para cambiar significativamente el diseño de estas páginas. En la mayoría de los casos, la plantilla de página "página" será la plantilla de página que se usará como uso general: se mostrará el contenido de una página web que use esta plantilla, así como una lista de páginas secundarias que se presentan como elementos de navegación.

## <a name="manage-page-templates"></a>Administrar plantillas de página

La creación de una nueva plantilla de página solo es necesaria cuando se crea una nueva página. aspx para mostrar el contenido en el sitio web, una tarea del desarrollador del portal. De hecho, para el propósito de simplemente personalizar el diseño del sitio, un programador del portal puede simplemente modificar las páginas. aspx existentes.

1. Pen la [aplicación de administración del portal](configure-portal.md).

2. Vaya a **portales** > **Página plantillas**.

3. Para crear una nueva plantilla de página, seleccione **nuevo**.

4. Para editar una plantilla de página existente, seleccione el nombre de la plantilla de página.

5. Escriba los valores adecuados en los campos.

6. Seleccione **Guardar y cerrar**.

### <a name="page-template-attributes"></a>Atributos de plantilla de página

|Nombre |Descripción |
|-----|--------|
|Nombre    |Nombre de la plantilla utilizada como referencia.   |
|Bsitio   |El sitio web asociado.   |
|Tipo   |El tipo de la plantilla, que controla cómo la plantilla determinará lo que se va a representar.<ul><li>**Reescribir**: usará el campo URL de reescritura para representar una plantilla de ASP.net determinada.</li><li>**Plantilla Web**: usará el campo de plantilla Web para representar una plantilla Web determinada.</li></ul>   |
|URL de reescritura   |Ruta de acceso de la página física ASP.NET. aspx (u otro recurso, como. ashx) que va a representar el contenido.<br> Este campo solo se muestra si se selecciona **reescribir URL** en la lista **tipo** . |
|Plantilla Web   |Referencia a una plantilla Web que se utilizará para representar esta plantilla.<br>Este campo solo se muestra si se selecciona **plantilla Web** en la lista **tipo** .  |
|Es el valor predeterminado   |Si es "sí", la plantilla será la predeterminada asignada a la lista desplegable de las herramientas de edición del lado cliente.   |
|Nombre de entidad   |Tipo de entidad de la página que esta plantilla espera presentar. Lo utilizará el sistema de edición en paralelo para presentar solo las opciones de plantilla adecuadas a los autores de contenido.<br>Normalmente, se trata de una página web (adx_webpage), pero puede ser otra entidad del portal, como el foro, el hilo del foro, el blog o la entrada de blog.   |
|Descripción  |Una descripción de esta plantilla, para beneficiarse de los usuarios de la edición frontal. |
|||

