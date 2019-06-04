---
title: Objeto de aplicación | Microsoft Docs
description: Información de referencia, incluida la sintaxis y ejemplos para el objeto de aplicación en PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 232accd1050fb84816e86ea95069b8c8778f6586
ms.sourcegitcommit: 562c7ed5fbb116be1cbb0f45e3f6e75e3e4cf011
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451619"
ms.PowerAppsDecimalTransform: true
---
# <a name="app-object-in-powerapps"></a>Objeto de aplicación en PowerApps

Proporciona información acerca de la aplicación y el control sobre el comportamiento de la aplicación que se está ejecutando.

## <a name="description"></a>Descripción

Al igual que un control, el **aplicación** objeto proporciona propiedades que identifican qué pantalla se muestra y que solicitan al usuario guardar los cambios para que no estén perdidos. Cada aplicación tiene un **aplicación** objeto.

Puede escribir fórmulas para algunas propiedades de la **aplicación** objeto. En la parte superior de la **vista de árbol** panel, seleccione el **aplicación** como se haría cualquier otro control o una pantalla de objeto. Ver y editar una de las propiedades del objeto, selecciónelo en la lista desplegable situada a la izquierda de la barra de fórmulas.

> [!div class="mx-imgBorder"]
> ![El objeto de aplicación en el panel de vista de árbol](media/object-app/appobject.png)

## <a name="activescreen-property"></a>Propiedad ActiveScreen

El **ActiveScreen** propiedad identifica la pantalla que muestra.

Esta propiedad devuelve un objeto de la pantalla, que puede usar para hacer referencia a propiedades de la pantalla o comparar a otra pantalla para determinar qué pantalla se muestra. También puede usar la expresión **App.ActiveScreen.Name** para recuperar el nombre de la pantalla que muestra.

Use la **[Atrás](function-navigate.md)** o **[Navigate](function-navigate.md)** función para cambiar la pantalla que muestra.

## <a name="onstart-property"></a>Propiedad OnStart

El **OnStart** propiedad que se ejecuta cuando el usuario inicia la aplicación. A menudo, los creadores de aplicaciones usar esta propiedad para realizar estas tareas:

- Recuperar y almacenar en caché datos en colecciones mediante el uso de la **[recopilar](function-clear-collect-clearcollect.md)** función.
- Configurar las variables globales mediante el **[establecer](function-set.md)** función.
- Navegue a una pantalla inicial mediante el uso de la **[Navigate](function-navigate.md)** función.

Esta fórmula se evalúa antes de que aparezca la primera pantalla. No hay pantalla se carga, por lo que no puede establecer las variables de contexto con el **[UpdateContext](function-updatecontext.md)** función. Sin embargo, puede pasar variables de contexto con el **Navigate** función.

Después de cambiar el **OnStart** propiedad, probarla mediante el mouse sobre el **aplicación** objeto en el **vista de árbol** panel, seleccione los puntos suspensivos (...) que aparece y, a continuación, seleccionar **Ejecutar OnStart**. A diferencia de cuando se cargue la aplicación por primera vez, se establecerán ya las variables y las colecciones existentes. Colecciones vacías para empezar, use el **[ClearCollect](function-clear-collect-clearcollect.md)** función en lugar de la **recopilar** función.

> [!div class="mx-imgBorder"]
> ![Menú contextual de elemento de la aplicación para ejecutar OnStart](media/object-app/appobject-runonstart.png)

## <a name="confirmexit-properties"></a>Propiedades de ConfirmExit

Nadie quiere perder los cambios no guardados. Use la **ConfirmExit** y **ConfirmExitMessage** propiedades para advertir al usuario antes de que cierre la aplicación.

> [!NOTE]
> **ConfirmExit** no funciona en las aplicaciones que se incrustan en, por ejemplo, Power BI y SharePoint.

> [!NOTE]
> En este momento, estas propiedades pueden hacer referencia a controles en solo la primera pantalla si el **demorada carga** característica de vista previa está habilitada (que es para las nuevas aplicaciones de forma predeterminada). Si se realizan las referencias, PowerApps Studio no muestra un error, pero la aplicación publicada resultante no se abre en PowerApps Mobile o en un explorador. Estamos trabajando activamente para superar esta limitación. Mientras tanto, puede desactivar **demorada carga** en **archivo** > **configuración de la aplicación** > **Configuraciónavanzada**(bajo **características en versión preliminar**).

### <a name="confirmexit"></a>ConfirmExit

**ConfirmExit** es una propiedad booleana que, cuando *true*, se abre un cuadro de diálogo de confirmación antes de cerrar la aplicación. De forma predeterminada, esta propiedad es *false*, y no aparece ningún cuadro de diálogo.

Utilice esta propiedad para mostrar un cuadro de diálogo de confirmación si el usuario ha realizado cambios pero no guardado. Usar una fórmula que puede comprobar las variables y propiedades del control (por ejemplo, el **no guardados** propiedad de la [ **Editar formulario** ](../controls/control-form-detail.md) control).

Aparece el cuadro de diálogo de confirmación en cualquier situación donde podrían perderse los datos, como en estos ejemplos:

- Ejecuta el [ **Exit** ](function-exit.md) función.
- Si la aplicación se ejecuta en un explorador:
  - Cierre el explorador o en la pestaña del explorador en el que se ejecuta la aplicación.
  - Seleccione el botón Atrás del explorador.
- Si se ejecuta la aplicación en PowerApps Mobile (iOS o Android):
  - Ejecuta el [ **iniciar** ](function-param.md) función.<br>El **iniciar** función no desencadena el cuadro de diálogo en un explorador, porque se abre otra ficha para que no se pierden datos.
  - Gesto de deslizar rápidamente para cambiar a otra aplicación en PowerApps Mobile.
  - Seleccione el botón Atrás en un dispositivo Android.

La apariencia exacta del cuadro de diálogo de confirmación puede variar entre los dispositivos y las versiones de PowerApps.

No aparece el cuadro de diálogo de confirmación en PowerApps Studio.

### <a name="confirmexitmessage"></a>ConfirmExitMessage

De forma predeterminada, el cuadro de diálogo de confirmación muestra un mensaje genérico, como **"No es posible que haya guardado los cambios."** en el idioma del usuario.

Use **ConfirmExitMessage** para proporcionar un mensaje personalizado en el cuadro de diálogo de confirmación. Si esta propiedad es *en blanco*, se usa el valor predeterminado. Mensajes personalizados se truncan según sea necesario para que quepa en el cuadro de diálogo de confirmación, por lo que mantendrá el mensaje a unas pocas líneas como máximo.

En un explorador, es posible que aparezca el cuadro de diálogo de confirmación con un mensaje genérico desde el explorador.

### <a name="example"></a>Ejemplo

1. Crear una aplicación que contiene dos controles de formulario, **AccountForm** y **ContactForm**.

1. Establecer el **aplicación** del objeto **ConfirmExit** propiedad en esta expresión:

    ```powerapps-comma
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    Este cuadro de diálogo aparece si el usuario cambia los datos en cualquiera de las formas y, a continuación, intenta cerrar la aplicación sin guardar los cambios.

    > [!div class="mx-imgBorder"]
    > ![Cuadro de diálogo de confirmación genérico](media/object-app/confirm-native.png)

1. Establecer el **aplicación** del objeto **ConfirmExitMessage** propiedad en esta fórmula:

    ```powerapps-comma
    If( AccountsForm.Unsaved;
        "Accounts form has unsaved changes.";
        "Contacts form has unsaved changes."
    )
    ```

    Este cuadro de diálogo aparece si el usuario cambia los datos en el formulario de cuenta y, a continuación, intenta cerrar la aplicación sin guardar los cambios.

    > [!div class="mx-imgBorder"]
    > ![Cuadro de diálogo de confirmación de forma específica](media/object-app/confirm-native-custom.png)
