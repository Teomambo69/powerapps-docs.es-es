---
title: Habilitar la compatibilidad con el portal de varios idiomas | MicrosoftDocs
description: Instrucciones para habilitar varios idiomas para un portal y crear contenido en varios idiomas.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f8da1ac4be7098fc712faef82f6c9566d5f10512
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552759"
---
# <a name="enable-multiple-language-portal-support"></a>Habilitar la compatibilidad con el portal de varios idiomas
La empresa no se limita a una sola región o a un idioma. Un solo portal puede mostrar contenido en varios idiomas para llegar a clientes de todo el mundo. El contenido del portal se puede traducir en varios idiomas mientras se mantiene una sola jerarquía de contenido.

![Lista desplegable multilingüe](../media/multi-language-dropdown.png "Lista desplegable de varios idiomas")  

Para habilitar varios idiomas para un portal, siga estos pasos:

1. [Habilitar idiomas en un entorno de Common Data Service.](https://technet.microsoft.com/library/dn832148.aspx)  
2. Vaya a **portales** > **sitio web** > **sitios**Web.
3. Seleccione el sitio web al que desea agregar compatibilidad con idiomas.
4. En la sección **idiomas admitidos** de la pestaña **General** , seleccione **nuevo idioma del sitio web**.
5. Rellene el formulario, incluido el **idioma del portal** (búsqueda de idiomas que están activados en la organización y que son compatibles con los portales) y el estado de **publicación**.

   ![Agregar un nuevo idioma del portal](../media/add-new-portal-language.png "Agregar un nuevo idioma del portal")

   ![Establecer el idioma predeterminado para el portal](../media/set-default-language-portal.png "Establecer el idioma predeterminado para el portal")

> [!Note]
> Si activa nuevos idiomas después de aprovisionar el portal, puede [importar las traducciones de metadatos](../admin/import-metadata-translation.md) para que los metadatos se traduzcan para los idiomas que se acaban de activar.

## <a name="supported-languages"></a>Idiomas admitidos

En la tabla siguiente se muestran todos los idiomas disponibles actualmente. Esta lista se puede encontrar **yendo a** portales &gt; **contenido** &gt; **lenguajes del portal**. El nombre para mostrar del portal de un idioma se puede cambiar después de seleccionar el idioma que se va a cambiar desde esta página. Tenga en cuenta que la lista ahora incluye idiomas de Asia Oriental (japonés, Chino y Coreano).

| **Nombre**                           | **Código de idioma** | **LCID** | **Nombre para mostrar del portal** |
|------------------------------------|-------------------|----------|-------------------------|
| Euskera (euskera)                    | EU-ES             | 1069     | euskara                 |
| Búlgaro-Bulgaria               | BG-BG             | 1026     | български               |
| Catalán-catalán                  | CA-ES             | 1027     | català                  |
| Chino (China)                    | zh-CN             | 2052     | 中文(中国)              |
| Chino (Hong Kong RAE)            | ZH-HK             | 3076     | 中文(香港特別行政區)    |
| Chino (tradicional)              | zh-TW             | 1028     | 中文(台灣)              |
| Croata-Croacia                 | hr-HR             | 1050     | Hrvatski                |
| Checo-República Checa             | CS-CZ             | 1029     | čeština                 |
| Danés (Dinamarca)                   | da-DK             | 1030     | Dansk                   |
| Neerlandés (Países Bajos)                | nl-NL             | 1043     | Holandes              |
| Inglés                            | en-US             | 1033     | Inglés                 |
| Estonio-Estonia                 | ET-EE             | 1061     | Eesti                   |
| Finés-Finlandia                  | fi-FI             | 1035     | Suomi                   |
| Francés (Francia)                    | fr-FR             | 1036     | francesa                |
| Gallego-España                   | GL-ES             | 1110     | Galego                  |
| Alemán (Alemania)                   | de-DE             | 1031     | Deutsch                 |
| Griego-Grecia                     | el-GR             | 1032     | Ελληνικά                |
| Hindi (India)                      | HI-IN             | 1081     | हिंदी                   |
| Húngaro (Hungría)                | Hu-HU             | 1038     | Magyar                  |
| Indonesio-Indonesia             | identificador ID.             | 1057     | Bahasa Indonesia        |
| Italiano-Italia                    | ti             | 1040     | italiana                |
| Japonés (Japón)                   | ja-JP             | 1041     | 日本語                  |
| Kazajo: Kazajstán                | kk-KZ             | 1087     | қазақ тілі              |
| Coreano (Corea)                     | ko-KR             | 1042     | 한국어                  |
| Letón (Letonia)                   | LV: LV             | 1062     | latviešu                |
| Lituano (Lituania)             | lt-LT             | 1063     | lietuvių                |
| Malayo-Malasia                   | MS-MY             | 1086     | Bahasa Melayu           |
| Noruego (bokmål)-Noruega        | NB-NO             | 1044     | Norsk Bokmål            |
| Polaco-Polonia                    | PL-PL             | 1045     | Polski                  |
| Portugués (Brasil)                | pt-BR             | 1046     | Português (Brasil)      |
| Portugués (Portugal)              | pt-PT             | 2070     | Português (Portugal)    |
| Rumano-Rumania                 | RO-RO             | 1048     | română                  |
| Ruso-Rusia                   | ru-RU             | 1049     | русский                 |
| Serbio (cirílico)-Serbia        | Sr-Cyrl-CS        | 3098     | српски                  |
| Serbio (Latino)-Serbia           | Sr-Latn-CS        | 2074     | Srpski                  |
| Eslovaco-Eslovaquia                  | SK-SK             | 1051     | slovenčina              |
| Esloveno-Eslovenia               | SL-SI             | 1060     | slovenščina             |
| Español (Alfabetización tradicional)-España | es-ES             | 3082     | Español                 |
| Sueco (Suecia)                   | SV-SE             | 1053     | Svenska                 |
| Tailandés (Tailandia)                    | TH-TH             | 1054     | ไทย                     |
| Turco-Turquía                   | TR-TR             | 1055     | Türkçe                  |
| Ucraniano (Ucrania)                | RU-UA             | 1058     | українська              |
| Vietnamita (Vietnam)               | VI-VN             | 1066     | Tiếng Việt              |

## <a name="create-content-in-multiple-languages"></a>Crear contenido en varios idiomas

1. Inicie sesión en Dynamics 365 portales.
2. Vaya a **portales** > **contenido** > **páginas web** para ver una lista de contenido. Para cada página web, habrá una versión primaria de la página y una versión secundaria de la página para cada idioma activado para el portal.
3. Para agregar una nueva localización de la página, vaya a una página base y desplácese hacia abajo hasta **contenido localizado**.
4. Seleccione el botón **+** del lado derecho para crear una búsqueda para la versión localizada.

    ![Agregar nuevo contenido localizado](../media/add-new-localized-content.png "Agregar nuevo contenido localizado")  

> [!Note]
> Los campos de configuración de la Página principal de una página de contenido no se heredan de las páginas de contenido existentes. Solo se usan en la creación de nuevas páginas de contenido. Debe actualizar las configuraciones de página de contenido individualmente.

Los artículos de conocimientos solo se mostrarán si se han traducido al idioma en el que el usuario establece el portal que se va a mostrar en. Sin embargo, los foros y blogs permiten un mayor control sobre cómo se presentan en otros idiomas. Especificar un idioma para un foro o blog es opcional. Si no se especifica un idioma, el foro o el blog se mostrarán en el idioma principal de la organización. Si desea que el foro o el blog sean específicos de un idioma, debe crearlos y asignarles el idioma.

Los conjuntos de vínculos Web son los vínculos de navegación en la parte superior del portal. Al navegar a **portales** > **contenido** > **conjuntos de vínculos Web** puede controlar cómo se traduce este contenido. Cuando un idioma está activo para el portal, se crea un nuevo conjunto de vínculos para el idioma recién activado.

![Vínculo Web activo para nuevo idioma](../media/active-weblink-new-language.png "Vínculo Web activo para nuevo idioma")
