---
title: Crear una relación entre entidades usando un campo de búsqueda | Microsoft Docs
description: Instrucciones paso a paso sobre cómo crear una relación entre entidades en PowerApps usando un campo de búsqueda.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-a-relationship-between-entities"></a>Crear una relación entre entidades
Los datos de una entidad suelen estar relacionados con los datos de otra entidad. Por ejemplo, podría tener una entidad **Profesores** y una entidad **Clase**, y la entidad **Clase** podría tener una relación de búsqueda con la entidad **Profesores** para indicar qué profesor da la clase. Puede usar un campo de búsqueda para mostrar los datos de la entidad **Profesores**. Se le suele denominar campo de búsqueda.

## <a name="define-a-relationship"></a>Definir una relación
Puede crear varios tipos de relaciones desde una entidad a otra (o entre una entidad y ella misma). Cada entidad puede tener una relación con más de una entidad, y cada entidad puede tener más de una relación con otra entidad. Algunos tipos de relación comunes son:

* **Varios a uno** - En este tipo de relación, cada registro de la entidad A puede coincidir con más de un registro de la entidad B, pero cada registro de la entidad B solo puede coincidir con un registro de la entidad A. Por ejemplo, una clase solo tiene una sala. Este es el tipo de relación más común y se muestra en la lista de campos como **Campo de búsqueda**
* **Uno a varios** - En este tipo de relación, cada registro de la entidad B puede coincidir con más de un registro de la entidad A, pero cada registro de la entidad A solo puede coincidir con un registro de la entidad B. Por ejemplo, un único profesor da varias clases.
* **Varios a varios** - En este tipo de relación, cada registro de la entidad A puede coincidir con más de un registro de la entidad B, y viceversa. Por ejemplo, los alumnos asisten a muchas clases y cada clase puede tener varios alumnos.

## <a name="add-a-lookup-field-many-to-one-relationship"></a>Agregar un campo de búsqueda (relación de varios a uno)

Para agregar una relación de búsqueda a una entidad, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que desee crear una relación.

1. En [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4. Haga clic en **Agregar relación**, se abrirá un nuevo panel para que elija la entidad con la que desea crear una relación. Seleccione la entidad en la lista desplegable **Entidad relacionada**.

    > [!div class="mx-imgBorder"] 
    > ![Relación de varios a uno](./media/data-platform-cds-newrelationship/manytoone-1.png "Relación de varios a uno")

5. Después de seleccionar una entidad, los campos de búsqueda se mostrarán en la entidad principal y adoptarán de forma predeterminada el nombre de las entidades (en este ejemplo, Clase), aunque puede cambiarlo si es necesario.

    ![Relación de varios a uno](./media/data-platform-cds-newrelationship/manytoone-2.png "Relación de varios a uno")

6. Haga clic en **Hecho** para agregar la relación a la entidad y, a continuación, haga clic en **Guardar entidad**.

    > [!div class="mx-imgBorder"] 
    > ![Relación de varios a uno](./media/data-platform-cds-newrelationship/manytoone-3.png "Relación de varios a uno")

## <a name="add-a-one-to-many-relationship"></a>Agregar una relación de uno a varios

Para agregar una relación de uno a varios, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que desee crear una relación.

1. En [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4. Haga clic en la flecha abajo, a la derecha de **Agregar relación**; se le ofrecerá la opción de ambos tipos de relaciones. Haga clic en **Uno a varios**, se abrirá un nuevo panel para que elija la entidad con la que desea crear una relación. Seleccione la entidad en la lista desplegable **Entidad relacionada**.

    ![Relación de uno a varios](./media/data-platform-cds-newrelationship/onetomany-1.png "Relación de uno a varios")

5. Después de seleccionar una entidad, los campos de búsqueda se mostrarán en la entidad principal y adoptarán de forma predeterminada el nombre de las entidades (en este ejemplo, Clase), aunque puede cambiarlo si es necesario.

    > [!NOTE]
    > En el caso de relaciones de uno a varios, el campo de búsqueda se creará en la entidad relacionada, no en la entidad seleccionada actualmente. Si necesita que la búsqueda esté en la entidad actual, cree una relación de varios a uno.

    > [!div class="mx-imgBorder"] 
    > ![Relación de uno a varios](./media/data-platform-cds-newrelationship/onetomany-2.png "Relación de uno a varios")

6. Haga clic en **Hecho** para agregar la relación a la entidad y, a continuación, haga clic en **Guardar entidad**.

    > [!div class="mx-imgBorder"] 
    > ![Relación de uno a varios](./media/data-platform-cds-newrelationship/onetomany-3.png "Relación de uno a varios")

## <a name="add-a-many-to-many-relationship"></a>Agregar una relación de varios a varios

Actualmente solo está disponible mediante el menú Avanzado. En la página principal de PowerApps, haga clic en “Avanzado” en el menú izquierdo. Para obtener información sobre cómo crear la relación, consulte [Crear relaciones de N:N](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships)

## <a name="use-a-lookup-field-in-an-app"></a>Usar un campo de búsqueda en una aplicación
Si [crea una aplicación automáticamente](../canvas-apps/data-platform-create-app.md) a partir de una entidad que contiene un campo de búsqueda, ésta aparece como control **Desplegable** que contiene datos del campo **Nombre principal** de la entidad.

## <a name="next-steps"></a>Pasos siguientes
* [Generar una aplicación usando una base de datos de Common Data Service](../canvas-apps/data-platform-create-app.md)
* [Crear una aplicación desde cero usando una base de datos de Common Data Service](../canvas-apps/data-platform-create-app-scratch.md)

