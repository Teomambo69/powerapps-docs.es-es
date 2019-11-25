---
title: 'Tutorial: Actualizar un complemento (Common Data Service) | Microsoft Docs'
description: 'Este tutorial es el tercero de una serie que le muestra cómo trabajar con los complementos. '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e28493c3790e49e616157124d49acae65c5bd9a0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749780"
---
# <a name="tutorial-update-a-plug-in"></a>Tutorial: Actualizar un complemento

Este tutorial es el tercero de una serie que le muestra cómo trabajar con los complementos. 

- [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)
- [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)
- Tutorial: Actualizar un complemento (este tutorial)

Para una explicación detallada de los conceptos relacionados y la información técnica, consulte:

- [Use complementos para ampliar los procesos de negocio](plug-ins.md)
- [Escribir un complemento](write-plug-in.md)
- [Registrar un complemento](register-plug-in.md)
- [Depuración de complementos](debug-plug-in.md)

## <a name="goal"></a>Objetivo

Este tutorial describirá acciones comunes adicionales que realizará con los complementos. En este tutorial usted realizará lo siguiente:

 - Actualizar un ensamblado de complementos
 - Crear y registrar un complemento sincrónico
 - Usar los datos de configuración en el complemento
 - Lanzar un error para mostrar al usuario
 - Configurar y usar una imagen previa de la entidad en el código
 - Anular el registro y ensamblado, un complemento, o un paso


El objetivo de este tutorial es:

- Crear un complemento sincrónico registrado en la fase anterior a la validación del mensaje de actualización de la entidad Cuenta. 
- El complemento evaluará un conjunto de valores de cadena establecidos en el uso de datos de configuración cuando se registra el complemento. 
- Si el nombre de la cuenta se cambia a uno de estos valores y el valor anterior no contenía el nuevo nombre, cancele la operación y envíe un mensaje de error de vuelta al usuario.


## <a name="prerequisites"></a>Requisitos previos

- Completar [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)
- [Tutorial: Se recomienda depurar un complemento](tutorial-debug-plug-in.md) pero no es obligatorio.

> [!NOTE]
> Puesto que muchos pasos básicos se describen en detalle en [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md), no se incluye el mismo nivel de detalle para los mismos pasos en este tutorial.

## <a name="create-a-new-plug-in-class"></a>Crear una nueva clase de complemento

1. En Visual Studio, agregue una nueva tipo al proyecto **BasicPlugin** llamado `ValidateAccountName.cs`
1. Agregue el siguiente código a la clase y vuelva a crear el ensamblado.


```csharp
using Microsoft.Xrm.Sdk;
using System;
using System.Collections.Generic;
using System.Linq;

namespace BasicPlugin
{
  public class ValidateAccountName : IPlugin
  {
    //Invalid names from unsecure configuration
    private List<string> invalidNames = new List<string>();

    // Constructor to capture the unsecure configuration
    public ValidateAccountName(string unsecure)
    {
      // Parse the configuration data and set invalidNames
      if (!string.IsNullOrWhiteSpace(unsecure))
        unsecure.Split(',').ToList().ForEach(s =>
        {
          invalidNames.Add(s.Trim());
        });
    }
    public void Execute(IServiceProvider serviceProvider)
    {

      // Obtain the tracing service
      ITracingService tracingService =
      (ITracingService)serviceProvider.GetService(typeof(ITracingService));
      try
      {

        // Obtain the execution context from the service provider.  
        IPluginExecutionContext context = (IPluginExecutionContext)
            serviceProvider.GetService(typeof(IPluginExecutionContext));

        // Verify all the requirements for the step registration
        if (context.InputParameters.Contains("Target") && //Is a message with Target
            context.InputParameters["Target"] is Entity && //Target is an entity
            ((Entity)context.InputParameters["Target"]).LogicalName.Equals("account") && //Target is an account
            ((Entity)context.InputParameters["Target"])["name"] != null && //account name is passed
            context.MessageName.Equals("Update") && //Message is Update
            context.PreEntityImages["a"] != null && //PreEntityImage with alias 'a' included with step
            context.PreEntityImages["a"]["name"] != null) //account name included with PreEntityImage with step
        {
          // Obtain the target entity from the input parameters.  
          var entity = (Entity)context.InputParameters["Target"];
          var newAccountName = (string)entity["name"];
          var oldAccountName = (string)context.PreEntityImages["a"]["name"];

          if (invalidNames.Count > 0)
          {
            tracingService.Trace("ValidateAccountName: Testing for {0} invalid names:", invalidNames.Count);

            if (invalidNames.Contains(newAccountName.ToLower().Trim()))
            {
              tracingService.Trace("ValidateAccountName: new name '{0}' found in invalid names.", newAccountName);

              // Test whether the old name contained the new name
              if (!oldAccountName.ToLower().Contains(newAccountName.ToLower().Trim()))
              {
                tracingService.Trace("ValidateAccountName: new name '{0}' not found in '{1}'.", newAccountName, oldAccountName);

                string message = string.Format("You can't change the name of this account from '{0}' to '{1}'.", oldAccountName, newAccountName);

                throw new InvalidPluginExecutionException(message);
              }

              tracingService.Trace("ValidateAccountName: new name '{0}' found in old name '{1}'.", newAccountName, oldAccountName);
            }

            tracingService.Trace("ValidateAccountName: new name '{0}' not found in invalidNames.", newAccountName);
          }
          else
          {
            tracingService.Trace("ValidateAccountName: No invalid names passed in configuration.");
          }
        }
        else
        {
          tracingService.Trace("ValidateAccountName: The step for this plug-in is not configured correctly.");
        }
      }
      catch (Exception ex)
      {
        tracingService.Trace("BasicPlugin: {0}", ex.ToString());
        throw;
      }
    }
  }
}
```

### <a name="about-the-code"></a>Acerca del código
- Esta clase incluye un constructor para capturar la configuración no segura que se establecerá al configurar un paso.
- Esta clase requiere una configuración del paso específico para funcionar correctamente:
    - Actualizar mensaje
    - En la entidad Cuenta
    - Con el nombre de cuenta incluido en los atributos
    - Con PreEntityImage utilizando alias específico ‘a’
    - Con PreEntityImage incluido el atributo Nombre.
- Si la configuración del paso no es correcta, el complemento escribirá únicamente en el seguimiento que no está configurado correctamente
- Si no se establecen nombres no válidos en la configuración, el complemento escribirá únicamente en el seguimiento que no se pasaron nombres no válidos a la configuración
- Si el nuevo nombre coincide con alguno de los nombres no válidos establecidos usando la configuración Y el nombre original no contiene el nuevo nombre, se producirá una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> con el mensaje al usuario de que esta operación no está permitida.

## <a name="update-the-plug-in-assembly-registration"></a>Actualizar el registro de ensamblados de complementos

El ensamblado existente de [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md) ya debe estar registrado. Para agregar el nuevo complemento **ValidateAccountName** sin registrar el ensamblado existente, deberá actualizarlo.

1. Seleccione el **(Ensamblado) Complemento básico** y seleccione **Actualizar**.

    ![Seleccione Actualizar](media/tutorial-update-plug-in-update.png)

1. En el diálogo **Actualizar un ensamblado: Complemento básico**, especifique la ubicación del ensamblado haciendo clic en los puntos suspensivos (**…**) y el ensamblado se cargará.

    ![Actualizar ensamblado: Diálogo complemento básico](media/tutorial-update-plug-in-update-assembly.png)

1. Compruebe que el ensamblado y ambos complementos están seleccionados y haga clic en **Actualizar complementos seleccionados**.

## <a name="configure-a-new-step"></a>Configurar un nuevo paso

Configure el complemento **ValidateAccountName** mediante estos valores:

|Configuración|Value|
|--|--|
|Mensaje|Update|
|Entidad principal|account|
|Atributos de filtro|nombre|
|Fase de canalización de eventos de ejecución|PreValidation|
|Modo de ejecución|Sincrónico|
|Configuración no segura|test,<br />foo,<br />bar|

![Registrar nuevo paso](media/tutorial-update-plug-in-register-new-step.png)

## <a name="add-an-image"></a>Agregar una imagen

1. Haga clic con el botón secundario en el paso que acaba de registrar y seleccione **Registrar nueva imagen**.

    ![Registrar nueva imagen](media/tutorial-update-plug-in-register-new-image.png)

1. En el diálogo **Registrar nueva imagen**, configure la imagen con estos valores:

    |Configuración|Value|
    |--|--|
    |Tipo de imagen|Imagen previa|
    |Nombre|account|
    |Alias de entidad|a|
    |Parámetros|nombre|

    ![Cuadro de diálogo de registro de nueva imagen](media/tutorial-update-plug-in-register-new-image-dialog.png)

1. Cuando se registra la imagen la verá en la herramienta de registro de complementos.

    ![La imagen registrada](media/tutorial-update-plug-in-image-added.png)

## <a name="test-the-plug-in"></a>Probar el complemento

1. Abra la aplicación e intente actualizar un nombre de cuenta existente a `test`, `foo`, o `bar`.
1. Al intentar guardar, deberá ver el siguiente mensaje:

    ![Mensaje de error](media/tutorial-update-plug-in-error-message.png)

1. Si actualiza una cuenta existente con un nombre que incluya `test`, `foo`, o `bar`, y después actualiza la cuenta a `test`, `foo`, o `bar` no debería ver el mensaje.

## <a name="unregister-assembly-plug-in-and-step"></a>Anule el registro del ensamblado, complemento, y paso

Use la herramienta de registro de complementos para **Anular el registro** (eliminar) cualquier ensamblado, complemento o paso. La eliminación de un ensamblado eliminarán todos los complementos y pasos para ese complemento.

![anular el registro de un ensamblado](media/tutorial-update-plug-in-unregister.png)
