---
title: Comprender las referencias de registros y búsquedas polimórficas | Microsoft Docs
description: Trabajar con registros referencias y polimórficas búsquedas en las aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/05/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 99024b447841668bd887571a269c2fb14f5f5289
ms.sourcegitcommit: f6c9e525130a03b8c76f0a4b4e90419604c5823c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527098"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>Comprender las referencias de registros y polimórficas búsquedas en las aplicaciones de lienzo

Cuando escribí un artículo de investigación en la escuela, probablemente le proporciona una lista de las referencias al final. No incluye una copia del material de fondo real utilizado, pero en su lugar un vínculo web, título de libro y autor u otra información para que alguien pudo localizar el origen original. Mezclar distintos tipos de orígenes en una sola lista de artículos periodísticos junto a las grabaciones de audio, cada uno con sus propios detalles específicos para una cita adecuada. Por ejemplo, los artículos de Wikipedia incluyen a menudo un [larga lista de referencias](https://en.wikipedia.org/wiki/Microsoft#References).

En las aplicaciones de lienzo, sueles trabajar con copias de registros descargados de orígenes de datos. Usa el [ **búsqueda** ](functions/function-filter-lookup.md) y [ **filtro** ](functions/function-filter-lookup.md) funciones y la [ **galería** ](controls/control-gallery.md) del control **seleccionados** propiedad para identificar el registro específico que desee. Todos los registros de **filtro** o **seleccionados** será del mismo tipo de entidad, por lo que puede usar campos con un sencillo. *Campo* notación. Estas copias a menudo incluyen información de referencia para que pueda usar el [ **Patch** ](functions/function-patch.md) función para actualizar el origen original.

También admiten aplicaciones de lienzo *registrar referencias*. Mucho como una referencia de documento de investigación, una referencia de registro hace referencia a un registro sin necesidad de incluir una copia completa del mismo. Este tipo de referencia puede hacer referencia a un registro en cualquier entidad.  También como artículo de investigación de referencias, puede combinar los registros de diferentes entidades de una sola columna.

Muchas operaciones en las referencias del registro son idénticas a trabajar con registros. Puede comparar registros referencias entre sí y a registros completos. Se puede establecer el valor de un registro de la referencia con la **revisión** funcionando como lo haría con una búsqueda con un registro completo.

Hay una diferencia importante del uso: no puede acceder directamente los campos de una referencia de registro sin establecer primero a la entidad que hace referencia. Esto es porque las aplicaciones de lienzo requieren que todos los tipos de conocerse al escribir fórmulas. Puesto que desconoce el tipo de una referencia de registro hasta que se ejecuta la aplicación, no puede usar el sencillo. *Campo* notation directamente. Primero debe determinar dinámicamente el tipo de entidad con el [ **IsType** ](functions/function-astype-istype.md) función y, a continuación, usar. *Campo* notación del resultado de la [ **AsType** ](functions/function-astype-istype.md) función.

*Tipo de entidad* hace referencia al esquema de cada registro de una entidad. Cada entidad tiene un único conjunto de campos con diferentes nombres y tipos de datos. Cada registro de la entidad hereda esa estructura; dos registros tienen el mismo tipo de entidad si proceden de la misma entidad.

## <a name="polymorphic-lookups"></a>Búsquedas polimórficas

Common Data Service admite las relaciones entre los registros. Cada registro de la **cuentas** entidad tiene un **contacto principal** campo de búsqueda a un registro en el **contactos** entidad. La búsqueda solo puede hacer referencia a un registro en **contactos** y no puede hacer referencia a un registro, por ejemplo, el **equipos** entidad. Que el último detalle es importante porque siempre sabe qué campos estarán disponibles para la búsqueda.

Common Data Service también admite búsquedas polimórficas, lo que pueden hacer referencia a un registro de cualquier entidad en un conjunto. Por ejemplo, el **propietario** campo puede hacer referencia a un registro en el **usuarios** entidad o la **equipos** entidad. El mismo campo de búsqueda de registros distintos podría referirse a registros de entidades diferentes. En este caso, no siempre sabemos qué campos estarán disponibles.  

Referencias de registros de lienzo se diseñaron para trabajar con las búsquedas polimórficas en común el servicio de datos. También puede utilizar referencias registros fuera de este contexto, que es cómo se diferencian los dos conceptos.

En la sección siguiente, comenzará a explorar estos conceptos cuando se trabaja con el **propietario** búsqueda.

## <a name="show-the-fields-of-a-record-owner"></a>Mostrar los campos de un propietario del registro

Todas las entidades de Common Data Service incluyen un **propietario** campo. No se puede quitar este campo, no se puede agregar otro y siempre se requiere un valor.

Para mostrar ese campo en el **cuenta** entidad:

1. Abra [este sitio](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
1. En la barra de navegación izquierdo, seleccione **datos** > **entidades**.
1. En la lista de entidades, seleccione **cuenta**.
1. En la esquina superior derecha, abra la lista de filtros (que se establece en **predeterminada** de forma predeterminada) y, a continuación, seleccione **todas**.
1. Desplácese hacia abajo hasta la **propietario** campo aparece.

> [!div class="mx-imgBorder"]
> ![Campo de propietario en la entidad de cuenta](media/working-with-references/owner-field.png)

Puede hacer referencia a un registro de este campo de búsqueda desde el **equipos** entidad o la **usuarios** entidad. No todos los registros de estas entidades tienen permisos para ser un **propietario**; Compruebe los roles compatibles si surge un problema.

Este gráfico muestra una sencilla Galería de **cuentas**, donde el **cuentas** entidad se ha agregado a la aplicación como un origen de datos:

> [!div class="mx-imgBorder"]
> ![Cuentas que se muestra en un control de galería](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> En este tema, los gráficos muestran algunos nombres y otros valores que no forman parte de los datos de ejemplo que se incluye con Common Data Service. Los pasos con precisión muestran cómo configurar los controles para un resultado concreto, pero la experiencia variará en función de los datos de su organización.

Para mostrar el propietario de cada cuenta en la galería, podría verse tentado a usar la fórmula **ThisItem.Owner.Name**. Sin embargo, el campo de nombre en el **equipo** entidad es **nombre de equipo**y el campo de nombre en el **usuario** entidad es **nombre completo**. La aplicación no puede saber qué tipo de búsqueda que está trabajando hasta que se ejecute la aplicación y puede variar entre los registros de la **cuentas** entidad.

Necesita una fórmula que puedan adaptarse a esta variación. También deberá agregar los orígenes de datos para tipos de la entidad que **propietario** podría ser (en este caso, **usuarios** y **equipos**). Agregue estos tres orígenes de datos a la aplicación:

> [!div class="mx-imgBorder"]
> ![Los usuarios, equipos y cuentas de entidades en el panel de datos](media/working-with-references/accounts-datasources.png)

Con estos datos en los orígenes de colocar, use esta fórmula para mostrar el nombre de un usuario o un equipo:

```powerapps-comma
If( IsType( ThisItem.Owner; [@Teams] );
    "Team: " & AsType( ThisItem.Owner; [@Teams] ).'Team Name';
    "User: " & AsType( ThisItem.Owner; [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> ![Cuentas que se muestra en un control de galería con el campo propietario mostrado](media/working-with-references/accounts-displayowner.png)

En esta fórmula, el **IsType** función pruebas la **propietario** campo contra la **equipos** entidad. Si es de ese tipo de entidad, el **AsType** función lo convierte a un **equipo** registro. En este momento, puede tener acceso a todos los campos de la **equipos** entidad, incluidos **nombre equipo**, mediante el uso de *. Campo* notación. Si **IsType** determina que el **propietario** no es un registro en el **equipos** entidad, ese campo debe ser un registro en el **usuarios** entidad porque el **propietario** campo es obligatorio (no puede ser *en blanco*).

Usa el [operador de desambiguación global](functions/operators.md#disambiguation-operator) para **[@Teams]** y **[@Users]** para asegurarse de que está usando el tipo de entidad global. Ya no lo necesita en este caso, pero es un buen hábito al formulario. Relaciones uno a varios a menudo entran en conflicto en el ámbito de registro de la galería, y esta práctica evita esa confusión.

Para usar los campos de una referencia de registro, primero debe usar el **AsType** función para convertirlo en un tipo de entidad concreto. No se puede obtener acceso a los campos directamente desde el **propietario** campo porque el sistema no sabe qué tipo de entidad que desea usar.

El **AsType** función devuelve un error si el **propietario** campo no coincide con el tipo de entidad que se solicita, por lo que puede usar el **IfError** función para simplificar esta fórmula. En primer lugar, active la característica experimental **administración de errores de nivel de fórmula**:

> [!div class="mx-imgBorder"]
> ![Conmutador experimental para activar la administración de errores de nivel de fórmula](media/working-with-references/accounts-iferror.png)

A continuación, reemplace la fórmula anterior por este otro:

```powerapps-comma
IfError(
    "Team: " & AsType( ThisItem.Owner; [@Teams] ).'Team Name';
    "User: " & AsType( ThisItem.Owner; [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>Filtrar por propietario

Enhorabuena: ha terminado el aspecto más difícil de trabajar con una referencia de registro. Otros casos de uso son más sencillas porque no acceden a los campos del registro. Como un caso puntual, realizar el filtrado, que se explorará en esta sección.

Agregar un **cuadro combinado** controlar por encima de la galería y establezca estas propiedades del nuevo control:

- **elementos**: `Users`
- **SelectMultiple**: `false`

> [!div class="mx-imgBorder"]
> ![Agregar control de cuadro combinado por encima de la galería con la propiedad elementos en los usuarios](media/working-with-references/filter-insert-combobox.png)

Para filtrar la Galería por un usuario específico seleccionado de este cuadro combinado, establezca la galería **elementos** fórmula para la propiedad.

```powerapps-comma
Filter( Accounts; Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![Galería filtrada según el valor establecido en el control de cuadro combinado](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> Las instrucciones de este tema son exactas si seguir exactamente los pasos. Sin embargo, se produce un error en cualquier fórmula que hace referencia a un control por su nombre si el control tiene un nombre diferente. Si elimina y agregar un control del mismo tipo, el número al final del nombre del control de cambios. Para cualquier fórmula que muestra un error, confirme que contiene los nombres de todos los controles correctos.

No es necesario usar **IsType** o **AsType** porque compara las referencias de registros para otras referencias a registros o registros completos. La aplicación conoce el tipo de entidad de **ComboBox1.Selected** porque se deriva el **usuarios** entidad. Las cuentas para el que el propietario es un equipo no coincide con el criterio de filtro.

Puede obtener un poco más elegante que admiten el filtrado por un usuario o un equipo.

1. Liberar algo de espacio en la parte superior de la pantalla al cambiar el tamaño de la galería y mover el cuadro combinado, inserte un [ **Radio** control](controls/control-radio.md) por encima de la galería y, a continuación, establezca estas propiedades para el nuevo control:

    - **elementos**: `[ "All"; "Users"; "Teams" ]`
    - **Diseño**: `Layout.Horizontal`

1. Para el **cuadro combinado** , establezca esta propiedad (si el cuadro combinado desaparece, seleccione **usuarios** en el control de radio):

    - **visible**: `Radio1.Selected.Value = "Users"`

1. Copie y pegue el **cuadro combinado** controlar, mueva la copia directamente con respecto al original y, a continuación, establezca estas propiedades para la copia:

    - **elementos**: `Teams`
    - **visible**: `Radio1.Selected.Value = "Teams"`

    La aplicación mostrará solo un cuadro combinado a la vez, en el estado del control de radio de función. Dado que son directamente encima de ellos, parecen ser el mismo control que cambia su contenido.

1. Por último, establezca el **elementos** propiedad de la **galería** control en esta fórmula:

    ```powerapps-comma
    Filter( Accounts;
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Galería filtrada que muestra todos los registros o un usuario o equipo específico](media/working-with-references/filter-combobox.png)

Con estos cambios, puede mostrar todos los registros o filtrar a partir de un usuario o un equipo:

> [!div class="mx-imgBorder"]
> ![animación que muestra resultados filtrados diferentes según el control de radio y combinado cuadros](media/working-with-references/filter-allthree.gif)

La fórmula es totalmente delegable. La parte que está comparando los valores de botón de opción es una constante en todos los registros y se evalúa antes de que el resto del filtro se envía a Common Data Service.

Si desea filtrar según el tipo de propietario, puede usar el **IsType** función, pero no del aún puede delegar:

> [!div class="mx-imgBorder"]
> ![Filtrar por tipo de propietario mediante IsType](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>Actualizar el propietario mediante la revisión

Puede actualizar el **propietario** campo en la misma manera que cualquier otra búsqueda. Para establecer el propietario de la cuenta seleccionada actualmente en el primer equipo:

```powerapps-comma
Patch( Accounts; Gallery1.Selected; { Owner: First( Teams ) } )
```

Este enfoque no es diferente de una búsqueda normal porque la aplicación conoce el tipo de **primero (equipos)**. Si desea que el primer usuario en su lugar, reemplace esa parte con **primero (usuarios)**. El **Patch** función sabe que la **propietario** campo se puede establecer en cualquiera de estos dos tipos de entidad.

Para agregar esta funcionalidad a la aplicación:

1. En el **vista de árbol** panel, seleccione el **Radio** control y los dos **cuadro combinado** controles al mismo tiempo.

1. En el menú de puntos suspensivos, seleccione **copiar estos elementos**:

    > [!div class="mx-imgBorder"]
    > ![Copia de varios controles mediante la vista de árbol](media/working-with-references/patch-copy.png)

1. En el mismo menú, seleccione **pegar**:

    > [!div class="mx-imgBorder"]
    > ![Pegado de varios controles mediante la vista de árbol](media/working-with-references/patch-paste.png)

1. Mueva los controles copiados a la derecha de la Galería:

    > [!div class="mx-imgBorder"]
    > ![Mover controles copiados a la derecha de la Galería](media/working-with-references/patch-position.png)

1. Seleccione el texto copiado **Radio** controlar y, a continuación, cambiar estas propiedades:

    - Elementos: `[ "Users"; "Teams" ]`
    - Valor predeterminado: `If( IsType( Gallery1.Selected.Owner; Users ); "Users"; "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![Quita la opción todos del control de radio](media/working-with-references/patch-noall.png) 

1. En el **Radio** control, seleccione **usuarios** para que el **cuadro combinado** control que enumera los usuarios está visible.

1. Seleccione el visible **cuadro combinado** y, a continuación, establezca el **DefaultSelectedItems** propiedad en esta fórmula:

    ```powerapps-comma
    If( IsType( Gallery1.Selected.Owner; Users );
        AsType( Gallery1.Selected.Owner; Users );
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer la propiedad Default para el cuadro combinado de los usuarios](media/working-with-references/patch-default-users.png)

1. En el **Radio** control, seleccione **equipos** para que el **cuadro combinado** control que muestra los equipos está visible.

1. Seleccione el **Radio** control para realizar la selección de la invisible ahora **cuadro combinado** control para los usuarios.

1. Seleccione el visible **cuadro combinado** para que los equipos y, a continuación, establezca su **DefaultSelectedItems** propiedad en esta fórmula:

    ```powerapps-comma
    If( IsType( Gallery1.Selected.Owner; Teams );
        AsType( Gallery1.Selected.Owner; Teams );
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer la propiedad Default para el cuadro combinado de los equipos](media/working-with-references/patch-default-teams.png)

1. Insertar un **botón** controlar, desplácelo bajo el **cuadro combinado** y, a continuación, establezca el botón **texto** propiedad `"Patch Owner"`.

1. Establecer el **OnSelect** propiedad del botón en esta fórmula:

    ```powerapps-comma
    Patch( Accounts; Gallery1.Selected;
        { Owner: If( Radio1_1.Selected.Value = "Users";
                ComboBox1_2.Selected;
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ![Fórmula establecida en el control de botón](media/working-with-references/patch-button.png)

Copiado **Radio** y **cuadro combinado** controles muestran el propietario de la cuenta seleccionada actualmente en la galería. Con los mismos controles, puede establecer el propietario de la cuenta a cualquier equipo o usuario seleccionando el botón:

> [!div class="mx-imgBorder"]
> ![Revisión de animación que muestra de propietario con un usuario o un equipo](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>Mostrar el propietario mediante un formulario

Puede mostrar un **propietario** campo dentro de un formulario mediante la adición de una tarjeta personalizada. Cuando se redactó este documento, no se puede cambiar el valor del campo con un control de formulario.

1. Insertar un **Editar formulario** controlar y, a continuación, cambiar el tamaño y muévalo a la esquina inferior derecha.

1. En el **propiedades** ficha del panel derecho, abrirlo el **origen de datos** lista y, a continuación, seleccione **cuentas**:

    > [!div class="mx-imgBorder"]
    > ![Control de formulario que muestra los campos adicionales con los valores en blanco](media/working-with-references/form-insert.png)  

1. Establezca el formulario **elemento** propiedad `Gallery1.Selected`:

    > [!div class="mx-imgBorder"]
    > ![Control de formulario que muestra los campos adicionales que se rellena a partir del elemento seleccionado en la Galería](media/working-with-references/form-item.png)

1. En el **propiedades** ficha del panel derecho, seleccione **editar campos**.

1. En el **campos** panel, seleccione los puntos suspensivos y, a continuación, seleccione **agregar una tarjeta personalizada**:

    > [!div class="mx-imgBorder"]
    > ![Comando para agregar una tarjeta personalizada](media/working-with-references/form-customcard.png)

    La tarjeta nueva aparece en la parte inferior del control de formulario.

1. Cambiar el tamaño de la tarjeta según sea necesario para mostrar todo el texto:

    > [!div class="mx-imgBorder"]
    > ![Tarjeta personalizada insertada, en blanco](media/working-with-references/form-inserted-customcard.png)

1. Insertar un **etiqueta** en la tarjeta personalizada y, a continuación, establezca la etiqueta **texto** propiedad a la fórmula que usó en la Galería:

    ```powerapps-comma
    If( IsType( ThisItem.Owner; Teams );
        "Team: " & AsType( ThisItem.Owner; Teams ).'Team Name';
        "User: " & AsType( ThisItem.Owner; Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![Tarjeta personalizada que muestra el campo propietario de un control label](media/working-with-references/form-displayowner.png)

Para cada selección en la galería, más campos de la cuenta, incluido el propietario del registro, aparecen en el formulario. Si cambia el propietario mediante el uso de la **revisión** button, el control de formulario también muestra dicho cambio.

> [!div class="mx-imgBorder"]
> ![Animación que muestra el control de formulario responder a cambios en la Galería](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>Mostrar los campos de un cliente

En Common Data Service, el **cliente** campo de búsqueda es otra búsqueda polimórfico que es muy similar a **propietario**.

**Propietario** está limitado a uno por cada entidad, pero las entidades puede incluir cero, uno o más **cliente** los campos de búsqueda. El **contactos** entidad del sistema incluye el **nombre de la compañía** campo, que es un **cliente** campo de búsqueda:

> [!div class="mx-imgBorder"]
> ![Póngase en contacto con la entidad que se muestra el campo de nombre de la empresa como un tipo de datos de cliente que no es necesario](media/working-with-references/customer-companyname.png)

Puede agregar más **cliente** los campos de búsqueda a una entidad seleccionando el **cliente** tipo de datos para un campo nuevo:

![Tipo de datos de cliente en la lista de tipos de datos al crear un campo](media/working-with-references/customer-datatype.png)

Un **cliente** puede hacer referencia a un registro de campo de búsqueda desde el **cuentas** entidad o la **contactos** entidad. Deberá usar el **IsType** y **AsType** functions con estas entidades, así que ahora es un buen momento para agregarlos como orígenes de datos (puede dejar **equipos** y **a los usuarios**  en su lugar):

> [!div class="mx-imgBorder"]
> ![Las cuentas, las entidades de los equipos, usuarios y contactos en el panel de datos](media/working-with-references/customer-datasources.png)

El tratamiento de la **cliente** y **propietario** campos son tan similares que literalmente se puede copiar la aplicación (**archivo** > **Guardar como**y, a continuación, especifique un nombre diferente) y realice estas sustituciones simple:

| Location | **Propietario** ejemplo | **Cliente** ejemplo |
|----------|-----------|------------------|
| de principio a fin | **Owner** | **"Customer Name"** |
| de principio a fin | **Usuarios** | **Cuentas** |
| de principio a fin | **Teams** | **Contactos** |
| La galería **elementos** propiedad | **Cuentas** | **Contactos** |
| De forma **elementos** propiedad | **Cuentas** | **Contactos** |
| El primer argumento de **revisión**<br>en el botón **Alseleccionar** propiedad | **Cuentas** | **Contactos** |
| Filtrar del radio **elementos** propiedad | **[&nbsp;"All";&nbsp;"Users"&nbsp;"Equipos"&nbsp;]** | **[&nbsp;"All";&nbsp;"Accounts";&nbsp;"Contacts"&nbsp;]** |
| Revisión del radio **elementos** propiedad | **[ "Users"; "Teams" ]** | **["Accounts"; "Contacts"]** |
| Del cuadro combinado **Visible** propiedad | **"Usuarios"** y **"Equipos"** | **"Cuentas"** y **"Contacts"** |

Por ejemplo, la nueva galería debe tener esto **elementos** propiedad:

```powerapps-comma
Filter( Contacts;
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> ![Aplicación de cliente derivado de la aplicación de propietario con cambios sencillos que se aplica](media/working-with-references/customer-simple-update.png)

Dos diferencias importantes entre **cliente** y **propietario** requieren una actualización de las fórmulas dentro de la galería y el formulario:

1. Relaciones uno a varios entre **cuentas** y **contactos** tienen prioridad cuando se hace referencia a estos tipos de entidad por su nombre. En lugar de **cuentas**, utilice  **\[ \@cuentas]**; en lugar de **contactos**, utilice  **\[ \@ Contactos]**. Mediante el uso de la [operador de desambiguación global](functions/operators.md#disambiguation-operator) asegurarse de que está haciendo referencia al tipo de entidad en **IsType** y **AsType**. Este problema solo existe en el contexto de registro de la galería y controles de formulario.

1. El **propietario** campo debe tener un valor, pero **cliente** los campos pueden ser *en blanco*. Para mostrar el resultado correcto sin un nombre de tipo, de pruebas para este caso con el [ **IsBlank** función](functions/function-isblank-isempty.md)y mostrar una cadena vacía en su lugar.

Ambos cambios están en la misma fórmula, que aparece en la tarjeta personalizada en el formulario, así como el **texto** propiedad del control de etiqueta de la Galería:

```powerapps-comma
If( IsBlank( ThisItem.'Company Name' ); "";
    IsType( ThisItem.'Company Name'; [@Accounts] );
        "Account: " & AsType( ThisItem.'Company Name'; [@Accounts] ).'Account Name';
    "Contact: " & AsType( ThisItem.'Company Name'; [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![Actualizar a la propiedad Text del control de etiqueta del subtítulo en la Galería](media/working-with-references/customer-update.png)

Con estos cambios, puede ver y cambiar la **nombre de la compañía** campo el **contactos** entidad:

> [!div class="mx-imgBorder"]
> ![Animación que muestra el cambio de selección en la lista de contactos en función de control de galería de realizar cambios en los demás controles y formularios](media/working-with-references/customer-allthree.gif)

> [!NOTE]
> Cuando se redactó este documento, **cliente** búsquedas tienen estas limitaciones:
>
> - No se puede filtrar una lista basada en un registro específico en el **contactos** o **cuentas** entidades. El control de botón de opción de filtro en el ejemplo anterior no funcionará.
> - El campo de solo cliente que está trabajando es definido por el sistema **nombre de la compañía** en el **contactos** entidad, que se usó en el ejemplo anterior. Aún no se admite la adición de un campo de cliente personalizada.
> - No se puede borrar el campo cliente mediante el uso de **Patch** establecerlo en *en blanco*.

## <a name="understand-regarding-lookup-fields"></a>Comprender sobre los campos de búsqueda

El **sobre** campo de búsqueda un poco diferente a las que ya ha trabajado con en este tema. Comenzará aplicando los patrones que en este tema se ha descrito anteriormente y, a continuación, obtendrá información sobre otros trucos.

Puede iniciar simplemente con el **Faxes** entidad. Esta entidad tiene un polimórfico **referente a** campo de búsqueda, que puede hacer referencia a **cuentas**, **contactos**y otras entidades. Puede tomar la aplicación **clientes** y modifíquelo para **Faxes**:

| Location | **Cliente** ejemplo | **Faxes** ejemplo |
|----------|-----------|------------------|
| de principio a fin | **"Customer Name"** | **Regarding** |
| La galería **elementos** propiedad | **Contactos** | **Faxes** |
| De forma **elementos** propiedad | **Contactos** | **Faxes** |
| El primer argumento de **revisión**<br> en el botón **Alseleccionar** propiedad | **Contactos** | **Faxes** |

De nuevo, deberá agregar un origen de datos: esta vez para **Faxes**. En el **vista** ficha, seleccione **orígenes de datos**:

> [!div class="mx-imgBorder"]
> ![Panel de datos que muestra las entidades de las cuentas, los equipos, usuarios, contactos y Faxes](media/working-with-references/faxes-datasources.png)

Una diferencia importante para **referente a** es que no se limita a **cuentas** y **contactos**. De hecho, la lista de entidades es extensible con entidades personalizadas. La mayoría de la aplicación puede dar cabida a este punto sin modificaciones, pero debe actualizar la fórmula para la etiqueta en la galería y el formulario:

```powerapps-comma
If( IsBlank( ThisItem.Regarding ); "";
    IsType( ThisItem.Regarding; [@Accounts] );
        "Account: " & AsType( ThisItem.Regarding; [@Accounts] ).'Account Name';
    IsType( ThisItem.Regarding; [@Contacts] );
        "Contacts: " & AsType( ThisItem.Regarding; [@Contacts] ).'Full Name';
    ""
)
```

> [!div class="mx-imgBorder"]
> ![Propiedad de texto actualizada para el control de subtítulo para con respecto a las búsquedas](media/working-with-references/regarding-label.png)

Después de realizar estos cambios, se trabaja con el **referente a** búsqueda como lo hizo el **propietario** y **cliente** búsquedas:

> [!div class="mx-imgBorder"]
> ![Animación que se muestran los cambios en los Faxes en función de control de galería de impulsar las actualizaciones a los otros controles y formularios](media/working-with-references/regarding-allthree.gif)

> [!NOTE]
> Cuando se redactó este documento, **sobre** búsquedas tienen estas limitaciones:
>
> - No se puede filtrar una lista basada en un registro específico. El control de botón de opción de filtro en el ejemplo anterior no funcionará.
> - No se puede borrar el campo referente a mediante el uso de **Patch** establecerlo en *en blanco*.

## <a name="understand-regarding-relationships"></a>Comprender sobre las relaciones

**Referente a** difiere **propietario** y **cliente** porque el primero implica una relación varios a uno. Por definición, una relación uno a varios inversa permite escribir **primero (cuentas). Faxes**.

Vamos a realizar copias de seguridad y examine las definiciones de entidad. En Common Data Service, las entidades como **Faxes**, **tareas**, **correos electrónicos**, **notas**, **llamadas telefónicas**, **Letras**, y **charlas** se designan como [ *actividades*](../../developer/common-data-service/activity-entities.md). También puede crear sus propios [entidades de actividad personalizada](../../developer/common-data-service/custom-activities.md). Al ver o crear una entidad de actividad, sus valores aparecen en **más configuraciones**:

![Configuración de la entidad de actividad al crear una entidad](media/working-with-references/activity-entitytype.png)

Otras entidades pueden estar relacionados con una entidad de actividad si se encuentran habilitadas como un *tarea actividad* en la configuración de la entidad. **Cuentas**, **contactos**, y por lo que se designan muchas otras entidades estándares (de nuevo, en **más configuraciones**):

![Configuración de la tarea de actividad al crear una entidad](media/working-with-references/activity-entityuse.png)

Todas las entidades de actividad y las entidades de la tarea de la actividad tienen una relación implícita. Si cambia el filtro de **todas** en la parte superior de la pantalla, seleccione el **Faxes** entidad y, a continuación, seleccione el **relaciones** pestaña todas las entidades que pueden ser el destino de un  **Referente a** búsqueda aparecen:

> [!div class="mx-imgBorder"]
> ![Relaciones de la entidad de los Faxes que se muestra con respecto a las relaciones de varios a uno](media/working-with-references/activity-manytoone.png)

Si se muestran las relaciones para el **cuentas** entidad, todas las entidades que pueden ser una fuente de un **referente a** aparecen el campo de búsqueda:

> [!div class="mx-imgBorder"]
> ![Relaciones de la entidad de cuenta que se muestra con respecto a las relaciones uno a varios](media/working-with-references/activity-onetomany.png)

¿Qué significa todo esto?

- Al escribir fórmulas, debe tener en cuenta que la lista de entidades de actividad no es fijo, y puede crear sus propios. La fórmula debe controlar adecuadamente una entidad de actividad que esperaba.
- Las actividades y tareas de la actividad tienen una relación uno a varios. Puede solicitar fácilmente todos los faxes que se relacionan con una cuenta.

Para explorar este concepto en la aplicación:

1. Agregue otra pantalla:

    > [!div class="mx-imgBorder"]
    > ![Insertar una pantalla en blanco](media/working-with-references/activitypointer-newscreen.png)

1. Insertar un control de galería, cambiar su tamaño y, a continuación, muévalo a la izquierda de la pantalla.

1. En el **propiedades** pestaña de la derecha, panel de la galería, especifique **elementos** a **cuentas**:

    > [!div class="mx-imgBorder"]
    > ![Configurar los elementos a las cuentas en el panel de propiedades](media/working-with-references/activitypointer-accounts.png)

1. Establece el diseño de la galería en **título**y, a continuación, establezca el campo de título en **nombreCuenta**:

    > [!div class="mx-imgBorder"]
    > ![Establecer diseño al título para el control de galería en el panel de propiedades](media/working-with-references/activitypointer-account-name.png)

1. Agregue una galería de segundo, cambiar su tamaño y, a continuación, muévalo a la derecha de la pantalla.

1. Establecer la nueva galería **elementos** propiedad `Gallery2.Selected.Faxes`.

    Este paso, devuelve la lista filtrada de faxes para una cuenta determinada:

    > [!div class="mx-imgBorder"]
    > ![Propiedad de conjunto de elementos para los faxes en función de control de galería](media/working-with-references/activitypointer-faxes.png)

1. Establece el diseño de la galería en **título y subtítulo**y, a continuación, establezca el campo de título para mostrar el **asunto** campo (que podría estar en minúsculas **asunto**):

    > [!div class="mx-imgBorder"]
    > ![Establecimiento del título para el campo de asunto](media/working-with-references/activitypointer-subject.png)

Al seleccionar un elemento en la lista de cuentas, la lista de faxes muestra faxes de esa cuenta.

> [!div class="mx-imgBorder"]
> ![Animación se muestra la selección en la Galería de cuentas impulsando la lista de faxes](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>Entidad de actividad

Como se describe en la sección anterior, puede mostrar todos los faxes de una cuenta. Sin embargo, también puede mostrar todas las actividades para una cuenta, incluidos los faxes, llamadas telefónicas, mensajes de correo electrónico y otras interacciones.

Para el último escenario, se usa el **actividad** entidad. Puede mostrar esta entidad activando **todas** en la esquina superior derecha para quitar el filtro de la lista de entidades:

> [!div class="mx-imgBorder"]
> ![Lista de entidades que muestra la entidad de actividad](media/working-with-references/activitypointer-entity.png)

El **actividad** entity es especial. Cada vez que se agregue un registro a la **Faxes** entidad, el sistema crea también un registro en el **actividad** entidad con los campos que son comunes a todas las entidades de actividad. De esos campos, **asunto** es uno de los más interesantes.

Puede mostrar todas las actividades cambiando sólo una línea en el ejemplo anterior. Reemplace `Gallery2.Selected.Faxes` con `Gallery2.Selected.Activities`:

> [!div class="mx-imgBorder"]
> ![Cambio de propiedad de los elementos de la Galería de segundo, cambiar de faxes a actividades](media/working-with-references/activitypointer-gallery.png)

Registros proceden de la **actividad** entidad, pero, sin embargo, puede usar el **IsType** función para identificar qué tipo de actividad son. Una vez más, antes de usar **IsType** con un tipo de entidad, debe agregar el origen de datos:

> [!div class="mx-imgBorder"]
> ![Panel de datos que muestra todas las entidades necesarias para la función IsType](media/working-with-references/activity-datasources.png)

Con esta fórmula, puede mostrar el tipo de registro en un control label dentro de la Galería:

```powerapps-comma
If( IsType( ThisItem; [@Faxes] ); "Fax";
    IsType( ThisItem; [@'Phone Calls'] ); "Phone Call";
    IsType( ThisItem; [@'Email Messages'] ); "Email Message";
    IsType( ThisItem; [@Chats] ); "Chat";
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![Establezca la propiedad de texto en la fórmula para mostrar la información de los faxes, llamadas telefónicas y otras actividades](media/working-with-references/activitypointer-type.png)

También puede usar **AsType** para tener acceso a los campos del tipo específico. Por ejemplo, esta fórmula determina el tipo de cada actividad y cuando, para las llamadas de teléfono, se muestra la dirección de número y llamada de teléfono desde el **números de teléfono** entidad:

```powerapps-comma
If( IsType( ThisItem; [@Faxes] ); "Fax";
    IsType( ThisItem; [@'Phone Calls'] );
       "Phone Call: " &
       AsType( ThisItem; [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem; [@'Phone Calls'] ).Direction & ")";
    IsType( ThisItem; [@'Email Messages'] ); "Email Message";
    IsType( ThisItem; [@Chats] ); "Chat";
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![Propiedad texto expandido con más información para una llamada de teléfono](media/working-with-references/activitypointer-phonecall.png)

Como resultado, la aplicación muestra una lista completa de las actividades. El **asunto** campo aparece para todos los tipos de actividades, si la fórmula las tiene en cuenta o no. Para los tipos de actividades que conozca, puede mostrar sus nombres de tipo y específicos del tipo de información sobre cada actividad:

> [!div class="mx-imgBorder"]
> ![Completar la pantalla que muestra información para los diferentes tipos de actividades](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>Notas de la entidad

Hasta ahora, todos los **referente a** ejemplos se basaban en las actividades, pero el **notas** entidad representa otro caso.

Cuando se crea una entidad, puede permitir que los datos adjuntos:

![Habilitación de los datos adjuntos y las notas al crear una entidad](media/working-with-references/notes-entity.png)

Si selecciona esta casilla, creará un **referente a** relación con la **notas** entidad, como en este gráfico se muestra para el **cuentas** entidad:

> [!div class="mx-imgBorder"]
> ![Entidad de la cuenta que muestra la relación a Notes a través de una relación uno a varios](media/working-with-references/notes-relationships.png)

Además de esta diferencia, utiliza el **referente a** búsqueda de la misma manera en que use las actividades. Las entidades que están habilitadas para los datos adjuntos tienen una relación uno a varios con **notas**, como en este ejemplo:

`First( Accounts ).Notes`

> [!NOTE]
> Cuando se redactó este documento, el **referente a** búsqueda no está disponible para el **notas** entidad. No se puede leer o filtro en función de la **referente a** campo y no se puede establecer el campo mediante el uso de **revisión**.
>
> Sin embargo, el orden inverso **notas** relación uno a varios está disponible, por lo que puede filtrar una lista de notas de un registro que está habilitado para los datos adjuntos. También puede usar el [ **relacionar** ](functions/function-relate-unrelate.md) función para agregar una nota a un registro **notas** tabla, pero la nota se debe crear en primer lugar, como en este ejemplo:
>
>`Relate( ThisItem.Notes; Patch( Notes; Defaults( Notes ); { Title: "A new note" } ) )`

## <a name="activity-parties"></a>Grupos de actividad

Cuando se redactó este documento, las aplicaciones de lienzo no son compatibles con los grupos de actividad.
