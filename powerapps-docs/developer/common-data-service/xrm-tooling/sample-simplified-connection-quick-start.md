---
title: 'Ejemplo: tutorial de conexión simplificada (Guía para desarrolladores de Common Data Service) | MicrosoftDocs'
description: 'Este ejemplo muestra cómo conectarse a los servicios web de Common Data Service usando el CrmServiceClient y realizar operaciones básicas de creación, actualización, recuperación y eliminación en una entidad. '
ms.custom: null
ms.date: 03/27/2019
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: samples
applies_to:
  - Common Data Service (online)
ms.assetid: a4fb3634-948e-4bac-a32f-f626c78d83a0
caps.latest.revision: 29
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - D365CE
  - PowerApps
---
# <a name="sample-simplified-connection-quick-start-using-common-data-service"></a>Ejemplo: tutorial de conexión simplificada con Common Data Service

Este ejemplo muestra cómo conectarse a los servicios web de Common Data Service usando el <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> y realizar operaciones básicas de creación, actualización, recuperación y eliminación en una entidad. Para obtener más información sobre la <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>, consulte [Usar constructores CrmServiceClient para conectarse a Common Data Service](use-crmserviceclient-constructors-connect.md).

## <a name="requirements"></a>Requisitos

El código de ejemplo completo se puede encontrar aquí [Ejemplo: Inicio rápido para Common Data Service](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/Xrm%20Tooling/QuickStartCS) 

Debe modificar el archivo `app.config` suministrado con la información de conexión para su instancia de Common Data Service antes de ejecutar el ejemplo. 

## <a name="demonstrates"></a>Demostraciones

Este ejemplo autentica al usuario con los servicios web de Common Data Service mediante el <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> y métodos. Después de obtener una referencia al servicio web de organización, el ejemplo realiza operaciones básicas de creación, actualización, recuperación y eliminación en una entidad de `account`. El ejemplo también controla excepciones comunes. No se utiliza ningún código de aplicación auxiliar para establecer una conexión con el servicio web de organización.  

Además, este ejemplo admite autenticación `OAuth` y el diagnóstico avanzado de conexión. Para obtener más información acerca de cómo usar diagnóstico, consulte [Configurar el seguimiento de útiles de XRM](configure-tracing-xrm-tooling.md).

## <a name="example"></a>Ejemplo

Lo siguiente muestra un `app.config file` de ejemplo. Para usar esto, borre los caracteres de comentario “<!- -” al principio de la línea \<add ... /> y “- ->” al final de la línea que corresponda al servidor y la organización. A continuación, modifique los valores de atributo de forma apropiada para su configuración.

```xml
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <connectionStrings>  
    <!-- Online using Office 365 -->  
    <!-- <add name="Server=CRM Online, organization=contoso, user=someone"  
         connectionString="Url=https://contoso.crm.dynamics.com; Username=someone@contoso.onmicrosoft.com; Password=password; authtype=Office365"/> -->  
  </connectionStrings>  
  <startup>  
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.2" />  
  </startup>  
<system.diagnostics>  
    <trace autoflush="true"/>  
    <sources>  
      <source name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" switchName="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="fileListener"/>  
        </listeners>  
      </source>  
      <source name="Microsoft.Xrm.Tooling.CrmConnectControl" switchName="Microsoft.Xrm.Tooling.CrmConnectControl" switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="fileListener"/>  
        </listeners>  
      </source>  
      <source name="CrmSvcUtil" switchName="CrmSvcUtil" switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="fileListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  

      <!--Possible values for switches: Off, Error, Warning, Information, Verbose  
                        Verbose:      includes Error, Warning, Info, Trace levels  
                        Information:  includes Error, Warning, Info levels  
                        Warning:      includes Error, Warning levels  
                        Error:        includes Error level-->  

      <add name="Microsoft.Xrm.Tooling.CrmConnectControl" value="Off"/>  
      <add name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" value="Error"/>  
      <add name="CrmSvcUtil" value="Off"/>  
    </switches>  

    <sharedListeners>  
      <add name="fileListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="CrmSvcUtil.log"/>  
    </sharedListeners>  

  </system.diagnostics>  
  <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <dependentAssembly>  
        <assemblyIdentity name="Microsoft.Xrm.Sdk" publicKeyToken="31bf3856ad364e35" culture="neutral" />  
        <bindingRedirect oldVersion="0.0.0.0-7.0.0.0" newVersion="8.0.0.0" />  
      </dependentAssembly>  
      <dependentAssembly>  
        <assemblyIdentity name="Microsoft.Xrm.Sdk.Deployment" publicKeyToken="31bf3856ad364e35" culture="neutral" />  
        <bindingRedirect oldVersion="0.0.0.0-7.0.0.0" newVersion="8.0.0.0" />  
      </dependentAssembly>  
      <dependentAssembly>  
        <assemblyIdentity name="Microsoft.ServiceBus" publicKeyToken="31bf3856ad364e35" culture="neutral" />  
        <bindingRedirect oldVersion="0.0.0.0-2.4.0.0" newVersion="2.4.0.0" />  
      </dependentAssembly>  
    </assemblyBinding>  
  </runtime>  
</configuration>  
```

## <a name="example"></a>Ejemplo

```csharp
using Microsoft.Crm.Sdk.Messages;
using Microsoft.Xrm.Sdk;
using Microsoft.Xrm.Sdk.Query;
using Microsoft.Xrm.Tooling.Connector;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace PowerApps.Samples
{
   public partial class SampleProgram
    {
        [STAThread] // Added to support UX
        static void Main(string[] args)
        {
            CrmServiceClient service = null;

            try
            {
                service = SampleHelpers.Connect("Connect");
                if (service.IsReady)
                {
                    #region Sample Code
                    ////////////////////////////////////
                    #region Set up
                    SetUpSample(service);
                    #endregion Set up
                    #region Demonstrate
                    // Obtain information about the logged on user from the web service.
                    Guid userid = ((WhoAmIResponse)service.Execute(new WhoAmIRequest())).UserId;
                    SystemUser systemUser = (SystemUser)service.Retrieve("systemuser", userid,
                        new ColumnSet(new string[] { "firstname", "lastname" }));
                    Console.WriteLine("Logged on user is {0} {1}.", systemUser.FirstName, systemUser.LastName);

                    // Retrieve the version of Microsoft Dynamics CRM.
                    RetrieveVersionRequest versionRequest = new RetrieveVersionRequest();
                    RetrieveVersionResponse versionResponse =
                        (RetrieveVersionResponse)service.Execute(versionRequest);
                    Console.WriteLine("Microsoft Dynamics CRM version {0}.", versionResponse.Version);

                    // Instantiate an account object. Note the use of option set enumerations defined in OptionSets.cs.
                    // Refer to the Entity Metadata topic in the SDK documentation to determine which attributes must
                    // be set for each entity.
                    Account account = new Account { Name = "Fourth Coffee" };
                    account.AccountCategoryCode = new OptionSetValue((int)AccountAccountCategoryCode.PreferredCustomer);
                    account.CustomerTypeCode = new OptionSetValue((int)AccountCustomerTypeCode.Investor);

                    // Create an account record named Fourth Coffee.
                    _accountId = service.Create(account);

                    Console.Write("{0} {1} created, ", account.LogicalName, account.Name);

                    // Retrieve the several attributes from the new account.
                    ColumnSet cols = new ColumnSet(
                        new String[] { "name", "address1_postalcode", "lastusedincampaign" });

                    Account retrievedAccount = (Account)service.Retrieve("account", _accountId, cols);
                    Console.Write("retrieved, ");

                    // Update the postal code attribute.
                    retrievedAccount.Address1_PostalCode = "98052";

                    // The address 2 postal code was set accidentally, so set it to null.
                    retrievedAccount.Address2_PostalCode = null;

                    // Shows use of a Money value.
                    retrievedAccount.Revenue = new Money(5000000);

                    // Shows use of a Boolean value.
                    retrievedAccount.CreditOnHold = false;

                    // Update the account record.
                    service.Update(retrievedAccount);
                    Console.WriteLine("and updated.");

                #region Clean up
                CleanUpSample(service);
                    #endregion Clean up
                }
                #endregion Demonstrate
                #endregion Sample Code
                else
                {
                    const string UNABLE_TO_LOGIN_ERROR = "Unable to Login to Dynamics CRM";
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

### <a name="see-also"></a>Vea también

[Usar cadenas de conexión en útiles de XRM para conectarse a Common Data Service](use-connection-strings-xrm-tooling-connect.md)<br />
[Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md)<br />
