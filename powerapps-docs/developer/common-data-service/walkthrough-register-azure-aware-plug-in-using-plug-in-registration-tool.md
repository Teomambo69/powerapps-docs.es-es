---
title: 'Tutorial: Registrar un complemento con Azure utilizando la herramienta de registro de complementos (Common Data Service para aplicaciones) | Microsoft Docs'
description: 'El tutorial muestra cómo registrar un paso del extremo de servicio con la herramienta de registro de complementos. '
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: b5ef50fa-8085-f425-3968-804d012fc840
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-register-an-azure-aware-plug-in-using-the-plug-in-registration-tool"></a>Tutorial: Registrar un complemento basado en Azure con la herramienta de registro de complementos

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool -->

Este tutorial muestra cómo registrar un paso del extremo de servicio con la herramienta de registro de complementos. Una vez configurado, Dynamics 365 (online) Common Data Service para aplicaciones puede publicar el contexto de ejecución de la operación actual a un extremo de la solución de Azure. Para este tutorial, el paso se registra para publicar el contexto de ejecución del mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> para una entidad `Account` en el Azure Service Bus.  
  
 Los siguientes requisitos previos se deben rellenar antes de iniciar este tutorial:  
  
-   Acceda a la herramienta de registro de complementos. [!INCLUDE[proc-download-plugin-registration-tool](../../includes/proc-download-plugin-registration-tool.md)]
  
-   La cuenta de usuario del sistema Dynamics 365 debe tener el rol de administrador del sistema o personalizador del sistema. 
  
-   Acceda a un espacio de nombres de servicios de plataforma de Azure que esté configurado para autorización SAS, en la que Dynamics 365 publicará un mensaje.  
  
  
-   Si planea usar cualquier otra entidad de mensajería de Azure distinta de una cola, por ejemplo, una retransmisión, debe haber una aplicación de escucha que escucha activamente el extremo de la solución especificado para que Dynamics 365 se publique correctamente en el Azure Service Bus. Para obtener más información, consulte [Escribir un agente de escucha para una solución de Azure](write-listener-application-azure-solution.md).  
  
-   Un extremo de servicio configurado con autorización SAS está disponible en la organización de destino. Más información: [Tutorial: configuración de Microsoft Azure (SAS) para la integración con Dynamics 365](walkthrough-configure-azure-sas-integration.md)  
  
## <a name="steps"></a>Pasos  
 Este tutorial contiene los pasos siguientes:  
  
1.  [Conectarse a Dynamics 365 Server](#BKMK_Connect)  
  
2.  [Registrar un paso del extremo de servicio para un evento](#BKMK_Register)  
  
3.  [Probar el registro del extremo](#BKMK_Test)  
  
<a name="BKMK_Connect"></a>   
## <a name="connect-to-the-dynamics-365-server"></a>Conectarse a Dynamics 365 Server  
 Siga los pasos indicados abajo para conectarse con Dynamics 365 Server mediante la herramienta de registro de complementos.  
  
1.  Ejecute la herramienta de registro de complementos.  
  
2.  Haga clic en **Crear nueva conexión**.  
  
3.  En el diálogo **Iniciar sesión**, seleccione el botón de opción de tipo de implementación correspondiente a Dynamics 365 Server en el que quiera registrar un extremo de servicio. El botón de opción **Local** incluye una implementación de IFD y el botón **Office 365** es para el proveedor Microsoft Online Services de Dynamics 365 (online).  
  
    |||  
    |-|-|  
    |![Formulario de inicio de sesión para una implementación en línea](media/crm-v6s-pr.png "Formulario de inicio de sesión para una implementación en línea")<br />Formulario de inicio de sesión para una implementación en línea|![Ventana de inicio de sesión para una implementación local](media/crm-v6s-pr-login-onprem.png "Ventana de inicio de sesión para una implementación local")<br />Formulario de inicio de sesión para una implementación local|  
  
4.  Si selecciona **Mostrar la lista de organizaciones disponibles**, se le presentará una lista de las organizaciones a las que pertenece tras hacer clic en **Iniciar sesión**. Esto le permite elegir la organización en la que desea registrar el extremo de servicio. De lo contrario, se usa la organización predeterminada.  
  
5.  Especifique la información indicada acerca de la cuenta de servidor y de inicio de sesión y, a continuación, haga clic en **Iniciar sesión**.  
  
<a name="BKMK_Register"></a>   
## <a name="register-a-service-endpoint-step-for-an-event"></a>Registrar un paso del extremo de servicio para un evento  
 Siga los pasos indicados abajo para registrar un paso para un evento en el extremo de servicio.  
  
1.  Seleccione un extremo de servicio existente en la pestaña de la organización de destino.  
  
2.  Vaya al menú **Registrar** de y haga clic en **Registrar nuevo paso**.  
  
3.  Complete el cuadro de diálogo **Registrar nuevo paso** para un evento de crear cuenta como se muestra en la siguiente ilustración.

 ![Crear paso de extremo de servicio](media/crm-v6s-pr-service-endpoint-step.png "Crear paso de extremo de servicio")
  
4.  Haga clic en **Registrar nuevo paso**.  
  
 Dynamics 365 publicará ahora el mensaje actual que contiene el contexto de ejecución para el bus de servicio cuando se crea una cuenta. La publicación se realiza asincrónicamente y no se ejecuta inmediatamente.  
  
<a name="BKMK_Test"></a>   
## <a name="test-the-endpoint-registration"></a>Probar el registro del extremo  
 Una vez registrado el extremo podrá probarlo. Debe haber un módulo de escucha ejecutándose o una cola disponible en el extremo de destino para que se produzca la publicación del bus de servicio desde el complemento.  
  
1.  Abra la aplicación web Dynamics 365 de la misma organización donde se ha registrado el extremo del servicio.  
  
2.  Haga clic en el botón **Crear** ![Botón Crear](media/crm-v6s-wa-create-icon.PNG "Botón Crear") y haga clic en **Cuenta**.  
  
3.  Escriba un nombre de cuenta, por ejemplo `Adventure Works Cycle`, en el campo **Nombre de cuenta** y, a continuación, haga clic en **Guardar**.  
  
4.  Espere unos 10 minutos hasta que se realice la publicación del Azure Service Bus.  
  
5.  Haga clic en **Configuración > Configuración del sistema**.  
  
6.  Abra el trabajo del sistema con el mismo nombre que el extremo del servicio. Compruebe el estado para ver si la publicación se realiza correctamente, está en espera o ha generado un error.  
  
 Ahora puede anular el registro del extremo, si así lo desea, seleccionándolo en la vista de árbol de la herramienta y haciendo clic en **Anular registro**.  
  
### <a name="see-also"></a>Vea también  
 [Integration de Azure para Dynamics 365](azure-integration.md)
 
 [Introducción a la integración de Microsoft Azure con Dynamics 365](azure-integration.md).
