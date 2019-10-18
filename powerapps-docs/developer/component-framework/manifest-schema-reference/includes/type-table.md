---
title: Tabla de tipo | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 41ea27ac-65b6-45a4-ae03-5f8d02dfc67b
ms.openlocfilehash: 058580b8f39417ccc5e77e7ac96a51bfc95939a1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338767"
---
|Value|Descripción|
|--|--|
|`Currency`|Los valores monetarios entre-922.337.203.685.477 y 922.337.203.685.477 pueden encontrarse en este campo. Puede establecer un nivel de precisión o elegir basar la precisión en una moneda concreta o en una precisión estándar usada por la organización.|
|`DateAndTime.DateAndTime`|Muestra la fecha y la hora.|
|`DateAndTime.DateOnly`|Muestra solo la fecha.|
|`Decimal`|Pueden usarse hasta 10 puntos decimales de precisión para los valores entre-100 mil millones y-100 mil millones en este campo. Puede especificar el nivel de precisión y los valores máximo y mínimo.|
|`Enum`|Tipo de datos enumerados.|
|`FP`|Se pueden usar hasta 5 puntos decimales de precisión para los valores entre-100 mil millones y-100 mil millones en este campo. Puede especificar el nivel de precisión y los valores máximo y mínimo. |
|`Multiple`|Este campo puede contener hasta 1.048.576 caracteres de texto. Puede establecer la longitud máxima en un valor inferior a este. Al agregar este campo a un formulario, puede especificar el tamaño del campo.|
|`OptionSet`|Este campo proporciona un conjunto de opciones. Cada opción tiene un valor numérico y una etiqueta. Cuando se agrega a un formulario, este campo muestra un control para que los usuarios seleccionen solo una opción. |
|`SingleLine.Email`|El texto proporciona un vínculo mailto para abrir la aplicación de correo electrónico del usuario.|
|`SingleLine.Phone`|En la aplicación Web, los campos estarán habilitados para iniciar llamadas con Skype o Lync si hay algún cliente de instalado en el equipo. La opción proveedor de telefonía está en la parte inferior de la pestaña General de configuración del sistema. para Dynamics 365 para tabletas, Skype es el único proveedor de telefonía disponible.|
|`SingleLine.Text`|Esta opción simplemente muestra texto.|
|`SingleLine.TextArea`|Esta opción de formato se puede utilizar para mostrar varias líneas de texto. Pero con un límite de 4000 caracteres, el campo de varias líneas de texto es una opción mejor si se esperan grandes cantidades de texto.|
|`SingleLine.Ticker`|Para la mayoría de los idiomas, el texto se habilitará como un vínculo para abrir el sitio web de MSN Money con el fin de mostrar los detalles del precio de las acciones que representa el símbolo del tablero de cotizaciones. En el caso de ciertos idiomas de Asia oriental, la ventana abrirá los resultados de búsqueda de Bing para el símbolo del tablero de cotizaciones.|
|`SingleLine.URL`|El texto proporciona un hipervínculo para abrir la página especificada. Cualquier texto que no empiece por un protocolo válido tendrá "http://" antepuesto. En este campo solo se permiten los protocolos HTTP, HTTPS, FTP, FTPS, ONENOTE y TEL.|
|`TwoOptions`|Este campo proporciona dos opciones. Cada opción tiene un valor numérico de 0 o 1 correspondiente a un valor false o true. Cada opción también tiene una etiqueta para que los valores true o false se puedan representar como "Yes" y "no", "Hot" y "Cold", "ON" y "OFF", o cualquier par de etiquetas que desee mostrar.|
|`Whole.None`|Esta opción simplemente muestra un número.|

## <a name="value-elements-that-are-not-supported"></a>Elementos de valor no admitidos

Actualmente no se admiten los siguientes valores de atributo de `of-type`:

|Value|Descripción|
|-----|------|
|`Whole.Duration`|Esta opción de formato se puede utilizar para mostrar una lista de opciones de duración. Pero los datos almacenados en la base de datos siempre son un número de minutos. El campo es similar a una lista desplegable y proporciona opciones sugeridas como 1 minuto, 15 minutos, 30 minutos hasta 3 días. Los usuarios pueden elegir estas opciones. Sin embargo, las personas también pueden escribir un número de minutos y se resuelven en ese período de tiempo.|
|`Whole.Timezone`|Esta opción muestra una lista de las zonas horarias como (GMT-12:00) Internacional de la línea de fecha oeste y (GMT-08:00) hora del Pacífico (EE. UU. & Canadá). Cada una de estas zonas se almacena como un número. Por ejemplo, para la hora del Pacífico (GMT-08:00) (EE. UU. & Canadá), TimeZoneCode es 4. Más información: [clase TimeZoneCode (ensamblado SDK)](https://docs.microsoft.com/en-us/previous-versions/dynamics-crm4/developers-guide/bb959779(v=msdn.10))|
|`Whole.Language`|Esta opción muestra una lista de los idiomas aprovisionados para su organización. Los valores se muestran como una lista desplegable de nombres de idioma, pero los datos se almacenan como un número mediante códigos LCID. Los códigos de idioma son identificadores de configuración regional de cuatro o cinco dígitos. Los valores de los identificadores de configuración regional válidos pueden encontrarse en [el gráfico de identificadores de configuración regional (LCID)](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms912047(v=winembedded.10)).|
|`Lookup.Simple`|Permite una sola referencia a una entidad específica. Todas las búsquedas personalizadas son de este tipo.|
|`Lookup.Customer`|Permite una sola referencia a una cuenta o a un registro de contacto. Estas búsquedas están disponibles para las entidades oportunidad, caso, oferta, pedido y factura. Estas entidades también tienen búsquedas de contactos y cuentas independientes que puede usar si sus clientes son siempre un tipo. O bien, puede incluir en lugar de usar la búsqueda de clientes.|
|`Lookup.Owner`|Permite una única referencia a un equipo o a un registro de usuario. Todas las entidades propiedad del equipo o del usuario tienen una de estas.|
|`Lookup.PartyList`|Permite varias referencias a varias entidades. Estas búsquedas se encuentran en los campos entidad de correo electrónico **para** y **CC** . También se usan en las entidades teléfono y cita.|
|`Lookup.Regarding`|Permite una sola referencia a varias entidades. Estas búsquedas se encuentran en el campo referente a usado en las actividades.|
|`MultiSelectOptionSet`|Puede personalizar formularios (vista principal, creación rápida y vista rápida) y plantillas de correo electrónico mediante la adición de campos de selección múltiple. Al agregar un campo de conjunto de opciones de selección múltiple, puede especificar varios valores que estarán disponibles para que los usuarios los seleccionen. Cuando los usuarios rellenan el formulario, pueden seleccionar uno, varios o todos los valores que se muestran en una lista desplegable.|
