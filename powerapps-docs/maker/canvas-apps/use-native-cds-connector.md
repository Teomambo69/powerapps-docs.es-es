---
title: Actualizar para usar el conector de Common Data Service nativo | Microsoft Docs
description: ''
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e77bf1304ac7d1083348dce18d7d78189dfef306
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845385"
ms.PowerAppsDecimalTransform: true
---
# <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service y la mejor experiencia de origen de datos

## <a name="overview"></a>Información general

Si ha creado una aplicación de lienzo con un conector de Common Data Service antes del 2019 de noviembre, es posible que no tenga la ventaja de la versión más reciente del Common Data Service. 

La opción **mejorar la experiencia del origen de datos y las vistas de Common Data Service** tiene las siguientes ventajas:

1. Mejoras en la velocidad significativa.
2. Mayor confiabilidad.
3. Acceso a las **vistas** de Common Data Service y **atributos de campo de archivo e imagen**.

La opción **mejorar la experiencia del origen de datos y las vistas de Common Data Service** aparece en la sección Configuración avanzada:

![Mejorar la experiencia del origen de datos y las vistas de Common Data Service](media/use-native-cds-connector/improved-data-source-setting.png)

Los **datos relacionales, los conjuntos de opciones y otras características nuevas de Common Data Service** aparecen ahora en la sección características desusadas.

## <a name="how-do-i-upgrade"></a>¿Cómo actualización?

Para actualizar la aplicación, revise la configuración de las características y, a continuación, siga las instrucciones que se indican a continuación:

### <a name="improve-data-source-experience-and-common-data-service-views-is-on"></a>*Mejorar la experiencia del origen de datos y las vistas de Common Data Service* está activada:

Ya ha convertido la aplicación de lienzo para usar esta característica, o bien ha iniciado una aplicación con la configuración predeterminada *activada* para esta característica. No es necesario realizar más acciones. 

También puede habilitar la característica de **selección de columnas explícita** :

![Selección de columnas explícita](media/use-native-cds-connector/explicit-column-selection.png)

> [!NOTE]
> **Mejorar la experiencia de origen de datos y las vistas de Common Data Service** no se admiten en [Power apps para Windows](https://www.microsoft.com/p/power-apps/9nblggh5z8f3). Debe *desactivar esta característica al* usar Power apps para Windows.

### <a name="relational-data-option-sets-and-other-new-features-for-common-data-service-is-off"></a>Los *datos relacionales, los conjuntos de opciones y otras características nuevas de Common Data Service* están desactivadas:

Active la sección *características en desuso* en *Configuración avanzada*.  Si se establece en *OFF*, continúe con las instrucciones siguientes como primer paso en la conversión. 

> [!IMPORTANT]
> Si no ve los **datos relacionales, los conjuntos de opciones y otras características nuevas de Common Data Service** en la *Configuración avanzada*, o si ya está *activado*, omita los pasos siguientes y continúe con la [siguiente sección](#improve-data-source-experience-and-common-data-service-views-is-off).

- **Paso 1**: activar la característica **usar nombres para mostrar** **en**:
    
    1. Active la característica **usar nombres para mostrar** *en*.
    1. Espere a que el monitor de estado termine de analizar la aplicación.
    1. Guarde, cierre y vuelva a abrir la aplicación.
    1. Resuelva todos los errores de fórmula.
    1. Guarde, cierre y vuelva a abrir la aplicación.
    
    *Posibles errores y sugerencias*:
    
    Es posible que algunos de los nombres para mostrar que se muestran recientemente entren en conflicto con los nombres para mostrar de otras entidades, campos o controles. Por ejemplo, puede tener un control y un campo con el mismo nombre. Puede cambiar el nombre del control con un valor único para corregirlo.
    
    Para cualquier conflicto de nombres para mostrar de entidades y campos, puede ver una fórmula que espera una entidad pero que se resuelve en un nombre de campo de ámbito local.

    Use el corchete con un símbolo de **@** para indicar un ámbito global, de modo que se resuelva en la entidad; por ejemplo, **[@entityName]** .
    
    
- **Paso 2**: activar los **datos relacionales, los conjuntos de opciones y otras características nuevas para Common Data Service** y **usar tipos de datos GUID en lugar de** las características de cadenas **en**:
    
    1. Convierta los **datos relacionales, los conjuntos de opciones y otras características nuevas de Common Data Service** característica *en*.
    1. Active **usar tipos de datos de GUID en lugar de** la característica de cadenas *en*.
    1. Espere a que el monitor de estado termine de analizar la aplicación.
    1. Resuelva todos los errores de fórmula.
    1. Guarde, cierre y vuelva a abrir la aplicación.  
    
    *Posibles errores y sugerencias*:
    
    Es posible que se produzcan errores en esta fase si usa un campo de conjunto de opciones o valores de texto GUID codificados de forma rígida.  <br><br> 
    
    - *Valores de conjunto de opciones*: Si usa un campo de conjunto de opciones con un identificador de texto para el valor del conjunto de opciones, use la notación de puntos en su lugar para hacer referencia al valor del conjunto de opciones. Por ejemplo, cambie `Patch(Accounts; OptionSet1 = “12345”)` a `Patch(Accounts; OptionSet.Item1)` donde `Item1` corresponde al valor de `12345`. <br>
    Vea la sección [ejemplos detallados](#detailed-examples) para obtener más información.
    - *GUID*: Si utiliza una cadena de GUID estática como `015e45e1044e49f388115be07f2ee116`, conviértala en una función que devuelva un objeto GUID. por ejemplo `GUID(“015e45e1044e49f388115be07f2ee116”)`. 
    - *Búsquedas*: Si utiliza funciones de búsqueda para obtener valores de búsqueda de primer nivel, como `Lookup(Contacts; ‘contactID’ = ThisItem.ContactID”)`, considere la posibilidad de usar `ThisItem.PrimaryContacts` (donde PrimaryContacts es el nombre de la entidad).

### <a name="improve-data-source-experience-and-common-data-service-views-is-off"></a>*Mejorar la experiencia de origen de datos y las vistas de Common Data Service* está desactivada:

Use la siguiente instrucción para activar la mejora de la **experiencia del origen de datos y Common Data Service característica vistas** *en*:

1. Quite las conexiones de origen de datos de Common Data Service existentes. 
1. Active *la* característica **mejorar la experiencia del origen de datos y las vistas de Common Data Service** .
1. Agregue la conexión Common Data Service con la nueva experiencia de selección de orígenes de datos.
1. Guarde la aplicación.

> [!NOTE]
> Si la aplicación es muy grande, la adición de las conexiones de origen de datos puede tardar unos minutos. No cierre la aplicación durante este proceso.

## <a name="converting-canvas-apps-with-the-dynamics-365-connector"></a>Conversión de aplicaciones de lienzo con el conector de Dynamics 365

Para convertir la aplicación que usa el conector de Dynamics 365, deberá quitar y agregar las conexiones a los orígenes de datos. Siga los pasos que se indican a continuación para convertir las conexiones a los orígenes de datos.

1. Asegúrese de que la característica **mejorar la experiencia del origen de datos y las vistas Common Data Service** está *activada.*
2. Quite las conexiones de origen de datos de Dynamics 365 existentes.
3. Agregue las conexiones a los orígenes de datos al Common Data Service con la nueva experiencia de selección de orígenes de datos. 

    > [!NOTE] 
    > Si tiene conexiones a otros entornos (distintos de actual), seleccione la categoría *entidad* y, a continuación, la opción *más* (...) para cambiar el entorno. Después, puede seleccionar una entidad de un entorno diferente para agregarla a la aplicación. Las conexiones entre inquilinos no funcionan con el conector nativo mejorado. Tendrá que usar la integración de datos para acceder a los datos entre inquilinos.
4.  Guarde la aplicación.

*Posibles errores y sugerencias*:

Es posible que se produzcan errores al realizar la conversión si: no está utilizando nombres para mostrar, si usa cadenas GUID, o si está usando un campo de conjunto de opciones.

- Si hay conflictos de nombres de control, cambie el nombre del control para que sea diferente y único. 
- En el caso de conflictos de nombres para mostrar de campos y entidades, es posible que vea una fórmula que espera una entidad pero que se resuelve en un nombre de campo con ámbito más local. Use el corchete con un símbolo de *@* para indicar un ámbito global, de modo que se resuelva en la entidad; por ejemplo, **[@entityName]** .
- *Valores de conjunto de opciones*: Si usa un campo de conjunto de opciones con un identificador de texto para el valor del conjunto de opciones, use la notación de puntos en su lugar para hacer referencia al valor del conjunto de opciones. Por ejemplo, cambie `Patch(Accounts; OptionSet1 = “12345”)` a `Patch(Accounts; OptionSet.Item1)` donde `Item1` corresponde al valor de `12345`. <br>
Vea la sección [ejemplos detallados](#detailed-examples) para obtener más información.
- *GUID*: Si usa una cadena de GUID estática como `015e45e1044e49f388115be07f2ee116`, conviértala en una función que devuelva un objeto GUID. por ejemplo `GUID(“015e45e1044e49f388115be07f2ee116”)`. 
- *Búsquedas*: Si usa funciones de búsqueda para obtener valores de búsqueda de primer nivel, como `Lookup(Contacts; ‘contactID’ = ThisItem.ContactID”)`, considere la posibilidad de usar `ThisItem.PrimaryContacts` (donde PrimaryContacts es el nombre de la entidad).
- Para obtener referencias polimórficas, consulte la sección ejemplos detallados a continuación. 

## <a name="detailed-examples"></a>Ejemplos detallados

La conversión de la aplicación para usar los nuevos **conjuntos** de opciones y **dos** tipos de datos de opciones con controles auxiliares puede ser difícil al actualizar una aplicación para usar la nueva característica de *vistas de Common Data Service y la experiencia de orígenes de datos mejorada* .

### <a name="option-sets"></a>Conjuntos de opciones

Los campos de `_myfield` y `_myfield_label` independientes se usaron para un conjunto de opciones anterior. Ahora, hay una única `myfield` que se puede usar tanto para las comparaciones independientes de la configuración regional como para obtener la etiqueta específica de la configuración regional.

#### <a name="removing-and-adding-option-set-data-cards"></a>Quitar y agregar tarjetas de datos de conjunto de opciones

Se recomienda quitar las tarjetas de datos existentes y volver a agregarlas para trabajar con el conjunto de opciones. Por ejemplo, si está trabajando con la entidad de cuenta y la opción de categoría establecida, verá que la propiedad *DataField* de la tarjeta de datos se estableció en `_accountcategorycode_label`. En la lista de campos puede ver que la tarjeta de datos tiene un tipo de *cadena*:

![OptionSet con el nombre de estilo antiguo](./media/use-native-cds-connector/OptionSet-with-old-style-name.png)

Con la nueva característica de vistas de la *experiencia de orígenes de datos y Common Data Service* , ya no verá `_accountcategorycode_label`. Se reemplaza por `accountcategorycode`. La tarjeta ahora está marcada como **personalizada** y verá errores. Quite la tarjeta de datos anterior y agregue la *opción establecida* de nuevo. La nueva tarjeta de datos tiene en cuenta los *conjuntos de opciones* .

![OptionSet con el nombre de estilo antiguo](./media/use-native-cds-connector/OptionSet-with-new-style-name.png)

#### <a name="editing-the-option-set-filter-expressions-to-use-new-syntax"></a>Editar el conjunto de opciones filtrar expresiones para usar la nueva sintaxis

Anteriormente, si quisiera utilizar un valor de conjunto de opciones en una expresión de filtro, tendría que usar el campo *valor* . Por ejemplo:

```powerapps-comma
Filter(Account;'Category Value' = "1")
```

Deberá editar esta fórmula. El identificador de texto del conjunto de opciones ya no se utiliza para el valor. Esta expresión debe actualizarse para que tenga el aspecto siguiente:

```powerapps-comma
Filter(Account; Category= ‘Category (Accounts)’.’Preferred Customer’)
```

' Category (accounts) ' es el nombre de la enumeración que se usa en el campo Category de la entidad accounts. Se trata de un conjunto de opciones local.  Puede leer más sobre los conjuntos de opciones locales y globales aquí: [conjuntos de opciones globales.](https://docs.microsoft.com/powerapps/maker/common-data-service/create-edit-global-option-sets)

#### <a name="editing-option-set-patch-statements-to-use-new-syntax"></a>Opción de edición establecer instrucciones patch para usar la nueva sintaxis

El siguiente es un ejemplo de una instrucción patch anterior del conjunto de opciones:

```powerapps-comma
Patch( Accounts; First(Accounts); { ‘Category Value’: 1 } ) )
```

Tendrá que actualizar las instrucciones para seguir este formulario:

```powerapps-comma
Patch( Accounts; First(Accounts); { Category: ‘Category (Accounts)’.’Preferred Customer’ } )
```

#### <a name="option-set-disambiguation"></a>Desambiguación de conjunto de opciones

Si el nombre para mostrar de un **campo** de conjunto de opciones y el nombre del conjunto de opciones son los mismos, deberá eliminar la ambigüedad de la fórmula. Para seguir usando el ejemplo de código de categoría cuentas, el **@** implica usar el conjunto de opciones, no el campo.

```powerapps-comma
Filter(Accounts; 'Category Code' = [@’Category Code’].'Preferred Customer')
```

### <a name="two-options"></a>Dos opciones

#### <a name="removing-and-adding-two-option-set-data-cards"></a>Quitar y agregar dos tarjetas de datos de conjunto de opciones

Debe quitar las tarjetas de datos existentes y volver a agregarlas para trabajar con los dos conjuntos de opciones. Los tipos de datos se reconocieron anteriormente como booleanos simples, como true/on y false/OFF sin Etiquetas:

![Conjunto de dos opciones: estilo antiguo](./media/use-native-cds-connector/TwoOptionSet-Old.png)

Con la nueva característica de *vistas de Common Data Service y la experiencia de orígenes de datos mejorada* , la tarjeta ahora se marcará como **personalizada** y verá errores.  Quite la tarjeta de datos anterior y agregue la opción establecida de nuevo. Después de agregar, verá un control de edición con dos opciones de forma predeterminada.

![TwoOptionSet-nuevo](./media/use-native-cds-connector/TwoOptionSet-New.png)

Si prefiere el modificador de alternancia para el campo booleano, puede desbloquear la tarjeta de datos y reemplazar el control en la tarjeta de datos con un comando de alternancia.  También deberá establecer estas propiedades en el control de alternancia.

```powerapps-comma
Toggle1.Default = ThisItem.’Do not allow Bulk Emails’
Toggle1.TrueText = ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’
Toggle1.FalseText = ‘Do not allow Bulk Emails (Accounts)’.Allow
DataCard.Value = If( Toggle1.Value;
    ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’;
    ‘Do not allow Bulk Emails (Accounts)’.Allow )
```

![Modificador de alternancia de dos opciones](./media/use-native-cds-connector/TwoOption-Toggle.png)

#### <a name="refining-two-option-patch-statements"></a>Refinamiento de dos instrucciones patch Option

El uso de la función [patch](./functions/function-patch.md) con dos opciones debería funcionar "tal cual". Admite el uso directo de true y false, similar a Boolean. La única diferencia es que si hubiera colocado el valor en un control de etiqueta antes de que mostrara true y false, ahora se mostrarán las dos etiquetas de opción en su lugar.

### <a name="polymorphic-lookups"></a>Búsquedas polimórficas

Las instrucciones siguientes le ayudarán a actualizar su aplicación si hace referencia a campos [polimórficos](working-with-references.md) . Las búsquedas polimórficas, del mismo campo, admiten referencias a un conjunto restringido de varias entidades.  De forma similar a las referencias en otros lenguajes, una referencia de registro es un puntero a un registro específico en una entidad específica. Una referencia de registro incluye la información de la entidad que le permite apuntar a un registro de varias otras entidades diferentes, que difiere de una búsqueda normal que solo puede apuntar a los registros de una entidad.  

#### <a name="access-set-and-filter-on-the-owner-field-of-a-record"></a>Obtener acceso, establecer y filtrar por el campo propietario de un registro

Por ejemplo, el campo propietario de una entidad puede hacer referencia a un registro de la entidad usuarios o de la entidad equipos. El mismo campo de búsqueda en distintos registros podría hacer referencia a los registros de entidades diferentes.
 
![Campo de propietario polimórfico](./media/use-native-cds-connector/Polymorphic1.png)
 
##### <a name="polymorphic-with-filter-and-patch"></a>Polimórficos con filtro y revisión

Las referencias de registro se pueden usar como un registro completo:

```powerapps-comma
Filter( Accounts; Owner = First( Teams ) )
Patch( Accounts; First( Accounts ); { Owner: First( Users ) })
```

##### <a name="polymorphic-with-a-gallery-displaying-owner-name"></a>Polimórficos con una galería que muestra el nombre del propietario

Dado que una referencia puede apuntar a diferentes entidades, debe ser específico. No puede usar **ThisItem.Owner.Name**, ya que el campo Nombre de la entidad **equipo** es **nombre del equipo**y el campo Nombre de la entidad **usuario** es **nombre completo**. Power apps no sabrá a qué tipo de búsqueda se hace referencia, hasta que ejecute la aplicación.

Para corregir este problema: 

1. Agregue los orígenes de datos para los tipos de entidad que el propietario podría ser; en el ejemplo actual, usuarios y equipos).
2. Use funciones adicionales para aclarar su intención.

Hay dos nuevas funciones que puede usar:

- IsType: comprueba si una referencia de registro es de un tipo de entidad determinado.
- Astype: convierte una referencia de registro a un tipo de entidad determinado.

Con estas funciones, puede escribir una fórmula que muestre el nombre del propietario tomado de dos campos con nombre diferentes, en función del tipo de entidad del propietario:

```powerapps-comma
If( IsType( ThisItem.Owner;  [@Teams]); 
    AsType( ThisItem.Owner; [@Teams]).'Team Name'; 
    AsType( ThisItem.Owner; [@Users]).'Full Name' )
```

![Galería con as Type](./media/use-native-cds-connector/Polymorphic-And-AsType-in-Gallery.png)

Se utiliza el operador de desambiguación global para `[@Teams]` y `[@Users]` para asegurarse de que se hace referencia al tipo de entidad global. Aunque en este caso no es necesario, se recomienda que siempre esté claro. Las relaciones uno a varios a menudo entran en conflicto en el ámbito de registro de la galería y esta práctica evita esa confusión.
 
#### <a name="access-and-set-the-company-name-field-a-customer-data-type-of-the-contacts-entity"></a>Acceder y establecer el campo de nombre de la compañía (un tipo de datos de cliente) de la entidad contactos

El campo de búsqueda de clientes es otra búsqueda polimórfica similar a Owner. Solo puede tener un campo propietario por entidad. Sin embargo, una entidad puede incluir cero, uno o más campos de búsqueda de clientes. La entidad sistema de contactos incluye el campo Nombre de la compañía, que es un campo de búsqueda de clientes. Lea [Mostrar los campos de un cliente](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#show-the-fields-of-a-customer) para obtener más detalles.
 
#### <a name="access-and-set-the-regarding-field-of-activity-entities-such-as-faxes-phone-calls-email-messages"></a>Acceder y establecer el campo referente a las entidades de actividad, como faxes, llamadas telefónicas y mensajes de correo electrónico

Las búsquedas polimórficas no se limitan a las cuentas y los contactos. La lista de entidades es extensible con entidades personalizadas. Por ejemplo, la entidad faxes tiene una polimórfico relacionada con el campo de búsqueda, que puede hacer referencia a cuentas, contactos y otras entidades. Si tiene una galería con el origen de datos establecido en faxes, puede usar la siguiente fórmula para mostrar el nombre asociado con el campo de búsqueda referente a. 
 
 ```powerapps-comma
If( IsBlank( ThisItem.Regarding ); "";
    IsType( ThisItem.Regarding; [@Accounts] );
        "Account: " & AsType( ThisItem.Regarding; [@Accounts] ).'Account Name';
    IsType( ThisItem.Regarding; [@Contacts] );
        "Contacts: " & AsType( ThisItem.Regarding; [@Contacts] ).'Full Name';
    "" )
```

![Galería con referente a](./media/use-native-cds-connector/Polymorphic-With-Regarding.png)
 
Lea [sobre los campos de búsqueda](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-lookup-fields) y las [relaciones relacionadas](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-relationships) para obtener más detalles.

#### <a name="access-the-list-of-all-activities-for-a-record"></a>Obtener acceso a la lista de todas las actividades de un registro

En Common Data Service, las entidades como faxes, tareas, correos electrónicos, notas, llamadas telefónicas, cartas y chats se designan como [actividades](https://docs.microsoft.com/powerapps/developer/common-data-service/activity-entities). También puede crear sus propias [entidades de actividad personalizadas](https://docs.microsoft.com/powerapps/developer/common-data-service/custom-activities).

Puede mostrar actividades de un tipo específico (como faxes o impuestos) o todas las actividades asociadas a una entidad como cuenta. Agregue la entidad actividades y otras entidades individuales cuyos datos se van a mostrar en la aplicación Canvas.

Cada vez que se agrega un registro a (por ejemplo, la entidad tareas), se crea un registro en la entidad de actividad con los campos comunes en todas las entidades de actividad. Lea la [entidad actividad](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#activity-entity) para obtener más detalles.

En el ejemplo siguiente se muestra que cuando se selecciona una cuenta, se mostrarán todas las actividades asociadas con esa cuenta:
 
![Actividades polimórficas](./media/use-native-cds-connector/Polymorphic-Activities.png) 
 
Los registros se muestran en la entidad de actividad. Sin embargo, puede seguir usando la función [IsType](./functions/function-astype-istype.md) para identificar el tipo de actividad que son. De nuevo, antes de utilizar IsType con un tipo de entidad, debe agregar el origen de datos necesario.
 
Con esta fórmula, puede mostrar el tipo de registro en un control etiqueta dentro de la Galería:

 ```powerapps-comma
If( IsType( ThisItem; [@Faxes] ); "Fax";
    IsType( ThisItem; [@'Phone Calls'] ); "Phone Call";
    IsType( ThisItem; [@'Email Messages'] ); "Email Message";
    IsType( ThisItem; [@Chats] ); "Chat";
    "Unknown")
```

 ![Polimórficos-IsType](./media/use-native-cds-connector/Polymorphic-IsType.png)

#### <a name="access-the-list-of-notes-for-a-record"></a>Obtener acceso a la lista de notas de un registro

Al crear una entidad, puede habilitar los datos adjuntos. Si activa la casilla para habilitar los datos adjuntos, creará una relación relacionada con la entidad notas, como se muestra en este gráfico para la entidad cuentas:

![Notas-campo](./media/use-native-cds-connector/Notes-Field.png)

##### <a name="filtering"></a>Filtrado

No se puede leer ni filtrar según el campo referente a. Sin embargo, la relación de notas inversas uno a varios está disponible. Para enumerar todas las notas asociadas a una entidad de cuenta, puede usar la fórmula siguiente:

```powerapps-comma
First( Accounts ).Notes
```

##### <a name="patch"></a>Revisión

No se puede establecer el campo notas en una entidad mediante patch. Para agregar un registro a la tabla de notas de una entidad, puede usar la función Relate. Cree primero la nota, como en este ejemplo:

```powerapps-comma
Relate( ThisItem.Notes; Patch( Notes; Defaults( Notes ); { Title: "A new note"; isdocument:'Is Document (Notes)'.No } ) )
```

## <a name="next-steps"></a>Pasos siguientes

- [Referencia sobre fórmulas](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [Referencia sobre controles](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties)

### <a name="see-also"></a>Vea también

[¿Qué es Common Data Service?](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)
