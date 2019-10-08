---
title: Objeto App | Microsoft Docs
description: Información de referencia para el objeto App en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b0ab20ce5e0700337bb059644c458a2665d20f1e
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983587"
ms.PowerAppsDecimalTransform: true
---
# <a name="app-object-in-powerapps"></a>Objeto App en PowerApps

Proporciona información sobre la aplicación que se está ejecutando actualmente y el control sobre el comportamiento de la aplicación.

## <a name="description"></a>Descripción

Al igual que un control, el objeto de **aplicación** proporciona propiedades que identifican la pantalla que se muestra y que solicitan al usuario que guarde los cambios para que no se pierdan. Cada aplicación tiene un objeto de **aplicación** .

Puede escribir fórmulas para algunas propiedades del objeto de **aplicación** . En la parte superior del panel de **vista de árbol** , seleccione el objeto de la **aplicación** como lo haría con cualquier otro control o pantalla. Para ver y editar una de las propiedades del objeto, selecciónela en la lista desplegable situada a la izquierda de la barra de fórmulas.

> [!div class="mx-imgBorder"]
> objeto de aplicación ![The en el panel de vista de árbol @ no__t-1

## <a name="activescreen-property"></a>Propiedad ActiveScreen

La propiedad **ActiveScreen** identifica la pantalla que se muestra.

Esta propiedad devuelve un objeto de pantalla, que puede usar para hacer referencia a las propiedades de la pantalla o comparar con otra pantalla para determinar la pantalla que se muestra. También puede usar la expresión **app.ActiveScreen.Name** para recuperar el nombre de la pantalla que se muestra.

Utilice la función **[back](function-navigate.md)** o **[Navigate](function-navigate.md)** para cambiar la pantalla que se muestra.

## <a name="onstart-property"></a>OnStart (propiedad)

La propiedad **OnStart** se ejecuta cuando el usuario inicia la aplicación. A menudo, los responsables de aplicaciones usan esta propiedad para realizar estas tareas:

- Recupere y almacene en caché los datos en colecciones mediante la función **[Collect](function-clear-collect-clearcollect.md)** .
- Configure variables globales mediante la función **[set](function-set.md)** .
- Navegue a una pantalla inicial mediante la función **[Navigate](function-navigate.md)** .

Esta fórmula se evalúa antes de que aparezca la primera pantalla. No se carga ninguna pantalla, por lo que no se pueden establecer variables de contexto con la función **[UpdateContext](function-updatecontext.md)** . Sin embargo, puede pasar las variables de contexto con la función **Navigate** .

Después de cambiar la propiedad **OnStart** , pruébelo manteniendo el mouse sobre el objeto **App** en el panel **vista de árbol** , seleccionando los puntos suspensivos (...) que aparece y seleccionando **Ejecutar OnStart**. A diferencia de la primera vez que se carga la aplicación, ya se establecerán las colecciones y variables existentes. Para empezar con colecciones vacías, utilice la función **[ClearCollect](function-clear-collect-clearcollect.md)** en lugar de la función **Collect** .

> [!div class="mx-imgBorder"]
> ![App: menú contextual para ejecutar OnStart @ no__t-1

## <a name="confirmexit-properties"></a>Propiedades de ConfirmExit

Nadie desea perder los cambios no guardados. Use las propiedades **ConfirmExit** y **ConfirmExitMessage** para avisar al usuario antes de cerrar la aplicación.

> [!NOTE]
> **ConfirmExit** no funciona en aplicaciones que están incrustadas en, por ejemplo, Power BI y SharePoint.

> [!NOTE]
> En la actualidad, estas propiedades solo pueden hacer referencia a los controles de la primera pantalla si está habilitada la característica de vista previa de **carga retrasada** (que es de forma predeterminada para las nuevas aplicaciones). Si se realizan referencias, PowerApps Studio no muestra un error, pero la aplicación publicada resultante no se abre en PowerApps Mobile o en un explorador. Estamos trabajando activamente para levantar esta limitación. Mientras tanto, puede desactivar la **carga retrasada** en la configuración de la**aplicación**de @no__t de **archivos**-2  > **Configuración avanzada** (en **características de vista previa**).

### <a name="confirmexit"></a>ConfirmExit

**ConfirmExit** es una propiedad booleana que, cuando es *true*, abre un cuadro de diálogo de confirmación antes de que se cierre la aplicación. De forma predeterminada, esta propiedad es *false*y no aparece ningún cuadro de diálogo.

Utilice esta propiedad para mostrar un cuadro de diálogo de confirmación si el usuario ha realizado cambios pero no los ha guardado. Use una fórmula que pueda comprobar variables y propiedades de control (por ejemplo, la propiedad no **guardada** del control [**Editar formulario**](../controls/control-form-detail.md) ).

El cuadro de diálogo de confirmación aparece en cualquier situación en la que se puedan perder los datos, como en estos ejemplos:

- Ejecutar la función [**Exit**](function-exit.md) .
- Si la aplicación se ejecuta en un explorador:
  - Cierre del explorador o de la pestaña del explorador en el que se ejecuta la aplicación.
  - Seleccionar el botón atrás del explorador.
- Si la aplicación se ejecuta en PowerApps Mobile (iOS o Android):
  - Ejecutar la función [**Launch**](function-param.md) .<br>La función **Launch** no desencadena el cuadro de diálogo en un explorador porque se abre otra pestaña para que no se pierdan los datos.
  - Deslizar rápidamente para cambiar a otra aplicación en PowerApps Mobile.
  - Seleccionar el botón atrás en un dispositivo Android.

La apariencia exacta del cuadro de diálogo de confirmación puede variar en los dispositivos y las versiones de PowerApps.

El cuadro de diálogo de confirmación no aparece en PowerApps Studio.

### <a name="confirmexitmessage"></a>ConfirmExitMessage

De forma predeterminada, el cuadro de diálogo de confirmación muestra un mensaje genérico, como **"es posible que tenga cambios sin guardar".** en el idioma del usuario.

Use **ConfirmExitMessage** para proporcionar un mensaje personalizado en el cuadro de diálogo de confirmación. Si esta propiedad está *en blanco*, se usa el valor predeterminado. Los mensajes personalizados se truncan según sea necesario para que quepan en el cuadro de diálogo de confirmación, por lo que debe mantener el mensaje a unas cuantas líneas como máximo.

En un explorador, el cuadro de diálogo de confirmación podría aparecer con un mensaje genérico del explorador.

### <a name="example"></a>Ejemplo

1. Cree una aplicación que contenga dos controles de formulario, **AccountForm** y **ContactForm**.

1. Establezca la propiedad **ConfirmExit** del objeto de **aplicación** en esta expresión:

    ```powerapps-comma
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    Este cuadro de diálogo aparece si el usuario cambia los datos de cualquier forma y, a continuación, intenta cerrar la aplicación sin guardar los cambios.

    > [!div class="mx-imgBorder"]
    > ![Generic cuadro de diálogo de confirmación @ no__t-1

1. Establezca la propiedad **ConfirmExitMessage** del objeto de **aplicación** en esta fórmula:

    ```powerapps-comma
    If( AccountsForm.Unsaved;
        "Accounts form has unsaved changes.";
        "Contacts form has unsaved changes."
    )
    ```

    Este cuadro de diálogo aparece si el usuario cambia los datos en el formulario de la cuenta y, a continuación, intenta cerrar la aplicación sin guardar los cambios.

    > [!div class="mx-imgBorder"]
    > @no__t 0Form-cuadro de diálogo de confirmación específico @ no__t-1
