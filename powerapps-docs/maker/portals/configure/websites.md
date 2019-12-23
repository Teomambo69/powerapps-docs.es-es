---
title: Administrar sitios web en los portales | MicrosoftDocs
description: Aprenda a administrar sitios web en los portales.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/14/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8f085f6958be120d689d04cad904804b8f891530
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "2817675"
---
# <a name="manage-websites"></a>Administrar sitios web

Un sitio web es la entidad principal de la aplicación de portales. Una aplicación del portal selecciona un único registro del sitio web, y esto determina qué entidades ([páginas web](web-page.md), [archivos web](web-files.md), [roles web](create-web-roles.md), [fragmentos de contenido](customize-content-snippets.md), etc.) son válidas para esta aplicación.

Con un sitio web que proporciona un ámbito de aplicación, las distintas aplicaciones del portal se pueden conectar a una única organización.

> [!NOTE]
> El nombre del sitio web determina normalmente el registro del sitio web que al que se enlaza una aplicación del portal determinada. Este nombre se especifica en la configuración de la implementación del portal.
Sin embargo, también es posible controlar esto mediante el prefijo de la ruta de la dirección URL (consulte las descripciones del sitio web principal y la dirección URL parcial en los [atributos del sitio web](#website-attributes)), o mediante un dominio, con enlaces a los sitios web.

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
|-----|----------|
|Nombre|El nombre descriptivo del sitio web. Este campo es obligatorio.|
|Nombre de dominio principal|El nombre de dominio principal del portal al que se agregó el registro de esta página web.|
|Sitio web primario|El sitio web principal del sitio web. Este campo se puede ignorar normalmente, excepto en determinadas configuraciones de portal avanzadas en las que una única aplicación del portal se enlaza con un sitio web maestro en la ruta raíz de la aplicación, con uno o más sitios web secundarios disponibles en las rutas secundarias específicas.|
|Dirección URL parcial|El segmento de la ruta de la dirección URL raíz para todas las direcciones URL generadas para las entidades del portal relacionadas con este sitio web.<br>Por ejemplo, si una aplicación del portal se implementa para estar disponible en la ruta del dominio example.com, y este atributo no tiene ningún valor, una solicitud a `http://example.com/` mostrará la página web de inicio del sitio web de la aplicación (ya que la página web de inicio tiene que tener la dirección URL parcial establecida en "/").<br>Si este atributo se establece en el valor "my-website", la página web de inicio tendrá una dirección URL de `http://example.com/my-website/`, y todas las páginas del sitio web tendrán el mismo prefijo de ruta "/my-website/".<br>En la mayoría de las configuraciones de portal, este campo puede ignorarse y dejarse en blanco.<br>Se usan valores de dirección URL parciales como segmentos de la dirección URL. Por tanto, no deben contener caracteres no válidos para dirección URL, como "?", "#", "!", "%". Dado que las direcciones URL del portal se generan combinando valores de dirección URL parciales con barras diagonales ("/"), tampoco deben contener normalmente las barras diagonales.<br>La práctica recomendada sería restringir valores parciales de la dirección URL a letras, números y guiones o caracteres de subrayado. Por ejemplo: "comunicados-de-prensa", "Users_Guide", "product1".|
|||

### <a name="see-also"></a>Vea también
[Enlaces a sitios web](website-bindings.md)
