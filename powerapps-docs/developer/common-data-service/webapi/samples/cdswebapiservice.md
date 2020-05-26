---
title: API web CDSWebApiService clase (C#) (Common Data Service) | Microsoft Docs
description: Este ejemplo de proyecto de biblioteca de .NET Framework Class muestra un ensamblado para definir un cliente de servicio cuando se utiliza la API web Common Data Service y C#.
ms.custom: ''
ms.date: 04/20/2020
ms.service: powerapps
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: pehecke
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5b0b8335352d80585a9f36494bc5b8f7a06b8b2b
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276713"
---
# <a name="web-api-cdswebapiservice-class-sample-c"></a>Web API CDSWebApiService clase de muestra (C#)


Este es un proyecto de biblioteca de .NET Framework Class que crea un ensamblado para definir un cliente de servicio cuando se utiliza la API web CDS.

Esta ensamblado demuestra cómo:

- Hacer su código "[SECO](/dotnet/architecture/modern-web-apps-azure/architectural-principles#dont-repeat-yourself-dry)" al envolver operaciones comunes por métodos Http.
- Administrar un <xref:System.Net.Http.HttpClient> de manera segura para hilos.
- Administrar errores de API de límite de protección de servicio [429 Demasiadas solicitudes](https://developer.mozilla.org/docs/Web/HTTP/Status/429) que debe esperar una aplicación cliente.
    - Más información: [Límites de API de protección de servicios](../../api-limits.md)

## <a name="example"></a>Ejemplo

Este ejemplo muestra cómo crear una instancia de CDSWebAPIService y crear un registro de contacto.

Este ejemplo espera que la cadena de conexión se establezca en el archivo App.config como se muestra a continuación.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0"
                      sku=".NETFramework,Version=v4.7.2" />
  </startup>
  <connectionStrings>
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;
         Authority=null;
         ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
         RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
         UserPrincipalName=you@yourorg.onmicrosoft.com;
         Password=y0urp455w0rd;
         CallerObjectId=null;
         Version=9.1;
         MaxRetries=3;
         TimeoutInSeconds=180;
         "/>
  </connectionStrings>
</configuration>
```
El código accederá a la cadena de conexión para crear una instancia del CDSWebApiService.

```csharp
//Get configuration data from App.config connectionStrings
static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;
static readonly ServiceConfig config = new ServiceConfig(connectionString);

    using (CDSWebApiService svc = new CDSWebApiService(config))
    {
        //Create a contact
        var contact1 = new JObject
            {
                { "firstname", "Rafel" },
                { "lastname", "Shillo" }
            };
        Uri contact1Uri = svc.PostCreate("contacts", contact1);
    }
```

## <a name="properties"></a>Propiedades

Esta clase expone solo la propiedad **BaseAddress**. Este es el <xref:System.Net.Http.HttpClient.BaseAddress> configurado utilizado por el <xref:System.Net.Http.HttpClient>. Puede ser útil construir URI completos cuando sea necesario, ya que la mayoría de los casos esperarán URI relativos.

## <a name="methods"></a>Métodos

Esta proporciona los métodos públicos siguientes:

## <a name="postcreate"></a>PostCreate

Crea una entidad sincrónicamente y devuelve el URI.

### <a name="parameters"></a>Parámetros

|Nombre  |Escribir  |Descripción  |
|---------|---------|---------|
|entitySetName|<xref:System.String>|El nombre del conjunto de entidades para el tipo de entidad a crear. |
|cuerpo|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|Contiene los datos para que la entidad a crear|

### <a name="return-value"></a>Valor devuelto

El <xref:System.Uri> de la unidad creada

### <a name="remarks"></a>Comentarios

Este método se proporciona porque la creación de entidades es una operación común y el URI se devuelve en el encabezado `OData-EntityId`. Tener este método especializado permite menos código que tener solo el método [Enviar](#post), que devuelve solo un [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm).

Más información_ [Recuperar un registro de entidad usando la API web](../create-entity-web-api.md).

## <a name="postcreateasync"></a>PostCreateAsync

La versión asincrónica de [PostCreate](#postcreate).

## <a name="post"></a>Publicación

Envía una solicitud `POST` sincrónicamente y devuelve la respuesta como un [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm).

### <a name="parameters"></a>Parámetros

|Nombre  |Escribir  |Descripción  |
|---------|---------|---------|
|path|<xref:System.String>|La ruta relativa para enviar la solicitud. Con frecuencia, el nombre de una acción o un nombre de conjunto de entidades.|
|cuerpo|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|La carga útil para `POST`|
|encabezados|`Dictionary<string, List<string>>`|(Opcional) Cualquier encabezado necesario para aplicar comportamientos especiales|

### <a name="return-value"></a>Valor devuelto

Un [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) que contiene la respuesta.

### <a name="remarks"></a>Comentarios

Este método se puede usar para cualquier operación que use el método http `POST`, pero solo incluye el contenido de la respuesta. Use [PostCreate](#postcreate) para crear entidades y devolver solo el URI de la entidad creada.

Más información:

- [Crear con datos devueltos](../create-entity-web-api.md#create-with-data-returned)
- [Usar acciones de la API web](../use-web-api-actions.md)


## <a name="postasync"></a>PostAsync

La versión asincrónica de [Post](#post).

## <a name="patch"></a>Revisión

Envía una solicitud `PATCH` sincrónicamente.

### <a name="parameters"></a>Parámetros

|Nombre  |Escribir  |Descripción  |
|---------|---------|---------|
|uri|<xref:System.Uri>|La ruta relativa para enviar la solicitud. Con frecuencia el Uri para una entidad específica|
|cuerpo|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|La carga útil para enviar|
|encabezados|`Dictionary<string, List<string>>`|(Opcional) Cualquier encabezado necesario para aplicar comportamientos especiales|

### <a name="remarks"></a>Comentarios

El parche se usa con frecuencia para actualizar o actualizar registros.

Más información:

- [Actualización básica](../update-delete-entities-using-web-api.md#basic-update)
- [Aplicar Upsert a una entidad](../update-delete-entities-using-web-api.md#upsert-an-entity)

## <a name="patchasync"></a>PatchAsync

La versión asincrónica de [Patch](#patch).

## <a name="get"></a>Get

Envía una solicitud `GET` sincrónicamente y devuelve datos

### <a name="parameters"></a>Parámetros

|Nombre  |Escribir  |Descripción  |
|---------|---------|---------|
|path|<xref:System.String>|La ruta relativa del recurso a devolver |
|encabezados|`Dictionary<string, List<string>>`|(Opcional) Cualquier encabezado necesario para aplicar comportamientos especiales|

### <a name="return-value"></a>Valor devuelto

Un [JToken](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JToken.htm) representando los datos solicitados.

### <a name="remarks"></a>Comentarios

Más información:

- [Consultar datos utilizando la API web](../query-data-web-api.md)
- [Recuperar un registro de entidad usando la API web](../retrieve-entity-using-web-api.md)
- [Usar funciones de la API web](../use-web-api-functions.md)


## <a name="getasync"></a>GetAsync

La versión asincrónica de [Get](#get).

## <a name="delete"></a>Eliminar

Envía una solicitud `DELETE` sincrónicamente.

### <a name="parameters"></a>Parámetros

|Nombre  |Escribir  |Descripción  |
|---------|---------|---------|
|uri|<xref:System.Uri>|La ruta relativa del recurso a eliminar |
|encabezados|`Dictionary<string, List<string>>`|(Opcional) Cualquier encabezado necesario para aplicar comportamientos especiales|

### <a name="remarks"></a>Comentarios

Más información:

- [Eliminación básica](../update-delete-entities-using-web-api.md#basic-delete)
- [Quite una referencia a una entidad](../associate-disassociate-entities-using-web-api.md#remove-a-reference-to-an-entity)
- [Eliminar un solo valor de propiedad](../update-delete-entities-using-web-api.md#delete-a-single-property-value)

## <a name="deleteasync"></a>DeleteAsync

La versión asincrónica de [Delete](#delete).

## <a name="put"></a>Colocar

Envía una solicitud `PUT` sincrónicamente.

### <a name="parameters"></a>Parámetros

|Nombre  |Escribir  |Descripción  |
|---------|---------|---------|
|uri|<xref:System.Uri>|La ruta relativa al recurso a actualizar.|
|propiedad|<xref:System.String>|El nombre de la propiedad a actualizar|
|valor|<xref:System.String>|El valor que se va a establecer|

### <a name="remarks"></a>Comentarios

Put se usa para actualizar propiedades específicas de la entidad.

**Nota**: el método Http `PUT` también se utiliza para actualizar los metadatos. Este método no puede usarse para ese propósito. Es específicamente para datos profesionales.

Más información: 

- [Actualizar un solo valor de propiedad](../update-delete-entities-using-web-api.md#update-a-single-property-value)
- [Cambie la referencia en una propiedad de navegación de un solo valor](../associate-disassociate-entities-using-web-api.md#change-the-reference-in-a-single-valued-navigation-property)


## <a name="putasync"></a>PutAsync

La versión asincrónica de [Put](#put).

## <a name="private-sendasync-method"></a>Método privado SendAsync

Todos los métodos anteriores redirigen sus solicitudes a través del método `SendAsync`. Aquí es donde ocurre la lógica común de bajo nivel.

Este método contiene la lógica para administrar los errores API 429 de Service Protection y para volver a intentarlos varias veces configurables en el servicio.

Para hacer esto, envía una copia de la solicitud en lugar de la solicitud real porque la solicitud se eliminará y no se puede volver a enviar si se devuelve un error.

La copia de la solicitud está disponible debido al método personalizado <xref:System.Net.Http.HttpRequestMessage> `Clone` definido en el archivo Extensions.cs.

## <a name="oauthmessagehandler"></a>OAuthMessageHandler

Cuando el <xref:System.Net.Http.HttpClient> interno se inicializa en el constructor CDSWebApiService, una instancia de esta clase se establece como un <xref:System.Net.Http.HttpMessageHandler>. Esta clase funciona con las bibliotecas ADAL para garantizar que `accessToken` se actualizará cada vez que se envíe una solicitud. Si el `accessToken` caduca, los métodos de la biblioteca ADAL lo actualizarán automáticamente.

Más información: [Ejemplo que demuestra un DelegatingHandler](../../authenticate-oauth.md#example-demonstrating-a-delegatinghandler)

## <a name="serviceconfig"></a>ServiceConfig

La clase CDSWebApiService debe inicializarse con una cadena de conexión a través de la clase ServiceConfig.

El constructor ServiceConfig acepta una cadena de conexión, generalmente de la configuración App.config, y los datos definidos allí se analizan en una instancia de ServiceConfig que requiere el constructor CDSWebApiService.

### <a name="properties"></a>Propiedades

Estas son las propiedades de la clase ServiceConfig.

|Nombre|Escribir|Descripción|
|---------|---------|---------|
|Autoridad|<xref:System.String>|La autoridad para usar para autorizar al usuario. El valor predeterminado es "https://login.microsoftonline.com/common"|
|CallerObjectId|<xref:System.Guid>|Los Azure AD ObjectId para que el usuario se haga pasar por otros usuarios.|
|ClientId|<xref:System.String>|El identificador de la aplicación registrada con Azure AD|
|MaxRetries|<xref:System.Byte>|El número máximo de intentos para volver a intentar una solicitud bloqueada por los límites de protección del servicio. El valor predeterminado es 3.|
|Contraseña:|<xref:System.Security.SecureString>|Contraseña del usuario del principal|
|RedirectUrl|<xref:System.String>|La URL de redireccionamiento de la aplicación registrada con Azure AD|
|TimeoutInSeconds|`ushort`|La cantidad de tiempo para intentar completar una solicitud antes de que se cancele. El valor predeterminado es 120 (2 minutos)|
|URL|<xref:System.String>|La URL del entorno CDS, es decir "https://yourorg.api.crm.dynamics.com"|
|UserPrincipalName|<xref:System.String>|El nombre principal de usuario del usuario. Es decir, you@yourorg.onmicrosoft.com|
|Versión|<xref:System.String>|La versión de la API web a utilizar. El valor predeterminado es "9.1"|

### <a name="example-connection-string"></a>Ejemplo de cadena de conexión

Cada una de las muestras que usa CDSWebApiService incluye una referencia a un App.config común y un código para leer un valor de cadena de conexión llamado "`Connect`". El siguiente es un ejemplo de ese App.config:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0"
                      sku=".NETFramework,Version=v4.7.2" />
  </startup>
  <connectionStrings>
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;
         Authority=null;
         ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
         RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
         UserPrincipalName=you@yourorg.onmicrosoft.com;
         Password=y0urp455w0rd;
         CallerObjectId=null;
         Version=9.1;
         MaxRetries=3;
         TimeoutInSeconds=180;
         "/>
  </connectionStrings>
</configuration>
```

Los valores **ClientId** y **RedirectUrl** son para aplicaciones de ejemplo. Puede usarlos para ejecutar los ejemplos, pero debe registrar sus propias aplicaciones e ingresar los valores correspondientes para estas propiedades. 

Más información: [Tutorial: Registrar una aplicación con Azure Active Directory](../../walkthrough-register-app-azure-active-directory.md).

## <a name="serviceexception"></a>ServiceException

Esta clase simplemente extiende <xref:System.Exception> y proporciona propiedades adicionales de una respuesta de error.

### <a name="properties"></a>Propiedades

|Nombre  |Escribir  |Descripción  |
|---------|---------|---------|
|Mensaje|<xref:System.String>|El mensaje devuelto por la plataforma|
|CódigoDeError|<xref:System.Int32>|El código de error devuelto por la plataforma|
|Código de estado|<xref:System.Int32>|La propiedad <xref:System.Net.Http.HttpResponseMessage>.<xref:System.Net.Http.HttpResponseMessage.StatusCode>|
|ReasonPhrase|<xref:System.String>|La propiedad <xref:System.Net.Http.HttpResponseMessage>.<xref:System.Net.Http.HttpResponseMessage.ReasonPhrase>|

## <a name="samples-using-this-class"></a>Ejemplos que usan esta clase

Los ejemplos siguientes usan esta clase:

- [Web API CDSWebApiService Ejemplo de operaciones básicas (C#)](cdswebapiservice-basic-operations.md)
- [Web API CDSWebApiService Ejemplo de operaciones en paralelo (C#)](cdswebapiservice-parallel-operations.md)
- [Web API CDSWebApiService Ejemplo de operaciones asincrónicas (C#)](cdswebapiservice-async-parallel-operations.md)