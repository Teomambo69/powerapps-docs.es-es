---
title: Uso de Cognitive Services en PowerApps | Microsoft Docs
description: "Creación de una aplicación básica que usa Text Analytics API de Microsoft Cognitive Services para analizar texto."
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/24/2017
ms.author: mblythe
ms.openlocfilehash: 2767ee72fcf62b626f0376e34f058e72bb3708e3
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="use-cognitive-services-in-powerapps"></a>Uso de Cognitive Services en PowerApps
En este artículo se muestra cómo compilar una aplicación básica que usa [Text Analytics API de Microsoft Cognitive Services](https://docs.microsoft.com/azure/cognitive-services/text-analytics/overview) para analizar texto. Le mostraremos cómo configurar Text Analytics API y cómo conectarse a ella con el [conector de Text Analytics](https://docs.microsoft.com/connectors/cognitiveservicestextanalytics/). A continuación, le mostraremos cómo crear una aplicación que llama a la API.

**Nota**: si no está familiarizado con la creación de aplicaciones en PowerApps, es recomendable leer [Crear una aplicación desde cero](get-started-create-from-blank.md) antes de profundizar en este artículo.

## <a name="introduction-to-microsoft-cognitive-services"></a>Introducción a Microsoft Cognitive Services
Microsoft Cognitive Services es un conjunto de API, SDK y servicios disponibles para hacer que sus aplicaciones sean más inteligentes, atractivas y detectables. Estos servicios permiten agregar fácilmente a sus aplicaciones características inteligentes tales como detección de emociones y vídeo; reconocimiento facial, visual y de voz; y comprensión de narración y lenguaje.

Nos centraremos en la "comprensión del lenguaje" en este artículo, y trabajaremos con la API Text Analytics. La API permite detectar la opinión, las frases clave, los temas y el idioma del texto. Para empezar, vamos a probar una demostración de la API; regístrese para obtener una versión preliminar.

### <a name="try-out-the-text-analytics-api"></a>Prueba de Text Analytics API
La API tiene una demostración en línea, en la que puede ver cómo funciona y ver el código JSON que el servicio devuelve.

1. Vaya a la página [Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/).
2. En la sección **Véala en acción**, utilice el texto de ejemplo o escriba su propio texto. Luego pulse o haga clic en **Analizar**. 
   
    ![Demostración de Text Analytics API](./media/cognitive-services-api/text-analytics-demo.png)
3. La página muestra los resultados con formato en la pestaña **Texto analizado**, y la respuesta JSON en la pestaña **JSON**. [JSON](http://json.org/) es una forma de representar los datos; en este caso, los datos devueltos por Text Analytics API.

## <a name="sign-up-for-the-text-analytics-api"></a>Registro para Text Analytics API
La API está disponible como versión preliminar gratuita y está asociada con una suscripción de Azure. La API se administra en Azure Portal.

1. Si aún no tiene una suscripción de Azure, [regístrese para obtener una suscripción gratuita](https://azure.microsoft.com/free/).
2. Inicie sesión en su cuenta de Azure.
3. Vaya a la hoja [Crear en Cognitive Services](https://go.microsoft.com/fwlink/?LinkId=761108), en Azure Portal.
4. Especifique la información de Text Analytics API, como en la siguiente imagen. Seleccione la tarifa **F0** (gratuita).
   
    ![Creación de Text Analytics API](./media/cognitive-services-api/azure-create.png)
5. En la esquina inferior izquierda, pulse o haga clic en **Crear**.
6. En el **Panel**, pulse o haga clic en la API que acaba de crear.
   
    ![Panel de Azure](./media/cognitive-services-api/azure-dashboard.png)
7. Haga clic o pulse en **Claves**.
   
    ![Menú de Azure](./media/cognitive-services-api/azure-menu-keys.png)
8. Copie una de las claves de la derecha de la pantalla. Esta clave se usará más tarde cuando creemos una conexión a la API.
   
    ![Claves de API](./media/cognitive-services-api/azure-keys.png)

## <a name="build-the-app"></a>Creación de la aplicación
Ahora que tenemos Text Analytics API lista y funcionando, podemos conectarnos a ella desde PowerApps y crear una aplicación que llame a la API. Es una aplicación de una sola pantalla que proporciona una funcionalidad similar a la demostración de la página Text Analytics API. Vamos a empezar a trabajar.

### <a name="create-the-app-and-add-a-connection"></a>Creación de la aplicación y adición de una conexión
En primer lugar, crearemos una aplicación de teléfono vacía y agregaremos una conexión con el conector de **Text Analytics**. Si necesita más información sobre estas tareas, consulte [Crear una aplicación desde cero](get-started-create-from-blank.md) y [Administración de las conexiones en PowerApps](add-manage-connections.md).

1. En PowerApps Studio, pulse o haga clic en **Archivo** > **Nuevo** y, en **Aplicación vacía**, haga clic o pulse en **Diseño de teléfono**.
   
    ![Aplicación vacía, diseño de teléfono](./media/cognitive-services-api/blank-app.png)
2. En el panel central, haga clic o pulse en **conectar a datos**.
3. En el panel derecho, haga clic o pulse en **Nueva conexión** > **Text Analytics**.
   
    ![Orígenes de datos de PowerApps](./media/cognitive-services-api/data-sources.png)
4. Copie la clave en **Clave de cuenta** y haga clic o pulse en **Crear**.
   
    ![Conector de Text Analytics](./media/cognitive-services-api/create-connection-ta.png)

### <a name="add-controls-to-the-app"></a>Adición de controles a la aplicación
El siguiente paso para crear aplicación es agregar todos los controles. Normalmente, al crear aplicaciones, agrego las fórmulas a los controles sobre la marcha pero, en este caso, nos centraremos primero en los controles y, después, agregaremos algunas fórmulas en la sección siguiente. La siguiente imagen muestra la aplicación con todos los controles.

![Aplicación finalizada](./media/cognitive-services-api/finished-app-no-data.png)

Siga los pasos a continuación para crear esta pantalla. Si se especifica un nombre de control, ese el nombre que se usará en una fórmula en la sección siguiente.

1. En la pestaña **Inicio**, pulse o haga clic en **Nueva pantalla** y en **Pantalla desplazable**. 
2. En **Screen2**, seleccione **[Título]** y cámbielo a **Text Analysis**.
3. Agregue un control **Etiqueta** para el texto que se escribe.
4. Agregue un control **Entrada de texto** para que podamos escribir el texto que se va a analizar. Asigne al control el nombre **tiTextToAnalyze**. Ahora la aplicación debería parecerse a la siguiente imagen.
   
    ![Aplicación con título, subtítulo y entrada de texto](./media/cognitive-services-api/partial-app-step1.png)
5. Agregue tres controles **Casilla** para poder elegir qué operaciones de API se realizarán. Asigne a los controles los nombres **chkLanguage**, **chkPhrases** y **chkSentiment**.
6. Agregue un botón para poder llamar a la API después de seleccionar qué operaciones se deben realizar. Ahora la aplicación debería parecerse a la siguiente imagen.
   
    ![Aplicación con casillas y un botón](./media/cognitive-services-api/partial-app-step2.png)
7. Agregue tres controles **Etiqueta**. Los dos primeros contendrán los resultados de las llamadas a la API sobre el idioma y la opinión; el tercero es simplemente una introducción a la galería, en la parte inferior de la pantalla.
8. Agregue un control **Galería vertical vacía** y, después, agregue un control **Etiqueta** control a la galería. La galería contendrá los resultados de la llamada a la API sobre frases clave. Ahora la aplicación debería parecerse a la siguiente imagen.
   
    ![Aplicación con etiquetas y la galería](./media/cognitive-services-api/partial-app-step3.png)
9. En el panel izquierdo, seleccione **Screen1** > puntos suspensivos (**...** ) > **Eliminar** (no necesitamos esta pantalla en nuestra aplicación).

Simplificaremos esta aplicación para centrarnos en las llamadas a Text Analytics API, pero puede agregar elementos tales como lógica para mostrar y ocultar los controles en función de las casillas que están activadas, para controlar los errores si el usuario no seleccione ninguna opción, etc.

### <a name="add-logic-to-make-the-right-api-calls"></a>Adición de lógica para realizar las llamadas correctas a la API
Ahora tenemos una aplicación bonita, pero aún no hace nada. Solucionaremos eso en un momento. Pero antes de profundizar en los detalles, vamos a comprender el modelo que la aplicación sigue:

1. La aplicación realiza llamadas específicas a la API en función de las casillas activadas en la aplicación. Cuando se hace clic o se pulsa **Analizar texto**, la aplicación realiza 1, 2 o 3 llamadas a la API.
2. Los datos devueltos por la API se almacenan en tres [colecciones](working-with-variables.md#create-a-collection) diferentes: **languageCollect**, **sentimentCollect** y **phrasesCollect**.
3. La propiedad **Text** de dos de las etiquetas y la propiedad **Items** de la galería se actualizan en función de lo que hay en las tres colecciones.

Con esa información, vamos a agregar la fórmula para la propiedad **OnSelect** de nuestro botón. Aquí es donde se produce la magia.

```
If(chkLanguage.Value=true,

        ClearCollect(languageCollect, TextAnalytics.DetectLanguage({numberOfLanguagesToDetect:1, text:tiTextToAnalyze.Text}).detectedLanguages.name)

);

If(chkPhrases.Value=true,

        ClearCollect(phrasesCollect, TextAnalytics.KeyPhrases({language:"en", text:tiTextToAnalyze.Text}).keyPhrases)

);

If(chkSentiment.Value=true,

        ClearCollect(sentimentCollect, TextAnalytics.DetectSentiment({language:"en", text:tiTextToAnalyze.Text}).score)

)
```

Vamos a ver con detalle lo que sucede:

* Las instrucciones **If** son sencillas: si se selecciona una casilla específica, se realiza la llamada a la API para esa operación.
* Dentro de cada llamada, especifique los parámetros adecuados:
  * En las tres llamadas, especificamos **tiTextToAnalyze.Text** como texto de entrada.
  * En **DetectLanguage()**, se codifica **numberOfLanguagesToDetect** de forma rígida como 1, pero podemos pasar este parámetro en función de alguna lógica de la aplicación.
  * En **KeyPhrases()** y **DetectSentiment()**, codificamos el idioma de forma rígida como "en", pero podemos pasar este parámetro en función de alguna lógica de la aplicación. Por ejemplo, podemos detectar el idioma en primer lugar y establecer este parámetro en función del valor que **DetectLanguage()** devuelva.
* Para cada llamada que se realiza, agregue los resultados a la colección correspondiente:
  * Para **languageCollect**, agregamos el valor de **name** del idioma que se identificó en el texto.
  * Para **phrasesCollect**, agregamos los valores de **keyPhrase** que se identificaron en el texto.
  * Para **sentimentCollect**, agregamos el valor de **score** de la opinión para el texto, que es un valor entre 0 y 1, donde 1 es 100% positivo.

### <a name="display-the-results-of-the-api-calls"></a>Presentación de los resultados de las llamadas a la API
Para mostrar los resultados de las llamadas a la API, haga referencia a la colección adecuada en cada control:

1. Establezca la propiedad **Text** de la etiqueta de idioma en: `"The language detected is " & First(languageCollect).name`.
   
    La función **First()** devuelve el primer registro (y único en este caso) de **languageCollect**, y mostramos el valor de **name** (el único campo) asociado con ese registro.
2. Establezca la propiedad **Text** de la etiqueta de opinión en: `"The sentiment score is " & Round(First(sentimentCollect.Value).Value, 3)\*100 & "% positive."`.
   
    Esta fórmula utiliza también la función **First()**, obtiene el valor de **Value** (0-1) del primer y único registro y, a continuación, le da formato como un porcentaje.
3. Establezca la propiedad **Items** de la galería de frases clave en: `phrasesCollect`.
   
    Ahora estamos trabajando con una galería y no se necesita la función **First()** para extraer un valor único. Hacemos referencia a la colección y la galería muestra las frases clave como una lista.

## <a name="run-the-app"></a>Ejecutar la aplicación
Ahora que la aplicación está terminada, ejecútela para ver cómo funciona. En la siguiente imagen, se seleccionan las tres opciones y el texto es el mismo que el texto predeterminado en la página de Text Analytics API.

![Aplicación finalizada con datos](./media/cognitive-services-api/finished-app.png)

Si compara la salida de esta aplicación con la página de Text Analytics API que indicamos al principio de este artículo, verá que obtenemos los mismos resultados.

Esperamos que ahora comprenda un poco mejor Text Analytics API y que haya disfrutado de ver cómo se incorpora a una aplicación. Háganos saber si hay otros servicios de Cognitive Services (u otros servicios en general) que desearía que tratáramos en nuestros artículos. Como siempre, puede enviarnos sus comentarios y sus preguntas.

