---
title: 'Control Editor de texto enriquecido: referencia | Microsoft Docs'
description: Información sobre el control Editor de texto enriquecido, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/24/2018
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c9bbfd724f588dce86c5ba2e620404f554d2bcd
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732122"
---
# <a name="rich-text-editor-control-in-power-apps"></a>Control de editor de texto enriquecido en Power apps
Permite a los usuarios finales dar formato al texto dentro de un área de edición WYSIWYG.  El formato de salida es HTML.

## <a name="description"></a>Descripción
El control **Editor de texto enriquecido** proporciona al usuario de la aplicación un área de edición WYSIWYG para dar formato al texto.  El formato de entrada y salida del control es HTML.

El control permite pegar texto enriquecido copiado (es decir, desde el explorador web o Word) en el control.  

El uso previsto del control consiste en dar formato al texto y no garantiza que se conserve la integridad de la entrada HTML.  El editor eliminará todas las etiquetas de script, estilo, objeto y otras que puedan ser comprometedoras.  Esto significa que si se crea texto enriquecido fuera de las aplicaciones avanzadas, puede que no tenga el mismo aspecto que en el producto en el que se creó.

Entre las características admitidas actualmente se incluyen las siguientes:
- Negrita, cursiva, subrayado
- Color del texto, color de resaltado
- Tamaño del texto
- Listas numeradas, listas de viñetas
- Hipervínculos
- Borrar formato

Para usar el control dentro de un formulario, seleccione la tarjeta "Editar texto multilínea" y personalícela insertando el control Editor de texto enriquecido.

## <a name="key-properties"></a>Propiedades principales
**[Default](properties-core.md)** : propiedad de entrada para el valor de texto inicial que se muestra en el editor.

**HtmlText**: propiedad de salida para el texto enriquecido resultante en formato HTML.


## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla. Debe describir el fin de los datos adjuntos.

**[DisplayMode](properties-core.md)** : indica si el control permite agregar y eliminar archivos (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**EnableSpellCheck** : indica si está habilitado el corrector ortográfico del explorador. Tenga en cuenta que esta funcionalidad solo proporcionará la revisión ortográfica en el idioma predeterminado del explorador.  Power apps para Windows no admite esta propiedad.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Visible](properties-core.md)** : indica si un control está visible u oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.

> [!TIP]
> Use **Alt + 0** mientras el editor está centrado para obtener información sobre otros métodos abreviados de teclado.
