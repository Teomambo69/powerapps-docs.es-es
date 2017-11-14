Ya está familiarizado con todos los elementos de PowerApps y con las opciones para crear aplicaciones, así que es buen momento para empezar a compilar realmente una aplicación. Para este tema, se generará una aplicación de teléfono a partir de una lista de SharePoint Online, pero puede usar datos de muchos otros orígenes, como Excel, servicios en la nube como Salesforce y orígenes locales como SQL Server.

## <a name="connect-to-a-data-source"></a>Conexión a un origen de datos
El primer paso a la hora de generar una aplicación a partir de datos es elegir qué PowerApps Studio usar y, a continuación, conectarse al origen de datos. En web.powerapps.com, haga clic o pulse en **Nueva aplicación**, a continuación, elija si desea utilizar PowerApps Studio para Windows o PowerApps Studio para web.

![Empezar a trabajar en web.powerapps.com](./media/learning-create-first-app-powerapps/generate-choose-studio.png)

En PowerApps Studio tiene la opción de empezar a partir de datos, de una plantilla o desde el principio. Estamos creando una aplicación de teléfono para una lista de SharePoint, así que en **SharePoint** haga clic o pulse en **Diseño de teléfono**.

![Aplicación de teléfono a partir de una lista de SharePoint](./media/learning-create-first-app-powerapps/generate-sharepoint-phone.png)

Las aplicaciones generadas siempre se basan en una sola lista o tabla (puede agregar más datos a la aplicación más adelante). Las siguientes tres pantallas le guiarán a través del proceso de conexión a la lista **Flooring Estimates** de SharePoint Online.

![Conectarse a una lista de SharePoint Online](./media/learning-create-first-app-powerapps/generate-connect-list.png)

Después de hacer clic en **Conectar**, PowerApps empieza a generar la aplicación. PowerApps hace todo tipo de inferencias sobre los datos para poder generar una aplicación útil como punto de partida.

## <a name="explore-the-generated-app"></a>Exploración de la aplicación generada
Todo correcto. La nueva aplicación de tres pantallas se abre en PowerApps Studio. Todas las aplicaciones que se generan a partir de datos tienen el mismo conjunto de pantallas:

* La pantalla **Examinar**: donde puede examinar, ordenar, filtrar y actualizar los datos que se extraigan de la lista, así como agregar elementos solo con hacer clic en el icono (+).
* La pantalla **Detalles**: donde puede obtener información más detallada sobre un elemento y decidir si lo elimina o lo edita.
* La pantalla **Editar o crear**: donde puede editar un elemento existente o crear uno nuevo.

En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura. 

![Alternancia de las vistas](./media/learning-create-first-app-powerapps/toggle-view.png)

Haga clic o pulse en las miniaturas para ver los controles en la pantalla correspondiente.

![La aplicación generada](./media/learning-create-first-app-powerapps/generate-finished-app.png)

Haga clic o pulse ![Flecha Iniciar vista previa de aplicación](./media/learning-create-first-app-powerapps/f5-arrow-sm.png) en la parte superior derecha para ejecutar la aplicación. Si se desplaza por la aplicación, verá que incluye todos los datos de la lista y proporciona una buena experiencia predeterminada.

Esto fue muy fácil. En unos minutos ha aprendido a conectarse a un origen de datos, generar una aplicación y familiarizarse con PowerApps Studio y con las tres pantallas de aplicación. En secciones posteriores, verá cómo personalizar las aplicaciones generadas. En el siguiente tema se repasará esta sección del curso y se le preparará para futuras lecciones.

