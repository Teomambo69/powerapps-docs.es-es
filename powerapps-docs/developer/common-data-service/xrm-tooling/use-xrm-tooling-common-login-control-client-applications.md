---
title: Usar el control de inicio de sesión común de los útiles de XRM en las aplicaciones cliente (Common Data Service)| Microsoft Docs
description: El SDK de Common Data Service proporciona una plantilla para Visual Studio que permite usar el control de inicio de sesión común en las aplicaciones cliente. El código para autenticación de Common Data Service, almacenamiento de credenciales y recuperación, y registro de diagnóstico está integrado en la plantilla, de modo que se pueden aprovechar rápidamente estas funciones en las aplicaciones cliente de Windows para Common Data Service
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: f77b2a20-0a30-4211-a1d9-74923d3eeae1
caps.latest.revision: 27
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 235132665462441616bfcdb9d05811584464fd6e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154868"
---
# <a name="use-the-xrm-tooling-common-login-control-in-your-client-applications"></a>Usar el control de inicio de sesión común de los útiles de XRM en las aplicaciones cliente

Existe una plantilla para Visual Studio que le permite usar el control de inicio de sesión común en las aplicaciones cliente. El código para autenticación de Common Data Service, almacenamiento de credenciales y recuperación, y registro de diagnóstico está integrado en la plantilla, de modo que se pueden aprovechar rápidamente estas funciones en las aplicaciones cliente de Windows para Common Data Service. El control común de inicio de sesión es una implementación de <xref:Microsoft.Xrm.Tooling.CrmConnectControl> y se asemeja a la siguiente imagen.  
  
![Control de inicio de sesión común de útiles de XRM](../media/crm-sdk-v6-commonlogincontrol.png "Control de inicio de sesión común de útiles de XRM")
  
<a name="Prereq"></a>

## <a name="prerequisites"></a>Requisitos previos
  
- .NET Framework 4.6.2 o superior.
- Visual Studio 2017 (recomendado)
- Conectado a Internet para poder descargar/restaurar los paquetes de Nuget necesarios mientras usa la plantilla del proyecto.  
  
<a name="NewProjectUsingTemplate"></a>
   
## <a name="create-a-wpf-application-using-the-common-login-control-template"></a>Crear una aplicación WPF con la plantilla de control de inicio de sesión común
  
Aquí se describe una forma rápida para crear una aplicación **Windows Presentation Foundation (WPF)** que aprovecha el control de inicio de sesión común y el código subyacente para la autenticación, el almacenamiento de credenciales y la reutilización, y el seguimiento predeterminado o registro.  
  
1.  Inicie Visual Studio y cree un nuevo proyecto.  
2.  En el cuadro de diálogo **Nuevo proyecto**:  
    1.  En la lista de plantillas instaladas, expanda **Visual C#**, y seleccione **Plantillas del SDK de Common Data Service**.  
    2.  Asegúrese de que **.NET Framework 4.6.2** está seleccionado.  
    3.  Seleccione **Aplicación WPF para Dynamics 365**.  
    4.  Especifique el nombre y la ubicación del proyecto y haga clic en **Aceptar**.  
  
     > [!div class="mx-imgBorder"]
     > ![Aplicación WPF para plantilla de Common Data Service](../media/crm-sdk-v6-xrm-tooling-newproject.png "Aplicación WPF para plantilla de Common Data Service")   

> [!NOTE]
> **Problema conocido de Visual Studio 2015**
> 
> Cuando se ejecuta el proyecto/solución en VS 2015 en modo de depuración, es posible que no pueda conectarse. Esto ocurre independientemente de si está usando un marco de destino de 4.6.2 o más alto. Esto puede producirse porque el proceso de hospedaje de Visual Studio se compila con .NET 4.5, lo que significa de forma predeterminada que no es compatible con TLS 1.2. Puede deshabilitar el proceso de hospedaje de Visual Studio como solución. 
>
> Haga clic con el botón derecho del mouse en el nombre del proyecto en Visual Studio y luego haga clic en **Propiedades**. En la pestaña **Depuración** puede desactivar la opción **Habilitar proceso de hospedaje de Visual Studio**. 
>
> Esto afecta solo a la experiencia de depuración en VS 2015. Esto no afecta a los archivos binarios o ejecutables que se crean. El mismo problema no se produce en Visual Studio 2017.
  
3. Para probar el proyecto:
  
    1. Guarde el proyecto y presione **F5**, o haga clic en **Depurar** > **Iniciar depuración** para comprobar si el proyecto se compila correctamente. Si la compilación es correcta, verá una MainWindow con el botón **Iniciar sesión en Dynamics 365**. Haga clic en el botón para mostrar el control de inicio de sesión común.  

    2.  Pruebe la autenticación mediante sus credenciales para conectarse a Common Data Service y, a continuación, haga clic en **Iniciar sesión**. Aparece un mensaje que muestra el estado de la conexión Common Data Service.  

  
 Para obtener un ejemplo en el que se usa una plantilla de control de inicio de sesión común para conectarse a Common Data Service y se realizan distintas operaciones, consulte [Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md).  
  
<a name="Add"></a>

## <a name="add-the-common-login-control-template-to-your-existing-wpf-application"></a>Agregar una plantilla de control de inicio de sesión común a la aplicación WPF existente

 Si ya tiene una aplicación cliente de WPF, puede agregar fácilmente la plantilla de control de inicio de sesión común a la aplicación para aprovechar la experiencia de inicio de sesión uniforme y el código subyacente para autenticación de Common Data Service, el almacenamiento de credenciales y la reutilización, y el seguimiento predeterminado o registro. En este caso, debe crear un control en la interfaz de usuario de la aplicación cliente existente para llamar al control de inicio de sesión común, crear una instancia del objeto de conexión de Common Data Service y después usar el objeto de conexión para realizar distintas operaciones en Common Data Service.  
  
1. Abra un proyecto de aplicación WPF existente en Visual Studio. Para este ejemplo, supongamos que el nombre del proyecto de aplicación WPF es `SampleWPFApp`.  
  
2. Agregue una plantilla de control de inicio de sesión común al proyecto.  
  
    1. En el panel **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto y después haga clic en **Agregar** > **Nuevo elemento**.  
  

    2.  En el cuadro de diálogo **Agregar nuevo artículo**, en la lista de plantillas instaladas, expanda **Visual C#** y seleccione **Plantillas SDK Common Data Service**. Haga clic en **Formulario de inicio de sesión de Common Data Service para aplicaciones WPF** y en **Aceptar**.  

          > [!div class="mx-imgBorder"]
          > ![Agregar la plantilla de control de inicio de sesión común](../media/crm-sdk-v6-xrmtooling-addtemplate01.png "Agregar la plantilla de control de inicio de sesión común")
  
3. El control de inicio de sesión `CrmLoginForm1.xaml` agregado recientemente se muestra en el área de diseñador de XAML. Si no se muestra, haga doble clic en el archivo `CrmLoginForm1.xaml` en el panel **Explorador de soluciones**.  
  
    > [!div class="mx-imgBorder"]
    > ![Compruebe que el control de inicio de sesión se representa correctamente](../media/crm-sdk-v6-xrmtooling-addtemplate03.png "Compruebe que el control de inicio de sesión se representa correctamente")
  

4.  Ahora debe llamar al control de inicio de sesión recién agregado desde la aplicación. Para ello, agregue un control **Botón** del archivo `MainWindow.xaml` y establezca el nombre y el contenido en **btnSignIn** y **Iniciar sesión en Common Data Service** respectivamente.  
 
     > [!div class="mx-imgBorder"]
     > ![Agregue un control para llamar al formulario de inicio de sesión](../media/crm-sdk-v6-xrmtooling-addtemplate02.png "Agregue un control para llamar al formulario de inicio de sesión")
  
5. Haga doble clic en el botón para agregar el código del evento de clic en el botón **btnSignIn** en el archivo `MainWindow.xaml.cs`.  
  
6.  Agregue el siguiente código de ejemplo en el evento de clic del botón **btnSignIn** para llamar al control `CrmLoginForm1` y cree una instancia del objeto de conexión de Common Data Service.  
 
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
  
7. Agregue la definición del evento `ctrl_ConnectionToCrmCompleted` debajo del evento de clic del botón:  
  
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
  
8. Así aparece el archivo `MainWindow.xaml.cs` después de agregar el código de los dos pasos anteriores:

    > [!div class="mx-imgBorder"]
    > ![Código de ejemplo ](../media/crm-sdk-v6-xrmtooling-addtemplate04.png "Código de ejemplo ")
  
9. Para probar el proyecto:  
  
    1.  Guarde el proyecto y presione F5, o haga clic en **Depurar** > **Iniciar depuración** para comprobar si el proyecto se compila correctamente. Si la compilación es correcta, verá una MainWindow con el botón nuevo **Conectarse a Common Data Service**. Haga clic en el botón para mostrar el control de inicio de sesión común.  
  
    2.  Pruebe la autenticación mediante sus credenciales para conectarse a Common Data Service y, a continuación, haga clic en **Iniciar sesión**. Si se realiza correctamente, aparecerá un mensaje que indica la versión y el nombre de la organización a la que está conectado. Haga clic en **Aceptar** para cerrar el mensaje.  
  
 
    > [!div class="mx-imgBorder"]
    > ![Resultados de las pruebas del proyecto](../media/crm-sdk-v6-xrmtooling-addtemplate05.png "Resultados de las pruebas del proyecto") 

  
    3. Si vuelve a hace clic en **Conectarse a Dynamics 365**, la aplicación le preguntará si desea elegir las credenciales guardadas en la última actividad de inicio de sesión o volver a especificar las nuevas credenciales.  
  
        > [!div class="mx-imgBorder"]
        > ![Credenciales almacenadas](../media/crm-sdk-v6-xrmtooling-addtemplate06.png "Credenciales almacenadas")
  
### <a name="see-also"></a>Vea también  

[Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md)<br />
[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)
