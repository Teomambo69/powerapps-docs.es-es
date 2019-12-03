---
title: Iniciar un flujo en una aplicación de lienzo | Microsoft Docs
description: Cree un flujo que realice una o varias tareas después de que un evento, como la selección de un botón por parte de un usuario, se produzca en una aplicación de lienzo.
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a4e19b4b261bb489dd5c63e4393452a500ab3df9
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732914"
---
# <a name="start-a-flow-in-a-canvas-app"></a>Iniciar un flujo en una aplicación de lienzo

Puede usar Power Automate para crear lógica que realice una o varias tareas cuando se produce un evento en una aplicación de lienzo. Por ejemplo, configure un botón para que cuando un usuario lo seleccione, se cree un elemento en una lista de SharePoint, se envíe un correo electrónico o una convocatoria de reunión, se agregue un archivo a la nube o se realicen todas estas acciones. Puede configurar cualquier control en la aplicación para iniciar el flujo, que continúa ejecutándose incluso si cierra Power apps.

> [!NOTE]
> Cuando un usuario ejecuta un flujo desde una aplicación, el usuario debe tener permiso para realizar las tareas que se especifican en el flujo. De lo contrario, se producirá un error en el flujo.

## <a name="prerequisites"></a>Requisitos previos

- [Regístrese](../signup-for-powerapps.md) en Power apps.
- Tiene que saber [configurar un control](add-configure-controls.md).

## <a name="create-a-flow"></a>Creación de un flujo

1. Inicie sesión en [Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. En la barra de navegación izquierda, seleccione **lógica de negocios**y, a continuación, seleccione **flujos**.

1. En la esquina superior izquierda de la página **Mis flujos** , seleccione **nuevo**y, a continuación, seleccione **crear desde**cero.

    ![Opción para crear un flujo sin usar una plantilla](./media/using-logic-flows/create-from-blank.png)

1. Cerca de la parte inferior de la página que aparece, seleccione **Buscar cientos de conexiones y desencadenadores**.

1. En el cuadro de búsqueda, escriba **powerapps**y, luego, seleccione el icono de **powerapps** .

    ![Creación de un desencadenador de Power apps](./media/using-logic-flows/set-trigger.png)
    
1. En la página siguiente, vuelva a seleccionar el icono de Power apps y luego seleccione **nuevo paso**.

1. En el cuadro que dice **Buscar conectores y acciones**, especifique una acción para el flujo, como en este ejemplo:

   1. Escriba **SharePoint** en el cuadro y, a continuación, seleccione **crear elemento** en la lista de **acciones**.

       ![Opción para crear un elemento de SharePoint](./media/using-logic-flows/create-sharepoint-item.png)

   1. Si se le solicita, especifique las credenciales para conectarse a SharePoint.

   1. En el cuadro **Dirección del sitio web**, escriba o pegue la dirección URL de un sitio de SharePoint Online que contenga una lista.

       > [!NOTE]
       > No Anexe el nombre de la lista a la dirección URL.

   1. En el cuadro **nombre de lista** , especifique la lista que desea utilizar.
   
       ![Especificar lista](./media/using-logic-flows/list-fields.png)

   1. Seleccione el cuadro de entrada de un campo en la lista (por ejemplo, **título**), seleccione **Ver más** en el panel de contenido dinámico y, a continuación, seleccione **preguntar en Power apps**. 

       ![Agregar el parámetro Ask en Power apps al campo title](./media/using-logic-flows/ask-in-powerapps.png)

1. opta Especifique uno o más pasos adicionales, como el envío de correo electrónico de aprobación a una dirección que especifique o la creación de una entrada relacionada en otro origen de datos.

1. Cerca de la esquina superior izquierda, escriba o pegue un nombre para el flujo y, a continuación, seleccione **Guardar** cerca de la esquina superior derecha.

## <a name="add-a-flow-to-an-app"></a>Agregar un flujo a una aplicación
1. En la barra de navegación izquierda, seleccione **crear**.

1. Mantenga el puntero sobre la **aplicación Canvas desde el icono en blanco** y seleccione **Make this App (crear esta aplicación**).

1. Agregue un control **[Entrada de texto](controls/control-text-input.md)** y llámelo **RecordTitle**.

1. Agregue un control **[Botón](controls/control-button.md)** y muévalo debajo de **RecordTitle**.

1. Con el control **[Botón](controls/control-button.md)** seleccionado, seleccione **Flujos** en la pestaña **Acción**.

    ![Opción Flujos en la pestaña Acción](./media/using-logic-flows/action-tab.png)

1. En el panel que aparece, seleccione el flujo que creó en el procedimiento anterior.

    > [!NOTE]
   > Si el flujo que ha creado no está disponible, confirme si Power apps está establecido en el entorno en el que creó el flujo.

    ![Agregar un flujo desde el panel de personalización](./media/using-logic-flows/add-flow-from-pane.png)

1. En la barra de fórmulas, escriba o pegue **RecordTitle.Text)** al final de la fórmula que se han agregado automáticamente.

    ![Propiedad AlSeleccionar que incluye el flujo](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>Probar la aplicación
1. Haga doble clic en el control **entrada de texto** y escriba o pegue texto en él.

1. Mientras mantiene presionada la tecla Alt, seleccione el control de **[botón](controls/control-button.md)** .

    Se crea un elemento de SharePoint en la lista que especificó con el texto que especificó como título. Si la lista estaba abierta cuando se ejecutó el flujo, tendrá que actualizar la ventana del explorador para mostrar los cambios.
