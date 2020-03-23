---
title: Importar texto de campo y entidad traducido con Power Apps | MicrosoftDocs
description: Obtenga información sobre como importar entidades traducidas y texto de campo
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 3d77d149-819b-45e6-8e70-1fbe54d5c153
caps.latest.revision: 19
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4ede184ad0629e71094c2f7ffdc8d71eb04460e7
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040763"
---
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>Importar entidades y texto de campo traducidos a una aplicación

Si ha personalizado texto de entidad o campo, como etiquetas de campos o valores de lista desplegable, puede ofrecer a los usuarios de su organización que no trabajan con la versión del idioma base del entorno texto personalizado en sus propios idiomas. Para ello, exporte las cadenas de texto de todas las personalizaciones para traducirlas a los idiomas que se usan en su organización.  
  
 Después de la traducción, debe importar las cadenas de texto traducidas en el entorno para que los usuarios puedan aprovechar los cambios.  
  
> [!IMPORTANT]
> - El archivo que importe debe ser un archivo comprimido que contiene los archivos CrmTranslations.xml y [Content_Types].xml en la raíz.  
> - No puede importar texto traducido que tenga más de 500 caracteres. Si alguno de los elementos del archivo de traducción tiene más de 500 caracteres, se producirá un error en el proceso de importación. Si esto sucede, revise la línea que provocó el error, reduzca el número de caracteres e intente de nuevo la importación. Tenga en cuenta también que después de importar texto traducido, debe volver a publicar las personalizaciones.  
  
1. Iniciar sesión en Power Apps en [https://make.powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2. Seleccione **Soluciones** y seleccione la solución no administrada desde la cual importar el texto traducido.

3. En el explorador de soluciones, en la barra de herramientas Acciones, seleccione **Traducciones** y, después, seleccione **Importar traducciones**.

4.  En el cuadro de diálogo **Importar texto traducido**, especifique el archivo que contiene el texto traducido y, a continuación, seleccione **Importar**.  
  
5.  Cuando finalice la importación, seleccione **Cerrar**.  
  
> [!NOTE]
>  La publicación de personalizaciones pueden interferir en el funcionamiento normal del sistema. Le recomendamos que programe la publicación cuando perjudique lo menos posible a los usuarios.  

## <a name="community-tools"></a>Herramientas de la Comunidad

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) es una herramienta desarrollada para Power Apps por la comunidad de XrmToolbox. Use Easy Translator para exportar e importar traducciones con información contextual. 

> [!NOTE]
> Las herramientas de la comunidad no se admiten en Microsoft. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Pasos siguientes  
 [Exportar texto personalizado de entidades y campos para su traducción](export-customized-entity-field-text-translation.md)
