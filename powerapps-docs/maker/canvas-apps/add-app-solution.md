---
title: Cree una aplicación de lienzo en una solución | Microsoft Docs
description: En PowerApps, cree una aplicación de lienzo en una solución para que pueda implementar la aplicación en otro entorno
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dcb6a9c69e602b739d58afde2242d18b60e6f477
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356825"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>Crear una aplicación de lienzo desde dentro de una solución

Crear una aplicación desde dentro de una solución si, por ejemplo, desea implementar la aplicación en un entorno diferente. Las soluciones pueden contener no solo las aplicaciones, pero también entidades personalizadas, conjuntos de opciones y otros componentes. Puede personalizar rápidamente un entorno en una variedad de formas mediante la creación de aplicaciones y otros componentes desde dentro de una solución, exportar la solución y, a continuación, importarlo en otro entorno.

Las soluciones se basan en la misma plataforma de Dynamics 365 for Customer Engagement. Para obtener más información, consulte [información general sobre soluciones](../common-data-service/solutions-overview.md).

## <a name="prerequisite"></a>Requisito previo

Para seguir los pasos descritos en este tema, debe cambiar a un entorno que contiene una base de datos de Common Data Service.

## <a name="create-a-solution"></a>Crear una solución

Puede omitir este procedimiento si ya tiene una solución en la que desea crear una aplicación o al que desea vincular a una aplicación.

1. [Inicie sesión en](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) a PowerApps y, a continuación, (si es necesario) al entorno adecuado:

    - Si desea crear una aplicación desde dentro de una solución, cambie a cualquier entorno que contiene una base de datos de Common Data Service.
    - Si desea vincular una aplicación existente a una solución, cambie al entorno que contiene esa aplicación.

1. En la barra de navegación izquierdo, seleccione **soluciones**.

    > [!div class="mx-imgBorder"]
    > ![Opción de soluciones en la barra de navegación izquierdo](./media/add-app-solution/left-nav.png "opción soluciones en la barra de navegación izquierdo")

1. En el encabezado de la barra de título, seleccione **nueva solución**.

    > [!div class="mx-imgBorder"]
    > ![Opción de solución de nuevo en el banner](./media/add-app-solution/banner-new-solution.png "opción nueva solución en el banner")

1. En la ventana que aparece, especifique un nombre para mostrar, un publicador y una versión de la solución.

    > [!div class="mx-imgBorder"]
    > ![Opciones para una nueva solución](./media/add-app-solution/configure-new-solution.png "opciones para una nueva solución")

    Un nombre (sin espacios) se generará automáticamente basándose en el nombre para mostrar que especifique, pero si desea que puede personalizar el nombre generado. Puede especificar el publicador predeterminado para su entorno y **1.0** para la versión si no tiene necesidades específicas en esas áreas.

1. Cerca de la esquina superior izquierda, seleccione **guardar y cerrar**.

    > [!div class="mx-imgBorder"]
    > ![Guardar una nueva solución](./media/add-app-solution/save-new-solution.png "guardar una nueva solución")

## <a name="create-a-canvas-app-in-a-solution"></a>Cree una aplicación de lienzo en una solución

Puede crear una aplicación de lienzo en blanco desde dentro de una solución. Automáticamente, no se puede generar una aplicación de tres pantallas o personalizar una aplicación de ejemplo o de plantilla desde dentro de una solución.

1. [Inicie sesión en](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) a PowerApps.

1. Si es necesario, cambie al entorno que contiene la solución en la que desea crear una aplicación de lienzo.

1. En la barra de navegación izquierdo, seleccione **soluciones**.

    > [!div class="mx-imgBorder"]
    > ![Opción de soluciones en la barra de navegación izquierdo](./media/add-app-solution/left-nav.png "opción soluciones en la barra de navegación izquierdo")

1. En la lista de soluciones, seleccione la solución en la que desea crear una aplicación de lienzo.

1. En el encabezado de la barra de título, seleccione **New** > **aplicación** > **aplicación de lienzo**y, a continuación, seleccione el factor de forma (tableta o teléfono) de la aplicación que desea crear.

    > [!div class="mx-imgBorder"]
    > ![Opciones para crear una aplicación en una solución](./media/add-app-solution/new-option.png "opciones para crear una aplicación en una solución")

    PowerApps Studio se abre con un lienzo en blanco en otra pestaña del explorador.

1. Creación de la aplicación (o realizar al menos un cambio) y, a continuación, guarde los cambios.

1. En la pestaña del explorador donde se ha seleccionado la solución, seleccione **realiza** para actualizar la lista de componentes de la solución.

    > [!div class="mx-imgBorder"]
    > ![Botón](./media/add-app-solution/done-button.png "botón Listo")

    La nueva aplicación aparece en la lista de componentes para esa solución. Si guarda los cambios en la aplicación, se reflejarán en la versión que está en la solución.

## <a name="link-an-existing-canvas-app-to-a-solution"></a>Vincular una aplicación de lienzo existente a una solución

Si desea vincular una aplicación a una solución, ambos deben estar en el mismo entorno, y la aplicación debe haberse creada a partir de una solución.

1. [Inicie sesión en](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) a PowerApps.

1. Si es necesario, cambie al entorno que contiene la solución a la que desea vincular una aplicación.

1. En la barra de navegación izquierdo, seleccione **soluciones**.

    > [!div class="mx-imgBorder"]
    > ![Opción de soluciones en la barra de navegación izquierdo](./media/add-app-solution/left-nav.png "opción soluciones en la barra de navegación izquierdo")

1. En la lista de soluciones, seleccione la solución a la que desea vincular una aplicación.

1. En el encabezado de la barra de título, seleccione **agregar existente** > **aplicación** > **aplicación de lienzo**.

    > [!div class="mx-imgBorder"]
    > ![Opciones para vincular una aplicación existente de banner](./media/add-app-solution/add-existing.png "Banner opciones para vincular una aplicación existente")

    Aparece una lista de aplicaciones de lienzo que se crearon dentro de una solución en este entorno.

1. En la lista de aplicaciones, seleccione la aplicación que desea vincular a la solución y, a continuación, seleccione **agregar**.

    > [!div class="mx-imgBorder"]
    > ![Botón Agregar](./media/add-app-solution/add-button.png "botón Agregar")

## <a name="known-limitations"></a>Limitaciones conocidas

Para obtener información sobre las limitaciones conocidas, consulte [utilizan las soluciones en PowerApps](../common-data-service/use-solution-explorer.md#known-limitations). 

## <a name="next-steps"></a>Pasos siguientes

- Crear o vincular a más aplicaciones y [otros componentes](../common-data-service/use-solution-explorer.md), como entidades, flujos y paneles a la solución.
- [Exportación de la solución](../common-data-service/import-update-export-solutions.md) para que pueda implementarla en otro entorno, en AppSource y así sucesivamente.
