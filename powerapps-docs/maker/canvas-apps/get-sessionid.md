---
title: Obtención de un identificador de sesión o un identificador de aplicación | Microsoft Docs
description: Cómo obtener un identificador de sesión o un identificador de aplicación para solucionar problemas en PowerApps
author: AFTOwen
ms.service: powerapps
ms.topic: conceptual
ms.component: canvas
ms.date: 06/18/2018
ms.author: anneta, brimcg
ms.openlocfilehash: add591d1bf565f3ad89e0138257fdf365d6add8e
ms.sourcegitcommit: 1126caa4c7516cd4dffcff7e0c3eca440a333a58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36304693"
---
# <a name="get-a-session-id-or-an-app-id"></a>Obtención de un identificador de sesión o un identificador de aplicación
Si encuentra un problema con una aplicación que se creó en PowerApps, puede ayudar a Microsoft a solucionar el problema de manera mucho más efectiva si les proporciona un identificador de sesión, un identificador de aplicación o ambos para ese problema.

## <a name="get-the-session-id"></a>Obtención del identificador de sesión

### <a name="when-editing-an-app"></a>Al editar una aplicación
1. En la esquina superior izquierda, seleccione **Archivo**.

1. Seleccionar **Cuenta**.

1. En **Diagnósticos**, seleccione **Detalles de la sesión**.

    ![Obtención de un identificador de sesión de PowerApps Studio](media/get-sessionid/studio.png)

### <a name="when-running-an-app-in-a-browser"></a>Al ejecutar una aplicación en un explorador
1. En la esquina superior derecha, seleccione el icono de engranaje.

1. Seleccione **Detalles de la sesión**.

    ![Obtención de un identificador de sesión de un explorador](media/get-sessionid/browser.png)

### <a name="when-running-an-app-on-a-phone-or-a-tablet"></a>Cuando ejecute una aplicación en un teléfono o una tableta
1. Deslice rápidamente hacia la derecha.

1. Pulse **Detalles de la sesión**.

    ![Obtención de un identificador de sesión de un explorador](media/get-sessionid/mobile.png)

### <a name="when-running-an-embedded-app-or-form"></a>Al ejecutar una aplicación o un formulario insertado
1. Realice uno de estos pasos:

    - Mientras mantiene presionada la tecla Alt, haga clic con el botón derecho en la aplicación o el formulario.
    - Pulse la aplicación o el formulario con dos dedos durante 1 o 2 segundos y luego suelte.

1. Seleccione **Detalles de la sesión**.

    ![Obtención de un identificador de sesión de una aplicación insertada](media/get-sessionid/embedded.png)

## <a name="get-an-app-id"></a>Obtención de un identificador de aplicación
1. [Inicie sesión en PowerApps](https://powerapps.microsoft.com).

1. Cerca del borde izquierdo, seleccione **Aplicaciones**.

1. Seleccione los puntos suspensivos ( **. . .** ) para la aplicación en la que está solucionando problemas y luego seleccione **Detalles**.

    ![Ir a los detalles de la aplicación](./media/get-sessionid/details.png)

    El identificador de la aplicación aparece en la parte inferior del panel **Detalles** para esa aplicación.

    ![Copiar el identificador de la aplicación desde los detalles](./media/get-sessionid/app-id.png)
