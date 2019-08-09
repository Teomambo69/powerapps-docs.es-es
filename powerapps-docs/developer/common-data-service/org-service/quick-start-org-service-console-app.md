---
title: 'Inicio rápido: Ejemplo de servicio de organización (C#) (Common Data Service) | Microsoft Docs'
description: En este tutorial se muestra cómo conectarse al servicio de la organización de Common Data Service
ms.custom: ''
ms.date: 04/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="quick-start-organization-service-sample-c"></a>Tutorial: ejemplo de servicio de organización (C#)

Aquí es donde comienza a trabajar con los ensamblados de .NET SDK para trabajar con datos usando Common Data Service.

En este tutorial creará una aplicación de consola mínima para conectarse al servicio de organización con la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. También pasará la información de conexión con una cadena de conexión al constructor.

Puede usar <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> el método que pasa una instancia del tipo <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest> y se mostrará <xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse>.<xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse.UserId> valor.

> [!NOTE]
> Este ejemplo de tutorial no incluye tratamiento de errores. Es un ejemplo mínimo de lo que necesita para conectarse y usar el servicio de organización.


## <a name="prerequisites"></a>Requisitos previos

 - Visual Studio (2017 recomendada)
 - Conexión a Internet
 - Cuenta de usuario válida para una instancia de Common Data Service
    - Su nombre de usuario
    - Su contraseña
 - Dirección URL al entorno de Common Data Service con el que quiere conectarse
 - Comprensión básica de lenguaje Visual C#

## <a name="create-visual-studio-project"></a>Crear proyecto de Visual Studio

1. Cree un nuevo proyecto de aplicación de consola (.NET Framework) mediante .NET Framework 4.6.2

    ![Inicie un proyecto de aplicación de consola](../media/quick-start-org-service-console-app-1.png)

    > [!NOTE]
    > Este captura de pantalla muestra el nombre `OrgServiceQuickStart`, pero puede elegir el nombre del proyecto y la solución que desee. 

1. En el **Explorador de soluciones** haga clic con el botón secundario en el proyecto que ha creado y seleccione **Administrar paquetes de NuGet...** en el menú contextual.

    ![Agregar paquete de NuGet](../media/quick-start-org-service-console-app-2.png)

1. Busque la versión del paquete `Microsoft.CrmSdk.XrmTooling.CoreAssembly` NuGet más reciente e instálelo.

    ![Instalar el paquete Microsoft.CrmSdk.XrmTooling.CoreAssembly NuGet](../media/quick-start-org-service-console-app-3.png)

> [!NOTE]
> Debe seleccionar **Acepto** en el diálogo **Aceptación de licencia**.

## <a name="edit-programcs"></a>Edite Program.cs

1. Agregue estas instrucciones a la parte superior de `Program.cs`

    ```csharp
    using Microsoft.Crm.Sdk.Messages;
    using Microsoft.Xrm.Tooling.Connector;
    ```

1. Reemplace el método `Main` con el siguiente. Los valores admitidos para *AuthType* se enumeran en [Parámetros de cadena de conexión](/dynamics365/customer-engagement/developer/xrm-tooling/use-connection-strings-xrm-tooling-connect#connection-string-parameters).

    ```csharp
    static void Main(string[] args)
    {            
        // e.g. https://yourorg.crm.dynamics.com
        string url = "<your environment url>";
        // e.g. you@yourorg.onmicrosoft.com
        string userName = "<your user name>";
        // e.g. y0urp455w0rd 
        string password = "<your password>";

        string conn = $@"
        Url = {url};
        AuthType = Office365;
        UserName = {userName};
        Password = {password};
        RequireNewInstance = True";

        using (var svc = new CrmServiceClient(conn))
        {

            WhoAmIRequest request = new WhoAmIRequest();

            WhoAmIResponse response = (WhoAmIResponse)svc.Execute(request);

            Console.WriteLine("Your UserId is {0}", response.UserId);

            Console.WriteLine("Press any key to exit.");
            Console.ReadLine();
        }
    }
    ```

1. Edite los siguientes valores para agregar información para el entorno. Puede encontrar la dirección URL del entorno en la aplicación web en **Configuración > Personalización > Recursos para desarrolladores**.

    ```csharp
    // e.g. https://yourorg.crm.dynamics.com
    string url = "<your environment url>";
    // e.g. you@yourorg.onmicrosoft.com
    string userName = "<your user name>";
    // e.g. y0urp455w0rd
    string password = "<your password>";
    ```

## <a name="run-the-program"></a>Ejecute el programa.

1. Pulse F5 para ejecutar el programa. Los resultados deberán tener un aspecto similar al siguiente:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

### <a name="congratulations"></a>Enhorabuena.

Se ha conectado con éxito al servicio de organización.


## <a name="next-steps"></a>Pasos siguientes

Estos temas explicarán cómo trabajar con entidades de Common Data Service:

[Operaciones de la entidad con el servicio de organización](entity-operations.md)<br />
[Crear entidades con el servicio de la organización](entity-operations-create.md)<br />
[Recuperar una entidad usando un servicio de organización](entity-operations-retrieve.md)<br />
[Actualizar y eliminar entidades con el servicio de la organización](entity-operations-update-delete.md)<br />
[Asociar y desasociar entidades con el servicio de la organización](entity-operations-associate-disassociate.md)