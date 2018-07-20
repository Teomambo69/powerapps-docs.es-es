---
title: Creación de un flujo para administrar aprobaciones de proyectos | Microsoft Docs
description: En esta tarea, vamos a crear un flujo que acciona el proceso de aprobación de proyectos.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/09/18
ms.author: mblythe
ms.openlocfilehash: 17b20a12b0bcbee994ce772efa08e7d7ef50b9bf
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39017005"
---
# <a name="create-a-flow-to-manage-project-approvals"></a>Creación de un flujo para administrar aprobaciones de proyectos
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales acerca del uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

En esta tarea, vamos a crear un flujo que acciona el proceso de aprobación de proyectos. Microsoft Flow está integrado con SharePoint, por lo que resulta fácil crear un flujo de directamente desde una lista. El flujo que vamos a crear se desencadena cuando se agrega un elemento a la lista **Project Requests**. El flujo envía un correo electrónico al aprobador del proyecto, quien aprueba o rechaza la solicitud directamente en el correo electrónico. Después, el flujo envía un correo electrónico de aprobación o rechazo al solicitante del proyecto y actualiza nuestras listas de SharePoint en consecuencia.

## <a name="step-1-configure-the-flow-template"></a>Paso 1: Configuración de la plantilla de flujo
1. En la lista **Project Requests**, pulse o haga clic en **Flujo** y, luego, en **Crear un flujo**.
   
    ![Creación de un flujo](./media/sharepoint-scenario-approval-flow/03-01-01-create-flow.png)
2. En el panel derecho, pulse o haga clic en **Enviar aprobación cuando se agregue un elemento nuevo**.
   
    ![Crear un flujo de aprobación](./media/sharepoint-scenario-approval-flow/03-01-02-approval-flow.png)
3. Si aún no ha iniciado sesión, inicie sesión en SharePoint y Outlook, y pulse o haga clic en **Continuar**.
   
    ![Iniciar sesión para usar la plantilla](./media/sharepoint-scenario-approval-flow/03-01-03-continue.png)
   
    Ahora verá la plantilla para este flujo, lista para que la complete. Los cuadros en el flujo representan pasos. Toman tanto la entrada de los pasos anteriores como la que el usuario proporcione. Cada paso puede proporcionar salida a los pasos posteriores.
   
    ![Plantilla de aprobación](./media/sharepoint-scenario-approval-flow/03-01-04-template.png)
4. En el cuadro **Asignado a**, escriba un nombre que sea válido en el inquilino.
   
    ![Contacto de correo electrónico de aprobación](./media/sharepoint-scenario-approval-flow/03-01-05-approval-email.png)
   
    El siguiente cuadro del flujo responde a la decisión del correo electrónico del aprobador del proyecto y enruta el flujo a una de las dos *ramas*: **En caso positivo** o **En caso negativo**.
   
    ![Condición de aprobación](./media/sharepoint-scenario-approval-flow/03-01-06-condition.png)

## <a name="step-2-create-actions-for-approve--yes"></a>Paso 2: Crear acciones en caso de Approve = yes
De forma predeterminada, esta rama envía un correo electrónico de aprobación al solicitante. También se actualizará la lista **Project Requests** lista y se agregará un elemento a la lista **Project Details** porque el proyecto se ha aprobado.

1. En la rama **En caso positivo**, pulse o haga clic en **Inform item creator of approval** (Informar al creador del elemento de la aprobación) y, después, en **Edit** (Editar) para ver las opciones predeterminadas del mensaje de correo electrónico enviado al solicitante.
   
    ![Editar configuración de correo electrónico](./media/sharepoint-scenario-approval-flow/03-01-07-yes-email.png)
2. De forma predeterminada, se envía un correo electrónico a la persona que creó el elemento de la lista, con la línea de asunto y cuerpo del mensaje que se ven. Puede actualizar estos elementos si lo desea.
   
    ![Configuración predeterminada de correo electrónico](./media/sharepoint-scenario-approval-flow/03-01-07a-yes-email-defaults.png)
3. Pulse o haga clic en **Agregar una acción**.
   
    ![Agregar una acción](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. En **Elegir una acción**, busque "SharePoint", a continuación, haga clic o pulse en **SharePoint: actualizar elemento**.
   
    ![Actualizar acción del elemento](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. Escriba el nombre de lista y la dirección URL del sitio de SharePoint.
   
    ![Actualizar los parámetros del elemento](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. Seleccione el cuadro **Identificador** y pulse o haga clic en **Identificador** en el cuadro de diálogo *Contenido dinámico*.
   
    ![Enumerar contenido dinámico de ID](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
   
    El contenido dinámico está disponible en todo el flujo, basándose en los pasos anteriores. En este caso, la información de la lista de SharePoint está disponible y se puede usar en las acciones que se creen.
7. Seleccione el cuadro **Title**, busque "Title" en el cuadro de diálogo de contenido dinámico y pulse o haga clic en **Title**.
   
    ![Enumerar contenido dinámico de Title](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. En el cuadro **Aprobado**, escriba "Sí". Ahora esta parte del flujo debería parecerse a la siguiente imagen.
   
    ![Actualización de lista](./media/sharepoint-scenario-approval-flow/03-01-08-yes-update-complete.png)
9. Vuelva a pulse o a hacer clic en **Agregar una acción**. Esta vez vamos a agregar un elemento a la lista **Project Details** del proyecto que se ha aprobado.
   
    ![Agregar una acción](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
10. En **Elegir una acción**, busque "SharePoint" y seleccione **SharePoint: crear elemento**.
    
    ![Acción Crear elemento](./media/sharepoint-scenario-approval-flow/03-01-09-create.png)
11. Escriba el nombre de lista y la dirección URL del sitio de SharePoint.
    
    ![Crear los parámetros del elemento](./media/sharepoint-scenario-approval-flow/03-01-10-yes-create-list.png)
12. Seleccione el cuadro **Title**, busque "Title" en el cuadro de diálogo de contenido dinámico y pulse o haga clic en **Title**.
    
    ![Enumerar contenido dinámico de Title](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
13. Seleccione el cuadro **RequestId** y pulse o haga clic en **ID** en el cuadro de diálogo de contenido dinámico.
    
    ![Enumerar contenido dinámico de ID](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
14. En el cuadro **PMAssigned**, escriba "Sin asignar". Ahora esta parte del flujo debería parecerse a la siguiente imagen.
    
    ![Crear elemento completo](./media/sharepoint-scenario-approval-flow/03-01-11-yes-create-complete.png)

## <a name="step-3-review-action-for-approve--no"></a>Paso 3: Revisar las acciones en caso de Approve = no
De forma predeterminada, esta rama envía un correo electrónico de rechazo al solicitante. También se actualizará la lista **Project Requests**. El proyecto no va a avanzar, así que no se agrega ningún elemento a la lista **Project Details**.

1. En la rama **En caso negativo**, pulse o haga clic en **Inform item creator of rejection** (Informar al creador del elemento del rechazo) y, después, en **Edit** (Editar) para ver las opciones predeterminadas del mensaje de correo electrónico enviado al solicitante.
   
    ![Editar configuración de correo electrónico](./media/sharepoint-scenario-approval-flow/03-01-12-no-email.png)
2. De forma predeterminada, se envía un correo electrónico a la persona que creó el elemento de la lista, con la línea de asunto y cuerpo del mensaje que se ven. Puede actualizar estos elementos si lo desea.
   
    ![Configuración predeterminada de correo electrónico](./media/sharepoint-scenario-approval-flow/03-01-13-no-email-defaults.png)
3. Pulse o haga clic en **Agregar una acción**.
   
    ![Agregar una acción](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. En **Elegir una acción**, busque "SharePoint", a continuación, haga clic o pulse en **SharePoint: actualizar elemento**.
   
    ![Actualizar acción del elemento](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. Escriba el nombre de lista y la dirección URL del sitio de SharePoint.
   
    ![Actualizar los parámetros del elemento](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. Seleccione el cuadro **Identificador** y pulse o haga clic en **Identificador** en el cuadro de diálogo Contenido dinámico.
   
    ![Enumerar contenido dinámico de ID](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
7. Seleccione el cuadro **Title**, busque "Title" en el cuadro de diálogo de contenido dinámico y pulse o haga clic en **Title**.
   
    ![Enumerar contenido dinámico de Title](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. En el cuadro **Aprobado**, escriba "No". Ahora esta parte del flujo debería parecerse a la siguiente imagen.
   
    ![Actualización de lista](./media/sharepoint-scenario-approval-flow/03-01-08-no-update-complete.png)
9. En la parte superior derecha de la pantalla, pulse o haga clic en **Crear flujo**.
   
    El flujo está completo y debería ser similar a la siguiente imagen si se contraen los cuadros.
   
    ![Flujo finalizado](./media/sharepoint-scenario-approval-flow/03-01-16-flow-complete.png)

10. En la parte superior derecha de la pantalla, pulse o haga clic en **Listo**.
   
    ![Botón Listo](./media/sharepoint-scenario-approval-flow/03-01-15a-done-button.png)

## <a name="step-4-run-the-approval-flow"></a>Paso 4: Ejecución del flujo de aprobación
1. En la lista **Solicitudes de proyecto**, haga clic en **editar rápido** y agregar un elemento como el siguiente:
   
   * **Title** = "New monitor for Megan"

   * **Description** = "Megan needs a 24" monitor"

   * **ProjectType** = "New hardware"

   * **RequestDate** = "02/03/2017"

   * **Requestor** = "Megan Bowen"

   * **EstimatedDays** = "1"

   * **Approved** = "Pending"

     ![Elemento agregado a la lista](./media/sharepoint-scenario-approval-flow/03-02-01-list-add.png)
2. Haga clic en **Listo** en la parte superior de la página cuando haya terminado.
   
    ![Marca de verificación de Listo](./media/sharepoint-scenario-approval-flow/03-02-02-done.png)
3. Compruebe la bandeja de entrada de la cuenta de correo electrónico del aprobador. Debe tener un correo electrónico similar al siguiente.
   
    ![Correo electrónico para Allan Deyoung](./media/sharepoint-scenario-approval-flow/03-02-03-allan-email.png)
4. Después de hacer clic en **Aprobar** o **Rechazar** el flujo ejecuta otro proceso y obtiene información similar a la siguiente directamente en el correo electrónico.
   
    ![Acción de aprobación completa](./media/sharepoint-scenario-approval-flow/03-02-04-action-complete.png)
5. El flujo envía un correo electrónico a Megan con la respuesta de Allan, como se muestra en la siguiente imagen. Dicho correo electrónico procede *de* Megan porque es la propietaria del flujo.
   
    ![Correo electrónico a Megan Bowen](./media/sharepoint-scenario-approval-flow/03-02-05-megan-email.png)

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso de esta serie de tutoriales es [crear una aplicación para administrar proyectos](sharepoint-scenario-build-app.md).

