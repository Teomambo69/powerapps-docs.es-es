---
title: Crear una relación entre entidades usando un campo de búsqueda | Microsoft Docs
description: Instrucciones paso a paso sobre cómo crear una relación entre entidades en Power Apps usando un campo de búsqueda.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 02/21/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 468f31eeb48a3e79f79db9188be78a7fa6d28c18
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883592"
---
# <a name="create-a-relationship-between-entities"></a>Crear una relación entre entidades
Los datos de una entidad suelen estar relacionados con los datos de otra entidad. Por ejemplo, podría tener una entidad **Profesores** y una entidad **Clase**, y la entidad **Clase** podría tener una relación de búsqueda con la entidad **Profesores** para indicar qué profesor da la clase. Puede usar un campo de búsqueda para mostrar los datos de la entidad **Profesores**. Se le suele denominar campo de búsqueda.

## <a name="define-a-relationship"></a>Definir una relación
Puede crear varios tipos de relaciones desde una entidad a otra (o entre una entidad y ella misma). Cada entidad puede tener una relación con más de una entidad, y cada entidad puede tener más de una relación con otra entidad. Algunos tipos de relación comunes son:

* **Varios a uno** - En este tipo de relación, cada registro de la entidad A puede coincidir con más de un registro de la entidad B, pero cada registro de la entidad B solo puede coincidir con un registro de la entidad A. Por ejemplo, una clase solo tiene una sala. Este es el tipo de relación más común y se muestra en la lista de campos como **Campo de búsqueda**
* **Uno a varios** - En este tipo de relación, cada registro de la entidad B puede coincidir con más de un registro de la entidad A, pero cada registro de la entidad A solo puede coincidir con un registro de la entidad B. Por ejemplo, un único profesor da varias clases.
* **Varios a varios** - En este tipo de relación, cada registro de la entidad A puede coincidir con más de un registro de la entidad B, y viceversa. Por ejemplo, los alumnos asisten a muchas clases y cada clase puede tener varios alumnos.

Además, puede establecer comportamientos en cascada avanzados en relaciones de varios a uno y de uno a varios siempre que se realice una acción en la entidad principal.

## <a name="add-a-lookup-field-many-to-one-relationship"></a>Agregar un campo de búsqueda (relación de varios a uno)

Para agregar una relación de búsqueda a una entidad, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que desee crear una relación.

1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4. Haga clic en **Agregar relación**, se abrirá un nuevo panel para que elija la entidad con la que desea crear una relación. Seleccione la entidad en la lista desplegable **Entidad relacionada**.

    > [!div class="mx-imgBorder"] 
    > ![Relación varios a uno](./media/data-platform-cds-newrelationship/manytoone-1.png "Relación varios a uno")

5. Después de seleccionar una entidad, los campos de búsqueda se mostrarán en la entidad principal y adoptarán de forma predeterminada el nombre de la entidad (en este ejemplo, Clase), aunque puede cambiarlo si es necesario.

    ![Relación varios a uno](./media/data-platform-cds-newrelationship/manytoone-2.png "Relación varios a uno")

6. Haga clic en **Hecho** para agregar la relación a la entidad y, a continuación, haga clic en **Guardar entidad**.

    > [!div class="mx-imgBorder"] 
    > ![Relación varios a uno](./media/data-platform-cds-newrelationship/manytoone-3.png "Relación varios a uno")

## <a name="add-a-one-to-many-relationship"></a>Agregar una relación de uno a varios

Para agregar una relación de uno a varios, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que desee crear una relación.

1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4. Haga clic en la flecha abajo, a la derecha de **Agregar relación**; se le ofrecerá la opción de ambos tipos de relaciones. Haga clic en **Uno a varios**, se abrirá un nuevo panel para que elija la entidad con la que desea crear una relación. Seleccione la entidad en la lista desplegable **Entidad relacionada**.
    > [!div class="mx-imgBorder"] 
    > ![Relación uno a varios](./media/data-platform-cds-newrelationship/onetomany-1.png "Relación uno a varios")

5. Después de seleccionar una entidad, los campos de búsqueda se mostrarán en la entidad principal y adoptarán de forma predeterminada el nombre de las entidades (en este ejemplo, Clase), aunque puede cambiarlo si es necesario.

    > [!NOTE]
    > En el caso de relaciones de uno a varios, el campo de búsqueda se creará en la entidad relacionada, no en la entidad seleccionada actualmente. Si necesita que la búsqueda esté en la entidad actual, cree una relación de varios a uno.

    > [!div class="mx-imgBorder"] 
    > ![Relación uno a varios](./media/data-platform-cds-newrelationship/onetomany-2.png "Relación uno a varios")

6. Haga clic en **Hecho** para agregar la relación a la entidad y, a continuación, haga clic en **Guardar entidad**.

    > [!div class="mx-imgBorder"] 
    > ![Relación uno a varios](./media/data-platform-cds-newrelationship/onetomany-3.png "Relación uno a varios")

## <a name="add-a-many-to-many-relationship"></a>Agregar una relación de varios a varios
Para agregar una relación de varios a varios, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que desee crear una relación.

1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

2. Haga clic o pulse en una entidad existente o [Cree una nueva entidad](data-platform-create-entity.md)

3. Haga clic en **Relaciones**.

4. Haga clic en la flecha abajo, a la derecha de **Agregar relación**; se le ofrecerá la opción de ambos tipos de relaciones. Haga clic en **Varios a varios**, se abrirá un nuevo panel para que elija la entidad con la que desea crear una relación. Seleccione la entidad en la lista desplegable **Entidad relacionada**.

5. Después de seleccionar una entidad, los nombres para la relación y la entidad de relación aparecerán. Adoptarán de forma predeterminada los nombres de las entidades combinadas, pero puede cambiarlos si es necesario.

    > [!div class="mx-imgBorder"] 
    > ![Relación de varios a varios](./media/data-platform-cds-newrelationship/manytomany-1.png "Relación de varios a varios")

6. Haga clic en **Hecho** para agregar la relación a la entidad y, a continuación, haga clic en **Guardar entidad**.


## <a name="add-advanced-relationship-behavior"></a>Agregar comportamiento de relación avanzado

Mientras crea una relación de uno a varios o de varios a uno, también puede definir comportamientos avanzados.

![Comportamiento avanzado](./media/data-platform-cds-newrelationship/advanced-1.png "Comportamiento avanzado")

Estas opciones también se denominan comportamientos en cascada ya que se despliegan en cascada en la jerarquía de entidades relacionadas. Por ejemplo, podría ser deseable eliminar las pruebas y las tareas relacionadas de un estudiante si este se quita del sistema. Este tipo de comportamiento se llama relación jerárquica.

Además, puede decidir que no desea que las acciones se sitúen en cascada en la jerarquía. Por ejemplo, en la relación de profesor a clase, puede decidir que la entidad secundaria (clase) *no* se debe eliminar cuando se elimina un superior (profesor). Esto se llama relación de referencia.

Cuando modela los datos empresariales mediante la creación de entidades personalizadas o cuando utiliza las entidades existentes del Common Data Model, analice el comportamiento que necesita y las consecuencias para la jerarquía completa de entidades relacionadas y elija entre uno de los siguientes comportamientos estándar:

* **De referencia, Quitar vínculo:** En una relación de referencia entre dos entidades, se puede navegar a registros relacionados, pero las acciones realizadas en una no afectarán a la otra. Por ejemplo, si tiene una relación de uno a varios entre profesores y clases, al eliminar un profesor no se producirá ningún impacto en la clase relacionada.

* **De referencia, restringir eliminación:** En una relación de referencia con restricción de eliminación, se puede navegar a registros relacionados. Las acciones realizadas en el registro primario no se aplicarán al registro secundario, pero el registro primario no se puede eliminar mientras exista el registro secundario. Esto es útil si no desea que los registros secundarios se queden huérfanos. Esto fuerza al usuario a eliminar todos los elementos secundarios antes de eliminar el elemento principal.

    > [!div class="mx-imgBorder"] 
    > ![De referencia, restringir eliminación](./media/data-platform-cds-newrelationship/advanced-3.png "De referencia, restringir eliminación")

* **Jerárquica:** En una relación jerárquica entre dos entidades, cualquier acción realizada en un registro de la entidad principal se realiza también en los registros de la entidad secundaria relacionados con el registro de la entidad principal. Por ejemplo, esto haría que todos registros secundarios se eliminaran cuando eliminara el elemento principal.

* **Personalizado:** En una relación personalizada entre dos entidades, seleccione el comportamiento asociado con un conjunto de acciones posibles. 

    > [!div class="mx-imgBorder"] 
    > ![Comportamiento personalizado](./media/data-platform-cds-newrelationship/advanced-2.png "Comportamiento personalizado")

Para obtener más información sobre valores predeterminados y comportamientos personalizados: [Configurar comportamiento de relaciones entre entidades](entity-relationship-behavior.md).



## <a name="use-a-lookup-field-in-an-app"></a>Usar un campo de búsqueda en una aplicación
Si [crea una aplicación automáticamente](../canvas-apps/data-platform-create-app.md) a partir de una entidad que contiene un campo de búsqueda, ésta aparece como control **Desplegable** que contiene datos del campo **Nombre principal** de la entidad.

## <a name="add-1n-and-nn-relationships-for-canvas-apps"></a>Agregue relaciones de 1:N y de N:N para las aplicaciones del lienzo
Use la función **Relacionar** para vincular dos registros a través de una relación de uno a varios o de varios a varios en Common Data Service. Más información: [Funciones Relacionar y Cancelar la relación en Power Apps](../canvas-apps/functions/function-relate-unrelate.md)

## <a name="next-steps"></a>Pasos siguientes
* [Generar una aplicación mediante una base de datos de Common Data Service](../canvas-apps/data-platform-create-app.md)
* [Crear una aplicación desde cero usando una base de datos de Common Data Service](../canvas-apps/data-platform-create-app-scratch.md)

