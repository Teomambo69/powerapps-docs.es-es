---
title: Usar el proveedor de datos de OData v4 de la entidad virtual con Common Data Service for Apps | MicrosoftDocs
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: null
caps.latest.revision: null
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="odata-v4-data-provider-configuration-requirements-and-best-practices"></a>Configuración, requisitos y prácticas recomendadas del proveedor de datos de OData v4

En este tema se describe cómo configurar el proveedor de datos de OData v4 así como los requisitos y las prácticas recomendadas para usar el proveedor de datos de OData v4 para establecer la conexión con un servicio web de OData v4. 

## <a name="odata-v4-data-provider-best-practices"></a>Prácticas recomendadas del proveedor de datos de OData v4

- Common Data Service for Apps requiere que todas las entidades tengan un atributo de id., este identificador es único y el valor debe ser un GUID.  Solo puede asignar los campos de id. a campos externos con el tipo de datos `Edm.Guid`.  No puede asignar un tipo de datos `Edm.Int32` a un campo de tipo de datos de identificador único en CDS for Apps.
-  Las entidades de OData que tengan propiedades con valores nulos se deben configurar para que coincidan con el campo asignado en la entidad virtual. Por ejemplo, una propiedad de la entidad de OData con un valor nulo =False debe tener el campo asignado en el conjunto de atributos de **Requisitos de campo** de CDS for Apps como **Requerido por la empresa**. 
- Para recuperar consultas múltiples como aquellas resultantes de cargar datos en una cuadrícula, debe controlar el tamaño del conjunto de datos devuelto desde el origen de datos externo; para ello, use los parámetros para seleccionar y filtrar la consulta.
- Si no está habilitado, los administradores del sistema deben habilitar la opción de seguimiento de complementos. Una habilitada, todos los errores del extremo de OData se capturan en el registro de seguimiento de complementos. Más información: [Guía del administrador: Cuadro de diálogo Configuración del sistema - Pestaña Personalización](/dynamics365/customer-engagement/admin/system-settings-dialog-box-customization-tab) 

## <a name="data-type-mapping"></a>Asignaciones de tipos de datos

En la siguiente tabla se enumeran las asignaciones de tipo de datos de OData Entity Data Model (EDM) con los tipos de datos de CDS for Apps. 

|Tipos de datos de OData|Tipos de datos de CDS for Apps  |
|---------|---------|
|`Edm.Boolean`|Dos opciones|
|`Edm.DateTime`|Fecha y hora|
|`Edm.DateTimeOffset`|Fecha y hora|
|`Edm.Decimal`|Número decimal o divisa|
|`Edm.Double`|Número de punto flotante|
|`Edm.Guid`|Identificador único|
|`Edm.Int32`|Número entero|
|`Edm.Int64`|Número entero|
|`Edm.String`|Línea de texto individual o varias líneas de texto|


### <a name="odata-edm-data-types-that-are-not-supported-for-mapping-with-virtual-entities"></a>Tipos de datos de OData EDM que no se admiten para asignarlos con entidades virtuales 

- `Edm.Binary `
- `Edm.Time` 
- `Edm.Float `
- `Edm.Single` 
- `Edm.Int16` 
- `Edm.Byte` 
- `Edm.SByte`

 
## <a name="add-a-data-source-using-the-odata-v4-data-provider"></a>Agregar un origen de datos con el proveedor de datos de OData v4

Este procedimiento muestra cómo usar el proveedor de datos de OData integrado como origen de datos de entidad virtual.   
  
1. Acceda a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Administración** > **Orígenes de datos de entidad virtual**.  
1. En la barra de herramientas Acciones, haga clic en **Nuevo**.  
1. En el cuadro de diálogo **Seleccionar proveedor de datos**, seleccione uno de los siguientes orígenes de datos y, a continuación, haga clic en **Aceptar**.  
  
    - **Proveedor de datos OData v4**. CDS for Apps incluye un proveedor de datos de Odata v4 que se puede usar para conectarse a los orígenes de datos que admiten el estándar abierto de OData v4.  
    - *Personalice el proveedor de datos*. Si ha importado un complemento del proveedor de datos, el proveedor de datos aparecerá aquí. Más información: [Documentación para desarrolladores: Introducción a las entidades virtuales](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)  
    
1. En la página de propiedades **Nuevo origen de datos**, rellene los siguientes campos y, a continuación, guarde el registro.  
  
    - **Nombre**. Escriba un nombre para describir el origen de datos.  
    - **Uri**. Si usa el proveedor de datos de OData, especifique el URI del servicio web de OData. Por ejemplo, si está usando el proveedor de OData para conectarse a un servicio web hospedado en Azure, el URI puede parecerse a *`http://contosodataservice.azurewebsites.net/odata/`*.  
    - **Tiempo de espera en segundos**. Escriba la cantidad de segundos que se debe esperar a una respuesta del servicio web antes de agotar el tiempo de espera de una solicitud de datos. Por ejemplo, escriba 30 para esperar un máximo de treinta segundos antes de que se agote el tiempo de espera.  
    - **Modo de paginación**. Seleccione si usará la paginación del lado del cliente o del servidor para controlar cómo se paginan los resultados de la consulta. El valor predeterminado es la paginación del lado del cliente. Con la paginación del lado de servidor, el servidor controla la manera de paginar los resultados mediante el parámetro $skiptoken, que se agrega a la cadena de consulta. Más información: [Opción para omitir la consulta del sistema de token ($skiptoken)](https://msdn.microsoft.com/library/dd942121.aspx)  
        -  **Devolver recuento alineado** Devuelve el número total de registros en el conjunto de resultados. Esta configuración se usa para habilitar la funcionalidad de la siguiente página cuando se devuelven los datos a una cuadrícula. Use un valor "false" si el extremo de OData no admite el parámetro de OData $inclinecount. El valor predeterminado es false.
    - **Parámetros de solicitud**. Como alternativa, puede agregar parámetros de cadena de consulta o de encabezado personalizado que se usan para conectar con el servicio web de OData, como parámetros de autenticación para el servicio externo. Haga clic en **Cadena de consulta** para alternar entre el parámetro de cadena de consulta y el encabezado y el valor. Se pueden agregar hasta 10 cadenas de consulta o encabezado. 
        > [!div class="mx-imgBorder"] 
        > ![Registro de origen de datos de entidad virtual](media/virtual-entity-data-source.png) 


## <a name="see-also"></a>Vea también  

[Crear y editar entidades virtuales que contienen datos desde un origen de datos externo](create-edit-virtual-entities.md) <br/>
[Blog de TechNet: interacción con datos de sistemas externos mediante nuevas entidades virtuales](https://blogs.technet.microsoft.com/lystavlen/2017/09/08/virtual-entities/)
