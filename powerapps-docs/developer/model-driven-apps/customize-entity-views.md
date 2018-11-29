---
title: Personalización de las vistas de la entidad (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo personalizar las vistas de entidad.
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: da2a9b57-fcd2-38c5-c670-63acf1767efa
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="customize-entity-views"></a>Personalizar vistas de entidad

Las vistas de entidad son consultas guardadas especiales que recuperan datos mediante un filtro específico. También contienen información sobre cómo se deben mostrar los datos de la vista en la aplicación. Las vistas de entidad son registros `SavedQuery` que se pueden crear mediante programación. También puede definirlas como XML, e importarlas con una solución no administrada.  
  
 Una vista de entidad es diferente de una `UserQuery`. Una consulta de usuario, llamada una vista guardada en la aplicación, es propiedad de un usuario individual, se puede asignar y compartir con otros usuarios, y pueden verla otros usuarios en función de sus privilegios de acceso. Esto es adecuado para consultas usadas frecuentemente que abarcan tipos de entidad y consultas que realizan agregación. Más información: [Consultas guardadas](../common-data-service/saved-queries.md) 
  
 También puede usar la herramienta de personalización para personalizar vistas. Más información: [Creación y edición de vistas](../../maker/model-driven-apps/create-edit-views.md)
  
<a name="BKMK_TypesOfViews"></a>   
## <a name="types-of-views"></a>Tipos de vistas  
 La siguiente tabla muestra los cinco tipos de vistas que son compatibles para la personalización. El código de tipo de una vista se almacenan en el atributo `SavedQuery.QueryType`. Tenga en cuenta que hay otros valores válidos para el atributo `QueryType` que no se muestran aquí porque esta entidad también se usa para almacenar los filtros y plantillas de Office Outlook. Para obtener más información, consulte [Plantillas y filtros de Outlook y sin conexión](../common-data-service/outlook-client/offline-outlook-filters-templates.md). 
  
 Cuando las vistas se definen para una entidad específica, el atributo `SavedQuery.ReturnedTypeCode` devuelve el nombre lógico de la entidad.  
  
|Tipo de vista|Código de tipo|Descripción|  
|---------------|---------------|-----------------|  
|**Pública**|0|- **Repeticiones**: muchas<br />- **Acciones**: crear, actualizar, eliminar<br />- **Comentarios**: puede establecer una de estas vistas como la vista pública predeterminada estableciendo `SavedQuery.IsDefault` en true.|  
|**Búsqueda avanzada**|1|- **Repeticiones**: 1<br />- **Acciones**: solo actualizar.<br />- **Comentarios**: de forma predeterminada, esta vista aparece cuando los resultados se muestran en **Búsqueda avanzada**.|  
|**Asociadas**|2|- **Repeticiones**: 1<br />- **Acciones**: solo actualizar.<br />- **Comentarios**: de forma predeterminada, esta vista se muestra cuando aparece una cuadrícula de registros relacionados en el panel de navegación de un registro.|  
|**Búsqueda rápida**|4|- **Repeticiones**: 1<br />- **Acciones**: solo actualizar.<br />- **Comentarios**: esta vista define las columnas en las que se buscará cuando un usuario busque registros mediante el campo de búsqueda de una vista de lista.|  
|**Búsqueda**|64|- **Repeticiones**: 1<br />- **Acciones**: solo actualizar.<br />- **Comentarios**: esta es la vista predeterminada que se usará para buscar un registro cuando no se haya configurado ninguna otra vista para el campo de búsqueda.|  
  
<a name="BKMK_CreateViews"></a>   
## <a name="create-views"></a>Crear vistas  
 Para crear una vista pública, especifique las propiedades siguientes:
  
- `SavedQuery.Name`: identificador único de la vista guardada.
  
- `SavedQuery.ReturnedTypeCode`: coincide con el nombre lógico de la entidad. 
  
- `SavedQuery.FetchXml`: Consulte [Usar FetchXML para crear una consulta](../common-data-service/use-fetchxml-construct-query.md).  
  
- `SavedQuery.LayoutXml`: Vea el elemento `layoutxml` en el [esquema de archivo de soluciones de personalización](../common-data-service/customization-solutions-file-schema.md) para los elementos válidos.
  
- `SavedQuery.QueryType`: debe ser siempre cero (0).  
  
  El siguiente ejemplo crea una vista pública nueva para la entidad de oportunidad:  
  
  ```csharp
  System.String layoutXml =
  @"<grid name='resultset' object='3' jump='name' select='1' 
    preview='1' icon='1'>
    <row name='result' id='opportunityid'>
    <cell name='name' width='150' /> 
    <cell name='customerid' width='150' /> 
    <cell name='estimatedclosedate' width='150' /> 
    <cell name='estimatedvalue' width='150' /> 
    <cell name='closeprobability' width='150' /> 
    <cell name='opportunityratingcode' width='150' /> 
    <cell name='opportunitycustomeridcontactcontactid.emailaddress1' 
        width='150' disableSorting='1' /> 
    </row>
  </grid>";

  System.String fetchXml =
  @"<fetch version='1.0' output-format='xml-platform' 
    mapping='logical' distinct='false'>
    <entity name='opportunity'>
    <order attribute='estimatedvalue' descending='false' /> 
    <filter type='and'>
        <condition attribute='statecode' operator='eq' 
        value='0' /> 
    </filter>
    <attribute name='name' /> 
    <attribute name='estimatedvalue' /> 
    <attribute name='estimatedclosedate' /> 
    <attribute name='customerid' /> 
    <attribute name='opportunityratingcode' /> 
    <attribute name='closeprobability' /> 
    <link-entity alias='opportunitycustomeridcontactcontactid' 
        name='contact' from='contactid' to='customerid' 
        link-type='outer' visible='false'>
        <attribute name='emailaddress1' /> 
    </link-entity>
    <attribute name='opportunityid' /> 
    </entity>
  </fetch>";

  SavedQuery sq = new SavedQuery
    {
      Name = "A New Custom Public View",
      Description = "A Saved Query created in code",
      ReturnedTypeCode = "opportunity",
      FetchXml = fetchXml,
      LayoutXml = layoutXml,
      QueryType = 0
    };
                    
  _customViewId = _serviceProxy.Create(sq);
  Console.WriteLine("A new view with the name {0} was created.", sq.Name);
  ```  
  
<a name="BKMK_UpdateViews"></a>   
## <a name="update-views"></a>Actualizar vistas  
 Si la propiedad administrada `SavedQuery.IsCustomizable` permite que se actualice la vista, puede usar el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> o el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> para actualizar la vista.  
  
<a name="BKMK_DeleteViews"></a>   
## <a name="delete-views"></a>Eliminar vistas  
 Debe eliminar solo las consultas guardadas que ha creado. Un componente de la solución o parte de la aplicación puede depender de una consulta guardada específica. Si hubiera consultas que no desea que aparezcan en la aplicación, debe desactivarlas.  
  
<a name="BKMK_RetrieveViews"></a>   
## <a name="retrieve-views"></a>Recuperar vistas  
 Use <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> o <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> para recuperar registros de consulta guardados.  
  
 El siguiente ejemplo recupera todas las vistas públicas para la entidad de oportunidad:  
  
 ```csharp
 QueryExpression mySavedQuery = new QueryExpression
        {
            ColumnSet = new ColumnSet("savedqueryid", "name", "querytype", "isdefault", "returnedtypecode", "isquickfindquery"),
            EntityName = SavedQuery.EntityLogicalName,
            Criteria = new FilterExpression
            {
                Conditions =
{
    new ConditionExpression
    {
        AttributeName = "querytype",
        Operator = ConditionOperator.Equal,
        Values = {0}
    },
    new ConditionExpression
    {
        AttributeName = "returnedtypecode",
        Operator = ConditionOperator.Equal,
        Values = {Opportunity.EntityTypeCode}
    }
}
            }
        };
        RetrieveMultipleRequest retrieveSavedQueriesRequest = new RetrieveMultipleRequest { Query = mySavedQuery };

        RetrieveMultipleResponse retrieveSavedQueriesResponse = (RetrieveMultipleResponse)_serviceProxy.Execute(retrieveSavedQueriesRequest);

        DataCollection<Entity> savedQueries = retrieveSavedQueriesResponse.EntityCollection.Entities;

        //Display the Retrieved views
        foreach (Entity ent in savedQueries)
        {
            SavedQuery rsq = (SavedQuery)ent;
            Console.WriteLine("{0} : {1} : {2} : {3} : {4} : {5},", rsq.SavedQueryId, rsq.Name, rsq.QueryType, rsq.IsDefault, rsq.ReturnedTypeCode, rsq.IsQuickFindQuery);
        }
```
  
<a name="BKMK_DeactivateViews"></a>   
## <a name="deactivate-views"></a>Desactivar vistas  
 Si no desea que una vista pública aparezca en la aplicación, puede desactivarla. No puede desactivar una vista pública que se establece como la vista predeterminada. El siguiente ejemplo deshabilita la vista **Oportunidades cerradas del año fiscal actual** para la entidad de oportunidad:  
  
 ```csharp
 System.String SavedQueryName = "Closed Opportunities in Current Fiscal Year";
QueryExpression ClosedOpportunitiesViewQuery = new QueryExpression
{
    ColumnSet = new ColumnSet("savedqueryid", "statecode", "statuscode"),
    EntityName = SavedQuery.EntityLogicalName,
    Criteria = new FilterExpression
    {
        Conditions =
        {
            new ConditionExpression
            {
                AttributeName = "querytype",
                Operator = ConditionOperator.Equal,
                Values = {0}
            },
            new ConditionExpression
            {
                AttributeName = "returnedtypecode",
                Operator = ConditionOperator.Equal,
                Values = {Opportunity.EntityTypeCode}
            },
                            new ConditionExpression
            {
                AttributeName = "name",
                Operator = ConditionOperator.Equal,
                Values = {SavedQueryName}
            }
        }
    }
};

RetrieveMultipleRequest retrieveOpportuntiesViewRequest = new RetrieveMultipleRequest { Query = ClosedOpportunitiesViewQuery };

RetrieveMultipleResponse retrieveOpportuntiesViewResponse = (RetrieveMultipleResponse)_serviceProxy.Execute(retrieveOpportuntiesViewRequest);

SavedQuery OpportunityView = (SavedQuery)retrieveOpportuntiesViewResponse.EntityCollection.Entities[0];
_viewOriginalState = (SavedQueryState)OpportunityView.StateCode;
_viewOriginalStatus = OpportunityView.StatusCode;


SetStateRequest ssreq = new SetStateRequest
{
    EntityMoniker = new EntityReference(SavedQuery.EntityLogicalName, (Guid)OpportunityView.SavedQueryId),
    State = new OptionSetValue((int)SavedQueryState.Inactive),
    Status = new OptionSetValue(2)
};
_serviceProxy.Execute(ssreq);
 ```  
  
<a name="BKMK_EditFilterOrSorting"></a>   
## <a name="edit-filter-criteria-or-configure-sorting"></a>Editar los criterios de filtro o configurar la ordenación  
 Para modificar el filtro o editar cómo se ordenan los datos, debe establecer el atributo `SavedQuery.FetchXml`. Para obtener más información, vea [Usar FetchXML para consultar datos](/powerapps/developer/common-data-service/use-fetchxml-construct-query).  
  
> [!TIP]
>  Si no está familiarizado con FetchXML los siguientes mensajes se pueden usar para convertir entre QueryExpression y FetchXML:<xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> y <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>.  
  
<a name="BKMK_EditColumns"></a>   
## <a name="edit-columns"></a>Editar columnas  
 Las columnas que desea mostrar en las vistas se pueden obtener de la entidad o las entidades relacionadas. Para obtener más información sobre cómo especificar las columnas para mostrar, vea el elemento `layoutxml` en el [esquema de archivo de soluciones de personalización](../common-data-service/customization-solutions-file-schema.md).  
  
<a name="BKMK_CustomIcons"></a>   
## <a name="add-custom-icons-with-tooltip-for-a-column"></a>Agregar iconos personalizados con información sobre herramientas para una columna  
 Puede agregar un icono personalizado con texto de información sobre herramientas en una columna según el valor de la columna; también puede especificar el texto de información sobre herramientas localizado. Esto puede realizarse agregando iconos personalizados como recursos web de imagen en su instancia y luego usar un recurso web de JavaScript para agregar código JavaScript para que una columna muestre los iconos según el valor de la columna.  
  
> [!NOTE]
>  Agregar iconos personalizados con información sobre herramientas se admite únicamente para cuadrículas de sólo lectura; esta característica no es compatible con las cuadrículas editables. Para obtener más información acerca de las cuadrículas editables, consulte [Usar cuadrículas editables](/powerapps/developer/model-driven-apps/use-editable-grids).  
  
 Dos atributos nuevos, `imageproviderwebresource` y `imageproviderfunctionname`, se agregan al elemento `cell` del layoutxml de la consulta guardada que le permite especificar el nombre de un recurso web y un nombre de función JavaScript para mostrar iconos personalizados y texto de información sobre herramientas para una columna. El código JavaScript se ejecuta cuando se carga la página.  
  
 También puede usar los nuevos campos **Recurso web** y **Nombre de función** en la página **Propiedades de columna** mientras modifica la propiedad de un atributo (columna) en una definición de vista para especificar el nombre del recurso web y el nombre de función de JavaScript.  
  
 El código de ejemplo siguiente demuestra cómo puede especificar mediante programación un recurso web y un nombre de función JavaScript para agregar iconos personalizados e información sobre herramientas para la columna `opportunityratingcode` en layoutxml:  
  
```csharp  
System.String layoutXml =  
@"<grid name='resultset' object='3' jump='name' select='1'  
  preview='1' icon='1'>  
  <row name='result' id='opportunityid'>  
    <cell name='name' width='150' />  
    <cell name='customerid' width='150' />  
    <cell name='estimatedclosedate' width='150' />  
    <cell name='estimatedvalue' width='150' />  
    <cell name='closeprobability' width='150' />  
    <cell name='opportunityratingcode' width='150' imageproviderwebresource='new_SampleWebResource'  
          imageproviderfunctionname='displayIconTooltip' />  
    <cell name='opportunitycustomeridcontactcontactid.emailaddress1'  
        width='150' disableSorting='1' />  
  </row>  
</grid>";  
```  
  
 La función JavaScript para mostrar iconos personalizados e informaciones sobre herramientas espera los dos argumentos siguientes: el objeto de fila completo especificado en layoutxml y el Id. de configuración regional del usuario que llama (LCID). El parámetro LCID permite especificar el texto de información sobre herramientas para el icono en varios idiomas. Para obtener más información sobre los idiomas admitidos, vea [Habilitar idiomas adicionales](/dynamics365/customer-engagement/customize/enable-additional-languages) <!-- TODO need to update the link in the powerapps repo--> e [Instalación o actualización de paquetes de idiomas](https://technet.microsoft.com/library/hh699674.aspx). Para ver una lista de valores de Id. de configuración regional (LCID) que puede usar en el código, consulte [Id. de configuración regional asignados por Microsoft](https://go.microsoft.com/fwlink/?linkid=829588).  
  
 Suponiendo que muy probablemente agregará iconos personalizados para un tipo de conjunto de opciones de atributo, ya que tiene un conjunto limitado de opciones predefinidas, asegúrese de que usa el valor entero de las opciones en lugar de etiqueta para evitar romper el código debido a cambios en la cadena de etiqueta localizada. Además, en la función JavaScript, especifique únicamente el nombre de un recurso web de imagen que desee usar como icono para un valor del atributo. La imagen debe ser de tamaño 16x16 píxeles; las imágenes más grandes automáticamente se reducirán proporcionalmente al tamaño 16x16 píxeles.  
  
 El siguiente código de ejemplo muestra iconos e informaciones sobre herramientas distintos basándose en uno de los valores (1: Muy interesado, 2: Algo interesado, 3: No interesado) del atributo `opportunityratingcode (Rating)`. El código de ejemplo también muestra cómo mostrar texto de información sobre herramientas localizado. Para que este ejemplo funcione, debe crear tres recursos web de imagen cada uno con imágenes de 16 x 16 (![botón de clasificación Muy interesado](media/dynamics365hotgridicon.png "botón de clasificación Muy interesado"), ![símbolo de clasificación Algo interesado](media/dynamics365warmgridicon.png "símbolo de clasificación Algo interesado") y ![botón de clasificación No interesado](media/dynamics365coldgridicon.png "botón de clasificación No interesado")) en su instancia con los siguientes nombres respectivamente: `new_Hot`, `new_Warm` y `new_Cold`.  
  
```javascript 
function displayIconTooltip(rowData, userLCID) {      
    var str = JSON.parse(rowData);  
    var coldata = str.opportunityratingcode_Value;  
    var imgName = "";  
    var tooltip = "";  
    switch (coldata) {  
        case 1:  
            imgName = "new_Hot";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Hot";  
                    break;  
                default:  
                    tooltip = "Opportunity is Hot";  
                    break;  
            }  
            break;  
        case 2:  
            imgName = "new_Warm";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Warm";  
                    break;  
                default:  
                    tooltip = "Opportunity is Warm";  
                    break;  
            }  
            break;  
        case 3:  
            imgName = "new_Cold";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Cold";  
                    break;  
                default:  
                    tooltip = "Opportunity is Cold";  
                    break;  
            }  
            break;  
        default:  
            imgName = "";  
            tooltip = "";  
            break;  
    }  
    var resultarray = [imgName, tooltip];  
    return resultarray;  
}  
```  
  
 Esto muestra los valores de la columna `Rating` con los iconos adecuados según el valor, y el texto de información sobre herramientas del icono cuando mantiene el mouse sobre los iconos.  
  
 ![Iconos personalizados que se muestran para una columna en una vista](media/customiconsinviews.png "Iconos personalizados que se muestran para una columna en una vista")  
  
<a name="BKMK_SetAsDefault"></a>   
## <a name="set-as-default"></a>Establecer como predeterminado  
 Solo se puede configurar una vista pública activa como la vista predeterminada. Para establecer una vista como predeterminada, establezca la propiedad `IsDefault` en true.  
  
