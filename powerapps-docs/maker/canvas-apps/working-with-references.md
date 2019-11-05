---
title: Descripción de las referencias de registros y las búsquedas polimórficas | Microsoft Docs
description: Trabajar con referencias de registros y búsquedas polimórficas en aplicaciones de Canvas
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0b1c81dd808b224ca30d9de3d4bab252a2676cf4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542315"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>Descripción de las referencias de registros y las búsquedas polimórficas en las aplicaciones de Canvas

Al escribir un documento de investigación en School, es probable que haya proporcionado una lista de las referencias al final. No incluyó una copia del material de fondo real que usó, sino un vínculo Web, un título de libro y un autor u otra información para que alguien pueda realizar un seguimiento del origen original. Ha mezclado distintos tipos de orígenes en una sola lista, artículos de periódicos junto a grabaciones de audio, cada uno con sus propios detalles específicos para una cita adecuada. Por ejemplo, los artículos de Wikipedia suelen incluir una [larga lista de referencias](https://en.wikipedia.org/wiki/Microsoft#References).

En las aplicaciones de lienzo, a menudo se trabaja con copias de registros descargados de orígenes de datos. Use las funciones de [**búsqueda**](functions/function-filter-lookup.md) y [**filtrado**](functions/function-filter-lookup.md) y la propiedad **seleccionada** del control [**Galería**](controls/control-gallery.md) para identificar el registro específico que desea. Todos los registros de **Filter** o **selected** serán del mismo tipo de entidad, por lo que puede usar campos con un simple. Notación de *campo* . Estas copias suelen incluir información de referencia, por lo que puede usar la función [**patch**](functions/function-patch.md) para actualizar el origen original.

Las aplicaciones de lienzo también admiten *referencias de registros*. De forma muy parecida a una referencia en papel de investigación, una referencia de registro hace referencia a un registro sin incluir una copia completa del mismo. Una referencia de este tipo puede hacer referencia a un registro de cualquier entidad. Además de las referencias de papel de investigación, puede mezclar registros de diferentes entidades en una sola columna.

Muchas operaciones en las referencias de registro son idénticas a trabajar con registros. Puede comparar referencias de registro entre sí y con registros completos. Puede establecer el valor de una referencia de registro con la función **patch** tal como lo haría con una búsqueda con un registro completo.

Hay una diferencia de uso importante: no puede acceder directamente a los campos de una referencia de registro sin tener que establecer primero la entidad a la que hace referencia. Esto se debe a que las aplicaciones de lienzo requieren que se conozcan todos los tipos al escribir fórmulas. Dado que no conoce el tipo de una referencia de registro hasta que se ejecuta la aplicación, no puede usar la sencilla. Notación de *campo* directamente. Primero debe determinar dinámicamente el tipo de entidad con la función [**IsType**](functions/function-astype-istype.md) y, a continuación, usar. Notación de *campo* en el resultado de la función [**astype**](functions/function-astype-istype.md) .

El *tipo de entidad* hace referencia al esquema de cada registro de una entidad. Cada entidad tiene un conjunto único de campos con nombres y tipos de datos diferentes. Cada registro de la entidad hereda esa estructura; dos registros tienen el mismo tipo de entidad si proceden de la misma entidad.

## <a name="polymorphic-lookups"></a>Búsquedas polimórficas

Common Data Service admite relaciones entre los registros. Cada registro de la entidad **cuentas** tiene un campo principal de búsqueda de **contactos** en un registro de la entidad **contactos** . La búsqueda solo puede hacer referencia a un registro de **contactos** y no puede hacer referencia a un registro en, por ejemplo, la entidad **equipos** . Este último detalle es importante porque siempre sabe qué campos estarán disponibles para la búsqueda.

Common Data Service también admite búsquedas polimórficas, que pueden hacer referencia a un registro de cualquier entidad de un conjunto. Por ejemplo, el campo **propietario** puede hacer referencia a un registro de la entidad **usuarios** o de la entidad **equipos** . El mismo campo de búsqueda en distintos registros podría hacer referencia a los registros de entidades diferentes. En este caso, no siempre sabe qué campos estarán disponibles.

Las referencias de los registros de Canvas se diseñaron para trabajar con búsquedas polimórficas en Common Data Service. También puede utilizar las referencias de registros fuera de este contexto, que es la diferencia entre los dos conceptos.

En la siguiente sección, comenzará a explorar estos conceptos trabajando con la búsqueda de **propietario** .

## <a name="show-the-fields-of-a-record-owner"></a>Mostrar los campos de un propietario de registro

Cada entidad de Common Data Service incluye un campo de **propietario** . Este campo no se puede quitar, no se puede agregar otro, y siempre requiere un valor.

Para mostrar ese campo en la entidad **cuenta** :

1. Abra [este sitio de PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
1. En la barra de navegación izquierda, seleccione **datos** > **entidades**.
1. En la lista de entidades, seleccione **cuenta**.
1. En la esquina superior derecha, abra la lista de filtros (que está establecida en **predeterminada** de forma predeterminada) y, a continuación, seleccione **todo**.
1. Desplácese hacia abajo hasta que aparezca el campo **propietario** .

 > [!div class="mx-imgBorder"]
 > ![campo propietario en la entidad cuenta](media/working-with-references/owner-field.png)

Este campo de búsqueda puede hacer referencia a un registro de la entidad **equipos** o de la entidad **usuarios** . No todos los registros de estas entidades tienen permiso para ser **propietarios**; Compruebe los roles admitidos si surge un problema.

En este gráfico se muestra una sencilla Galería de **cuentas**, donde la entidad **cuentas** se ha agregado a la aplicación como un origen de datos:

> [!div class="mx-imgBorder"]
> ![cuentas que se muestran en un control Galería](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> En este tema, los gráficos muestran algunos nombres y otros valores que no forman parte de los datos de ejemplo que se suministran con Common Data Service. Los pasos demuestran con precisión cómo configurar controles para un resultado determinado, pero su experiencia variará en función de los datos de su organización.

Para mostrar el propietario de cada cuenta en la galería, es posible que se sienta tentado a usar la fórmula **ThisItem.Owner.Name**. Sin embargo, el campo Nombre de la entidad **equipo** es **nombre del equipo**y el campo Nombre de la entidad **usuario** es **nombre completo**. La aplicación no puede conocer el tipo de búsqueda con el que está trabajando hasta que ejecute la aplicación y puede variar entre los registros de la entidad **cuentas** .

Necesita una fórmula que se pueda adaptar a esta varianza. También debe agregar los orígenes de datos para los tipos de entidad que el **propietario** podría ser (en este caso, **usuarios** y **equipos**). Agregue estos tres orígenes de datos a la aplicación:

> [!div class="mx-imgBorder"]
> ![las entidades cuentas, equipos y usuarios en el panel datos](media/working-with-references/accounts-datasources.png)

Con estos orígenes de datos en su lugar, use esta fórmula para mostrar el nombre de un usuario o un equipo:

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> ![cuentas que se muestran en un control galería con el campo propietario mostrado](media/working-with-references/accounts-displayowner.png)

En esta fórmula, la función **IsType** prueba el campo **propietario** con la entidad **Teams** . Si es de ese tipo de entidad, la función **astype** lo convierte en un registro de **equipo** . En este momento, puede tener acceso a todos los campos de la entidad **Teams** , incluido el **nombre del equipo**, mediante el *.* Notación de campo. Si **IsType** determina que el **propietario** no es un registro de la entidad **Teams** , ese campo debe ser un registro de la entidad **users** porque el campo **Owner** es obligatorio (no puede estar *en blanco*).

Utiliza el operador de [desambiguación global](functions/operators.md#disambiguation-operator) para **[@Teams]** y **[@Users]** para asegurarse de que está usando el tipo de entidad global. En este caso, no es necesario, pero es un buen hábito formar. Las relaciones uno a varios a menudo entran en conflicto en el ámbito de registro de la galería y esta práctica evita esa confusión.

Para usar cualquier campo de una referencia de registro, primero debe usar la función **astype** para convertirlo en un tipo de entidad concreto. No se puede acceder a los campos directamente desde el campo **propietario** porque el sistema no sabe qué tipo de entidad desea usar.

La función **astype** devuelve un error si el campo **Owner** no coincide con el tipo de entidad que se solicita, por lo que puede usar la función de tipo **de mensaje** para simplificar esta fórmula. En primer lugar, active la característica experimental **Administración de errores de nivel de fórmula**:

> [!div class="mx-imgBorder"]
> ![modificador experimental para activar la administración de errores de nivel de fórmula](media/working-with-references/accounts-iferror.png)

A continuación, reemplace la fórmula anterior por esta:

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>Filtrar según un propietario

Enhorabuena: ha terminado el aspecto más difícil de trabajar con una referencia de registro. Otros casos de uso son más sencillos porque no tienen acceso a los campos del registro. Como caso en el punto, tome el filtrado, que explorará en esta sección.

Agregue un control de **cuadro combinado** sobre la galería y establezca estas propiedades del nuevo control:

- **Elementos**: `Users`
- **SelectMultiple**: `false`

> [!div class="mx-imgBorder"]
> ![agregado el control de cuadro combinado anterior en la galería con la propiedad items establecida en users](media/working-with-references/filter-insert-combobox.png)

Para filtrar la galería por un usuario específico seleccionado en este cuadro combinado, establezca la propiedad **elementos** de la galería en esta fórmula:

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![Galería filtrada según el valor establecido en el control de cuadro combinado](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> Las instrucciones de este tema son precisas si sigue los pasos exactamente. Sin embargo, se produce un error en cualquier fórmula que haga referencia a un control por su nombre si el control tiene un nombre diferente. Si elimina y agrega un control del mismo tipo, cambia el número al final del nombre del control. Para cualquier fórmula que muestre un error, confirme que contiene los nombres correctos de todos los controles.

No es necesario usar **IsType** o **astype** porque está comparando las referencias de registros con otras referencias de registros o con registros completos. La aplicación conoce el tipo de entidad de **ComboBox1. seleccionado** porque se deriva de la entidad **usuarios** . Las cuentas para las que el propietario es un equipo no coinciden con el criterio de filtro.

Puede obtener un poco más elegante si admite el filtrado por parte de un usuario o un equipo.

1. Para colocar espacio cerca de la parte superior de la pantalla, cambie el tamaño de la galería y mueva el cuadro combinado, inserte un [control **radio** ](controls/control-radio.md) sobre la galería y, a continuación, establezca estas propiedades para el nuevo control:

    - **Elementos**: `[ "All", "Users", "Teams" ]`
    - **Diseño**: `Layout.Horizontal`

1. En el caso del control de **cuadro combinado** , establezca esta propiedad (si el cuadro combinado desaparece, seleccione **usuarios** en el control de radio):

    - **Visible**: `Radio1.Selected.Value = "Users"`

1. Copie y pegue el control de **cuadro combinado** , mueva la copia directamente sobre la original y, a continuación, establezca estas propiedades para la copia:

    - **Elementos**: `Teams`
    - **Visible**: `Radio1.Selected.Value = "Teams"`

    La aplicación solo mostrará un cuadro combinado cada vez, en función del estado del control de radio. Como están directamente encima de otras, parecerá que son el mismo control que cambia su contenido.

1. Por último, establezca la propiedad **elementos** del control **Galería** en esta fórmula:

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Galería filtrada que muestra todos los registros o un usuario o equipo específico](media/working-with-references/filter-combobox.png)

Con estos cambios, puede mostrar todos los registros o filtrarlos en función de un usuario o un equipo:

> [!div class="mx-imgBorder"]
> ![animación que muestra distintos resultados filtrados basados en el control de radio y los cuadros combinados](media/working-with-references/filter-allthree.gif)

La fórmula es totalmente delegables. La parte que compara los valores del botón de radio es una constante en todos los registros y se evalúa antes de que se envíe el resto del filtro a Common Data Service.

Si desea filtrar según el tipo del propietario, puede usar la función **IsType** , pero todavía no se delegables.

> [!div class="mx-imgBorder"]
> ![filtrar por tipo de propietario mediante IsType](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>Actualizar el propietario mediante el uso de patch

Puede actualizar el campo **propietario** de la misma manera que cualquier otra búsqueda. Para establecer el propietario de la cuenta seleccionada actualmente en el primer equipo:

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

Este enfoque no difiere de una búsqueda normal porque la aplicación conoce el tipo de **primero (equipos)** . Si desea el primer usuario en su lugar, reemplace esa parte con el **primero (usuarios)** . La función **patch** sabe que el campo **Owner** se puede establecer en cualquiera de estos dos tipos de entidad.

Para agregar esta funcionalidad a la aplicación:

1. En el panel de **vista de árbol** , seleccione el control de **radio** y los dos controles de **cuadro combinado** al mismo tiempo.

1. En el menú de puntos suspensivos, seleccione **copiar estos elementos**.

    > [!div class="mx-imgBorder"]
    > ![copia de varios controles mediante la vista de árbol](media/working-with-references/patch-copy.png)

1. En el mismo menú, seleccione **pegar**.

    > [!div class="mx-imgBorder"]
    > ![pegar varios controles mediante la vista de árbol](media/working-with-references/patch-paste.png)

1. Mueva los controles copiados a la derecha de la galería.

    > [!div class="mx-imgBorder"]
    > ![mueve los controles copiados a la derecha de la Galería](media/working-with-references/patch-position.png)

1. Seleccione el control de **radio** copiado y, a continuación, cambie estas propiedades:

    - Elementos: `[ "Users", "Teams" ]`
    - Valor predeterminado: `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![quitó la opción All del control radio](media/working-with-references/patch-noall.png) 

1. En el control **radio** , seleccione **usuarios** para que el control de **cuadro combinado** que muestra los usuarios esté visible.

1. Seleccione el control de **cuadro combinado** visible y, a continuación, establezca la propiedad **DefaultSelectedItems** en esta fórmula:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![conjunto de propiedades predeterminado para el cuadro combinado usuarios](media/working-with-references/patch-default-users.png)

1. En el control **radio** , seleccione **equipos** para que el control de **cuadro combinado** que muestra los equipos sea visible.

1. Seleccione el control de **radio** para quitar la selección del control de **cuadro combinado** ahora invisible para los usuarios.

1. Seleccione el control de **cuadro combinado** visible para equipos y, a continuación, establezca su propiedad **DefaultSelectedItems** en esta fórmula:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![conjunto de propiedades predeterminado para el cuadro combinado Teams](media/working-with-references/patch-default-teams.png)

1. Inserte un control de **botón** , muévalo debajo del control de **cuadro combinado** y, a continuación, establezca la propiedad **Text** del botón en `"Patch Owner"`.

1. Establezca la propiedad **alseleccionar** del botón en esta fórmula:

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ![fórmula establecida en el control de botón](media/working-with-references/patch-button.png)

Los controles de **radio** y de **cuadro combinado** copiados muestran el propietario de la cuenta seleccionada actualmente en la galería. Con los mismos controles, puede establecer el propietario de la cuenta en cualquier equipo o usuario seleccionando el botón:

> [!div class="mx-imgBorder"]
> ![animación que muestra la revisión del propietario con un usuario o un equipo](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>Mostrar el propietario mediante un formulario

Puede mostrar un campo **propietario** dentro de un formulario agregando una tarjeta personalizada. En el que se redactó este documento, no se puede cambiar el valor del campo con un control de formulario.

1. Inserte un control **Editar formulario** y, a continuación, cambie su tamaño y muévalo a la esquina inferior derecha.

1. En la pestaña **propiedades** situada cerca del lado derecho de la pantalla, abra la lista **origen de datos** y, a continuación, seleccione **cuentas**.

    > [!div class="mx-imgBorder"]
    > ![control de formulario que muestra campos adicionales con valores en blanco](media/working-with-references/form-insert.png)  

1. Establezca la propiedad **Item** del formulario en `Gallery1.Selected`.

    > [!div class="mx-imgBorder"]
    > ![control de formulario que muestra campos adicionales que se rellenan a partir del elemento seleccionado en la Galería](media/working-with-references/form-item.png)

1. En la pestaña **propiedades** situada cerca del lado derecho de la pantalla, seleccione **Editar campos**.

1. En el panel **campos** , seleccione los puntos suspensivos y, a continuación, seleccione **Agregar una tarjeta personalizada**.

    > [!div class="mx-imgBorder"]
    > ![comando para agregar una tarjeta personalizada](media/working-with-references/form-customcard.png)

    La nueva tarjeta aparece en la parte inferior del control de formulario.

1. Cambie el tamaño de la tarjeta según sea necesario para mostrar todo el texto.

    > [!div class="mx-imgBorder"]
    > ![tarjeta personalizada insertada, en blanco](media/working-with-references/form-inserted-customcard.png)

1. Inserte un control **etiqueta** en la tarjeta personalizada y, a continuación, establezca la propiedad **texto** de la etiqueta en la fórmula que usó en la Galería:

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![tarjeta personalizada que muestra el campo propietario en un control etiqueta](media/working-with-references/form-displayowner.png)

Para cada selección de la galería, aparecen en el formulario más campos de la cuenta, incluido el propietario del registro. Si cambia el propietario con el botón **patch** , el control de formulario también muestra ese cambio.

> [!div class="mx-imgBorder"]
> ![animación que muestra el control de formulario que responde a los cambios en la Galería](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>Mostrar los campos de un cliente

En Common Data Service, el campo de búsqueda de **clientes** es otra búsqueda polimórfica que es muy similar al **propietario**.

**Owner** está limitado a uno por entidad, pero las entidades pueden incluir cero, uno o más campos de búsqueda de **clientes** . La entidad sistema de **contactos** incluye el campo Nombre de la **compañía** , que es un campo de búsqueda de **clientes** .

> [!div class="mx-imgBorder"]
> ![entidad contacto que muestra el campo Nombre de la compañía como un tipo de datos de cliente que no es necesario](media/working-with-references/customer-companyname.png)

Puede agregar más campos de búsqueda de **clientes** a una entidad seleccionando el tipo de datos **Customer** para un campo nuevo.

![Tipo de datos de cliente de la lista de tipos de datos al crear un campo](media/working-with-references/customer-datatype.png)

Los campos de búsqueda de **clientes** pueden hacer referencia a un registro de la entidad **accounts** o de la entidad **Contacts** . Usará las funciones **IsType** y **astype** con estas entidades, por lo que ahora es un buen momento para agregarlas como orígenes de datos (puede dejar los **equipos** y **los usuarios** en su lugar).

> [!div class="mx-imgBorder"]
> ![las entidades cuentas, equipos, usuarios y contactos en el panel datos](media/working-with-references/customer-datasources.png)

El tratamiento de los campos **cliente** y **propietario** es tan similar que puede copiar literalmente la aplicación (**archivo** > **Guardar como**y, a continuación, especificar un nombre diferente) y realizar estos reemplazos sencillos:

| Location | Ejemplo **Owner** | Ejemplo de **cliente** |
|----------|-----------|------------------|
| Todas | **Propietario** | **' Nombre del cliente '** |
| Todas | **Pueden** | **Contabilidad** |
| Todas | **Asocia** | **Sus** |
| Propiedad **Items** de la galería | **Contabilidad** | **Sus** |
| Propiedad **Items** del formulario | **Contabilidad** | **Sus** |
| Primer argumento de **patch**<br>en la propiedad **alseleccionar** del botón | **Contabilidad** | **Sus** |
| Propiedad filtrar **elementos** de radio | **[&nbsp;"todos",&nbsp;"usuarios",&nbsp;"equipos"&nbsp;]** | **[&nbsp;"todas",&nbsp;"cuentas",&nbsp;"contactos"&nbsp;]** |
| Propiedad **elementos** de radio de revisión | **["Usuarios", "equipos"]** | **["Accounts", "Contacts"]** |
| Propiedad **visible** del cuadro combinado | **"Usuarios"** y **"equipos"** | **"Cuentas"** y **"contactos"** |

Por ejemplo, la nueva galería debe tener esta propiedad **Items** :

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> ![aplicación de cliente derivada de la aplicación propietaria con cambios sencillos aplicados](media/working-with-references/customer-simple-update.png)

Dos diferencias importantes entre **Customer** y **Owner** requieren una actualización de las fórmulas dentro de la galería y el formulario:

1. Las relaciones uno a varios entre **cuentas** y **contactos** tienen prioridad cuando se hace referencia a estos tipos de entidad por nombre. En lugar de **cuentas**, use **\[cuentas de \@]** ; en lugar de **contactos**, use **\[\@contactos]** . Mediante el [operador de desambiguación global](functions/operators.md#disambiguation-operator), asegúrese de que hace referencia al tipo de entidad en **IsType** y **astype**. Este problema solo existe en el contexto de registro de la galería y los controles de formulario.

1. El campo **propietario** debe tener un valor, pero los campos de **cliente** pueden estar *en blanco*. Para mostrar el resultado correcto sin un nombre de tipo, pruebe este caso con la [función **esblanco** ](functions/function-isblank-isempty.md)y muestre una cadena de texto vacía en su lugar.

Ambos de estos cambios están en la misma fórmula, que aparece en la tarjeta personalizada en el formulario, así como en la propiedad **texto** del control etiqueta de la Galería:

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![propiedad actualizar a texto del control etiqueta de subtítulos en la Galería](media/working-with-references/customer-update.png)

Con estos cambios, puede ver y cambiar el campo **nombre** de la compañía en la entidad **contactos** .

> [!div class="mx-imgBorder"]
> ![animación que muestra cómo la selección de un contacto cambia el resto de controles y el formulario](media/working-with-references/customer-allthree.gif)

## <a name="understand-regarding-lookup-fields"></a>Comprender con respecto a los campos de búsqueda

El campo de búsqueda **referente** a se diferencia de los que ya ha trabajado en este tema. Empezará aplicando los patrones descritos anteriormente en este tema y, a continuación, aprenderá otros trucos.

Puede empezar simplemente con la entidad **faxes** . Esta entidad tiene una polimórfico **relacionada** con el campo de búsqueda, que puede hacer referencia a **cuentas**, **contactos**y otras entidades. Puede usar la aplicación para **clientes** y modificarla para **faxes**.

| Location | Ejemplo de **cliente** | Ejemplo de **faxes** |
|----------|-----------|------------------|
| Todas | **' Nombre del cliente '** | **Sobre** |
| Propiedad **Items** de la galería | **Sus** | **Faxes** |
| Propiedad **Items** del formulario | **Sus** | **Faxes** |
| Primer argumento de **patch**<br> en la propiedad **alseleccionar** del botón | **Sus** | **Faxes** |

De nuevo, tendrá que agregar un origen de datos: esta vez para **faxes**. En la pestaña **Ver** , seleccione **orígenes de datos**:

> [!div class="mx-imgBorder"]
> ![panel datos que muestra las entidades cuentas, equipos, usuarios, contactos y faxes](media/working-with-references/faxes-datasources.png)

Una diferencia importante con **respecto** a es que no se limita a **las cuentas** y los **contactos**. De hecho, la lista de entidades es extensible con entidades personalizadas. La mayoría de la aplicación puede acomodar este punto sin modificaciones, pero debe actualizar la fórmula de la etiqueta en la galería y el formulario:

```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    ""
)
```

> [!div class="mx-imgBorder"]
> ![propiedad de texto actualizada para el control de subtítulo para las búsquedas relativas](media/working-with-references/regarding-label.png)

Después de realizar estos cambios, trabajará con la búsqueda **relacionada** tal como hizo con el **propietario** y las búsquedas del **cliente** .

> [!div class="mx-imgBorder"]
> ![animación que muestra cómo la selección de un elemento de la Galería cambia el resto de controles y el formulario](media/working-with-references/regarding-allthree.gif)

## <a name="understand-regarding-relationships"></a>Descripción de las relaciones

En lo que **respecta** difiere del **propietario** y del **cliente** porque el primero implica una relación de varios a uno. Por definición, una relación de uno a varios inversa le permite escribir **primero (cuentas). Faxes**.

Vamos a realizar una copia de seguridad y examinar las definiciones de entidad. En Common Data Service, las entidades como **faxes**, **tareas**, **correos electrónicos**, **notas**, **llamadas telefónicas**, **cartas**y **chats** se designan como [*actividades*](../../developer/common-data-service/activity-entities.md). También puede crear sus propias [entidades de actividad personalizadas](../../developer/common-data-service/custom-activities.md). Al ver o crear una entidad de actividad, su configuración aparece en **más configuraciones**.

![Configuración de la entidad de actividad al crear una entidad](media/working-with-references/activity-entitytype.png)

Otras entidades pueden estar relacionadas con una entidad de actividad si están habilitadas como una *tarea de actividad* en la configuración de la entidad. **Las cuentas**, los **contactos**y muchas otras entidades estándar se deben designar (de nuevo, en **más configuraciones**).

![Configuración de la tarea actividad al crear una entidad](media/working-with-references/activity-entityuse.png)

Todas las entidades de actividad y las entidades de tarea-tarea tienen una relación implícita. Si cambia el filtro a **todo** en la parte superior de la pantalla, selecciona la entidad **faxes** y, a continuación, selecciona la pestaña **relaciones** , se mostrarán todas las entidades que pueden ser un destino de una búsqueda **relacionada** .

> [!div class="mx-imgBorder"]
> ![relaciones de la entidad faxes que se muestran en relación con las relaciones de varios a uno](media/working-with-references/activity-manytoone.png)

Si muestra las relaciones de la entidad **cuentas** , aparecen todas las entidades que pueden ser un origen de un campo de búsqueda **referente** a.

> [!div class="mx-imgBorder"]
> ![las relaciones de la entidad de cuenta con respecto a las relaciones de uno a varios](media/working-with-references/activity-onetomany.png)

¿Qué significa todo?

- Al escribir fórmulas, debe tener en cuenta que la lista de entidades de actividad no es fija y puede crear la suya propia. La fórmula debe administrar correctamente una entidad de actividad que no se esperaba.
- Las actividades y tareas de actividad tienen una relación de uno a varios. Puede solicitar fácilmente todos los faxes relacionados con una cuenta.

Para explorar este concepto en la aplicación:

1. Agregue otra pantalla.

    > [!div class="mx-imgBorder"]
    > ![insertar una pantalla en blanco](media/working-with-references/activitypointer-newscreen.png)

1. Inserte un control de galería, cambie su tamaño y, a continuación, muévalo a la parte izquierda de la pantalla.

1. En la pestaña **propiedades** situada cerca del lado derecho de la pantalla, establezca los **elementos** de la galería en **cuentas**.

    > [!div class="mx-imgBorder"]
    > ![establecer elementos en cuentas en el panel de propiedades](media/working-with-references/activitypointer-accounts.png)

1. Establezca el diseño de la galería en **título**y, a continuación, establezca el campo título en **nombre de cuenta**.

    > [!div class="mx-imgBorder"]
    > ![establecer diseño en título para el control Galería en el panel Propiedades](media/working-with-references/activitypointer-account-name.png)

1. Agregue una segunda galería, cambie su tamaño y, a continuación, muévala al lado derecho de la pantalla.

1. Establezca la propiedad **elementos** de la nueva galería en `Gallery2.Selected.Faxes`.

    Este paso devuelve la lista filtrada de faxes para una cuenta determinada.

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad elementos de la galería que muestra los faxes](media/working-with-references/activitypointer-faxes.png)

1. Establezca el diseño de la galería en **título y subtítulo**y, a continuación, establezca el campo título para mostrar el campo **asunto** (que puede estar **en minúsculas**).

    > [!div class="mx-imgBorder"]
    > ![establecer título en el campo asunto](media/working-with-references/activitypointer-subject.png)

A medida que selecciona un elemento en la lista de cuentas, la lista de faxes solo muestra faxes para esa cuenta.

> [!div class="mx-imgBorder"]
> ![animación que muestra la selección en la galería de cuentas que conduce a la lista de faxes](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>Entidad de actividad

Como se describe en la sección anterior, puede mostrar todos los faxes de una cuenta. Sin embargo, también puede mostrar todas las actividades de una cuenta, incluidos los faxes, mensajes de correo electrónico, llamadas telefónicas y otras interacciones.

En el segundo escenario, se usa la entidad de **actividad** . Puede mostrar esta entidad activando **todo** en la esquina superior derecha para quitar el filtro de la lista de entidades.

> [!div class="mx-imgBorder"]
> ![lista de entidades que muestran la entidad de actividad](media/working-with-references/activitypointer-entity.png)

La entidad de **actividad** es especial. Siempre que se agrega un registro a la entidad **faxes** , el sistema también crea un registro en la entidad **actividad** con los campos que son comunes a todas las entidades de actividad. De esos campos, el **asunto** es uno de los más interesantes.

Puede mostrar todas las actividades cambiando solo una línea en el ejemplo anterior. Reemplace `Gallery2.Selected.Faxes` por `Gallery2.Selected.Activities`.

> [!div class="mx-imgBorder"]
> ![cambio de la propiedad elementos de la segunda galería, cambiando de faxes a actividades](media/working-with-references/activitypointer-gallery.png)

Los registros provienen de la entidad de **actividad** , pero puede usar la función **IsType** para identificar el tipo de actividad que son. De nuevo, antes de utilizar **IsType** con un tipo de entidad, debe agregar el origen de datos.

> [!div class="mx-imgBorder"]
> ![panel de datos que muestra todas las entidades necesarias para la función IsType](media/working-with-references/activity-datasources.png)

Con esta fórmula, puede mostrar el tipo de registro en un control etiqueta dentro de la Galería:

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![establecer la propiedad texto en fórmula para mostrar información de faxes, llamadas telefónicas y otras actividades](media/working-with-references/activitypointer-type.png)

También puede usar **astype** para tener acceso a los campos del tipo específico. Por ejemplo, esta fórmula determina el tipo de cada actividad y, en el caso de las llamadas telefónicas, muestra el número de teléfono y la dirección de llamada de la entidad **números de teléfono** :

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ),
       "Phone Call: " &
       AsType( ThisItem, [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem, [@'Phone Calls'] ).Direction & ")",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![propiedad de texto expandido con más información para una llamada telefónica](media/working-with-references/activitypointer-phonecall.png)

Como resultado, la aplicación muestra una lista completa de las actividades. El campo **asunto** aparece para todos los tipos de actividades, tanto si la fórmula los tiene en cuenta como si no. En el caso de los tipos de actividades que conoce, puede mostrar sus nombres de tipo e información específica del tipo de cada actividad.

> [!div class="mx-imgBorder"]
> ![pantalla completada que muestra información para diferentes tipos de actividades](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>Entidad de notas

Hasta ahora, todos los ejemplos **relacionados** se basaban en actividades, pero la entidad **notas** representa otro caso.

Al crear una entidad, puede habilitar los datos adjuntos.

> [!div class="mx-imgBorder"]
> ![habilitar datos adjuntos y notas al crear una entidad](media/working-with-references/notes-entity.png)

Si activa la casilla para habilitar los datos adjuntos, creará una relación **relacionada** con la entidad **notas** , como se muestra en este gráfico para la entidad **cuentas** :

> [!div class="mx-imgBorder"]
> ![entidad de cuenta que muestra la relación con las notas a través de una relación de uno a varios](media/working-with-references/notes-relationships.png)

Aparte de esta diferencia, se usa la búsqueda **relacionada** de la misma manera en que se usan las actividades. Las entidades que están habilitadas para los datos adjuntos tienen una relación de uno a varios con las **notas**, como en este ejemplo:

`First( Accounts ).Notes`

> [!NOTE]
> En el que se redactó este documento, la búsqueda **relacionada** no está disponible para la entidad **notas** . No se puede leer ni filtrar según el campo **referente** a y no se puede establecer el campo mediante **patch**.
>
> Sin embargo, la relación inverso de **notas** de uno a varios está disponible, por lo que puede filtrar una lista de notas para un registro habilitado para los datos adjuntos. También puede usar la función [**Relate**](functions/function-relate-unrelate.md) para agregar una nota a la tabla de **notas** de un registro, pero primero se debe crear la nota, como en este ejemplo:
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>Entidades de actividad

En el que se redactó este documento, las aplicaciones de lienzo no admiten las entidades de actividad.