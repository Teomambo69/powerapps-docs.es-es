---
title: Definir formularios de entidad | MicrosoftDocs
description: Instrucciones para crear formularios de entidad en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 79e6f02f9a13f1c828efe5c472d267e707b09576
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552713"
---
# <a name="about-entity-forms"></a>Acerca de los formularios de entidad

Una configuración controlada por datos que permite a los usuarios finales agregar un formulario para recopilar datos en el portal sin necesidad de que un desarrollador muestre el formulario en el portal, los formularios de entidad se crean en Common Data Service y se colocan en páginas web en el portal o se usan en conjunción w n subcuadrículas y listas de entidades para crear aplicaciones web completas. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [acerca de las listas de entidades](entity-lists.md) 

![Formulario de contacto](../media/contact-us-form.png "Formulario de contacto")  

## <a name="add-a-form-to-your-portal"></a>Agregar un formulario al portal

El formulario de la entidad contiene relaciones con las páginas web y propiedades adicionales para controlar la inicialización del formulario en el portal. La relación con las páginas web permite la recuperación dinámica de la definición del formulario para un nodo de página determinado dentro del sitio Web. 

Para ver los formularios de entidad existentes o crear formularios de entidad nuevos, abra la [aplicación administración del portal](configure-portal.md) y vaya **a portales &gt;** formularios de **entidad**.

Al crear un nuevo formulario de entidad, el primer paso es decidir el nombre de la **entidad** y del **formulario** que se va a representar, además del **modo: inserción, edición o solo lectura**. El modo seleccionado determinará si está creando un registro nuevo desde el portal, editando un registro existente o simplemente mostrando información sobre un registro en el portal.

> [!Note]
> - Un **formulario de entidad** debe estar asociado a una página web para un sitio Web determinado para que el formulario sea visible en el sitio.
> - Las subcuadrículas de la entidad de conexión no se admiten en los formularios de entidad. Si agrega una subcuadrícula de entidad de conexión al formulario mediante el diseñador de formularios, se muestran mensajes de error al representar el formulario en el portal y usar la entidad de conexión.
> - Los campos duplicados, conjunto de opciones de selección múltiple, controles personalizados y reglas de negocios no se admiten en los formularios de entidad.
> - Las reglas de negocios y la API de cliente pueden habilitar campos bloqueados en un formulario de solo lectura.
> - Si crea un formulario de entidad en el modo de inserción, no puede cambiar la alineación de un botón o colocar un botón de acción encima del formulario de la entidad.
> - Si representa un control de búsqueda como una lista desplegable en el formulario, el filtro de registros relacionados no funcionará.

Las páginas web asociadas al formulario de la entidad se pueden ver seleccionando el vínculo **páginas web** que se muestra en los vínculos de navegación **relacionados** en el menú de la izquierda.

Al crear o editar una página web, se puede especificar un **formulario de entidad** en el campo de búsqueda proporcionado en el formulario de la Página Web.

Las distintas páginas maestras que usa el portal contienen declaraciones del control de servidor **EntityForm** . Al representar la página web que contiene la plantilla de página de página (~/Pages/Page.aspx) o la plantilla de página de página completa (~/Pages/FullPage.aspx), los controles determinarán si la búsqueda del formulario de la entidad contiene un valor, en cuyo caso se representará el formulario.

## <a name="secure-your-forms"></a>Proteger los formularios

Para proteger los formularios, debe crear permisos de entidad que determinen el acceso y la propiedad de los registros según los roles Web. Si un usuario aterriza en un formulario de entidad y no tiene permisos, recibirá un mensaje de error. Para habilitar permisos para un formulario de entidad, establezca **Habilitar permisos de entidad** en true. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [crear roles web para portales](create-web-roles.md).  

## <a name="entity-form-attributes-and-relationships"></a>Atributos y relaciones del formulario de la entidad

|Nombre|Descripción|
|-----|----------|
|Nombre|Nombre descriptivo del registro. Este campo es obligatorio.|
|Nombre de entidad|Nombre de la entidad desde la que se cargará el formulario. Este campo es obligatorio.|
|Nombre del formulario| Nombre del formulario en la entidad de destino que se va a representar. Este campo es obligatorio.|
|Nombre de la pestaña|  Nombre opcional de una pestaña en un formulario para una entidad especificada que se va a representar.|
|Modo|Uno de los siguientes valores:<ul><li>Introducir</li><li>Editar</li><li>ReadOnly</li></ul>Al seleccionar _Insertar_ se indica que el formulario debe insertar un nuevo registro tras su envío. Al especificar _Edit_ , se indica que el formulario debe editar un registro existente. Al seleccionar _ReadOnly_ se indica que el formulario debe mostrar un formulario no editable de un registro existente. _Edit_ y _ReadOnly_ requiere que exista un registro de origen y los parámetros especificados en los campos ' tipo de origen de registro ' y ' nombre de parámetro de cadena de consulta de ID. de registro ' para seleccionar el registro adecuado cuando se carga el formulario en el portal.|
|Tipo de origen de registro|Uno de los siguientes valores:<ul><li>Cadena de consulta</li><li>Usuario del portal actual</li><li>Registro asociado al usuario actual del portal</li></ul>La selección de una _cadena de consulta_ requiere un nombre de parámetro que se debe proporcionar en la cadena de consulta de la dirección URL al formulario. Se puede especificar en el campo "nombre de parámetro de cadena de consulta de ID. de registro".<br>Al seleccionar _usuario del portal actual_ , se recuperará el registro de usuario del portal para el usuario autenticado actual.<br>Al seleccionar _registro asociado al usuario del portal actual_ , se recuperará el registro de usuario del portal para el usuario autenticado actual y, a continuación, se recuperará el registro de la relación especificada según lo especificado en el campo "nombre de relación".|
|Nombre de parámetro de cadena de consulta de ID. de registro| Un nombre de parámetro proporcionado en la cadena de consulta de la dirección URL de la página web que contiene este formulario de entidad.|
|Nombre de relación| Obligatorio cuando el tipo de origen del registro es registro asociado al usuario actual del portal. El nombre lógico de la relación entre el registro de usuario del portal actual y el registro de destino. Debe devolver el mismo tipo de entidad especificado por el campo Nombre de la entidad.|
|Permitir crear si es null|  Un valor booleano opcional disponible cuando el tipo de origen del registro es registro asociado al usuario actual del portal. Indica que si el registro relacionado no existe, permite al usuario crearlo la primera vez; de lo contrario, se producirá una excepción si el registro no existe ya que el formulario necesita un registro al que se enlazarán los datos.|
|Habilitar permisos de entidad| Hará que el formulario respete los permisos de entidad. El valor predeterminado es false por motivos de compatibilidad con versiones anteriores. Si se establece en true, se requieren permisos explícitos para cualquier usuario que desee tener acceso al formulario.|
|||

### <a name="form-options"></a>Opciones de formulario

|Nombre|Descripción|
|----|---------|
|Agregar CAPTCHA|   Muestra CAPTCHA.|
|Mostrar CAPTCHA para los usuarios autenticados|  Muestra CAPTCHA para los usuarios autenticados.|
|Grupo de validación|  Nombre del grupo asignado a los controles de entrada para evaluar la entrada válida de grupos con nombre.|
|Generar automáticamente pasos desde pestañas| Indica que se mostrarán varias pestañas en un formulario de entidad con cada pestaña como un paso secuencial empezando por la primera pestaña y continuará hasta que se haya navegado por todas las pestañas hasta que se haya insertado un registro final. De forma predeterminada, no está seleccionada. El valor predeterminado indica que solo se va a representar una pestaña o formulario para el paso actual. Si no se especifica el nombre de la pestaña, se muestra la primera pestaña.|
|Representar recursos Web en línea|   Elimina el iframe que abarca un recurso Web en un formulario de entidad.|
|Información sobre herramientas habilitada|  La información sobre herramientas se establece mediante la descripción del atributo en la entidad de destino.|
|Mostrar campos no admitidos|   Actualmente se admiten todos los campos. Esto está reservado para posibles cambios Common Data Service puede realizar en tipos de campo.|
|Establecer los campos recomendados según sea necesario|    Hace que todos los atributos necesarios que tienen el nivel de requisito de campo establecido en "empresa recomendada".|
|Convertir todos los campos en obligatorios|  Hace que todos los campos sean necesarios independientemente del nivel de requisito del campo.|
|Clase CSS de Resumen de validación|  Nombre de clase CSS asignado al Resumen de validación. El valor predeterminado es ' alerta de alerta de Resumen de validación-alerta de error-bloque '|
|Habilitar vínculos de Resumen de validación|   Un valor booleano de true o false que indica si los vínculos de delimitador se deben representar en el Resumen de la validación para desplazarse hasta el campo que contiene un error. El valor predeterminado es true.|
|Texto de vínculo de Resumen de validación|  Etiqueta asignada a los vínculos de Resumen de validación. El valor predeterminado es "haga clic aquí".|
|Texto de encabezado de Resumen de validación|    Etiqueta asignada al encabezado de Resumen de validación.|
|Las|  Instrucciones para trabajar con el formulario.|
|Mensaje de registro no encontrado|  Mensaje que se va a mostrar cuando no se encuentre un registro.|
|||

### <a name="on-success-settings"></a>En configuración correcta

|Nombre|Descripción|
|----|----------|
|En caso de éxito|    Uno de los siguientes valores:<ul><li>Mostrar mensaje de operación correcta (valor predeterminado)</li><li>Redirigir</li></ul>|
|Ocultar formulario en caso de éxito|  Requiere en el conjunto correcto para mostrar el mensaje de operación correcta. Cuando se selecciona, el formulario se oculta tras el envío correcto del formulario.|
|Mensaje de operación correcta|   Requiere en el conjunto correcto para mostrar el mensaje de operación correcta. Mensaje que se muestra al usuario cuando el envío se realiza correctamente. Si no se especifica uno, se mostrará un mensaje predeterminado (el envío se completó correctamente). Para cada paquete de idioma instalado y habilitado para la organización, un campo estará disponible para escribir el mensaje en el idioma asociado.|
|Dirección URL externa|Requiere en la operación correcta establecida en redirigir. Especifique una dirección URL a un recurso externo en la Web.
|o página web|Requiere en la operación correcta establecida en redirigir. Seleccione una página web del sitio web actual.|
|Anexar cadena de consulta existente|  Requiere en la operación correcta establecida en redirigir. Cuando se selecciona, los parámetros de cadena de consulta existentes se agregarán a la dirección URL de destino antes de la redirección.|
|Anexar el ID. de registro a la cadena de consulta|  Requiere en la operación correcta establecida en redirigir. Cuando se selecciona, el ID. del registro creado se anexa a la cadena de consulta de la dirección URL a la que se redirige.|
|Nombre de parámetro de cadena de consulta de ID. de registro|     Requiere en la operación correcta establecida en redirigir. Nombre del parámetro de identificador en la cadena de consulta de la dirección URL a la que se redirige.|
|Anexar cadena de consulta personalizada|    Requiere en la operación correcta establecida en redirigir. Una cadena personalizada que se puede anexar a la cadena de consulta existente de la dirección URL de redireccionamiento.|
|Anexar el valor del atributo a la cadena de consulta: nombre del parámetro|   Requiere en la operación correcta establecida en redirigir. Nombre que se va a asignar al parámetro que se correlaciona con el valor de atributo de la entidad de destino que se anexa a la cadena de consulta de la dirección URL de redireccionamiento.|
|Anexar el valor del atributo a la cadena de consulta: nombre lógico del atributo|Requiere en la operación correcta establecida en redirigir. Nombre lógico de un atributo de la entidad de destino para obtener el valor que se va a anexar a la cadena de consulta de la dirección URL de redireccionamiento.|
|||

### <a name="additional-settings"></a>Configuración adicional

|Nombre|Descripción|
|----|----------|
|Asociar usuario del portal actual| Indica que el registro del usuario que ha iniciado sesión actualmente se debe asociar al registro de la entidad de destino.|
|Atributo de búsqueda de usuario de portal de entidad de destino|    El nombre lógico del atributo en la entidad de destino que almacena el usuario del portal.|
|Parte de la actividad| Valor booleano que indica si el atributo de búsqueda de usuario de Entity portal de destino es un tipo de entidad de actividad.|
|Adjuntar archivo|   Active esta opción para que el formulario incluya un control de carga de archivos en la parte inferior del formulario para permitir que un archivo se adjunte al registro.|
|Asociar ubicación de File Storage|  Opciones: datos adjuntos de nota, Azure Blob Storage. Si su organización está configurada para usar Azure Storage, puede optar por almacenar allí los archivos cargados para este formulario de la entidad. De lo contrario, los archivos que se almacenan como datos adjuntos de nota.|
|Permitir varios archivos|Valor booleano que indica si el usuario puede cargar más de un archivo.|
|acept|    El atributo Accept especifica los tipos MIME de archivos que el servidor acepta a través de la carga de archivos. Para especificar más de un valor, separe los valores con una coma (por ejemplo, audio/ *, vídeo/* , imagen/*).|
|Etiquetas| Texto que se muestra junto al control de carga de archivos. Para cada paquete de idioma instalado y habilitado para la organización, un campo estará disponible para escribir el mensaje en el idioma asociado.|
|Se requiere adjuntar archivo| Hace que los datos adjuntos de un archivo sean necesarios para continuar.|
|Mensaje de error requerido|El mensaje que se muestra durante la validación del formulario si es necesario es true y el usuario no ha adjuntado un archivo. Para cada paquete de idioma instalado y habilitado para la organización, un campo estará disponible para escribir el mensaje en el idioma asociado.|
|Restringir archivos a tipos aceptados|  Fuerza la validación en el campo Accept. Si no se selecciona, el atributo Accept solo se utilizará como una sugerencia para el cuadro de diálogo de carga de archivos.|
|Mensaje de error de tipo de archivo|El mensaje que se muestra durante la validación del formulario si restringir archivos a tipos aceptados es true y el usuario ha intentado cargar un tipo de archivo no válido. Para cada paquete de idioma instalado y habilitado para la organización, un campo estará disponible para escribir el mensaje en el idioma asociado.|
|Tamaño máximo de archivo (en kilobytes)|  Fuerza la validación del tamaño máximo permitido del archivo cargado.|
|Mensaje de error de tamaño de archivo|   Mensaje que se muestra durante la validación del formulario si el tamaño máximo de archivo (en kilobytes) es true y el usuario intentó cargar un archivo demasiado grande. Para cada paquete de idioma instalado y habilitado para la organización, un campo estará disponible para escribir el mensaje en el idioma asociado.|
|JavaScript personalizado| Un bloque personalizado de JavaScript que se agregará a la parte inferior de la página justo antes del elemento de etiqueta de cierre del formulario. El ID. de entrada HTML de un campo de entidad se establece en el nombre lógico del atributo. Esto facilita la selección de un campo, la configuración de valores u otra manipulación del lado cliente con jQuery.<br>`$(document).ready(function() {   $(“#address1_stateorprovince”).val(“Saskatchewan”);});`|
|||

### <a name="entity-reference"></a>Referencia de entidad

Los parámetros siguientes están relacionados con la configuración de una referencia de entidad cuando se guarda el formulario.

Esto proporciona una manera de asociar el registro actual que está creando o actualizando el formulario con otro registro de destino. Esto resulta útil si tiene varios pasos con varios tipos de entidad y desea relacionar los registros resultantes o si se pasa a la página una cadena de consulta de un identificador de registro que le gustaría asociar. Por ejemplo, tenemos una página de carreras en la que se muestran los registros de trabajos, cada uno con un vínculo a una aplicación para el trabajo que contiene el identificador de la publicación del trabajo en el formulario de la aplicación, de modo que cuando se cree la aplicación el registro del trabajo esté asociado con el registro. 

|Nombre|Descripción|
|-----|---------|
|Establecer referencia de entidad al guardar|Sí o no. Un valor de Yes indica que se debe asignar una referencia de entidad cuando se guarda el formulario; de lo contrario, no se establecerá ninguno.|
|Nombre de relación|Nombre de la definición de relación para una relación determinada entre dos tipos de entidad.|
|Nombre lógico de entidad|Nombre lógico de la entidad de referencia.|
|Nombre lógico del atributo de búsqueda de destino|Nombre lógico del atributo de búsqueda en la entidad de destino que se va a crear o actualizar.|
|Rellenar campo de búsqueda| Si la búsqueda relacionada con la entidad de referencia está en el formulario, al activar este valor se rellenará el campo del formulario con el valor recuperado mediante la configuración siguiente.|
|Tipo de origen de entidad de referencia|  Uno de los siguientes valores:<ul><li>Cadena de consulta</li><li>Usuario del portal actual</li><li>Resultado del paso anterior</li></ul> La selección de una _cadena de consulta_ requiere un nombre de parámetro que se debe proporcionar en la cadena de consulta de la dirección URL al formulario. Se puede especificar en el campo **nombre** de la cadena de consulta. Si este parámetro es la clave principal, seleccione sí en la **cadena de consulta es la clave principal**; de lo contrario, seleccione no y proporcione el nombre lógico del atributo en la entidad de destino que se va a consultar según se especifica en el campo **nombre lógico del atributo de consulta** .  Al seleccionar usuario del portal actual, se recuperará el registro del contacto para el usuario autenticado actual. Si selecciona resultado en el paso anterior, se recuperará el registro creado como resultado del paso anterior al paso actual o de un paso específico según el paso asociado al paso de origen de la entidad.|
|Paso de entidad de referencia| El registro de paso del formulario web de un paso anterior para recuperar la entidad creada o editada en ese paso para asociarla con el registro para este paso actual.|
|Nombre de cadena de consulta| Nombre del parámetro proporcionado en la cadena de consulta de la dirección URL de la página web que contiene el formulario Web Forms.|
|La cadena de consulta es la clave principal|   Sí indica que el valor de la cadena de consulta es el valor de la clave principal. No indica que el valor de la cadena de consulta es un tipo de atributo distinto de la clave principal.|
|Nombre lógico del atributo de consulta|  Nombre lógico del atributo para consultar el registro.|
|Mostrar detalles de solo lectura| Indica que se debe representar un formulario en la parte superior de la página que muestra información de solo lectura relativa al registro de referencia. Requiere un nombre de formulario.|
|Nombre del formulario| Nombre del formulario en la entidad de referencia que se debe usar para mostrar los detalles de solo lectura.|
|||


## <a name="entity-form-action-configuration"></a>Configuración de la acción del formulario de la entidad

De forma predeterminada, un formulario de entidad permitirá la lectura o actualización de un registro existente, o la inserción de un nuevo registro.  Sin embargo, puede habilitar y configurar fácilmente acciones adicionales para los registros en un formulario de entidad (eliminar, activar, desactivar, etc.). También es posible invalidar las etiquetas predeterminadas, los tamaños y otros atributos que aparecerán si hay acciones habilitadas.

Esta configuración se encuentra en la sección **configuración adicional** del formulario de la entidad. De forma predeterminada, solo se muestra la **configuración básica** . Puede seleccionar la **Configuración avanzada** para mostrar la configuración adicional.

Puede agregar botones de acción para las acciones que se aplican a un registro individual y que aparecerán para cada fila de la cuadrícula siempre que los [permisos de entidad](assign-entity-permissions.md)hayan concedido el privilegio adecuado. Están disponibles las siguientes acciones:

- Elimínelos
- Flujo
- Crear registro relacionado
- Activación
- Desactivar

Al hacer clic en una de estas opciones, se muestra un área de configuración para esa acción. Además, algunas entidades tienen acciones especiales que están disponibles para cada entidad:

- Calcular el valor de la oportunidad (oportunidad)
- Cancelar acción de caso (incidente)
- Cerrar (resolver) acción de caso (incidente)
- Convertir comillas en pedido (comillas)
- Convertir el orden en factura (SalesOrder)
- Generar oferta a partir de la oportunidad (oportunidad)
- Acción de la oportunidad de pérdida (oportunidad)
- Acción de la oportunidad de ganar (oportunidad)
- Volver a abrir acción de caso (incidente)
- Establecimiento de la oportunidad en espera (oportunidad)

> [!NOTE]
> Se recomienda crear un flujo de trabajo en lugar de agregar un botón **Activar** o **desactivar para** las entidades fuera de la caja que tienen definidos los valores de **Estado** y **código de estado** específicos que necesitan para sus procesos empresariales. Por ejemplo, incidente ([Opciones de estado](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/incident#statuscode-options)), oportunidad ([Opciones de estado](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/opportunity#statuscode-options)), derechos ([Opciones de estado](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/entitlement#statuscode-options)). 


## <a name="geolocation-configuration-for-entity-forms"></a>Configuración de geolocalización para formularios de entidad

Un formulario administrado puede configurarse para mostrar un control de mapa con el fin de mostrar una ubicación existente como un PIN en un mapa o para proporcionar a los usuarios la posibilidad de especificar una ubicación. Consulte [Agregar geolocation](add-geolocation.md).

El control de mapa del formulario requiere una configuración adicional para indicarle los identificadores de los distintos campos de ubicación, para asignarles valores o recuperar valores de ellos. El registro del formulario de la entidad tiene una sección de configuración que define estas asignaciones de campos que se deben especificar. Los nombres de campo variarán en función del esquema que se haya creado.

![Datos de geolocalización en el formulario de la entidad](../media/geolocation-managed-form.png "Datos de geolocalización en el formulario de la entidad") 

> [!Note]
> - El campo Dirección de un formulario de entidad de solo lectura se sustituye por el mapa cuando la ubicación geográfica está habilitada.
> - La sección geolocation no es visible en el entorno de nube soberano. Si un usuario ha habilitado la geolocalización con un formato diferente, no se mostrará durante la representación en el portal.

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Propiedades de formularios Web para portales](web-form-properties.md)  
[Pasos de Web Form para portales](web-form-steps.md)  
[Metadatos de formularios Web Forms para portales](configure-web-form-metadata.md)  
[Configuración de subcuadrículas de formularios Web Forms para portales](configure-web-form-subgrid.md)  
[Configuración de notas para formularios de entidad y formularios Web Forms para portales](../configure-notes.md)
