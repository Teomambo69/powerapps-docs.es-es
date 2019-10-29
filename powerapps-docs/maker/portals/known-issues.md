---
title: Problemas conocidos de los portales de PowerApps | Microsoft Docs
description: Más información sobre los problemas conocidos de los portales de PowerApps
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 86dde24b131eb1d3825301d93735a6d006ebc2dc
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975205"
---
# <a name="known-issues"></a>Problemas conocidos


## <a name="general-issues"></a>Problemas generales

- Es posible que la **fecha modificada** de la aplicación sea incorrecta porque se trata de aplicaciones aprovisionadas previamente y que podrían haberse aprovisionado anteriormente.

- Cuando se crea un entorno junto con el portal de inicio, el propietario del portal no se muestra correctamente. Se muestra como System.

- Si va a volver a usar la dirección URL de un portal eliminado recientemente para crear un nuevo portal, tendrá algún retraso en el tiempo de ejecución para el programa de instalación. Esto se debe a que la purga de los recursos anteriores seguiría en curso y puede tardar entre 30 minutos y 1 hora en instalar el nuevo portal en Azure. En este momento, el portal no estará disponible para su edición y puede mostrar errores cuando se inicie en Studio para su edición.

- Al cambiar un entorno en PowerApps, es posible que los portales dentro de un entorno no se muestren inmediatamente en **aplicaciones** o en la lista de **aplicaciones recientes** . Esto sucede especialmente en los entornos creados en una región distinta a la de su inquilino. La solución consiste en usar la actualización del explorador o esperar algún tiempo para que el portal se muestre en la lista de aplicaciones.

- Si mantiene el panel de configuración del portal abierto en la Página principal de PowerApps al restablecer el portal desde el centro de administración de portales de PowerApps, un usuario verá el mensaje de error "se ha producido un problema" en el panel de configuración del portal, ya que el portal no está disponible.

- En algunos casos, cuando se crea un portal, los estilos no se aplican correctamente en el portal y el sitio web se muestra sin los estilos cuando se abre a través de **examinar sitio web**. Esto raramente sucede y los estilos se pueden recuperar reiniciando el portal desde el centro de administración de portales de PowerApps.

## <a name="powerapps-portals-studio-issues"></a>Problemas del estudio de portales de PowerApps

- Si un portal tiene una jerarquía de páginas de más de tres niveles, las páginas del cuarto nivel en adelante no se muestran en el estudio de portales de PowerApps.

- El tamaño de fuente del texto seleccionado solo se mostrará si hay un tamaño de fuente definido específicamente para ese texto. Si forma parte de las etiquetas HTML estándar como p, H1, H2, H3, etc., PowerApps portales Studio no mostrará el tamaño de fuente.

- La página web que usa la página con la plantilla de **navegación lateral** muestra solo el vínculo de las páginas que existían durante la creación de la Página Web. Puede actualizar los vínculos en el lado izquierdo de la página cambiando la plantilla de página a otra plantilla y, a continuación, volver a la **página con navegación lateral**.

- Al eliminar una página web, Canvas no refleja el menú actualizado hasta la siguiente actualización de canvas.

- El selector de colores y sus cadenas relacionadas solo se admiten en inglés.

- Algunas páginas de plantillas en el portal de autoservicio para empleados no pueden representar una ruta de navegación correcta.

- Algunas plantillas de portales de PowerApps, especialmente enlazadas a aplicaciones controladas por modelos en Dynamics 365, no tienen elementos de menú predeterminados según su jerarquía de páginas. La razón es que no hay ningún orden de páginas disponible en todas o algunas de las páginas Web. Cualquier portal sin el orden de presentación de las páginas web tendrá este problema.

- Se muestra un mensaje de error cuando el contenido de la página (copia de página) supera el límite de 65536 caracteres y el Resumen de página supera el límite predeterminado de 2000 caracteres.

- El menú de navegación solo está visible en el lienzo con una resolución de ancho mínimo de 1600px.

- Una imagen cargada en una página se convierte en el elemento secundario de la página. Si elimina la página y usa la imagen en otra página, la imagen no se representará en los portales y el sitio web de PowerApps portales.

- La representación de formularios no se admite actualmente en PowerApps portales Studio. Al agregar un formulario, debe seleccionar **examinar sitio web** para abrir el sitio web y comprobar el formulario.

- En un fondo de texto o de sección, si cambia el color a **ningún color**, PowerApps portales Studio no quita los atributos relacionados como el color de fondo o el color de fuente, sino que hace que los valores sean null.

- En los siguientes escenarios, PowerApps Portals Studio deja de cargarse y muestra el error "lo sentimos, hay una desconexión":
    - Si la Página principal se ha eliminado o deshabilitado para un portal.
    - Si una plantilla de página relacionada con la Página principal o cualquier página está deshabilitada o eliminada.

- PowerApps portales Studio no podrá cargar el código fuente de los fragmentos de contenido que no tienen un idioma asignado en Common Data Service.

- En algunos casos, los cambios de encabezado y pie de página, ya sea a través de la experiencia WYSIWYG de PowerApps portal Studio o a través del editor de código, no se reflejarán inmediatamente.

- Si se asigna a una página web la plantilla de búsqueda en PowerApps portales Studio, se mostrará una página simple con loader. Para que esto funcione, tendrá que crear un marcador de sitio adecuado para esa página.

- La plantilla de estudio predeterminada también se muestra como una opción en la plantilla de página al crear una nueva página una vez que se usa en PowerApps Portals Studio. Además, esta plantilla solo se inserta en el idioma inglés y no admite la localización basada en el Common Data Service o el idioma del portal predeterminados.

- Una lista representada como un control de calendario o asignación no es configurable a través de PowerApps portales Studio.

- El campo de dirección URL parcial de las propiedades de página no acepta caracteres especiales y interrumpe el procesamiento en el lienzo durante algún tiempo. 

- La carga de CSS podría producir un error en escenarios donde el nombre de archivo CSS contiene caracteres especiales o espacio en el nombre de archivo.

- Las páginas web no publicadas no se representan en el lienzo de PowerApps portales Studio.

- Al usar PowerApps portales Studio, si el idioma de la base del portal es diferente del idioma del explorador, las nuevas páginas web creadas con la plantilla de estudio predeterminada tendrán contenido ficticio insertado en el idioma del explorador en lugar de en el idioma del portal.

- En el panel de **tema** solo se muestra el CSS aplicado en la página raíz. Aunque, si intenta cargar un archivo CSS con el mismo nombre que cualquier otro archivo CSS disponible en el portal, PowerApps Portals Studio le pedirá que reemplace ese archivo.

- PowerApps portales Studio no se admite actualmente en Safari en el sistema operativo Mac y tiene los siguientes problemas:
    - La selección del componente no es correcta y el desplazarse por un componente proporciona una indicación de destino incorrecta.
    - Dos o tres secciones de columna no se representan correctamente en PowerApps portal Studio, pero funciona bien en el sitio Web.

