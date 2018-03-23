---
title: Generación de una aplicación para controlar solicitudes de proyecto | Microsoft Docs
description: En esta tarea, se generará una *aplicación de tres pantallas* básica directamente desde una lista de SharePoint.
services: ''
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/12/2017
ms.author: mblythe
ms.openlocfilehash: 021a323fbb5a1a3331c4eb92ce0b47427b5562b4
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="generate-an-app-to-handle-project-requests"></a>Generación de una aplicación para controlar solicitudes de proyecto
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales acerca del uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

Ahora que las listas de SharePoint están en su sitio, podemos generar y personalizar la primera aplicación. PowerApps está integrado con SharePoint, por lo que es fácil generar una *aplicación de tres pantallas* básica directamente desde una lista. Esta aplicación permite ver información tanto resumida como detallada de cada elemento de la lista, actualizar los elementos existentes en la lista y crear nuevos elementos en la lista. Si crea una aplicación directamente a partir de una lista, esta aparece como un *vista* en dicha lista. Posteriormente, dicha aplicación se puede ejecutar tanto en un explorador como en un teléfono móvil.

> [!TIP]
> El [paquete de descarga](https://aka.ms/o4ia0f) para este escenario incluye una versión terminada de esta aplicación: project-requests-app.msapp.

## <a name="step-1-generate-an-app-from-a-sharepoint-list"></a>Paso 1: Generación de una aplicación a partir de una lista de SharePoint

1. En la lista **Project Requests** que ha creado, pulse o haga clic en **PowerApps** y, después en, **Crear una aplicación**.
   
    ![Crear una aplicación](./media/sharepoint-scenario-generate-app/02-01-01-create-app.png)

2. Asigne un nombre a la aplicación, como "Project Requests app", y haga clic o pulse en **Crear**. Cuando la aplicación está lista, se abre en PowerApps Studio para web.
   
    ![Especifique un nombre para la aplicación](./media/sharepoint-scenario-generate-app/02-01-02-create-app-name.png)

## <a name="step-2-review-the-app-in-powerapps-studio"></a>Paso 2: Examen de la aplicación en PowerApps Studio

1. En PowerApps Studio, la barra de navegación izquierda muestra de forma predeterminada una vista jerárquica de las pantallas y los controles de la aplicación.
   
    ![PowerApps Studio con la vista jerárquica](./media/sharepoint-scenario-generate-app/02-02-01-studio-screens-hierarchy.png)

2. Haga clic o pulse en el icono de la miniatura para cambiar de vista.
   
    ![Selector de vistas de PowerApps Studio](./media/sharepoint-scenario-generate-app/02-02-02-studio-view-selector.png)

3. Pulse o haga clic en la pantalla que desee para verla en el panel central. Hay tres pantallas:
   
    (a). La pantalla de **exploración**, donde se exploran, ordenan y filtran los datos extraídos de la lista.
    
    (b). La pantalla de **detalles**, en la que aparece información más detallada de un elemento.
    
    (c). La pantalla de **edición o creación**, donde se editan los elementos existentes o se crean nuevos.
      
      ![PowerApps Studio con la vista de miniaturas](./media/sharepoint-scenario-generate-app/02-02-03-studio-screens-thumbnails.png)

## <a name="step-3-customize-the-apps-browse-screen"></a>Paso 3: Personalización de la pantalla de exploración de la aplicación

1. Haga clic o pulse en la pantalla de exploración.
   
    Esta pantalla tiene una *diseño* que contiene un *galería* que muestra los elementos de lista, así como otros *controles*, como una barra de búsqueda y un botón de ordenación.

2. Seleccione la galería **BrowseGallery1** haciendo clic o pulsando en cualquier registro, excepto en el primero.
   
    ![Explorar galería](./media/sharepoint-scenario-generate-app/02-03-01-browse-gallery.png)

3. En el panel derecho, en **Propiedades**, haga clic o pulse **Project Requests**. 

4. Actualice los campos para que coincidan con los de la siguiente lista:
   
   * **RequestDate**

   * **Requestor**

   * **Title**

     ![Campos de la galería](./media/sharepoint-scenario-generate-app/02-03-02-gallery-fields.png)

5. Con **BrowseGallery1** aún seleccionado, seleccione la propiedad **Elementos**.
   
    ![Propiedad Elementos](./media/sharepoint-scenario-generate-app/02-03-03-items.png)

6. Cambie la fórmula a **SortByColumns(Filter('Project Requests', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))**.
   
    ![Barra de fórmulas](./media/sharepoint-scenario-generate-app/02-03-04-formula.png)
   
    Le permite ordenar y buscar por el campo **Title**, en lugar del predeterminado que eligió PowerApps. Para más información, consulte [Formula deep-dive](#formula-deep-dive) (Análisis en profundidad de una fórmula).

6. Pulse o haga clic en **Archivo** y, luego, en **Guardar**. Haga clic o pulse en ![el icono Back to app](./media/sharepoint-scenario-generate-app/icon-back-to-app.png) (Volver a la aplicación) para volver a la aplicación.

## <a name="step-4-review-the-apps-details-screen-and-edit-screen"></a>Paso 4: Revisión de la pantalla de detalles y la pantalla de edición de la aplicación
1. Haga clic o pulse en la pantalla de detalles.
   
    Esta pantalla tiene un diseño diferente que contiene un *formulario de presentación* que muestra los detalles de un elemento seleccionado en la galería. Tiene controles para editar y eliminar elementos, y para volver a la pantalla de exploración.
   
    ![Detalles del formulario de presentación](./media/sharepoint-scenario-generate-app/02-04-01-details.png)

4. Haga clic o pulse en la pantalla de edición.
   
    Esta pantalla contiene un *formulario de edición* para editar el elemento seleccionado o para crear uno nuevo (si se accede a él directamente desde la pantalla de exploración). Tiene controles para guardar o descartar los cambios.

    ![Formulario de edición](./media/sharepoint-scenario-generate-app/02-04-03-edit.png)

## <a name="step-5-run-the-app-from-the-list"></a>Paso 5: Ejecución de la aplicación desde la lista

1. En la lista **Project Requests**, pulse o haga clic en **Todos los elementos** y en **Project Requests app**.
   
    ![Ver Project Requests app](./media/sharepoint-scenario-generate-app/02-05-01-view-app.png)
2. Haga clic en **Abrir**, lo que abre la aplicación en una nueva pestaña de explorador.
   
    ![Abrir Project Requests app](./media/sharepoint-scenario-generate-app/02-05-02-open-app.png)

3. En la aplicación, pulse o haga clic en ![Icono Ir a detalles](./media/sharepoint-scenario-generate-app/icon-details-arrow.png) en el primer elemento de la galería de exploración.
   
    ![Primer elemento de la galería](./media/sharepoint-scenario-generate-app/02-05-04-first-item.png)

4. Haga clic o pulse ![Icono Lápiz (edición)](./media/sharepoint-scenario-generate-app/icon-pencil.png) para editar el elemento.

5. Actualice el campo **Description**: cambie la última palabra de "group" a "team" y, luego, pulse o haga clic en el ![icono de marca de verificación](./media/sharepoint-scenario-generate-app/icon-check-mark.png)
   
   ![Actualizar campo Description](./media/sharepoint-scenario-generate-app/02-05-07-edit.png)

6. Cierre la pestaña del explorador.

7. Vuelva a la lista **Project Requests**, pulse o haga clic en **Project Requests app** y en **Todos los elementos**.
   
   ![Ver todos los elementos](./media/sharepoint-scenario-generate-app/02-05-08-view-all.png)
8. Compruebe el cambio que realizó en la aplicación.
   
    ![Comprobar la edición](./media/sharepoint-scenario-generate-app/02-05-09-verify-edit.png)

Se trata de una aplicación muy simple y solo hemos realizado unas pocas personalizaciones básicas, pero se puede ver que es posible crear rápidamente algo interesante. Vamos a pasar a la tarea siguiente, pero si lo desea, examine la aplicación con mayor profundidad para ver cómo funcionan conjuntamente los controles y las fórmulas para potenciar el comportamiento de la aplicación.

## <a name="formula-deep-dive"></a>Análisis en profundidad de una fórmula
Esta sección es opcional, pero le ayudará a conocer mejor cómo funcionan las fórmulas. En el paso 3 de esta tarea, se modificó la fórmula de la propiedad **Elementos** de **BrowseGallery1**. En concreto, se cambió la forma en que se realizaban las acciones de ordenación y búsqueda para utilizar el campo **Title**, en lugar del campo que PowerApps seleccionaba. Esta es la fórmula modificada:

**SortByColumns ( Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text ) ), "Title", If ( SortDescending1, Descending, Ascending ) )**

Pero, ¿qué hace esta fórmula? Determina el origen de datos que aparece en la galería, filtra los datos en función del texto que se escriba en el cuadro de búsqueda y ordena los resultados en función del botón de ordenación de la aplicación. La fórmula usa *funciones* para realizar todas estas acciones. Las funciones toman parámetros (es decir, entrada), realizan una operación (por ejemplo, filtrado) y un devuelven un valor (es decir, salida):

* La [función **SortByColumns**](functions/function-sort.md) ordena una tabla según una o varias columnas.
* La [función **Filter**](functions/function-filter-lookup.md) busca los registros en una tabla que satisface una fórmula que se especifica.
* La [función **StartsWith**](functions/function-startswith.md) comprueba si una cadena de texto comienza por otra.
* La [función**If**](functions/function-if.md) devuelve un valor si una condición es true y otro valor si es false.

Cuando se juntan las funciones en la fórmula, ocurre lo siguiente:

1. Si escribe texto en el cuadro de búsqueda, la función **StartsWith** compara dicho texto con el principio de cada cadena de la columna **Title** de la lista.
   
    **StartsWith (Title, TextSearchBox1.Text)**
   
    Por ejemplo, si escribe "de" en el cuadro de búsqueda, verá cuatro resultados, incluidos los elementos que comienza por "Desktop" y "Device". No verá todos los elementos de "Mobile devices" porque no *empiezan por* "de".

2. La función **Filter** *devuelve* filas de la tabla **Project Requests**. Si no hay texto en el cuadro de búsqueda con el que comparar, **Filter** devuelve todas las filas.
   
    **Filter ('Project Requests', StartsWith (Title, TextSearchBox1.Text)**

3. La función **If** examina si la variable **SortDescending1** está establecida en true o false (la establece el botón de ordenación de la aplicación). A continuación, la función devuelve uno de estos dos valores: **Descending** o **Ascending**.
   
    **If (SortDescending1, Descending, Ascending)**

4. Ahora la función **SortByColumns** puede ordenar la galería. En este caso, la ordena por el campo **Title**, pero puede ser un campo que no se en el que se busca.

Si ha seguido la explicación, esperamos que conozca mejor cómo funciona esta fórmula y cómo puede combinar funciones y otros elementos para lograr el comportamiento que las aplicaciones requieren. Para más información, consulte [Referencia sobre fórmulas para PowerApps](formula-reference.md).

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso de esta serie de tutoriales es [crear un flujo para administrar aprobaciones de proyectos](sharepoint-scenario-approval-flow.md).

