---
title: Búsqueda de una propiedad | Microsoft Docs
description: Busque una propiedad por control, por categoría o por orden alfabético.
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/17/2016
ms.author: gregli
ms.openlocfilehash: 8d54c632780ac827704535af5d24881685a0e518
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "34583610"
---
# <a name="controls-and-properties-in-powerapps"></a>Controles y propiedades en PowerApps
Para configurar la apariencia y el comportamiento de un control es preciso establecer una de sus propiedades. Cada tipo de control tiene un conjunto de propiedades diferente. Algunas propiedades, como **Alto** y **Ancho**, son comunes a casi todos los tipos de controles, pero otras, como **TamañoDeCasilla**, son específicas de un tipo de control.

## <a name="controls"></a>Controles
**[Agregar imagen](controls/control-add-picture.md)**: cargue imágenes desde el dispositivo local, para cargarlas en un origen de datos.

**[Datos adjuntos](controls/control-attachments.md)**: cargue y descargue archivos desde el dispositivo local a un origen de datos.

**[Audio](controls/control-audio-video.md)**: reproduzca un clip de audio o la parte de audio de un clip de vídeo.

**[Escáner de código de barras (experimental)](controls/control-barcodescanner.md)**: escanee un código de barras mediante un dispositivo que tiene una cámara.

**[Botón](controls/control-button.md)**: interactúe con la aplicación haciendo clic en él o pulsándolo.

**[Cámara](controls/control-camera.md)**: haga fotos y guárdelas en la aplicación o en un origen de datos.

**[Tarjeta](controls/control-card.md)**: muestre y edite un campo individual de un registro en un control de un **[formulario de edición](controls/control-form-detail.md)** o **[formulario de presentación](controls/control-form-detail.md)**.

**[Casilla](controls/control-check-box.md)**: active o desactive una opción para especificar **true** o **false**.

**[Gráfico de columnas](controls/control-column-line-chart.md)**: muestre los valores en forma de barras verticales en relación a dos ejes.

**[Columna](controls/control-column.md)**: proporciona la representación de un solo campo en un control [**Tabla de datos**](controls/control-data-table.md).

**[Cuadro combinado](controls/control-combo-box.md)**: permite a los usuarios seleccionar entre las opciones proporcionadas. Admite tanto la búsqueda como la selección múltiple.

**[Tabla de datos](controls/control-data-table.md)**: muestre datos en formato tabular.

**[Selector de fecha](controls/control-date-picker.md)**: especifique una fecha haciendo clic en él o pulsándolo.

**[Mostrar formulario](controls/control-form-detail.md)**: muestre los registros de un origen de datos mediante un formulario.

**[Desplegable](controls/control-drop-down.md)**: muestre el primer elemento de una lista hasta que se selecciona un botón de contenido adicional.

**[Formulario de edición](controls/control-form-detail.md)**: edite y cree registros en un origen de datos mediante un formulario.

**[Formulario de entidad](entity-form-control.md)** (característica experimental): agregue formularios dinámicos en el que los usuarios puedan ver datos relacionales de Common Data Service, editarlos y navegar por ellos.

**[Exportar](controls/control-export-import.md)** : exporte datos para usarlos en cualquier otro lugar de PowerApps.

**[Galería](controls/control-gallery.md)**: muestre una lista de los registros que pueden contener varios tipos de datos.

**[Texto HTML](controls/control-html-text.md)**: convierta automáticamente las etiquetas HTML.

**[Icono](controls/control-shapes-icons.md)**: agregue un gráfico atractivo y aumente el interés visual.

**[Imagen](controls/control-image.md)**: muestre una imagen de, por ejemplo, un archivo local o un origen de datos.

**[Importar](controls/control-export-import.md)**: importe datos de cualquier otro lugar de PowerApps.

**[Gráfico de líneas](controls/control-column-line-chart.md)**: muestre los valores en forma de puntos de datos en relación a dos ejes.

**[Cuadro de lista](controls/control-list-box.md)**: seleccione uno o varios elementos de una lista.

**[Micrófono](controls/control-microphone.md)**: grabe y guarde sonidos en la aplicación o en un origen de datos.

**[Visor de PDF (experimental)](controls/control-pdf-viewer.md)**: muestre el contenido de un archivo PDF en Internet.

**[Entrada manuscrita](controls/control-pen-input.md)**: dibuje una imagen o escriba texto y guárdelo en la aplicación o en un origen de datos.

**[Gráfico circular](controls/control-pie-chart.md)**: muestre la relación de los valores entre sí.

**[Icono de Power BI](controls/control-power-bi-tile.md)**: mostrar un icono de Power BI dentro de una aplicación.

**[Radio](controls/control-radio.md)** : muestre opciones que se excluyen mutuamente.

**[Clasificación](controls/control-rating.md)**: indique un valor entre 1 y un número especificado.

**[Editor de texto enriquecido (experimental)](controls/control-richtexteditor.md)**: permite a los usuarios de la aplicación aplicar formato de texto enriquecido.

**[Pantalla](controls/control-screen.md)**: muestre y actualice los datos sobre una tarea específica.

**[Forma](controls/control-shapes-icons.md)**: muestre flechas y formas geométricas, como rectángulos.

**[Control deslizante](controls/control-slider.md)**: especifique un valor arrastrando un controlador.

**[Etiqueta](controls/control-text-box.md)**: muestre datos como texto, números, fechas o moneda.

**[Entrada de texto](controls/control-text-input.md)**: escriba texto, números y otros datos.

**[Temporizador](controls/control-timer.md)**: configure la aplicación para que responda cuando transcurra un período concreto.

**[Alternancia](controls/control-toggle.md)**: arrastre un cuadro para especificar **true** o **false**.

**[Vídeo](controls/control-audio-video.md)**: reproduzca un clip de vídeo de un archivo local, un origen de datos o YouTube.

## <a name="common-properties-by-category"></a>Propiedades comunes por categoría
**[Color y borde](controls/properties-color-border.md)**: configure el color y borde de un control que puede cambiar cuando un usuario interactúa con él.

**[Núcleo](controls/properties-core.md)**: configure si el usuario puede ver un control e interactuar con él.

**[Imagen](controls/properties-visual.md)**: configure qué imagen se muestra y cómo rellena el control.

**[Tamaño y ubicación](controls/properties-size-location.md)**: configure el tamaño de un control (o un elemento de un control) y dónde se encuentra en relación con la pantalla en la que está.

**[Texto](controls/properties-text.md)**: configure la apariencia del texto en los controles, como las características de la fuente, la alineación y el alto de línea.  

## <a name="all-properties"></a>Todas las propiedades
### <a name="a"></a>A
**[ActualZoom](controls/control-pdf-viewer.md)**: el zoom real del control, que puede diferir del zoom solicitado con la propiedad **Zoom**.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[Align](controls/properties-text.md)**: la ubicación del texto respecto al centro horizontal de su control.  Se aplica a muchos controles.

**[TodosLosElementos](controls/control-gallery.md)**: todos los elementos de una galería, entre los que se incluyen valores de control adicionales que formen parte de la plantilla de la galería.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**AutoDisableOnSelect**: deshabilita automáticamente el control mientras se ejecuta el comportamiento AlSeleccionar.  Se aplica a los controles **[Botón](controls/control-button.md)** e **[Imagen](controls/control-image.md)**.

**[AutoHeight](controls/properties-size-location.md)** (AlturaAutomática): indica si una etiqueta aumenta automáticamente su altura si su propiedad **[Texto](controls/properties-core.md)** contiene más caracteres de los que el control permite mostrar. Se aplica al control **[Etiqueta](controls/control-text-box.md)**.

**PausarAutomáticamente**: indica si un clip de audio o vídeo se detiene automáticamente si el usuario se desplaza a otra pantalla.  Se aplica a los controles **[Audio](controls/control-audio-video.md)**, **[Temporizador](controls/control-timer.md)** y **[Vídeo](controls/control-audio-video.md)**.

**IniciarAutomáticamente**: indica si un control de audio o vídeo empieza a reproducir automáticamente un clip cuando el usuario navega a la pantalla que contiene ese control.  Se aplica a los controles **[Audio](controls/control-audio-video.md)**, **[Temporizador](controls/control-timer.md)** y **[Vídeo](controls/control-audio-video.md)**.

### <a name="b"></a>B
**[ImagenDeFondo](controls/properties-visual.md)**: nombre de un archivo de imagen que aparece en el fondo de una pantalla.  Se aplica al control **[Pantalla](controls/control-screen.md)**.

**[BorderColor](controls/properties-color-border.md)**: el color de un borde del control.  Se aplica a muchos controles.

**[BorderStyle](controls/properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.  Se aplica a muchos controles.

**[BorderThickness](controls/properties-color-border.md)**: el grosor de un borde del control.  Se aplica a muchos controles.

**[Brillo](controls/control-camera.md)**: la claridad que el usuario es probable que perciba en una imagen.  Se aplica al control **[Cámara](controls/control-camera.md)**.

### <a name="c"></a>C
**[CalculateOriginalDimensions](controls/control-image.md)**: habilita las propiedades **[AltoOriginal](controls/control-image.md)** y **[AnchoOriginal](controls/control-image.md)**.  Se aplica al control **[Imagen](controls/control-image.md)**.

**[Cámara](controls/control-camera.md)**: en los dispositivos que tienen más de una cámara, el identificador numérico de la cámara que usa la aplicación.  Se aplica al control **[Cámara](controls/control-camera.md)**.

**[CheckboxBackgroundFill](controls/control-check-box.md)** (RellenoDeFondoDeCasilla): el color de fondo del cuadro que rodea la marca de verificación en un control de casilla.  Se aplica al control **[Casilla](controls/control-check-box.md)**.

**[CheckboxBorderColor](controls/control-check-box.md)**: el color del borde que rodea la marca de verificación en un control de casilla.  Se aplica al control **[Casilla](controls/control-check-box.md)**.

**[TamañoDeCasilla](controls/control-check-box.md)**: el ancho y alto del cuadro que rodea la marca de verificación en un control de casilla.  Se aplica al control **[Casilla](controls/control-check-box.md)**.

**[CheckmarkFill](controls/control-check-box.md)**: el color de la marca de verificación en un control de casilla.  Se aplica al control **[Casilla](controls/control-check-box.md)**.

**[ChevronBackground](controls/control-drop-down.md)**: el color detrás de la flecha hacia abajo en una lista desplegable.  Se aplica al control **[Desplegable](controls/control-drop-down.md)**.

**[ChevronFill](controls/control-drop-down.md)**: el color de la flecha hacia abajo en una lista desplegable.  Se aplica al control **[Desplegable](controls/control-drop-down.md)**.

**[Clear](controls/control-text-input.md)**: si un control de entrada de texto muestra una "X" que el usuario puede pulsar o hacer clic para borrar el contenido del control.  Se aplica al control **[Entrada de texto](controls/control-text-input.md)**.

**[Color](controls/properties-color-border.md)**: el color del texto en un control.  Se aplica a muchos controles.

**[Contraste](controls/control-camera.md)**: indica cómo el usuario puede distinguir fácilmente colores similares en una imagen.  Se aplica al control **[Cámara](controls/control-camera.md)**.

**[CurrentFindText](controls/control-pdf-viewer.md)**: el término de búsqueda que está en uso en ese momento.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[CurrentPage](controls/control-pdf-viewer.md)**: el número de la página de un archivo PDF que se muestra realmente.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

### <a name="d"></a>D
**[Data](controls/control-export-import.md)**: el nombre de una colección que desea exportar a un archivo local.  Se aplica al control **[Exportar](controls/control-export-import.md)**.

**[DataField](controls/control-card.md)**: el nombre del campo de un registro que esta tarjeta muestra y edita.  Se aplica al control **[Tarjeta](controls/control-card.md)**.

**[DataSource](controls/control-form-detail.md)**: el origen de datos que contiene el registro que el usuario mostrará, editará o creará.  Se aplica a los controles **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)**.

**[Predeterminado](controls/properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.  Se aplica a muchos controles.

**[DefaultDate](controls/control-date-picker.md)**: el valor inicial de un control de fecha antes de que lo cambie el usuario.  Se aplica al control **[Selector de fecha](controls/control-date-picker.md)**.

**[DefaultMode](controls/control-form-detail.md)**: el modo inicial de un control de formulario, ya sea **Edit**, **New** o **View**.  Se aplica al control **[Formulario de edición](controls/control-form-detail.md)**.

**[Dirección](controls/control-gallery.md)**: indica si el primer elemento de una galería con orientación horizontal aparece cerca del borde izquierdo o derecho.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**[Disabled](controls/properties-core.md)**: indica si el usuario puede interactuar con el control.  Se aplica a muchos controles.

**[DisabledBorderColor](controls/properties-color-border.md)**: el color de un borde del control si la propiedad **[Disabled](controls/properties-core.md)** del control está establecida en **true**.  Se aplica a muchos controles.

**[DisabledColor](controls/properties-color-border.md)**: el color del texto en un control si su propiedad **[Disabled](controls/properties-core.md)** está establecida en **true**.  Se aplica a muchos controles.

**[DisabledFill](controls/properties-color-border.md)**: el color de fondo de un control si su propiedad **[Disabled](controls/properties-core.md)** está establecida en **true**.  Se aplica a muchos controles.

**[DisplayName](controls/control-card.md)**: el nombre descriptivo de un campo de un origen de datos.  Se aplica al control **[Tarjeta](controls/control-card.md)**.

**[DisplayMode](controls/properties-core.md)**: los valores pueden ser Edit, View o Disabled. Configura si el control permite entradas de usuario (Edit), solo muestra datos (View) o si está deshabilitado (Disabled).

**[Documento](controls/control-pdf-viewer.md)**: la dirección URL, entre comillas dobles, de un archivo PDF.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[Duración](controls/control-timer.md)**: tiempo de ejecución del temporizador.  Se aplica al control **[Temporizador](controls/control-timer.md)**.

### <a name="e"></a>E
**[EndYear](controls/control-date-picker.md)**: el último año en el que el usuario puede establecer el valor de un control selector de fecha.  Se aplica al control **[Selector de fecha](controls/control-date-picker.md)**.

**Error**: el significado de esta propiedad depende del control:

* Control **[Agregar imagen](controls/control-add-picture.md)**: si aparece algún problema al cargar una imagen, esta propiedad contendrá una cadena de error apropiada.
* Control **[Tarjeta](controls/control-card.md)**: el mensaje de error descriptivo que se muestra en este campo cuando se produce un error de validación.
* Control **[Formulario de edición](controls/control-form-detail.md)**: un mensaje de error descriptivo que se muestra en este formulario cuando se produce un error en la función **[SubmitForm](functions/function-form.md)**.

**[ErrorKind](controls/control-form-detail.md)**: si se produce un error durante la ejecución de **SubmitForm**, el tipo de error que se produjo.  Se aplica a los controles **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)**.

**[Seccionar](controls/control-pie-chart.md)**: las distancia entre las cuñas de un gráfico circular.  Se aplica al control **[Gráfico circular](controls/control-pie-chart.md)**.

### <a name="f"></a>F
**[Fill](controls/properties-color-border.md)**: el color de fondo de un control.  Se aplica a muchos controles.

**[FindNext](controls/control-pdf-viewer.md)**: busca la siguiente instancia de **FindText** en el documento.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[FindPrevious](controls/control-pdf-viewer.md)**: busca la instancia anterior de **FindText** en el documento.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[FindText](controls/control-pdf-viewer.md)**: el término que se busca en el documento.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[Font](controls/properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.  Se aplica a muchos controles.

**[FontWeight](controls/properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.  Se aplica a muchos controles.

### <a name="g"></a>G
**[GridStyle](controls/control-column-line-chart.md)**: indica si un gráfico de columnas o de líneas muestra su eje x, su eje, ambos o ninguno.  Se aplica a los controles **[Gráfico de columnas](controls/control-column-line-chart.md)** y **[Gráfico de líneas](controls/control-column-line-chart.md)**.

### <a name="h"></a>H
**[RellenoDeControladorActivo](controls/control-slider.md)**: el color del controlador de un control deslizante cuando el usuario cambia el valor.  Se aplica al control **[Control deslizante](controls/control-slider.md)**.

**[RellenoDeControlador](controls/control-slider.md)**: el color del controlador (el elemento que cambia de posición) en un control de alternancia o control deslizante.  Se aplica al control **[Control deslizante](controls/control-slider.md)**.

**[RellenoDeControladorAlMantener](controls/control-slider.md)**: el color del texto del controlador cuando el usuario mantiene el puntero sobre él.  Se aplica al control **[Control deslizante](controls/control-slider.md)**.

**[Height](controls/properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.  Se aplica a muchos controles.

**[TextoDeSugerencia](controls/control-text-input.md)**: texto de color gris claro que aparece en un control de entrada de texto si está en blanco.  Se aplica al control **[Entrada de texto](controls/control-text-input.md)**.

**[HoverBorderColor](controls/properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.  Se aplica a muchos controles.

**[HoverColor](controls/properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.  Se aplica a muchos controles.

**[HoverFill](controls/properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.  Se aplica a muchos controles.

**[Texto HTML](controls/control-html-text.md)**: texto que aparece en un control de texto HTML y que puede contener etiquetas HTML.  Se aplica al control **[Texto HTML](controls/control-html-text.md)**.

### <a name="i"></a>I
**[Imagen](controls/properties-visual.md)**: el nombre de la imagen que aparece en un control de imagen, audio o micrófono.  Se aplica a los controles **[Audio](controls/control-audio-video.md)**, **[Image](controls/control-image.md)**, **[Microphone](controls/control-microphone.md)** y **[Video](controls/control-audio-video.md)**.

**[PosiciónDeLaImagen](controls/properties-visual.md)**: posición (**Rellenar**, **Ajustar**, **Estirar**, **Icono** o **Centrar**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.  Se aplica a muchos controles.

**[Input](controls/control-pen-input.md)**: entrada.  Se aplica al control **[Entrada manuscrita](controls/control-pen-input.md)**.

**[Italic](controls/properties-text.md)**: indica si el texto de un control está en cursiva.  Se aplica a muchos controles.

**[Elemento](controls/control-form-detail.md)**: el registro en el **origen de datos** que el usuario mostrará o editará.  Se aplica a los controles **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)**.

**[ItemBorderColor](controls/control-pie-chart.md)**: el color del borde que rodea cada cuña de un gráfico circular.  Se aplica al control **[Gráfico circular](controls/control-pie-chart.md)**.

**[ItemBorderThickness](controls/control-pie-chart.md)**: el grosor del borde que rodea cada cuña de un gráfico circular.  Se aplica al control **[Gráfico circular](controls/control-pie-chart.md)**.

**ItemColorSet**: color de cada punto de datos de un gráfico.  Se aplica a los controles **[Gráfico de columnas](controls/control-column-line-chart.md)**, **[Gráfico de líneas](controls/control-column-line-chart.md)** y **[Gráfico circular](controls/control-pie-chart.md)**.

**[ItemPaddingLeft](controls/control-list-box.md)**: la distancia entre el texto de un cuadro de lista y su borde izquierdo.  Se aplica al control **[Cuadro de lista](controls/control-list-box.md)**.

**[Elementos](controls/properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.  Se aplica a muchos controles.

**[ItemsGap](controls/control-column-line-chart.md)**: la distancia entre las columnas de un gráfico de columnas.  Se aplica al control **[Gráfico de columnas](controls/control-column-line-chart.md)**.

### <a name="l"></a>Grande
**[LabelPosition](controls/control-pie-chart.md)**: ubicación de las etiquetas en un gráfico circular con respecto a sus cuñas.  Se aplica al control **[Gráfico circular](controls/control-pie-chart.md)**.

**[LastSubmit](controls/control-form-detail.md)**: el último registro enviado correctamente, incluidos todos los campos que ha generado el servidor.  Se aplica al control **[Formulario de edición](controls/control-form-detail.md)**.

**Layout**: indica si el usuario se desplaza por la galería o ajusta un control deslizante de arriba a abajo (**Vertical**) o de izquierda a derecha (**Horizontal**).  Se aplica a los controles **[Galería](controls/control-gallery.md)** y **[Control deslizante](controls/control-slider.md)**.

**[AlturaDeLínea](controls/properties-text.md)**: distancia entre, por ejemplo, líneas de texto o elementos de una lista.  Se aplica a los controles **[Cuadro de lista](controls/control-list-box.md)**, **[Botón de selección](controls/control-radio.md)**, **[Etiqueta](controls/control-text-box.md)** y **[Entrada de texto](controls/control-text-input.md)**.

**[Bucle](controls/control-audio-video.md)**: indica si un clip de audio o de vídeo empieza de nuevo automáticamente en cuanto termina de reproducirse.  Se aplica a los controles **[Audio](controls/control-audio-video.md)** y **[Vídeo](controls/control-audio-video.md)**.

### <a name="m"></a>Mediana
**[Marcadores](controls/control-column-line-chart.md)**: indica si un gráfico de columnas o de líneas muestra el valor de cada punto de datos.  Se aplica a los controles **[Gráfico de columnas](controls/control-column-line-chart.md)** y **[Gráfico de líneas](controls/control-column-line-chart.md)**.

**[MarkerSuffix](controls/control-column-line-chart.md)**: texto que aparece después de cada valor en un gráfico de columnas en el que la propiedad **[Marcadores](controls/control-column-line-chart.md)** está establecida en **true**.  Se aplica al control **[Gráfico de columnas](controls/control-column-line-chart.md)**.

**Max**: el valor máximo para el que el usuario puede establecer un control deslizante o una clasificación.  Se aplica a los controles **[Clasificación](controls/control-rating.md)** y **[Control deslizante](controls/control-slider.md)**.

**[MaxLength](controls/control-text-input.md)**: el número de caracteres que el usuario puede escribir en un control de entrada de texto.  Se aplica al control **[Entrada de texto](controls/control-text-input.md)**.

**Multimedia**: un identificador de la secuencia que reproduce un control de audio o de vídeo.  Se aplica a los controles **[Agregar imagen](controls/control-add-picture.md)**, **[Audio](controls/control-audio-video.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[Micrófono](controls/control-microphone.md)**: en un dispositivo que tenga varios micrófonos, el identificador numérico del micrófono que usa la aplicación.  Se aplica al control **[Micrófono](controls/control-microphone.md)**.

**[Mín](controls/control-slider.md)**: el valor mínimo para el que el usuario puede establecer un control deslizante.  Se aplica al control **[Control deslizante](controls/control-slider.md)**.

**[AnchoDeBarraMínimo](controls/control-column-line-chart.md)**: el ancho mínimo posible de las columnas de un gráfico de columnas.  Se aplica al control **[Gráfico de columnas](controls/control-column-line-chart.md)**.

**Mode**: el significado de esta propiedad depende del control:

* Control **[Formulario de edición](controls/control-form-detail.md)**: el control está en modo **Edición** o **Nuevo**.
* Control **[Entrada manuscrita](controls/control-pen-input.md)**: el control está en los modos **Dibujar**, **Borrar** o **Selección**.
* Control **[Entrada de texto](controls/control-text-input.md)**: el control se encuentra en modo **LíneaÚnica**, **Multilínea** o **Contraseña**.

### <a name="n"></a>N
**[PasoDeNavegación](controls/control-gallery.md)**: lo lejos que se desplaza una galería si su propiedad **[MostrarNavegación](controls/control-gallery.md)** está establecida en **true** y el usuario selecciona una flecha de navegación de cualquier extremo de esa galería.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**[NúmeroDeSeries](controls/control-column-line-chart.md)**: el número de columnas de datos reflejadas en un gráfico de columnas o de líneas.  Se aplica a los controles **[Gráfico de columnas](controls/control-column-line-chart.md)** y **[Gráfico de líneas](controls/control-column-line-chart.md)**.

### <a name="o"></a>O
**[AlCambiar](controls/properties-core.md)**: el comportamiento de una aplicación cuando el usuario cambia el valor de un control (por ejemplo, al ajustar un control deslizante).  Se aplica a muchos controles.

**AlActivar**: el comportamiento de una aplicación cuando el valor de una casilla o de un control Alternar cambia a **true**.  Se aplica a los controles **[Casilla](controls/control-check-box.md)** y **[Alternancia](controls/control-toggle.md)**.

**[AlFinalizar](controls/control-audio-video.md)**: el comportamiento de una aplicación cuando finaliza la reproducción de un clip de audio o de vídeo.  Se aplica a los controles **[Audio](controls/control-audio-video.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[OnFailure](controls/control-form-detail.md)** (ConError): el comportamiento de una aplicación cuando una operación de datos ha sido incorrecta.  Se aplica al control **[Formulario de edición](controls/control-form-detail.md)**.

**[AlEstarOculto](controls/control-screen.md)**: el comportamiento de una aplicación cuando el usuario navega fuera de una pantalla.  Se aplica al control **[Pantalla](controls/control-screen.md)**.

**[AlPausar](controls/control-audio-video.md)**: el comportamiento de una aplicación cuando el usuario pausa el clip que reproduce un control de audio o de vídeo.  Se aplica a los controles **[Audio](controls/control-audio-video.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[OnReset](controls/control-form-detail.md)** (AlRestablecer): el comportamiento de una aplicación cuando se restablece un control **[Formulario de edición](controls/control-form-detail.md)**.  Se aplica al control **[Formulario de edición](controls/control-form-detail.md)**.

**[AlSeleccionar](controls/properties-core.md)**: el comportamiento de una aplicación cuando el usuario pulsa o hace clic en un control.  Se aplica a muchos controles.

**AlIniciar**: el comportamiento de una aplicación cuando el usuario la abre o comienza a grabar con un control de micrófono. Se aplica a los controles **[Audio](controls/control-audio-video.md)**, **[Micrófono](controls/control-microphone.md)**, **[Pantalla](controls/control-screen.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[OnStateChange](controls/control-pdf-viewer.md)** (AlCambiarEstado): el comportamiento de una aplicación cuando cambia el estado del control. Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[AlDetener](controls/control-microphone.md)**: el comportamiento de una aplicación cuando el usuario detiene la grabación con un control de micrófono. Se aplica al control **[Micrófono](controls/control-microphone.md)**.

**[EnSecuencia](controls/control-camera.md)**: el comportamiento de una aplicación cuando se actualiza la propiedad  **[Secuencia](controls/control-camera.md)**.  Se aplica al control **[Cámara](controls/control-camera.md)**.

**[OnSuccess](controls/control-form-detail.md)** (ConResultadoCorrecto): el comportamiento de una aplicación cuando una operación de datos ha sido correcta.  Se aplica al control **[Formulario de edición](controls/control-form-detail.md)**.

**[AlFinalizarTemporizador](controls/control-timer.md)**: el comportamiento de una aplicación cuando se termina de ejecutar un temporizador.  Se aplica al control **[Temporizador](controls/control-timer.md)**.

**[AlIniciarTemporizador](controls/control-timer.md)**: el comportamiento de una aplicación cuando se empieza a ejecutar un temporizador.  Se aplica al control **[Temporizador](controls/control-timer.md)**.

**AlDesactivar**: el comportamiento de una aplicación cuando el valor de una casilla o de un control Alternar cambia a **false**.  Se aplica a los controles **[Casilla](controls/control-check-box.md)** y **[Alternancia](controls/control-toggle.md)**.

**[AlEstarVisible](controls/control-screen.md)**: el comportamiento de una aplicación cuando el usuario navega a una pantalla.  Se aplica al control **[Pantalla](controls/control-screen.md)**.

**[AltoOriginal](controls/control-image.md)**: el alto original de una imagen, habilitada con la propiedad **[CalculateOriginalDimensions](controls/control-image.md)**.  Se aplica al control **[Imagen](controls/control-image.md)**.

**[AnchoOriginal](controls/control-image.md)**: el ancho original de una imagen, habilitada con la propiedad **[CalculateOriginalDimensions](controls/control-image.md)**.  Se aplica al control **[Imagen](controls/control-image.md)**.

**[Desbordamiento](controls/control-text-box.md)**: indica si aparece una barra de desplazamiento en una etiqueta si su propiedad **[Wrap](controls/control-text-box.md)** (Ajuste) está establecida en **verdadero** y el valor de la propiedad **[Texto](controls/properties-core.md)** del control contiene más caracteres de los que el control permite mostrar a la vez.  Se aplica al control **[Etiqueta](controls/control-text-box.md)**.

### <a name="p"></a>P
**[Padding](controls/properties-size-location.md)**: la distancia entre el texto de un botón Exportar o Importar y los bordes de ese botón.  Se aplica a los controles **[Add picture](controls/control-add-picture.md)**, **[Export](controls/control-export-import.md)** y **[Import](controls/control-export-import.md)**.

**[RellenoInferior](controls/properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.  Se aplica a muchos controles.

**[RellenoIzquierdo](controls/properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.  Se aplica a muchos controles.

**[RellenoDerecho](controls/properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.  Se aplica a muchos controles.

**[RellenoSuperior](controls/properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.  Se aplica a muchos controles.

**[Página](controls/control-pdf-viewer.md)**: el número de la página que desea mostrar.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[PageCount](controls/control-pdf-viewer.md)**: el número de páginas de un documento.  Se aplica al control **[Visor de PDF](controls/control-pdf-viewer.md)**.

**[Paused](controls/control-audio-video.md)**: *true* si un control de reproducción multimedia está actualmente en pausa; en caso contrario, *false*.  Se aplica a los controles **[Audio](controls/control-audio-video.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[Foto](controls/control-camera.md)**: la imagen que se captura cuando el usuario hace una foto.  Se aplica al control **[Cámara](controls/control-camera.md)**.

**[Presionado](controls/control-button.md)**: *true* mientras se presiona un control; en caso contrario, *false*.  Se aplica al control **[Botón](controls/control-button.md)**.

**[PressedBorderColor](controls/properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.  Se aplica a muchos controles.

**[PressedColor](controls/properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.  Se aplica a muchos controles.

**[PressedFill](controls/properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.  Se aplica a muchos controles.

### <a name="r"></a>R
**[RadioBackgroundFill](controls/control-radio.md)**: el color de fondo de los círculos en un control de botón de radio.  Se aplica al control **[Radio](controls/control-radio.md)**.

**[RadioBorderColor](controls/control-radio.md)**: el color del círculo de cada opción de un control de botón de radio.  Se aplica al control **[Radio](controls/control-radio.md)**.

**[RadioSelectionFill](controls/control-radio.md)**: el color que aparece dentro del círculo de la opción seleccionada en un control de botón de radio.  Se aplica al control **[Radio](controls/control-radio.md)**.

**[TamañoDeBotónDeRadio](controls/control-radio.md)**: el diámetro de los círculos de un control de botón de radio.  Se aplica al control **[Radio](controls/control-radio.md)**.

**[RadiusBottomLeft](controls/properties-size-location.md)**: el grado al que se redondea la esquina inferior izquierda de un control.  Se aplica a muchos controles.

**[RadiusBottomRight](controls/properties-size-location.md)**: el grado al que se redondea la esquina inferior derecha de un control.  Se aplica a muchos controles.

**[RadiusTopLeft](controls/properties-size-location.md)**: el grado al que se redondea la esquina superior izquierda de un control.  Se aplica a muchos controles.

**[RadiusTopRight](controls/properties-size-location.md)**: el grado al que se redondea la esquina superior derecha de un control.  Se aplica a muchos controles.

**RellenoDeRaíl**: color de fondo del rectángulo en un control Alternar cuando su valor es **false** o color de la línea a la derecha del identificador en un control deslizante.  Se aplica a los controles **[Control deslizante](controls/control-slider.md)** y **[Alternancia](controls/control-toggle.md)**.

**RellenoRaílAlMantenerPuntero**: al mantener el puntero sobre un control Alternar o deslizante, color de fondo del rectángulo del primero cuando su valor es **false** o color de la línea a la derecha del identificador del segundo.  Se aplica a los controles **[Control deslizante](controls/control-slider.md)** y **[Alternancia](controls/control-toggle.md)**.

**[RellenoDeClasificación](controls/control-rating.md)**: el color de las estrellas de un control de clasificación.  Se aplica al control **[Clasificación](controls/control-rating.md)**.

**ReadOnly**: indica si un usuario puede cambiar el valor de un control deslizante o el control de clasificación.  Se aplica a los controles **[Clasificación](controls/control-rating.md)** y **[Control deslizante](controls/control-slider.md)**.

**[Repetir](controls/control-timer.md)**: si un temporizador se reinicia automáticamente cuando finaliza la ejecución.  Se aplica al control **[Temporizador](controls/control-timer.md)**.

**[Required](controls/control-card.md)**: indica si una tarjeta, al editar el campo de un origen de datos, debe contener un valor.  Se aplica al control **[Tarjeta](controls/control-card.md)**.

**[Reset](controls/properties-core.md)**: indica si un control vuelve a su valor predeterminado.  Se aplica a muchos controles.  Consulte también la función **[Reset](functions/function-reset.md)**.

### <a name="s"></a>S
**Seleccionados**: el elemento seleccionado.  Se aplica a los controles **[Desplegable](controls/control-drop-down.md)** y **[Galería](controls/control-gallery.md)**.

**[SelectedDate](controls/control-date-picker.md)**: la fecha seleccionada actualmente en un control de fecha.  Se aplica al control **[Selector de fecha](controls/control-date-picker.md)**.

**[ColorDeSelección](controls/properties-color-border.md)**: color del texto de los elementos seleccionados en una lista o de la herramienta de selección de un control de entrada manuscrita.  Se aplica a los controles **[Desplegable](controls/control-drop-down.md)**, **[Cuadro de lista](controls/control-list-box.md)** y **[Entrada manuscrita](controls/control-pen-input.md)**.

**[RellenoDeSelección](controls/properties-color-border.md)**: el color de fondo de uno o varios elementos seleccionados en una lista o un área seleccionada de un control de entrada manuscrita.  Se aplica a los controles **[Desplegable](controls/control-drop-down.md)** y **[Cuadro de lista](controls/control-list-box.md)**.

**[GrosorDeSelección](controls/control-pen-input.md)**: el grosor de la herramienta de selección de un control de entrada manuscrita.  Se aplica al control **[Entrada manuscrita](controls/control-pen-input.md)**.

**[SelecciónMúltiple](controls/control-list-box.md)**: si un usuario puede seleccionar más de un elemento en un cuadro de lista.  Se aplica al control **[Cuadro de lista](controls/control-list-box.md)**.

**[SeriesAxisMax](controls/control-column-line-chart.md)**: el valor máximo del eje y en un gráfico de columnas o de líneas.  Se aplica al control **[Gráfico de columnas](controls/control-column-line-chart.md)**.

**[SeriesAxisMin](controls/control-column-line-chart.md)**: un número que determina el valor mínimo del eje y de un gráfico de columnas.  Se aplica al control **[Gráfico de columnas](controls/control-column-line-chart.md)**.

**MostrarControles**: indica si se muestra un reproductor de audio o vídeo, por ejemplo, un botón de reproducción y un control deslizante de volumen, y un control de entrada manuscrita muestra, por ejemplo, iconos para dibujar, borrar y borrar todo.  Se aplica a los controles **[Audio](controls/control-audio-video.md)**, **[Visor de PDF](controls/control-pdf-viewer.md)**, **[Entrada manuscrita](controls/control-pen-input.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[ShowLabels](controls/control-pie-chart.md)**: si un gráfico circular muestra el valor asociado a cada una de sus cuñas.  Se aplica al control **[Gráfico circular](controls/control-pie-chart.md)**.

**[MostrarNavegación](controls/control-gallery.md)**: si aparece una flecha en cada extremo de una galería para que un usuario pueda desplazarse por los elementos de la galería haciendo clic en una flecha o pulsando en ella.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**[MostrarBarraDesplazamiento](controls/control-gallery.md)**: si aparece una barra de desplazamiento cuando el usuario mantiene el puntero sobre una galería.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**MostrarValor**: indica si el valor de un control deslizante o una clasificación aparece cuando el usuario cambia ese valor o mantiene el puntero sobre el control.  Se aplica a los controles **[Clasificación](controls/control-rating.md)** y **[Control deslizante](controls/control-slider.md)**.

**[Size](controls/properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.  Se aplica a muchos controles.

**[Ajustar](controls/control-gallery.md)**: si, cuando un usuario se desplaza por una galería, se ajusta automáticamente para que aparezca el siguiente elemento en su totalidad.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**Inicio**: indica si se reproduce un clip de audio o vídeo.  Se aplica a los controles **[Audio](controls/control-audio-video.md)**, **[Temporizador](controls/control-timer.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[HoraDeInicio](controls/control-audio-video.md)**: la hora después del inicio de un clip de audio o de vídeo en que el clip empieza a reproducirse.  Se aplica a los controles **[Audio](controls/control-audio-video.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[StartYear](controls/control-date-picker.md)**: el primer año en el que el usuario puede establecer el valor de un control de selector de fecha.  Se aplica al control **[Selector de fecha](controls/control-date-picker.md)**.

**[Secuencia](controls/control-camera.md)**: la imagen se actualiza automáticamente en la propiedad **[TasaSecuencia](controls/control-camera.md)**.  Se aplica al control **[Cámara](controls/control-camera.md)**.

**[TasaSecuencia](controls/control-camera.md)**: la frecuencia de actualización de la imagen en la propiedad **[Secuencia](controls/control-camera.md)**, en milisegundos.  Este valor puede oscilar entre 100 (1/10 centésimas de segundo) y 3 600 000 (1 hora).  Se aplica al control **[Cámara](controls/control-camera.md)**.

**[Strikethrough](controls/properties-text.md)**: indica si aparece una línea sobre el texto de un control.  Se aplica a muchos controles.

### <a name="t"></a>T
**[RellenoDePlantilla](controls/control-gallery.md)**: el color de fondo de una galería.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**[EspaciadoInternoDePlantilla](controls/control-gallery.md)**: la distancia entre los elementos de una galería.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**[TamañoDePlantilla](controls/control-gallery.md)**: el alto de la plantilla en una galería con orientación vertical o el ancho de la plantilla en una galería con orientación horizontal.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**[Text](controls/properties-core.md)**: texto que aparece en un control o que el usuario escribe en un control.  Se aplica a muchos controles.

**[Time](controls/control-audio-video.md)**: posición actual de un control multimedia.  Se aplica a los controles **[Audio](controls/control-audio-video.md)** y **[Vídeo](controls/control-audio-video.md)**.

**[Información sobre herramientas](controls/properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.  Se aplica a muchos controles.

**[Transición](controls/control-gallery.md)**: el efecto visual (**Emergente**, **Insertar** o **Ninguno**) cuando el usuario mantiene el puntero sobre un elemento de la galería.  Se aplica al control **[Galería](controls/control-gallery.md)**.

**[Transparencia](controls/control-image.md)**: el grado de visibilidad de los controles de detrás de una imagen.  Se aplica al control **[Imagen](controls/control-image.md)**.

### <a name="u"></a>U
**[Underline](controls/properties-text.md)**: indica si aparece una línea debajo del texto de un control.  Se aplica a muchos controles.

**[Sin guardar](controls/control-form-detail.md)**: true si el control **[Formulario de edición](controls/control-form-detail.md)** contiene cambios de usuario que no se guardaron.  Se aplica al control **[Formulario de edición](controls/control-form-detail.md)**.

**[Actualizar](controls/control-card.md)**: el valor que se reescribe en el origen de datos de un campo.  Se aplica al control **[Tarjeta](controls/control-card.md)**.

**[Actualizaciones](controls/control-form-detail.md)**: los valores que se escriben en el origen de datos de un registro cargado en un control de formulario.  Se aplica al control **[Formulario de edición](controls/control-form-detail.md)**.

### <a name="v"></a>V
**Válido**: si un control **[Tarjeta](controls/control-card.md)** o **[Formulario de edición](controls/control-form-detail.md)** contiene entradas válidas listas para enviarse al origen de datos.  Se aplica a los controles **[Tarjeta](controls/control-card.md)** y **[Formulario de edición](controls/control-form-detail.md)**.

**[Valor](controls/properties-core.md)**: el valor de un control de entrada.  Se aplica a los controles **[Casilla](controls/control-check-box.md)**, **[Radio](controls/control-radio.md)**, **[Control deslizante](controls/control-slider.md)** y **[Alternancia](controls/control-toggle.md)**.

**RellenoDeValor**: color de fondo del rectángulo en un control Alternar cuando su valor es **true** o color de la línea a la izquierda del identificador en un control deslizante.  Se aplica a los controles **[Control deslizante](controls/control-slider.md)** y **[Alternancia](controls/control-toggle.md)**.

**RellenoValorAlMantenerPuntero**: al mantener el puntero sobre un control Alternar o Control deslizante, color de fondo del rectángulo del primero cuando su valor es **true** o color de la línea a la izquierda del identificador del segundo.  Se aplica a los controles **[Control deslizante](controls/control-slider.md)** y **[Alternancia](controls/control-toggle.md)**.

**[VerticalAlign](controls/properties-text.md)**: la ubicación del texto en un control respecto al centro vertical de ese control.  Se aplica a muchos controles.

**[Visible](controls/properties-core.md)**: indica si un control aparece o está oculto.  Se aplica a muchos controles.

### <a name="w"></a>W
**[Width](controls/properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.  Se aplica a muchos controles.

**[WidthFit](controls/properties-size-location.md)** (AjusteDeAncho): indica si un control crece automáticamente en la horizontal para llenar el espacio vacío de un control de contenedor, como un control **[Formulario de edición](controls/control-form-detail.md)**. Si varias tarjetas tienen esta propiedad establecida en **true**, el espacio se divide entre ellas. Para más información, consulte [Understand data form layout in Microsoft PowerApps](working-with-form-layout.md) (Introducción al diseño de formularios de datos en Microsoft PowerApps).

**[Wrap](controls/control-text-box.md)** (Ajuste): indica si el texto que es demasiado largo para caber en una etiqueta se ajusta a la línea siguiente.  Se aplica al control **[Etiqueta](controls/control-text-box.md)**.

**[WrapCount](controls/control-gallery.md)**: el número de registros que aparecen en cada elemento de una galería.  Se aplica al control **[Galería](controls/control-gallery.md)**.

### <a name="x"></a>X
**[X](controls/properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario). Se aplica a muchos controles. Para un control **[Tarjeta](controls/control-card.md)** en un contenedor con varias columnas, esta propiedad determina la columna en la que aparece la tarjeta.

**[XLabelAngle](controls/control-column-line-chart.md)**: el ángulo de las etiquetas del eje x de un gráfico de columnas o de líneas.  Se aplica a los controles **[Gráfico de columnas](controls/control-column-line-chart.md)** y **[Gráfico de líneas](controls/control-column-line-chart.md)**.

### <a name="y"></a>Y
**[Y](controls/properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario). Se aplica a muchos controles. Para un control **[Tarjeta](controls/control-card.md)** en un contenedor con varias filas, esta propiedad determina la fila en la que aparece la tarjeta.

**[EjeYMáximo](controls/control-column-line-chart.md)**: el valor máximo del eje y de un gráfico de líneas.  Se aplica al control **[Gráfico de líneas](controls/control-column-line-chart.md)**.

**[EjeYMínimo](controls/control-column-line-chart.md)**: el valor mínimo del eje y de un gráfico de líneas.  Se aplica al control **[Gráfico de líneas](controls/control-column-line-chart.md)**.

**[YLabelAngle](controls/control-column-line-chart.md)**: el ángulo de las etiquetas del eje y de un gráfico de líneas o de columnas.  Se aplica a los controles **[Gráfico de columnas](controls/control-column-line-chart.md)** y **[Gráfico de líneas](controls/control-column-line-chart.md)**.

### <a name="z"></a>Z
**Zoom**: el porcentaje en que se amplía una imagen de una cámara o la vista de un archivo en un visor de PDF.  Se aplica a los controles **[Cámara](controls/control-camera.md)** y **[Visor de PDF](controls/control-pdf-viewer.md)**.
