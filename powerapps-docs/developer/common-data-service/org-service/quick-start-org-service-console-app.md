---
title: 'Tutorial: Ejemplo de servicio de organización (C#) (Common Data Service para aplicaciones) | Microsoft Docs'
description: En este tutorial se muestra cómo conectarse al servicio de la organización de Common Data Service para aplicaciones
ms.custom: ''
ms.date: 10/31/2018
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

Aquí es donde comienza a trabajar con los ensamblados de .NET SDK para trabajar con datos usando Common Data Service para aplicaciones.

En este tutorial creará una aplicación de consola mínima para conectarse al servicio de organización con la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. También pasará la información de conexión con una cadena de conexión al constructor.

Puede usar <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> el método que pasa una instancia del tipo <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest> y se mostrará <xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse>.<xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse.UserId> valor.

> [!NOTE]
> Este ejemplo de tutorial no incluye tratamiento de errores. Es un ejemplo mínimo de lo que necesita para conectarse y usar el servicio de organización.


## <a name="prerequisites"></a>Requisitos previos

 - Visual Studio (2017 recomendado)
 - Conexión a Internet
 - Una cuenta de usuario válida para la estancia de Common Data Service para aplicaciones
    - Su nombre de usuario
    - Su contraseña
 - Dirección URL a CDS del entorno de aplicaciones con el que quiere conectarse
 - Comprensión básica de lenguaje Visual C#

## <a name="create-visual-studio-project"></a>Crear proyecto en Visual Studio

1. Cree un nuevo proyecto de aplicación de consola (.NET Framework) mediante .NET Framework 4.6.2

    ![Inicie un proyecto de aplicación de consola](../media/quick-start-org-service-console-app-1.png)

    > [!NOTE]
    > Este captura de pantalla muestra el nombre `OrgServiceQuickStart`, pero puede elegir el nombre del proyecto y la solución que desee. 

1. En el **Explorador de soluciones** haga clic con el botón secundario en el proyecto que ha creado y seleccione **Administrar paquetes de NuGet...** en el menú contextual.

    ![Agregar paquete de NuGet](../media/quick-start-org-service-console-app-2.png)

1. Busque el paquete de NuGet `Microsoft.CrmSdk.XrmTooling.CoreAssembly` más reciente e instálelo.

    ![Instalar el paquete Microsoft.CrmSdk.XrmTooling.CoreAssembly NuGet](../media/quick-start-org-service-console-app-3.png)

> [!NOTE]
> Debe seleccionar **Acepto** en el diálogo **Aceptación de licencia**.

## <a name="edit-programcs"></a>Edite Program.cs

1. Agregue estas instrucciones a la parte superior de `Program.cs`

    ```csharp
    using Microsoft.Crm.Sdk.Messages;
    using Microsoft.Xrm.Tooling.Connector;
    ```

1. Reemplace el método `Main` con el siguiente:

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

1. Edite los siguientes valores para agregar información para el entorno:

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

Estos temas explicarán cómo trabajar con CDS de las entidades de aplicaciones:

[Operaciones de la entidad con el servicio de organización](entity-operations.md)<br />
[Crear entidades con el servicio de la organización](entity-operations-create.md)<br />
[Recuperar una entidad usando un servicio de organización](entity-operations-retrieve.md)<br />
[Actualizar y eliminar entidades con el servicio de la organización](entity-operations-update-delete.md)<br />
[Asociar y desasociar entidades con el servicio de la organización](entity-operations-associate-disassociate.md)