---
title: Relacionar y Anular relación con las funciones | Microsoft Docs
description: Hacer referencia a información, incluida la sintaxis y un ejemplo, para el relacionar y Anular relación con las funciones de PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4b2c6b9518e987ef17f2ff2b50987568c8a0b69f
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61527523"
---
# <a name="relate-and-unrelate-functions-in-powerapps"></a>Relacionar y Anular relación con las funciones de PowerApps

Relacionar y Anular relación con los registros de dos entidades a través de una relación uno a varios o varios a varios.

## <a name="description"></a>Descripción

El **relacionar** función vincula dos registros a través de una relación uno a varios o varios a varios en Common Data Service. El **Unrelate** función invierte el proceso y quita el vínculo.

Para las relaciones uno a varios, la entidad muchos tiene un campo de clave externa que apunta a un registro de una entidad. **Relacionar** establece este campo para que apunte a un registro específico de una entidad, mientras que **Unrelate** establece este campo en *en blanco*. Si el campo ya se establece cuando **relacionar** es llama, el vínculo existente se pierde en favor de nuevo el vínculo. También puede establecer este campo con el [ **Patch** ](function-patch.md) función o un **[Editar formulario](../controls/control-form-detail.md)** control; que no necesita usar el **relacionar**  función.

Para las relaciones de varios a varios, el sistema que vincula los registros mantiene una tabla de combinación oculto. No se puede obtener acceso a esta tabla de combinación directamente; se puede leer sólo a través de una proyección uno a varios y se establece a través del **relacionar** y **Unrelate** funciones. Ninguna entidad relacionada con una clave externa.

Los datos de la entidad que especifique en el primer argumento se actualizará para reflejar el cambio, pero no los datos de la entidad que especifique en el segundo argumento. Que los datos deben ser manualmente actualiza con el **[actualizar](function-refresh.md)** función para mostrar el resultado de la operación.

Estas funciones nunca crean o eliminación un registro. Solo se relacionan o Anular relación con dos registros que ya existen.

Puede usar estas funciones solo en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

> [!NOTE]
> Estas funciones son parte de una característica de versión preliminar y su comportamiento solo está disponible cuando el **datos relacionales, conjuntos de opciones y otras características nuevas para CDS** característica está habilitada. Se trata de una configuración de nivel de aplicación que está habilitada de forma predeterminada para las nuevas aplicaciones. Para buscar este modificador de característica, abra el **archivo** menú, seleccione **configuración de la aplicación**y, a continuación, seleccione **configuración avanzada**. Sus comentarios nos sirven mucho: denos su opinión en los [foros de la comunidad de PowerApps](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To).

## <a name="syntax"></a>Sintaxis

**Relate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* : requerido. Para un registro de *Entity1*, la tabla de *Entity2* registros relacionados mediante una relación uno a varios o varios a varios.
* *Entity2Record* : requerido. El *Entity2* registro va a agregar a la relación.

**Unrelate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* : requerido. Para un registro de *Entity1*, la tabla de *Entity2* registros relacionados mediante una relación uno a varios o varios a varios.
* *Entity2Record* : requerido. El *Entity2* registro para quitar de la relación.

## <a name="examples"></a>Ejemplos

Considere la posibilidad de un **productos** entidad con las siguientes relaciones tal como se muestra en el [Visor de entidad del portal de PowerApps](../../common-data-service/create-edit-entities-portal.md):

| Nombre para mostrar relación | Entidad relacionada | Tipo de relación |
| --- | --- |
| Reserva de producto | Reserva | Uno a varios |
| Producto &harr; póngase en contacto con | Contacto | Varios a varios |

**Productos** y **reservas** se relacionan a través de uno a varios relación.  Para relacionar el primer registro de la **reservas** entidad con el primer registro de la **productos** entidad:

`Relate( First( Products ).Reservations, First( Reservations ) )`

Para quitar la relación entre estos registros:

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

En ningún momento creamos o remove o un registro, solo la relación entre los registros se ha modificado.

**Productos** y **contactos** se relacionan a través de varios a varios relación.  Para relacionar el primer registro de la **contactos** entidad con el primer registro de la **productos** entidad:

`Relate( First( Products ).Contacts, First( Contacts ) )`

Como muchos a muchos relaciones son simétricas, podríamos también haber hecho esto en la dirección opuesta:

`Relate( First( Contacts ).Products, First( Products ) )`

Para quitar la relación entre estos registros:

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

o:

`Unrelate( First( Contacts ).Products, First( Products ) )`

El recorrido a través de la que se indica a continuación las hace exactamente en estas entidades mediante una aplicación con **galería** y **cuadro combinado** controles para seleccionar los registros implicados.

Estos ejemplos dependen de los datos de ejemplo que se instala en su entorno. Cualquier [crear un entorno de prueba incluye datos de ejemplo](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps) o [agregar datos de ejemplo en un entorno existente](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data).

### <a name="one-to-many"></a>Uno a varios

#### <a name="relate-function"></a>**Relacionar** (función)

Primero vamos a crear una aplicación sencilla para ver y reasignar las reservas de direcciones que están asociados con un producto.

1. Crear un [aplicación de tableta desde cero](../data-platform-create-app-scratch.md).

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.

1. En el **datos** panel, seleccione **agregar origen de datos** > **Common Data Service** > **productos**  >  **Conectar**.  

    La entidad de productos es parte de los datos de ejemplo cargados anteriormente.

     ![Agregar la entidad de productos como un origen de datos](media/function-relate-unrelate/products-connect.png)

1. En el **insertar** pestaña, agregue una galería vertical en blanco **[galería](../controls/control-gallery.md)** control.

1. Asegúrese de que el control que acaba de agregar se denomina **Gallery1**y, a continuación, mover y cambiar su tamaño para rellenar el lado izquierdo de la pantalla.

1. En el **propiedades** pestaña, establezca **Gallery1**del **elementos** propiedad **productos** y su **diseño** a **Imagen y título**.

    ![Configurar ProductsGallery](media/function-relate-unrelate/products-gallery.png)

1. En **Gallery1**, asegúrese de que el **etiqueta** control se denomina **Title1**y, a continuación, establezca su **texto** propiedad  **ThisItem.Name**.

    ![Configuración de la etiqueta en Gallery1](media/function-relate-unrelate/products-title.png)

1. Seleccione la pantalla para evitar la inserción en el siguiente elemento en **Gallery1**.  Agregar una segunda vertical en blanco **galería** controlar y asegurarse de que se denomina **Gallery2**.

    **Gallery2** mostrará las reservas de cualquier producto que el usuario selecciona en **Gallery1**.

1. Mover y cambiar el tamaño de **Gallery2** para rellenar el cuadrante superior derecho de la pantalla.

1. (opcional) Agregar el azul **etiqueta** control anterior **Gallery2**, tal y como se muestra en el gráfico siguiente.

1. En la barra de fórmulas, establezca el **elementos** propiedad de **Gallery2** a **Gallery1.Selected.Reservations**.

    ![Configurar elementos Gallery2](media/function-relate-unrelate/reservations-gallery.png)

1. En el panel Propiedades, establezca **Gallery2**del **diseño** a **título**.

    ![Configurar Gallery2 diseño](media/function-relate-unrelate/reservations-gallery-right.png)

1. En **Gallery2**, agregue un **[cuadro combinado](../controls/control-combo-box.md)** controlar, asegúrese de que se denomina **ComboBox1**y, a continuación, mover y cambiar su tamaño para evitar el bloqueo de la otros controles en **Gallery2**.

1. En el **propiedades** pestaña, establezca **ComboBox1**del **elementos** propiedad **productos**.

    ![Establezca la propiedad elementos en productos](media/function-relate-unrelate/reservations-combo-right.png)

1. Desplácese hacia abajo en la **propiedades** pestaña y establezca **ComboBox1**del **permitir la selección múltiple** propiedad **desactivar**.

    ![Conjunto de permitir la selección múltiple en desactivado](media/function-relate-unrelate/reservations-singleselect-right.png)

1. En la barra de fórmulas, establezca **ComboBox1**del **DefaultSelectedItems** propiedad **ThisItem. 'Reserva de producto'**.

    ![Establecer DefaultSelectedItems para ReserveCombo](media/function-relate-unrelate/reservations-combo.png)

1. En **Gallery2**, establezca **NextArrow2**del **OnSelect** propiedad en esta fórmula:

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    Cuando el usuario selecciona este icono, cambia la reserva actual para el producto que el usuario seleccionó en **ComboBox1**.

    ![Configurar NextArrow2](media/function-relate-unrelate/reservations-relate.png)

1. Presione F5 para probar la aplicación en modo de vista previa.

Con esta aplicación, el usuario puede mover una reserva de un producto a otro. Para una reserva en un solo producto, el usuario puede seleccionar un producto diferente en **ComboBox1** y, a continuación, seleccione **NextArrow2** para cambiar esa reserva.

![Demostrar la función de relacionar de aplicación de uno a varios](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>**Anular la relación** (función)

En este momento, puede mover la relación de un registro a otro, pero no se puede quitar la relación por completo. Puede usar el **Unrelate** función para desconectarse de un registro de reserva de cualquier producto.

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.

1. En el **datos** panel, seleccione **agregar origen de datos** > **Common Data Service** > **reservas**  >  **Conectar**.

1. En **Gallery2**, establezca el **Alseleccionar** fórmulas para **NextArrow2** en esta fórmula:

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![Configurar icono adecuado](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. Copia **Gallery2** en el Portapapeles, selecciónela y, a continuación, presione Ctrl-C.

1. Pegue un duplicado de **Gallery2** a la misma pantalla presionando Ctrl-V y, a continuación, muévalo al cuadrante inferior derecha de la pantalla.

1. (opcional) Si agrega una etiqueta anterior **Gallery2**, repita los dos pasos anteriores para esa etiqueta.

1. Asegúrese de que el duplicado de **Gallery2** se denomina **Gallery2_1**y, a continuación, establezca su **elementos** propiedad en esta fórmula:

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    Aparece una advertencia de delegación, pero no importa con la cantidad pequeña de datos en este ejemplo.

    ![Establezca la propiedad Items de Gallery2_1](media/function-relate-unrelate/reservations-lost.png)

Con estos cambios, los usuarios pueden borrar la selección en **ComboBox1** para un contacto si esa persona no ha reservado un producto. Contactos que no ha reservado un producto aparecen en **Gallery2_1** donde los usuarios pueden asignar a cada contacto a un producto.

   ![Demostrar relacionar y Anular relación con las funciones de aplicación de uno a varios](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>Varios a varios

#### <a name="create-a-many-to-many-relationship"></a>Crear una relación varios a varios

Los datos de ejemplo no incluyen una relación varios a varios, pero creará uno entre la entidad de productos y la entidad de contactos. Los usuarios pueden relacionar cada producto para cada contacto a más de un producto y más de un contacto.

1. Desde [esta página](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **datos** en el panel de navegación izquierdo de la barra y, a continuación, seleccione **entidades**.

    ![Apertura de la lista de entidades](media/function-relate-unrelate/entity-list.png)

1. Cambie el filtro de la entidad para incluir todas las entidades.

    De forma predeterminada, no aparecen las entidades de ejemplo.

    ![Quitar filtro de entidad](media/function-relate-unrelate/entity-all.png)

1. Desplácese hacia abajo, abra el **producto** entidad y seleccione **relaciones**.

    ![Ficha relaciones para la entidad producto](media/function-relate-unrelate/entity-relationships.png)

1. Seleccione **agregar relación** > **-to-many**.

    ![Agregar relación de varios a varios](media/function-relate-unrelate/entity-manytomany.png)

1. Seleccione el **póngase en contacto con** entidad para la relación.

    ![Seleccione la entidad Contact](media/function-relate-unrelate/entity-contact.png)

1. Seleccione **realiza** > **guardar entidad**.

    ![Lista de relaciones de entidad de productos](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>Relacionar y Anular relación con los contactos con uno o varios productos

Podrá crear otra aplicación que es similar a la que creó anteriormente en este tema, pero la nueva aplicación ofrecerá una relación varios a varios. Cada contacto podrán reservar varios productos en lugar de solo uno.

1. En una aplicación en blanco para tabletas, crear **Gallery1** como el [primer procedimiento](#one-to-many) en este tema se describe.

1. Agregar otra vertical en blanco **galería** controlar, asegúrese de que se denomina **Gallery2**, y, a continuación, muévalo a la esquina superior derecha de la pantalla.

    Más adelante en este tema, agregará un **cuadro combinado** controlar bajo **Gallery2**.

1. En la barra de fórmulas, establezca **Gallery2**del **elementos** propiedad **Gallery1.Selected.Contacts**.

    ![Configurar ContactsGallery](media/function-relate-unrelate/contacts-gallery.png)

1. En el **propiedades** pestaña, establezca **diseño** a **imagen y título**.

    ![Configurar ContactsGallery](media/function-relate-unrelate/contacts-gallery-right.png)

1. En **Gallery2**, asegúrese de que el **etiqueta** control se denomina **Title2**y, a continuación, establezca su **texto** propiedad  **ThisItem. "Full Name"**.

    No hay texto aparecerá en ese control hasta que finalice este procedimiento y asignar un contacto a un producto.

    ![Mostrar el nombre de contacto](media/function-relate-unrelate/contacts-title.png)

1. Eliminar **NextArrow2**, inserte un **cancelar** icono y asegúrese de que se denomina **icon1**.

1. Establecer el **cancelar** del icono **OnSelect** propiedad en esta fórmula: 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![Configurar icono Cancelar](media/function-relate-unrelate/contacts-unrelate.png)

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.

1. En el **datos** panel, seleccione **agregar origen de datos** > **Common Data Service** > **contactos**  >  **Conectar**.

1. En **Gallery2**, agregue un **cuadro combinado** controlar, asegúrese de que se denomina **ComboBox1**y, a continuación, establezca su **elementos** propiedad **Contactos**.

    ![Configurar la propiedad de los elementos del cuadro combinado](media/function-relate-unrelate/contacts-combo.png)

1. En el **propiedades** pestaña, establezca **permitir la selección múltiple** a **desactivar**.

    ![Configurar la propiedad de diseño del cuadro combinado](media/function-relate-unrelate/contacts-combo-right.png)

1. Insertar un **agregar** icono y establezca su **OnSelect** propiedad en esta fórmula: 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![Configurar icono Agregar](media/function-relate-unrelate/contacts-relate.png)

Con esta aplicación, los usuarios pueden ahora libremente relacionar y Anular relación con un conjunto de contactos para cada producto.

- Para agregar un contacto a un producto, seleccione el contacto en el cuadro combinado en la parte inferior de la pantalla y, a continuación, seleccione el **agregar** icono.
- Para quitar un contacto de un producto, seleccione el **cancelar** icono de dicho contacto.

    A diferencia de uno a varios, una relación muchos a muchos permite a los usuarios asociar el mismo contacto con varios productos.

![Demostrar relacionar y Anular relación con las funciones de aplicación de varios a varios](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>En orden inverso: relacionar y Anular relación con los productos con varios contactos

Relaciones varios a varios son simétricas. Puede ampliar el ejemplo para agregar productos a un contacto y, a continuación, alternar entre las dos pantallas para mostrar cómo aparece la relación desde cualquier dirección.

1. Establecer el **Alestarvisible** propiedad de **Screen1** a **actualizar (productos)**.

    Cuando se actualiza una relación uno a varios o varios a varios, sólo los datos de la primera entidad de argumento de la **relacionar** o **Unrelate** se actualiza la llamada. El segundo debe actualizarse manualmente si desea alternar entre las pantallas de la aplicación.

    ![Establezca la propiedad OnVisible en función de actualización](media/function-relate-unrelate/contacts-refresh.png)

1. Duplicar **Screen1**.

    El duplicado se denominará **Screen1_1** y forman la base para mirar las relaciones en el lado de contactos.

    ![Duplique una pantalla](media/function-relate-unrelate/contacts-duplicate.png)

1. Para crear la vista inversa, cambiar estas fórmulas en los controles de **Screen1_1**:

    - Screen1_1.OnVisible = `Refresh( Contacts )`
    - Gallery1_1.Items = `Contacts`
    - Title1_1.Text = `ThisItem.'Full Name'`
    - Label1_1.Text = `"Selected Contact Products"`
    - Gallery2_1.Items = `Gallery1_1.Selected.Products`
    - Title2_1.Text = `ThisItem.Name`
    - Icon1_1.onselect = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1.Items = `Products`
    - Icon2_1.OnSelect = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    El resultado tendrá un aspecto muy similar a la pantalla anterior, pero tiene la relación desde la **contactos** lado.

    ![Mostrar relaciones de varios a varios a partir de contactos](media/function-relate-unrelate/reverse-screen.png)

1. Insertar un **flechas abajo hasta** icono y el conjunto su **OnSelect** propiedad a **navegar (Screen1, None)**.  Lo mismo en **Screen1** con la fórmula **Navigate (Screen1_1, None)**.

    ![Agregar navegación entre pantallas](media/function-relate-unrelate/reverse-navigate.png)

Con esta nueva pantalla, los usuarios pueden agregar un contacto a un producto y, a continuación, cambie a una vista de contactos y ver el producto asociado. Las relaciones son simétricas y compartida entre las dos pantallas.

![Demostrar la relación de varios a varios desde ambos lados](media/function-relate-unrelate/contacts-reverse.gif)
