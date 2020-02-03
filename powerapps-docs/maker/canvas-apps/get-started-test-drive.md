---
title: Creación de una aplicación a partir de una plantilla | Microsoft Docs
description: Instrucciones paso a paso para crear una aplicación de lienzo automáticamente a partir de una plantilla de Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/29/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d64b1ef3f6d885093fc9f89ecf31b785c07ea6bd
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918722"
---
# <a name="create-a-canvas-app-from-a-template-in-power-apps"></a>Creación de una aplicación a partir de una plantilla en Power Apps

Cree automáticamente una aplicación de lienzo a partir de una plantilla para un escenario concreto, como el seguimiento de presupuestos y la programación de vacaciones, y luego ejecute la aplicación para reconocer su comportamiento predeterminado.

Para crear una aplicación a partir de una plantilla, se necesita una cuenta de almacenamiento en la nube (por ejemplo, DropBox, OneDrive o Google Drive) para almacenar los datos de ejemplo de la plantilla.

Si no tiene una licencia para Power Apps, puede [registrarse gratuitamente](../signup-for-powerapps.md).

## <a name="create-an-app"></a>Crear una aplicación

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el menú de navegación de la izquierda. Seleccione el menú desplegable **Nueva aplicación** y, a continuación, **Lienzo**.

    ![Nueva aplicación de lienzo](./media/get-started-test-drive/new-canvas-app.png)

    Se abrirá [Power Apps Studio](https://docs.microsoft.com/powerapps/powerapps-overview#power-apps-for-app-makerscreators) en una nueva pestaña.

1. En el icono **Plantillas de aplicación**, seleccione **Diseño de teléfono** o **Diseño de tableta**.

    ![Icono Aplicación desde una plantilla](./media/get-started-test-drive/template-tile.png)

1. En la lista de plantillas, seleccione una plantilla y, a continuación, **Usar**, cerca de la esquina inferior derecha.

    ![Apertura de una plantilla de Power Apps](./media/get-started-test-drive/open-template.png)

    Power Apps Studio se abre en una nueva pestaña y se crea la aplicación.

    > [!NOTE]
    > Si el botón **Usar** está deshabilitado, asegúrese de haber seleccionado un origen de datos para la aplicación. Para hacerlo, seleccione **Elegir** en la parte inferior.
    >
    > ![Elegir origen de datos](./media/get-started-test-drive/choose-data-source.png)

## <a name="run-the-app"></a>Ejecutar la aplicación
Una aplicación creada a partir de una plantilla se abre en el área de trabajo predeterminada en la que pasará la mayor parte del tiempo personalizándola. Antes de realizar cualquier cambio en la aplicación, explore cómo funciona la aplicación en el modo **Vista previa**.

1. Presione F5 (o haga clic o pulse en la flecha derecha situada en la esquina superior derecha) para abrir la aplicación en modo de **vista previa**.

    ![Botón para abrir el modo de vista previa](./media/get-started-test-drive/open-preview.png)

    La aplicación se rellena con datos de ejemplo para demostrar su funcionalidad. Por ejemplo, la aplicación Cost Estimator contiene datos para crear citas y estimar el costo de la instalación de un producto específico para suelos en una sala de un tamaño determinado.

4. Explore el comportamiento predeterminado de la aplicación mediante la creación, actualización y eliminación de datos de ejemplo y, después, compruebe que los datos de la cuenta de almacenamiento en la nube reflejan los cambios.

    Por ejemplo, concierte una cita y cree una estimación del costo en la aplicación Cost Estimator.

5. Presione Esc para volver al área de trabajo predeterminada (o pulse o haga clic en el icono **X** situado cerca de la esquina superior derecha).

## <a name="next-steps"></a>Pasos siguientes
1. Presione Ctrl-S, proporcione un nombre a su aplicación y, a continuación, haga clic o pulse **Guardar** para guardar la aplicación en la nube.

1. [Comparta su aplicación](share-app.md) con otras personas de su organización.

> [!IMPORTANT]
> Antes de compartir una aplicación, asegúrese de que las personas con quienes la comparta tengan acceso a los datos. Por ejemplo, quiere [compartir una hoja de Excel u otro archivo](share-app-data.md) en una cuenta de almacenamiento en la nube.
