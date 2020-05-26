---
title: 'Ejemplo: Biblioteca paralela de tareas con CrmServiceClient (Common Data Service)| Microsoft Docs'
description: La Biblioteca de tareas paralelas (TPL) hace que los desarrolladores sean más productivos al simplificar el proceso de agregar paralelismo y concurrencia a las aplicaciones. Este ejemplo demuestra su uso con CrmServiceClient
ms.custom: ''
ms.date: 04/20/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20aeaaf471e99e2201de90ceb1dbc13985baf7a4
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276714"
---
# <a name="sample-task-parallel-library-with-crmserviceclient"></a>Ejemplo: Biblioteca paralela de tareas con CrmServiceClient

La Biblioteca de tareas paralelas (TPL) hace que los desarrolladores sean más productivos al simplificar el proceso de agregar paralelismo y concurrencia a las aplicaciones.

Agregar paralelismo y concurrencia puede mejorar significativamente el rendimiento total de las aplicaciones que necesitan realizar una gran cantidad de operaciones de CDS en un corto período de tiempo.

Descargue el ejemplo: [Biblioteca paralela de tareas con CrmServiceClient](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/Xrm%20Tooling/TPLCrmServiceClient).

## <a name="how-to-run-the-sample"></a>Cómo ejecutar el ejemplo

1. Descargar y extraer la muestra para que tenga una copia local.  
2. Abra el archivo `TPLCrmServiceClient.sln` en Visual Studio.  
3. Presione **F5** para compilar y ejecutar el programa.  

## <a name="demonstrates"></a>Demostraciones

Dado que la [clase Microsoft.Xrm.Tooling.Connector.CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) incluye control de errores transitorios generados por los límites de protección del servicio CDS, la combinación de TPL y CrmServiceClient es valiosa para crear aplicaciones que puedan optimizar el rendimiento, mientras son resistentes a los errores de límite de protección del servicio al volver a intentar las solicitudes rechazadas debido a estos límites.

Más información: [Límites de API de protección de servicios](../api-limits.md)

El [método CrmServiceClient.Clone](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient.clone) permite que TPL use el cliente con múltiples subprocesos.

Este sencillo ejemplo generará una serie de registros de entidad de cuenta utilizando el [método System.Threading.Tasks.Parallel.ForEach](/dotnet/api/system.threading.tasks.parallel.foreach).

Luego usará esa técnica nuevamente para eliminar las entidades creadas.

**NOTA**:
> De manera predeterminada, esta muestra creará solo 10 registros, lo que no es suficiente para alcanzar los errores de límite de API de protección de servicio. Si aumenta el valor de la variable `numberOfRecords` a 10 000, puede usar Fiddler para observar cómo se rechazarán y volverán a intentar algunas de las solicitudes.

Este ejemplo no está configurado para deshabilitar las cookies de Azure Affinity, que es otra recomendación para mejorar el rendimiento. Para habilitar esto, agregue lo siguiente al archivo App.config de su aplicación:

```xml
  <appSettings>
    <add key="PreferConnectionAffinity"
         value="false" />
  </appSettings>
```

## <a name="code-listing"></a>Lista de código

El código para este ejemplo se divide entre dos archivos que definen diferentes partes de la misma clase parcial.

SampleProgram.cs contiene este código:

```csharp
using Microsoft.Xrm.Sdk;
using Microsoft.Xrm.Tooling.Connector;
using System;
using System.Collections.Generic;
using System.Linq;

namespace PowerApps.Samples
{
    public partial class SampleProgram
    {
        // Limit on the max degree of parallelism
        private static int maxDegreeOfParallelism = 10;

        //How many records to create with this sample.
        private static readonly int numberOfRecords = 10;

        [STAThread] // Added to support UX
        private static void Main()
        {
            CrmServiceClient service = null;

            try
            {
                service = SampleHelpers.Connect("Connect");
                if (service.IsReady)
                {
                    #region Sample Code

                    #region Set up

                    SetUpSample(service);

                    #endregion Set up

                    #region Demonstrate

                    #region Optimize Connection settings

                    //Change max connections from .NET to a remote service default: 2
                    System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
                    //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
                    System.Threading.ThreadPool.SetMinThreads(100, 100);
                    //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
                    System.Net.ServicePointManager.Expect100Continue = false;
                    //Can decreas overall transmission overhead but can cause delay in data packet arrival
                    System.Net.ServicePointManager.UseNagleAlgorithm = false;

                    #endregion Optimize Connection settings

                    // Generate a list of account entities to create.

                    var accountsToImport = new List<Entity>();
                    var count = 0;
                    Console.WriteLine($"Preparing to create {numberOfRecords} acccount records");
                    while (count < numberOfRecords)
                    {
                        var account = new Entity("account");
                        account["name"] = $"Account {count}";
                        accountsToImport.Add(account);
                        count++;
                    }

                    try
                    {
                        Console.WriteLine($"Creating {accountsToImport.Count} accounts");

                        var startCreate = DateTime.Now;

                        //Import the list of accounts
                        var createdAccounts = CreateEntities(service, accountsToImport);

                        var secondsToCreate = (DateTime.Now - startCreate).TotalSeconds;

                        Console.WriteLine($"Created {accountsToImport.Count} accounts in  {Math.Round(secondsToCreate)} seconds.");

                        Console.WriteLine($"Deleting {createdAccounts.Count} accounts");
                        var startDelete = DateTime.Now;

                        //Delete the list of accounts created
                        DeleteEntities(service, createdAccounts.ToList());

                        var secondsToDelete = (DateTime.Now - startDelete).TotalSeconds;

                        Console.WriteLine($"Deleted {createdAccounts.Count} accounts in {Math.Round(secondsToDelete)} seconds.");
                    }
                    catch (AggregateException)
                    {
                        // Handle exceptions
                    }

                    Console.WriteLine("Done.");
                    Console.ReadLine();
                }

                #endregion Demonstrate

                #endregion Sample Code

                else
                {
                    const string UNABLE_TO_LOGIN_ERROR = "Unable to Login to Common Data Service";
                    if (service.LastCrmError.Equals(UNABLE_TO_LOGIN_ERROR))
                    {
                        Console.WriteLine("Check the connection string values in cds/App.config.");
                        throw new Exception(service.LastCrmError);
                    }
                    else
                    {
                        throw service.LastCrmException;
                    }
                }
            }
            catch (Exception ex)
            {
                SampleHelpers.HandleException(ex);
            }
            finally
            {
                if (service != null)
                    service.Dispose();

                Console.WriteLine("Press <Enter> to exit.");
                Console.ReadLine();
            }
        }
    }
}
```

SampleMethods.cs contiene la definición de dos métodos estáticos (`CreateEntities` y `DeleteEntities`) utilizados en el código:


```csharp
/// <summary>
/// Creates entities in parallel
/// </summary>
/// <param name="svc">The CrmServiceClient instance to use</param>
/// <param name="entities">A List of entities to create.</param>
/// <returns></returns>
private static ConcurrentBag<EntityReference> CreateEntities(CrmServiceClient svc, List<Entity> entities)
{
    var createdEntityReferences = new ConcurrentBag<EntityReference>();

    Parallel.ForEach(entities,
        new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism },
        () =>
        {
            //Clone the CrmServiceClient for each thread
            return svc.Clone();
        },
        (entity, loopState, index, threadLocalSvc) =>
        {
            // In each thread, create entities and add them to the ConcurrentBag
            // as EntityReferences
            createdEntityReferences.Add(
                new EntityReference(
                    entity.LogicalName,
                    threadLocalSvc.Create(entity)
                    )
                );

            return threadLocalSvc;
        },
        (threadLocalSvc) =>
        {
            //Dispose the cloned CrmServiceClient instance
            if (threadLocalSvc != null)
            {
                threadLocalSvc.Dispose();
            }
        });

    //Return the ConcurrentBag of EntityReferences
    return createdEntityReferences;
}

/// <summary>
/// Deletes a list of entity references
/// </summary>
/// <param name="svc">The CrmServiceClient instance to use</param>
/// <param name="entityReferences">A List of entity references to delete.</param>
private static void DeleteEntities(CrmServiceClient svc, List<EntityReference> entityReferences)
{
    Parallel.ForEach(entityReferences,
        new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism },
        () =>
        {
            //Clone the CrmServiceClient for each thread
            return svc.Clone();
        },
        (er, loopState, index, threadLocalSvc) =>
        {
            // In each thread, delete the entities
            threadLocalSvc.Delete(er.LogicalName, er.Id);

            return threadLocalSvc;
        },
        (threadLocalSvc) =>
        {
            //Dispose the cloned CrmServiceClient instance
            if (threadLocalSvc != null)
            {
                threadLocalSvc.Dispose();
            }
        });
}
```

### <a name="more-information"></a>Más información

[Biblioteca paralela de tareas (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)