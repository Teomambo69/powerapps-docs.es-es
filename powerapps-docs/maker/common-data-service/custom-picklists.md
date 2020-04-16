---
title: Crear un conjunto de opciones| Microsoft Docs
description: Instrucciones paso a paso para saber cómo crear un conjunto de opciones.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 375ead78421dae021841009c5c6d1308fa4ed24b
ms.sourcegitcommit: ca7df48f819795d28ccfcd4a862639e20a7fe8fe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "3169093"
---
# <a name="create-an-option-set"></a>Crear un conjunto de opciones

Los conjuntos de opciones le permiten incluir listas desplegables de valores fijos para un usuario dentro de la aplicación para garantizar la coherencia de datos. A veces se hace referencia a ellos como listas desplegables o campos de opciones en otras aplicaciones. Similar a las entidades, hay conjuntos de opciones estándar y la posibilidad de crear conjuntos de opciones personalizadas para usar dentro de la aplicación.

Los conjuntos de opciones se pueden crear de dos maneras, ya sea desde la lista de **Conjuntos de opciones** del portal o directamente en una entidad cuando se crea un campo. Para obtener más información sobre cómo crear una entidad, consulte [Crear una entidad](data-platform-create-entity.md).

## <a name="creating-an-option-set-while-adding-a-field"></a>Crear un conjunto de opciones mientras agrega un campo

1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Agregue un nuevo campo a la entidad haciendo clic en **Agregar campo**.

4. En el panel del nuevo campo, introduzca el **Nombre para mostrar** para el campo, el **Nombre** se rellenará automáticamente y se usa como el nombre único para el campo. Se usa **Nombre para mostrar** al mostrar este campo a sus usuarios, se usa **Nombre** cuando crea la aplicación, en expresiones y fórmulas.

5. Haga clic en la lista desplegable **Tipo de datos** y seleccione **Conjunto de opciones** o **Conjunto de opciones de selección múltiple**.

    > [!div class="mx-imgBorder"] 
    > ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel.png "Panel Nuevo campo")

6. Haga clic en la lista desplegable **Conjunto de opciones** y seleccione **Nuevo conjunto de opciones**

    > [!NOTE]
    > Si un conjunto de opciones existente puede usarse para la entidad, puede seleccionarla de esta lista sin crear una nueva.

    ![Lista de conjunto de opciones](./media/data-platform-cds-newoptionset/fieldpanel-1.png "Lista de conjunto de opciones")

7. Se abrirá un nuevo panel para crear el conjunto de opciones. El **Nombre para mostrar** y el **Nombre** se adoptarán por defecto del nombre del campo, pero se pueden cambiar si es necesario. Haga clic en **Agregar nuevo elemento** para empezar a crear la lista de opciones. Repita este paso hasta que se creen todos los elementos.

    > [!div class="mx-imgBorder"] 
    > ![Nuevo conjunto de opciones](./media/data-platform-cds-newoptionset/field-optionsetpanel.png "Nuevo conjunto de opciones")

8. Una vez que haya introducido los elementos, haga clic en **Guardar** para crear el conjunto de opciones.

    > [!div class="mx-imgBorder"] 
    > ![Nuevo conjunto de opciones](./media/data-platform-cds-newoptionset/field-optionsetpanel-values.png "Nuevo conjunto de opciones")

9. Haga clic en **Hecho** para cerrar el panel del campo y, a continuación, en **Guardar entidad** para guardar la entidad en Common Data Service.

    > [!NOTE]
    > Puede seleccionar uno de los elementos como **Predeterminado** para este campo y se seleccionará de forma predeterminada cuando los usuarios creen nuevos registros en la entidad.

    > [!div class="mx-imgBorder"] 
    > ![Nuevo campo](./media/data-platform-cds-newoptionset/fieldpanel-2.png "Panel Nuevo campo")

## <a name="creating-an-option-set-from-the-option-set-list"></a>Crear un conjunto de opciones desde la lista de conjuntos de opciones

1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Conjuntos de opciones** en el panel de navegación de la izquierda.

    > [!div class="mx-imgBorder"] 
    > ![Conjuntos de opciones](./media/data-platform-cds-newoptionset/optionsetlist.png "Lista de conjunto de opciones")

2. Haga clic en **Nuevo conjunto de opciones**

3. Se abrirá un nuevo panel para crear el conjunto de opciones, introduzca el **Nombre para mostrar** y el **Nombre**. Haga clic en **Agregar nuevo elemento** para empezar a crear la lista de opciones. Repita este paso hasta que se creen todos los elementos.

    > [!div class="mx-imgBorder"] 
    > ![Crear conjunto de opciones](./media/data-platform-cds-newoptionset/optionset-create.png "Crear conjunto de opciones")

4. Una vez que haya introducido los elementos, haga clic en **Guardar** para crear el conjunto de opciones.

    > [!div class="mx-imgBorder"] 
    > ![Nuevo conjunto de opciones](./media/data-platform-cds-newoptionset/optionset-create-values.png "Nuevo conjunto de opciones")

5. Ahora puede utilizar este conjunto de opciones para crear un nuevo campo en una entidad.

## <a name="global-and-local-option-sets"></a>Conjuntos de opciones globales y locales

De forma predeterminada, los conjuntos de opciones se crean como conjuntos de opciones globales que permite reutilizarlos en varias entidades. En la opción **Ver más**, al crear un nuevo conjunto de opciones puede elegir establecer un conjunto de opciones como **Local**. Esta opción solo está disponible al crear un conjunto de opciones mientras agrega un campo, y no en la lista de **Conjuntos de opciones**. Los conjuntos de opciones locales solo se pueden usar en la entidad y el campo para los que se han creado, y no se pueden reutilizar en otras entidades. Este método se recomienda solo para usuarios avanzados con una necesidad específica para un conjunto de opciones local.

> [!IMPORTANT]
> Una vez creado un conjunto de opciones como local o global, no se puede cambiar.
