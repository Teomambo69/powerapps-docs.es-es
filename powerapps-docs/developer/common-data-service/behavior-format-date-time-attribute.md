---
title: Comportamiento y formato del atributo Fecha y hora (Common Data Service) | MicrosoftDocs
description: La clase DateTimeAttributeMetadata se usa para definir y administrar los atributos de tipo DateTime en Dynamics 365 Customer Engagement.
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
# <a name="behavior-and-format-of-the-date-and-time-attribute"></a>Comportamiento y formato del atributo de fecha y hora

Si tiene usuarios y oficinas en todo el mundo, es importante representar correctamente valores de fecha y hora en varias zonas horarias. Los `DateTimeAttributeMetadata` (clase <xref href="Microsoft.Dynamics.CRM.DateTimeAttributeMetadata?text=DateTimeAttributeMetadata EntityType" /> o <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata>) se usan para definir y administrar atributos de tipo `DateTime` en Common Data Service. Use la propiedad `DateTimeBehavior` (para el servicio de la organización, consulte <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata.DateTimeBehavior>) para definir si almacenar valores de fecha y hora con o sin información de zona horaria, y use la propiedad `DateTimeAttributeMetadata.Format` para especificar el formato de visualización de estos atributos.  

  
 También puede usar el área personalización en Common Data Service para definir el comportamiento y el formato de los atributos de fecha y hora. Más información: [Comportamiento y formato del campo de fecha y hora](/dynamics365/customer-engagement/customize/behavior-format-date-time-field).  
  
> [!NOTE]
>  Todos los atributos de fecha y hora en Common Data Service admiten valores que se pueden remontar hasta el 1/1/1753 a las 12:00.  
  
<a name="SpecifyBehavior"></a>   

## <a name="specify-the-behavior-of-a-date-and-time-attribute"></a>Especifique el comportamiento de un atributo de fecha y hora

 Puede usar `DateTimeBehavior` (clase <xref href="Microsoft.Dynamics.CRM.DateTimeBehavior?text=DateTimeBehavior ComplexType" /> o <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeBehavior>) para especificar un valor para la propiedad <xref href="Microsoft.Dynamics.CRM.DateTimeAttributeMetadata?text=DateTimeAttributeMetadata EntityType" />.DateTimeBehaviour. El `DateTimeBehavior` contiene los siguientes miembros, cada uno de los cuales devuelve una cadena con el mismo valor que el nombre del miembro:  
  
|Nombre y valor del miembro|Descripción|  
|---------------------------|-----------------|  
|`UserLocal`|-   Almacena el valor de fecha y hora como valor UTC en el sistema.<br />-   La operación de recuperación devuelve el valor UTC.<br />-   La operación de actualización convierte el valor UTC en el valor de zona horaria del usuario actual y, a continuación almacena el valor actualizado tal cual o como el valor UTC equivalente en función del tipo ([DateTimeKind](https://msdn.microsoft.com/library/shx7s921.aspx)) del valor especificado para la actualización. Si el valor especificado es de tipo UTC, se almacena tal cual. En caso contrario, se almacena el valor equivalente de UTC.<br />-   La recuperación del valor con formato convierte de UTC a la zona horaria actual del usuario en función de la zona horaria y la configuración regional del usuario.<br />-   Para la API web, el atributo se expone como DateTimeOffset.<br />-   Este comportamiento se usa para atributos del sistema como `CreatedOn` y `ModifiedOn`, y no se puede cambiar. Debe usar este comportamiento para atributos personalizados donde desee almacenar valores de fecha y hora con la información de la zona horaria.|  
|`DateOnly`|-   Almacena el valor de fecha real con el valor de hora como 12:00 AM (00:00:00) en el sistema.<br />-   Para operaciones de recuperación y actualización, no se realiza conversión de zona horaria, y el valor de hora siempre es 12 AM (00:00:00).<br />-   La recuperación del valor con formato muestra el valor de fecha sin ninguna conversión de zona horaria.<br />-   Para la API web, el atributo se expone como DateTimeOffset.<br />-   Este comportamiento se debe usar para atributos personalizados que almacenan cumpleaños y aniversarios, donde la información de hora no es obligatoria.|  
|`TimeZoneIndependent`|-   Almacena los valores reales de fecha y hora en el sistema independientemente de la zona horaria del usuario.<br />-   Para operaciones de recuperación y de actualización, no se realiza conversión de zona horaria, y los valores reales de fecha y hora se devuelven y actualizan respectivamente en el sistema independientemente de la zona horaria del usuario.<br />-   La recuperación del valor con formato muestra el valor de fecha y hora (sin ninguna conversión de zona horaria) basándose en el formato especificado por la configuración regional y de zona horaria del usuario actual.<br />-   Para la API web, el atributo se expone como DateTimeOffset.<br />-   Este comportamiento se debe usar para atributos que almacenan información como hora de registro y salida en hoteles.|  
  
 El siguiente código de ejemplo demuestra cómo establecer un comportamiento de `UserLocal` para un nuevo atributo de fecha y hora:  
  
 ```csharp
// Create a date time attribute for the Account entity
// with the UserLocal behavior
dtAttribute = new DateTimeAttributeMetadata
{                             
    SchemaName = "new_SampleDateTimeAttribute",
    DisplayName = new Label("Sample Date Time Attribute", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),                
    Description = new Label("Created by SDK Sample", _languageCode),                
    DateTimeBehavior = DateTimeBehavior.UserLocal,
    Format = DateTimeFormat.DateAndTime,
    ImeMode = ImeMode.Disabled
};

CreateAttributeRequest createAttributeRequest = new CreateAttributeRequest
{
    EntityName = Account.EntityLogicalName,
    Attribute = dtAttribute
};
_serviceProxy.Execute(createAttributeRequest);
Console.WriteLine("Created attribute '{0}' with UserLocal behavior\nfor the Account entity.\n", 
                            dtAttribute.SchemaName);
```
  
 En el código de ejemplo, también puede establecer el valor de la propiedad `DateTimeBehavior` especificando directamente el valor de cadena: `DateTimeBehavior = "UserLocal"`  
  
 Si no especifica el comportamiento cuando crea un atributo de fecha y hora, el atributo se crea con el comportamiento `UserLocal` de forma predeterminada. Para ver un código de ejemplo completo, consulte [Ejemplo: Convertir valores de fecha y hora](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior).  
  
> [!IMPORTANT]
>  -   Una vez que cree un atributo de fecha y hora con el comportamiento establecido como `DateOnly` o `TimeZoneIndependent`, no puede cambiar el comportamiento del atributo. Más información: [Cambiar el comportamiento de un atributo de fecha y hora](behavior-format-date-time-attribute.md#ChangeBehavior)  
> -   Los atributos de fecha y hora con el comportamiento `DateOnly` o `TimeZoneIndependent` se tratarán como si tuvieran el comportamiento `UserLocal` cuando se editen en una versión anterior del cliente de Dynamics 365 for Outlook en modo sin conexión. Esto se debe a que el cliente no comprende todos los nuevos comportamientos y no los tratará de forma distinta de `UserLocal`. Ningún atributo de fecha y hora se convierte a los nuevos comportamientos en la actualización, por lo que la recomendación aquí sería actualizar todos los clientes de Common Data Service a la última versión antes de que un personalizador adopte uno de los comportamientos nuevos. Cuando está en línea, la modificación de los datos de los campos con los nuevos comportamientos funcionará bien.  
  
<a name="SpecifyFormat"></a>   

## <a name="specify-format-of-the-date-and-time-attribute"></a>Especificar el formato del atributo de fecha y hora  

 Use la propiedad `Format` para especificar el formato de visualización de la fecha y hora del atributo con independencia de cómo se almacena en el sistema. Puede usar la enumeración de `DateTimeFormat` (enumeración <xref href="Microsoft.Dynamics.CRM.DateTimeFormat?text=DateTimeFormat EnumType" /> o <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeFormat>) para especificar el formato de visualización: `DateAndTime` o `DateOnly`.  
  
 Si la propiedad `DateTimeAttributeMetadata.DateTimeBehavior` se establece en `DateOnly`, no puede establecer o cambiar el valor de la propiedad `DateTimeAttributeMetadata.Format` a `DateAndTime`.  
  
<a name="UnsupportedQueryOperators"></a>   

## <a name="date-and-time-query-operators-not-supported-for-dateonly-behavior"></a>Operadores de consulta de fecha y hora no admitidos en el comportamiento Solo fecha  

 No se admite operadores de consulta relacionados con el tiempo para el comportamiento `DateOnly`. Aparte de los operadores de consulta específicos de tiempo que se muestran aquí, se admiten todos los demás operadores de consulta.  
  
-   Más antiguo de X minutos  
  
-   Más antiguo de X horas  
  
-   Últimas X horas  
  
-   Próximas X horas  
  
 Más información: [Operadores de consulta de fecha y hora en FetchXML](/dynamics365/customer-engagement/developer/org-service/fiscal-date-older-datetime-query-operators-fetchxml)  
  
<a name="ChangeBehavior"></a>
   
## <a name="change-the-behavior-of-a-date-and-time-attribute"></a>Cambiar el comportamiento de un atributo de fecha y hora  

 Puede actualizar un atributo de fecha y hora para cambiar su comportamiento si tiene el rol Personalizador del sistema en su instancia de Common Data Service y la propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` para el atributo de fecha y hora se establece en `True`.  
  
> [!CAUTION]
>  Antes de modificar el comportamiento de un atributo de fecha y hora, debe comprobar todas las dependencias del atributo, como reglas de negocio, flujos de trabajo, atributos calculados o consolidados, para asegurarse de que no hay problemas como resultado de modificar el comportamiento. Los personalizadores del sistema pueden limitar la modificación del comportamiento de los atributos existentes de fecha y hora usando la propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior`.  
>   
>  Como mínimo, después de modificar el comportamiento de un atributo de fecha y hora, debe abrir cada regla de negocio, flujo de trabajo, atributo calculado y atributo consolidado dependiente del atributo de fecha y hora cambiado, revisar la información y guardar el registro, para asegurarse de que se usarán el atributo y el valor más recientes del campo de fecha y hora.  
>   
>  Después de modificar el comportamiento de los datos y el tiempo de un atributo calculado o consolidado, abra el editor de definición de campos calculados o consolidados y guarde la definición del campo para asegurarse de que el atributo sigue siendo válido después del cambio de comportamiento. Los personalizadores del sistema pueden abrir el editor de definición del atributo calculado o consolidado haciendo clic en **Editar** junto a **Tipo de campo** en el área personalización en Common Data Service. Más información: [Definir los campos calculados](/dynamics365/customer-engagement/customize/define-calculated-fields) y [Definir campos consolidados](/dynamics365/customer-engagement/developer/customize/define-rollup-fields)  
  
-   El comportamiento de los atributos `CreatedOn` y `ModifiedOn` para las entidades predefinidas y personalizadas se establece en `UserLocal` de forma predeterminada, y la propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` se establece en `False`, lo que implica que no puede modificar el comportamiento de estos atributos. Aunque los usuarios pueden cambiar el valor de propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` de estos atributos para entidades personalizadas, aún no pueden modificar el comportamiento de los atributos.  
  
-   Para nuevos atributos de fecha y hora personalizados, la propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` se establece en `True`. Esto implica que puede cambiar el comportamiento de un atributo personalizado de fecha y hora de `UserLocal` a `DateOnly` o `TimeZoneIndependent`; no se permite ninguna otra transición de comportamiento.  
  
     Para los atributos de fecha y hora que forman parte de una organización de Common Data Service, la propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` se establece en `True` a menos que el atributo o la entidad principal no se puede personalizar.  
  
    > [!NOTE]
    >  Cuando se actualiza la propiedad `DateTimeAttributeMetadata.DateTimeBehavior` de un atributo de `UserLocal` a `DateOnly`, asegúrese de cambiar también la propiedad `DateTimeAttributeMetadata.Format` de `DateAndTime` a `DateOnly`. De lo contrario, aparecerá una excepción.  
  
-   Los siguientes atributos de fecha y hora predefinidos de Common Data Service se establecen de forma predeterminado en `DateOnly` y la propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` se establece en `False` de estos atributos, lo que implica que no puede modificar el comportamiento de estos atributos:  
  
    |Atributo de fecha y hora|Entidad primaria|  
    |-----------------------------|-------------------|  
    |aniversario|Contacto|  
    |fecha de nacimiento|Contacto|  
    |duedate|Factura|  
    |estimatedclosedate|Cliente potencial|  
    |actualclosedate|Oportunidad|  
    |estimatedclosedate|Oportunidad|  
    |finaldecisiondate|Oportunidad|  
    |validfromdate|Producto|  
    |validtodate|Producto|  
    |closedon|Oferta|  
    |expireson|Oferta|  
  
     El comportamiento de estos atributos se establece en `UserLocal` y la propiedad administrada `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` a `True`, y solo podrá cambiar el comportamiento de estos atributos `DateOnly`. No se permite ninguna otra transición de comportamiento.  
  
 Después de actualizar el comportamiento de un atributo, debe publicar las personalizaciones para que el cambio surta efecto. Actualizar el comportamiento de un atributo de fecha y hora garantiza que todos los valores especificados o actualizados *después* de cambiar el comportamiento del atributo, se almacenan en el sistema de acuerdo con el nuevo comportamiento. Esto no afecta a los valores que ya están almacenados en la base de datos, y siguen estando almacenados como valores UTC. No obstante, cuando se recuperan los valores existentes mediante el SDK o se ven en la interfaz de usuario, los valores existentes se muestran de acuerdo con el nuevo comportamiento del atributo. Por ejemplo, si cambió el comportamiento de un atributo personalizado en una entidad de cuenta de `UserLocal` a `DateOnly` y recupera un registro de cuenta existente mediante el SDK, la fecha y la hora se mostrarán como \<Date> seguida de la hora como 12 AM (00:00:00). De forma similar, para el cambio de comportamiento de `UserLocal` a `TimeZoneIndependent`, el valor real en la base de datos se mostrará como está sin conversiones de zona horaria.  
  
 El siguiente código de ejemplo demuestra cómo actualizar el comportamiento de un atributo de fecha y hora:  
  
```csharp
// Retrieve the attribute to update its behavior and format
RetrieveAttributeRequest attributeRequest = new RetrieveAttributeRequest
{
    EntityLogicalName = Account.EntityLogicalName,
    LogicalName = "new_sampledatetimeattribute",
    RetrieveAsIfPublished = false
};
// Execute the request
RetrieveAttributeResponse attributeResponse =
                (RetrieveAttributeResponse)_serviceProxy.Execute(attributeRequest);

Console.WriteLine("Retrieved the attribute '{0}'.",
                attributeResponse.AttributeMetadata.SchemaName);

// Modify the values of the retrieved attribute
DateTimeAttributeMetadata retrievedAttributeMetadata =
                (DateTimeAttributeMetadata)attributeResponse.AttributeMetadata;
retrievedAttributeMetadata.DateTimeBehavior = DateTimeBehavior.DateOnly;
retrievedAttributeMetadata.Format = DateTimeFormat.DateOnly;

// Update the attribute with the modified value
UpdateAttributeRequest updateRequest = new UpdateAttributeRequest
{
    Attribute = retrievedAttributeMetadata,
    EntityName = Account.EntityLogicalName,
    MergeLabels = false
};
_serviceProxy.Execute(updateRequest);
Console.WriteLine("Updated the behavior and format of '{0}' to DateOnly.",
    retrievedAttributeMetadata.SchemaName);

// Publish customizations to the account entity
PublishXmlRequest pxReq = new PublishXmlRequest
{
    ParameterXml = String.Format("<importexportxml><entities><entity>account</entity></entities></importexportxml>")
};
_serviceProxy.Execute(pxReq);
Console.WriteLine("Published customizations to the Account entity.\n");
 
``` 
  
 Para ver un código de ejemplo completo, consulte [Ejemplo: Convertir valores de fecha y hora](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior).  
  
<a name="Convert"></a>   
## <a name="convert-behavior-of-existing-date-and-time-values-in-the-database"></a>Convertir el comportamiento de valores existentes de fecha y hora en la base de datos 

 Cuando se actualiza un atributo de fecha y hora para cambiar su comportamiento de `UserLocal` a `DateOnly` o `TimeZoneIndependent`, no convierte automáticamente los valores del atributo existente en la base de datos. El cambio de comportamiento sólo afecta a los valores que se introducirán o actualizarán en el atributo *después* de que haya cambiado el comportamiento. Los valores de fecha y hora existentes del sistema continúan estando en UTC y Common Data Service los muestra de acuerdo con el nuevo comportamiento cuando se recuperan mediante el SDK o en la interfaz de usuario como se explica en la sección anterior. Para los atributos cuyo comportamiento ha cambiado de `UserLocal` a `DateOnly`, puede convertir los valores UTC existentes en la base de datos al valor `DateOnly` adecuado para evitar cualquier anomalía de datos mediante el mensaje `ConvertDateAndTimeBehavior`.  
  
 El mensaje le permite especificar una regla de conversión (Si trabaja con el servicio de organización, consulte <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest.ConversionRule>) para seleccionar la zona horaria para usar en la conversión de los valores de UTC a DateOnly. Puede especificar una de las siguientes reglas de conversión:  
  
-   `SpecificTimeZone`: Convierte el valor UTC a un valor DateOnly de acuerdo con el código de zona horaria de Common Data Service especificado. En este caso, también debe especificar un valor para el parámetro <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest.TimeZoneCode>.  
  
-   `CreatedByTimeZone`: Convierte un valor UTC en un valor DateOnly que el usuario que creó el registro vería en la interfaz de usuario.  
  
-   `OwnerTimeZone`: Convierte un valor UTC en un valor DateOnly que el usuario que es propietario del registro vería en la interfaz de usuario.  
  
-   `LastUpdatedByTimeZone`: Convierte un valor UTC en un valor DateOnly que el usuario que actualizó por última vez el registro vería en la interfaz de usuario.  
  
 Puede usar uno de los cuatro miembros de la clase <xref:Microsoft.Xrm.Sdk.DateTimeBehaviorConversionRule> para especificar un valor válido para el parámetro <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest.ConversionRule>.  
  
> [!NOTE]
>  Debe tener el rol de administrador del sistema en su instancia de Common Data Service para ejecutar el mensaje <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest>.  
  
 Cuando ejecute el mensaje `ConvertDateAndTimeBehavior` (Si trabaja con el servicio de organización, consulte el mensaje <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest>), se crea un trabajo del sistema (operación asincrónica) para ejecutar la solicitud de conversión. El atributo `ConvertDateAndTimeBehaviorResponse.JobId` en la respuesta del mensaje muestra el Id. de trabajo del sistema que se crea como resultado de la solicitud de la conversión. Cuando finalice el trabajo del sistema, verifique los detalles del trabajo (`AsyncOperation.Message`) para ver detalles o errores de conversión, si los hay.  
  
> [!NOTE]
>  Se recomienda agrupar la conversión de varios atributos en un solo trabajo de conversión, y ejecutar un solo trabajo de conversión al mismo tiempo para asegurarse de que no existen conflictos en la conversión y para un rendimiento óptimo del sistema.  
  
 Algunos aspectos importantes que se deben tener en cuenta mientras usa el mensaje `ConvertDateAndTimeBehavior`:  
  
-   Debe evitar cualquier cambio importante en las soluciones en Common Data Service durante la ejecución del mensaje, como importar una solución o eliminar un entidad o el atributo principal. Si lo hace podría producirse un comportamiento inesperado; sin embargo, no se producirá pérdida de datos.  
  
-   Las actualizaciones realizadas en el sistema como resultado de ejecutar el mensaje no ejecutarán flujos de trabajo y complementos.  
  
-   Las actualizaciones realizadas en el sistema como resultado de ejecutar el mensaje no cambiarán el valor de "última modificación" para los atributos, pero serán auditadas para ayudar a los administradores a determinar el tiempo de la conversión y los valores original/cambiado de un atributo.  
  
 El siguiente código de ejemplo muestra cómo usar el mensaje:  
  
```csharp
ConvertDateAndTimeBehaviorRequest request = new ConvertDateAndTimeBehaviorRequest()
{
    Attributes = new EntityAttributeCollection() 
            { 
                new KeyValuePair<string, StringCollection>("account", new StringCollection() 
                { "new_sampledatetimeattribute" }) 
            },
    ConversionRule = DateTimeBehaviorConversionRule.SpecificTimeZone.Value,
    TimeZoneCode = 190, // Time zone code for India Standard Time (IST) in CRM
    AutoConvert = false // Conversion must be done using ConversionRule
};

// Execute the request
ConvertDateAndTimeBehaviorResponse response = (ConvertDateAndTimeBehaviorResponse)_serviceProxy.Execute(request);

```
  
 Para ver un código de ejemplo completo, consulte [Ejemplo: Convertir valores de fecha y hora](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior).  
  
### <a name="see-also"></a>Vea también  
 [Ejemplo: Convertir valores de fecha y hora](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior.md)   
 [Comportamiento y formato del campo de fecha y hora](/dynamics365/customer-engagement/developer/customize/behavior-format-date-time-field)   
 [Personalizar metadatos de atributos de entidad](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)          
 <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest>      
 <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata> 