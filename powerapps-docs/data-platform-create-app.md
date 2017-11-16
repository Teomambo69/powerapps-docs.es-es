---
title: "Generación de una aplicación mediante una base de datos de Common Data Service | Microsoft Docs"
description: "Genere una aplicación para agregar, actualizar y eliminar registros."
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 7fffa909b42dfd23bc4b72d032a524df27d614aa
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="generate-an-app-by-using-a-common-data-service-database"></a>Generar una aplicación mediante una base de datos de Common Data Service
[!VIDEO nb:cid:UUID:6d7aa0a1-cd31-47c6-9a32-93b4e5476ece]


Puede generar automáticamente una aplicación para administrar datos almacenados en Common Data Service. Puede administrar datos en una de las numerosas entidades estándar que están integradas en el modelo o en una entidad personalizada creada por usted u otra persona de la organización.

Si no está familiarizado con Common Data Service, consulte [Comprender las entidades](data-platform-intro.md).

En este tema, se describe cómo puede generar automáticamente una aplicación basada en una sola entidad que especifique. Para información acerca de cómo crear una aplicación que se basa en más de una entidad, consulte [Crear una aplicación desde cero](data-platform-create-app-scratch.md).

De forma predeterminada, todas las aplicaciones generadas por Microsoft PowerApps tienen tres pantallas:

* La pantalla de exploración muestra un subconjunto de uno o varios campos, una barra de búsqueda y un botón de ordenación que permite que los usuarios encuentren fácilmente un registro específico.
* La pantalla de detalles muestra algunos o todos los campos de un registro específico.
* La pantalla de edición proporciona elementos de interfaz de usuario que permiten que los usuarios creen o actualicen un registro y guarden los cambios.

**Nota**: Al generar una aplicación desde Common Data Service, no es necesario crear una conexión desde PowerApps, como ocurre con los orígenes de datos tales como SharePoint, Dynamics 365 y Salesforce. Basta con que especifique la entidad que desee mostrar, administrar, o mostrar y administrar en la aplicación.

## <a name="generate-an-app"></a>Generar una aplicación
1. Cree una base de datos de Common Data Service. Para más información, consulte [Crear una base de datos de Common Data Service](create-database.md).
2. En PowerApps Studio para Windows, pulse o haga clic en **Nuevo** en el menú **Archivo** (cerca del borde izquierdo).
3. En **Comenzar con los datos**, en el icono **Common Data Service**, pulse o haga clic en **Diseño de teléfono**.
4. En **Elegir una entidad**, haga clic o pulse en la entidad **Contact**.
5. Haga clic o pulse en **Conectar** para generar una aplicación automáticamente.
   
    En este punto, es posible que se le pida que realice un paseo introductorio. Para realizar el paseo más tarde, pulse o haga clic en el signo de interrogación situado cerca de la esquina superior derecha y pulse o haga clic en **Take the intro tour** (Realizar paseo introductorio).
6. En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.
   
    ![Alternancia de las vistas](./media/data-platform-create-app/toggle-view.png)

## <a name="customize-the-browse-screen"></a>Personalizar la pantalla de exploración
1. En el panel derecho, pulse o haga clic en el diseño que muestra solo un encabezado.
   
    ![Seleccione un diseño](./media/data-platform-create-app/choose-gallery-layout.png)
2. En el cuadro de búsqueda, haga clic o pulse en el control **Etiqueta** para seleccionarlo.
   
    ![Seleccione una etiqueta](./media/data-platform-create-app/select-textbox.png)
3. En el panel derecho, seleccione **Apellidos de Nombre proporcionado** en la lista desplegable.
   
     El control **Etiqueta** que seleccionó muestra los datos del campo.
4. En la pantalla de exploración, seleccione la galería haciendo clic o pulsando en cualquier nombre, excepto el primero.
   
    Se muestra un cuadro de selección alrededor de la galería.
   
    ![Seleccione la galería](./media/data-platform-create-app/select-gallery.png)
5. Copie la siguiente fórmula seleccionándola y presionando CTRL+C.
   
    **SortByColumns(Search(Contact, TextSearchBox1.Text, "Name_Surname"), "Name_Surname", If(SortDescending1, Descending, Ascending))**
6. Cerca de la esquina superior izquierda, asegúrese de que la lista de propiedades muestre **Elementos**.
7. En la barra de fórmulas, seleccione la fórmula predeterminada.
   
    ![Valor predeterminado de la propiedad Items](./media/data-platform-create-app/default-items.png)
8. Presione Supr para eliminar la fórmula predeterminada y, después, pegue la que ha copiado. Los nombres de la galería siguen un orden alfabético.

## <a name="test-the-browse-screen"></a>Probar la pantalla de exploración
1. Para abrir el modo de vista previa, presione F5 o pulse o haga clic en el botón **Reproducir** cerca de la esquina superior derecha.
2. Desplácese por todos los registros usando una pantalla táctil o la rueda del mouse, o señalando a la galería con el mouse para que aparezca la barra de desplazamiento.
3. Cerca de la esquina superior derecha, pulse o haga clic en el botón de ordenación una o más veces para cambiar el orden de los nombres.
   
    ![Cambiar el criterio de ordenación](./media/data-platform-create-app/sort-button.png)
4. En el cuadro de búsqueda, escriba una letra para mostrar solo los nombres que la contengan.
5. Quite todo el texto del cuadro de búsqueda y pulse o haga clic en la flecha situada a la derecha del primer nombre de la lista.
   
    Se abre la pantalla de detalles, que muestra más información sobre el contacto que seleccionó.
6. Para volver al área de trabajo de diseño, presione Esc o pulse o haga clic en el icono **Cerrar** situado cerca de la esquina superior derecha, debajo de la barra de título.

## <a name="customize-the-other-screens"></a>Personalizar las otras pantallas
1. Si **PantallaDetalles** no aparece, pulse o haga clic en la miniatura intermedia en la barra de navegación izquierda.
2. Cerca de la parte superior de **PantallaDetalles**, pulse o haga clic en **Nombre completo** para mostrar las opciones para personalizar el formulario en esa pantalla.
3. En el panel derecho, pulse o haga clic en el botón del ojo para **Name_MiddleName** para ocultar ese campo.
4. En el panel derecho, pulse o haga clic en el botón del ojo para **Name_Surname** para mostrar ese campo.
5. En el panel derecho, arrastre **Name_Surname** hacia arriba y colóquelo justo debajo de **Name_GivenName**.
   
    **PantallaDetalles** refleja los cambios.
6. En la barra de navegación izquierda, pulse o haga clic en la miniatura inferior para mostrar **EditarPantalla** y repita los pasos anteriores de este procedimiento para que **EditarPantalla** coincida con **PantallaDetalles**.

## <a name="test-the-app"></a>Probar la aplicación
1. En la barra de navegación izquierda, pulse o haga clic en la imagen en miniatura superior para mostrar la pantalla de exploración.
2. Para abrir el modo de vista previa, presione F5 o pulse o haga clic en el botón **Reproducir** cerca de la esquina superior derecha.
3. En la esquina superior derecha de la pantalla de exploración, pulse o haga clic en el icono del signo más (**+**) para crear un registro.
4. Agregue texto en los campos **Nombre proporcionado** y **Apellidos**, y pulse o haga clic en el botón de marca de verificación para guardar el nuevo registro y volver a la pantalla de exploración.
5. Busque el registro que acaba de crear y pulse o haga clic en la flecha situada a su derecha para mostrarlo en la pantalla de detalles.
6. En la esquina superior derecha, pulse o haga clic en el botón de lápiz para mostrar el registro en la pantalla de edición.
7. Cambie los datos del campo **Nombre proporcionado** y pulse o haga clic el botón de marca de verificación para guardar los cambios.
8. Cerca de la esquina superior derecha, pulse o haga clic en el botón de papelera para eliminar el registro que acaba de crear y actualizar.

## <a name="next-steps"></a>Pasos siguientes
[Crear una aplicación desde cero mediante una base de datos de Common Data Service](data-platform-create-app-scratch.md)

