---
title: Definir formularios de entidad | MicrosoftDocs
description: Instrucciones para crear formularios de entidad en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/09/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4ddc8daba01d281a483d51b1ce7a42205d0c6e93
ms.sourcegitcommit: 2484ebce6563cfd1c849e1e2f66dd2d29fdb7b64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2020
ms.locfileid: "3256699"
---
# <a name="about-entity-forms"></a>Acerca de formularios de entidad

Una configuración controlada por datos para permitir que los usuarios finales agreguen un formulario para recopilar datos en el portal sin necesidad de que un desarrollador exponga el formulario en el portal, los formularios de entidades se crean en Common Data Service y después se incluyen en páginas web en el portal o se usan conjuntamente con subcuadrículas y listas de entidad para crear aplicaciones web completas. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Acerca de listas de entidades](entity-lists.md) 

![Formulario Póngase en contacto con nosotros](../media/contact-us-form.png "Formulario Póngase en contacto con nosotros")  

## <a name="add-a-form-to-your-portal"></a>Agregar un formulario al portal

El formulario de entidad contiene relaciones con páginas web y propiedades adicionales para controlar la inicialización del formulario dentro del portal. La relación con páginas webs permite la recuperación dinámica de la definición de formulario para un determinado nodo de página en el sitio web. 

Para ver formularios de entidad existentes o crear nuevos formularios de entidad, abra la [aplicación Administración del portal](configure-portal.md) y vaya a **Portales** &gt; **Formularios de entidad**.

Cuando cree un nuevo formulario de entidad el primer paso es decidir la **Entidad** y **Nombre del formulario** que representará, así como **modo: Insertar, Editar o Solo lectura**. El modo seleccionado determinará si está creando un nuevo registro del portal, editando un registro existente, o solo mostrando información de un registro en el portal.

> [!Note]
> - Un **formulario de entidad** debe estar asociado con una página web para un determinado sitio web para que el formulario sea visible desde el sitio.
> - Las subcuadrículas de la entidad de conexión no se admiten en formularios de entidad. Si agrega una subcuadrícula de entidad de conexión al formulario con el diseñador formularios, se muestran los mensajes de error cuando procesa el formulario en el portal y usa la entidad de la conexión.
> - Los campos duplicados, el conjunto de opciones multiselección, los campos de lista de partes y las reglas de negocio no son compatibles en los formularios de entidad.
> - Las reglas de negocio y el cliente API pueden permitir campos bloqueados en un formulario de sólo lectura.
> - Si crea un formulario de entidad en el modo de inserción, no podrá cambiar la alineación de un botón o colocar un botón de acción encima del formulario de entidad.
> - Si genera un control de búsqueda como lista desplegable en el formulario, el filtro de registros relacionados no funciona.

Las páginas web asociadas al formulario de entidad se pueden ver al seleccionar el vínculo **Páginas web** mostrado en los vínculos de navegación **Relacionados** en el menú de la izquierda.

Al crear o editar una página web, un **formulario de entidad** se puede especificar en el campo de búsqueda proporcionado en el formulario de la página web.

Las distintas páginas maestras usadas por el portal contienen declaraciones del control de servidor de **EntityForm**. Al representar la página web que contiene la plantilla de páginas de la Página (~/Pages/Page.aspx) o una plantilla de páginas de Página completa (~/Pages/FullPage.aspx), los controles determinarán si la búsqueda del formulario de entidad contiene un valor, en cuyo caso, se representará el formulario.

## <a name="secure-your-forms"></a>Proteger los formularios

Para proteger los formularios, debe crear permisos de entidad que determinan el acceso y la propiedad de los registros de acuerdo con roles web. Si un usuario aterriza en un formulario de entidad y no tiene permisos, recibirá un mensaje de error. Para habilitar los permisos para un formulario de entidad, establezca **Habilitar permisos de entidad** en true. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Crear roles web para portales](create-web-roles.md).  

## <a name="entity-form-attributes-and-relationships"></a>Atributos y relaciones del formulario de entidades

|Nombre|Descripción|
|-----|----------|
|Nombre|Nombre descriptivo del registro. Este campo es obligatorio.|
|Nombre de entidad|El nombre de la entidad desde la que se cargará el formulario. Este campo es obligatorio.|
|Nombre del formulario|    El nombre del formulario de la entidad de destino que se va a representar. Este campo es obligatorio.|
|Nombre de pestaña|    Nombre opcional de una pestaña en un formulario para una entidad especificada que debe ser representada.|
|Modo|Uno de los siguientes valores:<ul><li>Inserción</li><li>Edición</li><li>Solo lectura</li></ul>Si selecciona _Insertar_ indica que el formulario debe insertar un nuevo registro tras el envío. Especificar _Editar_ indica que el formulario deben modificar un registro existente. Si selecciona _ReadOnly_ indica que el formulario debe mostrar el formulario no editable de un registro existente. _Editar_ y _ReadOnly_ requieren que exista un registro de origen y los parámetros especificados en los campos 'Tipo de origen de registro' y 'Nombre del parámetro de cadena de consulta de id. de registro' para seleccionar el registro adecuado cuando el formulario se carga en el portal.|
|Tipo de origen de registro|Uno de los siguientes valores:<ul><li>Cadena de consulta</li><li>Usuario actual del portal</li><li>Registro asociado al usuario actual del portal</li></ul>Si selecciona _Cadena de consulta_ se requiere un nombre de parámetro que se debe proporcionar en la cadena de consulta de la dirección URL del formulario. Esto se puede especificar en el campo 'Nombre del parámetro de cadena de consulta de id. de registro'.<br>Si selecciona _Usuario actual del portal_ se recuperará el registro de usuario del portal para el usuario autenticado actual.<br>Si selecciona _Registro asociado al usuario actual del portal_ se recuperará el registro de usuario del portal para el usuario actual autenticado y después se recuperará el registro para la relación dada especificada por el campo 'Nombre de relación'.|
|Nombre del parámetro de cadena de consulta de id. de registro|    Un nombre de parámetro proporcionado en la cadena de consulta de la dirección URL de la página web que contienen este formulario de entidad.|
|Nombre de la relación|    Requerido cuando Tipo de origen del registro es Registro asociado al usuario actual del portal. El nombre lógico de la relación entre el registro de usuario del portal actual y el registro de destino. Esto debe devolver el mismo tipo de entidad especificado por el campo Nombre de entidad.|
|Permitir creación si es nulo|    Un valor booleano opcional disponible cuando Tipo de origen del registro es Registro asociado al usuario actual del portal. Indica que si no existe el registro relacionado, se permite que el usuario lo cree la primera vez, en caso contrario se lanzará una excepción si el registro no existe aún, pues el formulario necesita un registro con el que enlazar datos.|
|Habilitar permisos de entidad|    Hará que el formulario respete permisos de entidad. El valor predeterminado es false por razones de compatibilidad con versiones anteriores. Si se establece como true, SE REQUERIRÁN permisos explícitos para cualquier usuario que desee obtener acceso al formulario.|
|||

### <a name="form-options"></a>Opciones de formulario

|Nombre|Descripción|
|----|---------|
|Agregar captcha|    Muestra captcha.|
|Mostrar captcha para usuarios autenticados|    Muestra captcha para usuarios autenticados.|
|Grupo de validación|    El nombre de grupo asignado a los controles de entrada para evaluar entrada válida de grupos con nombre.|
|Generar automáticamente pasos desde pestañas|    Indica que múltiples pestañas en un formulario de entidad se mostrarán con cada pestaña como paso secuencial que comienza con la primera pestaña y continúa hasta recorrer todas las pestañas y tras el envío final se inserta un registro. De forma predeterminada no está seleccionado. El valor predeterminado indica que sólo un formulario o pestaña debe ser representado para el paso actual. Si el Nombre de pestaña no se especifica, aparecerá la primera pestaña.|
|Representar recursos web insertados|    Elimina el iframe que abarca un recurso web en un formulario de entidad .|
|Informaciones sobre herramientas habilitadas|    La información sobre herramientas se establece utilizando la descripción del atributo de la entidad de destino.|
|Mostrar campos no compatibles|    Todos los campos son compatibles actualmente. Esto se reserva para los cambios potenciales que Common Data Service pueda hacer en los tipos de campo.|
|Establecer campos recomendados como obligatorios|     Hace que sean obligatorios todos los atributos que tengan el nivel de requisito del campo establecido en 'Recomendado por la empresa'.|
|Hacer que todos los campos sean obligatorios|     Hace que sean obligatorios todos los campos independientemente del nivel de requisito del campo.|
|Clase CSS de resumen de validación|    Nombre de clase CSS asignado el resumen de validación. El valor predeterminado es 'validation-summary alert alert-error alert-block'|
|Habilitar vínculos de resumen de validación|    Un valor booleano de true o false de que indica si los vínculos de delimitador deben representarse en el resumen de validación para desplazarse al campo que contiene un error. El valor predeterminado es true.|
|Texto del vínculo de resumen de validación|    La etiqueta asignada a los vínculos de resumen de validación. El valor predeterminado es 'haga clic aquí'.|
|Texto del encabezado de resumen de validación|    La etiqueta asignada al encabezado de resumen de validación.|
|Instrucciones|    Instrucciones para trabajar con el formulario.|
|Mensaje No se encuentra el registro|    Mensaje para mostrar cuando no se encuentra un registro.|
|||

### <a name="on-success-settings"></a>Configuración en caso de éxito

|Nombre|Descripción|
|----|----------|
|En caso de éxito|    Uno de los siguientes valores:<ul><li>Mostrar mensaje de correcto (opción predeterminada)</li><li>Redirigir</li></ul>|
|Ocultar formulario en caso de éxito|    Requiere que En caso de éxito se establezca como Mostrar mensaje de correcto. Cuando se selecciona, el formulario está oculto tras el envío correcto del formulario.|
|Mensaje de correcto|    Requiere que En caso de éxito se establezca como Mostrar mensaje de correcto. El mensaje se muestra al usuario tras el envío correcto. Si no se especifica uno se mostrará un mensaje predeterminado ("Envío completado correctamente”). Para cada paquete de idioma instalado y activado para la organización un campo estará disponible para especificar el mensaje en el idioma asociado.|
|Dirección URL externa|Requiere establecer En caso de éxito como Redirigir. Especifique una dirección URL a un recurso externo de la web.
|o página web|Requiere establecer En caso de éxito como Redirigir. Seleccione una página web desde el sitio web actual.|
|Anexar cadena de consulta existente|    Requiere establecer En caso de éxito como Redirigir. Cuando seleccionada esta opción, los parámetros de cadena de consulta existente se agregarán a la dirección URL de destino antes del redireccionamiento.|
|Anexar id. de registro a la cadena de consulta|     Requiere establecer En caso de éxito como Redirigir. Cuando seleccionada esta opción, el Id. del registro creado se anexa a cadena de consulta de la dirección URL a la que se está realizando el redireccionamiento.|
|Nombre del parámetro de cadena de consulta de id. de registro|     Requiere establecer En caso de éxito como Redirigir. El nombre del parámetro Id. de la cadena de consulta de la dirección URL a la que se está realizando el redireccionamiento.|
|Anexar cadena de consulta personalizada|    Requiere establecer En caso de éxito como Redirigir. Una cadena personalizada que se puede anexar a la cadena de consulta existente de la dirección URL de redireccionamiento.|
|Anexar valor de atributo a la cadena de consulta: nombre de parámetro|    Requiere establecer En caso de éxito como Redirigir. Un nombre para dar al parámetro que se correlaciona con el valor de atributo de la entidad de destino que se anexa a cadena de consulta de la dirección URL de redireccionamiento.|
|Anexar valor de atributo a la cadena de consulta: nombre lógico de atributo|Requiere establecer En caso de éxito como Redirigir. Un nombre lógico de un atributo en la entidad de destino para obtener el valor que se anexa a cadena de consulta de la dirección URL de redireccionamiento.|
|||

### <a name="additional-settings"></a>Configuración adicional

|Nombre|Descripción|
|----|----------|
|Asociar usuario actual del portal|    Indica que el registro del usuario que ha iniciado sesión actualmente se debe asociar al registro de la entidad de destino.|
|Atributo de búsqueda de usuarios del portal de la entidad de destino|    El nombre lógico del atributo de la entidad de destino que almacena el usuario del portal.|
|Es grupo de actividad|    Valor booleano que indica si el Atributo de búsqueda de usuarios del portal de la entidad de destino es un tipo del grupo de actividad.|
|Adjuntar archivo |  Seleccionar para que el formulario incluya un control de carga de archivos en la parte inferior del formulario para permitir adjuntar un archivo al registro. <br> **Nota**: Portales con [versión 9.2.2.x y posterior](https://support.microsoft.com/help/4541765/power-apps-portals-version-9-2-2-x-release) no requieren habilitar **Habilitar permisos de entidad** en el formulario de entidad para adjuntar archivos. Sin embargo, si lo ha seleccionado, debe asegurarse de que se otorguen los privilegios apropiados en la entidad principal y la entidad de anotación para mostrar el botón **Adjuntar archivo** en el formulario. La entidad de anotación debe tener al menos privilegios **Crear** y **Adjuntar** privilegios y la entidad matriz debe tener el correspondiente privilegio **AppendTo**. Dependiendo de si tiene un formulario de creación o actualización, también puede necesitar **Crear**, **Leer** y **Escribir** privilegios para completar el escenario del formulario. |
|Ubicación de almacenamiento de archivos adjuntos|    Opciones: Datos adjuntos de nota, Almacenamiento de blobs de Azure. Si su organización está configurada para utilizar Azure Storage, puede elegir almacenar los archivos cargados para este formulario de entidad allí. De lo contrario, los archivos se almacenarán como Datos adjuntos de nota.|
|Permitir varios archivos|Valor booleano que indica si el usuario puede cargar más de un archivo.|
|Aceptar|    El atributo de aceptación especifica los tipos MIME de archivos que el servidor acepta a través de la carga de archivos. Para especificar más de un valor, separe los valores con comas (por ejemplo, audio/*,video/*,image/*).|
|Etiqueta|    Texto mostrado junto al control de carga de archivos. Para cada paquete de idioma instalado y activado para la organización un campo estará disponible para especificar el mensaje en el idioma asociado.|
|Obligatorio adjuntar archivo| Hace que avancen los datos adjuntos de un archivo requerido.|
|Mensaje de error obligatorio|El mensaje mostrado durante la validación de formulario si Es obligatorio es true y el usuario no ha adjuntado un archivo. Para cada paquete de idioma instalado y activado para la organización un campo estará disponible para especificar el mensaje en el idioma asociado.|
|Restringir archivos a los tipos aceptados|    Fuerza validación en el campo de Aceptar. Si no se selecciona, el atributo de Aceptar se usará únicamente como sugerencia para el diálogo de carga de archivos.|
|Mensaje de error de tipo de archivo|El mensaje mostrado durante la validación de formulario si Restringir archivos a los tipos aceptados es True y el usuario ha intentado cargar un tipo de archivo no válido. Para cada paquete de idioma instalado y activado para la organización un campo estará disponible para especificar el mensaje en el idioma asociado.|
|Tamaño máximo de archivo (en kilobytes)|    Fuerza la validación en el tamaño máximo permitido del archivo cargado.|
|Mensaje de error de tamaño de archivo|    El mensaje mostrado durante la validación de formulario si Tamaño máximo de archivo (en kilobytes) es True y el usuario ha intentado cargar un archivo que es demasiado grande. Para cada paquete de idioma instalado y activado para la organización un campo estará disponible para especificar el mensaje en el idioma asociado.|
|JavaScript personalizado|    Un bloque personalizado de JavaScript que se agregará a la parte inferior de la página justo delante el elemento de etiqueta de formulario de cierre. El identificador de entrada HTML de un campo de entidad se define con el nombre lógico del atributo. Esto facilita la selección de un campo, el establecimiento de valores u otras manipulaciones del lado del cliente con jQuery.<br>`$(document).ready(function() {   $("#address1_stateorprovince").val("Saskatchewan");});`|
|||

### <a name="entity-reference"></a>Referencia de entidad

Los siguientes parámetros pertenecen al establecimiento de una referencia de entidad al guardar el formulario.

Esto proporciona una forma de asociar el registro actual que crea o actualiza el formulario con otro registro de destino. Esto es útil si tiene varios pasos con tipos de entidad múltiple y desea relacionar los registros resultantes o si se pasa a la página una cadena de consulta de un identificador de registro que desea asociar. Por ejemplo tenemos una página de trabajo que incluye registros de trabajo, cada uno con un vínculo a una solicitud del trabajo que contiene el identificador del registro de trabajo al formulario de solicitud de forma que cuando se crea la solicitud, el registro de trabajo se asocia con el registro. 

|Nombre|Descripción|
|-----|---------|
|Establecer referencia de entidad al guardar|Sí o No. Un valor de sí indica que una referencia de entidad debe asignarse al guardar el formulario, en caso contrario no se establecerá ninguna.|
|Nombre de la relación|El Nombre de definición de relación para una determinada relación entre dos tipos de entidad.|
|Nombre lógico de la entidad|El nombre lógico de la entidad de referencia.|
|Nombre lógico del atributo de búsqueda de destinos|Nombre lógico del atributo de búsqueda en la entidad de destino que se crea o actualiza.|
|Rellenar campo de búsqueda|    Si la búsqueda relativa a la entidad de referencia se encuentra en el formulario, al activar este valor se completará el campo del formulario con el valor recuperado mediante el valor siguiente.|
|Tipo de origen de entidad de referencia|    Uno de los siguientes valores:<ul><li>Cadena de consulta</li><li>Usuario actual del portal</li><li>Resultado del paso anterior</li></ul> Si selecciona _Cadena de consulta_ se requiere un nombre de parámetro que se debe proporcionar en la cadena de consulta de la dirección URL del formulario. Esto se puede especificar en el campo **Nombre de cadena de consulta**. Si este parámetro es la clave principal, seleccione Sí para **La cadena de consulta es la clave principal**, en caso contrario, seleccione No y proporcione el nombre lógico del atributo de la entidad de destino para consultar por lo especificado en el campo **Nombre lógico del atributo de consulta**.  Si selecciona Usuario actual del portal se recuperará el registro de contacto para el usuario autenticado actual. Al seleccionar Resultado del paso anterior se recuperará el registro creado como resultado del paso antes del paso actual o de un paso específico basado en el paso asociado con el paso de origen de entidad.|
|Paso de entidad de referencia|    El registro del paso del formulario web de un paso anterior para recuperar la entidad creada o modificada en dicho paso para asociarlo con el registro de este paso actual.|
|Nombre de cadena de consulta|    Nombre de parámetro proporcionado en la cadena de consulta de la dirección URL de la página web que contienen el formulario web.|
|La cadena de consulta es la clave principal|    Sí indica que el valor de cadena de consulta es el valor de clave principal. No indica que el valor de cadena de consulta es un tipo de atributo distinto de la clave principal.|
|Nombre lógico del atributo de consulta|    Nombre lógico del atributo para consultar el registro.|
|Mostrar detalles de solo lectura|    Indica que un formulario debe representarse en la parte superior de la página que muestra información de solo lectura referente al registro de referencia. Requiere un nombre de formulario.|
|Nombre del formulario|    El nombre del formulario de la entidad de referencia que debe utilizarse para mostrar detalles de solo lectura.|
|||


## <a name="entity-form-action-configuration"></a>Configuraciones de acciones de formulario de entidad

De forma predeterminada un formulario de entidad permitirá leer o actualizar un registro existente, o la inserción de un nuevo registro.  Sin embargo, también puede habilitar y configurar fácilmente acciones adicionales para los registros de un formulario de entidad (eliminar, activar, desactivar, etc.). También es posible reemplazar etiquetas predeterminadas, tamaños, y otros atributos que aparecerán si hay acciones habilitadas.

Estos valores se encuentran en la sección **Configuración adicional** del formulario de entidad. De forma predeterminada, sólo aparece **Configuración básica**. Puede seleccionar **Configuración avanzada** para mostrar configuración adicional.

Puede agregar los botones de acción para las acciones que son aplicables a un registro individual y aparecerán para cada fila de la cuadrícula siempre que el privilegio apropiado haya sido otorgado por [permisos de entidad](assign-entity-permissions.md). Las siguientes acciones están disponibles:

- Eliminar
- Flujo de trabajo
- Crear registro relacionado
- Activar
- Desactivar

Haga clic en una de estas opciones para mostrar un área de configuración para dicha acción. Además, determinadas entidades tienen acciones específicas que están disponibles para estos por entidad:

- Calcular valor de oportunidad (oportunidad)
- Cancelar acción del caso (incidente)
- Cerrar (resolver) acción de caso (incidente)
- Convierta oferta en pedido (oferta)
- Convertir pedido en factura (salesorder)
- Generar oferta a partir de oportunidad (oportunidad)
- Perder acción de oportunidad (oportunidad)
- Ganar acción de oportunidad (oportunidad)
- Reabrir acción del caso (incidente)
- Establecer oportunidad en espera (oportunidad)

> [!NOTE]
> Se recomienda crear un flujo de trabajo en lugar de agregar un botón **Activar** o **Desactivar** para las entidades listas para usar después de definir valores de **estado** y **código de estado** específico que necesitan para sus procesos de negocio. Por ejemplo, incidente ([opciones de estado](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/incident#statuscode-options)), oportunidad ([opciones de estado](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/opportunity#statuscode-options)), derechos ([opciones de estado](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/entitlement#statuscode-options)). 


## <a name="geolocation-configuration-for-entity-forms"></a>Configuración de ubicación geográfica para formularios de entidad

Un formulario administrado se puede configurar para mostrar un control de mapa para que se muestre una ubicación existente como una chincheta en un mapa o proporcionar la capacidad de que el usuario especifique una ubicación. Vea [Agregar ubicación geográfica](add-geolocation.md).

El control de mapa del formulario requiere configuración adicional para indicarle cuáles son los id. de los diferentes campos de ubicación para poder asignar o recuperar valores. El registro del formulario de entidad tiene una sección de configuración que define las asignaciones de campo que debe especificar. Los nombres de campo variarán en función del esquema que ha elegido.

![Datos de ubicación geográfica en formulario de entidad](../media/geolocation-managed-form.png "Datos de ubicación geográfica en formulario de entidad") 

> [!Note]
> - El campo de dirección de un formulario de entidad de solo lectura se reemplaza por el mapa si la ubicación geográfica está habilitada.
> - La sección de ubicación geográfica no podrá verse en el entorno de la nube soberana alemana. Si un usuario ha habilitado la ubicación geográfica con otro formulario, no se mostrarán durante la representación en portal.

## <a name="request-validation"></a>Validación de solicitud

[Validación de solicitud](https://docs.microsoft.com/aspnet/whitepapers/request-validation), una característica de ASP.NET desde la versión 1.1, evita que el servidor acepte contenido que contenga HTML sin codificar. Esta característica está diseñada para ayudar a prevenir algunos ataques de inyección de script mediante los cuales el código de script del cliente o HTML pueden enviarse sin saberlo a un servidor, almacenarse y luego presentarse a otros usuarios. Seguimos recomendando encarecidamente que valide todos los datos de entrada y que los codifique en HTML cuando sea apropiado.

De forma predeterminada, la validación de solicitud está habilitada en el portal, lo que genera el siguiente error genérico si introduce código de script sin codificación HTML en los campos del formulario de entidad:

![Error de validación de solicitud](../media/request-validation-error.png)

Para deshabilitar la validación de solicitud, siga estos pasos:

1. Vaya a [configuración de portal](https://docs.microsoft.com/powerapps/maker/portals/manage-existing-portals#settings) y seleccione **Configuraciones de sitios**.

1. Seleccione **Nuevo**.

1. Escribe el nombre como **DisableValidationWebTemplate**.

1. Seleccione el registro del sitio web apropiado.

1. Escriba el valor como **true**. De forma predeterminada, la configuración es **false**, lo que permite la validación de la solicitud.

1. Escriba la descripción adecuada.

1. Seleccione **Guardar y cerrar**.

> [!CAUTION]
> Cuando la validación de solicitud está deshabitada, el contenido se puede enviar a una página. Debe asegurarse de que el contenido se codifica o procesa correctamente.

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Propiedades del formulario web para portales](web-form-properties.md)  
[Pasos de formulario web para portales](web-form-steps.md)  
[Metadatos de formularios web para portales](configure-web-form-metadata.md)  
[Configuración de la subcuadrícula de formularios web para portales](configure-web-form-subgrid.md)  
[Configuración de notas para formularios de entidad y formularios web en portales](../configure-notes.md)
