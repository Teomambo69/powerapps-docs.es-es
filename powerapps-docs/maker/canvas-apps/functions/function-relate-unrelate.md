---
title: Funciones de relación y desrelación | Microsoft Docs
description: Información de referencia, incluida la sintaxis y un ejemplo, para las funciones relacionar y no relacionar en PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 94400c88740ea93b3966db8a62a461b5616eaeef
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678359"
---
# <a name="relate-and-unrelate-functions-in-powerapps"></a>Funciones de relación y desrelación en PowerApps

Relacionar y desrelacionar registros de dos entidades a través de una relación de uno a varios o de varios a varios.

## <a name="description"></a>Descripción

La función **Relate** vincula dos registros a través de una relación de uno a varios o de varios a varios en Common Data Service. La función no **relacional** invierte el proceso y quita el vínculo.

En el caso de las relaciones uno a varios, la entidad muchos tiene un campo de clave externa que apunta a un registro de la entidad. **Relacionar** establece este campo para que señale a un registro específico de la entidad, mientras que sin **relación** establece este campo en *en blanco*. Si el campo ya está establecido cuando se llama a **Relate** , el vínculo existente se pierde en favor del nuevo vínculo. También puede establecer este campo mediante la función [**patch**](function-patch.md) o un control **[Edit Form](../controls/control-form-detail.md)** . no es necesario usar la función **Relate** .

En el caso de las relaciones de varios a varios, el sistema que vincula los registros mantiene una tabla combinada oculta. No se puede obtener acceso a esta tabla de combinación directamente; solo se puede leer a través de una proyección uno a varios y establecerse a través de las funciones **relacionar** y no **relacionar** . Ninguna entidad relacionada tiene una clave externa.

Los datos de la entidad que especifique en el primer argumento se actualizarán para reflejar el cambio, pero los datos de la entidad que especifique en el segundo argumento no lo serán. Esos datos se deben actualizar manualmente con la función de **[actualización](function-refresh.md)** para mostrar el resultado de la operación.

Estas funciones nunca crean o eliminan un registro. Solo relacionan o desrelacionan dos registros que ya existen.

Estas funciones solo se pueden usar en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

> [!NOTE]
> Estas funciones forman parte de una característica de vista previa y su comportamiento solo está disponible cuando está habilitada la característica **datos relacionales, conjuntos de opciones y otras características nuevas de CDs** . Se trata de una configuración de nivel de aplicación que está habilitada de forma predeterminada para las nuevas aplicaciones. Para encontrar este modificador de características, abra el menú **archivo** , seleccione Configuración de la **aplicación**y, a continuación, seleccione **Configuración avanzada**. Sus comentarios son muy valiosos: díganos lo que piensa en los foros de la [comunidad de Power apps](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To).

## <a name="syntax"></a>Sintaxis

**Relacionar**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* : requerido. Para un registro de *Entity1*, la tabla de registros *Entity2* relacionados con una relación de uno a varios o de varios a varios.
* *Entity2Record* : requerido. Registro *Entity2* que se va a agregar a la relación.

No **relacionar**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* : requerido. Para un registro de *Entity1*, la tabla de registros *Entity2* relacionados con una relación de uno a varios o de varios a varios.
* *Entity2Record* : requerido. Registro *Entity2* que se va a quitar de la relación.

## <a name="examples"></a>Ejemplos

Considere una entidad **Products** con las siguientes relaciones, tal como se ha visualizado en el [visor de entidades del portal de Power apps](../../common-data-service/create-edit-entities-portal.md):

| Nombre para mostrar de relación | Entidad relacionada | Tipo de relación |
| --- | --- |
| Reserva del producto | Movs | Uno a varios |
| Contacto del &harr; del producto | Contacto | Varios a varios |

**Los productos** y las **reservas** se relacionan a través de una relación de uno a varios.  Para relacionar el primer registro de la entidad **reservas** con el primer registro de la entidad **productos** :

`Relate( First( Products ).Reservations, First( Reservations ) )`

Para quitar la relación entre estos registros:

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

En ningún momento se crea o quita un registro, solo se modificó la relación entre los registros.

**Los productos y los** **contactos** se relacionan a través de una relación de varios a varios.  Para relacionar el primer registro de la entidad **Contacts** con el primer registro de la entidad **Products** :

`Relate( First( Products ).Contacts, First( Contacts ) )`

Como las relaciones varios a varios son simétricas, podríamos hacer esto también en la dirección opuesta:

`Relate( First( Contacts ).Products, First( Products ) )`

Para quitar la relación entre estos registros:

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

de

`Unrelate( First( Contacts ).Products, First( Products ) )`

En el siguiente tutorial se realizan exactamente estas operaciones en estas entidades mediante una aplicación con controles de **Galería** y de **cuadro combinado** para seleccionar los registros implicados.

Estos ejemplos dependen de los datos de ejemplo que se instalan en el entorno. [Cree un entorno de prueba que incluya datos de ejemplo](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps) o [agregue datos de ejemplo a un entorno existente](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data).

### <a name="one-to-many"></a>Uno a varios

#### <a name="relate-function"></a>Función **Relate**

En primer lugar, creará una aplicación sencilla para ver y reasignar las reservas asociadas a un producto.

1. Cree una [aplicación de Tablet PC en blanco](../data-platform-create-app-scratch.md).

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.

1. En el panel **datos** , seleccione **Agregar origen de datos** > **Common Data Service** > **productos** > **conectar**.  

    La entidad Products forma parte de los datos de ejemplo cargados anteriormente.

     ![Agregar la entidad Products como origen de datos](media/function-relate-unrelate/products-connect.png)

1. En la pestaña **Insertar** , agregue un control **[Galería](../controls/control-gallery.md)** vertical en blanco.

1. Asegúrese de que el control que acaba de agregar se denomina **Gallery1**y, a continuación, muévalo y cambie su tamaño para rellenar el lado izquierdo de la pantalla.

1. En la pestaña **propiedades** , establezca la propiedad **elementos** de **Gallery1**en **productos** y su **diseño** en **imagen y título**.

    ![Configuración de ProductsGallery](media/function-relate-unrelate/products-gallery.png)

1. En **Gallery1**, asegúrese de que el control **etiqueta** se denomine **Title1**y, a continuación, establezca su propiedad **Text** en **ThisItem.Name**.

    ![Configuración de la etiqueta en Gallery1](media/function-relate-unrelate/products-title.png)

1. Seleccione la pantalla para evitar que se inserte el siguiente elemento en **Gallery1**.  Agregue un segundo control **Galería** vertical en blanco y asegúrese de que se denomina **Gallery2**.

    **Gallery2** mostrará las reservas de cualquier producto que seleccione el usuario en **Gallery1**.

1. Mueva y cambie el tamaño de **Gallery2** para rellenar el cuadrante superior derecho de la pantalla.

1. opta Agregue el control de **etiqueta** azul sobre **Gallery2**, como se muestra en el gráfico siguiente.

1. En la barra de fórmulas, establezca la propiedad **Items** de **Gallery2** en **Gallery1. Selected. reservas**.

    ![Configurar elementos de Gallery2](media/function-relate-unrelate/reservations-gallery.png)

1. En el panel Propiedades, establezca **diseño** de **Gallery2**en **título**.

    ![Configuración del diseño de Gallery2](media/function-relate-unrelate/reservations-gallery-right.png)

1. En **Gallery2**, agregue un control de **[cuadro combinado](../controls/control-combo-box.md)** , asegúrese de que se llama **ComboBox1**y, a continuación, muévalo y cambie su tamaño para evitar que se bloqueen los demás controles de **Gallery2**.

1. En la pestaña **propiedades** , establezca la propiedad **elementos** de **ComboBox1**en **productos**.

    ![Establecer la propiedad items en Products](media/function-relate-unrelate/reservations-combo-right.png)

1. Desplácese hacia abajo en la pestaña **propiedades** y establezca la propiedad **Permitir selección múltiple** de **ComboBox1**en **OFF**.

    ![Establecer permitir selección múltiple en desactivado](media/function-relate-unrelate/reservations-singleselect-right.png)

1. En la barra de fórmulas, establezca la propiedad **DefaultSelectedItems** de **ComboBox1**en **ThisItem. ' Product reservation '** .

    ![Establecer DefaultSelectedItems para ReserveCombo](media/function-relate-unrelate/reservations-combo.png)

1. En **Gallery2**, establezca la propiedad **alseleccionar** de **NextArrow2**en esta fórmula:

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    Cuando el usuario selecciona este icono, la reserva actual cambia al producto que el usuario seleccionó en **ComboBox1**.

    ![Configuración de NextArrow2](media/function-relate-unrelate/reservations-relate.png)

1. Presione F5 para probar la aplicación en modo de vista previa.

Con esta aplicación, el usuario puede trasladar una reserva de un producto a otro. En el caso de una reserva de un producto, el usuario puede seleccionar un producto diferente en **ComboBox1** y seleccionar **NextArrow2** para cambiar esa reserva.

![Demostración de la función relacionada en una aplicación de uno a varios](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>No **Relacionate** (función)

Llegados a este punto, puede trasladar la relación de un registro a otro, pero no puede quitar la relación por completo. Puede usar la función no **relacionar** para desconectar un registro de reserva de cualquier producto.

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.

1. En el panel **datos** , seleccione **Agregar origen de datos** > **Common Data Service** > **reservas** > **conectar**.

1. En **Gallery2**, establezca la fórmula **alseleccionar** para **NextArrow2** en esta fórmula:

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![Configurar icono derecho](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. Copie **Gallery2** en el portapapeles; para ello, selecciónelo y presione Ctrl + C.

1. Pegue un duplicado de **Gallery2** en la misma pantalla presionando Ctrl-V y, a continuación, muévalo al cuadrante inferior derecho de la pantalla.

1. opta Si agregó una etiqueta por encima de **Gallery2**, repita los dos pasos anteriores para esa etiqueta.

1. Asegúrese de que el duplicado de **Gallery2** se denomine **Gallery2_1**y, a continuación, establezca la propiedad **elementos** en esta fórmula:

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    Aparece una advertencia de delegación, pero no importa la pequeña cantidad de datos en este ejemplo.

    ![Establezca la propiedad items de Gallery2_1](media/function-relate-unrelate/reservations-lost.png)

Con estos cambios, los usuarios pueden borrar la selección en **ComboBox1** para un contacto si esa persona no ha reservado un producto. Los contactos que no han reservado un producto aparecen en **Gallery2_1** en los que los usuarios pueden asignar cada contacto a un producto.

   ![Demostración de funciones de relación y desrelación en una aplicación de uno a varios](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>Varios a varios

#### <a name="create-a-many-to-many-relationship"></a>Crear una relación de varios a varios

Los datos de ejemplo no incluyen una relación de varios a varios, pero creará uno entre la entidad productos y la entidad contactos. Los usuarios pueden relacionar cada producto con más de un contacto y cada contacto con más de un producto.

1. En [esta página](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **datos** en la barra de navegación izquierda y, a continuación, seleccione **entidades**.

    ![Abrir lista de entidades](media/function-relate-unrelate/entity-list.png)

1. Cambie el filtro de entidad para incluir todas las entidades.

    De forma predeterminada, las entidades de ejemplo no aparecen.

    ![Quitar filtro de entidad](media/function-relate-unrelate/entity-all.png)

1. Desplácese hacia abajo, abra la entidad **Product** y seleccione **Relationships (relaciones**).

    ![Pestaña relaciones de la entidad Product](media/function-relate-unrelate/entity-relationships.png)

1. Seleccione **Agregar relación** > **varios a varios**.

    ![Agregar relación de varios a varios](media/function-relate-unrelate/entity-manytomany.png)

1. Seleccione la entidad **contacto** para la relación.

    ![Seleccionar la entidad contacto](media/function-relate-unrelate/entity-contact.png)

1. Seleccione **listo** > **Guardar entidad**.

    ![Lista de relaciones para la entidad Products](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>Relacionar y desrelacionar contactos con uno o varios productos

Creará otra aplicación similar a la que creó anteriormente en este tema, pero la nueva aplicación proporcionará una relación de varios a varios. Cada contacto podrá reservar varios productos en lugar de uno solo.

1. En una aplicación en blanco para tabletas, cree **Gallery1** como se describe en el [primer procedimiento](#one-to-many) de este tema.

1. Agregue otro control **Galería** vertical en blanco, asegúrese de que se llama **Gallery2**y, a continuación, muévalo a la esquina superior derecha de la pantalla.

    Más adelante en este tema, agregará un control de **cuadro combinado** en **Gallery2**.

1. En la barra de fórmulas, establezca la propiedad **elementos** de **Gallery2**en **Gallery1. Selected. contacts**.

    ![Configuración de ContactsGallery](media/function-relate-unrelate/contacts-gallery.png)

1. En la pestaña **propiedades** , establezca **diseño** en **imagen y título**.

    ![Configuración de ContactsGallery](media/function-relate-unrelate/contacts-gallery-right.png)

1. En **Gallery2**, asegúrese de que el control **etiqueta** se denomine **Title2**y, a continuación, establezca su propiedad **Text** en **ThisItem. ' Full Name '** .

    No aparecerá ningún texto en ese control hasta que finalice este procedimiento y asigne un contacto a un producto.

    ![Mostrar nombre de contacto](media/function-relate-unrelate/contacts-title.png)

1. Elimine **NextArrow2**, inserte un icono de **cancelación** y asegúrese de que se llama **icon1**.

1. Establezca la propiedad **alseleccionar** del icono **Cancelar** en esta fórmula: 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![Configurar el icono de cancelación](media/function-relate-unrelate/contacts-unrelate.png)

1. En la pestaña **Vista**, seleccione **Orígenes de datos**.

1. En el panel **datos** , seleccione **Agregar origen de datos** > **Common Data Service** > **contactos** > **conectar**.

1. En **Gallery2**, agregue un control de **cuadro combinado** , asegúrese de que se llama **ComboBox1**y, a continuación, establezca su propiedad **Items** en **Contacts**.

    ![Configurar la propiedad elementos del cuadro combinado](media/function-relate-unrelate/contacts-combo.png)

1. En la pestaña **propiedades** , establezca **Permitir selección múltiple** en **desactivado**.

    ![Configurar la propiedad de diseño de cuadro combinado](media/function-relate-unrelate/contacts-combo-right.png)

1. Inserte un icono **Agregar** y establezca su propiedad **alseleccionar** en esta fórmula: 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![Configurar agregar icono](media/function-relate-unrelate/contacts-relate.png)

Con esta aplicación, los usuarios ahora pueden relacionar libremente y desrelacionar un conjunto de contactos con cada producto.

- Para agregar un contacto a un producto, seleccione el contacto en el cuadro combinado de la parte inferior de la pantalla y, a continuación, seleccione el icono **Agregar** .
- Para quitar un contacto de un producto, seleccione el icono **Cancelar** del contacto.

    A diferencia de uno a varios, una relación de varios a varios permite a los usuarios asociar el mismo contacto con varios productos.

![Demostración de funciones de relación y desrelación en una aplicación de varios a varios](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>En orden inverso: relacionar y desrelacionar productos con varios contactos

Las relaciones de varios a varios son simétricas. Puede extender el ejemplo para agregar productos a un contacto y después alternar entre las dos pantallas para mostrar cómo aparece la relación desde cualquier dirección.

1. Establezca la propiedad **divisible** de **Screen1** en **Actualizar (productos)** .

    Cuando se actualiza una relación de uno a varios o de varios a varios, solo se actualizan los datos de la entidad del primer argumento de la llamada **relacionada** o no **relacionada** . La segunda debe actualizarse manualmente si desea cambiar entre las pantallas de esta aplicación.

    ![Establecer la propiedad divisible en la función Refresh](media/function-relate-unrelate/contacts-refresh.png)

1. **Screen1**duplicado.

    El duplicado se denominará **Screen1_1** y formará la base para examinar las relaciones del lado de los contactos.

    ![Duplicar una pantalla](media/function-relate-unrelate/contacts-duplicate.png)

1. Para crear la vista inversa, cambie estas fórmulas en los controles de **Screen1_1**:

    - Screen1_1. divisible = `Refresh( Contacts )`
    - Gallery1_1. Items = `Contacts`
    - Title1_1. Text = `ThisItem.'Full Name'`
    - Label1_1. Text = `"Selected Contact Products"`
    - Gallery2_1. Items = `Gallery1_1.Selected.Products`
    - Title2_1. Text = `ThisItem.Name`
    - Icon1_1. Select = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1. Items = `Products`
    - Icon2_1. Select = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    El resultado tendrá un aspecto muy similar al de la pantalla anterior, pero se incluye en la relación del lado de los **contactos** .

    ![Mostrar relación de varios a varios empezando por contactos](media/function-relate-unrelate/reverse-screen.png)

1. Inserte un icono **de flechas hacia arriba** y establezca su propiedad **Alseleccionar** en **Navigate (Screen1, None)** .  Haga lo mismo en **Screen1** con la fórmula **navigate (Screen1_1, None)** .

    ![Agregar navegación entre pantallas](media/function-relate-unrelate/reverse-navigate.png)

Con esta nueva pantalla, los usuarios pueden agregar un contacto a un producto y, a continuación, pasar a una vista de contactos y ver el producto asociado. Las relaciones son simétricas y se comparten entre las dos pantallas.

![Demostrar la relación de varios a varios desde cualquier lado](media/function-relate-unrelate/contacts-reverse.gif)
