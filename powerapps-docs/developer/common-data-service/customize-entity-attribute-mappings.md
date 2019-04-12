---
title: Personalizar asignaciones de entidades y atributos en PowerApps (Common Data Service) | Microsoft Docs
description: Obtenga información sobre cómo asignar atributos entre entidades que tienen una relación de entidad en PowerApps. Esto le permite establecer valores predeterminados para un registro creado en el contexto de otro registro.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="customize-entity-and-attribute-mappings"></a>Personalizar asignaciones de entidad y atributo

Puede asignar atributos entre entidades que tienen una relación de entidad. Esto le permite establecer valores predeterminados para un registro creado en el contexto de otro registro. Use las herramientas de personalización de la aplicación para asignar atributos; consulte [Asignar campos de entidad](../../maker/common-data-service/map-entity-fields.md).

<a name="bkmk_BehaviorintheApplication"></a>

## <a name="behavior-in-the-application"></a>Comportamiento en la aplicación

 La asignación en Common Data Service simplifica la entrada de datos cuando se crean nuevos registros que están asociados con otro registro. Cuando una entidad tiene una relación entre entidades con otra entidad, puede crear nuevos registros de entidades relacionadas con la ficha **Crear relacionados** en la cinta de opciones. Al crear un nuevo registro de esta forma, los datos asignados del registro de la entidad primaria se copian al formulario para el nuevo registro de la entidad relacionada. Al asignar atributos de entidad, se controlan los datos que se copian agregando nuevas asignaciones en la relación entre las dos entidades. Si crea un registro sin usar la vista asociada de la entidad primaria, los datos no se asignarán.  

 Por ejemplo, es posible que desee configurar una asignación entre los campos de dirección en cuentas y los campos de dirección en contactos. Con esta asignación, cuando un usuario agrega un contacto asociado a una cuenta específica, los campos de dirección del contacto se rellenan automáticamente.  

 Puede asignar un atributo a varios atributos de destino. Por ejemplo, puede asignar la información de dirección de una cuenta a las direcciones de facturación y envío de un pedido.  

 La asignación se aplica antes de que se cree un nuevo registro relacionado. Los usuarios pueden hacer cambios antes de guardar el registro. Los cambios posteriores que se realicen en el registro principal no se aplicarán al registro relacionado.  

<a name="bkmk_UsingEntityandAttributeMappingData"></a>

## <a name="using-entity-and-attribute-mapping-data"></a>Uso de datos de asignación de entidades y atributos

### <a name="using-web-api"></a>Uso de la API web

Al trabajar con la API web, puede utilizar <xref href="Microsoft.Dynamics.CRM.InitializeFrom?text=InitializeFrom Function" /> para crear registros nuevos en el contexto de registros existentes donde existe una asignación entre las entidades. 

La respuesta recibida de la solicitud InitializeFrom consta de valores de atributos asignados entre la entidad de origen y la entidad de destino y el GUID del registro primario. La asignación de atributos entre las entidades que tienen una relación de entidad es diferente para conjuntos de entidades diferentes y se puede personalizar, por lo que la respuesta de la solicitud de la función InitializeFrom puede variar para organizaciones y entidades diferentes. Cuando se pasa esta respuesta en el cuerpo de la solicitud de creación del nuevo registro, estos valores de atributo se replican en el nuevo registro. Los valores de los atributos asignados personalizados también se definen en el nuevo registro durante el proceso.

> [!NOTE] 
> Para determinar si se pueden asignar dos entidades, utilice la siguiente solicitud de la API web:<br/>`GET [Organization URI]/api/data/v9.0/entitymaps?$select=sourceentityname,targetentityname&$orderby=sourceentityname`

Para obtener más información, consulte [Crear una nueva entidad a partir de otra entidad](webapi/create-entity-web-api.md#create-a-new-entity-from-another-entity).

### <a name="using-organization-service"></a>Uso del servicio de organización

 Al crear registros nuevos en el contexto de un registro existente donde existe una asignación entre entidades, puede usar el mensaje de <xref:Microsoft.Crm.Sdk.Messages.InitializeFromRequest> para definir un nuevo registro que contiene los valores especificados en la asignación. A continuación, ya podrá usar el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> para guardar el registro. De esta manera, se aplican todas las asignaciones definidas.  

 Se crean los mapas válidos de entidad cuando se crea una relación de entidad. Use la relación de entidades de `entity_map_attribute_maps` para recuperar las asignaciones de atributos para el par de entidades especificadas por el mapa de entidad.  
 Puede crear o actualizar registros de asignación de atributos. Los siguientes requisitos deben cumplirse para los mapas de atributo:  
- El tipo de <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> debe coincidir.
- La longitud del campo de destino no puede ser más corta que el campo de origen.
- El formato debe coincidir.
- El campo de destino no se debe usar en otra asignación.
- El campo de origen debe estar visible en el formulario de entidad.
- El campo de destino debe ser un campo en el que un usuario pueda especificar datos.
- Los valores de identificador de dirección no se pueden asignar.
- Los atributos PartyList, donde <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.AttributeType> es <xref:Microsoft.Xrm.Sdk.Metadata.AttributeTypeCode>.PartyList, no pueden asignarse.

<a name="bkmk_Automapping"></a>

## <a name="auto-mapping-attributes-between-entities"></a>Atributos de asignación automática entre entidades

 Puede editar asignaciones de atributos entre entidades para relaciones de entidades que admitan la asignación. 

 Además de crear cada asignación de atributo manualmente, puede usar el mensaje `AutoMapEntity` (clase <xref href="Microsoft.Dynamics.CRM.AutoMapEntity?text=AutoMapEntity Action" /> o <xref:Microsoft.Crm.Sdk.Messages.AutoMapEntityRequest>) para generar un nuevo conjunto de asignaciones de atributos. Este mensaje realiza la acción encontrada en la opción del menú **Generar asignaciones** en el menú **Más acciones** de la barra de herramientas (consulte [Generar asignaciones de campos automáticamente](../../maker/common-data-service/map-entity-fields.md#automatically-generate-field-mappings)). Este mensaje asigna todos los atributos entre las dos entidades relacionadas donde los nombres de atributo y los tipos son idénticos. Este mensaje se proporciona como aumento de la productividad de modo que no es necesario agregar manualmente todas las asignaciones de atributos. En su lugar, puede generar un conjunto de asignaciones potenciales y reducir la cantidad de trabajo manual para agregar o quitar asignaciones individuales para adaptarse a sus requisitos. 

> [!NOTE]
> Generar asignaciones automáticamente de esta manera quitará cualquier asignación de atributo definido anteriormente y puede incluir las asignaciones que no desee.  

<a name="BKMK_mapping"></a>

## <a name="retrieve-the-entity-and-attribute-mappings"></a>Recuperar asignaciones de entidad y atributo

 Una forma sencilla de ver las asignaciones que se han realizado es usar la siguiente consulta de FetchXML. Para obtener más información sobre cómo ejecutar esta consulta, vea [Usar FetchXML para consultar datos](use-fetchxml-construct-query.md).

```xml

<fetch version='1.0' mapping='logical' distinct='false'>
   <entity name='entitymap'>
      <attribute name='sourceentityname'/>
      <attribute name='targetentityname'/>
      <link-entity name='attributemap' alias='attributemap' to='entitymapid' from='entitymapid' link-type='inner'>
         <attribute name='sourceattributename'/>
         <attribute name='targetattributename'/>
      </link-entity>
   </entity>
 </fetch>
```

### <a name="see-also"></a>Vea también

 [Asignar campos de entidad](../../maker/common-data-service/map-entity-fields.md)