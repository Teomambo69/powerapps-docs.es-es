---
title: Funciones AsType y IsType en las aplicaciones de lienzo | Microsoft Docs
description: Información de referencia, incluida la sintaxis y un ejemplo, para las funciones AsType y IsType en las aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 999653159f838e840f7f569aa9953633a6a70065
ms.sourcegitcommit: 93096dfa1aadba77159db1e5922f3d5528eecb7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65986332"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>Funciones AsType y IsType en las aplicaciones de lienzo

Comprueba una referencia del registro para un tipo de entidad concreto (**IsType**) y trata la referencia como un tipo específico (**AsType**).

## <a name="description"></a>Descripción

Lectura [comprender las referencias de registros y búsquedas polimórficas](../working-with-references.md) para una introducción más amplia y más detalles.

Normalmente, un campo de búsqueda hace referencia a los registros de una entidad determinada. Dado que el tipo de entidad es bien establecido, puede acceder a los campos de la búsqueda mediante el uso de una notación de puntos simple. Por ejemplo, **primero (cuentas). " Contacto principal '.' El nombre completo '** recorre desde el **cuentas** entidad a la **contacto principal** registros en el **contactos** entidad y extrae el **nombre completo**  campo.

Common Data Service también admite los campos de búsqueda polimórfica, lo que pueden hacer referencia a los registros de un conjunto de entidades, como en estos ejemplos.

| Campo de búsqueda | Puede hacer referencia a |
|--------------|--------------|
| **Owner** | **Los usuarios** o **equipos** |
| **Customer** | **Cuentas** o **contactos** |
| **Regarding** | **Cuentas**, **contactos**, **artículos de conocimientos**, etcetera. |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

En las fórmulas de la aplicación de lienzo, puede utilizar las referencias del registro para trabajar con búsquedas polimórficas. Dado que una referencia de registro puede hacer referencia a entidades diferentes, no sabe qué campos estarán disponibles al escribir una fórmula. El *. Campo* notación no está disponible. Las fórmulas se deben adaptar a los registros que se encuentra de la aplicación cuando se ejecuta.

El **IsType** función comprueba si una referencia de registro hace referencia a un tipo de entidad concreto. La función devuelve un valor booleano TRUE o FALSE.

El **AsType** función trata una referencia de registro como un tipo de entidad concreto, a veces se denomina *conversión*. Puede usar el resultado como si fuese un registro de la entidad y, de nuevo, use el *. Campo* notación para tener acceso a todos los campos de ese registro. Se produce un error si la referencia no es del tipo específico.

Use estas funciones juntas para probar primero el tipo de entidad de un registro y, a continuación, tratarlo como un registro de ese tipo para que los campos están disponibles:

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

Necesita estas funciones solo si está accediendo a los campos de una referencia de registro. Por ejemplo, puede utilizar referencias de registros en el [ **filtro** ](function-filter-lookup.md) funcionando sin necesidad de **IsType** o **AsType**:

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

De forma similar, puede utilizar referencias de registros con el [ **Patch** ](function-patch.md) función:

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

Si se utilizan en un contexto de registro, por ejemplo, dentro de un [ **galería** ](../controls/control-gallery.md) o [ **Editar formulario** ](../controls/control-form-detail.md) control, es posible que deba usar el [global operador de desambiguación](operators.md#disambiguation-operator) para hacer referencia al tipo de entidad. Por ejemplo, esta fórmula sería eficaz para una galería que muestra una lista de contactos donde **nombre de la compañía** es un **cliente** búsqueda:

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

Para ambas funciones, especifique el tipo a través del nombre del origen de datos que está conectado a la entidad. Para que la fórmula para que funcione, debe agregar también un origen de datos a la aplicación para cualquier tipo que se desea probar o convertir. Por ejemplo, debe agregar el **usuarios** entidad como un origen de datos si desea usar **IsType** y **AsType** con un **propietario** búsqueda y registros de esa entidad. Puede agregar solo los orígenes de datos que utiliza realmente en la aplicación; no es necesario agregar todas las entidades que podría hacer referencia a una búsqueda.

Si la referencia del registro es *en blanco*, **IsType** devuelve FALSE, y **AsType** devuelve *en blanco*. Todos los campos de un *en blanco* registro será *en blanco*.

## <a name="syntax"></a>Sintaxis

**AsType**( *RecordReference*, *EntityType* )

- *RecordReference* : requerido. Una referencia de registro, a menudo un campo de búsqueda que puede hacer referencia a un registro en cualquiera de varias entidades.
- *EntityType* : requerido. La entidad concreta para que se va a probar.

**IsType**( *RecordReference*, *EntityType* )

- *RecordReference* : requerido. Una referencia de registro, a menudo un campo de búsqueda que puede hacer referencia a un registro en cualquiera de varias entidades.
- *EntityType* : requerido. La entidad concreta a la que se debe convertir el registro.

## <a name="example"></a>Ejemplo

[Comprender las referencias de registros y búsquedas polimórficas](../working-with-references.md) contiene ejemplos extensos.

1. Creación de una aplicación de lienzo en blanco para tabletas.

1. En el **vista** ficha, seleccione **orígenes de datos**y, a continuación, agregue el **contactos** y **cuentas** entidades como orígenes de datos.
    > [!div class="mx-imgBorder"]
    > ![Aplicación en blanco con dos orígenes de datos: cuentas y contactos](media/function-astype-istype/contacts-add-datasources.png)

1. Insertar un **galería** controlar con un **en blanco vertical** orientación.

    > [!div class="mx-imgBorder"]
    > ![Inserte un control de galería con un diseño vertical en blanco](media/function-astype-istype/contacts-customer-gallery.png)

1. En el **propiedades** pestaña situada cerca del lado derecho de la pantalla, establezca la galería **elementos** propiedad **contactos**.

    > [!div class="mx-imgBorder"]
    > ![Conjunto de elementos a los contactos en el panel Propiedades](media/function-astype-istype/contacts-customer-datasource.png)

1. Establece el diseño de la galería en **título y subtítulo**.

    > [!div class="mx-imgBorder"]
    > ![Abra el selector de diseño desde el panel de propiedades](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![Diseño de conjunto para el título y subtítulo](media/function-astype-istype/contacts-customer-flyout.png)

1. En el **datos** panel, abra el **Title1** lista y, a continuación, seleccione **nombre completo**.

    > [!div class="mx-imgBorder"]
    > ![Valor de título del conjunto](media/function-astype-istype/contacts-customer-title.png)

1. Seleccione el **subtítulo1** control de etiqueta.

    > [!div class="mx-imgBorder"]
    > ![Valor del conjunto de subtítulo](media/function-astype-istype/contacts-customer-subtitle.png)

1. Establecer el **texto** propiedad de **subtítulo1** en esta fórmula:

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Pantalla ahora está completa mostrando cuentas y contactos mezclado en la Galería](media/function-astype-istype/contacts-customer-complete.png)

    El subtítulo en la galería muestra estos valores:
    - "--" si el **nombre de la compañía** es *en blanco*.
    - "Cuenta:" y, a continuación, el **nombre de la cuenta** arrastrándolo desde la **cuentas** entidad si la **nombre de la compañía** campo hace referencia a una cuenta.
    - "Póngase en contacto con:" y, a continuación, el **nombre completo** arrastrándolo desde la **contactos** entidad si la **nombre de la compañía** campo hace referencia a un contacto.

    Los resultados pueden diferir de los de este tema, porque utiliza datos de ejemplo que se ha modificado para mostrar otros tipos de resultados.
