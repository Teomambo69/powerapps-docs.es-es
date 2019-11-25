---
title: Tipos de datos de campo en Common Data Service | MicrosoftDocs
description: Comprender los distintos tipos de datos de campos disponibles para su aplicación
keywords: ''
ms.date: 09/30/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 734b4ffa-5543-4f88-8517-299589f433f7
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cf8a30ae29712804cea2da42b0e448acc6286553
ms.sourcegitcommit: e4b3b6b610f91a0c704a4fa87c6ec238aa81d25f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "2767259"
---
# <a name="types-of-fields"></a>Tipos de campos

Los nombres usados para los tipos dependen del diseñador usado. El [portal de PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) usa una convención que incluye la forma en que están formateados los datos. El tipo de explorador de soluciones usa un nombre alineado con el tipo de datos de la base de datos con un modificador de formato. La tabla siguiente incluye el tipo de API `AttributeTypeDisplayName` correspondiente.

|Tipo de datos del portal |Tipo de explorador de soluciones| Tipo de API|
|--|--|--|
|**Entero grande**|**Marca de tiempo**|`BigIntType`|
|**Divisa**|**Divisa**|`MoneyType`|
|**Cliente**|**Cliente**|`CustomerType`|
|**Fecha y hora**|**Fecha y hora**<br />Formato de *fecha y hora*|`DateTimeType`|
|**Solo fecha**|**Fecha y hora**<br />Formato de *Solo fecha*|`DateTimeType`|
|**Número decimal**|**Número decimal**|`DecimalType`|
|**Duración**|**Número entero**<br />Formato de*Duración*|`IntegerType`|
|**Correo electrónico**|**Línea de texto única**<br />Formato de *Correo electrónico*|`StringType`|
|**Archivo** | **Archivo**   | `FileType`  |
|**Número de punto flotante**|**Número de punto flotante**|`DoubleType`|
|**Imagen**|**Imagen**|`ImageType`|
|**Idioma**|**Número entero**<br />Formato de *Idioma*|`IntegerType`|
|**Búsqueda**|**Búsqueda**|`LookupType`|
|**Conjunto de opciones de selección múltiple**|**Conjunto de opciones multiselección**|`MultiSelectPicklistType`|
|**Texto multilínea**|**Varias líneas de texto**|`MemoType`|
|**Conjunto de opciones**|**Conjunto de opciones**|`PicklistType`|
|**Propietario**|**Propietario**|`OwnerType`|
|**Teléfono**|**Línea de texto única**<br />Formato de*Teléfono*|`StringType`|
|**Razón para el estado**|**Razón para el estado**|`StatusType`|
|**Estado**|**Estado**|`StateType`|
|**Área de texto**|**Línea de texto única**<br />Formato de *Área de texto*|`StringType`|
|**Texto**|**Línea de texto única**<br />Formato de*Texto*|`StringType`|
|**Símbolo del valor**|**Línea de texto única**<br />Formato de Símbolo del valor|`StringType`|
|**Zona horaria**|**Número entero**<br />Formato de *Zona horaria*|`IntegerType`|
|**Dos opciones**|**Dos opciones**|`BooleanType`|
|**Identificador único**|**Identificador único** o **Clave principal**|`UniqueidentifierType`|
|**Dirección URL**|**Línea de texto única**<br />Formato de *URL*|`StringType`|
|**Número entero**|**Número entero**<br />Formato de *Ninguno*|`IntegerType`|

Para obtener más descripciones para cada tipo que puede agregar o editar, consulte el tema sobre el diseñador correspondiente:
 - [Crear y editar campos para Common Data Service mediante el portal de PowerApps: Tipos de datos de campo](create-edit-field-portal.md#field-data-types)
 - [Crear y editar campos para Common Data Service mediante el explorador de soluciones de PowerApps: Tipos de datos de campo](create-edit-field-solution-explorer.md#field-data-types)

Para obtener más información acerca de cómo se definen los tipos de datos de campos en la API, consulte [Metadatos de atributos](/powerapps/developer/common-data-service/entity-attribute-metadata)

## <a name="field-types-used-by-the-system"></a>Tipos de campos que se usan en el sistema

Existen algunos campos usados por el sistema que no es posible agregar mediante el diseñador.

|Escriba|Descripción|
|--|--|
|**Entero grande** o **Marca de tiempo**|Usado por el sistema para capturar un número de versión para administrar las actualizaciones en una entidad.|
|**Cliente**|Un campo de búsqueda que puede usar para especificar un cliente, que puede ser una cuenta o un contacto.<br />**Nota**: este atributo se puede agregar con el diseñador del explorador de soluciones.|
|**Propietario**|Un campo de búsqueda del sistema que hace referencia al usuario o al equipo que tiene asignado un registro de entidad propiedad de un usuario o equipo.|
|**Razón para el estado**|Un campo del sistema que tiene opciones que proporcionan información adicional sobre el campo Estado. Cada opción está asociada con una de las opciones de Estado disponibles. Puede agregar y editar las opciones. <br /><br /> También puede incluir transiciones de estado personalizadas para controlar qué las opciones de estado están disponibles para determinadas entidades. Más información: [Definir las transiciones de razón para el estado para entidades personalizadas](define-status-reason-transitions.md)|
|**Estado**|Un campo del sistema que tiene opciones que corresponden normalmente a los estados activo e inactivo. Algunos atributos del sistema tienen opciones adicionales, pero todos los atributos personalizados solo tienen las opciones de estado **Activo** e **Inactivo**.  |
|**Identificador único**|Un campo del sistema almacena un identificador único global (GUID) para cada registro.|

  
## <a name="multiselect-option-set"></a>Conjunto de opciones multiselección

Puede personalizar formularios (principal, creación rápida y vista rápida) así como plantillas de correo electrónico agregando campos de selección múltiple. Cuando agrega un campo de conjunto de opciones de selección múltiple, puede especificar múltiples valores que los usuarios pueden seleccionar. Cuando los usuarios rellenan el formulario pueden seleccionar uno, varios o todos los valores mostrados en una lista desplegable.

Por ejemplo, si una organización opera en varias áreas o países, puede incluir varias ubicaciones o países en un campo 'Área de operación'. Un usuario puede seleccionar entonces una ubicación o varias en la lista de valores disponibles.

El conjunto de opción de selección múltiple solo está disponible en formularios, cuadrículas editables y formularios. El conjunto de opciones de selección múltiple no es compatible en: 
- Flujos de trabajo, acciones, cuadros de diálogo, resúmenes, gráficos y campos calculados.
- Informes, SLA y regla de enrutamiento.

Los campos de selección múltiple están permitidos en los siguientes tipos de formularios:

|Tipo de formulario|Disponibilidad|
|--|--|
|**Formulario turbo**|Sí|
|**Formulario actualización**|Solo lectura (el campo estará disponible, pero no se puede editar)|
|**Formulario heredado**|No|
|**Formulario de edición masiva**|No|

Puede usar los conjuntos de opciones globales definidos en su organización para configurar los valores para los conjuntos de opciones de selección múltiple.


<a name="BKMK_UsingTheRightTypeOfNumber"></a>
  
## <a name="using-the-right-type-of-number"></a>Usar el tipo de número correcto

Al elegir el tipo correcto de campo de número que se va a usar, la opción para usar el tipo **Número entero** o **Divisa** debe ser suficientemente directa. La decisión entre usar números de **Punto flotante** o **Decimal** requiere más premeditación.  
  
Los números decimales se almacenan en la base de datos exactamente como están especificados. Los números de punto flotante almacenan una aproximación extremadamente parecida al valor. ¿Por qué elige la aproximación extremadamente parecida cuándo puede tener el valor exacto? La respuesta es que se obtiene un rendimiento diferente del sistema.  
  
Use decimales si necesita proporcionar informes que requieren cálculos muy precisos, o si suele usar consultas que buscan valores iguales o distintos a otro valor.  
  
Use los números de punto flotante cuando almacene datos que representen fracciones o valores que normalmente consultaría para compararlos con otro valor utilizando operadores mayor que o menor que. En la mayoría de los casos, la diferencia entre los tipos decimal y flotante es imperceptible. A menos que necesite realizar cálculos los más precisos posible, los números de punto flotante son una opción adecuada para usted.  
  
<a name="BKMK_UsingCurrencyFields"></a>
 
## <a name="using-currency-fields"></a>Usar campos de divisa

Los campos de divisa permiten a una organización configurar varias divisas que puedan usarse para registros de la organización. Cuando las organizaciones tienen varias divisas, suelen desear poder realizar cálculos para proporcionar valores usando la divisa base. Cuando se agrega un campo de divisa a una entidad que no tiene ningún otro campo de divisa, se agregan dos campos adicionales:  
  
- Un campo de búsqueda llamado **Divisa** que puede establecer en cualquier divisa activa configurada para su organización. Puede configurar varias divisas activas para su organización en **Configuración** > **Administración de empresas** > **Divisas**. Aquí puede especificar la divisa y un tipo de cambio con respecto a la divisa base establecida para su organización. Si tiene varias divisas activas, puede agregar el campo de divisa al formulario y permitir a los usuarios especificar qué divisa debería aplicarse a los valores monetarios del registro. Esto cambiará el símbolo de moneda que aparece para los campos de divisa en el formulario.  
  
  Los individuos también pueden cambiar sus opciones personales para seleccionar una divisa predeterminada para los registros que crean.
  
- Un campo decimal llamado **Tipo de cambio** que proporciona el tipo de cambio para una divisa seleccionada asociada a la entidad en cuanto a la divisa base. Si este campo se agrega al formulario, los usuarios pueden ver el valor, pero no pueden modificarlo. El tipo de cambio se almacena con la divisa.  
  
Para cada campo de divisa que agregue, se agrega otro campo de divisa con el prefijo `_Base` en el nombre. Este campo almacena el cálculo del valor del campo de divisa que ha agregado y la divisa base. Una vez más, si este campo se agrega al formulario, no se puede editar.  
  
Cuando se configura un campo de divisa puede elegir el valor de precisión. Existen tres opciones, como se muestra en la siguiente tabla.  
  
|Opción|Descripción|  
|------------|-----------------|  
|Precisión de precios decimal|Se trata de una sola precisión de la organización que se usará para los precios que se encuentran en **Configuración** > **Administración** > **Configuración del sistema** > **Pestaña General**.|  
|Precisión de la divisa|Esta opción aplica la precisión definida para la divisa del registro.|  
|Valores de precisión específica|Estos valores permiten definir una precisión específica usando valores entre 0 y 4.|  
  
<a name="BKMK_DifferentTypesOfLookups"></a> 
  
## <a name="different-types-of-lookups"></a>Diferentes tipos de búsquedas  

Cuando crea un nuevo campo de búsqueda se crea una nueva relación de entidad de varios a uno (N:1) entre la entidad en la que está trabajando y el **Tipo de registro de destino** definido para la búsqueda. Hay opciones de configuración adicionales para esta relación que se describen en [Crear y editar relaciones entre entidades](create-edit-entity-relationships.md). Pero todas las búsquedas personalizadas pueden permitir solo una referencia a un registro único para un único tipo de registro de destino.  
  
Sin embargo, debe conocer que no todas las búsquedas se comportan de esta forma. Existen varios tipos diferentes de búsquedas del sistema como se indica a continuación.  
  
|Tipo de búsqueda|Descripción|  
|-----------------|-----------------|  
|**Básico**|Permite una única referencia a una entidad específica. Todas las búsquedas personalizadas son de este tipo.|  
|**Cliente**|Permite una única referencia a una cuenta o un registro de contacto.|  
|**Propietario**|Permite una única referencia a un equipo o un registro de usuario. Todas las entidades propiedad del equipo el usuario presentan una de estas opciones. Más información: [Agregar la entidad de equipo como opción de búsqueda en la aplicación](../model-driven-apps/team-entity-lookup.md)|  
|**Lista de partes**|Permite asignar varias referencias a varias entidades. Estas búsquedas se encuentran en los campos **Para** y **CC** de la entidad Correo electrónico. También se usan en las entidades Teléfono y Cita.|  
|**Referente a**|Permite asignar una sola referencia a varias entidades. Estas búsquedas se encuentran en el campo referente usado en las actividades.|  

<a name="BKMK_ImageFields"></a>

## <a name="image-fields"></a>Campos de imagen  
Use los campos de imagen para presentar una sola imagen por cada registro de la aplicación. Cada entidad puede tener un campo de imagen. Puede agregar un campo de imagen a entidades personalizadas pero no a entidades estándar. Algunas entidades estándar tienen campos de imágenes definidos.
  
Aunque una entidad tenga un campo de imagen, la visualización de dicha imagen en una aplicación controlada por modelos requiere que habilite dos ajustes. 
- El valor de propiedad **Imagen principal** de la definición de entidad estándar se debe establecer como **Imagen predeterminada**. Las entidades personalizadas requieren un campo de imagen personalizado. A continuación, puede seleccionar ese campo de imagen para el valor **Imagen principal** en la definición de entidad personalizada.  
- El formulario de entidad donde se debe mostrar la imagen debe tener la propiedad **Mostrar la imagen en el formulario** habilitada.  
  
Cuando se habilita la visualización de la imagen para una entidad, cualquier registro que no tenga una imagen mostrará una imagen de marcador de posición. Por ejemplo:

> [!div class="mx-imgBorder"] 
> ![Imagen de entidad predeterminada](../common-data-service/media/account-record-default-image.png "Imagen de entidad de cuenta predeterminada")
  
Los usuarios pueden elegir la imagen predeterminada para cargar una imagen desde su equipo. Las imágenes deben ser de tamaño inferior a 10 MB y deben tener uno de los siguientes formatos:  
  
- jpg
- jpeg
- gif
- tif
- tiff
- bmp
- png
  
Cuando la imagen se cargue, se convertirá al formato .jpg y todas las imágenes descargadas también usarán este formato. Si se carga un archivo .gif animado, solo se guardará el primer fotograma.  
  
Cuando se cargue una imagen, su tamaño se modificará como imagen en "miniaturaa" hasta una tamaño máximo de 144 píxeles por 144 píxeles. Los usuarios deben cambiar el tamaño de las imágenes o recortarlas antes de cargarlas, de modo que se muestren correctamente con este tamaño. Todas las imágenes se recortan para ser cuadradas. Si ambos lados de una imagen son más pequeños que 144 píxeles, la imagen se recortará para que sea cuadrada con las dimensiones del más pequeño.  

<!-- 
By default, when an app user adds an image to display to a form or canvas app, the image displayed is the thumbnail image. To display a full image for a canvas app, see [Display a full-sized image on a canvas app form](../canvas-apps/display-full-image-on-form.md).


### Add an image field to an entity using the PowerApps site

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

1. Sign in to [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  
2.  Select **Data** > **Entities** and then select the entity where you want to add an image field. 
3. Select **Add field** on the command bar, enter the following properties, and then select **Done**: 
   - **Display name**. Enter a friendly name for the field. 
   - **Data type**. Select **Image**. 
   - **Primary image**. When selected, the primary image field becomes the image field for the entity. You can only have one primary image for each entity. 
   - **Maximum image size**. The maximum file size that an app user can upload to the record. 10,240 KB is the default maximum size and 10 MB is the maximum size limit. 
   - **Can store full images**. When selected, in addition to the rescaled thumbnail image described earlier, the full image is stored when uploaded by the user for each record. Full size images are limited to 30 MB.  -->

### <a name="add-image-support-for-a-form-in-a-custom-entity-using-solution-explorer"></a>Agregar compatibilidad de imagen para un formulario en una entidad personalizada usando el explorador de soluciones
1. Abra el [explorador de soluciones](../model-driven-apps/advanced-navigation.md#solution-explorer). 
2. En el panel de navegación izquierda, expanda **Entidades**, expanda la entidad personalizada que desee y luego seleccione **Campos**. 
3. En la barra de herramientas, seleccione **Nuevo**. 
4. En la sección **Tipo** en la lista desplegable **Tipo de datos** seleccione **Imagen**. 
5. Escriba un **Nombre para mostrar**, como *Imagen de entidad personalizada*. 
6. Complete los campos restantes como corresponda. Tenga en cuenta que los campos **Nombre**, **Requisitos de campo** y **Búsqueda** no podrán cambiarse. Seleccione **Guardar y cerrar**. 
7. En la definición de entidad junto a la propiedad **Imagen principal** asegúrese de que el valor se ha configurado como la imagen personalizada que creó en el paso anterior. Si no es así, selecciónela.  
    > [!div class="mx-imgBorder"] 
    > ![Propiedad de imagen principal seleccionada](media/primary-image-property.png "Propiedad de imagen principal seleccionada")

8.  Abra el formulario donde desea compatibilidad de imagen, como el formulario principal de entidad. 
9.  En la cinta de opciones del editor de formularios, seleccione **Propiedades del formulario**. 
10. En la página **Propiedades de formulario**, seleccione la pestaña **Mostrar**, seleccione **Mostrar imagen en el formulario** y, a continuación seleccione **Aceptar**. 

    > [!div class="mx-imgBorder"] 
    > ![Mostrar imagen en configuración de formulario](media/show-image-on-form.png "Mostrar imagen en configuración de formulario")

11. En la cinta de opciones del editor de formularios, seleccione **Guardar** y, después, seleccione **Publicar**. Cierre el editor de formularios. 

Los usuarios de la aplicación ahora pueden seleccionar la imagen para mostrar en el formulario. Cuando un usuario abre el formulario para un registro, puede elegir la imagen que desea mostrar en el formulario. 

> [!IMPORTANT]
> Si el registro es un nuevo registro que no se ha guardado, el error Argumento no válido se devuelve al intentar cambiar la imagen. 

### <a name="change-the-image-for-a-record"></a>Cambiar la imagen para un registro
Una vez que un formulario de entidad tiene un campo de imagen, los usuarios de la aplicación pueden cambiar la imagen para un registro determinado. 

1. Abra la aplicación que incluye el formulario de entidad y luego seleccione la imagen en el formulario. 
   > [!div class="mx-imgBorder"] 
   > ![Imagen de entidad predeterminada](../common-data-service/media/default-entity-image-on-form.png "Imagen de entidad predeterminada")

2. Seleccione **Cargar imagen**, examine y seleccione la imagen que desea mostrar en el formulario de entidad y, a continuación seleccione **Cambiar**. La imagen aparecerá en el registro. 
   > [!div class="mx-imgBorder"] 
   > ![Imagen cambiada guardada a un registro](../common-data-service/media/custom-entity-icon-record.png "Imagen cambiada guardada a un registro")


Más información para desarrolladores que trabajan con datos de imágenes:
- [Metadatos de entidad > Imágenes de entidad](/powerapps/developer/common-data-service/entity-metadata#entity-images)
- [Atributos de imagen](/powerapps/developer/common-data-service/image-attributes)


## <a name="file-fields"></a>Campos del archivo
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Actualmente, el tipo de datos de archivo sólo está disponible para aplicaciones de lienzo y flujos. 

El campo **Archivo** sirve para almacenar datos binarios. El uso principal previsto de este campo es almacenar una sola imagen, nota, o datos adjuntos. Sin embargo, el almacenamiento de otras formas de datos binarios es también posible. Uno o varios campos de este tipo de datos se pueden agregar a una entidad personalizable estándar existente o una entidad personalizada.

El **Tamaño máximo de archivo** predeterminado es 32 MB y el tamaño mayor que puede establecer es 128 MB. El límite de tamaño de archivo puede establecerse de forma individual para cada campo del tipo de archivo agregado a una entidad. 

Más información para desarrolladores que trabajan con datos de archivo: [Atributos de archivo](/powerapps/developer/common-data-service/file-attributes)