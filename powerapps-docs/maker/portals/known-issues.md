---
title: Problemas conocidos en portales de PowerApps | Microsoft Docs
description: Obtenga más información sobre problemas conocidos en portales de PowerApps
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="known-issues"></a>Problemas conocidos

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

## <a name="general-issues"></a>Problemas generales

- La **Fecha de modificación** para la aplicación puede ser incorrecta porque son aplicaciones preaprovisionadas y podrían haber sido aprovisionadas anteriormente.

- El propietario del portal no se muestra correctamente. Se muestra como sistema.

- Si está reutilizando la dirección URL de un portal eliminado recientemente para crear un nuevo portal, tendrá cierto retraso para configurar tiempo de ejecución. Esto se debe a que la purga de recursos anteriores aún estaría en curso y puede tardar de 30 minutos a 1 hora para que el nuevo portal se configure en Azure.

- Al cambiar un entorno en PowerApps, los portales en un entorno pueden no mostrarse inmediatamente en **Aplicaciones** o lista **Aplicaciones recientes**. Esto ocurre en particular en entornos que se crean en una región distinta que su inquilino. La solución alternativa consiste en usar la actualización de explorador o esperar algún tiempo a que portal aparezca en la lista de aplicaciones.

- Cuando restablece el portal correctamente desde el Centro de administración de portales de PowerApps, aparece el error siguiente: “El portal al que está tratando de acceder no pertenece al inquilino en el que ha iniciado la sesión actual. Cierre la sesión e inicie sesión en el inquilino correcto.” Puede visite la página principal de PowerApps y crear un nuevo portal. 

## <a name="portal-designer-issues"></a>Problemas de diseñador del portal

-   Cuando se selecciona el texto en el cuadro de texto, el tamaño de fuente del texto seleccionado no se muestra en la barra de herramientas Formato.

- El espaciado de columnas en una sección no es lo mismo que el que se representa en la página web. El espaciado interno se ajusta según el contenido dentro de las secciones.

- El lienzo no carga contenido en idioma chino.

- La página web que utiliza la plantilla **Página con navegación lateral** muestra sólo el vínculo de las páginas que existían durante la creación de la página web. Puede actualizar los vínculos de la parte lateral izquierdo de la página cambiando la plantilla de página a otra plantilla y después de nuevo a **Página con navegación lateral**.

- Cuando elimina una página web, el lienzo no refleja el menú actualizado hasta la siguiente actualización del lienzo.

- Al crear una página secundaria desde una página de reescritura (páginas no admitidas en diseñador del portal), debe elegir manualmente la plantilla del panel de propiedades para representar la página.

- Si el nombre de página es grande y no se muestran completamente en el panel **Páginas**, no se muestra el botón **Puntos suspensivos** (...). Debe hacer clic con el botón secundario en el nombre de página para ver las opciones de página.

- Si agregó un fragmento de código de contenido desactivado en una página, se mostrará en el diseñador de portal. Sin embargo, el miniprograma de contenido desactivado estará oculto en la página web real.

- El marcador de algunos componentes como vínculos de web, Power BI, gráfico, etc. no son editables. Pero aún puede editar el texto de los mismos. Los cambios en los marcadores no se guardarán.

- La información y las acciones relacionados en el lienzo, como nombre componente, en el diseñador del portal sólo se admiten en inglés.

- El selector de colores y sus cadenas relacionadas sólo se admiten en inglés.

- Algunas páginas de plantilla en el portal Autoservicio de empleados no pueden representar la ruta de exploración correcta.

- Algunas plantillas de portales de Dynamics 365 no tienen elementos de menú según su jerarquía de páginas. Sin embargo, si crea nuevas páginas, los elementos de menú se crean en consecuencia.
