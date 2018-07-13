---
title: Examen de un código de barras | Microsoft Docs
description: Examinar una variedad de tipos de código de barras, como UPC y Codabar
documentationcenter: na
author: aftowen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 10/23/2016
ms.author: anneta
ms.openlocfilehash: 3e1bc218e6be8dcbbb1a72672aedf1de5d1cd7e9
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37895946"
---
# <a name="scan-a-barcode-in-powerapps"></a>Examen de un código de barras en PowerApps
Escanee varios tipos de códigos de barras creando una aplicación y ejecutándola en un dispositivo, como un teléfono con cámara. El equivalente numérico del código de barras aparece en un control **Etiqueta**, y puede cargar esos datos en diversos [orígenes de datos](connections-list.md).

Si no está familiarizado con PowerApps, consulte [Introducción](getting-started.md).

## <a name="known-limitations"></a>Limitaciones conocidas
* Los códigos de barras deben ser al menos de 1" (2,5 cm) de alto y 1,5" (4 cm) de ancho.
* Para examinar los códigos de barras con un teléfono, manténgalo en orientación vertical y muévalo lentamente de 7"(18 cm) hasta 10" (25 cm) de distancia del código de barras.
* Los tipos de código de barras largos (por ejemplo, I2of5, que puede tener 15 o más caracteres) pueden dar resultados truncados o incorrectos, especialmente si el código de barras no se imprime con claridad.
* Para iPhone y dispositivos Android, puede especificar la propiedad **Height** del control **Barcode**, pero una relación de aspecto fija determina su ancho.
* Tendrá que establecer la propiedad **Scanrate** del control **Barcode** en **35** o menos.
* Para retrasar la situación de quedarse sin memoria en los dispositivos con iOS, establezca la propiedad **Height** del control **Barcode** en **700** (o inferior) y la propiedad **Scanrate** en **30**.
* Si el dispositivo se queda sin memoria y la aplicación se bloquea, reinicie la aplicación.

## <a name="create-a-blank-app"></a>Crear una aplicación en blanco
1. [Suscríbase a PowerApps](../signup-for-powerapps.md) y, a continuación, haga lo *siguiente*:

2. [Abra PowerApps](https://create.powerapps.com) en un explorador en un dispositivo con cámara.

3. En **Comenzar con una plantilla o un lienzo en blanco**, haga clic o pulse en **Diseño de teléfono** en el icono **Aplicación vacía**.

    ![Crear una aplicación desde cero](./media/scan-barcode/create-from-blank.png)

4. Si no ha usado PowerApps antes, familiarícese con las áreas clave de la aplicación haciendo un paseo introductorio (o haga clic o pulse en **Omitir**).

    ![Pantalla inicial del paseo introductorio](./media/scan-barcode/quick-tour.png)

    > [!NOTE]
   > Siempre puede realizar el paseo más tarde haciendo clic o pulsando en el icono del signo de interrogación situado cerca de la esquina superior derecha de la pantalla y, a continuación, haciendo clic o pulsando en **Take the intro tour** (Realizar paseo introductorio).

## <a name="add-a-barcode-control"></a>Agregar un control Barcode
1. En la pestaña **Insertar**, haga clic o pulse en **Multimedia** y, a continuación, en **Barcode**.

    ![Agregar escáner de código de barras](./media/scan-barcode/add-scanner.png)

2. Asegúrese de que el control **Barcode** esté seleccionado. Para ello, confirme que se encuentra rodeado por un cuadro de selección (con controladores para cambiar el tamaño del control).

    ![Cuadro de selección](./media/scan-barcode/selection-box.png)

3. En la pestaña **Inicio**, haga clic o pulse en **Barcode1** y, a continuación, escriba o pegue **MyScanner** en **Cambiar nombre**.

    > [!TIP]
   > El primer control **Barcode** que agregue tendrá el nombre **Barcode1** de forma predeterminada. Si elimina ese control y agrega otro control **Barcode**, se denominará **Barcode2** de forma predeterminada. Al cambiar manualmente el nombre de un control, se asegura de que las fórmulas harán referencia al control por su nombre correcto.

    ![Cambiar el nombre del control de código de barras](./media/scan-barcode/rename-barcode.png)

## <a name="add-a-text-input-control"></a>Agregar un control Text input
1. En la pestaña **Insertar**, haga clic o pulse en **Text**, y, a continuación, en **Text input**.

    Si la pestaña **Insertar** no aparece, maximice la ventana de PowerApps.

    ![Agregar un control Text input](./media/scan-barcode/add-text-input.png)

2. Arrastre el cuadro de selección (no los controladores de cambio de tamaño) alrededor del control **Text input** hacia abajo hasta que aparezca debajo de **MyScanner**.

    ![Etiqueta con el cuadro de selección](./media/scan-barcode/move-input-text.png)

3. Con el control **Text input** aún seleccionado, asegúrese de que aparece **Default** en la lista de propiedades y, a continuación, escriba o pegue **MyScanner.Text** en la barra de fórmulas.

    ![Propiedad Texto del control Etiqueta](./media/scan-barcode/default-text.png)

## <a name="change-the-barcode-type"></a>Cambiar el tipo de código de barras
1. En la pestaña **Insertar**, pulse o haga clic en **Controles** y, a continuación, en **Drop down**.

    ![Agregar lista desplegable](./media/scan-barcode/insert-dropdown.png)

2. Mueva el control **Drop down** de forma que aparezca debajo de los otros controles en la pantalla.

    ![Mover lista desplegable](./media/scan-barcode/move-dropdown.png)

3. Con el control **Drop down** aún seleccionado, asegúrese de que la lista de propiedades muestra **Items** y, a continuación, escriba o pegue esta cadena de texto en la barra de fórmulas:<br>
    **[Codabar, Code128, Code39, Ean, I2of5, Upc]**

    ![Establecer la propiedad Items de la lista desplegable](./media/scan-barcode/items-property.png)

4. En la pestaña **Inicio**, cambie el nombre del control **Drop down** a **ChooseType**.

    ![Cambiar el nombre de la lista desplegable](./media/scan-barcode/rename-dropdown.png)

5. Haga clic o pulse en **MyScanner** para seleccionarlo, asegúrese de que la lista de propiedades muestra **BarcodeType** y, a continuación, escriba o pegue esta cadena en la barra de fórmula:<br>
    **ElegirTipo.Valor.Seleccionado**

## <a name="test-the-app"></a>Probar la aplicación
1. Para abrir el modo de vista previa, presione F5 (o haga clic o pulse en el icono de reproducción situado cerca de la esquina superior derecha).

    ![Abrir el modo de vista previa](./media/scan-barcode/open-preview.png)

2. Mantenga el código de barras en la cámara del dispositivo hasta que aparezca el componente numérico de la barra de código en el control **Etiqueta**.

    Si no aparece el componente numérico, pruebe una opción distinta en la lista **BarcodeType**. Si siguen sin aparecer los datos correctos, escriba el número correcto en el control **Input text**.

## <a name="next-steps"></a>Pasos siguientes
* [Conecte la aplicación a un origen de datos](add-data-connection.md) y configure la función **[Patch](functions/function-patch.md)** de forma que los usuarios puedan guardar los resultados.
* Agregue un control **[Drop down](controls/control-drop-down.md)** y configúrelo para que los usuarios puedan elegir el tipo de código de barras que deseen examinar.
* Agregue un control **[Slider](controls/control-slider.md)** y configúrelo para que los usuarios puedan ajustar la frecuencia de exploración o el alto del control **Barcode**.
