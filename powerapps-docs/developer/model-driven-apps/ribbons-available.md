---
title: Cintas de opciones disponibles en aplicaciones basadas en modelos | Microsoft Docs
description: En este tema se describe cómo se definen y modifican las cintas de opciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c839738bb0ab1a533a432ea4d6e8ad6be1f7a6ce
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754565"
---
# <a name="ribbons-available"></a>Cintas de opciones disponibles

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/ribbons-available-microsoft-dynamics-365 -->

En este tema se describe cómo se definen y modifican las cintas de opciones en aplicaciones basadas en modelos.

<a name="ribbon_defs"></a>   
## <a name="ribbon-definitions"></a>Definiciones de cintas de opciones  
 Las aplicaciones basadas en modelos contienen definiciones `<RibbonDiffXml>` predeterminadas para todas las cintas de opciones de la aplicación. Puede exportar y ver el código XML que define actualmente la cinta de opciones de su organización, pero no puede actualizar directamente el XML. La definición de la cinta se personaliza definiendo cómo se desea que cambie. Las definiciones de los cambios que especifique se aplican en tiempo de ejecución cuando la cinta se muestra en la aplicación. Todos los cambios estarán en los elementos `<CustomAction>` o `<HideCustomAction>`. Estos elementos se aplican sobre las definiciones de cintas de opciones predeterminadas proporcionadas por aplicaciones basadas en modelos.  

 Cuando escriba definiciones de cambios, normalmente deberá consultar con frecuencia las definiciones de las cintas de opciones predeterminadas. Por ejemplo, si desea ocultar un elemento específico de la cinta de opciones, deberá conocer el identificador único del elemento. Si desea situar un nuevo elemento de cinta de opciones dentro o junto a un elemento de cinta de opciones existente, deberá conocer los valores de los identificadores de los elementos, así como el orden de la secuencia que controlará la posición relativa de los elementos.  

 Debido a este requisito de hacer referencia a las definiciones de los elementos existentes de las cintas de opciones, es muy importante comprender las definiciones actuales de las cintas de opciones de la organización. Hay dos mensajes que puede usar para exportar los archivos XML que representan el estado actual de las cintas de opciones. Esas definiciones incluyen las personalizaciones que ya se han aplicado en el sistema de modo que pueda personalizar las cintas de opciones personalizadas que se aplicaron previamente. Para obtener más información, consulte [Exportar definiciones de cinta de opciones](export-ribbon-definitions.md).  

 Para ayudarle a empezar puede descargar las definiciones de cintas de opciones predeterminadas para MDA desde [Descargas de Microsoft: ExportedRibbonXml.zip](https://download.microsoft.com/download/C/2/A/C2A79C47-DD2D-4938-A595-092CAFF32D6B/ExportedRibbonXml.zip). El archivo ExportedRibbonXml.zip incluye los archivos de salida que tendría en una organización con una cinta de opciones que no se ha personalizado. No es necesario ejecutar la aplicación de ejemplo para exportar estos datos. Si tiene una cinta personalizada, debe ejecutar la aplicación de ejemplo para actualizar los archivos de esta carpeta con las personalizaciones que haya aplicado previamente a la organización.  

 En los archivos XML de cinta de opciones exportados, el archivo applicationRibbon.xml incluye todas las cintas de opciones que no se han definido para una entidad específica. Son las que corresponden al componente de la solución **Cintas de opciones de la aplicación**. Para cada entidad, encontrará un archivo *nombre de la entidad*ribbon.xml. Este corresponde al `RibbonDiffXml` que se incluye en cada entidad. Si desea modificar la cinta de opciones para una entidad específica, debe buscar el archivo XML de cinta de opciones de esa entidad.  

<a name="entity_ribbons"></a>   
## <a name="entity-ribbons"></a>Cintas de opciones de entidad  
 Todas las entidades usan una definición de cinta de opciones común denominada *plantilla de cinta de opciones de la entidad*. La definición de la plantilla de cinta de opciones de la entidad se encuentra en el archivo applicationribbon.xml. Cuando cree una entidad personalizada, la cinta de opciones que verá es la cinta de opciones predeterminada especificada por la plantilla de cinta de opciones de la entidad. Cada entidad del sistema tiene su propia definición de `<RibbonDiffXml>` que modifica a la definición de la plantilla de cinta de opciones de la entidad.  

 En el archivo applicationribbon.xml, podrá ver las siguientes pestañas que se aplican a todas las entidades:  

- `Mscrm.Form.{!EntityLogicalName}.MainTab`  

   Esta pestaña muestra el nombre para mostrar de la entidad en la etiqueta.  

- `Mscrm.Form.{!EntityLogicalName}.Related`  

   Esta pestaña tiene la etiqueta **Agregar**.  

- `Mscrm.Form.{!EntityLogicalName}.Developer`  

   Esta pestaña tiene la etiqueta **Personalizar**.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.MainTab`  

   Esta pestaña muestra el nombre para mostrar de la entidad plural en la etiqueta.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.View`  

   Esta pestaña tiene la etiqueta **Ver**.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.Related`  

   Esta pestaña tiene la etiqueta **Agregar**.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.Developer`  

   Esta pestaña tiene la etiqueta **Personalizar**.  

- `Mscrm.SubGrid.{!EntityLogicalName}.ContextualTabs`  

   Cuando una subcuadrícula de un formulario o un gráfico tiene el foco, la pestaña contextual aparece con la etiqueta **Herramientas de listas**.  

  -   `Mscrm.SubGrid.{!EntityLogicalName}.MainTab`  

       Esta pestaña muestra el nombre para mostrar de la entidad plural.  

  Al ver las definiciones de la cinta de opciones de una entidad específica, verá que el nombre de la entidad normalmente reemplaza al símbolo `{!EntityLogicalName}`. Cuando se ve el símbolo `{!EntityLogicalName}` en la definición de la cinta de opciones de una entidad específica, significa que no hay una definición específica para esa entidad y simplemente usa la definición de la plantilla de cinta de opciones de la entidad. Cuando defina las cintas de una entidad específica, use siempre el nombre real de la entidad. Las modificaciones de la cinta de opciones de una entidad específica deben definirse en el nodo `//ImportExportXml/Entities/Entity/RibbonDiffXml`.  

  Puede realizar cambios que se apliquen a todas las entidades definiendo los cambios en las cintas de opciones de la aplicación sustituyendo el símbolo `{!EntityLogicalName}` en lugar del nombre lógico de una entidad en el nodo RibbonDiffXml. Los cambios a las cintas de opciones de la aplicación que se definen para todas las entidades deben definirse en el nodo `ImportExportXml/RibbonDiffXml`. No pueden definirse en el nodo RibbonDiffXml de una entidad específica.  

### <a name="grid-ribbons"></a>Cintas de opciones de cuadrícula  
 La cinta de opciones de cuadrícula de entidad es una recopilación de pestañas que tienen un valor de atributo de identificador que comienza por `Mscrm.HomepageGrid.<entity logical name>`. Por ejemplo, la pestaña con el texto "Cuentas" en una cuadrícula de entidad de cuenta es `Mscrm.HomepageGrid.account.MainTab`. Todas las pestañas que se muestren en la cuadrícula de entidad de cuenta tendrán un valor de identificador que comienza por `Mscrm.HomepageGrid.account`.  

<a name="BKMK_SubGridRibbons"></a>   
### <a name="subgrid-ribbons"></a>Cintas de opciones de subcuadrícula  
 La cinta de opciones de subcuadrícula de entidad es un grupo contextual con una recopilación de pestañas que tienen un valor de atributo de identificador que comienza por `Mscrm.SubGrid.<entity logical name>`. Por ejemplo, la pestaña con el texto "Cuentas" en una subcuadrícula de entidad de cuenta es `Mscrm.SubGrid.account.MainTab`.  

 Cuando se muestre una lista de registros de una entidad en una subcuadrícula en el formulario de otra entidad o en un gráfico, solo habrá tres controles disponibles directamente encima o dentro de la subcuadrícula. Los comportamientos de estos controles se pueden modificar cambiando los comandos que tienen asociados.  

- **Agregar** El comportamiento predeterminado del comando con el icono ![botón Agregar](media/customization-subgrid-add.PNG "Botón Agregar") depende de si los registros de la subcuadrícula están relacionados con el registro actual.  

     Si los registros están relacionados con el registro actual, el comportamiento predeterminado es buscar registros existentes. Si no se encuentra un registro existente, o si el usuario simplemente desea para crear un nuevo registro, puede hacer clic en **Agregar nuevo**.  

     Si los registros no están relacionados con el registro actual, el comportamiento predeterminado es agregar un nuevo registro. Si la entidad tiene un formulario Creación rápida este se mostrará; si no lo tiene, se mostrará un nuevo formulario completo.  

     Las actividades son la excepción a este patrón. El comando de agregar siempre preguntará primero el tipo de actividad.

     > [!NOTE]
     >  El modo sin conexión en Microsoft Dynamics 365 no admite relación de varios a varios en entidades personalizadas. Por este motivo, el botón **Agregar nuevo** en una subcuadrícula en Dynamics 365 en modo sin conexión no se mostrará.

- **Mostrar lista** El comando con el icono ![botón Abrir vista](media/customization-open-view.PNG "Botón Abrir vista") abrirá la lista completa donde se pueden usar todos los comandos disponibles.  

     Si la subcuadrícula está asociada con el registro actual, el comportamiento predeterminado de este comando es abrir la vista asociada.  

     Si la subcuadrícula no está asociada con el registro actual, el comportamiento predeterminado de este comando es abrir la vista en la vista de la lista principal.  

- **Eliminar** El ![icono Eliminar sublista](media/customization-subgrid-delete.PNG "Icono Eliminar sublista") aparece en la parte derecha de la fila cuando se mantiene el mouse sobre los registros de la lista.  

     Para los registros con un una relación de 1:N o sin relación, el comportamiento predeterminado es eliminar el registro. La eliminación puede estar bloqueada si está prohibida debido a la configuración de la relación. Las actividades abiertas y las facturas son ejemplos comunes de registros que no pueden eliminarse debido a la configuración de la relación.  

     Para las relaciones que muestran relaciones de N:N el comportamiento predeterminado consiste en quitar la relación que une los registros en lugar del registro propiamente dicho.  

  Puede cambiar el comportamiento predeterminado cambiando las acciones asociadas con el comando mediante `<CommandDefinition>`, pero no puede cambiar el nombre del comando. Por ejemplo, puede cambiar la acción de eliminación de modo que desactive el registro en lugar de eliminarlo.  

  No es posible cambiar los iconos que se muestran para estos comandos. 
  Puede ocultar estos comandos mediante `<HideCustomAction>`.  

### <a name="form-ribbons"></a>Cintas de opciones de formulario  
 Cada entidad puede tener varios formularios. Puede definir cambios en la cinta de opciones de formulario para todos los formularios de una entidad agregando la definición en el nivel de entidad (`//ImportExportXml/Entities/Entity/RibbonDiffXml`).  

 Cada formulario de entidad puede tener una definición específica de la cinta de opciones. En el archivo customizations.xml exportado, deberá agregar el `<RibbonDiffXml>` modificado en esta ubicación: `//ImportExportXml/Entities/Entity/FormXml/forms/systemform/form/RibbonDiffXml`.  

 La cinta de opciones de formulario de entidad es una recopilación de pestañas que tienen un valor de atributo de identificador que comienza por `Mscrm.Form.<entity logical name>`. Por ejemplo, la pestaña con la etiqueta **Cuenta** en un formulario de entidad de cuenta es `Mscrm.Form.account.MainTab`. Todas las pestañas que se muestren en el formulario de entidad de cuenta tendrán un valor de identificador que comienza por `Mscrm.Form.account`.  

<a name="BKMK_BasicHomeTab"></a>   
## <a name="basic-home-tab"></a>Pestaña de inicio básica  
 La pestaña de inicio básica se muestra en la cinta de opciones principal de la aplicación siempre que no se haya definido una pestaña alternativa debido al contexto de la entidad o a una regla de visualización que la suprima para determinadas páginas. Por ejemplo, esta pestaña se muestra cuando se ve la **Ayuda** de MDA. El identificador de la pestaña de inicio básica es `Mscrm.BasicHomeTab`.  

<!-- [!NOTE]-->
<!-- >  The Jewel that was shown in [!INCLUDE[pn_crm2011_and_online](../../includes/pn-crm2011-and-online.md)] is no longer displayed. Changes to the Jewel will not appear in [!INCLUDE[pn_dynamics_crm_online](../../includes/pn-dynamics-crm-online.md)]  -->

<!--<a name="outlook_ribbons"></a>   
## [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] for Microsoft Office Outlook ribbons  
 [!INCLUDE[pn_MS_Outlook_Full](../../includes/pn-ms-outlook-full.md)] 2007 do not display a ribbon. [!INCLUDE[ribbon_enum_Version_2010](../../includes/ribbon-enum-version-2010.md)] uses the ribbon. You can use [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] ribbon definitions to add controls to all of them.  -->

<!--### Microsoft Office Outlook 2007  
 The [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)] controls to support older versions of [!INCLUDE[pn_MS_Outlook_Full](../../includes/pn-ms-outlook-full.md)] toolbars and menus are defined as tabs with the Id values of `Mscrm.LegacyOfficeToolbar` and `Mscrm.LegacyOfficeMenubar`, respectively.  -->

<!--### Microsoft Office Outlook 2010  
 The [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)] controls to support [!INCLUDE[ribbon_enum_Version_2010](../../includes/ribbon-enum-version-2010.md)] toolbars and menus are defined as tabs with the Id values of `Mscrm.Outlook14GlobalToolbar` and `Mscrm.Outlook14GlobalMenubar`, respectively.  -->

<a name="other_ribbons"></a> ## Otras cintas de opciones MDA define otras pestañas de la cinta de opciones con propósitos especiales y un grupo contextual.
Cada pestaña está asociada a una `<TabDisplayRule>` específica que controla cuándo se muestra. La siguiente tabla muestra estas pestañas.  


|                 Pestaña                  |             Identificador raíz              |                                                              Descripción                                                              |
|--------------------------------------|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|     Pestaña de la página Editar recurso web.      |    `Mscrm.WebResourceEditTab`    |                                        Se muestra cuando se editan recursos web dentro de una solución.                                         |
|           Pestana del Editor de formularios            |      `Mscrm.FormEditorTab`       |                               Proporciona los grupos de acciones Guardar, Editar, Seleccionar y Ver para los formularios de entidad.                               |
|        Pestaña Insertar del Editor de formularios        |   `Mscrm.FormEditorInsertTab`    |                               Proporciona botones para insertar secciones, pestañas y controles en los formularios de entidad.                                |
|        Pestaña de la página principal del panel        |       `Mscrm.DashboardTab`       |                                                    Se muestra en el Área de trabajo.                                                    |
| Grupo contextual Herramientas de visualización |    `Mscrm.VisualizationTools`    |             Se muestra cuando se hace clic en el botón **Nuevo gráfico** en la pestaña **Gráficos** que se muestra en la cinta de opciones de cuadrícula de entidad.              |
|       Ficha de la página principal de AptbookTab        |        `Mscrm.AptbookTab`        |                                    Se muestra cuando se visualiza el Calendario de servicios en el área Servicios.                                    |
|          Pestaña Búsqueda avanzada           |       `Mscrm.AdvancedFind`       |                                               Se muestra en la ventana **Búsqueda avanzada**.                                               |
|         Pestaña Editor de paneles         |    `Mscrm.DashboardEditorTab`    |                                                  Se muestra cuando se edita un panel.                                                   |
|            Pestaña Documentos             |       `Mscrm.DocumentsTab`       | Se muestra si se ha habilitado la integración de SharePoint para la organización. |
|           Pestaña Editor de gráficos           | `Mscrm.VisualizationDesignerTab` |                                       Se muestra cuando se edita un gráfico desde la ventana de soluciones.                                        |
|    Grupo contextual Herramientas de búsqueda     |      `Mscrm.ArticleSearch`       |                                             Se muestra cuando se ve la entidad `KBarticle`.                                             |

<a name="BKMK_RibbonsForCustomPages"></a>

## <a name="ribbons-for-custom-pages"></a>Cintas de opciones para las páginas personalizadas

Puede mostrar páginas personalizadas en la navegación de la aplicación mediante el mapa del sitio. Estas páginas siempre mostrarán la [pestaña de inicio básica](ribbons-available.md#BKMK_BasicHomeTab) (`Mscrm.BasicHomeTab`). 

No es posible usar una regla `<PageRule>` para habilitar o mostrar componentes de cinta de opciones personalizados en las páginas personalizadas.  

### <a name="see-also"></a>Vea también  
 [Personalizar la cinta de opciones](customize-commands-ribbon.md)   
 [Presentación de la barra de comandos o la cinta de opciones](command-bar-ribbon-presentation.md)
