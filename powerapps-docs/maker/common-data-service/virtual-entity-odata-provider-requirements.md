---
title: Uso del proveedor de datos de OData v4 en entidades virtuales con Common Data Service for Apps | Microsoft Docs
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
ms.assetid: ''
caps.latest.revision: ''
author: Mattp123
ms.author: matp
manager: brycho
ms.openlocfilehash: 0bd2aed852b5d7eb9b354f30978725b1386a89aa
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39710218"
---
# <a name="odata-v4-data-provider-configuration-requirements-and-best-practices"></a>Configuración, requisitos y procedimientos recomendados del proveedor de datos de OData v4

En este tema se describe cómo configurar el proveedor de datos de OData v4, así como los requisitos y procedimientos recomendados para usar el proveedor de datos de OData v4 con el fin de conectarse con un servicio de web de OData v4. 

## <a name="odata-v4-data-provider-best-practices"></a>Procedimientos recomendados del proveedor de datos de OData v4

- Common Data Service (CDS) for Apps requiere que todas las entidades tengan un atributo de identificador; este identificador se conoce como "identificador único" y el valor debe ser un GUID.  Solo puede asignar campos de identificador a campos externos con el tipo de datos `Edm.Guid`.  No puede asignar un tipo de datos `Edm.Int32` a un campo de tipo de datos de identificador único en CDS for Apps.
-  Las entidades de OData con propiedades que aceptan valores NULL deben establecerse para que coincidan con el campo asignado en la entidad virtual. Por ejemplo, una propiedad de entidad de OData con el valor false en Acepta valores NULL debe tener el campo asignado en el atributo **Requisito de campo** de CDS for Apps establecido en **Requerido por la empresa**. 
- Para recuperar varias consultas, por ejemplo, cuando cargue datos en una cuadrícula, controle el tamaño del conjunto de datos devuelto por el origen de datos externo usando los parámetros de consulta de selección y filtro.
- Si aún no está habilitado, los administradores del sistema deben habilitar el seguimiento de complementos. Cuando lo esté, se capturan todos los errores del punto de conexión de OData en el registro de seguimiento de complementos. Más información: [Guía del administrador: Cuadro de diálogo Configuración del sistema: pestaña Personalización](/dynamics365/customer-engagement/admin/system-settings-dialog-box-customization-tab) 

## <a name="data-type-mapping"></a>Asignación de tipos de datos

En la tabla siguiente se enumera las asignaciones de tipos de datos de Entity Data Model (EDM) de OData con los tipos de datos de CDS for Apps. 

|Tipo de datos de OData|Tipos de datos de CDS for Apps  |
|---------|---------|
|`Edm.Boolean`|Dos opciones|
|`Edm.DateTime`|Fecha y hora|
|`Edm.DateTimeOffset`|Fecha y hora|
|`Edm.Decimal`|Número decimal o moneda|
|`Edm.Double`|Número de punto flotante|
|`Edm.Guid`|Identificador único|
|`Edm.Int32`|Número entero|
|`Edm.Int64`|Número entero|
|`Edm.String`|Línea de texto única o varias líneas de texto|


### <a name="odata-edm-data-types-that-are-not-supported-for-mapping-with-virtual-entities"></a>Tipos de datos de EDM de OData que no se admiten para la asignación con entidades virtuales 

- `Edm.Binary `
- `Edm.Time` 
- `Edm.Float `
- `Edm.Single` 
- `Edm.Int16` 
- `Edm.Byte` 
- `Edm.SByte`

 
## <a name="add-a-data-source-using-the-odata-v4-data-provider"></a>Adición de un origen de datos mediante el proveedor de datos de OData v4

En este procedimiento se muestra cómo usar el proveedor de datos de OData incluido como origen de datos de entidades virtuales.   
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Administración** > **Orígenes de datos de entidades virtuales**.  
1. En la barra de herramientas de acciones, haga clic en **Nuevo**.  
1. En el cuadro de diálogo **Seleccionar proveedor de datos**, elija los siguientes orígenes de datos y, a continuación, haga clic en **Aceptar**.  
  
    - **Proveedor de datos de OData v4**. CDS for Apps incluye un proveedor de datos de Odata v4 que puede utilizarse para conectarse a orígenes de datos que admiten el estándar abierto de OData v4.  
    - *Proveedor de datos personalizado*. Si ha importado un complemento de proveedor de datos, el proveedor de datos aparecerá aquí. Más información: [Documentación para desarrolladores: Introducción a las entidades virtuales](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)  
    
1. En la página de propiedades **Nuevo origen de datos**, complete los siguientes campos y, a continuación, guarde el registro.  
  
    - **Nombre**. Escriba un nombre que describa el origen de datos.  
    - **URI**. Si usa el proveedor de datos OData, escriba el URI del servicio web de OData. Por ejemplo, si utiliza el proveedor de OData para conectarse a un servicio web hospedado en Azure, el URI puede ser similar a *`http://contosodataservice.azurewebsites.net/odata/`*.  
    - **Tiempo de espera en segundos**. Escriba el número de segundos que se esperará una respuesta del servicio web antes de que se agote el tiempo de espera de solicitud de datos. Por ejemplo, escriba 30 para esperar un máximo de treinta segundos antes de que se agote el tiempo de espera.  
    - **Modo de paginación**. Elija si desea usar la paginación del lado cliente o servidor para controlar cómo se paginan los resultados de la consulta. El valor predeterminado es la paginación del lado cliente. Con la paginación del lado servidor, el servidor controla cómo se paginan los resultados mediante el parámetro $skiptoken, que se agrega a la cadena de consulta. Más información: [Opción de consulta del sistema de token de omisión ($skiptoken)](https://msdn.microsoft.com/library/dd942121.aspx)  
        -  **Return inline count** (Devolver recuento alineado). Devuelve el número total de registros del conjunto de resultados. Esta configuración se utiliza para habilitar la funcionalidad de siguiente página cuando se devuelven datos a una cuadrícula. Use un valor false si el punto de conexión de OData no es compatible con el parámetro de OData $inclinecount. El valor predeterminado es false.
    - **Parámetros de solicitud**. Si lo desea, puede agregar parámetros personalizados de cadena de consulta o encabezado usados para conectarse al servicio web de OData, como los parámetros de autenticación al servicio externo. Haga clic en **Cadena de consulta** para alternar entre valor y parámetro de cadena de consulta y encabezado. Se pueden agregar hasta 10 cadenas de consulta o encabezado. 
        ![Registro de origen de datos de entidades virtuales](media/virtual-entity-data-source.png) 


## <a name="see-also"></a>Vea también  

[Crear y editar entidades virtuales que contienen datos de un origen de datos externos](create-edit-virtual-entities.md) <br/>
[Blog de TechNet: Interact with data from external systems using the new virtual entities (Interacción con datos de sistemas externos usando las nuevas entidades virtuales)](https://blogs.technet.microsoft.com/lystavlen/2017/09/08/virtual-entities/)
