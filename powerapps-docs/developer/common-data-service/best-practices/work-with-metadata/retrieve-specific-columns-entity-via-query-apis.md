---
title: Recuperar columnas específicas para una entidad mediante API de consulta | MicrosoftDocs
description: Las consultas enviadas para recuperar datos deben incluir columnas específicas en la instancia de ColumnSet asociadas a la consulta en lugar de a todas las columnas.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
--- 
# <a name="do-not-retrieve-entity-all-columns-via-query-apis"></a>No recuperar la entidad todas las columnas mediante las API de consulta

**Categoría**: rendimiento

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Recuperar todas las columnas puede provocar:

- Problemas de rendimiento por la cantidad de datos recuperados
- Ejecución involuntaria de complementos y procesos

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Para obtener un rendimiento óptimo, debe seleccionar solo una cantidad mínima de datos necesarios por su aplicación cuando se consultan datos de Common Data Service para aplicaciones. 

### <a name="columnset-parameter"></a>Parámetro de ColumnSet

Cuando usa el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> establezca el parámetro `columnSet` en una instancia <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> con columnas especificadas.  Cuando se use <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> establezca la propiedad <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.ColumnSet> con los atributos requeridos.

Estos son algunos ejemplos:

- Sobrecarga del constructor [ColumnSet (columnas de la cadena [] del parámetro)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_String___) para <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>.

    ```csharp
        var query = new QueryExpression("account")
        {
            ColumnSet = new ColumnSet("name", "address1_city")
        };

        var results = service.RetrieveMultiple(query);
    ```

- Sobrecarga del constructor [ColumnSet (columnas de la cadena [] del parámetro)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_String___) para <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>.

    ```csharp
        var entity = service.Retrieve("account", Guid.NewGuid(), new ColumnSet("name", "address1_city"));
    ```

- Llamada al método <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.<xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AddColumn(System.String)> .

    ```csharp
        var query = new QueryExpression("account");
        query.ColumnSet.AddColumn("name");
        query.ColumnSet.AddColumn("address1_city");

        var results = service.RetrieveMultiple(query);
    ```

- Llamada al método <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.<xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AddColumns(System.String[])> .

    ```csharp
        var query = new QueryExpression("account");
        query.ColumnSet.AddColumns("name", "address1_city");

        var results = service.RetrieveMultiple(query);
    ```

Las siguientes contienen una instancia <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>:

- <xref:Microsoft.Crm.Sdk.Messages.ConvertQuoteToSalesOrderRequest>
- <xref:Microsoft.Crm.Sdk.Messages.GenerateInvoiceFromOpportunityRequest>
- <xref:Microsoft.Crm.Sdk.Messages.GenerateQuoteFromOpportunityRequest>
- <xref:Microsoft.Crm.Sdk.Messages.GenerateSalesOrderFromOpportunityRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveAllChildUsersSystemUserRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveBusinessHierarchyBusinessUnitRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveMembersTeamRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveSubsidiaryTeamsBusinessUnitRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveSubsidiaryUsersBusinessUnitRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveTeamsSystemUserRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUnpublishedRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUserSettingsSystemUserRequest>
- <xref:Microsoft.Crm.Sdk.Messages.ReviseQuoteRequest>
- <xref:Microsoft.Crm.Sdk.Messages.SearchByBodyKbArticleRequest>
- <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>
- <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

Las consultas que incluyen un <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> definido donde la propiedad <xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AllColumns> es `true` indican a la plataforma que emita un comando de SQL para ["SELECT *"](https://technet.microsoft.com/library/ms189287.aspx) en todos los datos físicos incluidos en el plan de consultas.  Este escenario debe evitarse siempre que sea posible.

> [!WARNING]
> Estos escenarios deben evitarse.

- Llamada al método establecedor <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.<xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AllColumns> .

    ```csharp
        var columns = new ColumnSet();
        columns.AllColumns = true;

        var query = new QueryExpression("account");
        query.ColumnSet = columns;

        var results = service.RetrieveMultiple(query);
    ```

- Sobrecarga del constructor [ColumnSet (valor booleano allColumns)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_Boolean_).

    ```csharp
        var query = new QueryExpression("account")
        {
            ColumnSet = new ColumnSet(true)
        };

        var results = service.RetrieveMultiple(query);
    ```

- Sobrecarga del constructor [ColumnSet (valor booleano allColumns)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_Boolean_) para <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>.

    ```csharp
        var entity = service.Retrieve("account", Guid.Parse("bec45132-392a-4617-b935-a64ef04738e4"), new ColumnSet(true));
    ```

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Las consultas enviadas para recuperar los datos de Microsoft Dynamics 365 no deben seleccionar todas las columnas.  En su lugar, especifique columnas individuales específicas que se deben especificar en la instancia <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> asociada a la consulta. Recuperar todas las columnas de una entidad puede tener un impacto negativo en el rendimiento. Además, puede desencadenar involuntariamente eventos de complementos al recuperar columnas con la que no trabaja y emitir una actualización.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

<xref href="Microsoft.Xrm.Sdk.Query.ColumnSet?text=ColumnSet Class" /><br />
[Usar la clase ColumnSet](../../org-service/use-the-columnset-class.md)<br />
[Crear consultas con QueryExpression](../../org-service/build-queries-with-queryexpression.md)<br />