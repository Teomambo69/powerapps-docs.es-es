---
title: Crear y editar campos para Common Data Service mediante el explorador de soluciones de PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 05/18/2018
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
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-fields-for-common-data-service-using-powerapps-solution-explorer"></a>Crear y editar campos para Common Data Service usando el explorador de soluciones de PowerApps

El explorador de soluciones proporciona una forma de crear y editar campos para Common Data Service.

El [portal PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. <br />Más información: 
- [Creación y edición de campos para Common Data Service](create-edit-fields.md)
- [Crear y editar campos para Common Data Service mediante el portal de PowerApps](create-edit-field-portal.md)
  
## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier campo personalizado que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="view-fields"></a>Campos de vista

Con el explorador de soluciones abierto, en **Componentes** expanda **Entidades** y seleccione la entidad donde desea crear o editar el campo.

![Vista de los campos del explorador de soluciones](media/solution-explorer-fields-view.png)

Puede seleccionar las siguientes vistas: 

 |Vista|Descripción|
 |--|--|
 |**Todo**| Muestra todos los campos para la entidad|
 |**Personalizada**|Muestra solo campos personalizados para la entidad|
 |**Personalizable**|Muestra solo los campos que se pueden editar|

## <a name="create-a-field"></a>Crear un campo

Mientras ve campos, en la barra de comandos, haga clic en **Nuevo** que abrirá el nuevo formulario de campo.  Es posible que algunas entidades estándar o entidades personalizadas que se incluyen en una solución administrada no permitan que agregue nuevos campos.

> [!NOTE]
> Para aplicaciones basadas en modelos también puede crear un nuevo campo desde el editor de formularios. En el editor de formularios, debajo de **Explorador de campos** haga clic en **Nuevo campo** para crear un nuevo campo. Más información: [Agregar un campo a un formulario](../model-driven-apps/add-field-form.md)

![Formulario de nuevo campo del explorador de soluciones](media/solution-explorer-new-field-form.png)

Debe especificar datos y confirmar los valores predeterminados establecidos para las propiedades siguientes antes de guardar.

|Propiedad|Descripción|
|--|--|
|**Nombre para mostrar**|El texto que se muestra para el campo en la interfaz de usuario. Puede cambiar esto después de guardar, pero el valor que especifique generará un valor para el campo **Nombre**.|
|**Requisito de campo**|Si se necesitan datos en el campo para guardar el registro. Más información: [Opciones de requisito de campo](#field-requirement-options)|
|**Nombre**|El nombre único en el entorno. Se generará un nombre para usted basado en el nombre para mostrar que ha especificado, pero puede editarlo antes de guardar. Una vez que un campo se crea el nombre no se puede cambiar, ya que se puede hacer referencia a él en sus aplicaciones o código. El nombre tendrá antepuesto el prefijo de personalización del editor de la solución actual.|
|**Búsqueda**|Establezca esta como **No** para los campos de la entidad que no use.  Cuando un campo permite búsquedas aparece en **Búsqueda avanzada** en aplicaciones basadas en modelos y está disponible cuando se personalizan las vistas. Si anula esta selección se reducirá el número de opciones mostradas a las personas que usan la búsqueda avanzada.|
|**Seguridad de campo**|Si los datos del campo están protegidos a un nivel más alto que la entidad. Más información: [Seguridad de nivel de campo para controlar el acceso](/dynamics365/customer-engagement/admin/field-level-security)|
|**Auditoría**|Si los datos para este campo se auditarán cuando la entidad esté habilitada para auditoría. Más información: [Auditar datos y actividad de usuario para seguridad y conformidad](/customer-engagement/admin/audit-data-user-activity)|
|**Descripción**|Escriba instrucciones para indicar al usuario para qué sirve el campo. Estas descripciones aparecen como información sobre herramientas para el usuario en aplicaciones basadas en modelos cuando mantienen el mouse sobre la etiqueta del campo.|
|**Aparece en el filtro global en la experiencia interactiva**|Más información: [Configurar paneles de experiencia interactiva](/dynamics365/customer-engagement/customize/configure-interactive-experience-dashboards) |
|**Se puede ordenar en el panel de experiencia interactiva**|Más información: [Configurar paneles de experiencia interactiva](/dynamics365/customer-engagement/customize/configure-interactive-experience-dashboards)|
|**Tipo de datos**|Controla cómo se almacenan los valores y también cómo se formatean en algunas aplicaciones. Un vez se guarda un campo, no puede cambiar el tipo de datos ya que puede afectar a los datos en la entidad. Más información: [Tipos de datos de campos](#field-data-types)|
|**Tipo de campo**|Si el campo es **Simple**, **Calculado** o **Consolidado**. Más información: [Tipo de campo](#field-type)|
|**Formato**|Cómo se formateará el campo. Las opciones de formato disponibles dependen del **Tipo de datos**.|

Puede establecer opciones adicionales en función de su elección de **Tipo de datos**. Más información: [Tipos de datos de campos](#field-data-types)

## <a name="field-requirement-options"></a>Opciones de requisito del campo

Hay tres opciones de requisito del campo:
- **Opcional**: Se puede guardar el registro aunque no haya ningún dato en este campo
- **Recomendado por la empresa**: Se puede guardar el registro aunque no haya ningún dato en este campo Sin embargo, un símbolo azul aparece junto al campo para indicar que es importante.
- **Necesario para la empresa**: No se puede guardar el registro si no hay ningún dato en este campo
> [!NOTE]
> Tenga cuidado cuando cree campos requeridos por la empresa. Los usuarios se opondrán al uso de la aplicación si no pueden guardar registros porque carecerán de la información correcta para introducir en un campo obligatorio. Los usuarios pueden especificar datos incorrectos simplemente para guardar el registro y comenzar con su trabajo. Puede usar reglas de negocio o scripts de formulario para cambiar el nivel de requisito a medida que los datos del registro cambian con el trabajo de los usuarios. Más información: [Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

## <a name="field-data-types"></a>Tipos de datos de campo

Hay muchos diferentes tipos de campos, pero solo puede crear algunos. Para obtener más información sobre todos los tipos de campos, consulte [Tipos de campos y tipos de datos de campo](types-of-fields.md).

Cuando crea un campo, **Tipo de datos** proporciona las siguientes opciones:

|Opción|Descripción|
|--|--|
|**Línea de texto única**|Este campo puede contener hasta 4000 caracteres de texto. Puede establecer una longitud máxima inferior a esta. Este campo tiene varias opciones de formato que cambiarán la presentación del texto.  Más información: [Opciones de una línea de texto única](#single-line-of-text-options)|
|**Conjunto de opciones**|Muestra una lista de opciones donde puede seleccionar una. Más información: [Opciones de campo de conjunto de opciones](#option-set-field-options)|
|**Conjunto de opciones multiselección**|Muestra una lista de opciones donde puede seleccionar más de una. Más información: [Opciones de campo de conjunto de opciones](#option-set-field-options)|
|**Dos opciones**|Muestra una lista de opciones donde puede seleccionar dos.<br /><br /> Dos campos de opción no proporcionarán opciones de formato en el de nivel de campo. Pero cuando agregue uno al formulario puede elegir presentarlos como botones de opción, una casilla o una lista de selección.|
|**Imagen**|Muestra una sola imagen por cada registro de la aplicación. Cada entidad puede tener un campo de imagen. Los campos de imagen siempre se denominan `EntityImage`.|
|**Número entero**|Los valores enteros con un valor entre -2.147.483.648 y 2.147.483.647 pueden estar en este campo.  Este campo tiene opciones que cambian en función de cómo se presenta el campo. Más información: [Opciones de número entero](#whole-number-options)|
|**Número de punto flotante**|Hasta 5 puntos decimales de precisión se pueden usar para valores entre -100.000.000.000 y -100.000.000.000 en este campo. Puede especificar el nivel de precisión y los valores máximo y mínimo. Más información: [Uso del tipo correcto de número](types-of-fields.md#using-the-right-type-of-number)|
|**Número decimal**|Hasta 10 puntos decimales de precisión se pueden usar para valores entre -100.000.000.000 y -100.000.000.000 en este campo. Puede especificar el nivel de precisión y los valores máximo y mínimo. Más información: [Uso del tipo correcto de número](types-of-fields.md#using-the-right-type-of-number)|
|**Divisa**|Los valores monetarios entre -922.337.203.685.477 y 922.337.203.685.477 pueden estar en este campo. Puede establecer un nivel de precisión o elegir basar la precisión en una divisa específica o una precisión estándar única usada por la organización. Más información: [Uso de campos de divisa](types-of-fields.md#using-currency-fields)|
|**Varias líneas de texto**|Este campo puede contener hasta 1 048 576 caracteres de texto. Puede establecer que la longitud máxima sea inferior a esta. Cuando agrega este campo a un formulario de aplicación basado en modelos, puede especificar las dimensiones del campo.|
|**Fecha y hora**|Use estos campos para almacenar valores de hora. Puede almacenar valores de hasta 1/1/1753 12:00 AM. Más información: [Opciones de fecha y hora](#date-and-time-options)|
|**Búsqueda**|Un campo que permite la configuración de una referencia a un registro único de un tipo específico de entidad. Algunos campos de búsqueda del sistema se comportan de forma distinta. Más información: [Diferentes tipos de búsquedas](types-of-fields.md#different-types-of-lookups)|
|**Cliente**|Un campo de búsqueda que puede usar para especificar un cliente, que puede ser una cuenta o un contacto.  Más información: [Diferentes tipos de búsquedas](types-of-fields.md#different-types-of-lookups)|

### <a name="single-line-of-text-options"></a>Opciones de una sola línea de texto

El tipo de datos de una sola línea de texto tiene las opciones de formato siguientes:

|Formato|Descripción|
|--|--|
|**Texto**|Un valor de texto pensado para mostrar en un cuadro de texto de una línea.|
|**Área de texto**|Un valor de texto pensado para mostrar en un cuadro de texto de varias líneas. Si requiere más de 4.000 caracteres, use un tipo de datos **Varias líneas de texto**.|
|**Correo electrónico**|Valor de texto validado como dirección de correo electrónico y generado como vínculo mailto en el campo. |
|**Dirección URL**|Valor de texto validado como dirección URL y generado como un vínculo para abrir la dirección URL.|
|**Símbolo del valor**|Un valor del texto para un símbolo de valor que mostrará un vínculo que se abrirá para mostrar una oferta para el símbolo de valor bursátil. |
|**Teléfono**|Valor de texto validado como número de teléfono generado como vínculo para realizar una llamada de teléfono con Skype. |

También puede establecer una **Longitud máxima** para que el sistema no permita valores de texto más largos de los que especifique.

### <a name="option-set-field-options"></a>Opciones de campos Conjunto de opciones

Los campos que proporcionan un conjunto de opciones pueden incluir su propio conjunto de opciones *locales* o hacer referencia a un conjunto común de opciones *globales* que se pueden usar para varios campos.

El uso de un conjunto de opciones global es útil cuando se tiene que crear el mismo conjunto de opciones de varios campos. Con un conjunto de opciones global, solo necesita mantener el conjunto de opciones en un lugar. 

Cuando seleccione el tipo de datos **Conjunto de opciones multiselección** o **Conjunto de opciones** el diseñador del explorador de soluciones le confiere la opción para un conjunto de opciones local de forma predeterminada.

![Configurar un conjunto de opciones local](media/local-option-set-solution-explorer.png)

#### <a name="configure-local-options"></a>Configurar opciones locales

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

#### <a name="use-existing-option-set"></a>Usar Conjunto de opciones existente

Si elige **Usar Conjunto de opciones existente** el diseñador mostrará una lista de *conjuntos de opciones globales* existentes e incluirá los botones **Editar** y **Nuevo** para configurar las opciones globales que este campo deberá usar.

![Configurar un conjunto de opciones global](media/global-option-set-solution-explorer.png)

También puede configurar conjuntos de opciones globales por separado. Más información: [Creación y edición de conjuntos de opciones globales para Common Data Service (listas desplegables)](create-edit-global-option-sets.md)

> [!NOTE]
> Si define cada conjunto de opciones como conjunto de opciones global, la lista de conjuntos de opciones globales crecerá y puede resultar difícil de administrar. Si sabe que el conjunto de opciones solo se usará en un lugar, use un conjunto de opciones local.


### <a name="whole-number-options"></a>Opciones de número entero

Los campos de número entero tienen las siguientes opciones de formato:

|Formato|Descripción|
|--|--|
|**Ninguno**|Valor de número presentado en un cuadro de texto.|
|**Duración**|Valor de número presentado como lista desplegable que contiene intervalos de tiempo. El usuario puede seleccionar un valor de la lista o escribir un valor entero que represente el número de minutos.|
|**Zona horaria**|Valor de número presentado como lista desplegable que contiene una lista de zonas horarias.|
|**Idioma**|Un valor numérico presentado como lista desplegable con los idiomas que se hayan habilitado para el entorno. Si no se ha activado ningún otro idioma, el idioma base será la única opción. El valor guardado es el valor del Identificador de configuración regional (LCID) del idioma.|

También puede restringir los valores máximo o mínimos permitidos.

### <a name="date-and-time-options"></a>Opciones de fecha y hora

Los campos de fecha y hora tienen las siguientes opciones:

|Formato |Descripción|
|--|--|
|**Fecha y hora**|Un valor de fecha y hora.|
|**Solo fecha**|Valor de fecha y hora que solo se muestra una fecha. El valor de hora se almacena como 12:00 AM (00:00: 00) en el sistema.|

También puede establecer un **Comportamiento** específico para los campos de fecha y hora en **Opciones avanzadas**.

- **Local del usuario** : Muestra valores convertidos a la zona horaria local del usuario actual. Es el valor predeterminado de nuevos campos.
- **Solo fecha**: Este comportamiento está disponible para el tipo **Solo fecha**. Muestra valores sin conversión de zona horaria. Úselo para datos como cumpleaños y aniversarios.
- **Independiente de la zona horaria**: Muestra valores sin conversión de la zona horaria.

Más información: [Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)

## <a name="field-type"></a>Tipo de campo

Puede establecer que un **Tipo de campo** personalizado se **Simple**, **Calculado** o **Consolidado**. 

### <a name="simple"></a>Básico

Simple significa que el campo no es un campo calculado ni consolidado.

### <a name="calculated"></a>Calculado

Con un campo calculado puede especificar una fórmula para asignar un valor al campo. Estos tipos de datos pueden establecerse como campos calculados: **Divisa**, **Fecha y hora**, **Número decimal**, **Conjunto de opciones multiselección**, **Conjunto de opciones**, **Línea única de texto**, **Dos opciones** y **Número entero**.

Más información: [Definir campos calculados para automatizar los cálculos manuales](define-calculated-fields.md)

### <a name="rollup"></a>Consolidado

Con un campo consolidado puede establecer funciones de agregación que se ejecutarán periódicamente para configurar un valor numérico para el campo. Estos tipos de datos pueden establecerse como campos calculados: **Divisa**, **Fecha y hora**, **Número decimal** y **Número entero**.

Más información: [Definir campos consolidados que agregan valores](define-rollup-fields.md)

## <a name="save-new-field"></a>Guardar nuevo campo

Una vez que haya configurado el campo, use uno de los tres comandos en la barra de comandos:

|Comando|Descripción|
|--|--|
|**Guardar**|Guarde la definición del campo y deje la ventana del formulario abierta.|
|**Guardar y cerrar**|Guarde la definición del campo y cierre la ventana.|
|**Guardar y crear nuevo**|Guarde la definición de campo y abra un formulario nuevo para crear un campo nuevo.|


## <a name="edit-a-field"></a>Editar un campo 

Mientras [ve campos](#view-fields), haga clic en el campo que desea editar. Es posible que algunos campos estándar o campos personalizados que se incluyen en una solución administrada no permitan que los edite.

> [!NOTE]
> Cuando edite un formulario, para los campos ya agregados al formulario puede hacer doble clic en el campo para mostrar **Propiedades de campo**. En la pestaña **Detalles**, haga clic en **Editar**. Más información: [Agregar un campo a un formulario](../model-driven-apps/add-field-form.md)

Después de realizar cambios en un campo, debe publicar personalizaciones. 

- Para publicar los cambios para una entidad, en **Componentes**, seleccione **Entidades**, y luego seleccione la entidad en la que ha realizado cambios. En la barra de herramientas **Acciones**, seleccione **Publicar**.  
  
- Para publicar todos los cambios realizados en varias entidades o componentes, en la barra de herramientas **Acciones**, seleccione **Publicar todas las personalizaciones**.  
  
> [!NOTE]
>  La instalación de una solución o la publicación de personalizaciones puede interferir en el funcionamiento normal del sistema. Le recomendamos que programe una solución para que se publique cuando menos perjudique a los usuarios.  

### <a name="edit-multiple-fields"></a>Editar varios campos

Para editar uno o más campos, seleccione el campo o los campos (mediante la tecla Mayús) que desee modificar y en la barra de herramientas **Acciones**, seleccione **Editar**. 
  
Al seleccionar varios campos para la edición, aparece el cuadro de diálogo **Editar varios campos**. Puede editar **Requisito de campo**, **Búsqueda** y **Auditoría**. 

## <a name="delete-a-field"></a>Eliminación de campos

Con el rol de seguridad de administrador del sistema, puede eliminar campos personalizados que no sean parte de una solución administrada. Si elimina campos, los datos almacenados en los campos se perderán. La única forma de recuperar datos de un campo que se haya eliminado es restaurar la base de datos de un punto anterior a la eliminación del campo.

> [!NOTE]
> Antes de poder eliminar un campo personalizado, debe quitar las dependencias que pueden existir en otros componentes de la solución. 

1. Mientras [ve campos](#view-fields), si selecciona un campo personalizado que se puede eliminar en la lista y haga clic en el botón ![Eliminar comando](../model-driven-apps/media/delete.gif) en la barra de comandos.
2. En el cuadro de diálogo **Confirmar eliminación**, seleccione **Eliminar**.

> [!TIP]
> Puede seleccionar varios campos personalizados para eliminar en una operación.

### <a name="check-field-dependencies"></a>Compruebe las dependencias de campo 

Seleccione el campo en la lista. En el menú **Más acciones**, seleccione **Mostrar dependencias**.

![Mostrar dependencias para campo](media/check-field-dependencies.png)

Las dependencias son cualquier uso relacionado del campo que evitaría que se eliminara. Por ejemplo, si el campo se usa en un formulario o una vista, primero debe quitar las referencias al campo en esos componentes de la solución.  
  
Si elimina un campo de búsqueda, la relación de entidad 1:N correspondiente se eliminará automáticamente.  

## <a name="ime-mode"></a>Modo IME

Cualquiera de los campos que proporcionan la entrada de texto directa tienen un Modo IME. El editor de métodos de entrada (IME) se usa para idiomas asiáticos orientales como el japonés. Los IME permiten que el usuario especifique miles de caracteres distintos usados en idiomas escritos del este de Asia con un teclado estándar de 101 teclas.


### <a name="see-also"></a>Vea también  
[Creación y edición de campos para Common Data Service](create-edit-fields.md)<br />
[Crear y editar campos para Common Data Service mediante el portal de PowerApps](create-edit-field-portal.md)<br />
[Tipos de campos y tipos de datos de campos](types-of-fields.md)<br />
[Definir campos calculados para automatizar los cálculos manuales](define-calculated-fields.md)<br />
[Definir campos consolidados que agregan valores](define-rollup-fields.md)<br />
[Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)
