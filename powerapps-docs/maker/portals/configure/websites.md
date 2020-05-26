---
title: Administrar sitios web en los portales | MicrosoftDocs
description: Aprenda a administrar sitios web en los portales.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/30/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ce0b60b8801873376696c446a56e28ffa69b8d80
ms.sourcegitcommit: 8e76afb331745f1da929a39e831634680dfa6008
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3346955"
---
# <a name="manage-websites"></a>Administrar sitios web

Un sitio web es la entidad principal de la aplicación de portales. Una aplicación del portal selecciona un único registro del sitio web, y esto determina qué entidades como [páginas web](web-page.md), [archivos web](web-files.md), [roles web](create-web-roles.md) y [fragmentos de contenido](customize-content-snippets.md) son válidas para esta aplicación.

Con un sitio web que proporciona un ámbito de aplicación, las distintas aplicaciones del portal se pueden conectar a una única organización.

> [!NOTE]
> El nombre del sitio web determina normalmente el registro del sitio web que al que se enlaza una aplicación del portal determinada. Este nombre se especifica en la configuración de la implementación del portal.
Sin embargo, también es posible controlar esto por nombre de dominio o enlaces de sitios web.

## <a name="manage-websites"></a>Administrar sitios web

Los sitios web se crean cuando crea un nuevo portal. Sin embargo, la administración de sitios web avanzada se puede realizar desde la aplicación Portal Management. 

> [!WARNING]
> Cuando elimina un registro de sitio web, también se eliminan los datos relacionados con el registro del sitio web en las entidades de metadatos del portal, como páginas web y enlaces web. Este es normalmente el comportamiento deseado, ya que implica que se pueda quitar el sitio web completo y todos sus datos relacionados de una organización de  en una única operación.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Páginas web**.

3. Para editar un sitio web existente, seleccione el nombre del sitio web.

4. Especifique o edite los valores adecuados en los campos.

5. Seleccione **Guardar y cerrar**.

### <a name="website-attributes"></a>Atributos del sitio web

|Nombre|Descripción|
|-|-|
|Nombre|El nombre descriptivo del sitio web. Este campo es obligatorio.|
| Idioma predeterminado | Idioma predeterminado para el portal seleccionado. Antes de cambiar el idioma predeterminado, debe: <br> - [Agregar el idioma en el entorno de Common Data Service](https://docs.microsoft.com/power-platform/admin/enable-languages). <br> - [Agregar el idioma en la sección de Idiomas compatibles](enable-multiple-language-support.md) para el registro de Sitios web.
| Propietario | El registro de contacto del propietario para el registro de Sitios web seleccionado.
|Nombre de dominio principal|El nombre de dominio principal del portal al que se agregó el registro de esta página web.|
|Sitio web primario\*|El sitio web principal del sitio web. Este campo se puede ignorar normalmente, excepto en determinadas configuraciones de portal avanzadas en las que una única aplicación del portal se enlaza con un sitio web maestro en la ruta raíz de la aplicación, con uno o más sitios web secundarios disponibles en las rutas secundarias específicas. <br>\* Solo para compatibilidad con versiones anteriores, no se debe utilizar para portales nuevos o existentes. |
| Plantillas de encabezado y pie de página | Las [Plantillas web para encabezados y pies de página](../liquid/store-content-web-templates.md#web-templates-as-page-templates) reemplazan encabezados y pies de página globales.
| Idiomas compatibles | Los [idiomas compatibles](enable-multiple-language-support.md) para el registro de Sitios web seleccionado.

### <a name="see-also"></a>Vea también

[Enlaces a sitios web](website-bindings.md)
