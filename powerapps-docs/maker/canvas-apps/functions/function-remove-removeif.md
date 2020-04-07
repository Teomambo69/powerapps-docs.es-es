---
title: Funciones Quitar y RemoveIf | Microsoft Docs
description: Información de referencia de las funciones Remove y RemoveIf de Power Apps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/02/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bddce14842d111757859b836c0137b35111805d1
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759829"
---
# <a name="remove-and-removeif-functions-in-power-apps"></a>Funciones Remove y RemoveIf en Power apps
Quita [registros](../working-with-tables.md#records) de un [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción
### <a name="remove-function"></a>Función Remove
Use la función **Remove** para quitar un registro o registros específicos de un origen de datos.  

Para las [colecciones](../working-with-data-sources.md#collections), tiene que coincidir con todo el registro. Puede usar el argumento **Todo** para quitar todas las copias de un registro; en caso contrario, se quita solo una copia del registro.

### <a name="removeif-function"></a>Función RemoveIf
Use la función **RemoveIf** para quitar un registro o registros en función de una condición o un conjunto de condiciones. Cada condición puede ser cualquier fórmula que da como resultado **true** o **false** y puede hacer referencia a [columnas](../working-with-tables.md#columns) del origen de datos por su nombre. Cada condición se evalúa individualmente para cada registro, y si todas las condiciones se evalúan como **true** se elimina el registro.

**Remove** y **RemoveIf** devuelven el origen de datos modificado como una [tabla](../working-with-tables.md). Puede usar ambas funciones únicamente en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

También puede usar la función **[Clear](function-clear-collect-clearcollect.md)** para eliminar registros en un origen de datos.

### <a name="delegation"></a>Delegación
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Sintaxis
**Remove**( *DataSource*, *Record1* [, *Record2*, ... ] [, **All** ] )

* *DataSource*: requerido. El origen de datos que contiene el registro o los registros que desea quitar.
* *Registro(s)* : requerido. El registro o los registros que se van a quitar.
* **Todo**: opcional. En una colección, el mismo registro puede aparecer más de una vez.  Puede agregar el argumento **Todo** para quitar todas las copias del registro.

**Remove**( *DataSource*, *Table* [, **All** ] )

* *DataSource*: requerido. El origen de datos que contiene los registros que desea quitar.
* *Table*: requerido. Tabla de registros que se van a quitar.
* **Todo**: opcional. En una colección, el mismo registro puede aparecer más de una vez.  Puede agregar el argumento **Todo** para quitar todas las copias del registro.

**RemoveIf**( *DataSource*, *Condición* [,...])

* *DataSource*: requerido. El origen de datos que contiene el registro o los registros que desea quitar.
* *Condition(s)* : requerido. Una fórmula que se evalúa como **true** para el registro o los registros que se van a quitar.  Puede usar nombres de columna de *DataSource* en la fórmula.  Si especifica varias *Condiciones*, todas se deben evaluar como **true** para el registro o registros que va a quitar.

## <a name="examples---single-formulas"></a>Ejemplos: fórmulas únicas

En estos ejemplos, va a quitar un registro o registros de un origen de datos que se denomina **IceCream** y que comienza con los datos en esta tabla:

![](media/function-remove-removeif/icecream.png)

#### <a name="create-a-collection-with-sample-records"></a>Crear una colección con registros de ejemplo

Para crear una colección con estos datos:

1. Inserte un control de [**botón**](../controls/control-button.md) .
1. Establezca la propiedad **alseleccionar** del control de botón en la fórmula siguiente:

    ```powerapps-dot
    ClearCollect( IceCream,
                  { ID: 1, Flavor: "Chocolate",  Quantity: 100 },
                  { ID: 2, Flavor: "Vanilla",    Quantity: 200 },
                  { ID: 3, Flavor: "Strawberry", Quantity: 300 }
    )
    ```
1. Seleccione el botón [mientras mantiene presionada la tecla Alt](../keyboard-shortcuts.md#alternate-behavior):


#### <a name="remove-sample-records-from-collection-using-a-formula"></a>Quitar registros de ejemplo de la colección mediante una fórmula

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) )** |Quita el registro **Chocolate** del origen de datos. |<style>IMG {Max-width: None}</style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;) )** |Quita los dos registros del origen de datos. |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **RemoveIf (&nbsp;IceCream, Cantidad&nbsp;>&nbsp;150)** |Quita los registros que tienen una **Cantidad** superior a **150**. |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **RemoveIf(&nbsp;IceCream, Cantidad&nbsp;>&nbsp;150, Left(&nbsp;Flavor,&nbsp;1&nbsp;) = "S" )** |Quita los registros que tienen una **Cantidad** superior a 150 y cuyo valor **Flavor** empieza con **S**. |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>El origen de datos **IceCream** se ha modificado. |
| **RemoveIf (&nbsp;IceCream, true)** |Quita todos los registros del origen de datos. |![](media/function-remove-removeif/icecream-empty.png)<br><br>El origen de datos **IceCream** se ha modificado. |

## <a name="examples---remove-button-outside-a-gallery"></a>Ejemplos: botón Quitar fuera de una galería

En este ejemplo, usará un [control **Galería** ](../controls/control-gallery.md) para mostrar los registros de una tabla. Y, a continuación, utilice la función **Remove** para quitar un elemento de forma selectiva.  

### <a name="prepare-for-sample-data"></a>Preparar los datos de ejemplo

En este ejemplo se usa la entidad **Contacts** en Common Data Service disponible con las *aplicaciones y los datos de ejemplo*. Puede implementar *aplicaciones de ejemplo y datos* al [crear un entorno](https://docs.microsoft.com/power-platform/admin/create-environment#create-an-environment-with-a-database). En su lugar, también puede usar cualquier otro origen de datos.

### <a name="remove-button-outside-a-gallery"></a>Botón Quitar fuera de una galería

En este ejemplo, quitará un elemento mediante un *botón* que está fuera de la galería.

1. Cree una [nueva aplicación de lienzo en blanco](../data-platform-create-app-scratch.md) con un diseño de teléfono.

    ![Una aplicación de lienzo en blanco con el diseño del teléfono](media/function-remove-removeif/gallery-new.png)

1. Seleccione la **inserción** en el panel izquierdo.

1. Seleccione **Galería vertical**. <br>
    Se agrega un control **Galería** a la pantalla.

    ![Usar el panel de herramientas insertar para agregar un control Galería vertical](media/function-remove-removeif/gallery-add.png)

1. Se le pedirá que seleccione un origen de datos en el que puede seleccionar un origen de datos de los orígenes de datos disponibles. <br>
    Por ejemplo, seleccione la entidad **contactos** para usar *datos de ejemplo*:  

    ![Selección de la entidad contactos que se va a mostrar en la galería](media/function-remove-removeif/gallery-datasource.png)

    La galería muestra los elementos de esta entidad: 

    ![Galería agregada que muestra la entidad contactos](media/function-remove-removeif/gallery-data.png)

1. Inserte un control de [**botón**](../controls/control-button.md) del panel izquierdo:
    
    ![Usar el panel de herramientas insertar para agregar un control de botón](media/function-remove-removeif/gallery-addbutton.png)

1. Mueva el botón Agregar debajo de los elementos de la Galería:

    ![Botón de movimiento](media/function-remove-removeif/move-button-down.png)

1. Actualice la propiedad texto del botón para *quitar el registro*. También puede usar el texto que prefiera:

    ![Botón Cambiar nombre](media/function-remove-removeif/button-text.png)

1. Establezca la propiedad **alseleccionar** para este control de botón en la fórmula siguiente:

    ```powerapps-dot
    Remove( Contacts, Gallery1.Selected )
    ```

    ![Establecer la propiedad alseleccionar del control Button](media/function-remove-removeif/gallery-button-onselect.png)

    El control Galería hace que el registro seleccionado actualmente esté disponible mediante la propiedad **seleccionada** . **Quitar** función hace referencia a este registro seleccionado para quitarlo.

1. Obtenga una vista previa de la aplicación con el botón *reproducir* en la parte superior derecha o presione *F5* en el teclado:

    ![Aplicación de vista previa](media/function-remove-removeif/preview-app.png)

1. Seleccione un registro para quitarlo, como el registro de *Nancy*en este ejemplo:

    ![Seleccionar un registro](media/function-remove-removeif/select-nancy-record.png)

1. Seleccione **quitar registro**:

    ![Galería de contactos, ahora sin el registro de Nancy que se ha quitado](media/function-remove-removeif/gallery-activatebutton.png)

    Al seleccionar el botón se quita el registro seleccionado (en este ejemplo, el registro de Nancy).

1. Cierre la vista previa de la aplicación.

    > [!TIP]
    > También puede usar un comportamiento alternativo con la [*tecla Alt*](../keyboard-shortcuts.md#alternate-behavior) en lugar de usar la vista previa de la aplicación con el botón *reproducir* o *F5*.

## <a name="examples---trash-can-icon-inside-a-gallery"></a>Ejemplos: el icono de la papelera se encuentra dentro de una galería

En este ejemplo, quitará un elemento mediante un *icono* colocado dentro de la galería.

### <a name="create-a-collection-with-sample-data"></a>Crear una colección con datos de ejemplo

Si ya ha [preparado datos de ejemplo](#prepare-for-sample-data), omita este paso y vaya a la [papelera icono dentro de una galería](#trash-can-icon-inside-a-gallery).

1. Agregue un control [**botón**](../controls/control-button.md) a la pantalla.
1. Establezca la propiedad **AlSeleccionar** en la fórmula siguiente:

    ```powerapps-dot
    ClearCollect( SampleContacts, 
          { 'Full Name': "Yvonne McKay (sample)",      'Primary Email': "someone_a@example.com" },
          { 'Full Name': "Susanna Stubberod (sample)", 'Primary Email': "someone_b@example.com" },
          { 'Full Name': "Nancy Anderson (sample)",    'Primary Email': "someone_c@example.com" },
          { 'Full Name': "Maria Campbell (sample)",    'Primary Email': "someone_d@example.com" },
          { 'Full Name': "Robert Lyon (sample)",       'Primary Email': "someone_e@example.com" },
          { 'Full Name': "Paul Cannon (sample)",       'Primary Email': "someone_f@example.com" },
          { 'Full Name': "Rene Valdes (sample)",       'Primary Email': "someone_g@example.com" } 
    )
    ```
1. Seleccione el botón [mientras mantiene presionada la tecla Alt](../keyboard-shortcuts.md#alternate-behavior).

Se crea una colección de ejemplo que puede usar en el ejemplo siguiente.

### <a name="trash-can-icon-inside-a-gallery"></a>El icono de la papelera se encuentra dentro de una galería

1. Cree una [nueva aplicación de lienzo en blanco](../data-platform-create-app-scratch.md) con un diseño de teléfono.

    ![Una aplicación de lienzo en blanco con el diseño del teléfono](media/function-remove-removeif/gallery-new.png)

1. Seleccione la **inserción** en el panel izquierdo.

1. Seleccione **Galería vertical**. <br>
    Se agrega un control **Galería** a la pantalla.

    ![Usar el panel de herramientas insertar para agregar un control Galería vertical](media/function-remove-removeif/gallery-add.png)

1. Se le pedirá que seleccione un origen de datos en el que puede seleccionar un origen de datos de los orígenes de datos disponibles. <br>
    Por ejemplo, seleccione la entidad **contactos** para usar *datos de ejemplo*:  

    ![Selección de la entidad contactos que se va a mostrar en la galería](media/function-remove-removeif/gallery-datasource.png)

    Si ha creado una [colección](#create-a-collection-with-sample-data), seleccione la colección en su lugar:

    ![Colección de contactos de ejemplo](media/function-remove-removeif/sample-contacts.png)

1. Seleccione un control en el elemento superior de la galería. <br>
    
    Para asegurarse de que el paso siguiente inserta un elemento en la plantilla de la galería y no fuera de la galería, asegúrese de seguir este paso antes de pasar al paso siguiente.
    
    ![Seleccionar el registro superior en una galería](media/function-remove-removeif/gallery-select-template.png)

1. Seleccione **Agregar icono** en el panel izquierdo. <br>
    
    ![Usar el panel de herramientas insertar para agregar un control de icono](media/function-remove-removeif/gallery-addicon.png)

    > [!NOTE]
    > **Agregar icono** inserta un icono de **+** en el lado izquierdo de la galería, replicado para cada elemento de la galería. 

1. En el elemento superior, mueva el icono al lado derecho de la pantalla.

    ![Icono Mover](media/function-remove-removeif/move-icon.png)

1. Seleccione la propiedad **icono** para icono y establézcala en la siguiente fórmula para actualizar la imagen del icono como icono de la papelera:

    ```powerapps-dot 
    Icon.Trash
    ```
    
    > [!NOTE]
    > **Icono.** el prefijo solo se muestra cuando está editando la fórmula activamente.

    ![Cambiar el icono al icono de la papelera](media/function-remove-removeif/gallery-icontrash.png)

1. Establezca la propiedad **AlSeleccionar** en la fórmula siguiente:

    ```powerapps-dot
    Remove( [@Contacts], ThisItem )
    ```

    > [!NOTE]
    > Debe usar el [operador de desambiguación global](operators.md#disambiguation-operator) **[@** ... **]** en este ejemplo con datos de ejemplo que usan la entidad *Contacts* para evitar conflictos con una relación de *uno a varios* . Si usa orígenes de datos como una lista de SharePoint o una tabla de SQL Server, no es necesario usar el *operador disambgulation global* .

    ![Seleccionar para el icono de la papelera](media/function-remove-removeif/gallery-onselect.png)

1. Obtenga una vista previa de la aplicación con el botón *reproducir* en la parte superior derecha o presione *F5* en el teclado.

1. Seleccione el icono de la papelera junto a un registro, por ejemplo *María*:

    ![Galería con uno de los contactos quitados](media/function-remove-removeif/gallery-activateicon.png)

    Se elimina el registro:

    ![Registro eliminado](media/function-remove-removeif/deleted-record.png)

1. Cierre la vista previa de la aplicación.
