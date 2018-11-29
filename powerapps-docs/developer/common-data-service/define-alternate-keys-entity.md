---
title: Trabajar con claves alternativas (Common Data Service para aplicaciones) | Microsoft Docs
description: En este tema se explica cómo crear claves alternativas para una entidad. Las claves alternativas pueden crearse mediante programación o usando las herramientas de personalización
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="work-with-alternate-keys"></a>Trabajar con claves alternativas

Todos los registros de Common Data Service para aplicaciones tienen identificadores únicos definidos como GUID. Éstos son clave principal para cada entidad. Si necesita integrarse con un almacén de datos externos, es posible que pueda agregar una columna a las tablas de base de datos externas para incluir una referencia al identificador único de CDS for Apps. Esto permite tener una referencia local al vínculo con el registro de CDS for Apps. Sin embargo, a veces no puede modificar la base de datos externa. Con claves alternativas, ahora puede definir un atributo de una entidad CDS for Apps para que corresponda a un identificador único (o una combinación única de columnas) usado por el almacén de datos externos. Esta clave alternativa se puede usar para identificar de manera única un registro en CDS for Apps en lugar de la clave principal. Debe poder definir qué atributos representan una única identidad para sus registros. Una vez identifique los atributos que son únicos con la entidad, puede declararlos como claves alternativas con la interfaz de usuario de personalización (UI) o en el código. En este tema se proporciona información acerca de la definición de claves alternativas en el modelo de datos.  

<a name="BKMK_Declare"></a>

## <a name="create-alternate-keys"></a>Crear claves alternativas  

Puede crear claves alternativas mediante programación o usando las herramientas de personalizaciones. Para obtener más información sobre el uso de las herramientas de personalización, vea [Definir claves alternativas para hacer referencia a registros de CRM](https://technet.microsoft.com/library/29e53691-0b18-4fde-a1d0-7490aa227898.aspx).  

Para definir claves alternativas mediante programación, primero tiene que crear un tipo de objeto <xref:Microsoft.Xrm.Sdk.Metadata.EntityKeyMetadata> (o <xref href="Microsoft.Dynamics.CRM.EntityKeyMetadata?text=EntityKeyMetadata EntityType" /> si trabaja con la API web). Esta clase contiene los atributos clave. Una vez que se establecen los atributos clave, puede usar `CreateEntityKey` para crear las claves para una entidad. Este mensaje toma el nombre de la entidad y los valores de `EntityKeyMetadata` como entrada para crear la clave.  

Debe conocer las siguientes restricciones al crear claves alternativas:  

- **Atributos válidos en definiciones de clave**  

   Solo los atributos de los siguientes tipos se pueden incluir en definiciones de clave alternativa:  


  |      Tipo de atributo      |    Nombre     |
  |--------------------------|---------------------|
  | DecimalAttributeMetadata |   Número decimal    |
  | IntegerAttributeMetadata |    Número entero     |
  | StringAttributeMetadata  | Línea de texto única |


- **Tamaño de clave válido**  

   Cuando se crea una clave, el sistema valida que la plataforma puede admitir la clave, incluido que el tamaño total de la clave no infringe restricciones de índice basadas en SQL como 900 bytes por clave y 16 columnas por clave. Si el tamaño de la clave no cumple las restricciones, un mensaje de error se mostrará.  

- **Número máximo de definiciones de clave alternativa para una entidad**  

   Puede haber un máximo de 5 definiciones de clave alternativa para una entidad en una instancia de CDS for Apps.  

- **Caracteres Unicode en valor de clave**

  Si los datos en un campo que se usa en una clave alternativa contienen uno de los caracteres siguientes `<``>`,`*`,`%`,`&`,`:`,`\\`, las acciones de revisión o upsert no funcionarán.  Si solo necesita unicidad, este método funciona, pero si necesita usar estas claves como parte de la integración de datos, entonces es mejor crear la clave en los campos que no tendrán datos con dichos caracteres.

<a name="BKMK_crud"></a>   

## <a name="retrieve-and-delete-alternate-keys"></a>Recuperar y eliminar claves alternativas  

Si necesita recuperar o eliminar claves alternativas, puede usar la interfaz de usuario de personalización para ello, sin necesidad de escribir código. Sin embargo, el SDK proporciona los dos mensajes siguientes para recuperar y eliminar claves alternativas mediante programación.  

|Clase de solicitud de mensajes|Descripción|  
|---------------------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityKeyRequest>|Recupera la clave alternativa especificada.|  
|<xref:Microsoft.Xrm.Sdk.Messages.DeleteEntityKeyRequest>|Elimina la clave alternativa especificada.|  

Para recuperar todas las claves para una entidad, use la nueva propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Keys> de `EntityMetadata` (clase <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> o <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>). Obtiene una matriz de claves para una entidad.  

<a name="BKMK_index"></a>   

## <a name="monitor-index-creation-for-alternate-keys"></a>Supervisar la creación del índice para claves alternativas  

Las claves alternativas utilizan índices de base de datos para forzar exclusividad y para optimizar el rendimiento de búsqueda. Si hay muchos registros existentes en una tabla, la creación del índice puede ser un proceso largo. Puede aumentar la capacidad de respuesta de la interfaz de usuario de personalización y la importación de soluciones realizando la creación de índices como un proceso en segundo plano. La propiedad `EntityKeyMetadata.AsyncJob` (<xref href="Microsoft.Dynamics.CRM.EntityKeyMetadata?text=EntityKeyMetadata EntityType" /> o <xref:Microsoft.Xrm.Sdk.Metadata.EntityKeyMetadata>) hace referencia a los trabajos asincrónicos que realiza la creación de índice. La propiedad `EntityKeyMetadata.EntityKeyIndexStatus` especifica el estado de la clave mientras progresa su trabajo de creación de índice. El estado podría ser cualquiera de los siguientes:  

- Pendiente  
- En curso  
- Activo  
- Incorrecto  

Cuando se crea una clave alternativa con la API, si se produce un error en la creación del índice, puede analizar los detalles sobre la causa del error, corregir los problemas y reactivar la solicitud de clave con `ReactivateEntityKey` (mensaje <xref href="Microsoft.Dynamics.CRM.ReactivateEntityKey?text=ReactivateEntityKey Action" /> o <xref:Microsoft.Xrm.Sdk.Messages.ReactivateEntityKeyRequest>).  

Si se elimina la clave alternativa mientras un trabajo de creación de índice sigue pendiente o en progreso, el trabajo se cancela y se elimina el índice.  

### <a name="see-also"></a>Vea también  
 [Uso de claves alternativas](use-alternate-key-create-record.md)<br />
 [Uso del seguimiento de cambios para sincronizar los datos con sistemas externos](use-change-tracking-synchronize-data-external-systems.md)<br />
 [Use Upsert para insertar o actualizar un registro](use-upsert-insert-update-record.md) [Definir teclas alternativas para hacer referencia a los registros](../../maker/common-data-service/define-alternate-keys-reference-records.md)