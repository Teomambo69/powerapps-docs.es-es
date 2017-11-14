En este tema, examinamos más detenidamente la aplicación generada y se revisan las pantallas y los controles que definen el comportamiento de la aplicación. Aunque no expliquemos todos los detalles, el mero hecho de ver cómo funciona esta aplicación le ayudará a compilar sus propias aplicaciones. En un tema posterior, examinaremos las fórmulas que funcionan con las pantallas y los controles.

## <a name="run-the-app-in-preview-mode"></a>Ejecutar la aplicación en modo de vista previa
Haga clic o pulse ![Flecha Iniciar vista previa de aplicación](./media/learning-case-app-explore-controls/f5-arrow-sm.png) en la parte superior derecha para ejecutar la aplicación. Si se desplaza por la aplicación, verá que incluye los datos de la entidad y proporciona una buena experiencia predeterminada.

![Ejecutar la aplicación en modo de vista previa](./media/learning-case-app-explore-controls/run-app.png)

## <a name="understanding-controls-in-powerapps"></a>Descripción de los controles de PowerApps
Un control no es más que un elemento de la interfaz de usuario que tiene comportamientos asociados. Muchos de los controles de PowerApps son los mismos que ha utilizado en otras aplicaciones: etiquetas, cuadros de entrada de texto, listas desplegables, elementos de navegación, etc. Pero PowerApps tiene controles más especializados como **Galerías** (que muestran datos resumidos) y **Formularios** (que muestran datos detallados y permiten crear y editar elementos). También tiene otros controles realmente increíbles, como **Imagen**, **Cámara** y **Código de barras**. Para ver cuáles están disponibles, pulse o haga clic en **Insertar** en la cinta de opciones y, después, pulse o haga clic en cada una de las opciones, de **Texto** a **Iconos**.

![Pestaña de controles en la cinta de opciones de PowerApps Studio](./media/learning-case-app-explore-controls/ribbon-controls.png)

## <a name="explore-the-browse-screen"></a>Exploración de la pantalla de exploración
Cada una de las tres pantallas de la aplicación tiene un control principal y varios controles adicionales. La primera pantalla de la aplicación es la pantalla de exploración, denominada **BrowseScreen1** de manera predeterminada. El control principal de esta pantalla es una galería denominada **BrowseGallery1**. **BrowseGallery1** contiene otros controles, como **NextArrow1** (un control de icono; haga clic en él o púlselo para ir a la pantalla de detalles). En la pantalla también hay controles independientes, como **IconNewItem1** (un control de icono; haga clic en él o púlselo para crear un elemento en la pantalla de edición o creación).

![Pantalla de exploración con controles](./media/learning-case-app-explore-controls/browse-screen.png)

PowerApps tiene varios tipos de galerías, por lo que puede utilizar la que mejor se adapte a los requisitos de diseño de la aplicación. Más adelante en esta sección encontrará más formas de controlar el diseño.

![Opciones de galería de PowerApps](./media/learning-case-app-explore-controls/insert-gallery.png)

## <a name="explore-the-details-screen"></a>Exploración de la pantalla de detalles
A continuación se encuentra la pantalla de detalles, denominada **DetailScreen1** de manera predeterminada. El control principal de esta pantalla es un formulario de presentación denominado **DetailForm1**. **DetailForm1** contiene otros controles, como **DataCard1** (un control de tarjeta, que muestra la categoría de preguntas en este caso). En la pantalla también hay controles independientes, como **IconEdit1** (un control de icono; haga clic en él o púlselo para editar el elemento actual en la pantalla de edición o creación).

![Pantalla de detalles con controles](./media/learning-case-app-explore-controls/details-screen.png)

Hay muchas opciones en la galería, pero los formularios son más sencillos, ya que solo se puede elegir entre un formulario de edición o un formulario de presentación.

![Opciones de formulario de PowerApps](./media/learning-case-app-explore-controls/forms.png)

## <a name="explore-the-editcreate-screen"></a>Explorar la pantalla de edición o creación
La tercera pantalla de la aplicación es la pantalla de edición o creación, denominada **EditScreen1** de forma predeterminada. El control principal de esta pantalla es un formulario de edición denominado **EditForm1**. **EditForm1** contiene otros controles, como **DataCard8** (un control de tarjeta, que permite editar la categoría de preguntas en este caso). En la pantalla también hay controles independientes, como **IconAccept1** (un control de icono; haga clic en él o púlselo para guardar los cambios realizados en la pantalla de edición o creación).

![Pantalla de edición con controles](./media/learning-case-app-explore-controls/edit-screen.png)

Ahora que tiene una idea de las pantallas y los controles que componen la aplicación, en el siguiente tema veremos cómo personalizarla.

