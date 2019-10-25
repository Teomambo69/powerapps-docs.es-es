---
title: Funciones astype y IsType en aplicaciones de Canvas | Microsoft Docs
description: Información de referencia, incluida la sintaxis y un ejemplo, para las funciones astype y IsType en las aplicaciones de Canvas
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ecb30a5a452a6ee092ccf9bc9d47f6182ef60ab
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "71993010"
ms.PowerAppsDecimalTransform: true
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>Funciones astype y IsType en aplicaciones de Canvas

Comprueba una referencia de registro para un tipo de entidad específico (**IsType**) y trata la referencia como un tipo específico (**astype**).

## <a name="description"></a>Descripción

Lea [comprender las referencias de registros y las búsquedas polimórficas](../working-with-references.md) para obtener una introducción más amplia y más detalles.

Normalmente, un campo de búsqueda hace referencia a los registros de una entidad determinada. Dado que el tipo de entidad está bien establecido, puede tener acceso a los campos de la búsqueda mediante una notación de puntos simple. Por ejemplo, **primero (cuentas). Contacto principal '. ' Nombre completo '** se dirige de la entidad **accounts** al registro de **contacto principal** de la entidad **Contacts** y extrae el campo de **nombre completo** .

Common Data Service también admite campos de búsqueda polimórficos, que pueden hacer referencia a los registros de un conjunto de entidades, como en estos ejemplos.

| Campo de búsqueda | Puede hacer referencia a |
|--------------|--------------|
| **Propietario** | **Usuarios** o **equipos** |
| **Customer** | **Cuentas** o **contactos** |
| **Sobre** | **Cuentas**, **contactos**, **artículos de conocimientos**, etc. |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

En las fórmulas de canvas-App, puede usar referencias de registros para trabajar con búsquedas polimórficas. Dado que una referencia de registro puede hacer referencia a distintas entidades, no sabe qué campos estarán disponibles cuando escriba una fórmula. El *.* La notación de campo no está disponible. Dichas fórmulas se deben adaptar a los registros que encuentra la aplicación cuando se ejecuta.

La función **IsType** comprueba si una referencia de registro hace referencia a un tipo de entidad concreto. La función devuelve un valor booleano TRUE o FALSE.

La función **astype** trata una referencia de registro como un tipo de entidad concreto, que a veces se conoce como *conversión*. Puede usar el resultado como si fuera un registro de la entidad y, de nuevo, usar *.* Notación de campo para tener acceso a todos los campos de ese registro. Se produce un error si la referencia no es del tipo específico.

Use estas funciones juntas para probar primero el tipo de entidad de un registro y, a continuación, tratarlo como un registro de ese tipo para que los campos estén disponibles:

```powerapps-comma
If( IsType( First( Accounts ).Owner; Users );
    AsType( First( Accounts ).Owner; Users ).'Full Name';
    AsType( First( Accounts ).Owner; Teams ).'Team Name'
)
```

Solo necesita estas funciones si tiene acceso a los campos de una referencia de registro. Por ejemplo, puede usar referencias de registros en la función de [**filtro**](function-filter-lookup.md) sin **IsType** o **astype**:

```powerapps-comma
Filter( Accounts; Owner = First( Users ) )
```

Del mismo modo, puede usar referencias de registros con la función [**patch**](function-patch.md) :

```powerapps-comma
Patch( Accounts; First( Accounts ); { Owner: First( Teams ) } )
```  

Si se usa en un contexto de registro, como en un control de [**Galería**](../controls/control-gallery.md) o de [**edición de formulario**](../controls/control-form-detail.md) , puede que tenga que usar el [operador de desambiguación global](operators.md#disambiguation-operator) para hacer referencia al tipo de entidad. Por ejemplo, esta fórmula sería efectiva en una galería que muestre una lista de contactos en la que **el nombre** de la compañía es una búsqueda de **clientes** :

```powerapps-comma
If( IsType( ThisItem.'Company Name'; [@Accounts] );
    AsType( ThisItem.'Company Name'; [@Accounts] ).'Account Name';
    AsType( ThisItem.'Company Name'; [@Contacts] ).'Full Name'
)
```

En ambas funciones, se especifica el tipo mediante el nombre del origen de datos que está conectado a la entidad. Para que la fórmula funcione, también debe agregar un origen de datos a la aplicación para cualquier tipo que desee probar o convertir. Por ejemplo, debe agregar la entidad **users** como origen de datos si desea usar **IsType** y **astype** con una búsqueda de **propietario** y registros de esa entidad. Solo puede Agregar los orígenes de datos que usa realmente en la aplicación; no es necesario agregar todas las entidades a las que podría hacer referencia una búsqueda.

Si la referencia del registro está *en blanco*, **IsType** devuelve false y **astype** devuelve *Blank*. Todos los campos de un registro *en blanco* estarán *en blanco*.

## <a name="syntax"></a>Sintaxis

**Astype**( *RecordReference*; *EntityType* )

- *RecordReference* : requerido. Una referencia de registro, a menudo un campo de búsqueda que puede hacer referencia a un registro en cualquiera de las varias entidades.
- *EntityType* : requerido. Entidad específica que se va a probar.

**IsType**( *RecordReference*; *EntityType* )

- *RecordReference* : requerido. Una referencia de registro, a menudo un campo de búsqueda que puede hacer referencia a un registro en cualquiera de las varias entidades.
- *EntityType* : requerido. La entidad específica a la que se debe convertir el registro.

## <a name="example"></a>Ejemplo

[Comprender las referencias de registros y las búsquedas polimórficas](../working-with-references.md) contiene extensos ejemplos.

1. Cree una aplicación de lienzo en blanco para tabletas.

1. En la pestaña **Ver** , seleccione **orígenes de datos**y, a continuación, agregue las entidades **contactos** y **cuentas** como orígenes de datos.
    > [!div class="mx-imgBorder"]
    > ![Blank aplicación con dos orígenes de datos: cuentas y contactos ](media/function-astype-istype/contacts-add-datasources.png)

1. Inserte un control **Galería** con una orientación **vertical en blanco** .

    > [!div class="mx-imgBorder"]
    > ![Insert un control galería con un diseño vertical en blanco ](media/function-astype-istype/contacts-customer-gallery.png)

1. En la pestaña **propiedades** situada cerca del lado derecho de la pantalla, establezca la propiedad **elementos** de la galería en **contactos**.

    > [!div class="mx-imgBorder"]
    > ![Set elementos a contactos en el panel Propiedades ](media/function-astype-istype/contacts-customer-datasource.png)

1. Establezca el diseño de la galería en **título y subtítulo**.

    > [!div class="mx-imgBorder"]
    > ![Open el selector de diseño en el panel Propiedades ](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![Set diseño al título y al subtítulo ](media/function-astype-istype/contacts-customer-flyout.png)

1. En el panel **datos** , abra la lista **Title1** y, a continuación, seleccione **nombre completo**.

    > [!div class="mx-imgBorder"]
    > ![Set valor de título ](media/function-astype-istype/contacts-customer-title.png)

1. Seleccione el control etiqueta **Subtitle1** .

    > [!div class="mx-imgBorder"]
    > ![Set valor de subtítulo ](media/function-astype-istype/contacts-customer-subtitle.png)

1. Establezca la propiedad **Text** de **Subtitle1** en esta fórmula:

    ```powerapps-comma
    If( IsBlank( ThisItem.'Company Name' ); "--";
        IsType( ThisItem.'Company Name'; [@Accounts] );
            "Account: " & AsType( ThisItem.'Company Name'; [@Accounts] ).'Account Name';
        "Contact: " & AsType( ThisItem.'Company Name'; [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Screen ya está completo y muestra las cuentas y los contactos que se combinan en la Galería ](media/function-astype-istype/contacts-customer-complete.png)

    El subtítulo de la galería muestra estos valores:
    - "--" si el valor de **"Company name"** está *en blanco*.
    - "Cuenta:" y, a continuación, el campo **nombre de cuenta** de la entidad **cuentas** si el campo Nombre de la **compañía** hace referencia a una cuenta.
    - "Contacto:" y, a continuación, el campo **nombre completo** de la entidad **contactos** si el campo Nombre de la **compañía** hace referencia a un contacto.

    Los resultados pueden diferir de los de este tema, ya que usa datos de ejemplo que se modificaron para mostrar tipos adicionales de resultados.
