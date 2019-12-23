---
title: Crear y administrar plantillas de página en el portales de Power Apps | MicrosoftDocs
description: Aprenda a crear y administrar plantillas de página en portales de Power Apps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 435270ec5c996b90d5633650ed3813e6344a2db6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866815"
---
# <a name="create-and-manage-page-templates"></a>Crear y administrar plantillas de página

Mientras que las páginas web son nodos en el mapa de sitio del portal que representan el contenido accesible a los usuarios del portal, las plantillas de página representan las páginas .aspx reales que proporcionan una forma de conservar un aspecto coherente en todo el sitio web. Las plantillas de página se crean mediante páginas ASP.NET, páginas maestras, hojas de estilo en cascada (CSS), controles de usuario y controles de servidor.

Al crear una nueva página web para el sitio, ya sea mediante la publicación delantera o la interfaz del portal, debe seleccionar una plantilla de página que presentará el contenido de la página a los usuarios del portal.

Es posible que la diferencia entre las páginas web y las plantillas de página se entienda mejor como la diferencia entre la dirección URL exacta y una página .aspx real que funciona como modelo para la visualización de contenido. Cada página web representa una dirección URL específica en su sitio, a la que los usuarios pueden dirigirse. Cuando un usuario vaya a una dirección URL, se mostrará el contenido asociado con esa dirección URL. Sin embargo, una página web no contiene información sobre cómo se muestra ese contenido.  Esto lo determina la plantilla de página, que es la página .aspx real que genera el HTML que visualiza el usuario.

Al crear una nueva página web, debe elegir una plantilla de página de una lista de plantillas existentes. Se incluyen varias plantillas de página con cada uno de los portales de inicio. Cuando se usan estos portales como base para el propio sitio web, estas plantillas serán útiles como medio básico para demostrar la funcionalidad del portal. Sin embargo, será necesario desarrollador del portal para cambiar significativamente el diseño de estas páginas. En la mayoría de los casos, la plantilla de página "Página" será la plantilla de página que utiliza para fines generales: una página web que utiliza esta plantilla mostrará el contenido, así como una lista de páginas secundarias presentadas como elementos de navegación.

## <a name="manage-page-templates"></a>Administrar plantillas de página

La creación de una nueva plantilla de página solo es necesaria cuando se crea una página .aspx nueva para mostrar contenido en su sitio web, una tarea del desarrollador del portal. De hecho, para realizar una personalización sencilla del diseño de su sitio, un desarrollador del portal puede modificar en gran medida las páginas .aspx existentes.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Plantillas de página**.

3. Para crear una nueva plantilla de página, seleccione **Nuevo**.

4. Para editar una plantilla de página existente, seleccione el nombre de plantilla de página.

5. Especifique los valores adecuados en los campos.

6. Seleccione **Guardar y cerrar**.

### <a name="page-template-attributes"></a>Atributos de plantilla de página

|Nombre |Descripción |
|-----|--------|
|Nombre    |Nombre de la plantilla usada como referencia.   |
|Sitio web   |Sitio web asociado.   |
|Escribir   |El tipo de plantilla, que controla la forma en la que la plantilla determinará qué mostrar.<ul><li>**Reescritura**: se usará el campo Dirección URL de reescritura para mostrar una plantilla ASP.NET determinada.</li><li>**Plantilla web**: utilizará el campo Plantilla web para mostrar una plantilla web determinada.</li></ul>   |
|Dirección URL de reescritura   |Ruta de la página .aspx ASP.NET física (u otro recurso, como .ashx), que mostrará el contenido.<br> Este campo se muestra solo si se selecciona **Dirección URL de reescritura** en la lista **Tipo**. |
|Plantilla web   |Una referencia a una plantilla web que se usará para mostrar esta plantilla.<br>El campo se muestra solo si se selecciona **Plantilla web** en la lista **Tipo**.  |
|Es predeterminada   |Si el valor es "Sí", la plantilla se asignará de forma predeterminada al menú desplegable en las herramientas de edición del cliente.   |
|Nombre de entidad   |El tipo de entidad de la página que espera mostrar esta plantilla. El sistema de edición delantero lo usará para presentar solo las opciones de plantilla adecuadas a los autores de contenido.<br>Generalmente, será Página web (adx_webpage), pero puede ser otra entidad de portal , como Foro, Hilo de foro, Blog o Entada de blog.   |
|Descripción  |Una descripción de esta plantilla para el beneficio de los usuarios de edición delanteros. |
|||

