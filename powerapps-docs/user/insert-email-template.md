---
title: Inserción de una plantilla de correo electrónico al redactar un correo electrónico en aplicaciones basadas en modelos | Microsoft Docs
description: Inserte un mensaje de correo electrónico con formato previo al redactar un correo electrónico.
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: sbmjais
ms.author: shjais
manager: shujoshi
ms.openlocfilehash: abbef00f3b93809dadf617c4180b52a1372e625a
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051853"
---
# <a name="preview-insert-an-email-template"></a>Versión preliminar: Inserción de una plantilla de correo electrónico

La inserción de una plantilla de correo electrónico es una característica de acceso anticipado. Puede optar por la habilitación anticipada de estas características en el entorno. Esto le permite probar estas características y después adoptarlas en los entornos. Para obtener más información sobre cómo habilitar estas características, vea [Participación en actualizaciones de acceso anticipado](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

Puede usar una plantilla de correo electrónico (un mensaje de correo electrónico con formato previo) para crear y enviar mensajes de correo electrónico rápidamente. Para insertar la plantilla mientras redacta un correo electrónico, seleccione **Insertar plantilla** en la barra de comandos. La lista de plantillas disponibles se muestra en la ventana **Plantillas de correo electrónico**. En la sección **Usadas recientemente** se muestran las cuatro plantillas usadas más recientemente por el usuario. En la sección **Todas las plantillas** se muestra una lista de todas las plantillas de correo electrónico de serie (globales y específicas de entidad) en orden alfabético. Las plantillas globales se muestran como el tipo Usuario. Si ha creado una plantilla de correo electrónico personalizada, también está disponible aquí. Para obtener información sobre cómo crear una plantilla de correo electrónico personalizada, vea [Crear plantillas de correo electrónico](https://docs.microsoft.com/power-platform/admin/create-templates-email).

Puede ver las plantillas de un idioma determinado si selecciona un idioma en la lista **Idioma**. Puede buscar una plantilla o examinar la lista y seleccionarla. Al seleccionar una plantilla de correo electrónico, se muestra una vista previa en el lado derecho de la ventana. En la vista previa se muestra el contenido para que pueda elegir la plantilla que mejor se adapte a sus necesidades. Después de insertar una plantilla de correo electrónico, puede modificar el contenido según sea necesario y luego enviar el correo electrónico.

> [!NOTE]
> La búsqueda no admite expresiones regulares y solo funciona en el nombre de plantilla.

**Para insertar una plantilla de correo electrónico**

1.  En el editor de correo electrónico, seleccione **Insertar plantilla** en la barra de comandos.

     > [!div class="mx-imgBorder"]
     > ![Botón Insertar plantilla](media/insert-email-template-button.png "Botón Insertar plantilla") 

    Se abre la ventana **Plantillas de correo electrónico**.

2.  Para ver las plantillas de otra configuración regional, seleccione un idioma en la lista **Idioma**. Las plantillas se cargan según el idioma seleccionado.    

3.  Busque la plantilla que quiera. Seleccione la plantilla y obtenga una vista previa de su contenido.

4.  De forma opcional, puede seleccionar la flecha abajo del nombre de la plantilla para ver una descripción de su contenido.

5.  Seleccione **Aplicar plantilla** para insertar el contenido en el correo electrónico.

     > [!div class="mx-imgBorder"]
     > ![Ventana Plantillas de correo electrónico](media/email-templates-window.png "Ventana Plantillas de correo electrónico")

Si intenta insertar una plantilla de correo electrónico en un dispositivo con un tamaño de pantalla menor, solo se ve una opción para buscar y seleccionar una plantilla.

> [!div class="mx-imgBorder"]
> ![Búsqueda de plantilla](media/search-template.png "Búsqueda de plantilla") 

### <a name="see-also"></a>Vea también

[Configuración de correo electrónico mejorado](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[Redacción y envío de correo electrónico con la experiencia de correo electrónico mejorada](enhanced-email.md)
