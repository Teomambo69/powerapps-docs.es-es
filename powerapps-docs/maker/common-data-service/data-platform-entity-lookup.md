---
title: Inicio rápido para relaciones de entidad mediante un campo de búsqueda | Microsoft Docs
description: Inicio rápido para crear una relación entre entidades mediante un campo de búsqueda.
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: a607058d1e26f37a4bffa054d9dc148be8b6b011
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-create-a-relationship"></a>Inicio rápido: Creación de una relación
A menudo, los datos de una entidad se relacionan con los datos de otra entidad. Por ejemplo, es posible que tenga las entidades **Profesores** y **Clase**, y es posible que la entidad **Clase** tenga una relación de búsqueda con la entidad **Profesores** para mostrar qué profesor imparte la clase. Puede usar un campo de búsqueda para mostrar los datos de la entidad **Profesores**. Esto se conoce normalmente como un campo de búsqueda.

## <a name="define-a-relationship"></a>Definir una relación
Puede crear varios tipos de relaciones de una entidad a otra (o entre una entidad y ella misma). Cada entidad puede tener una relación con más de una entidad, y cada entidad puede tener más de una relación con otra entidad. Algunos tipos de relación comunes son:


* **Varios a uno**: en este tipo de relación, cada registro de la entidad A se corresponde con más de un registro en la entidad B, pero cada registro de la entidad B solo se corresponde con un registro de la entidad A. Por ejemplo, una clase solo tiene un aula. Es el tipo de relación más común y se muestra en la lista de campos como un **Campo de búsqueda**
* **Uno a varios**: en este tipo de relación, cada registro de la entidad B se puede corresponder con más de un registro en la entidad A, pero cada registro de la entidad A solo se corresponde con un registro de la entidad B. Por ejemplo, un mismo profesor imparte muchas clases.
* **Varios a varios**: en este tipo de relación, cada registro de la entidad A se corresponde con más de un registro de la entidad B y viceversa. Por ejemplo, los alumnos asisten a muchas clases y cada clase puede tener varios estudiantes.

## <a name="add-a-lookup-field-many-to-one-relationship"></a>Agregar un campo de búsqueda (relación varios a uno)

Para agregar una relación de búsqueda a una entidad, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que desea crear una relación.

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Pulse o haga clic en una entidad existente, o bien en [Crear una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4. Haga clic en **Agregar relación**; se abrirá un nuevo panel para elegir la entidad con la que quiere crear una relación. Seleccione la entidad en la lista desplegable **Entidades relacionadas**.

    ![Relación varios a uno](./media/data-platform-cds-newrelationship/manytoone-1.png "Many to One Relationship")

5. Después de seleccionar una entidad que los campos de búsqueda mostrarán en la Entidad principal, su valor predeterminado será el nombre de las entidades (en este ejemplo Aula), pero se pueden cambiar si es necesario.

    ![Relación varios a uno](./media/data-platform-cds-newrelationship/manytoone-2.png "Many to One Relationship")

6. Haga clic en **Listo** para agregar la relación a la entidad y, después, haga clic en **Guardar entidad**.

    ![Relación varios a uno](./media/data-platform-cds-newrelationship/manytoone-3.png "Many to One Relationship")

## <a name="add-a-one-to-many-relationship"></a>Agregar una relación uno a varios

Para agregar una relación uno a varios, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que quiere crear una relación.

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. Pulse o haga clic en una entidad existente, o bien en [Crear una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4. Haga clic en la flecha hacia abajo situada a la derecha de **Agregar relación**, esto le dará la opción de ambos tipos de relaciones. Haga clic en **Uno a varios**; se abrirá un nuevo panel para elegir la entidad con la que quiere crear una relación. Seleccione la entidad en la lista desplegable **Entidades relacionadas**.

    ![Relación uno a varios](./media/data-platform-cds-newrelationship/onetomany-1.png "One to Many Relationship")

5. Después de seleccionar una entidad que los campos de búsqueda mostrarán en la Entidad principal, su valor predeterminado será el nombre de las entidades (en este ejemplo Clase), pero se pueden cambiar si es necesario.

    > [!NOTE]
    > En el caso de las relaciones uno a varios, el campo de búsqueda se creará en la entidad relacionada, no en la entidad actualmente seleccionada. Si necesita la búsqueda en la entidad actual, cree una relación varios a uno.

    ![Relación uno a varios](./media/data-platform-cds-newrelationship/onetomany-2.png "One to Many Relationship")

6. Haga clic en **Listo** para agregar la relación a la entidad y, después, haga clic en **Guardar entidad**.

    ![Relación uno a varios](./media/data-platform-cds-newrelationship/onetomany-3.png "One to Many Relationship")

## <a name="add-a-many-to-many-relationship"></a>Agregar una relación varios a varios

Actualmente, esto solo está disponible a través del menú Opciones avanzadas. En la página de inicio de PowerApps, haga clic en "Opciones avanzadas" en el menú de la izquierda. Para obtener información sobre cómo crear la relación, vea [Crear relaciones N:N (varios a varios)](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships)

## <a name="use-a-lookup-field-in-an-app"></a>Usar un campo de búsqueda en una aplicación
Si [crea una aplicación automáticamente](../canvas-apps/data-platform-create-app.md) a partir de una entidad que contiene un campo de búsqueda, aparece como un control **Lista desplegable** que contiene los datos del campo **Nombre principal** de la entidad.

## <a name="next-steps"></a>Pasos siguientes
* [Generate an app by using a Common Data Service database](../canvas-apps/data-platform-create-app.md) (Generar una aplicación mediante una base de datos de Common Data Service)
* [Create an app from scratch using a Common Data Service database](../canvas-apps/data-platform-create-app-scratch.md) (Crear una aplicación desde cero mediante una base de datos de Common Data Service)

