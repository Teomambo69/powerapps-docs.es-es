---
title: Introducción a la conexión de Microsoft Translator | Microsoft Docs
description: Consulte cómo conectarse a Microsoft Translator a través de algunos ejemplos y vea todas las funciones
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4eab4585a2abd8633704c76b57cde52702982e97
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994035"
---
# <a name="connect-to-microsoft-translator-from-powerapps"></a>Conexión a Microsoft Translator desde PowerApps
![Microsoft Translator](./media/connection-microsoft-translator/translatoricon.png)

Agregue el conector de Microsoft Translator para que muestre el texto traducido en un control **Etiqueta** de la aplicación. Por ejemplo, puede crear un cuadro de texto de entrada que solicite al usuario que escriba algún texto para traducir. En otra etiqueta, puede mostrar el texto traducido.

En este tema se muestra cómo utilizar la conexión de Microsoft Translator, cómo usar la conexión de Microsoft Translator en una aplicación y cómo enumerar las funciones disponibles.

> [!NOTE]
> Este conector se limita a 150 llamadas por usuario y día.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-microsoft-translator"></a>Conexión a Microsoft Translator
1. Abra PowerApps, seleccione **Nuevo** y cree una **aplicación vacía**. Elija el diseño de teléfono o tableta. El diseño de tableta le ofrece más área de trabajo:  

   ![Abra una aplicación en blanco](./media/connection-microsoft-translator/blank-app.png)
2. En el panel derecho, pulse o haga clic en la pestaña **Datos** y, después, en **Agregar origen de datos**.
3. Seleccione **Nueva conexión** y, después, **Microsoft Translator**:  

    ![Conexión a Microsoft Translator](./media/connection-microsoft-translator/addconnection.png)

    ![Conexión a Microsoft Translator](./media/connection-microsoft-translator/add-translator.png)
4. Seleccione **Conectar**. La conexión aparecerá bajo **Orígenes de datos**:  

    ![Conexión a Microsoft Translator](./media/connection-microsoft-translator/translatordatasource.png)

## <a name="use-the-microsoft-translator-connection-in-your-app"></a>Utilice la conexión de Microsoft Translator en su aplicación
### <a name="translate-text"></a>Traducir texto
1. En el menú **Insert** (Insertar), seleccione **Text** (Texto) y luego seleccione **Text input** (Entrada de texto). Cambie el nombre del control de entrada de texto a **Origen**:  

    ![Cambiar nombre](./media/connection-microsoft-translator/renametosource.png)
2. Agregar una lista **desplegable** (menú **Insertar** > **Controles**), cambie su nombre a **TargetLang** y muévalo debajo de **Origen**.
3. Establezca la propiedad **[Elementos](../controls/properties-core.md)** de **TargetLang** a la fórmula siguiente:  

    `MicrosoftTranslator.Languages()`
4. Agregue una etiqueta, muévalo debajo de **TargetLang** y establezca su propiedad **[Texto](../controls/properties-core.md)** en la fórmula siguiente:  

    `MicrosoftTranslator.Translate(Source.Text, TargetLang.Selected.Value)`
5. Escriba algún texto en **Origen** y seleccione un idioma en **TargetLang**. La etiqueta muestra el texto que escribió en el idioma elegido:  

    ![Traducir texto de inglés a español](./media/connection-microsoft-translator/translate-text.png)

### <a name="speak-translated-text"></a>Pronunciar texto traducido
Si no lo ha hecho ya, siga los pasos descritos en la sección anterior para traducir el texto. Los pasos siguientes utilizan los mismos controles.

1. Establezca la propiedad **[Elementos](../controls/properties-core.md)** de la lista desplegable **TargetLang** en la fórmula siguiente:  

    `MicrosoftTranslator.SpeechLanguages()`
2. Cambie el nombre de la segunda etiqueta (no del cuadro **Origen**) a **Destino**.
3. Agregue un control **Audio** (menú **Insertar** > **Multimedia**) y establezca la propiedad **Multimedia** en la fórmula siguiente:  

    `MicrosoftTranslator.TextToSpeech(Target.Text, TargetLang.Selected.Value)`
4. Presione F5 o seleccione el botón Vista previa (![](./media/connection-microsoft-translator/preview.png)). Escriba algún texto en **Origen**, seleccione un idioma en **TargetLang** y seleccione el botón Reproducir en el control de audio.

    La aplicación reproduce una versión de audio del texto que ha escrito en el idioma elegido.
5. Presione Esc para volver al área de trabajo predeterminada.

### <a name="detect-the-source-language"></a>Detectar el idioma de origen
Los pasos siguientes utilizan la misma entrada de texto **Origen** y los controles de texto **Destino**. Puede crear nuevos controles si lo prefiere, solo tiene que actualizar los nombres en la fórmula.

1. Seleccione el control de texto **Destino** y establezca la propiedad **[Texto](../controls/properties-core.md)** en la fórmula siguiente:  

    `MicrosoftTranslator.Detect(Source.Text).Name`
2. Escriba algún texto en **Origen**.

    La etiqueta se muestra el idioma del texto que ha escrito. Por ejemplo, la etiqueta muestra **Francés** si escribe **bonjour** o **Italiano** si escribe **ciao**.

## <a name="view-the-available-functions"></a>Visualización de las funciones disponibles
Esta conexión incluye las siguientes funciones:

| Nombre de la función | Descripción |
| --- | --- |
| [Idiomas](connection-microsoft-translator.md#languages) |Recupera todos los idiomas que admite Microsoft Translator. |
| [Traducir](connection-microsoft-translator.md#translate) |Traduce el texto a un idioma especificado mediante Microsoft Translator. |
| [Detectar](connection-microsoft-translator.md#detect) |Detecta el idioma de origen del texto proporcionado. |
| [SpeechLanguages](connection-microsoft-translator.md#speechlanguages) |Recupera los idiomas disponibles para síntesis de voz. |
| [TextToSpeech](connection-microsoft-translator.md#texttospeech) |Convierte un texto proporcionado en voz como una secuencia de audio en formato de onda. |

### <a name="languages"></a>Lenguajes
Obtener idiomas: Recupera todos los idiomas que admite Microsoft Translator.

#### <a name="input-properties"></a>Propiedades de entrada
Ninguna

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| Código |string |No | |
| Nombre |string |No | |

### <a name="translate"></a>Traducir
Traducir texto: Traduce el texto a un idioma especificado mediante Microsoft Translator.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| query |string |yes |Texto que se traducirá |
| languageTo |string |yes |Código del idioma de destino (ejemplo: 'fr') |
| languageFrom |string |no |Idioma de origen (si no se proporciona, Microsoft Translator intentará detectarlo automáticamente) (ejemplo: en) |
| category |string |no |Categoría de traducción (predeterminado: 'general') |

#### <a name="output-properties"></a>Propiedades de salida
Ninguna

### <a name="detect"></a>Detectar
Detectar idioma: Detecta el idioma de origen del texto proporcionado.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| query |string |yes |Texto cuyo idioma se identificará |

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| Código |string |No | |
| Nombre |string |No | |

### <a name="speechlanguages"></a>SpeechLanguages
Obtener idiomas de voz: Recupera los idiomas disponibles para síntesis de voz.

#### <a name="input-properties"></a>Propiedades de entrada
Ninguna

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| Código |string |No | |
| Nombre |string |No | |

### <a name="texttospeech"></a>TextToSpeech
Texto a voz: Convierte un texto proporcionado en voz como una secuencia de audio en formato de onda.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| query |string |yes |Texto que se convertirá |
| language |string |yes |Código de idioma para generar voz (ejemplo: 'en-us') |

#### <a name="output-properties"></a>Propiedades de salida
Ninguna

## <a name="helpful-links"></a>Vínculos útiles
Consulte todas las [conexiones disponibles](../connections-list.md).  
Aprenda a [agregar conexiones](../add-manage-connections.md) a sus aplicaciones.

