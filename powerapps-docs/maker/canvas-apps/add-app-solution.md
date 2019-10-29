---
title: Crear una aplicación de lienzo en una solución | Microsoft Docs
description: En PowerApps, cree una aplicación de lienzo en una solución para que pueda implementar la aplicación en otro entorno.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c908e3d25530b52b103ef58989545e46b931e791
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "71987702"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>Crear una aplicación de lienzo desde una solución

Cree una aplicación desde una solución si, por ejemplo, desea implementar la aplicación en un entorno diferente. Las soluciones pueden contener no solo aplicaciones, sino también entidades personalizadas, conjuntos de opciones y otros componentes. Puede personalizar rápidamente un entorno de varias maneras mediante la creación de aplicaciones y otros componentes desde una solución, exportar la solución y, a continuación, importarla en otro entorno.

Para obtener más información acerca de las soluciones, consulte [información general sobre soluciones](../common-data-service/solutions-overview.md).

## <a name="prerequisite"></a>Requisito previo

Para seguir los pasos de este tema, debe cambiar a un entorno que contenga una base de datos de Common Data Service.

## <a name="create-a-solution"></a>Crear una solución

Puede omitir este procedimiento si ya tiene una solución en la que desea crear una aplicación o a la que desea vincular una aplicación.

1. [Inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps y, si es necesario, cambie al entorno adecuado:

    - Si desea crear una aplicación desde una solución, cambie a cualquier entorno que contenga una base de datos de Common Data Service.
    - Si desea vincular una aplicación existente a una solución, cambie al entorno que contiene esa aplicación.

1. En la barra de navegación izquierda, seleccione **soluciones**.

    > [!div class="mx-imgBorder"]
    > ![Opción soluciones en la barra de navegación izquierda](./media/add-app-solution/left-nav.png "Opción soluciones en la barra de navegación izquierda")

1. En el encabezado situado debajo de la barra de título, seleccione **nueva solución**.

    > [!div class="mx-imgBorder"]
    > ![Opción New-Solution en el banner](./media/add-app-solution/banner-new-solution.png "Opción New-Solution en el banner")

1. En la ventana que aparece, especifique un nombre para mostrar, un publicador y una versión de la solución.

    > [!div class="mx-imgBorder"]
    > ![Opciones para una nueva solución](./media/add-app-solution/configure-new-solution.png "Opciones para una nueva solución")

    Un nombre (sin espacios) se generará automáticamente en función del nombre para mostrar que especifique, pero puede personalizar el nombre generado si lo desea. Puede especificar el publicador predeterminado para su entorno y **1,0** para la versión si no tiene necesidades específicas en esas áreas.

1. Cerca de la esquina superior izquierda, seleccione **Guardar y cerrar**.

    > [!div class="mx-imgBorder"]
    > ![Guardar una nueva solución](./media/add-app-solution/save-new-solution.png "Guardar una nueva solución")

## <a name="create-a-canvas-app-in-a-solution"></a>Crear una aplicación de lienzo en una solución

Puede crear una aplicación de lienzo en blanco en una solución. No se puede generar automáticamente una aplicación de tres pantallas ni personalizar una plantilla o aplicación de ejemplo desde una solución.

1. [Inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps.

1. Si es necesario, cambie al entorno que contiene la solución en la que desea crear una aplicación de lienzo.

1. En la barra de navegación izquierda, seleccione **soluciones**.

    > [!div class="mx-imgBorder"]
    > ![Opción soluciones en la barra de navegación izquierda](./media/add-app-solution/left-nav.png "Opción soluciones en la barra de navegación izquierda")

1. En la lista de soluciones, seleccione la solución en la que desea crear una aplicación de lienzo.

1. En el encabezado situado debajo de la barra de título, seleccione **nuevo** > aplicación > **Canvas**y, después, seleccione el factor de forma (teléfono o tableta) de **la aplicación que** desea crear.

    > [!div class="mx-imgBorder"]
    > ![Opciones para crear una aplicación en una solución](./media/add-app-solution/new-option.png "Opciones para crear una aplicación en una solución")

    PowerApps Studio se abre con un lienzo en blanco en otra pestaña del explorador.

1. Cree la aplicación (o realice al menos un cambio) y, a continuación, guarde los cambios.

1. En la pestaña explorador donde seleccionó la solución, seleccione **listo** para actualizar la lista de componentes de la solución.

    > [!div class="mx-imgBorder"]
    > ![Botón listo](./media/add-app-solution/done-button.png "Botón Listo")

    La nueva aplicación aparece en la lista de componentes de la solución. Si guarda cualquier cambio en la aplicación, se reflejará en la versión que se encuentra en la solución.

## <a name="link-an-existing-canvas-app-to-a-solution"></a>Vincular una aplicación de lienzo existente a una solución

Si desea vincular una aplicación a una solución, ambos deben estar en el mismo entorno y la aplicación debe haberse creado desde una solución.

1. [Inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps.

1. Si es necesario, cambie al entorno que contiene la solución a la que desea vincular una aplicación.

1. En la barra de navegación izquierda, seleccione **soluciones**.

    > [!div class="mx-imgBorder"]
    > ![Opción soluciones en la barra de navegación izquierda](./media/add-app-solution/left-nav.png "Opción soluciones en la barra de navegación izquierda")

1. En la lista de soluciones, seleccione la solución a la que desea vincular una aplicación.

1. En el encabezado situado debajo de la barra de título, seleccione Agregar > **aplicación** **existente** > **aplicación Canvas**.

    > [!div class="mx-imgBorder"]
    > ![Opciones de banner para vincular una aplicación existente](./media/add-app-solution/add-existing.png "Opciones de banner para vincular una aplicación existente")

    Aparece una lista de las aplicaciones de lienzo que se crearon en una solución en este entorno.

1. En la lista de aplicaciones, seleccione la aplicación que quiere vincular a la solución y, a continuación, seleccione **Agregar**.

    > [!div class="mx-imgBorder"]
    > ![Botón Agregar](./media/add-app-solution/add-button.png "Botón Agregar")

## <a name="known-limitations"></a>Limitaciones conocidas

Para obtener información sobre las limitaciones conocidas, consulte [uso de soluciones en PowerApps](../common-data-service/use-solution-explorer.md#known-limitations). 

## <a name="next-steps"></a>Pasos siguientes

- Cree o vincule más aplicaciones y [otros componentes](../common-data-service/use-solution-explorer.md), como entidades, flujos y paneles, a la solución.
- [Exporte la solución](../common-data-service/import-update-export-solutions.md) para que pueda implementarla en otro entorno, en AppSource, etc.
