---
title: Web API CDSWebApiService Ejemplo de operaciones en paralelo (C#) (Common Data Service) | Microsoft Docs
description: Este ejemplo demuestra el uso de la Biblioteca de tareas paralelas (TPL) con solicitudes sincrónicas.
ms.custom: ''
ms.date: 04/20/2020
ms.service: powerapps
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: pehecke
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8bf51ab169671f95dede5e8b68ca1fcfff8a2a39
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276712"
---
# <a name="web-api-cdswebapiservice-parallel-operations-sample-c"></a>Web API CDSWebApiService Ejemplo de operaciones en paralelo (C#)

Este ejemplo muestra cómo usar un bucle [Método System.Threading.Tasks.Parallel.ForEach](/dotnet/api/system.threading.tasks.parallel.foreach) para habilitar el paralelismo de datos sobre un conjunto de registros para crear en CDS.

Este ejemplo utiliza los métodos síncronos de la clase CDSWebApiService dentro de las operaciones. Debido a que la clase CDSWebApiService puede administrar los límites de la API de protección de servicio, este código puede ser resistente a los errores transitorios 429 que los clientes deben esperar. Lo reintentará un número configurable de veces. 

Más información:

- [Web API CDSWebApiService clase de muestra (C#)](cdswebapiservice.md)
- [Límites de la API de protección de servicio](../../api-limits.md)

Esta muestra se basa en el ejemplo [Cómo: escribir un bucle simple Parallel.ForEach](/dotnet/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop), pero modificado para realizar operaciones de creación y eliminación con entidades CDS utilizando los métodos sincrónicos proporcionados por la clase CDSWebApiService.

> [!NOTE]
> Si desea utilizar Fiddler para observar los límites esperados de la API de protección del servicio, deberá establecer el número de registros para crear en alrededor de 10 000. Comenzarán a aparecer después de 5 minutos. Observe cómo la aplicación vuelve a intentar los fallos y completa el flujo de todos los registros.

## <a name="prerequisites"></a>Requisitos previos

Los siguientes elementos son necesarios para crear y ejecutar los ejemplos de CDSWebApiService C#:

- Microsoft Visual Studio 2019. 
- Acceso a Common Data Service con privilegios para realizar operaciones CRUD.
  
<a name="bkmk_runSample"></a>
  
## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Vaya a [Ejemplo CDSWebApiService de la API web](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/CDSWebApiService), clone o descargue el repositorio de ejemplos y extraiga su contenido en una carpeta local.

1. Abre el [CDSWebApiService.sln](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/CDSWebApiService.sln).

1. Selecciona el proyecto **Operaciones paralelas** y abra la App.config. Este es un archivo común [App.config](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/App.config) utilizado por todos los ejemplos en esta solución. Una vez edite esto, puede ejecutar cualquiera de los ejemplos en esta solución.

1. Debes editar los valores `Url`, `UserPrincipalName` y `Password` para establecer la instancia de CDS y las credenciales a las que desea conectarse.

    ```xml
        <add name="Connect"
            connectionString="Url=https://yourorg.api.crm.dynamics.com;
            Authority=null;
            ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
            RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
            UserPrincipalName=you@yourorg.onmicrosoft.com;
            Password=y0urp455w0rd;
            CallerObjectId=null;
            Version=9.1;
            MaxRetries=3;
            TimeoutInSeconds=180;
            "/>
    ```

1. Asegúrese de que el proyecto **Operaciones paralelas** se establece como el proyecto de inicio. El nombre del proyecto debe estar en negrita para indicar que es el proyecto de inicio. Si el nombre no está en negrita, haga clic con el botón derecho en el explorador de soluciones y seleccione **Establecer como proyecto de inicio**.

1. Presione F5 para ejecutar el programa en modo de depuración.

## <a name="code-listing"></a>Lista de código

Esta muestra depende del ensamblado incluido en el proyecto CDSWebAPIService. Para obtener información sobre los métodos que proporciona esta clase, consulte: [Web API CDSWebApiService clase de muestra (C#)](cdswebapiservice.md).

El siguiente es el código del archivo Program.cs:

```csharp
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Configuration;
using System.Threading.Tasks;

namespace PowerApps.Samples
{
    internal class Program
    {
        //Get configuration data from App.config connectionStrings
        private static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

        private static readonly ServiceConfig serviceConfig = new ServiceConfig(connectionString);

        //Controls the max degree of parallelism
        private static readonly int maxDegreeOfParallelism = 10;

        //How many records to create with this sample.
        private static readonly int numberOfRecords = 100;

        private static void Main()
        {
            #region Optimize Connection

            //Change max connections from .NET to a remote service default: 2
            System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
            //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
            System.Threading.ThreadPool.SetMinThreads(100, 100);
            //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
            System.Net.ServicePointManager.Expect100Continue = false;
            //Can decreas overall transmission overhead but can cause delay in data packet arrival
            System.Net.ServicePointManager.UseNagleAlgorithm = false;

            #endregion Optimize Connection

            var parallelOptions = new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism };

            var count = 0;

            //Will be populated with account records to import
            List<JObject> accountsToImport = new List<JObject>();
            //ConcurrentBag is a thread-safe, unordered collection of objects.
            ConcurrentBag<Uri> accountsToDelete = new ConcurrentBag<Uri>();
            Console.WriteLine($"Preparing to create {numberOfRecords} acccount records using Web API.");

            //Add account records to the list to import
            while (count < numberOfRecords)
            {
                var account = new JObject
                {
                    ["name"] = $"Account {count}"
                };
                accountsToImport.Add(account);
                count++;
            }

            try
            {
                using (CDSWebApiService svc = new CDSWebApiService(serviceConfig))
                {
                    Console.WriteLine($"Creating {accountsToImport.Count} accounts");
                    var startCreate = DateTime.Now;

                    //Create the accounts in parallel
                    Parallel.ForEach(accountsToImport, parallelOptions, (account) =>

                    {
                        //Add the Uri returned to the ConcurrentBag to delete later
                        accountsToDelete.Add(svc.PostCreate("accounts", account));
                    });

                    //Calculate the duration to complete
                    var secondsToCreate = (DateTime.Now - startCreate).TotalSeconds;

                    Console.WriteLine($"Created {accountsToImport.Count} accounts in  {Math.Round(secondsToCreate)} seconds.");

                    Console.WriteLine($"Deleting {accountsToDelete.Count} accounts");
                    var startDelete = DateTime.Now;

                    //Delete the accounts in parallel
                    Parallel.ForEach(accountsToDelete, parallelOptions, (uri) =>
                    {
                        svc.Delete(uri);
                    });

                    //Calculate the duration to complete
                    var secondsToDelete = (DateTime.Now - startDelete).TotalSeconds;

                    Console.WriteLine($"Deleted {accountsToDelete.Count} accounts in {Math.Round(secondsToDelete)} seconds.");
                    Console.WriteLine("Sample completed. Press any key to exit.");
                    Console.ReadLine();
                }
            }
            catch (Exception)
            {
                throw;
            }
        }
    }
}
```

### <a name="see-also"></a>Vea también

[Usar la API web de Common Data Service](../overview.md)<br />
[Web API CDSWebApiService clase de muestra (C#)](cdswebapiservice.md)<br />
[Web API CDSWebApiService Ejemplo de operaciones asincrónicas (C#)](cdswebapiservice-async-parallel-operations.md)<br />
[Web API CDSWebApiService Ejemplo de operaciones básicas (C#)](cdswebapiservice-basic-operations.md)<br />
[Cree una entidad usando API web](../create-entity-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](../update-delete-entities-using-web-api.md)