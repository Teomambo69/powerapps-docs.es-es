---
title: Creación de un conjunto de opciones | Microsoft Docs
description: Instrucciones paso a paso sobre cómo crear un conjunto de opciones.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 188add46a8e52cfeb75ef1bb670ca3b457963024
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34168605"
---
# <a name="create-an-option-set"></a>Creación de un conjunto de opciones

Los conjuntos de opciones permiten incluir listas desplegables de valores fijos para un usuario de la aplicación para garantizar la coherencia de los datos, lo que en otras aplicaciones a veces se denominan listas desplegables o campos de elección. Al igual que las entidades, existe la posibilidad de usar conjuntos de opciones estándar o crear conjuntos de opciones personalizados para usarlos en una aplicación.

Los conjuntos de opciones se pueden crear de dos maneras, desde la lista Conjuntos de opciones en el portal o directamente desde una entidad durante la creación de un campo. Para obtener más información sobre cómo crear una entidad, vea [Crear una entidad](data-platform-create-entity.md).

## <a name="creating-an-option-set-while-adding-a-field"></a>Creación de un conjunto de opciones mientras se agrega un campo.

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Pulse o haga clic en una entidad existente, o bien en [Crear una nueva entidad](data-platform-create-entity.md)

3. Agregue un campo nuevo a la entidad haciendo clic en **Agregar campo**.

4. En el panel Nuevo campo, escriba el **Nombre para mostrar** para el campo, **Nombre** se rellenará automáticamente y se usará como el nombre único del campo. El **Nombre para mostrar** se usa cuando se presenta este campo a los usuarios, el **Nombre** se usa al compilar la aplicación, en las fórmulas y expresiones.

    ![Nuevo campo](./media/data-platform-cds-create-entity/newfieldpanel.png "Panel Nuevo campo")

5. Haga clic en la lista desplegable **Tipo de datos** y seleccione **Conjunto de opciones** o **Conjunto de opciones de selección múltiple**.

6. Haga clic en la lista desplegable **Conjunto de opciones**  y seleccione **Nuevo conjunto de opciones**.

    > [!NOTE]
    > Si se puede usar un conjunto de opciones existente para la entidad, se puede seleccionar en esta lista sin crear uno.

    ![Lista Conjunto de opciones](./media/data-platform-cds-newoptionset/fieldpanel-1.png "Option Set list")

7. Se abrirá un nuevo panel para crear el conjunto de opciones, y **Nombre para mostrar** y **Nombre** tendrán como valor predeterminado del nombre del campo, pero se puede cambiar si es necesario. Haga clic en **Agregar nuevo elemento** para comenzar a crear la lista de opciones. Repita este paso hasta que se creen todos los elementos.

    ![Nuevo conjunto de opciones](./media/data-platform-cds-newoptionset/field-optionsetpanel.png "New Option Set")

8. Una vez escritos los elementos, haga clic en **Guardar** para crear el conjunto de opciones.

    ![Nuevo conjunto de opciones](./media/data-platform-cds-newoptionset/field-optionsetpanel-values.png "New Option Set")

9. Haga clic en **Listo** para cerrar el panel Campo y después en **Guardar entidad** para guardar la entidad en Common Data Service.

    > [!NOTE]
    > Puede seleccionar uno de los elementos como el **Predeterminado** para este campo y se seleccionará de forma predeterminada cuando los usuarios creen registros en la entidad.

    ![Nuevo campo](./media/data-platform-cds-newoptionset/fieldpanel-2.png "Panel Nuevo campo")

## <a name="creating-an-option-set-from-the-option-set-list"></a>Creación de un conjunto de opciones desde la lista Conjunto de opciones

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Conjuntos de opciones** en el panel de navegación de la izquierda.

    ![Conjunto de opciones](./media/data-platform-cds-newoptionset/optionsetlist.png "Lista Conjunto de opciones")

2. Haga clic en **Nuevo conjunto de opciones**

3. Se abrirá un panel nuevo para crear el conjunto de opciones, escriba el **Nombre para mostrar** y el **Nombre**. Haga clic en **Agregar nuevo elemento** para comenzar a crear la lista de opciones. Repita este paso hasta que se creen todos los elementos.

    ![Crear conjunto de opciones](./media/data-platform-cds-newoptionset/optionset-create.png "Option Set Create")

4. Una vez escritos los elementos, haga clic en **Guardar** para crear el conjunto de opciones.

    ![Nuevo conjunto de opciones](./media/data-platform-cds-newoptionset/optionset-create-values.png "New Option Set")

5. Ahora se puede usar este conjunto de opciones mediante la creación de campos en una entidad.

## <a name="global-and-local-option-sets"></a>Conjuntos de opciones globales y locales

De forma predeterminada, los conjuntos de opciones se crean como conjuntos de opciones globales, lo que permite reutilizarlos en varias entidades. Al crear un conjunto de opciones, en la opción **Ver más** se puede elegir crear un conjunto de opciones **Local**. Esta opción solo está disponible al crear un conjunto de opciones al agregar un campo y no a través de la lista Conjunto de opciones. Los conjuntos de opciones locales solo se pueden usar por la entidad y el campo sobre los que se crean, y no se pueden reutilizar en otras entidades. Solo se recomienda este enfoque para usuarios avanzados con una necesidad concreta para un conjunto de opciones local.

> [!IMPORTANT]
> Una vez que se crea un conjunto de opciones como local o global, no se puede cambiar.