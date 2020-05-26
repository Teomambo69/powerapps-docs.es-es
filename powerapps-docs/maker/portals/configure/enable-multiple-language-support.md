---
title: Habilitar compatibilidad de portal en varios idiomas| MicrosoftDocs
description: Instrucciones para habilitar varios idiomas para un portal y crear contenido en varios idiomas.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/30/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3af930d100dca4920c3bcb832aefc0f06c93e612
ms.sourcegitcommit: 8e76afb331745f1da929a39e831634680dfa6008
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3346999"
---
# <a name="enable-multiple-language-portal-support"></a>Habilitar compatibilidad de portal en varios idiomas
El negocio no se restringe una sola región o un idioma. Un único portal puede mostrar el contenido en varios idiomas para llegar a los clientes de todo el mundo. El contenido del portal se puede traducir a varios idiomas mientras se mantiene una sola jerarquía del contenido.

![Desplegable de varios idiomas](../media/multi-language-dropdown.png "Lista desplegable de varios idiomas")  

Para habilitar varios idiomas para un portal, sigas estos pasos:

1. [Habilite idiomas en un entorno de Common Data Service.](https://docs.microsoft.com/power-platform/admin/enable-languages)  
2. Vaya a **Portales** > **Página web** > **Páginas web**.
3. Seleccione el sitio web al que agregar compatibilidad con idiomas.
4. En la sección **Idiomas compatibles** en la pestaña **General**, seleccione **Nuevo idioma del sitio web**.
5. Rellene el formulario, incluido **Lenguaje del portal** (una búsqueda de idiomas que están activados en la organización y son compatibles con los portales) y **Estado de publicación**.

   ![Agregar un nuevo idioma del portal](../media/add-new-portal-language.png "Agregar un nuevo idioma del portal")

   ![Establecer el idioma predeterminado para el portal](../media/set-default-language-portal.png "Establecer el idioma predeterminado para el portal")

   ![Idiomas compatibles](../media/supported-languages.png "Idiomas compatibles")

> [!Note]
> Si activa nuevos idiomas una vez que se haya aprovisionado el portal, puede [importar las traducciones de metadatos](../admin/import-metadata-translation.md) para obtener los metadatos traducidos para idiomas recién activados.

## <a name="supported-languages"></a>Idiomas compatibles

La tabla de debajo muestra todos los idiomas disponibles actualmente de manera predefinida. Esta lista se encuentra yendo a **Portales** &gt; **Contenido** &gt; **Idiomas del portal**. El Nombre para mostrar del portal de un idioma se puede cambiar después de seleccionar el idioma a cambiar desde esta página. Tenga en cuenta que la lista ahora incluye idiomas asiáticos orientales (japonés, chino, y coreano).

| **Nombre**                           | **Código de idioma** | **LCID** | **Nombre para mostrar del portal** |
|------------------------------------|-------------------|----------|-------------------------|
| Euskera - Euskera                    | eu-ES             | 1069     | euskara                 |
| Búlgaro (Bulgaria)               | bg-BG             | 1026     | български               |
| Catalán - Catalán                  | ca-ES             | 1027     | català                  |
| Chino - China                    | zh-CN             | 2052     | 中文(中国)              |
| Chino (RAE de Hong Kong)            | zh-HK             | 3076     | 中文(香港特別行政區)    |
| Chino - Tradicional              | zh-TW             | 1028     | 中文 (台灣)              |
| Croata (Croacia)                 | hr-HR             | 1050     | hrvatski                |
| Checo (República Checa)             | cs-CZ             | 1029     | čeština                 |
| Danés (Dinamarca)                   | da-DK             | 1030     | dansk                   |
| Neerlandés (Países Bajos)                | nl-NL             | 1043     | Nederlands              |
| Inglés                            | es-ES             | 3082     | Inglés                 |
| Estonio (Estonia)                 | et-EE             | 1061     | eesti                   |
| Finés (Finlandia)                  | fi-FI             | 1035     | suomi                   |
| Francés (Francia)                    | fr-FR             | 1036     | français                |
| Gallego - España                   | gl-ES             | 1110     | galego                  |
| Alemán (Alemania)                   | de-DE             | 1031     | Deutsch                 |
| Griego (Grecia)                     | el-GR             | 1032     | Ελληνικά                |
| Hindi - India                      | hi-IN             | 1081     | हिंदी                   |
| Húngaro (Hungría)                | hu-HU             | 1038     | magyar                  |
| Indonesio (Indonesia)             | id-ID             | 1057     | Bahasa Indonesia        |
| Italiano (Italia)                    | it-IT             | 1040     | italiano                |
| Japonés (Japón)                   | ja-JP             | 1041     | 日本語                  |
| Kazajo (Kazajistán)                | kk-KZ             | 1087     | қазақ тілі              |
| Coreano (Corea)                     | ko-KR             | 1042     | 한국어                  |
| Letón (Letonia)                   | lv-LV             | 1062     | latviešu                |
| Lituano (Lituania)             | lt-LT             | 1063     | lietuvių                |
| Malayo (Malasia)                   | ms-MY             | 1086     | Bahasa Melayu           |
| Noruego (Bokmål, Noruega)        | nb-NO             | 1044     | norsk bokmål            |
| Polaco (Polonia)                    | pl-PL             | 1045     | polski                  |
| Portugués (Brasil)                | pt-BR             | 1046     | português (Brasil)      |
| Portugués (Portugal)              | pt-PT             | 2070     | português (Portugal)    |
| Rumano (Rumanía)                 | ro-RO             | 1048     | română                  |
| Ruso (Rusia)                   | ru-RU             | 1049     | русский                 |
| Serbio (cirílico, Serbia)        | sr-Cyrl-CS        | 3098     | српски                  |
| Serbio (latino, Serbia)           | sr-Latn-CS        | 2074     | srpski                  |
| Eslovaco (Eslovaquia)                  | sk-SK             | 1051     | slovenčina              |
| Esloveno (Eslovenia)               | sl-SI             | 1060     | slovenščina             |
| Español (Alfabetización tradicional) - España | es-ES             | 3082     | español                 |
| Sueco (Suecia)                   | sv-SE             | 1053     | svenska                 |
| Tailandés (Tailandia)                    | th-TH             | 1054     | ไทย                     |
| Turco (Turquía)                   | tr-TR             | 1055     | Türkçe                  |
| Ucraniano (Ucrania)                | uk-UA             | 1058     | українська              |
| Vietnamita (Vietnam)               | vi-VN             | 1066     | Tiếng Việt              |

## <a name="create-content-in-multiple-languages"></a>Crear contenido en varios idiomas

1. Iniciar sesión en los portales de Dynamics 365
2. Vaya a **Portales** > **Contenido** > **Páginas web** para ver una lista de contenido. Para cada página web, habrá una versión principal de la página y una versión secundaria de la página para cada idioma activado para el portal.
3. Para agregar una nueva localización de la página, vaya a una página base y desplácese hasta **Contenido localizado**.
4. Seleccione el botón **+** en el lado derecho para crear operaciones de búsqueda para la versión localizada.

    ![Agregar nuevo contenido localizado](../media/add-new-localized-content.png "Agregar nuevo contenido localizado")  

> [!Note]
> Los campos de configuración en la página principal de una página de contenido no se heredan en las páginas de contenido existentes. Se usan solo en la creación de nuevas páginas de contenido. Debe actualizar las configuraciones de la página de contenido individualmente.

Los artículos de conocimientos se mostrarán solo si se han traducido al idioma en el que el usuario establece el portal. Sin embargo, foros y blogs permiten mayor control sobre cómo se presentan en otros idiomas. Especificar un idioma para un foro o un blog es opcional. Si un idioma no se especifica, el foro o el blog se mostrarán en el idioma principal de la organización. Si desea que el foro o el blog sean específicos a un idioma, debe hacerlo y asignarle el idioma.

Los conjuntos de vínculos web son vínculos de navegación en la parte superior del portal. Al navegar a **Portales** > **Contenido** > **Conjuntos de vínculos web** puede controlar el modo en que se traduce este contenido. Cuando un idioma está activo en el portal, se crea un nuevo conjunto de vínculos para el idioma recién activado.

![Vínculo web activo para el nuevo idioma](../media/active-weblink-new-language.png "Vínculo web activo para el nuevo idioma")
