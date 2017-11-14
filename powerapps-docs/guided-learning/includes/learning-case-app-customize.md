En los dos primeros temas de esta sección, se generó una aplicación a partir de una entidad de Common Data Service y se exploró dicha aplicación para conocer mejor la composición de las tres aplicaciones en pantalla. La aplicación que PowerApps generó es útil, pero a menudo las aplicaciones se personalizan después de generarlas. En este tema, explicaremos varios de los cambios de la pantalla de exploración de la aplicación. Puede personalizar cualquiera de las pantallas, pero queríamos centrarnos en una y proporcionar una información más detallada acerca de las personalizaciones. Le animamos a que tome cualquier aplicación que genere (a partir de una entidad, un archivo de Excel o cualquier otro origen) y vea cómo se puede personalizar. Esta es la mejor manera de aprender a combinar aplicaciones.

## <a name="change-gallery-and-data-bindings"></a>Cambios de la galería y los enlaces de datos
Cuando PowerApps genera la aplicación, decide el formato a usar y los campos concretos que aparecerán en cada pantalla. Para esta aplicación vamos a seleccionar un control de galería que incluye una barra de estado que personalizaremos en breve. En el panel derecho, en la pestaña **Diseño**, seleccione el diseño que desee. Los resultados se verán de inmediato, ya que PowerApps actualiza la aplicación en cuanto se realizan los cambios.

![Cambiar el diseño de la pantalla de exploración](./media/learning-case-app-customize/change-layout.png)

Con el diseño básico correcto, cambie los campos que se muestran. Haga clic en un campo del primer elemento, o púlselo, y, después, en el panel derecho, cambie los datos que se muestran en cada elemento. Así se proporciona un mejor resumen de cada elemento de la entidad.

![Cambiar los campos de la pantalla de exploración](./media/learning-case-app-customize/change-browse-fields.png)

## <a name="change-the-app-theme"></a>Cambio del tema de la aplicación
PowerApps proporciona un conjunto de temas que puede utilizar en la aplicación de forma muy parecida a PowerPoint. En la siguiente pantalla, verá que se ha aplicado el tema **Dune** y que se ha pegado un logotipo sencillo en la aplicación. Estos son cambios básicos, pero se puede hacer mucho para mejorar el aspecto de la aplicación. 

![Cambiar el tema y agregar un logotipo](./media/learning-case-app-customize/change-theme.png)

## <a name="use-a-formula-to-show-the-case-status"></a>Uso de una fórmula para mostrar el estado del caso
Una de las principales ventajas de PowerApps es que no hace falta escribir código de aplicación tradicional (no es preciso ser programador para crear aplicaciones). Pero se necesita una forma de expresar la lógica de una aplicación y controlar la navegación, el filtrado, la ordenación y otras funcionalidades de una aplicación. Aquí es donde entran en juego las fórmulas.

Si ha usado fórmulas de Excel, el enfoque que usa PowerApps le resultará familiar. Imagine que desea mostrar la barra de estado en verde si se resuelve un caso o, de lo contrario, en rojo. Para ello, seleccione el control de estado en la pantalla y, a continuación, establezca la propiedad **Fill** de ese control en esta fórmula en la barra de fórmulas: `If(Status="Resolved", Color.Green, Color.Red)`. Esto es parecido a una fórmula de Excel, pero las fórmulas de PowerApps hacen referencia a controles y a otros elementos de la aplicación en lugar de a celdas de una hoja de cálculo. La siguiente imagen muestra dónde se establecerá la fórmula y el resultado en la aplicación.

![Fórmula para mostrar el estado del caso](./media/learning-case-app-customize/case-status.png)

## <a name="sort-and-filter-based-on-date"></a>Ordenar y filtrar según la fecha
En la pantalla de exploración, la aplicación generada le permite buscar los casos y ordenar la lista de elementos de la galería. Vamos a quitar la funcionalidad de búsqueda y ordenación y, en su lugar, mostraremos los casos según una fecha. Puede combinar estos métodos, pero nos centraremos en el enfoque basado en la fecha para esta aplicación. En la imagen siguiente puede ver los elementos que hemos agregado:

* Una etiqueta de texto ("Mostrar casos después de:") para que los usuarios sepan qué hacer: **Insertar** > **Texto** > **Etiqueta**. Cambie la fórmula de **Relleno** a **Blanco**.
* Un selector de fecha: **Insertar** > **Controles** > **Selector de fecha**.
* Una fórmula que conecta la propiedad **Items** de la galería de exploración con el selector de fecha: `Filter(Case, DatePicker1.SelectedDate < LastModifiedDateTime)`.

La fecha se establece en el 20 de octubre y, como resultado, puede ver que la aplicación muestra los casos que se crearon después de esta fecha. Tenga en cuenta que, de forma predeterminada, todos los casos de la entidad tienen la misma fecha de última modificación. Puede actualizar una o varias de ellas para ver cómo funciona el filtrado. El trabajo con datos de la entidad se explica más adelante en el curso.

![Aplicación actualizada para usar el selector de datos](./media/learning-case-app-customize/date-picker.png)

## <a name="show-total-number-of-cases"></a>Exposición del número total de casos
Se está abarcando mucha información en este tema, pero ya casi hemos terminado con las personalizaciones. Lo último que vamos a hacer en este tema es agregar etiquetas que muestran dos números: el número total de casos y el número de casos que coinciden con el filtro basado en fecha.

![Mostrar los casos totales y los filtrados](./media/learning-case-app-customize/number-cases.png)

El vídeo describe detalladamente cómo agregar las dos etiquetas, pero estos son los datos básicos de las propiedades que establecemos para cada una de ellas:

* **Alineación** = `Center`
* **Ancho** = `Parent.Width/2`
* **Texto** del cuadro izquierdo  = `"Total cases: " & CountRows(Case)`. Este incluye todos los casos que se encuentran en la entidad. 
* **Texto** del cuadro derecho  = `Filtered cases: " & CountRows(BrowseGallery1.AllItems)`. Este incluye solo los casos que coinciden con el filtro según la fecha.

Esto resume todo lo relacionado con la personalización de aplicaciones. En el tema siguiente se agregará un origen de datos y un flujo y se mostrará la aplicación finalizada.

