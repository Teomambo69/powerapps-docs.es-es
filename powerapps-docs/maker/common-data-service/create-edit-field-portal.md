---
title: Crear y editar campos para Common Data Service mediante el portal de Power apps | MicrosoftDocs
ms.custom: ''
ms.date: 08/13/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c8788aea002942bae7828411cec298592ea6e872
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78403944"
---
# <a name="create-and-edit-fields-for-common-data-service-using-power-apps-portal"></a>Crear y editar campos para Common Data Service mediante el portal de Power apps

El [portal de Power apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) proporciona una manera sencilla de crear y editar campos de entidad con el Common Data Service.

El portal permite configurar las opciones más comunes, pero ciertas opciones solo se pueden establecer mediante el explorador de soluciones. <br />Más información: 
- [Crear y editar campos para Common Data Service](create-edit-fields.md)
- [Crear y editar campos para Common Data Service mediante el explorador de soluciones de Power apps](create-edit-field-solution-explorer.md)

## <a name="view-fields"></a>Ver campos

1. En el [portal de Power apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **datos** > **entidades** y seleccione la entidad que contiene los campos que desea ver.
2. Con la pestaña **campos** seleccionada, puede seleccionar las siguientes vistas: 

 |Ver|Descripción|
 |--|--|
 |**Todos**| Muestra todos los campos de la entidad|
 |**Administrador**| Muestra solo los campos administrados y estándar de la entidad|
 |**Personal**|Muestra solo los campos personalizados para la entidad|
 |**Predeterminada**|Muestra solo los campos estándar de la entidad|
<!-- TODO: What is the actual difference between All and Default? -->

## <a name="create-a-field"></a>Crear un campo

Mientras ve los campos, en la barra de comandos, haga clic en **Agregar campo** que mostrará el panel **propiedades del campo** .

![Propiedades de campo](media/field-properties.png)

Inicialmente, solo hay tres propiedades de campo disponibles:

 |Propiedad|Descripción|
 |--|--|
 |**Nombre para mostrar**|Texto que se va a mostrar para el campo en la interfaz de usuario.|
 |**Nombre**|El nombre único en todo el entorno. Se generará un nombre basado en el nombre para mostrar que ha escrito, pero puede editarlo antes de guardarlo. Una vez que se crea un campo, no se puede cambiar el nombre, ya que se puede hacer referencia a él en las aplicaciones o el código. El nombre tendrá el prefijo de personalización para el **Common Data Service publicador predeterminado** .|
 |**Tipo de datos**|Controla cómo se almacenan los valores y cómo se les da formato en algunas aplicaciones. Una vez que se guarda un campo, no se puede cambiar el tipo de datos, a excepción de la conversión de campos de texto en campos Autonuméricos.|
 |**Obligatorio**| No se puede guardar un registro sin datos en este campo. |
 |**Búsqueda**| Este campo aparece en búsqueda avanzada y está disponible al personalizar las vistas. |
 |**Calculado o acumulativo**| Use para automatizar cálculos manuales. Use valores, fechas o texto.|
 |**Opciones avanzadas**| Agregue una descripción y especifique una longitud máxima y el modo IME para el campo.

Puede establecer opciones adicionales en función del **tipo de datos**que elija.

## <a name="field-data-types"></a>Tipos de datos de campo

Hay muchos tipos diferentes de campos, pero solo puede crear algunos de ellos. Para obtener más información sobre todos los tipos de campos, vea [tipos de campos y tipos de datos de campo](types-of-fields.md).

Al crear un campo, el **tipo de datos** proporciona las siguientes opciones:

### <a name="text"></a>Texto 

Los campos de texto estándar pueden almacenar hasta 4.000 caracteres. La opción [longitud máxima](#max-length) predeterminada está establecida en un valor inferior que se puede ajustar.

|Tipo de datos|Descripción|
|--|--|
|**Texto**|Un valor de texto que se va a mostrar en un cuadro de texto de una sola línea.|
|**Área de texto**|Un valor de texto que se va a mostrar en un cuadro de texto de varias líneas. Si necesita más de 4.000 caracteres, use un tipo de datos de [texto de varias líneas](#multi-line-field) .|
|**Email**|Un valor de texto que se valida como una dirección de correo electrónico y se representa como un vínculo mailto en el campo. |
|**URL**|Un valor de texto validado como una dirección URL y representado como un vínculo para abrir la dirección URL.|
|**Símbolo de marca de graduación**|Un valor de texto para un símbolo de indicador que mostrará un vínculo que se abrirá para mostrar una comilla para el símbolo del tablero de cotizaciones. |
|**Número**|Un valor de texto validado como un número de teléfono que se representa como un vínculo para iniciar una llamada telefónica mediante Skype. |
|**Autonumeración**|Combinación personalizable de números y letras que el servidor genera automáticamente cada vez que se crea el registro. Más información: [campos Autonuméricos](autonumber-fields.md) |

#### <a name="max-length"></a>Longitud máxima

Los campos que almacenan texto tienen un máximo absoluto según el tipo. La opción **longitud máxima** establece un valor inferior al máximo específico para el entorno. Puede aumentar esta longitud máxima, pero no debe reducirla si tiene datos en el sistema que superan el valor inferior.

### <a name="whole-number"></a>Número entero

Estos campos almacenan datos como un número, pero incluyen diferentes opciones de presentación y validación.

|Tipo de datos|Descripción|
|--|--|
|**Número entero**|Un valor numérico que aparece en un cuadro de texto.|
|**Duration**|Un valor numérico que aparece como una lista desplegable que contiene intervalos de tiempo. Un usuario puede seleccionar un valor de la lista o escribir un valor entero que represente el número de minutos. La duración debe especificarse en el formato: "x minutes", "x hours" o "x Days". Las horas y los días también se pueden escribir con decimales, por ejemplo, "x. x hours" o "x. x Days". Los valores especificados deben expresarse en minutos; los valores de subminuto se redondearán al minuto más cercano.|
|**TimeZone**|Un valor numérico que aparece como una lista desplegable que contiene una lista de zonas horarias.|
|**Idioma**|Un valor numérico que se muestra como una lista desplegable que contiene una lista de los idiomas que se han habilitado para el entorno. Si no se han habilitado otros idiomas, el idioma base será la única opción. El valor guardado es el valor de identificador de configuración regional (LCID) del idioma.|


### <a name="date-time"></a>Fecha/hora

Use estos campos para almacenar valores de hora. Puede almacenar valores tan pronto como 1/1/1753 12:00 AM.

|Tipo de datos|Descripción|
|--|--|
|**Fecha y hora**|Valor de fecha y hora.|
|**Fecha solo**|Valor de fecha y hora que solo muestra una fecha. El valor de hora se almacena como 12:00 AM (00:00:00) en el sistema.|

También puede establecer un **comportamiento** específico para los campos de fecha y hora en las **Opciones avanzadas**.

- **Local del usuario** : muestra los valores convertidos en en la zona horaria local del usuario actual. Este es el valor predeterminado para los nuevos campos.
- **Solo fecha**: este comportamiento está disponible para el tipo de **solo fecha** . Muestra valores sin conversión de zona horaria. Úselo para datos como cumpleaños y aniversarios.
- **Independiente de la zona horaria**: muestra valores sin conversión de zona horaria.

Más información: [Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)

### <a name="other-data-types"></a>Otros tipos de datos

|Tipo de datos|Descripción|
|--|--|
|**Moneda**|Un valor de moneda para las monedas configuradas para el entorno. Puede establecer un nivel de precisión o elegir basar la precisión en una moneda concreta o en una precisión estándar usada por la organización. Más información: [uso de campos de moneda](types-of-fields.md#using-currency-fields)|
|**Número decimal**| Un valor decimal con hasta 10 puntos de precisión. Más información: [usar el tipo de número correcto](types-of-fields.md#using-the-right-type-of-number)|
|**Archivo**| Para almacenar datos binarios.|
|**Número de punto flotante**|Número de punto flotante con un máximo de 5 puntos de precisión. Más información: [usar el tipo de número correcto](types-of-fields.md#using-the-right-type-of-number)|
|**Imagen**|Muestra una sola imagen por registro en la aplicación. Cada entidad puede tener un campo de imagen. Se omitirá el **nombre** que escriba al crear un campo de imagen. Los campos de imagen siempre se denominan "EntityImage".|
|**Búsqueda**| Crea una referencia a un único registro para un tipo de registro de destino único.|
|**Conjunto de opciones de selección múltiple**|Muestra una lista de opciones en las que se puede seleccionar más de una.|
|<a name="multi-line-field"></a>**Texto multilínea**|Un valor de texto que se va a mostrar en un cuadro de texto de varias líneas. Limitado a un máximo de 1.048.576 caracteres. También puede establecer una [longitud máxima](#max-length)inferior. |
|**Conjunto de opciones**|Muestra una lista de opciones en las que solo se puede seleccionar una.|
|**Dos opciones**|Muestra dos opciones donde solo se puede seleccionar una. Elija las etiquetas que se van a mostrar para cada opción. Los valores predeterminados son **sí** y **no**.|

## <a name="save-new-field"></a>Guardar nuevo campo

Una vez que haya establecido las propiedades **nombre para mostrar**, **nombre** y **tipo de datos** , puede hacer clic en **listo** para cerrar el panel **propiedades de campo** . 

Puede continuar editando la entidad y agregando campos adicionales o devolviendo y continuando editando este campo. Los campos no se crearán hasta que haga clic en **Guardar entidad** para guardar todos los cambios en la entidad.

![Botón Guardar entidad](media/save-entity-button.png)

También puede hacer clic en **descartar** para descartar los cambios realizados.
 
## <a name="edit-a-field"></a>Editar un campo

Al ver los campos, seleccione el campo que desea editar. Puede modificar el **nombre para mostrar** , pero no puede cambiar el **nombre** y el tipo de **datos** si ha guardado los cambios en la entidad para agregar el campo.

### <a name="general-properties"></a>Propiedades generales
Cada campo tiene las siguientes propiedades que se pueden cambiar:

|Propiedad|Descripción|
|--|--|
|**Obligatorio**|Cuando se selecciona, no se puede guardar un registro sin datos en este campo.|
|**Búsqueda**|Anule la selección de este campo para los campos de la entidad que no use.  Cuando se puede buscar en un campo, aparece en **búsqueda avanzada** y está disponible al personalizar las vistas. Si anula la selección, se reducirá el número de opciones que se muestran a las personas mediante la búsqueda avanzada.|
|**Descripción**|Se encuentra dentro de **Opciones avanzadas**. Escriba instrucciones para el usuario sobre para qué sirve el campo. Estas descripciones aparecen como información sobre herramientas para el usuario en las aplicaciones controladas por modelos al mantener el mouse sobre la etiqueta del campo.|

> [!NOTE]
> **Hacer que los campos sean necesarios**: tenga cuidado al hacer que los campos sean necesarios. Las personas podrán resistir el uso de la aplicación si no pueden guardar registros porque no tienen la información correcta para entrar en un campo obligatorio. Es posible que los usuarios escriban datos incorrectos para guardar el registro y empezar a trabajar con su trabajo.
>
>**Establecer requisito dinámicamente**: en las aplicaciones controladas por modelos, puede usar reglas de negocios o scripts de formulario para cambiar el nivel de requisito a medida que los datos del registro cambian a medida que las personas trabajan en él. Más información: [crear reglas de negocios y recomendaciones para aplicar lógica en un formulario](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
>
>**Disponibilidad avanzada**de la búsqueda: la búsqueda avanzada solo está disponible actualmente para aplicaciones controladas por modelos mediante el cliente web. La búsqueda avanzada no está actualmente disponible en los clientes de interfaz unificada.

## <a name="calculated-or-rollup"></a>Calculado o acumulativo

Puede establecer un campo personalizado para que sea un campo **calculado** o de **Resumen** . A veces, los campos que no son campos calculados o de resumen se denominan campos *simples* .

### <a name="calculated"></a>Calculado

Con un campo calculado, puede escribir una fórmula para asignar un valor al campo. Estos tipos de datos se pueden establecer en campos calculados: **moneda**, **fecha y hora**, **solo fecha**, **número decimal**, **duración**, **correo electrónico**, **idioma**, **conjunto de opciones de selección múltiple**, conjunto de **Opciones,** **texto**, **área de texto**, símbolo de marca de **graduación**, **zona horaria**, **dos opciones**, **dirección URL**y **número entero**.

Más información: [definir campos calculados para automatizar cálculos manuales](define-calculated-fields.md)

### <a name="rollup"></a>889669

Con un campo ROLLUP puede establecer funciones de agregación que se ejecutarán periódicamente para establecer un valor numérico para el campo. Estos tipos de datos se pueden establecer en campos calculados: **moneda**, **fecha y hora**, **solo fecha**, **número decimal**, **duración**, **idioma**, **zona horaria**y **número entero**.

Más información: [Definir campos consolidados que agregan valores](define-rollup-fields.md)

## <a name="number-field-options"></a>Opciones de campo de número

Cada tipo de campo de número tiene valores mínimos y máximos absolutos. Puede establecer el **valor mínimo** adecuado y el **valor máximo** en estos valores absolutos. Haga esto para que Common Data Service valide los valores de los datos que desea almacenar en el campo.

En el caso de los tipos de datos número de **punto flotante** y **número decimal** , puede especificar un número de **posiciones decimales**.


## <a name="option-set-field-options"></a>Opciones de campo de conjunto de opciones

Los campos que proporcionan un conjunto de opciones pueden incluir su propio conjunto de opciones *locales* o hacer referencia a un conjunto común de opciones *globales* que pueden usarse en varios campos.

El uso de un conjunto de opciones global es útil cuando se encuentra creando el mismo conjunto de opciones para varios campos. Con un conjunto de opciones globales, solo tiene que mantener el conjunto de opciones en un solo lugar. 

Al elegir el tipo de datos conjunto de opciones de **selección múltiple** o **conjunto de opciones** , el diseñador mostrará un conjunto de conjuntos de opciones globales disponibles entre los que elegir y proporcionar la opción de crear un **nuevo conjunto de opciones**.

![Elegir tipo de conjunto de opciones](media/option-set-options.png)

Si elige **nuevo conjunto de opciones** , el comportamiento predeterminado es crear un nuevo conjunto de opciones global.

> [!NOTE]
> Mientras edita las opciones de un nuevo conjunto de opciones globales, los valores de nombre para **Mostrar** y **nombre** son para el conjunto de opciones global en lugar de para el campo. Los valores predeterminados coinciden con los valores de campo, pero puede editarlos mientras edita el conjunto de opciones global para que sea diferente del campo que está creando actualmente.

Si desea crear un conjunto de opciones local, debe hacer clic en **Ver más** y elegir **conjunto de opciones local**.

![Conjunto de opciones local](media/local-option-set.png)

> [!NOTE]
> Si define cada conjunto de opciones como un conjunto de opciones globales, la lista de conjuntos de opciones globales crecerá y podría ser difícil de administrar. Si sabe que el conjunto de opciones solo se usará en un lugar, use un conjunto de opciones local.

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-field"></a>Eliminar un campo

Con el rol de seguridad Administrador del sistema, puede eliminar cualquier campo personalizado que no forme parte de una solución administrada. Si elimina campos, los datos almacenados en los campos se perderán. La única forma de recuperar datos de un campo que se haya eliminado es restaurar la base de datos de un punto anterior a la eliminación del campo.

> [!NOTE]
> Antes de poder eliminar un campo personalizado, debe quitar todas las dependencias que puedan existir en otros componentes de la solución. 

Al [ver los campos](#view-fields), si selecciona un campo personalizado que se puede eliminar de la lista, el comando **eliminar campo** aparece y está habilitado.

![Eliminación de un campo mediante el portal](media/delete-field-portal.png)

Use el comando **eliminar campo** para eliminar el campo. Después de eliminar el campo, debe guardar los cambios en la entidad.

![Guardar entidad después de eliminar el campo](media/delete-field-portal-save-entity.png)

> [!NOTE]
> Si recibe un error relacionado con las dependencias, debe usar el explorador de soluciones para detectar las dependencias. Más información: [comprobar las dependencias de campo](create-edit-field-solution-explorer.md#check-field-dependencies)

## <a name="ime-mode"></a>Modo IME

Cualquiera de los campos que proporcionan la entrada de texto directo tienen un modo IME. El editor de métodos de entrada (IME) se usa para idiomas de Asia oriental como el japonés. Los IME permiten al usuario escribir los miles de caracteres que se usan en los idiomas escritos en Asia oriental mediante un teclado estándar 101-Key.



### <a name="see-also"></a>Vea también  
[Crear y editar campos para Common Data Service](create-edit-fields.md)<br />
[Crear y editar campos para Common Data Service mediante el explorador de soluciones de Power apps](create-edit-field-solution-explorer.md)<br />
[Tipos de campos y tipos de datos de campo](types-of-fields.md)<br />
[Definir campos calculados para automatizar cálculos manuales](define-calculated-fields.md)<br />
[Definir los campos de resumen que agregan valores](define-rollup-fields.md)<br />
[Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)
