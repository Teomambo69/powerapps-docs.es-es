En esta sección del curso, vamos a crear una aplicación a partir de la lista de SharePoint "Flooring Estimates". Esta aplicación la podría usar, por ejemplo, un comercial para realizar una estimación in-situ, para poder hacer referencia a la lista y mantenerla actualizada. En la sección Introducción, ya le mostramos cómo generar una aplicación a partir de esa lista. ¿Por qué tenemos que verlo otra vez? Primero, en lugar de empezar en PowerApps Studio, ahora le mostraremos cómo se integra PowerApps en SharePoint Online. En segundo lugar, veremos con más detalle cómo ensamblar y personalizar la aplicación. En esta sección recibirá información nueva, así que vamos a comenzar.

## <a name="generate-the-app"></a>Generar la aplicación
La siguiente imagen muestra la lista de SharePoint "Flooring Estimates", que contiene información básica como el nombre, el precio y una imagen para cada tipo de suelo. Puede ver cómo se integran PowerApps y Microsoft Flow en SharePoint Online, lo que permite compilar fácilmente aplicaciones y los flujos a partir de listas.

![Lista Flooring Estimates](./media/learning-spo-app-generate/flooring-estimates-list.png)

Para crear una aplicación, haga clic en **PowerApps** y en **Crear una aplicación**. En el panel derecho, escriba un nombre para la aplicación y haga clic en **Crear**. Después de hacer clic en **Crear**, PowerApps empieza a generar la aplicación. PowerApps hace todo tipo de inferencias sobre los datos para poder generar una aplicación útil como punto de partida.

![Generar una aplicación a partir de una lista](./media/learning-spo-app-generate/generate-app.png)

## <a name="view-the-app-in-powerapps-studio"></a>Ver la aplicación en PowerApps Studio
La nueva aplicación de tres pantallas se abre en PowerApps Studio. Todas las aplicaciones que se generan a partir de datos tienen el mismo conjunto de pantallas:

* La pantalla **Examinar**: donde puede examinar, ordenar, filtrar y actualizar los datos que se extraigan de la lista, así como agregar elementos solo con hacer clic en el icono (+).
* La pantalla **Detalles**: donde puede obtener información más detallada sobre un elemento y decidir si lo elimina o lo edita.
* La pantalla **Editar o crear**: donde puede editar un elemento existente o crear uno nuevo.

En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.

![Alternancia de las vistas](./media/learning-spo-app-generate/toggle-view.png)

Haga clic o pulse en las miniaturas para ver los controles en la pantalla correspondiente.

![La aplicación generada](./media/learning-spo-app-generate/generate-finished-app.png)

## <a name="run-the-app-in-preview-mode"></a>Ejecutar la aplicación en modo de vista previa
Haga clic o pulse ![Flecha Iniciar vista previa de aplicación](./media/learning-spo-app-generate/f5-arrow-sm.png) en la esquina superior derecha para ejecutar la aplicación. Si se desplaza por la aplicación, verá que incluye todos los datos de la lista y proporciona una buena experiencia predeterminada.

![Ejecutar la aplicación en modo de vista previa](./media/learning-spo-app-generate/generate-run-app.png)

Después, exploraremos la aplicación con más detalle y la personalizaremos para que se adapte mejor a nuestras necesidades.

