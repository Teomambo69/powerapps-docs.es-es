---
title: "Inicio de un flujo en una aplicación | Microsoft Docs"
description: "Cree un flujo que realice una o varias tareas después de que un evento, como la selección de un botón por parte de un usuario, se produzca en una aplicación."
services: 
suite: powerapps
documentationcenter: 
author: stepsic-microsoft-com
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/05/2017
ms.author: karthikb
ms.openlocfilehash: 9c4ff3d1f6a01c2a0362f4a9c994bb740c0a66b8
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="start-a-flow-in-an-app"></a>Inicio de un flujo en una aplicación
Microsoft Flow se puede usar para crear lógica que realice una o varias tareas cuando se produce un evento en una aplicación. Por ejemplo, configure un botón para que cuando un usuario lo seleccione, se cree un elemento en una lista de SharePoint, se envíe un correo electrónico o una convocatoria de reunión, se agregue un archivo a la nube o se realicen todas estas acciones. Puede configurar que el flujo pueda iniciarlo cualquier control de la aplicación, que continúa ejecutándose aunque cierre PowerApps.

**Requisitos previos**

* [Suscríbase](signup-for-powerapps.md) a PowerApps y, después, siga estos pasos:
  
  * En la [Tienda Windows](http://aka.ms/powerappsinstall), instale PowerApps Studio para Windows, ábralo e inicie sesión con las mismas credenciales que usó para suscribirse.
  * En [powerapps.com](http://web.powerapps.com), abra PowerApps Studio para web haciendo clic o pulsando en **Nueva aplicación** en la esquina inferior izquierda.
* Tiene que saber [configurar un control](add-configure-controls.md).

## <a name="create-a-flow"></a>Creación de un flujo
1. Inicie sesión en [powerapps.com](http://web.powerapps.com) y seleccione **Flujos** en la barra de navegación izquierda.
2. En la página **Mis flujos**, seleccione **Crear desde cero**.
   
    ![Opción para crear un flujo sin usar una plantilla](./media/use-logic-flows/create-from-blank.png)
   
    **PowerApps** se agrega como el desencadenador predeterminado.
   
    ![PowerApps como desencadenador que inicia el flujo](./media/use-logic-flows/set-trigger.png)
3. Seleccione **Nuevo paso** y, después, seleccione **Agregar una acción**.
   
    ![Opción para agregar una sección](./media/use-logic-flows/add-action.png)
4. En el cuadro que dice **Buscar todos los servicios y acciones**, especifique una acción para el flujo, como en el ejemplo:
   
   1. Escriba **SharePoint** en el cuadro y seleccione **SharePoint - Create item** (SharePoint: crear elemento) en la lista **Acciones**.
      
       ![Opción para crear un elemento de SharePoint](./media/use-logic-flows/create-sharepoint-item.png)
   2. Si se le solicita, especifique las credenciales para conectarse a SharePoint.
   3. En el cuadro **Dirección del sitio web**, escriba o pegue la dirección URL de un sitio de SharePoint Online que contenga una lista.
      
       **Nota:** Especifique la dirección URL del sitio, sin incluir la lista.
   4. En el cuadro **Nombre de lista** , seleccione la lista que desea utilizar.
   5. Haga clic o pulse en el cuadro **Título** y seleccione **Agregar contenido dinámico**.
      
       ![Agregar el parámetro Preguntar en PowerApps al campo Título](./media/use-logic-flows/ask-in-powerapps.png)
   6. En la lista de parámetros, seleccione **Preguntar en PowerApps**.
      
       ![Agregar parámetro](./media/use-logic-flows/add-parameter.png)
5. (opcional) Especifique una o varias acciones adicionales, como el envío de correo electrónico de aprobación a una dirección que especifique o la creación de una entrada relacionada en otro origen de datos.
6. Cerca de la parte superior de la pantalla, escriba o pegue el nombre del flujo y, después, seleccione **Crear flujo**.
   
    ![Asignar un nombre y guardar el flujo](./media/use-logic-flows/name-flow.png)

## <a name="add-a-flow-to-an-app"></a>Agregar un flujo a una aplicación
1. En el menú **Archivo** de PowerApps, seleccione **Nuevo**.
2. En el icono **Aplicación vacía**, seleccione **Diseño de teléfono**.
3. Agregue un control **[Entrada de texto](controls/control-text-input.md)** y llámelo **RecordTitle**.
4. Agregue un control **[Botón](controls/control-button.md)** y muévalo debajo de **RecordTitle**.
5. Con el control **[Botón](controls/control-button.md)** seleccionado, seleccione **Flujos** en la pestaña **Acción**.
   
    ![Opción Flujos en la pestaña Acción](./media/use-logic-flows/action-tab.png)
6. En el panel que aparece, seleccione el flujo que creó en el procedimiento anterior.
   
    **Nota**: Si el flujo que ha creado no está disponible, compruebe si PowerApps está establecido en el entorno donde lo creara.
   
    ![Agregar un flujo desde el panel de personalización](./media/use-logic-flows/add-flow-from-pane.png)
7. En la barra de fórmulas, escriba o pegue **RecordTitle.Text)** al final de la fórmula que se han agregado automáticamente.
   
    ![Propiedad AlSeleccionar que incluye el flujo](./media/use-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>Probar la aplicación
1. Abra Versión preliminar, para lo que debe presionar F5 (o seleccione la flecha que hay cerca de la esquina superior derecha).
   
    ![Propiedad AlSeleccionar que incluye el flujo](./media/use-logic-flows/open-preview.png)
2. Escriba o pegue el texto en **RecordTitle** y haga clic en el control **[Botón](controls/control-button.md)**.
   
    Se crea un elemento de SharePoint en la que lista especificó con el texto que especificó como título. Si la lista estaba abierta cuando se ejecutó el flujo, tendrá que actualizar la ventana del explorador para mostrar los cambios.
