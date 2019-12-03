---
title: Obtención de un identificador de sesión o un identificador de aplicación de lienzo | Microsoft Docs
description: Cómo obtener un identificador de sesión o un identificador de aplicación de lienzo para solucionar problemas en PowerApps
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 81c1db4ab44f3ca8517c6154f0516ca9dad5f825
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74676520"
---
# <a name="get-a-session-id-or-a-canvas-app-id"></a>Obtención de un identificador de sesión o un identificador de aplicación de lienzo
Si se produce un problema con una aplicación de lienzo creada en Power Apps, puede ayudar a Microsoft a solucionar el problema de forma más eficaz si se les proporciona un identificador de sesión, un identificador de aplicación o ambos para ese problema.

## <a name="get-the-session-id"></a>Obtención del identificador de sesión

### <a name="when-editing-an-app"></a>Al editar una aplicación
1. En la esquina superior izquierda, seleccione **Archivo**.

1. Seleccionar **Cuenta**.

1. En **Diagnósticos**, seleccione **Detalles de la sesión**.

    ![Obtención de un identificador de sesión de Power apps Studio](media/get-sessionid/studio.png)

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
