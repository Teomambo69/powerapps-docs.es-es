---
title: Problemas conocidos en portales de PowerApps | Microsoft Docs
description: Obtenga más información sobre problemas conocidos en portales de PowerApps
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 743db54c0f26323be841dd177c993fb30b310d5f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757376"
---
# <a name="known-issues"></a>Problemas conocidos


## <a name="general-issues"></a>Problemas generales

- La **Fecha de modificación** para la aplicación puede ser incorrecta porque son aplicaciones preaprovisionadas y podrían haber sido aprovisionadas anteriormente.

- Al crear un entorno junto con el portal de inicio, no se muestra el propietario del portal correctamente. Se muestra como sistema.

- Si está reutilizando la dirección URL de un portal eliminado recientemente para crear un nuevo portal, tendrá cierto retraso para configurar tiempo de ejecución. Esto se debe a que la purga de recursos anteriores aún estaría en curso y puede tardar de 30 minutos a 1 hora para que el nuevo portal se configure en Azure. El portal tampoco estará disponible para editar durante este tiempo y puede mostrar errores cuando se lance en Studio para su edición.

- Al cambiar un entorno en PowerApps, los portales en un entorno pueden no mostrarse inmediatamente en **Aplicaciones** o lista **Aplicaciones recientes**. Esto ocurre en particular en entornos que se crean en una región distinta que su inquilino. La solución alternativa consiste en usar la actualización de explorador o esperar algún tiempo a que portal aparezca en la lista de aplicaciones.

- Si mantiene abierto el panel de configuración del portal en la página principal de PowerApps mientras restablece el portal desde el Centro de administración de portales de PowerApps, un usuario verá el mensaje de error “Se ha producido un error" el panel de configuración del portal, ya que el portal no está disponible.

- En determinados casos, cuando se crea un portal, los estilos no se aplican correctamente al portal, y el sitio web se muestra sin los estilos cuando se abre con **Examinar sitio web**. Esto ocurre raramente y los estilos pueden ser recuperados reiniciando el portal desde el Centro de administración de portales de PowerApps.

## <a name="powerapps-portals-studio-issues"></a>Problemas de portales de PowerApps Studio

- Si un portal tiene jerarquía de páginas de más de tres niveles, las páginas del cuarto nivel en adelante no se muestran en portales de PowerApps Studio.

- El tamaño de fuente de texto seleccionado solo se visualizará si hay un tamaño de fuente definido específicamente para ese texto. Si es parte de etiquetas HTML estándar como p, H1, H2, H3, etc., portales de PowerApps Studio no mostrará el tamaño de fuente.

- La página web que utiliza la plantilla **Página con navegación lateral** muestra sólo el vínculo de las páginas que existían durante la creación de la página web. Puede actualizar los vínculos de la parte lateral izquierdo de la página cambiando la plantilla de página a otra plantilla y después de nuevo a **Página con navegación lateral**.

- Cuando elimina una página web, el lienzo no refleja el menú actualizado hasta la siguiente actualización del lienzo.

- El selector de colores y sus cadenas relacionadas sólo se admiten en inglés.

- Algunas páginas de plantilla en el portal Autoservicio de empleados no pueden representar la ruta de exploración correcta.

- Algunas plantillas de portales de PowerApps, enlazadas especialmente a las aplicaciones basadas en modelo en Dynamics 365, no tienen elementos de menú predeterminados en su jerarquía de páginas. La razón es que no hay orden de páginas disponible en todas o algunas páginas web. Cualquier portal sin orden de presentación de páginas web tendrá este problema.

- Se muestra un mensaje de error cuando el contenido de la página (copia de página) supera el límite de 65536 caracteres y el resumen de la página supera el límite predeterminado de 2000 caracteres.

- El menú de navegación solo es visible en el lienzo con una resolución de ancho mínimo de 1600px.

- Una imagen cargada en una página se convierte en el elemento secundario de la página. Si elimina la página, y usa la imagen en otra página, la imagen no se representará en portales de PowerApps Studio ni el sitio web.

- La representación de formulario no se admite actualmente en portales de PowerApps Studio. Cuando se agrega un formulario, debe seleccionar **Examinar sitio web** para abrir el sitio web y comprobar el formulario.

- En un fondo de texto o de sección, si cambia color a **Sin color**, portales de PowerApps Studio no quita los atributos relacionados como color de fondo o color de fuente, sino que convierte los valores en nulos.

- En los siguientes escenarios, portales de PowerApps Studio deja de cargar y muestra el error "Hay una desconexión":
    - Si la página principal se elimina o deshabilita para un portal.
    - Si una plantilla de página relacionada con la página principal o cualquier página se deshabilita o se elimina.

- Portales de PowerApps Studio no podrá cargar código fuente esos fragmentos de contenido que no tienen un idioma asignado en Common Data Service.

- En algunos casos los cambios del encabezado y el pie de página, a través de la experiencia WYSIWYG de portales de PowerApps Studio o a través del editor de código, no se reflejarán inmediatamente.

- Si a una página web se le asigna la plantilla de búsqueda en portales de PowerApps Studio, mostrará una página sencilla con el cargador. Para que esto funcione, tendrá que crear un marcador del sitio adecuado para esa página.

- La plantilla de Studio predeterminada también aparece como opción en la plantilla de página cuando se crea una nueva página una vez se usa en portales de PowerApps Studio. Además, esta plantilla se inserta solo en inglés y no admite la localización en función del idioma predeterminado de Common Data Service o del portal.

- Una lista representada como control del calendario o mapa no se puede configurar a través de portales de PowerApps Studio.

- El campo Dirección URL parcial en las propiedades de página no acepta caracteres especiales y rompe la representación en el lienzo durante algún tiempo. 

- La carga de CSS podría producir un error cuando el nombre de archivo CSS contenga caracteres especiales o espacios en el nombre de archivo.

- Las páginas web no publicadas no se representan en el lienzo de portales de PowerApps Studio.

- Mientras usa portales de PowerApps Studio, si el idioma base del portal es diferente del idioma del explorador, las nuevas páginas web creadas mediante la plantilla predeterminada de Studio tendrán contenido ficticio insertado en el idioma del explorador en lugar del idioma del portal.

- Solo se muestra CSS aplicado en la página raíz en el panel **Tema**. Aunque si intenta cargar un archivo CSS con un mismo nombre que cualquier otro archivo CSS disponible en el portal, portales de PowerApps Studio le pedirá que reemplace ese archivo.

- Portales de PowerApps Studio no se admite actualmente en Safari en un sistema operativo Mac y tiene los siguientes problemas:
    - La selección de componente no es correcta y al pasar el cursor sobre un componente se proporciona una indicación de destino incorrecta.
    - Dos o tres secciones de columna no se representan correctamente en portales de PowerApps Studio pero son correctas en el sitio web.

