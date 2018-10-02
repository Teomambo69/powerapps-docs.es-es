---
title: Crear y editar campos para Common Data Service para aplicaciones mediante el portal de PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 05/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-fields-for-common-data-service-for-apps-using-powerapps-portal"></a>Crear y editar campos para Common Data Service para aplicaciones mediante el portal de PowerApps

El [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) proporciona una forma fácil de crear y de editar campos de entidad con Common Data Service para aplicaciones.

El portal permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. <br />Más información: 
- [Creación y edición de campos para Common Data Service para aplicaciones](create-edit-fields.md)
- [Crear y editar campos para Common Data Service para aplicaciones mediante el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md)

## <a name="view-fields"></a>Campos de vista

1. En el [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione el modo de diseño **Basadas en modelos** o **Lienzo**.
2. Seleccione **Datos**  > **Entidades** y seleccione la entidad que contiene los campos que desea ver.
3. Con la pestaña **Campos** seleccionada, seleccione las vistas siguientes: 

 |Vista|Descripción|
 |--|--|
 |**Todo**| Muestra todos los campos para la entidad|
 |**Personalizada**|Muestra solo campos personalizados para la entidad|
 |**Predeterminado**|Muestra solo campos estándar para la entidad|
<!-- TODO: What is the actual difference between All and Default? -->

## <a name="create-a-field"></a>Crear un campo

Mientras ve campos, en la barra de comandos, haga clic en **Agregar campo** que mostrará el panel **Propiedades de campo**.

![Propiedades de campo](media/field-properties.png)


En principio, solo tres propiedades de campo están disponibles:

 |Propiedad|Descripción|
 |--|--|
 |**Nombre para mostrar**|El texto que se muestra para el campo en la interfaz de usuario.|
 |**Nombre**|El nombre único en el entorno. Se generará un nombre para usted basado en el nombre para mostrar que ha especificado, pero puede editarlo antes de guardar. Una vez que un campo se crea el nombre no se puede cambiar, ya que se puede hacer referencia a él en sus aplicaciones o código. El nombre tendrá el prefijo de personalización para su **Editor predeterminado de CDS** antepuesto.|
 |**Tipo de datos**|Controla cómo se almacenan los valores y también cómo se formatean en algunas aplicaciones. Un vez se guarda un campo, no puede cambiar el tipo de datos ya que puede afectar a los datos en la entidad.|

Puede establecer opciones adicionales en función de su elección de **Tipo de datos**.

## <a name="field-data-types"></a>Tipos de datos de campo

Hay muchos diferentes tipos de campos, pero solo puede crear algunos. Para obtener más información sobre todos los tipos de campos, consulte [Tipos de campos y tipos de datos de campo](types-of-fields.md).

Cuando crea un campo, **Tipo de datos** proporciona las siguientes opciones:

### <a name="text"></a>Texto 

Los campos de texto estándar pueden almacenar hasta de 4.000 caracteres. La opción [Longitud máxima](#max-length) predeterminada se establece en un valor menor que puede ajustar.

|Tipo de datos|Descripción|
|--|--|
|**Texto**|Un valor de texto pensado para mostrar en un cuadro de texto de una línea.|
|**Área de texto**|Un valor de texto pensado para mostrar en un cuadro de texto de varias líneas. Si requiere más de 4.000 caracteres, use un tipo de datos [Texto multilínea](#multi-line-field).|
|**Correo electrónico**|Valor de texto validado como dirección de correo electrónico y generado como vínculo mailto en el campo. |
|**Dirección URL**|Valor de texto validado como dirección URL y generado como un vínculo para abrir la dirección URL.|
|**Símbolo del valor**|Un valor del texto para un símbolo de valor que mostrará un vínculo que se abrirá para mostrar una oferta para el símbolo de valor bursátil. |
|**Teléfono**|Valor de texto validado como número de teléfono generado como vínculo para realizar una llamada de teléfono con Skype. |

#### <a name="max-length"></a>Longitud máxima

Los campos que almacenan el texto tienen un máximo absoluto según el tipo. La opción **Longitud máxima** establece un valor menor que el máximo específico del entorno. Puede aumentar esta longitud máxima pero no debería bajarla si tiene datos en el sistema que superen el valor inferior.

### <a name="whole-number"></a>Número entero

Estos campos almacenan datos como número pero incluyen distintas opciones de presentación y validación.

|Tipo de datos|Descripción|
|--|--|
|**Número entero**|Valor de número presentado en un cuadro de texto.|
|**Duración**|Valor de número presentado como lista desplegable que contiene intervalos de tiempo. El usuario puede seleccionar un valor de la lista o escribir un valor entero que represente el número de minutos.|
|**Zona horaria**|Valor de número presentado como lista desplegable que contiene una lista de zonas horarias.|
|**Idioma**|Un valor numérico presentado como lista desplegable con los idiomas que se hayan habilitado para el entorno. Si no se ha activado ningún otro idioma, el idioma base será la única opción. El valor guardado es el valor del Identificador de configuración regional (LCID) del idioma.|


### <a name="date-time"></a>Fecha y hora

Use estos campos para almacenar valores de hora. Puede almacenar valores de hasta 1/1/1753 12:00 AM.

|Tipo de datos|Descripción|
|--|--|
|**Fecha y hora**|Un valor de fecha y hora.|
|**Solo fecha**|Valor de fecha y hora que solo se muestra una fecha. El valor de hora se almacena como 12:00 AM (00:00: 00) en el sistema.|

También puede establecer un **Comportamiento** específico para los campos de fecha y hora en **Opciones avanzadas**.

- **Local del usuario** : Muestra valores convertidos a la zona horaria local del usuario actual. Es el valor predeterminado de nuevos campos.
- **Solo fecha**: Este comportamiento está disponible para el tipo **Solo fecha**. Muestra valores sin conversión de zona horaria. Úselo para datos como cumpleaños y aniversarios.
- **Independiente de la zona horaria**: Muestra valores sin conversión de la zona horaria.

Más información: [Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)

### <a name="other-data-types"></a>Otros tipos de datos

|Tipo de datos|Descripción|
|--|--|
|**Divisa**|Un valor de divisa para divisas configuradas para el entorno. Puede establecer un nivel de precisión o elegir basar la precisión en una divisa específica o una precisión estándar única usada por la organización. Más información: [Usar campos de divisa](types-of-fields.md#using-currency-fields)|
|**Número decimal**| Valor decimal con una precisión de hasta 10 puntos. Más información: [Uso del tipo correcto de número](types-of-fields.md#using-the-right-type-of-number)|
|**Número de punto flotante**|Número de punto flotante con una precisión de hasta 5 puntos. Más información: [Uso del tipo correcto de número](types-of-fields.md#using-the-right-type-of-number)|
|**Imagen**|Muestra una sola imagen por cada registro de la aplicación. Cada entidad puede tener un campo de imagen. El **Nombre** que escriba cuando crea un campo de imagen se omitirá. Los campos de imagen siempre se denominan 'EntityImage'.|
|**Conjunto de opciones multiselección**|Muestra una lista de opciones donde puede seleccionar más de una.|
|<a name="multi-line-field"></a> **Texto multilínea**|Un valor de texto pensado para mostrar en un cuadro de texto de varias líneas. Limitado a un máximo de 1.048.576 caracteres. También puede establecer una [Longitud máxima](#max-length) menor. |
|**Conjunto de opciones**|Muestra una lista de opciones donde solo puede seleccionar una.|
|**Dos opciones**|Muestra dos opciones donde solo puede seleccionar una. Puede elegir las etiquetas que se muestran para cada opción. Los valores predeterminados son **Sí** y **No**.|

## <a name="save-new-field"></a>Guardar nuevo campo

Una vez que ha establecido las propiedades de **Nombre para mostrar**, **Nombre** y **Tipo de datos** puede hacer clic en **Listo** para cerrar el panel **Propiedades de campo**. 

Puede seguir editando la entidad y agregar campos adicionales o volver y seguir editando este campo. Los campos no se crearán hasta que haga clic en **Guardar entidad** para guardar todos los cambios a la entidad.

![Botón Guardar entidad](media/save-entity-button.png)

También puede hacer clic en **Descartar** para descartar los cambios que ha realizado.
 
## <a name="edit-a-field"></a>Editar un campo

Mientras ve campos, seleccione el campo que desea editar. Puede modificar el **Nombre para mostrar** pero no puede cambiar el **Nombre** y **Tipo de datos** si ha guardado cambios en la entidad para agregar el campo.

### <a name="general-properties"></a>Propiedades generales
Cada campo tiene las siguientes propiedades que puede modificar:

|Propiedad|Descripción|
|--|--|
|**Obligatorio**|Cuando selecciona esto, el registro no se puede guardar sin datos en este campo.|
|**Búsqueda**|Anule esta selección para los campos de la entidad que no use.  Cuando un campo permite búsquedas aparece en **Búsqueda avanzada** y está disponible cuando se personalizan las vistas. Si anula esta selección se reducirá el número de opciones mostradas a las personas que usan la búsqueda avanzada.|
|**Descripción**|Encontrado en **Opciones avanzadas**. Escriba instrucciones para indicar al usuario para qué sirve el campo. Estas descripciones aparecen como información sobre herramientas para el usuario en aplicaciones basadas en modelos cuando mantienen el mouse sobre la etiqueta del campo.|

> [!NOTE]
> **Crear campos obligatorios**: Tenga cuidado al crear campos obligatorios. Los usuarios se opondrán al uso de la aplicación si no pueden guardar registros porque carecerán de la información correcta para introducir en un campo obligatorio. Los usuarios pueden especificar datos incorrectos simplemente para guardar el registro y comenzar con su trabajo.
>
>**Establecer requisito dinámicamente**: En aplicaciones basadas en modelo, puede usar reglas de negocio o scripts de formulario para cambiar el nivel de requisito a medida que los datos del registro cambian con el trabajo de los usuarios. Más información: [Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
>
>**Disponibilidad de búsqueda avanzada**: Búsqueda avanzada actualmente solo está disponible para aplicaciones basadas en modelo que utilizan el cliente web. Búsqueda avanzada no está disponible para clientes de la interfaz unificada.

## <a name="calculated-or-rollup"></a>Calculado o consolidado

Puede establecer un campo personalizado como campo **Calculado** o **Consolidado**. Los campos que no son campos calculados o consolidados a veces se denominan campos *sencillos*.

### <a name="calculated"></a>Calculado

Con un campo calculado puede especificar una fórmula para asignar un valor al campo. Estos tipos de datos pueden establecerse como campos calculados: **Divisa**, **Fecha y hora**, **Solo fecha**, **Número decimal**, **Duración**, **Correo electrónico**, **Idioma**, **Conjunto de opciones multiselección**, **Conjunto de opciones**, **Texto**, **Área de texto**, **Símbolo del valor**, **Zona horaria**, **Dos opciones**, **Dirección URL** y **Número entero**.

Más información: [Definir campos calculados para automatizar los cálculos manuales](define-calculated-fields.md)

### <a name="rollup"></a>Consolidado

Con un campo consolidado puede establecer funciones de agregación que se ejecutarán periódicamente para configurar un valor numérico para el campo. Estos tipos de datos pueden establecerse como campos calculados: **Divisa**, **Fecha y hora**, **Solo fecha**, **Número decimal**, **Duración**, **Idioma**, **Zona horaria** y **Número entero**.

Más información: [Definir campos consolidados que agregan valores](define-rollup-fields.md)

## <a name="number-field-options"></a>Opciones de campo de número

Cada tipo de campo de número tiene valores mínimos y máximos absolutos. Puede establecer el **Valor mínimo** y el **Valor máximo** dentro de estos valores absolutos. Haga esto para que CDS para aplicaciones valide los valores de los datos que desea almacenar en el campo.

Para los tipos de datos **Número de punto flotante** y **Número decimal**, puede especificar varias **Posiciones decimales**.


## <a name="option-set-field-options"></a>Opciones de campos Conjunto de opciones

Los campos que proporcionan un conjunto de opciones pueden incluir su propio conjunto de opciones *locales* o hacer referencia a un conjunto común de opciones *globales* que se pueden usar para varios campos.

El uso de un conjunto de opciones global es útil cuando se tiene que crear el mismo conjunto de opciones de varios campos. Con un conjunto de opciones global, solo necesita mantener el conjunto de opciones en un lugar. 

Cuando seleccione el tipo de datos **Conjunto de opciones multiselección** o **Conjunto de opciones** el diseñador mostrará una serie de conjuntos de opciones globales disponibles para elegir y proporcionará la opción de crear un **Nuevo conjunto de opciones**.

![Elija el tipo de conjunto opciones](media/option-set-options.png)

Si elige **Nuevo conjunto de opciones** el comportamiento predeterminado es crear un nuevo conjunto de opciones global.

> [!NOTE]
> Cuando está editando opciones para un nuevo conjunto de opciones global, los valores de **Nombre para mostrar** y **Nombre** son para el conjunto de opciones global en lugar de para el campo. Los valores predeterminados coinciden con los valores de campo, pero puede editarlos mientras edita el conjunto de opciones global para que sea distinto del campo que está creando actualmente.

Si desea crear un conjunto de opciones local debe hacer clic en **Ver más** y elegir **Conjunto de opciones local**.

![Conjunto de opciones local](media/local-option-set.png)

> [!NOTE]
> Si define cada conjunto de opciones como conjunto de opciones global, la lista de conjuntos de opciones globales crecerá y puede resultar difícil de administrar. Si sabe que el conjunto de opciones solo se usará en un lugar, use un conjunto de opciones local.

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-field"></a>Eliminación de campos

Con el rol de seguridad de administrador del sistema, puede eliminar campos personalizados que no sean parte de una solución administrada. Si elimina campos, los datos almacenados en los campos se perderán. La única forma de recuperar datos de un campo que se haya eliminado es restaurar la base de datos de un punto anterior a la eliminación del campo.

> [!NOTE]
> Antes de poder eliminar un campo personalizado, debe quitar las dependencias que pueden existir en otros componentes de la solución. 

Mientras [ve campos](#view-fields), si selecciona un campo personalizado que se puede eliminar en la lista, el comando **Eliminar campo** aparece y está habilitado.

![Eliminar un campo mediante el portal](media/delete-field-portal.png)

Use el comando **Eliminar el campo** para eliminar el campo. Después de eliminar el campo debe guardar los cambios de la entidad.

![Guarde la entidad después de eliminar el campo](media/delete-field-portal-save-entity.png)

> [!NOTE]
> Si obtiene un error relacionado con las dependencias, debe usar el explorador de soluciones para detectar dependencias. Más información: [Comprobar dependencias de campos](create-edit-field-solution-explorer.md#check-field-dependencies)

## <a name="ime-mode"></a>Modo IME

Cualquiera de los campos que proporcionan la entrada de texto directa tienen un Modo IME. El editor de métodos de entrada (IME) se usa para idiomas asiáticos orientales como el japonés. Los IME permiten que el usuario especifique miles de caracteres distintos usados en idiomas escritos del este de Asia con un teclado estándar de 101 teclas.



### <a name="see-also"></a>Vea también  
[Creación y edición de campos para Common Data Service para aplicaciones](create-edit-fields.md)<br />
[Crear y editar campos para Common Data Service para aplicaciones mediante el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md)<br />
[Tipos de campos y tipos de datos de campos](types-of-fields.md)<br />
[Definir campos calculados para automatizar los cálculos manuales](define-calculated-fields.md)<br />
[Definir campos consolidados que agregan valores](define-rollup-fields.md)<br />
[Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)
