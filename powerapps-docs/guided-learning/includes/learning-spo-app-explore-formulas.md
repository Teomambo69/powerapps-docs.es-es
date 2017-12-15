Una de las principales ventajas de PowerApps es que no hace falta escribir código de aplicación tradicional (no es preciso ser programador para crear aplicaciones). Pero se necesita una forma de expresar la lógica de una aplicación y controlar la navegación, el filtrado, la ordenación y otras funcionalidades de una aplicación. Aquí es donde entran en juego las fórmulas. Si ha usado fórmulas de Excel, el enfoque que usa PowerApps le resultará familiar. En este tema, se mostrarán un par de fórmulas básicas para dar formato a texto y, después, se explicarán tres de las fórmulas que PowerApps incluye en la aplicación generada. Se hará una idea de lo que pueden hacer las fórmulas. Después puede dedicar un tiempo a examinar otras fórmulas de la aplicación generada y crear las suyas propias.

## <a name="understanding-formulas-and-properties"></a>Descripción de fórmulas y propiedades
En el tema anterior, se incluyó el campo de precio en la galería de la pantalla de exploración, pero se mostraba como un número sin formato y sin símbolo de moneda. Imaginemos que deseamos agregar un signo de dólar y cambiar el color del texto en función del coste del elemento (por ejemplo, rojo si cuesta más de 5 dólares y verde en caso contrario). La siguiente imagen muestra la idea.

![Formato de texto, en lo referente al color y la moneda](./media/learning-spo-app-explore-formulas/text-formatting.png)

Empecemos con el formato de moneda. De manera predeterminada, PowerApps simplemente usa un valor Price para cada elemento, que se establece como la **propiedad** *Texto* de la etiqueta que muestra el precio.

![Formato predeterminado del precio](./media/learning-spo-app-explore-formulas/price-default.png)

Para agregar el símbolo de moneda estadounidense, haga clic o pulse en el control de etiqueta y, en la barra de fórmulas, establezca la propiedad **Texto** en esta fórmula.

![Formato de moneda de precio](./media/learning-spo-app-explore-formulas/price-formatted.png)

La fórmula - `Text(Price, "[$-en-US]$ ##.00"` utiliza la **función** *Text* para especificar cómo debe formatear el número. Esta fórmula es parecida a una de Excel, pero las fórmulas de PowerApps hacen referencia a controles y a otros elementos de la aplicación en lugar de a celdas de una hoja de cálculo. Si hace clic en un control, o lo pulsa, y después hace clic en la lista desplegable de propiedades, o la pulsa, verá una lista de propiedades que son pertinentes para el control. Por ejemplo, esta es una lista parcial de las propiedades de una etiqueta. Algunas de ellas son pertinentes en un amplio conjunto de controles, mientras que otras solo lo son para un control específico.

![Establecimiento de propiedades](./media/learning-spo-app-explore-formulas/properties.png)

Para dar formato el color de manera condicional en función del precio, use una fórmula como la siguiente para la propiedad **Color** de la etiqueta: `If(Price > 5, Color.Red, Color.Green)`.

![Formato de color por precio](./media/learning-spo-app-explore-formulas/color-formatted.png)

## <a name="formulas-included-in-the-generated-app"></a>Fórmulas incluidas en la aplicación generada
Ahora que sabe cómo utilizar las fórmulas en conjunción con propiedades, examinaremos tres ejemplos de fórmulas que PowerApps utiliza en la aplicación generada. Todos los ejemplos son de la pantalla de exploración y funcionan con la propiedad OnSelect, que define lo que sucede cuando un usuario hace clic en un control de la aplicación, o lo pulsa.

* La primera fórmula está asociada con el control **IconNewItem1**: ![Icono Elemento nuevo](./media/learning-spo-app-explore-formulas/icon-add-item.png). Haga clic en este control, o púlselo, para pasar de la pantalla de exploración a la de edición o creación, y crear un elemento. 
  
  * La fórmula es `NewForm(EditForm1);Navigate(EditScreen1, ScreenTransition.None)`
  * La fórmula *crea una instancia de* un nuevo formulario de edición y, después, navega a la pantalla de edición o creación para que pueda crear un elemento nuevo. El valor `ScreenTransition.None` significa que no hay transición entre pantallas (por ejemplo, un fundido).
* La segunda fórmula está asociada con el control **IconSortUpDown1**: ![Icono Ordenar galería](./media/learning-spo-app-explore-formulas/icon-sort.png). Haga clic en este control, o púlselo, para ordenar la lista de elementos de la galería de la pantalla de exploración.
  
  * La fórmula es `UpdateContext({SortDescending1: !SortDescending1})`
  * La fórmula utiliza `UpdateContext` para actualizar una *variable* denominada `SortDescending1`. El valor de la variable se desplaza hacia delante y detrás al hacer clic en el control. Esto indica a la galería de esta pantalla cómo ordenar los elementos (para más información, vea el vídeo). 
* La tercera fórmula está asociada con el control **NextArrow1**: ![Icono de flecha Ir a detalles](./media/learning-spo-app-explore-formulas/icon-arrow.png). Haga clic en este control, o púlselo, para pasar de la pantalla de exploración a la de detalles.
  
  * La fórmula es `Navigate(DetailScreen1, ScreenTransition.None)`
  * La fórmula navega a la pantalla de detalles de nuevo sin transición alguna.

Hay muchas otras fórmulas en la aplicación, por lo se recomienda invertir un tiempo en hacer clic en los controles y ver qué fórmulas están establecidas para las distintas propiedades.

## <a name="wrapping-it-all-up"></a>En resumen
Así llegamos al final de la exploración de la aplicación generada y podemos echar un vistazo a las pantallas, los controles, las propiedades y las fórmulas que confieren a la aplicación sus funcionalidades. Si ha seguido estos pasos, debe conocer mejor el funcionamiento de una aplicación generada, algo que puede aprovechar para crear sus propias aplicaciones. 

Antes de pasar la siguiente sección, queremos volver a SharePoint y mostrarle cómo se integra ahora la aplicación con la experiencia de la lista. Como puede ver, **FlooringApp** ahora funciona como un *vista* de la lista y para iniciar la aplicación, es preciso hacer clic en **Abrir**. Esta es una forma sencilla de administrar las listas con una experiencia personalizada fácil de usar.

![Aplicación como vista de la lista de Sharepoint](./media/learning-spo-app-explore-formulas/list-view.png)

Una vez que ha terminado la sección de la aplicación SharePoint, puede elegir a dónde desea dirigirse:

* [Administración de aplicaciones](../manage-apps#step-1)
* [Generate an app (Common Data Service)](../create-app-cds#step-1) [Generación de una aplicación (Common Data Service)]

La sección de administración muestra cómo compartir y controlar las versiones de las aplicaciones, y presenta los entornos, que son contenedores de aplicaciones, datos y otros recursos. Se recomienda que todos los usuarios lean la sección de administración en algún momento, pero la información que contiene la sección relativa a Common Data Service es excelente e incluye más personalizaciones de las aplicaciones. 

