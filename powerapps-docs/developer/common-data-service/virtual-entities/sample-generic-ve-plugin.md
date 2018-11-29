---
title: 'Ejemplo: Complemento de proveedor de datos de entidad virtual genérico (Common Data Service para aplicaciones | MicrosoftDocs)'
description: El ejemplo muestra cómo implementar un complemento de entidad virtual personalizado genérico en Dynamics 365.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
  - Dynamics 365 (online)
ms.assetid: d329dade-16c5-46e9-8dec-4b8efb996d24
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="sample-generic-virtual-entity-data-provider-plug-in"></a>Ejemplo: Complemento de proveedor de datos de entidad virtual genérico

## <a name="demonstrates"></a>Demostraciones

Este ejemplo muestra una implementación mínima para un complemento de proveedor de datos de entidad virtual genérico de CDS para aplicaciones, **DropboxRetrieveMultiplePlugin**, para el servicio de uso compartido de archivos [Dropbox](https://www.dropbox.com/). Utiliza el método "básico" de traducir la expresión <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> creando la clase visitante personalizada **DropBoxExpressionVisitor**. Devuelve una colección de archivos que cumplen con los criterios de búsqueda como <xref:Microsoft.Xrm.Sdk.EntityCollection>. 

## <a name="getting-started"></a>Introducción

Para crear este ejemplo, primero debe instalar los paquetes NuGet [Dropbox.Api](https://www.nuget.org/packages/Dropbox.Api/) y [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/) en la solución.  También necesitará una cuenta de Dropbox y pasará un token de acceso real al crear una instancia del **DropboxClient**.

Agregue las siguientes instrucciones de uso a su código:

```csharp
using Microsoft.Xrm.Sdk;
using Microsoft.Xrm.Sdk.Query;
using Dropbox.Api;
using Dropbox.Api.Files;
```

## <a name="sample-code"></a>Código de ejemplo  

```csharp  

public class DropBoxExpressionVisitor : QueryExpressionVisitorBase
{
    public string SearchKeyWords { get; private set; }

    public override QueryExpression Visit(QueryExpression query)
    {
        // Very simple visitor that extracts search keywords
        var filter = query.Criteria;
        if (filter.Conditions.Count > 0)
        {
            foreach (ConditionExpression condition in filter.Conditions)
            {
                if (condition.Operator == ConditionOperator.Like && condition.Values.Count > 0)
                {
                    string exprVal = (string)condition.Values[0];

                    if (exprVal.Length > 2)
                    {
                        this.SearchKeyWords += " " + exprVal.Substring(1, exprVal.Length - 2);
                    }
                }
            }
            return query;
        }
    }
}

public class DropboxRetrieveMultiplePlugin : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
        var qe = (QueryExpression)context.InputParameters["Query"];
        if (qe != null)
        {
            var visitor = new DropBoxExpressionVisitor();
            qe.Accept(visitor);
            using (var dbx = new DropboxClient(AccessToken))
            {
                if (visitor.SearchKeyWords != string.Empty)
                {
                    var searchCriteria = new SearchArg(string.Empty, visitor.SearchKeyWords);
                    var task = Task.Run(() => this.SearchFile(dbx, searchCriteria));
                    context.OutputParameters["BusinessEntityCollection"] = task.Result;
                }
            }
        }
    }

    public async Task<EntityCollection> SearchFile(DropboxClient dbx, SearchArg arg)
    {
        EntityCollection ec = new EntityCollection();
        var list = await dbx.Files.SearchAsync(arg);
        foreach (var item in list.Matches)
        {
            if (item.Metadata.IsFile)
            {
                Entity e = new Entity("new_dropbox");
                e.Attributes.Add("new_dropboxid", Guid.NewGuid());
                e.Attributes.Add("new_filename", item.Metadata.AsFile.Name);
                e.Attributes.Add("new_filesize", item.Metadata.AsFile.Size);
                e.Attributes.Add("new_modifiedon", item.Metadata.AsFile.ServerModified);
                ec.Entities.Add(e);
            }
        }
        return ec;
    }
}

``` 

### <a name="see-also"></a>Vea también

[Introducción a las entidades virtuales](get-started-ve.md)<br />
[Consideraciones sobre API para entidades virtuales](api-considerations-ve.md)<br />
[Proveedores de datos de entidad virtual personalizados](custom-ve-data-providers.md)