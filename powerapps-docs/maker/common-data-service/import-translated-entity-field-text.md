---
title: Importación de texto traducido de campos y entidades con PowerApps | Microsoft Docs
description: Obtenga información sobre cómo importar texto traducido de campos y entidades
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: e2417f7ad75e327fdfc54d4cd4fdd3f62395326b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712719"
---
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>Importación de texto traducido de campos y entidades a una aplicación

Si personalizó el texto de una entidad o de un campo, como las etiquetas de un campo o los valores de una lista desplegable, puede brindar a los usuarios de la organización que no trabajan con la versión del idioma base del entorno este texto personalizado en sus propios idiomas. Para ello, debe exportar las cadenas de texto de todas las personalizaciones para poder traducirlas a los idiomas que se usan en la organización.  
  
 Después de la traducción, debe importar las cadenas de texto traducidas al entorno antes de que los usuarios puedan aprovechar los cambios.  
  
> [!IMPORTANT]
> - El archivo que se importa debe ser un archivo comprimido que contenga los archivos CrmTranslations.xml y [Content_Types].xml en la raíz.  
> - No se puede importar texto con más de 500 caracteres. Si cualquier elemento del archivo de traducción tiene más de 500 caracteres, el proceso de importación no se realizará correctamente. Si se produce un error en el proceso de importación, revise la línea del archivo que provocó este error, disminuya la cantidad de caracteres y trate nuevamente de realizar la importación. Tenga en cuenta también que debe volver a publicar las personalizaciones una vez que importe el texto traducido.  
  
1. Abra el [Explorador de soluciones](../model-driven-apps/advanced-navigation.md#solution-explorer).  
  
2. En la barra de herramientas Acciones del Explorador de soluciones, seleccione **Importar traducciones**.  
3.  En el cuadro de diálogo **Import Translated Text** (Importar texto traducido), especifique el archivo que contiene el texto traducido y seleccione **Importar**.  
  
4.  Una vez que se complete la importación, seleccione **Cerrar**.  
  
> [!NOTE]
>  La publicación de las personalizaciones pueden interferir con el funcionamiento normal del sistema. Se recomienda programar la publicación cuando sea menos problemática para los usuarios.  

## <a name="community-tools"></a>Herramientas de la comunidad

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) es una herramienta que la comunidad de XrmToolBox desarrolló para Dynamics 365 Customer Engagement. Use Easy Translator para exportar e importar traducciones con información contextual. 

> [!NOTE]
> Las herramientas de la comunidad no cuentan con el respaldo de Microsoft. Si tiene preguntas sobre la herramienta, póngase en contacto con el editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Pasos siguientes  
 [Exportar entidades personalizadas y texto de campo para su traducción](export-customized-entity-field-text-translation.md)
