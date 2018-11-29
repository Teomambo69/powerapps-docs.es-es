---
title: openForm (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0206c43b-b1fc-490d-a867-1d75331885a8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openform-client-api-reference"></a>openForm (referencia de la API de cliente)



[!INCLUDE[./includes/openForm-description.md](./includes/openForm-description.md)]

## <a name="syntax"></a>Sintaxis

`Xrm.Navigation.openForm(entityFormOptions,formParameters).then(successCallback,errorCallback);`

## <a name="parameters"></a>Parámetros


<table style="width:100%">
  <tr>
    <th>Nombre</th>
    <th>Tipo</th> 
    <th>Obligatoria</th>
    <th>Descripción</th>
  </tr>
  <tr>
    <td>entityFormOptions</td>
    <td>Objeto</td> 
    <td>Sí</td>
    <td>Opciones de formulario de entidad para abrir el formulario. El objeto contiene los siguientes atributos:<ul>
<li><b>cmdbar</b>: booleano (opcional). Indica si se muestra la barra de comandos. Si no especifica este parámetro, la barra de comandos se muestra de forma predeterminada.</li>
<li><b>createFromEntity</b>: búsqueda (opcional). Señala un registro que proporcionará valores predeterminados según los valores de atributo asignados. El objeto de búsqueda tiene las siguientes propiedades de cadena: <code>entityType</code>, <code>id</code> y <code>name</code> (opcional).</li>
<li><b>entityId</b>: cadena (opcional). Identificador del registro de entidad para el que se va a mostrar el formulario.</li>
<li><b>entityName</b>: cadena (opcional). Nombre lógico de la entidad para la que se va a mostrar el formulario.</li>
<li><b>formId</b>: cadena (opcional). Identificador de la instancia de formulario que se va a mostrar.</li>
<li><b>height</b>: número (opcional). Alto de la ventana de formulario que se mostrará, en píxeles.</li>
<li><b>navBar</b>: cadena (opcional). Controla si la barra de navegación se muestra y si la navegación por la aplicación está disponible mediante las áreas y subáreas definidas en el mapa del sitio. Los valores válidos son: "on", "off" o "entity".<ul><li><code>on</code>: se muestra la barra de navegación. Este es el comportamiento predeterminado si el parámetro <b>navBar</b> no se usa.</li>
<li><code>off</code>: no se muestra la barra de navegación. Los usuarios pueden navegar usando otros elementos de la interfaz de usuario o los botones adelante y atrás.</li><li><code>entity</code>: en un formulario de entidad, solo están disponibles las opciones de navegación de entidades relacionadas. Después de navegar a una entidad relacionada, se muestra un botón atrás en la barra de navegación para permitir volver al registro original.</li></ul></li>
<li><b>openInNewWindow</b>: booleano (opcional). Indica si se debe mostrar el formulario en una nueva ventana.</li>
<li><b>windowPosition</b>: número (opcional). Especifique uno de los siguientes valores para la posición del formulario de la ventana en la pantalla:<ul><li><code>1:center</code></li><li><code>2:side</code></li></ul>
<li><b>processId</b>: cadena (opcional). Identificador de los procesos de negocio que se muestran en el formulario.</li>
<li><b>processInstanceId</b>: cadena (opcional). Identificador de la instancia de proceso de negocio que se muestra en el formulario.</li>
<li><b>relationship</b>: objeto (opcional). Defina un objeto de relación para mostrar los registros relacionados en el formulario. El objeto tiene los siguientes atributos.
<table style="width:100%">
  <tr>
    <th>Nombre</th>
    <th>Tipo</th> 
    <th>Descripción</th>
<tr>
<td>attributeName</td>
<td>String</td>
<td>Nombre del atributo usado para la relación.</td>
</tr>
<tr>
<td>nombre</td>
<td>String</td>
<td>Nombre de la relación.</td>
</tr>
<tr>
<td>navigationPropertyName</td>
<td>String</td>
<td>Nombre de la propiedad de navegación de esta relación.</td>
</tr>
<tr>
<td>relationshipType</td>
<td>Número</td>
<td>Tipo de relación. Especifique uno de los siguientes valores:
<ul><li><code>0:OneToMany</code></li><li><code>1:ManyToMany</code></li></ul></td>
</tr>
<tr>
<td>roleType</td>
<td>Número</td>
<td>Tipo de rol en la relación. Especifique uno de los siguientes valores:
<ul><li><code>1:Referencing</code></li><li><code>2:AssociationEntity</code></li></ul></td>
</tr>
</table>
</li>
<li><b>selectedStageId</b>: cadena (opcional). Identificador de la fase seleccionada en la instancia de proceso de negocio.</li>
<li><b>useQuickCreateForm</b>: booleano (opcional). Indica si se abre un formulario de creación rápida. Si no especifica esto, se pasa <b>false</b> de forma predeterminada.</li>
<li><b>width</b>: número (opcional). Ancho de la ventana de formulario que se mostrará, en píxeles.</li>
</ul>
</tr>
<tr>
<td>formParameters</td>
<td>Objeto</td>
<td>No</td>
<td>Un objeto de diccionario que pasa parámetros adicionales al formulario. Los parámetros no válidos provocarán un error.<br/><br/>Para obtener información acerca de cómo pasar parámetros a un formulario, consulte [Establecer valores de campo mediante parámetros que se pasan a un formulario](../../../set-field-values-using-parameters-passed-form.md) y [Configurar un formulario para aceptar parámetros de cadena de consulta personalizada](../../../configure-form-accept-custom-querystring-parameters.md) </td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td>Una función para ejecutarse cuando:
<ul>
<li>El formulario de la entidad se muestra en los registros existentes.</li>
<li>El registro se guarda en el formulario de la entidad que se muestra para un nuevo registro.</li>
<li>El registro se guarda en el formulario de creación rápida.</li>
</ul>
<b>NOTA</b>: En [Interfaz unificada](/dynamics365/get-started/whats-new/customer-engagement/new-in-july-2017-update#unified-interface-framework-for-new-apps), la función <b>successCallback</b> solo se ejecuta al guardar un registro en un formulario de creación rápida que se abrió mediante el método **openForm**.

A esta funcionalidad se le pasa un objeto como parámetro. El objeto tiene una matriz <b>savedEntityReference</b> con las siguientes propiedades para identificar el registro(s) mostrado(s) o creado(s):
<ul>
<li><b>entityType</b>: el nombre lógico de la entidad.</li>
<li><b>id</b>: Representación en cadena de un valor GUID del registro.</li>
<li><b>name</b>: El valor del atributo principal del registro mostrado o creado.</li></ul>

<b>NOTA</b>: Al abrir un formulario para un registro existente o crear un registro, <b>el savedEntityReference</b> contiene un solo artículo. Al abrir un formulario de creación rápida en [Interfaz unificada](/dynamics365/get-started/whats-new/customer-engagement/new-in-july-2017-update#unified-interface-framework-for-new-apps) y crear varios registros haciendo clic en <b>Guardar y nuevo</b>, <b>savedEntityReference</b> contendrá varios elementos, cada uno representando el registro creado mediante el formulario de creación rápida.
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Función que se ejecuta cuando la operación produce un error.<br>

<b>NOTA</b>: en [interfaz unificada](/dynamics365/get-started/whats-new/customer-engagement/new-in-july-2017-update#unified-interface-framework-for-new-apps), la función <b>errorCallback</b> se ejecutará solo si abre un formulario de creación rápida.</td>
</tr>
</table>

## <a name="remarks"></a>Comentarios

Debe usar este método para abrir formularios de entidad o de creación rápida en lugar de los métodos obsoletos [Xrm.Utility.openEntityForm](https://msdn.microsoft.com/library/jj602956.aspx#openEntityForm) y [Xrm.Utility.openQuickCreate](https://msdn.microsoft.com/library/jj602956.aspx#openQuickCreate).
 

## <a name="examples"></a>Ejemplos

### <a name="example-1-open-an-entity-form-for-existing-record"></a>Ejemplo 1: Abrir el formulario de entidad de un registro existente

El código de ejemplo siguiente abre un formulario de contacto para mostrar un registro de contacto existente:

```JavaScript
var entityFormOptions = {};
entityFormOptions["entityName"] = "contact";
entityFormOptions["entityId"] = "8DA6E5B9-88DF-E311-B8E5-6C3BE5A8B200"

// Open the form.
Xrm.Navigation.openForm(entityFormOptions).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });
```

### <a name="example-2-open-an-entity-form-for-new-record"></a>Ejemplo 2: Abrir el formulario de entidad de un registro nuevo

El código de ejemplo siguiente abre un formulario de contacto con algunos valores preestablecidos para crear un registro nuevo:

```JavaScript
var entityFormOptions = {};
entityFormOptions["entityName"] = "contact";

// Set default values for the Contact form
var formParameters = {};
formParameters["firstname"] = "Sample";
formParameters["lastname"] = "Contact";
formParameters["fullname"] = "Sample Contact";
formParameters["emailaddress1"] = "contact@adventure-works.com";
formParameters["jobtitle"] = "Sr. Marketing Manager";
formParameters["donotemail"] = "1";
formParameters["description"] = "Default values for this record were set programmatically.";

// Open the form.
Xrm.Navigation.openForm(entityFormOptions, formParameters).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });
```

### <a name="example-3-open-a-quick-create-form"></a>Ejemplo 3: Abrir una forma de creación rápida

El código de ejemplo siguiente abre un formulario de contacto de creación rápida con algunos valores preestablecidos:

```JavaScript
var entityFormOptions = {};
entityFormOptions["entityName"] = "contact";
entityFormOptions["useQuickCreateForm"] = true;

// Set default values for the Contact form
var formParameters = {};
formParameters["firstname"] = "Sample";
formParameters["lastname"] = "Contact";
formParameters["fullname"] = "Sample Contact";
formParameters["emailaddress1"] = "contact@adventure-works.com";
formParameters["jobtitle"] = "Sr. Marketing Manager";
formParameters["donotemail"] = "1";
formParameters["description"] = "Default values for this record were set programmatically.";

// Open the form.
Xrm.Navigation.openForm(entityFormOptions, formParameters).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });
```

### <a name="related-topics"></a>Temas relacionados

[Xrm.Navigation](../xrm-navigation.md)




