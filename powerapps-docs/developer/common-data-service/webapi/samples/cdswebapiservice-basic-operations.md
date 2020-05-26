---
title: Web API CDSWebApiService Ejemplo de operaciones básicas (C#) (Common Data Service) | Microsoft Docs
description: Este ejemplo muestra cómo realizar operaciones básicas CRUD (Crear, Recuperar, Actualizar y Eliminar) y de asociación y disociación en instancias de entidades Common Data Service, usando la API web de Common Data Service con la clase CDSWebAPIService
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
ms.openlocfilehash: 8d1af1a70073b95a32e908e91b82f4afe397c0dc
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276716"
---
# <a name="web-api-cdswebapiservice-basic-operations-sample-c"></a>Web API CDSWebApiService Ejemplo de operaciones básicas (C#)

Este ejemplo muestra cómo realizar operaciones básicas CRUD (Crear, Recuperar, Actualizar y Eliminar) y de asociación y disociación en instancias de la entidad de Common Data Service mediante la API web de Common Data Service.  
  
> [!NOTE]
> Este ejemplo implementa las operaciones de Common Data Service y la salida de la consola detalladas en el [Ejemplo de operaciones básicas de la API web](../web-api-basic-operations-sample.md) y utiliza las construcciones comunes de C# que se describen en [Ejemplos de API web (C#)](../web-api-samples-csharp.md). 

## <a name="prerequisites"></a>Requisitos previos

Los siguientes elementos son necesarios para crear y ejecutar los ejemplos de CDSWebApiService C#:

- Microsoft Visual Studio 2019. 
- Acceso a Common Data Service con privilegios para realizar operaciones CRUD.
  
<a name="bkmk_runSample"></a>
  
## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Vaya a [Ejemplo CDSWebApiService de la API web](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/CDSWebApiService), clone o descargue el repositorio de ejemplos y extraiga su contenido en una carpeta local.

1. Abre el [CDSWebApiService.sln](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/CDSWebApiService.sln).

1. Selecciona el proyecto **BasicOperations** y abra la App.config. Este es un archivo común [App.config](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/App.config) utilizado por todos los ejemplos en esta solución. Una vez edite esto, puede ejecutar cualquiera de los ejemplos en esta solución.

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

1. Asegúrese de que el proyecto **BasicOperations** se establece como el proyecto de inicio. El nombre del proyecto debe estar en negrita para indicar que es el proyecto de inicio. Si el nombre no está en negrita, haga clic con el botón derecho en el explorador de soluciones y seleccione **Establecer como proyecto de inicio**.

1. Presione F5 para ejecutar el programa en modo de depuración.

## <a name="code-listing"></a>Lista de código

Esta muestra depende del ensamblado incluido en el proyecto CDSWebAPIService. Para obtener información sobre los métodos que proporciona esta clase, consulte: [Web API CDSWebApiService clase de muestra (C#)](cdswebapiservice.md).

El siguiente es el código del archivo Program.cs: 

```csharp
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Configuration;

namespace PowerApps.Samples
{
    internal class Program
    {
        //Get configuration data from App.config connectionStrings
        private static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

        private static readonly ServiceConfig config = new ServiceConfig(connectionString);

        private static void Main()
        {
            //List of Uris for records created in this sample
            List<Uri> entityUris = new List<Uri>();
            bool deleteCreatedRecords = true;

            try
            {
                using (CDSWebApiService svc = new CDSWebApiService(config))
                {
                    Console.WriteLine("--Starting Basic Operations--");

                    #region Section 1: Basic Create and Update operations

                    Console.WriteLine("--Section 1 started--");
                    //Create a contact
                    var contact1 = new JObject
                        {
                            { "firstname", "Rafel" },
                            { "lastname", "Shillo" }
                        };
                    Uri contact1Uri = svc.PostCreate("contacts", contact1);
                    Console.WriteLine($"Contact '{contact1["firstname"]} " +
                        $"{contact1["lastname"]}' created.");
                    entityUris.Add(contact1Uri); //To delete later
                    Console.WriteLine($"Contact URI: {contact1Uri}");

                    //Update a contact
                    JObject contact1Add = new JObject
                    {
                        { "annualincome", 80000 },
                        { "jobtitle", "Junior Developer" }
                    };
                    svc.Patch(contact1Uri, contact1Add);
                    Console.WriteLine(
                    $"Contact '{contact1["firstname"]} {contact1["lastname"]}' " +
                    $"updated with jobtitle and annual income");

                    //Retrieve a contact
                    var retrievedcontact1 = svc.Get(contact1Uri.ToString() +
                        "?$select=fullname,annualincome,jobtitle,description");
                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' retrieved: \n" +
                    $"\tAnnual income: {retrievedcontact1["annualincome"]}\n" +
                    $"\tJob title: {retrievedcontact1["jobtitle"]} \n" +
                    //description is initialized empty.
                    $"\tDescription: {retrievedcontact1["description"]}.");

                    //Modify specific properties and then update entity instance.
                    JObject contact1Update = new JObject
                        {
                            { "jobtitle", "Senior Developer" },
                            { "annualincome", 95000 },
                            { "description", "Assignment to-be-determined" }
                        };
                    svc.Patch(contact1Uri, contact1Update);

                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' updated:\n" +
                    $"\tJob title: {contact1Update["jobtitle"]}\n" +
                    $"\tAnnual income: {contact1Update["annualincome"]}\n" +
                    $"\tDescription: {contact1Update["description"]}\n");

                    // Change just one property
                    string telephone1 = "555-0105";
                    svc.Put(contact1Uri, "telephone1", telephone1);
                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' " +
                        $"phone number updated.");

                    //Now retrieve just the single property.
                    var telephone1Value = svc.Get($"{contact1Uri}/telephone1");
                    Console.WriteLine($"Contact's telephone # is: {telephone1Value["value"]}.");

                    #endregion Section 1: Basic Create and Update operations

                    #region Section 2: Create record associated to another

                    /// <summary>
                    /// Demonstrates creation of entity instance and simultaneous association to another,
                    ///  existing entity.
                    /// </summary>
                    ///

                    Console.WriteLine("\n--Section 2 started--");

                    //Create a new account and associate with existing contact in one operation.
                    var account1 = new JObject
                    {
                        { "name", "Contoso Ltd" },
                        { "telephone1", "555-5555" },
                        { "primarycontactid@odata.bind", contact1Uri }
                    };
                    var account1Uri = svc.PostCreate("accounts", account1);
                    entityUris.Add(account1Uri); //To delete later
                    Console.WriteLine($"Account '{account1["name"]}' created.");
                    Console.WriteLine($"Account URI: {account1Uri}");
                    //Retrieve account name and primary contact info
                    JObject retrievedAccount1 = svc.Get($"{account1Uri}?$select=name," +
                        $"&$expand=primarycontactid($select=fullname,jobtitle,annualincome)") as JObject;

                    Console.WriteLine($"Account '{retrievedAccount1["name"]}' has primary contact " +
                        $"'{retrievedAccount1["primarycontactid"]["fullname"]}':");
                    Console.WriteLine($"\tJob title: {retrievedAccount1["primarycontactid"]["jobtitle"]} \n" +
                        $"\tAnnual income: {retrievedAccount1["primarycontactid"]["annualincome"]}");

                    #endregion Section 2: Create record associated to another

                    #region Section 3: Create related entities

                    /// <summary>
                    /// Demonstrates creation of entity instance and related entities in a single operation.
                    /// </summary>
                    ///
                    Console.WriteLine("\n--Section 3 started--");
                    //Create the following entries in one operation: an account, its
                    // associated primary contact, and open tasks for that contact.  These
                    // entity types have the following relationships:
                    //    Accounts
                    //       |---[Primary] Contact (N-to-1)
                    //              |---Tasks (1-to-N)

                    //Build the Account object inside-out, starting with most nested type(s)
                    JArray tasks = new JArray();
                    JObject task1 = new JObject
                    {
                        { "subject", "Sign invoice" },
                        { "description", "Invoice #12321" },
                        { "scheduledend", DateTimeOffset.Parse("4/19/2019") }
                    };
                    tasks.Add(task1);
                    JObject task2 = new JObject
                    {
                        { "subject", "Setup new display" },
                        { "description", "Theme is - Spring is in the air" },
                        { "scheduledstart", DateTimeOffset.Parse("4/20/2019") }
                    };
                    tasks.Add(task2);
                    JObject task3 = new JObject
                    {
                        { "subject", "Conduct training" },
                        { "description", "Train team on making our new blended coffee" },
                        { "scheduledstart", DateTimeOffset.Parse("6/1/2019") }
                    };
                    tasks.Add(task3);

                    JObject contact2 = new JObject
                    {
                        { "firstname", "Susie" },
                        { "lastname", "Curtis" },
                        { "jobtitle", "Coffee Master" },
                        { "annualincome", 48000 },
                        //Add related tasks using corresponding navigation property
                        { "Contact_Tasks", tasks }
                    };

                    JObject account2 = new JObject
                    {
                        { "name", "Fourth Coffee" },
                        //Add related contacts using corresponding navigation property
                        { "primarycontactid", contact2 }
                    };

                    //Create the account and related records
                    Uri account2Uri = svc.PostCreate("accounts", account2);
                    Console.WriteLine($"Account '{account2["name"]}  created.");
                    entityUris.Add(account2Uri); //To delete later
                    Console.WriteLine($"Contact URI: {account2Uri}");

                    //Retrieve account, primary contact info, and assigned tasks for contact.
                    //CDS only supports querying-by-expansion one level deep, so first query
                    // account-primary contact.
                    var retrievedAccount2 = svc.Get($"{account2Uri}?$select=name," +
                        $"&$expand=primarycontactid($select=fullname,jobtitle,annualincome)");

                    Console.WriteLine($"Account '{retrievedAccount2["name"]}' " +
                        $"has primary contact '{retrievedAccount2["primarycontactid"]["fullname"]}':");

                    Console.WriteLine($"\tJob title: {retrievedAccount2["primarycontactid"]["jobtitle"]} \n" +
                        $"\tAnnual income: {retrievedAccount2["primarycontactid"]["annualincome"]}");

                    //Next retrieve same contact and its assigned tasks.
                    //Don't have a saved URI for contact 'Susie Curtis', so create one
                    // from base address and entity ID.
                    Uri contact2Uri = new Uri($"{svc.BaseAddress}contacts({retrievedAccount2["primarycontactid"]["contactid"]})");
                    //Retrieve the contact
                    var retrievedcontact2 = svc.Get($"{contact2Uri}?$select=fullname," +
                        $"&$expand=Contact_Tasks($select=subject,description,scheduledstart,scheduledend)");

                    Console.WriteLine($"Contact '{retrievedcontact2["fullname"]}' has the following assigned tasks:");
                    foreach (JToken tk in retrievedcontact2["Contact_Tasks"])
                    {
                        Console.WriteLine(
                            $"Subject: {tk["subject"]}, \n" +
                            $"\tDescription: {tk["description"]}\n" +
                            $"\tStart: {tk["scheduledstart"].Value<DateTime>().ToString("d")}\n" +
                            $"\tEnd: {tk["scheduledend"].Value<DateTime>().ToString("d")}\n");
                    }

                    #endregion Section 3: Create related entities

                    #region Section 4: Associate and Disassociate entities

                    /// <summary>
                    /// Demonstrates associating and disassociating of existing entity instances.
                    /// </summary>
                    Console.WriteLine("\n--Section 4 started--");
                    //Add 'Rafel Shillo' to the contact list of 'Fourth Coffee',
                    // a 1-to-N relationship.
                    JObject rel1 = new JObject
                    {
                        { "@odata.id", contact1Uri }
                    }; //relationship object for msg content
                    Uri navUri1 = new Uri($"{account2Uri}/contact_customer_accounts/$ref");
                    //Create relationship
                    svc.Post(navUri1.ToString(), rel1);
                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' " +
                        $"associated to account '{account2["name"]}'.");

                    //Retrieve and output all contacts for account 'Fourth Coffee'.
                    var retrievedContactList1 = svc.Get($"{account2Uri}/contact_customer_accounts?" +
                        $"$select=fullname,jobtitle");

                    Console.WriteLine($"Contact list for account '{retrievedAccount2["name"]}':");

                    foreach (JToken ct in retrievedContactList1["value"])
                    {
                        Console.WriteLine($"\tName: {ct["fullname"]}, Job title: {ct["jobtitle"]}");
                    }

                    //Dissociate the contact from the account.  For a collection-valued
                    // navigation property, must append URI of referenced entity.
                    Uri dis1Uri = new Uri($"{navUri1}?$id={contact1Uri}");
                    //Equivalently, could have dissociated from the other end of the
                    // relationship, using the single-valued navigation ref, located in
                    // the contact 'Peter Cambel'.  This dissociation URI has a simpler form:
                    // [Org URI]/api/data/v9.1/contacts([contactid#])/parentcustomerid_account/$ref

                    svc.Delete(dis1Uri);
                    //'Rafel Shillo' was removed from the the contact list of 'Fourth Coffee'

                    //Associate an opportunity to a competitor, an N-to-N relationship.
                    //First, create the required entity instances.
                    JObject comp1 = new JObject
                    {
                        { "name", "Adventure Works" },
                        {
                            "strengths",
                            "Strong promoter of private tours for multi-day outdoor adventures"
                        }
                    };
                    Uri comp1Uri = svc.PostCreate("competitors", comp1);
                    entityUris.Add(comp1Uri); //To delete later

                    JObject oppor1 = new JObject
                    {
                        ["name"] = "River rafting adventure",
                        ["description"] = "Sales team on a river-rafting offsite and team building"
                    };
                    Uri oppor1Uri = svc.PostCreate("opportunities", oppor1);
                    entityUris.Add(oppor1Uri); //To delete later

                    //Associate opportunity to competitor via opportunitycompetitors_association.
                    // navigation property.
                    JObject rel2 = new JObject
                    {
                        { "@odata.id", comp1Uri }
                    };
                    Uri navUri2 = new Uri($"{oppor1Uri}/opportunitycompetitors_association/$ref");

                    svc.Post(navUri2.ToString(), rel2);
                    Console.WriteLine($"Opportunity '{oppor1["name"]}' associated with competitor '{comp1["name"]}'.");

                    //Retrieve all opportunities for competitor 'Adventure Works'.
                    var retrievedOpporList1 = svc.Get($"{comp1Uri}?$select=name,&$expand=opportunitycompetitors_association($select=name,description)");

                    Console.WriteLine($"Competitor '{retrievedOpporList1["name"]}' has the following opportunities:");
                    foreach (JToken op in
                        retrievedOpporList1["opportunitycompetitors_association"])
                    {
                        Console.WriteLine($"\tName: {op["name"]}, \n" +
                            $"\tDescription: {op["description"]}");
                    }

                    //Dissociate opportunity from competitor.
                    svc.Delete(new Uri($"{navUri2}?$id={comp1Uri}"));
                    // 'River rafting adventure' opportunity disassociated with 'Adventure Works' competitor

                    #endregion Section 4: Associate and Disassociate entities

                    #region Section 5: Delete sample entities

                    Console.WriteLine("\n--Section 5 started--");
                    //Delete all the created sample entities.  Note that explicit deletion is not required
                    // for contact tasks because these are automatically cascade-deleted with owner.

                    if (!deleteCreatedRecords)
                    {
                        Console.Write("\nDo you want these entity records deleted? (y/n) [y]: ");
                        String answer = Console.ReadLine();
                        answer = answer.Trim();
                        if (!(answer.StartsWith("y") || answer.StartsWith("Y") || answer == string.Empty))
                        { entityUris.Clear(); }
                        else
                        {
                            Console.WriteLine("\nDeleting created records.");
                        }
                    }
                    else
                    {
                        Console.WriteLine("\nDeleting created records.");
                    }

                    foreach (Uri entityUrl in entityUris)
                    {
                        svc.Delete(entityUrl);
                    }

                    #endregion Section 5: Delete sample entities

                    Console.WriteLine("--Basic Operations Completed--");
                    Console.WriteLine("Press any key to close");
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
[Cree una entidad usando API web](../create-entity-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](../update-delete-entities-using-web-api.md)<br />
[Recuperar una entidad usando API web](../retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](../update-delete-entities-using-web-api.md)<br />
[Ejemplos de la API web](../web-api-samples.md)<br />
[Ejemplo de operaciones básicas de la API web](../web-api-basic-operations-sample.md)
[Ejemplo de consulta de datos de la API web (C#)](query-data-csharp.md)<br />
[Ejemplo de operaciones condicionales de la API web (C#)](conditional-operations-csharp.md)<br />
[Ejemplo de funciones y acciones de la API web (C#)](functions-actions-csharp.md)