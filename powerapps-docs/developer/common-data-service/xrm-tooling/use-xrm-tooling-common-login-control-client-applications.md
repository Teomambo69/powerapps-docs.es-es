---
title: Usar el control de inicio de sesión común de útiles de XRM en las aplicaciones cliente (Common Data Service para aplicaciones)| Microsoft Docs
description: 'El SDK de CDS para aplicaciones proporciona una plantilla para Visual Studio que le permite usar el control de inicio de sesión común en las aplicaciones cliente. El código para autenticación de CDS para aplicaciones, almacenamiento de credenciales y recuperación, y registro de diagnóstico está integrado en la plantilla, de modo que se pueden aprovechar rápidamente estas funciones en las aplicaciones cliente de Windows para CDS para aplicaciones.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: f77b2a20-0a30-4211-a1d9-74923d3eeae1
caps.latest.revision: 27
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-xrm-tooling-common-login-control-in-your-client-applications"></a>Usar el control de inicio de sesión común de los útiles de XRM en las aplicaciones cliente

Existe una plantilla para Visual Studio que le permite usar el control de inicio de sesión común en las aplicaciones cliente. El código para autenticación de CDS para aplicaciones, almacenamiento de credenciales y recuperación, y registro de diagnóstico está integrado en la plantilla, de modo que se pueden aprovechar rápidamente estas funciones en las aplicaciones cliente de Windows para CDS para aplicaciones. El control común de inicio de sesión es una implementación de <xref:Microsoft.Xrm.Tooling.CrmConnectControl> y se asemeja a la siguiente imagen.  
  
 <!--TODO:
 ![XRM Tooling common login control](../media/crm-sdk-v6-commonlogincontrol.png "XRM Tooling common login control")   -->
  
<a name="Prereq"></a>

## <a name="prerequisites"></a>Requisitos previos
  
- .NET Framework 4.5.2
- Visual Studio 2012 o superior
- Administrador del paquete de Nuget para la versión de Visual Studio  
- Conectado a Internet para poder descargar/restaurar los paquetes de Nuget necesarios mientras usa la plantilla del proyecto.  
- Plantillas SDK de CRM para Visual Studio que contienen la plantilla del control de inicio de sesión común. Puede obtenerla descargando las [plantillas de SDK de Microsoft Dynamics CRM](http://go.microsoft.com/fwlink/p/?LinkId=400925) de la galería de Visual Studio y haciendo doble clic en el archivo de `CRMSDKTemplates.vsix` para instalar la plantilla en Visual Studio.  
  
<a name="NewProjectUsingTemplate"></a>
   
## <a name="create-a-wpf-application-using-the-common-login-control-template"></a>Crear una aplicación WPF con la plantilla de control de inicio de sesión común
  
 Aquí se describe una forma rápida para crear una aplicación Windows Presentation Foundation (WPF) que aprovecha el control de inicio de sesión común y el código subyacente para la autenticación, el almacenamiento de credenciales y la reutilización, y el seguimiento predeterminado o registro.  
  
1.  Inicie Visual Studio y cree un nuevo proyecto.  
2.  En el cuadro de diálogo **Nuevo proyecto**:  
    1.  En la lista de plantillas instaladas, expanda **Visual c#**, y seleccione **Plantillas de SDK de CDS para aplicaciones**.  
    2.  Asegúrese de que **.NET Framework 4.6.2** está seleccionado.  
    3.  Seleccione **Aplicación WPF para Dynamics 365**.  
    4.  Especifique el nombre y la ubicación del proyecto, y haga clic en **Aceptar**.  
  
 <!-- TODO:
 ![WPF Application for CDS for Apps template](../media/crm-sdk-v6-xrmtooling-newproject.png "WPF Application for CDS for Apps template")   -->
  
3.  Para probar el proyecto:  
  
    1.  Guarde el proyecto y presione F5, o haga clic en **Depurar** > **Iniciar depuración** para comprobar si el proyecto se compila correctamente. Si la compilación es correcta, verá una MainWindow con el botón **Iniciar sesión en Dynamics 365**. Haga clic en el botón para mostrar el control de inicio de sesión común.  
  
    2.  Pruebe la autenticación mediante sus credenciales para conectarse a CDS para aplicaciones y, a continuación, haga clic en **Iniciar sesión**. Aparece un mensaje que muestra el estado de la conexión de CDS para aplicaciones.  
  
 Para obtener un ejemplo en el que se usa una plantilla de control de inicio de sesión común para conectarse a CDS para aplicaciones y se realizan distintas operaciones, consulte [Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md).  
  
<a name="Add"></a>

## <a name="add-the-common-login-control-template-to-your-existing-wpf-application"></a>Agregar una plantilla de control de inicio de sesión común a la aplicación WPF existente

 Si ya tiene una aplicación cliente de WPF, puede agregar fácilmente la plantilla de control de inicio de sesión común a la aplicación para aprovechar la experiencia de inicio de sesión uniforme y el código subyacente para autenticación de CDS para aplicaciones, el almacenamiento de credenciales y la reutilización, y el seguimiento predeterminado o registro. En este caso, debe crear un control en la interfaz de usuario de la aplicación cliente existente para llamar al control de inicio de sesión común, crear una instancia del objeto de conexión de CDS para aplicaciones y después usar el objeto de conexión para realizar distintas operaciones en CDS para aplicaciones.  
  
1.  Abra un proyecto de aplicación WPF existente en Visual Studio. Para este ejemplo, supongamos que el nombre del proyecto de aplicación WPF es SampleWPFApp.  
  
2.  Agregue una plantilla de control de inicio de sesión común al proyecto.  
  
    1.  En el panel **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto y después haga clic en **Agregar** > **Nuevo elemento**.  
  
    2.  En el cuadro de diálogo **Agregar nuevo artículo**, en la lista de plantillas instaladas, expanda **Visual C#** y seleccione **Plantillas SDK de CDS para aplicaciones**. Haga clic en **Formulario de inicio de sesión de CDS para aplicaciones WPF** y en **Aceptar**.  
  
 <!--TODO:
 ![Add the common login control template](../media/crm-sdk-v6-xrmtooling-addtemplate01.png "Add the common login control template")   -->
  
3.  El control de inicio de sesión `CrmLoginForm1.xaml` agregado recientemente se muestra en el área de diseñador de XAML. Si no se muestra, haga doble clic en el archivo `CrmLoginForm1.xaml` en el panel **Explorador de soluciones**.  
  
 <!--TODO: 
![Verify that the login control renders properly](../media/crm-sdk-v6-xrmtooling-addtemplate03.png "Verify that the login control renders properly")   -->
  
4.  Ahora debe llamar al control de inicio de sesión recién agregado desde la aplicación. Para ello, agregue un control **Botón** del archivo `MainWindow.xaml` y establezca el nombre y el contenido en **btnSignIn** y **Iniciar sesión en CDS para aplicaciones** respectivamente.  
  
 <!--TODO:
 ![Add a control to call the login form](../media/crm-sdk-v6-xrmtooling-addtemplate02.png "Add a control to call the login form")   -->
  
5.  Haga doble clic en el botón para agregar el código del evento de clic en el botón **btnSignIn** en el archivo `MainWindow.xaml.cs`.  
  
6.  Agregue el siguiente código de ejemplo en el evento de clic del botón **btnSignIn** para llamar al control `CrmLoginForm1` y cree una instancia del objeto de conexión de CDS para aplicaciones.  
  
    ```csharp
    // Establish the Login control.  
    CRMLoginForm1 ctrl = new CRMLoginForm1();  
  
    // Wire event to login response.   
    ctrl.ConnectionToCrmCompleted += ctrl_ConnectionToCrmCompleted;  
  
    // Show the login control.   
    ctrl.ShowDialog();  
  
    // Handle the returned CRM connection object.  
    // On successful connection, display the CRM version and connected org name   
    if (ctrl.CrmConnectionMgr != null && ctrl.CrmConnectionMgr.CrmSvc != null && ctrl.CrmConnectionMgr.CrmSvc.IsReady)  
    {  
        MessageBox.Show("Connected to CRM! Version: " + ctrl.CrmConnectionMgr.CrmSvc.ConnectedOrgVersion.ToString() +   
        " Org: " + ctrl.CrmConnectionMgr.CrmSvc.ConnectedOrgUniqueName, "Connection Status");  
  
        // Perform your actions here  
    }  
    else  
    {  
        MessageBox.Show("Cannot connect; try again!", "Connection Status");  
    }  
    ```  
  
7.  Agregue la definición del evento `ctrl_ConnectionToCrmCompleted` debajo del evento de clic del botón:  
  
    ```csharp  
    private void ctrl_ConnectionToCrmCompleted(object sender, EventArgs e)  
    {  
        if (sender is CRMLoginForm1)  
        {  
            this.Dispatcher.Invoke(() =>  
            {  
                ((CRMLoginForm1)sender).Close();  
            });  
        }  
    }  
    ```  
  
8.  Así aparece el archivo `MainWindow.xaml.cs` después de agregar el código de los dos pasos anteriores:  
  
 <!--TODO: ![Sample code](../media/crm-sdk-v6-xrmtooling-addtemplate04.png "Sample code")   -->
  
9. Para probar el proyecto:  
  
    1.  Guarde el proyecto y presione F5, o haga clic en **Depurar** > **Iniciar depuración** para comprobar si el proyecto se compila correctamente. Si la compilación es correcta, verá una MainWindow con el botón nuevo **Conectarse a CDS para aplicaciones**. Haga clic en el botón para mostrar el control de inicio de sesión común.  
  
    2.  Pruebe la autenticación mediante sus credenciales para conectarse a CDS para aplicaciones y, a continuación, haga clic en **Iniciar sesión**. Si se realiza correctamente, aparecerá un mensaje que indica la versión y el nombre de la organización a la que está conectado. Haga clic en **Aceptar** para cerrar el mensaje.  
  
 <!--TODO:
 ![Project test results](../media/crm-sdk-v6-xrmtooling-addtemplate05.png "Project test results")   -->
  
    3.  Si vuelve a hace clic en **Conectarse a Dynamics 365**, la aplicación le preguntará si desea elegir las credenciales guardadas en la última actividad de inicio de sesión o volver a especificar las nuevas credenciales.  
  
 <!--TODO:
 ![Stored credentials](../media/crm-sdk-v6-xrmtooling-addtemplate06.png "Stored credentials")   -->
  
### <a name="see-also"></a>Vea también  

[Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md)<br />
[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)