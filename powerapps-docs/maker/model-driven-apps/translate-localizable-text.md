---
title: Traducción de texto localizable para aplicaciones basadas en modelos | Microsoft Docs
description: Obtenga información sobre cómo obtener texto localizable traducido para admitir varios idiomas.
ms.custom: ''
ms.date: 06/03/2018
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
ms.openlocfilehash: e2e305313f3b86be2ea410f6668676b56aa79d95
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698893"
---
# <a name="translate-localizable-text-for-model-driven-apps"></a>Traducción de texto localizable para aplicaciones basadas en modelos

Si ha personalizado texto de entidad o campo, como etiquetas de campos o valores de lista desplegable, puede ofrecer a los usuarios de su entorno que no trabajan con la versión del idioma base del entorno texto personalizado en sus idiomas preferidos. 

El proceso consta de los siguientes pasos:
1. Habilitar otros idiomas para el entorno
2. Exportar el texto localizable
3. Obtener el texto localizable traducido
4. Importar el texto localizado

## <a name="enable-other-languages-for-your-environment"></a>Habilitar otros idiomas para el entorno

Si todavía no ha habilitado los idiomas para el entorno, siga los pasos descritos en [Habilitar el idioma](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages) para habilitarlos.

> [!IMPORTANT]
> Habilitar cada idioma puede llevar varios minutos. Durante este tiempo, puede que otros usuarios del entorno no puedan usar la aplicación. Debe habilitar los idiomas en el momento en que menos molestias ocasione a los usuarios.

> [!TIP]
> Mientras habilita los idiomas, anote los valores de LCID usados para cada idioma. Este valor representará el idioma en los datos exportados del texto localizable. Los códigos de idioma son identificadores de configuración regional de cuatro o cinco dígitos. Los valores de los identificadores de configuración regional válidos pueden encontrarse en [el gráfico de identificadores de configuración regional (LCID)](http://go.microsoft.com/fwlink/?LinkId=122128).

## <a name="export-the-localizable-text"></a>Exportar el texto localizable

El ámbito del texto localizable que se exportará es la solución no administrada que contiene el texto localizable. Esto solo se puede hacer usando el Explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Abra la solución no administrada que contiene el texto localizable y, en la barra de menús, seleccione **Traducciones** > **Exportar traducciones**. 

![Exportar traducciones](media/export-localizable-text.png)

Debería ver una alerta que indica:
> La exportación de etiquetas personalizadas para la traducción puede tardar varios minutos. No haga clic en el vínculo de exportación de nuevo hasta que la primera exportación haya finalizado. ¿Está seguro de que desea exportar ahora? 

Haga clic en **Aceptar** si desea continuar.

Cuando finalice la exportación, puede encontrar un archivo con un nombre parecido a `CrmTranslations_{0}_{1}.zip` en la carpeta de descargas donde `{0}` es el nombre único de la solución y `{1}` es el número de versión de la solución.

## <a name="get-the-localizable-text-translated"></a>Obtener el texto localizable traducido

Puede enviar este archivo a un lingüista experto, a una agencia de traducción o a una empresa de localización.

Si sabe traducir el texto o si solo desea ver el formato, puede extraer el archivo ZIP que exportó y verá que contiene dos archivos XML. 
 - `[Content_Types].xml`
 - `CrmTranslations.xml`

Puede abrir el archivo CrmTranslations.xml con Microsoft Office Excel.

> [!TIP]
> A menos que normalmente abra archivos XML con Excel, puede que sea más fácil abrir Excel y, después, abrir el archivo pegando la ruta de acceso al archivo CrmTranslations.xml extraído.

> [!IMPORTANT]
> Asegúrese de no cambiar el formato del archivo. Si guarda el archivo en otro formato, no podrá volver a importarlo.

Cuando visualice los datos en Excel, consulte la pestaña **Etiquetas localizadas**.

![Texto exportado para la localización](media/localized-labels-tab-exported-languages.png)

Cualquier entidad o campo personalizado tendrá celdas vacías para el texto localizable. Agregue los valores localizados para esos elementos.

> [!NOTE]
> Si ha cambiado el nombre para mostrar o la descripción de cualquier entidad estándar o campo de la entidad, las cadenas localizadas seguirán reflejando las traducciones del valor original. Estas deberían localizarse para reflejar el nuevo valor.

La pestaña **Cadenas para mostrar** contiene el texto que se muestra para otros elementos de la IU, como comandos de la cinta de opciones, mensajes de error y etiquetas del formulario.

### <a name="updating-localizable-text-in-the-base-language"></a>Actualizar el texto localizable en el idioma base

Si cambia el nombre para mostrar para cualquier entidad o campo de la entidad que está incluido en algún mensaje especial, puede actualizar la información en la pestaña **Cadenas para mostrar** para usar el nombre personalizado.

> [!TIP]
> Aunque la interfaz de usuario expuesta a la edición de mensajes de entidades del sistema incluye muchas referencias a nombres de entidades, no incluye todas ellas. Con esta técnica puede encontrar información adicional. Más información: [Editar mensajes de entidad del sistema](../common-data-service/edit-system-entity-messages.md)

Por ejemplo, si cambia el nombre para mostrar de la entidad Cuenta a *Compañía*, busque en la columna de idioma base en **Cadenas para mostrar** las coincidencias siguientes: `account`, `accounts`, `Account` y `Accounts`, y luego realice las sustituciones correspondientes en `company`, `companies`, `Company` y `Companies`, respectivamente.

> [!IMPORTANT]
> No haga una búsqueda/sustitución general en el archivo para ello. Debe prestar atención para que el texto coincidente haga referencia a los nombres que ha cambiado.


## <a name="import-the-localized-text"></a>Importar el texto localizado
Para importar el texto es necesario comprimir los archivos e importarlos al sistema.

### <a name="compress-the-files"></a>Comprimir los archivos

Una vez realizados los cambios en el archivo `CrmTranslations.xml`, debe comprimir el archivo junto el archivo `[Content_Types].xml` en formato ZIP. Simplemente seleccione *ambos archivos* y haga clic con el botón derecho para abrir el menú contextual. En el menú contextual, elija **Enviar a** > **Carpeta comprimida (en zip)**.

### <a name="import-the-files"></a>Importar los archivos

Desde la misma solución no administrada desde la que exportó las traducciones, en el menú elija **Traducciones** > **Importar traducciones**. 

![Importar traducciones](media/import-translations.png)

Seleccione el archivo que contiene el texto traducido comprimido y, a continuación, seleccione **Importar**.

![Importar el archivo seleccionado](media/import-translated-text-dialog.png)

Una vez importado el texto traducido, debe publicar todas las personalizaciones para ver los cambios en sus aplicaciones.

## <a name="community-tools"></a>Herramientas de la comunidad

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) es una herramienta desarrollada por la comunidad de XrmToolbox. Use Easy Translator para exportar e importar traducciones con información contextual. 

> [!NOTE]
> Las herramientas de la comunidad no cuentan con el respaldo de Microsoft.
> Si tiene preguntas sobre la herramienta, póngase en contacto con el editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).


## <a name="next-steps"></a>Pasos siguientes
[Opciones de configuración regional y de idioma para la organización](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)<br />
[Editar mensajes de entidades del sistema](../common-data-service/edit-system-entity-messages.md)

