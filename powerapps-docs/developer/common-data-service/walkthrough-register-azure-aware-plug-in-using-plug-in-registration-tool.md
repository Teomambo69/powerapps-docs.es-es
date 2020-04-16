---
title: 'Tutorial: registrar un complemento basado en Azure con la herramienta de registro de complementos (Common Data Service) | Microsoft Docs'
description: 'El tutorial muestra cómo registrar un paso del extremo de servicio con la herramienta de registro de complementos. '
keywords: ''
ms.date: 06/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: b5ef50fa-8085-f425-3968-804d012fc840
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 727b627a3069d8010828c829f5c133a0e868700f
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155164"
---
# <a name="tutorial-register-an-azure-aware-plug-in-using-the-plug-in-registration-tool"></a>Tutorial: Registrar un complemento basado en Azure con la herramienta de registro de complementos

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool -->

Este tutorial muestra cómo registrar un paso del extremo de servicio con la herramienta de registro de complementos. Una vez que esté configurado, Common Data Service (CDS) puede publicar el contexto de ejecución de la operación actual un extremo de soluciones de Azure. Para este tutorial, el paso se registra para publicar el contexto de ejecución del mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> para una entidad `Account` en el Azure Service Bus.  
  
Los siguientes requisitos previos se deben rellenar antes de iniciar este tutorial:  
  
- Acceda a la herramienta de registro de complementos. [!INCLUDE[proc-download-plugin-registration-tool](../../includes/proc-download-plugin-registration-tool.md)]
- La cuenta de usuario del sistema CDS debe tener el rol de administrador del sistema o personalizador del sistema. 
- Acceda a un espacio de nombres de servicios de plataforma de Azure que esté configurado para autorización SAS, en la que CDS publicará un mensaje.  
- Si planea usar cualquier otra entidad de mensajería de Azure distinta de una cola, por ejemplo, una retransmisión, debe haber una aplicación de escucha que escucha activamente el extremo de la solución especificado para que CDS se publique correctamente en el Azure Service Bus. Para obtener más información, consulte [Escribir un agente de escucha para una solución de Azure](write-listener-application-azure-solution.md).  
- Un extremo de servicio configurado con autorización SAS está disponible en la organización de destino. Más información: [Tutorial: Configurar Microsoft Azure (SAS) para la integración con CDS](walkthrough-configure-azure-sas-integration.md).  
  
## <a name="steps"></a>Pasos

Este tutorial contiene los pasos siguientes:  
  
1. [Conectarse a CDS](#BKMK_Connect)  
1. [Registrar un paso del extremo de servicio para un evento](#BKMK_Register)  
1. [Probar el registro del extremo](#BKMK_Test)
  
<a name="BKMK_Connect"></a>

## <a name="connect-to-cds"></a>Conectarse a CDS
 
Siga los pasos indicados abajo para conectarse con CDS mediante la herramienta de registro de complementos.  
  
1. Ejecute la herramienta de registro de complementos.  
1. Haga clic en **Crear nueva conexión**.  
1. En el cuadro de diálogo **Iniciar sesión**, seleccione **Office 365**.

    ![Formulario de inicio de sesión para una implementación en línea](media/crm-v6s-pr.png "Formulario de inicio de sesión para una implementación en línea")

1. Si selecciona **Mostrar la lista de organizaciones disponibles**, se le presentará una lista de las organizaciones a las que pertenece tras hacer clic en **Iniciar sesión**. Esto le permite elegir la organización en la que desea registrar el extremo de servicio. De lo contrario, se usa la organización predeterminada.  
1. Especifique la información indicada acerca de la cuenta de servidor y de inicio de sesión y, a continuación, haga clic en **Iniciar sesión**.  
  
<a name="BKMK_Register"></a>

## <a name="register-a-service-endpoint-step-for-an-event"></a>Registrar un paso del extremo de servicio para un evento

Siga los pasos indicados abajo para registrar un paso para un evento en el extremo de servicio.  
  
1. Seleccione un extremo de servicio existente en la pestaña de la organización de destino.  
1. Vaya al menú **Registrar** de y haga clic en **Registrar nuevo paso**.  
1. Complete el cuadro de diálogo **Registrar nuevo paso** para un evento de crear cuenta como se muestra en la siguiente ilustración.

    ![Crear paso de extremo de servicio](media/crm-v6s-pr-service-endpoint-step.png "Crear paso de extremo de servicio")
  
1. Haga clic en **Registrar nuevo paso**.  
  
CDS publicará ahora el mensaje actual que contiene el contexto de ejecución para el bus de servicio cuando se crea una cuenta. La publicación se realiza asincrónicamente y no se ejecuta inmediatamente.  
  
<a name="BKMK_Test"></a>

## <a name="test-the-endpoint-registration"></a>Probar el registro del extremo

Una vez registrado el extremo podrá probarlo. Debe haber un módulo de escucha ejecutándose o una cola disponible en el extremo de destino para que se produzca la publicación del bus de servicio desde el complemento.  
  
1. Abra una aplicación basada en lienzo o modelos de la misma organización donde se ha registrado el extremo del servicio.  
1. Creación de un nuevo registro Cuenta.
1. Escriba un nombre de cuenta, por ejemplo, 'Adventure Works Cycle', en el campo **Nombre de cuenta** y, a continuación, haga clic en **Guardar**.  
1. Espere unos 10 minutos hasta que se realice la publicación del Azure Service Bus.  
1. En la aplicación basada en modelos **Dynamics 365 - Personalizado**, seleccione **Configuración > Sistema > Trabajos del sistema**.  
1. Abra el trabajo del sistema con el mismo nombre que el extremo del servicio. Compruebe el estado para ver si la publicación se realiza correctamente, está en espera o ha generado un error.  
  
Ahora puede anular el registro del extremo, si así lo desea, seleccionándolo en la vista de árbol de la herramienta y haciendo clic en **Anular registro**.  
  
### <a name="see-also"></a>Vea también

[Integración de Azure para CDS](azure-integration.md)<br />
[Introducción a la integración de Microsoft Azure con CDS](azure-integration.md)
 