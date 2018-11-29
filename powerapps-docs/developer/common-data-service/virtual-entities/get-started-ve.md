---
title: Introducción a las entidades virtuales (Common Data Service para aplicaciones) | Microsoft Docs
description: 'Las entidades virtuales habilitan la integración de los datos que se encuentran en sistemas externos y representan sin problemas esos datos como entidades de Common Data Service para aplicaciones, sin replicación de datos y a menudo sin código personalizado.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 14c5fbbc-98db-4e49-b245-2c84c1cd11cd
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="get-started-with-virtual-entities"></a>Introducción a las entidades virtuales

Las entidades virtuales habilitan la integración de los datos que se encuentran en sistemas externos y representan sin problemas esos datos como entidades de Common Data Service para aplicaciones, sin replicación de datos y a menudo sin código personalizado. La implementación inicial de esta característica permite solamente la compatibilidad de solo lectura de tales entidades y tiene una serie de limitaciones que se describen en la sección [Limitaciones de las entidades virtuales](#limitations-of-virtual-entities) a continuación. Además de estas limitaciones, las entidades virtuales se comportan de la misma forma que otras entidades personalizadas. 

Las entidades virtuales reemplazan los enfoques anteriores de cliente y servidor para la integración de datos externos, que requerían código personalizado y tenían numerosas limitaciones, incluidas la integración imperfecta, la duplicación de datos o el compromiso amplio de recursos de desarrollo.  Además, para los administradores y personalizadores del sistema, el uso de entidades virtuales simplifica la configuración y la administración.

> [!NOTE]
> En esta sección se describen las implicaciones de las entidades virtuales para desarrolladores. Para obtener más información sobre cómo administrar entidades virtuales de la interfaz de usuario, consulte [Crear y editar entidades virtuales que contienen datos de un origen de datos externo](../../../maker/common-data-service/create-edit-virtual-entities.md).

## <a name="virtual-entities-data-providers-and-data-sources"></a>Entidades virtuales, proveedores de datos y orígenes de datos

Una entidad virtual es una definición de una entidad en los metadatos de la plataforma CDS for Apps sin las tablas físicas asociadas para las instancias de entidad que se crean en la base de datos de CDS for Apps. Por el contrario, en tiempo de ejecución, cuando se necesita una instancia de entidad, su estado se recupera de forma dinámica desde el sistema externo asociado. Cada tipo de entidad virtual está asociado a un *proveedor de datos de entidad virtual* y (opcionalmente) a alguna información de configuración de un *origen de datos de entidad virtual* asociado. 

<!-- TODO:
A data provider is a particular type of CDS for Apps plug-in, which is registered against CRUD events that occur in the platform. This initial release only supports READ operations. More information: [Write a plug-in](../write-plugin.md) -->

Los siguientes proveedores de datos se incluyen con Common Data Service para aplicaciones:
- Un proveedor [OData v4](http://www.odata.org/documentation/) se incluye con el servicio y se instala de forma predeterminada.
- Hay un proveedor de [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) (anteriormente *Microsoft Document DB*) disponible en [AppSource](https://appsource.microsoft.com).

Los proveedores adicionales estarán disponibles a través de Microsoft, sus partners o terceros. Si no se encuentra un proveedor de datos para el origen de datos externos, puede desarrollar un *proveedor de datos de entidad virtual personalizado*; para obtener más información, consulte [proveedores de datos de entidad virtual](custom-ve-data-providers.md).

## <a name="virtual-entity-creation-and-mapping"></a>Asignación y creación de entidades virtuales

En principio, definir una entidad virtual es lo mismo que definir una entidad personalizada: hay que especificar la entidad, los atributos y las relaciones para el nuevo tipo de entidad virtual. Sin embargo, además hay que conectar la entidad virtual a un proveedor de datos para administrar la recuperación de datos. El tipo de entidad personalizada y sus campos se deben asignar a los datos correspondientes en el origen de datos externo.  Por ejemplo, una entidad virtual puede representarse como una fila en una base de datos relacional externa y cada uno de sus campos puede corresponder a una columna de esa fila.  (Tenga en cuenta que los nombres de estos datos externos con frecuencia son diferentes de los nombres de entidad virtual correspondientes). Se produce una asignación específica, necesaria para el campo de identificador de la entidad: el proveedor de datos debe ser capaz de proporcionar este GUID y asociarlo con el registro externo que representa esta instancia de entidad. La forma más directa de lograr esto es usar las GUID realmente como claves primarias en el origen de datos externo.  

En este ejemplo, también se proporciona un origen de datos de entidad virtual correspondiente para suministrar la información de usuario y de conexión para la base de datos externa.

## <a name="limitations-of-virtual-entities"></a>Limitaciones de las entidades virtuales

En esta versión, hay algunas limitaciones de las entidades virtuales que debe tener en cuenta al evaluar si puede usar entidades virtuales con los datos externos.
- Los datos son de solo lectura. La característica de entidad virtual no admite que los cambios realizados en CDS for Apps se inserten de nuevo en el sistema externo.
- Se admiten únicamente las entidades que son propiedad de la organización. No se admite el filtrado de seguridad que se aplica a entidades que son propiedad del usuario. El acceso a los datos de la entidad virtual se puede activar o desactivar para usuarios individuales según su rol de seguridad. No se admite la seguridad de nivel de campo.
- Debe ser posible modelar los datos externos como una entidad de CDS for Apps. Esto significa:
    - Todas las entidades del origen de datos externo deben tener una clave principal de GUID asociada.  
    - Todas las propiedades de entidad deben representarse como atributos de CDS for Apps. Puede usar tipos simples que representen texto, números, conjuntos de opciones, fechas, imágenes y búsquedas. 
    - Debe ser capaz de modelar las relaciones de entidad en CDS for Apps.
    - No se puede calcular ni consolidar un atributo de una entidad virtual.Los cálculos que desee deben realizarse en el lado externo, probablemente dentro del proveedor de datos o dirigidos por él.
- No se admite auditoría o seguimiento de los cambios.  Estos pueden implementarse en el almacén de datos externo.
- No se pueden habilitar entidades virtuales para colas.
- No se admite el almacenamiento en caché sin conexión de valores para las entidades virtuales.
- Una entidad virtual no puede representar una actividad y no admite flujos de proceso de negocio.
- Una vez creada, una entidad virtual no se puede cambiar para que sea una entidad estándar (no virtual).  Lo contrario también es cierto: una entidad estándar no se puede convertir en una entidad virtual.

<!-- TODO: Make bulleted list into table?  Make more complete by reviewing API modification tables. -->

Para obtener más información sobre cómo se reflejan estas limitaciones en la API de CDS for Apps, consulte [Consideraciones de la API de entidades virtuales](api-considerations-ve.md). 

### <a name="see-also"></a>Vea también

[Consideraciones sobre API para entidades virtuales](api-considerations-ve.md)<br />
[Proveedores de datos de entidad virtual personalizados](custom-ve-data-providers.md)<br />
[Ejemplo: Complemento de proveedor de datos de entidad virtual genérico](sample-generic-ve-plugin.md)