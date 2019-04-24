---
title: Iniciar un flujo en una aplicación de lienzo | Microsoft Docs
description: Cree un flujo que realice una o varias tareas después de que un evento, como la selección de un botón por parte de un usuario, se produzca en una aplicación de lienzo.
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5439399a22b47fcf4195cf878208e0e0bd4e0764
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61532157"
---
# <a name="start-a-flow-in-a-canvas-app"></a>Iniciar un flujo en una aplicación de lienzo

Microsoft Flow se puede usar para crear lógica que realice una o varias tareas cuando se produce un evento en una aplicación de lienzo. Por ejemplo, configure un botón para que cuando un usuario lo seleccione, se cree un elemento en una lista de SharePoint, se envíe un correo electrónico o una convocatoria de reunión, se agregue un archivo a la nube o se realicen todas estas acciones. Puede configurar que el flujo pueda iniciarlo cualquier control de la aplicación, que continúa ejecutándose aunque cierre PowerApps.

> [!NOTE]
> Cuando un usuario ejecuta un flujo desde dentro de una aplicación, que el usuario debe tener permiso para realizar las tareas que se especifican en el flujo. En caso contrario, se producirá un error en el flujo.

## <a name="prerequisites"></a>Requisitos previos

- [Inicie sesión](../signup-for-powerapps.md) en PowerApps.
- Tiene que saber [configurar un control](add-configure-controls.md).

## <a name="create-a-flow"></a>Creación de un flujo

1. Inicie sesión en [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. En la barra de navegación izquierdo, seleccione **lógica de negocios**y, a continuación, seleccione **flujos**.

1. En la esquina superior izquierda de la **Mis flujos** página, seleccione **New**y, a continuación, seleccione **crear desde cero**.

    ![Opción para crear un flujo sin usar una plantilla](./media/using-logic-flows/create-from-blank.png)

1. La parte inferior de la página que aparece, seleccione **buscar entre cientos de conexiones y los desencadenadores**.

1. En el cuadro de búsqueda, escriba **PowerApps**y, a continuación, seleccione el **PowerApps** icono.

    ![Crear un desencadenador de PowerApps](./media/using-logic-flows/set-trigger.png)
    
1. En la siguiente página, seleccione el icono de PowerApps de nuevo y, a continuación, seleccione **nuevo paso**.

1. En el cuadro que dice **buscar conectores y acciones**, especificar una acción para el flujo, como en este ejemplo:

   1. Tipo **SharePoint** en el cuadro y, a continuación, seleccione **crear elemento** en la lista bajo **acciones**.

       ![Opción para crear un elemento de SharePoint](./media/using-logic-flows/create-sharepoint-item.png)

   1. Si se le solicita, especifique las credenciales para conectarse a SharePoint.

   1. En el cuadro **Dirección del sitio web**, escriba o pegue la dirección URL de un sitio de SharePoint Online que contenga una lista.

       > [!NOTE]
       > No agregue el nombre de la lista a la URL.

   1. En el **nombre de la lista** , especifique la lista que desea usar.
   
       ![Especifique la lista](./media/using-logic-flows/list-fields.png)

   1. Seleccione el cuadro de entrada para un campo en la lista (como **título**), seleccione **más** en el panel de contenido dinámico y, a continuación, seleccione **preguntar en PowerApps**. 

       ![Agregar el parámetro Preguntar en PowerApps al campo Título](./media/using-logic-flows/ask-in-powerapps.png)

1. (opcional) Especifique uno o varios pasos adicionales, como enviar correo electrónico de aprobación a una dirección que especifique o crear una entrada relacionada en otro origen de datos.

1. Cerca de la esquina superior izquierda, escriba o pegue el nombre del flujo y, a continuación, seleccione **guardar** cerca de la esquina superior derecha.

## <a name="add-a-flow-to-an-app"></a>Agregar un flujo a una aplicación
1. En la barra de navegación izquierdo, seleccione **crear**.

1. Mantenga el mouse sobre el **desde cero una aplicación de lienzo** icono y, a continuación, seleccione **hacer que esta aplicación**.

1. Agregue un control **[Entrada de texto](controls/control-text-input.md)** y llámelo **RecordTitle**.

1. Agregue un control **[Botón](controls/control-button.md)** y muévalo debajo de **RecordTitle**.

1. Con el control **[Botón](controls/control-button.md)** seleccionado, seleccione **Flujos** en la pestaña **Acción**.

    ![Opción Flujos en la pestaña Acción](./media/using-logic-flows/action-tab.png)

1. En el panel que aparece, seleccione el flujo que creó en el procedimiento anterior.

    > [!NOTE]
   > Si el flujo que ha creado no está disponible, compruebe si PowerApps está establecido en el entorno en el que lo creó.

    ![Agregar un flujo desde el panel de personalización](./media/using-logic-flows/add-flow-from-pane.png)

1. En la barra de fórmulas, escriba o pegue **RecordTitle.Text)** al final de la fórmula que se han agregado automáticamente.

    ![Propiedad AlSeleccionar que incluye el flujo](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>Probar la aplicación
1. Haga doble clic en el **entrada de texto** controlar y escriba o pegue el texto en él.

1. Mientras mantiene presionada la tecla Alt, seleccione el **[botón](controls/control-button.md)** control.

    Se crea un elemento de SharePoint en la lista que ha especificado con el texto que especificó como título. Si la lista estaba abierta cuando se ejecutó el flujo, tendrá que actualizar la ventana del explorador para mostrar los cambios.
