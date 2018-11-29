---
title: Proveedores de datos de entidades virtuales personalizados (Common Data Service para aplicaciones) | MicrosoftDocs
description: 'Al utilizar el SDK de datos de CDS for Apps, los desarrolladores de .NET tienen la opción de crear proveedores de datos de entidad virtuales personalizados con el fin de integrar los tipos de orígenes de datos externos que no admite un proveedor de datos existente.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d329dade-16c5-46e9-8dec-4b8efb996d22
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="custom-virtual-entity-data-providers"></a>Proveedores de datos de entidad virtuales personalizados

Al utilizar el SDK de datos de CDS for Apps, los desarrolladores de .NET tienen la opción de crear proveedores de datos de entidad virtuales personalizados con el fin de integrar los tipos de orígenes de datos externos que no admite un proveedor de datos existente. Cada proveedor de datos consta de un conjunto reutilizable de complementos de CDS for Apps que implementan las operaciones CRUD admitidas. (La versión inicial está limitada a las operaciones de lectura **Retrieve** y **RetrieveMultiple**.) En esta sección se ofrece información fundamental sobre los proveedores de datos y enfoques para desarrollar proveedores personalizados, incluido el código de ejemplo.

> [!NOTE]
> Como alternativa a la creación de un proveedor de origen de datos personalizado, debe considerar adaptar el origen de datos a un proveedor de datos existente. Por ejemplo, si crea una interfaz de OData v4 con el origen de datos externo entonces podrá acceder directamente a él con el proveedor de datos OData v4 estándar proporcionado. El mecanismo para agregar esta interfaz REST varía con la tecnología de servicio de datos subyacente, por ejemplo consulte [Servicios de datos de WCF 4.5](https://docs.microsoft.com/dotnet/framework/data/wcf/). OData es ampliamente compatible en el sector gracias a una gran variedad de herramientas dedicadas y tecnologías compatibles.


## <a name="prerequisites"></a>Requisitos previos

Los proveedores de datos personalizados requieren recursos de desarrollo importantes para crear y mantener. Debe tener conocimiento fundamental de las áreas siguientes:

- El esquema de origen de datos externos y las técnicas de acceso a datos asociadas.  Este conocimiento de dominio es específico del tipo de origen de datos externos.


<!-- TODO:
- CDS for Apps metadata schema: More information: [The metadata and data models in Microsoft Dynamics 365](../metadata-data-models.md).
- CDS for Apps event system: More information: [Introduction to the event framework](../introduction-event-framework.md). 
- CDS for Apps plug-in architecture and development: More information: [Plug-in development](../plugin-development.md). -->

El ensamblado de `Microsoft.Xrm.Sdk.Data.dll` está disponible como paquete de NuGet: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

<!-- ## Data Provider Architecture -->
<!-- TODO: it would be nice to have a more detailed architecture diagram of a data provider and add discussion. -->


## <a name="categories-of-providers"></a>Categorías de proveedores

Puede crear dos categorías generales de proveedor de datos con los ensamblados del SDK de datos de entidad virtual: genérico o específico. La tabla siguiente describe estos métodos y los enlaza con el modelo de desarrollo de proveedor de datos más adecuado para cada método.

|**Categoría**|**Modelo de desarrollo**|**Descripción**|
|------------|-------------|---------------|
|Genérico|Proveedor "básico"|Estos proveedores pueden traducir con flexibilidad las expresiones de la consulta de FetchXML a la solicitud asociada al origen de datos externos y luego volver a las instancias de la entidad resultantes. Este tipo de proveedor puede volver a utilizarse para todas las instancias de este tipo de origen de datos. Este método es el más general, pero es más difícil de desarrollar.  Si cambia el esquema del origen de datos, solo deberán reasignarse las entidades virtuales afectadas.|
|Específico|Proveedor LINQ para esquemas conocidos|Un proveedor de este tipo solo traduce las consultas de forma limitada a la llamada LINQ asociada a una instancia de origen de datos existente y conocida. El origen de datos debe ser un proveedor LINQ, tal como se explica en el tema [Habilitar un origen de datos para las consultas LINQ](/dotnet/csharp/programming-guide/concepts/linq/enabling-a-data-source-for-linq-querying1). Este método está limitado a una instancia de origen de datos específica, pero requiere mucho menos código. Si cambia el esquema del origen de datos, el proveedor de datos debe actualizarse y generarse de nuevo.|

El proveedor de datos Odata v4 estándar y el proveedor de datos Cosmos DB son ejemplos de proveedores genéricos.

## <a name="steps-to-use-a-custom-data-provider"></a>Pasos para usar un proveedor de datos personalizado

Hay varios pasos que se deben seguir para crear una solución de proveedor de datos de entidad virtual que se pueda importar a las aplicaciones de CDS for Apps:

1. Desarrolle el complemento DLL de proveedor de datos personalizado (o conjunto de DLL).
2. Registre el proveedor de datos personalizado con el servicio de CDS for Apps mediante la herramienta de registro de complementos (PRT).
3. Cree una solución de proveedor de datos.
4. Personalice la entidad de origen de datos para reflejar el tipo de datos o instancia específica.
5. Exporte la solución de proveedor de datos personalizada.


### <a name="plug-in-development"></a>Desarrollo de complementos

Puesto que las entidades virtuales en esta versión son de solo lectura, escribirá el proveedor de datos en forma de complemento registrado en los eventos **Retrieve** y **RetrieveMultiple**. Cada evento respectivo incluye información en el contexto de ejecución que describe el tipo de datos a devolver. 

|**Evento**|**Contexto de ejecución**|
|---------|---------------------|
|**Recuperar**|Describe qué entidad recuperar, así como los atributos y cualquier entidad relacionada que desee incluir.|
|**RetrieveMultiple**|Contiene un objeto <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> que define la consulta. El marco contiene una clase **QueryExpressionVisitor** diseñada para comprobar diferentes partes del árbol de expresión de consulta.|

Para ambos eventos, debe:

1. Convertir la información respectiva en el contexto de ejecución en una consulta compatible con el origen de datos externos.
2. Recuperar los datos del sistema externo.
3. Para **Retrieve**, convierta los datos en una <xref:Microsoft.Xrm.Sdk.Entity>; en caso contrario, para **RetrieveMultiple**, conviértalos en una <xref:Microsoft.Xrm.Sdk.EntityCollection>. Este resultado se devuelve a través de la plataforma de CDS for Apps al usuario que ejecuta la consulta. 

Las clases en el espacio de nombres <xref:Microsoft.Xrm.Sdk.Data> proporcionan un marco para ayudarle a asignar la información de la consulta de CDS for Apps desde el contexto de ejecución a una consulta en el formato adecuado para el origen de datos externos. Este mismo marco le ayudará a convertir los datos que se devuelven a los tipos <xref:Microsoft.Xrm.Sdk.Entity> o <xref:Microsoft.Xrm.Sdk.EntityCollection> adecuados que espera la plataforma de CDS for Apps. 

#### <a name="data-provider-exceptions"></a>Excepciones del proveedor de datos

Si por cualquier motivo, el código no logra el resultado previsto, deberá lanzar el error correspondiente. El espacio de nombres <xref:Microsoft.Xrm.Sdk.Data.Exceptions> contiene las siguientes clases de excepción, que se derivan de <xref:Microsoft.Xrm.Sdk.SdkExceptionBase>, que puede usar para este fin:  

|**Clase de excepción**|**Descripción**|
|---------------|-----------|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.AttributeNotFoundException>|La consulta especifica un atributo que no se encontró en el registro de datos externos asociado. Normalmente, se produce como resultado de una asignación de tipo errónea o por un cambio de esquema del origen de datos externos.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.AuthenticationException>|Se ha producido un error durante la autenticación de seguridad en el servicio de origen de datos externos. Por ejemplo: estado HTTP 401 recibido del servicio de datos externos. Normalmente, se produce porque el usuario actual no tiene privilegios adecuados o la información de conexión del **EntityDataSource** asociado no es correcta.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.EndpointException>|La configuración del extremo en la entidad de origen de datos no es válida o el extremo no existe.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.EntityNotFoundException>|La consulta está dirigida a una entidad que no existe. Normalmente, se produce como resultado de una asignación de tipo errónea o por un cambio de esquema del origen de datos externos.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.GenericDataAccessException>|Error de acceso de datos general utilizado cuando el error no encaja con una excepción más específica.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.InvalidMetadataException>| |
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.InvalidQueryException>|La consulta especificada no es válida. Por ejemplo, una combinación de cláusulas no válida u operador de comparación no compatible.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.ObjectNotFoundException>|El registro especificado en el origen de datos externos no existe.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.TimeoutException>|No se ha completado la operación externa en el tiempo permitido. Por ejemplo, el resultado de un estado HTTP 408 del servicio de datos externos.|

<!-- 
  TODO:
  To assist you in plug-in development, the Data SDK contains the _Plugin Profiler and Debugger_; for more information see [TBD]TODO: Obtain information on this tool, create subtopic. 
-->


### <a name="plug-in-registration"></a>Registro de complementos

A diferencia de un complemento normal, solo usará la herramienta de registro de complemento (PRT) para registrar el ensamblado y los complementos para cada evento. No registrará pasos específicos. El complemento se ejecutará en la fase 30, la fase de transacciones centrales principal de la operación que no está disponible para los pasos de complemento normales. En lugar de registrar pasos, configurará el proveedor de datos mediante las siguientes entidades. 


|**Entidad**|**Descripción**|
|-----|-----|
|[EntityDataProvider](../reference/entities/entitydataprovider.md)|Define los complementos a utilizar para cada evento y el nombre lógico del origen de datos.|
|[EntityDataSource](../reference/entities/entitydatasource.md)|Proporciona el contexto de la entidad y cualquier información de conexión necesaria para el origen de datos externos, incluidos los secretos necesarios para autenticar.|

Una vez configurados los metadatos de la entidad virtual, los complementos se registran con el PRT y los datos de configuración correctos se establecen en las entidades **EntityDataProvider** y **EntityDataSource**, y la entidad virtual empieza a responder a las solicitudes.

### <a name="see-also"></a>Vea también

[Introducción a las entidades virtuales](get-started-ve.md)<br />
[Consideraciones sobre API para entidades virtuales](api-considerations-ve.md)<br />
[Ejemplo: Complemento de proveedor de datos de entidad virtual genérico](sample-generic-ve-plugin.md)

 