---
title: Type Table | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 41ea27ac-65b6-45a4-ae03-5f8d02dfc67b
---

|Value|Descripción|
|--|--|
|`Currency`|Los valores monetarios entre -922.337.203.685.477 y 922.337.203.685.477 pueden estar en este campo. Puede establecer un nivel de precisión o elegir basar la precisión en una divisa específica o una precisión estándar única usada por la organización.|
|`DateAndTime.DateAndTime`|Muestra fecha y hora.|
|`DateAndTime.DateOnly`|Solo muestra la fecha.|
|`Decimal`|Hasta 10 puntos decimales de precisión se pueden usar para valores entre -100.000.000.000 y -100.000.000.000 en este campo. Puede especificar el nivel de precisión y los valores máximo y mínimo.|
|`Enum`|Tipo de datos enumerados.|
|`FP`|Hasta 5 puntos decimales de precisión se pueden usar para valores entre -100.000.000.000 y -100.000.000.000 en este campo. Puede especificar el nivel de precisión y los valores máximo y mínimo. |
|`Multiple`|Este campo puede contener hasta 1 048 576 caracteres de texto. Puede establecer que la longitud máxima sea inferior a esta. Cuando agrega este campo a un formulario, puede especificar el tamaño del campo.|
|`OptionSet`|Este campo proporciona un conjunto de opciones. Cada opción tiene un valor y una etiqueta del número. Cuando se agrega a un formulario, este campo muestra un control para que lo usuarios solo puedan seleccionar una opción. |
|`SingleLine.Email`|El texto proporciona un vínculo mailto para abrir la aplicación de correo electrónico del usuario.|
|`SingleLine.Phone`|En la aplicación web, los campos permitirán hacer clic para realizar llamadas usando Skype o Lync si un cliente de cualquiera de estas aplicaciones se instala en el equipo. La opción del proveedor de telefonía está en la parte inferior de la pestaña General de Configuración del sistema. Para Dynamics 365 for tablets, Skype es el único proveedor de telefonía disponible.|
|`SingleLine.Text`|Esta opción solo muestra el texto.|
|`SingleLine.TextArea`|Esta opción de formato se puede usar para mostrar varias líneas de texto. Pero con un límite de 4000 caracteres, el campo Varias líneas de texto es una opción mejor si se prevén grandes cantidades de texto.|
|`SingleLine.Ticker`|Para la mayoría de los idiomas, el texto se habilitará como vínculo para abrir la página web MSN Money para mostrar detalles sobre el precio de las acciones representado por el símbolo del valor. Para algunos idiomas asiáticos orientales la ventana abrirá los resultados de la búsqueda de Bing para el símbolo del valor.|
|`SingleLine.URL`|El texto proporciona un hipervínculo para abrir la página especificada. A cualquier texto que no comience por un protocolo válido se le antepondrá “http://”. Solo los protocolos HTTP, HTTPS, FTP, FTPS, ONENOTE y TEL se permiten en este campo.|
|`TwoOptions`|Este campo proporciona dos opciones. Cada opción tiene un valor numérico de 0 o 1 correspondiente a un valor true o false. Cada opción también tiene una etiqueta para poder representar valores true o false como "Sí" y "No", "muy interesado" y "No interesado", "Activado" y "Desactivado" o un par de etiquetas que desee mostrar.|
|`Whole.None`|Esta opción solo muestra un número.|
