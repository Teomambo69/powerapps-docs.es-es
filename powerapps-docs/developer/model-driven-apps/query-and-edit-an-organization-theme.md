---
title: Consultar y editar un tema de organización (aplicaciones orientadas a modelos) | Microsoft Docs
description: Obtenga información sobre cómo definir y aplicar temas visuales para una organización. Esto proporciona una forma compatible de aplicar el logotipo y las opciones de color de una organización a la aplicación.
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
---
# <a name="query-and-edit-an-organization-theme"></a>Consultar y editar un tema de organización

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/query-and-edit-an-organization-theme -->

Puede definir y aplicar temas visuales a una organización. Esto proporciona una forma compatible de aplicar el logotipo y las opciones de color de una organización a la aplicación. Puede crear un tema personalizado para su aplicación realizando cambios en los colores predeterminados y los elementos visuales proporcionados en el sistema de aplicaciones orientadas a modelos. Por ejemplo, puede crear su marca de producto personal, agregar un logotipo de compañía y proporcionar colores específicos de la entidad. Los colores de tema se aplican globalmente en toda la aplicación, con la excepción de algunas áreas heredadas.  
  
<!-- [!NOTE]
> [!INCLUDE[cc_feature_included_with_2015_update_1_admins](../../includes/cc-feature-included-with-2015-update-1-admins.md)]  -->
  
 La personalización del tema se admite en esta versión solo para la aplicación web. Los cambios realizados en el tema de una organización no están incluidos en soluciones exportadas desde la organización. Puede definir varios temas, pero solo puede establecer y publicar uno como tema predeterminado.  
  
 Vídeo: [Temas](http://go.microsoft.com/fwlink/p/?LinkId=529568)  
  
<a name="BKMK_QueryTheme"></a>

## <a name="query-the-current-theme"></a>Consulte el tema actual
 Es posible que necesite consultar el tema actual utilizando código del lado cliente si tiene una solución con recursos web HTML que desea adaptar a las decisiones de tema tomadas para una organización. Puede usar la siguiente consulta con la API web para recuperar esa información.  

 **Solicitud:** 

```http
GET [Organization URI]/api/data/v9.0/themes?$filter=isdefaulttheme eq true&$select=defaultentitycolor,defaultcustomentitycolor,controlborder,controlshade,selectedlinkeffect,globallinkcolor,processcontrolcolor,headercolor,logotooltip,hoverlinkeffect,navbarshelfcolor,navbarbackgroundcolor
```

 **Respuesta:**

```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#themes(defaultentitycolor,defaultcustomentitycolor,controlborder,controlshade,selectedlinkeffect,globallinkcolor,processcontrolcolor,headercolor,logotooltip,hoverlinkeffect,navbarshelfcolor,navbarbackgroundcolor)",  
    "value": [  
        {  
            "defaultentitycolor": "#001CA5",  
            "defaultcustomentitycolor": "#006551",  
            "controlborder": "#CCCCCC",  
            "controlshade": "#F3F1F1",  
            "selectedlinkeffect": "#B1D6F0",  
            "globallinkcolor": "#1160B7",  
            "processcontrolcolor": "#D24726",  
            "headercolor": "#1160B7",  
            "logotooltip": "Model-driven apps",  
            "hoverlinkeffect": "#D7EBF9",  
            "navbarshelfcolor": "#DFE2E8",  
            "navbarbackgroundcolor": "#002050",  
            "themeid": "f499443d-2082-4938-8842-e7ee62de9a23"  
        }  
    ]  
}  
```

 Para obtener más información, consulte [Consultar datos mediante la API web](../common-data-service/webapi/query-data-web-api.md).
  
<a name="BKMK_EditAndPublish"></a>

## <a name="edit-and-publish-theme-data"></a>Editar y publicar datos de temas

 Un tema se crea mediante las herramientas de personalización de la interfaz de usuario, sin necesidad de que un programador escriba código. Encontrará información sobre cómo aplicar estas personalizaciones en [Cambiar la combinación de colores o agregar un logotipo para que coincida con la marca de la organización](/dynamics365/customer-engagement/customize/change-color-scheme-add-logo-match-organizations-brand).  

 La mayoría de datos del tema se almacenan en la entidad de tema. Personalizar colores para entidades específicas incluidas en la <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.EntityColor>. . Estos datos se exportan con la entidad si la entidad se incluye en una solución.

 La siguiente tabla describe los atributos de entidad de `Theme` que son válidos para la actualización y contienen datos que aplica el tema:  

|Nombre del esquema|Tipo|Valor del tema predeterminado|Descripción|  
|-----------------|----------|----------------------------|-----------------| 
|AccentColor|String|#E83D0F|El color del tema secundario Interfaz unificada que se utilizará en el control de proceso.| 
|BackgroundColor|String|#FFFFFF|Solo para uso interno.|
|ControlBorder|String|#BDC3C7|El color que los controles usarán para los bordes.|  
|ControlShade|String|#FFFFFF|El color que los controles usarán para indicar cuándo pasa el puntero sobre elementos.|  
|DefaultCustomEntityColor|String|#00CCA3|El color predeterminado de entidad personalizada si no se asigna ningún color.|  
|DefaultEntityColor|String|#666666|El color predeterminado para las entidades del sistema si no se asigna ningún color.|  
|GlobalLinkColor|String|#1160B7|El color para vínculos, como direcciones de correo electrónico o búsquedas.|  
|HeaderColor|String|#1160B7|El color para el texto de encabezado, como las etiquetas de las pestañas del formulario.|  
|HoverLinkEffect|String|#E7EFF7|El color que los comandos o listas usarán al pasar el puntero sobre los elementos.|  
|ImportSequenceNumber|Entero|null|Número de secuencia de la importación que creó este registro.|
|IsDefaultTheme|Valor booleano|True|El valor predeterminado de un tema personalizado es false.|
|LogoId|String|null|El nombre de un recurso web que desea usar como logotipo. Las dimensiones recomendadas son una altura de 50 píxeles y un ancho máximo de 400 píxeles.|  
|LogoToolTip|String|Aplicaciones basadas en modelos|El texto que se usará como información en pantalla y texto alternativo para el logotipo.| 
|MainColor|String|#3B79B7|El color del tema principal Interfaz unificada que se utilizará en la barra de comandos, las pestañas y los botones principales.| 
|Nombre|String|Tema predeterminado de MDA|El nombre de la entidad de tema.|  
|NavBarBackgroundColor|String|#002050|El color de barra de navegación principal.|  
|NavBarShelfColor|String|#DFE2E8|El color de barra de navegación secundaria.|  
|OverriddenCreatedOn|DateTime|null|Fecha y hora de migración del registro.|  
|PageHeaderBackgroundColor|String|#E0E0E0|El color de fondo del encabezado de página.|  
|PanelHeaderBackgroundColor|String|#F3F3F3|El color de fondo del encabezado de panel.|  
|ProcessControlColor|String|#41A053|El color principal para los controles de proceso.|  
|SelectedLinkEffect|String|#F8FAFC|El color que los comandos o listas usarán para indicar los elementos seleccionados.| 
|TransactionCurrencyId|Búsqueda|null|Tipo de cambio para la divisa asociada al tema en relación con la divisa base.| 
 
 Una vez que haya aplicado los cambios, use <xref href="Microsoft.Dynamics.CRM.PublishTheme?text=PublishTheme Action" /> o la clase <xref:Microsoft.Crm.Sdk.Messages.PublishThemeRequest> para crear uno de los registros del tema actual.  

<a name="BKMK_ExportingAndImportingThemes"></a>

## <a name="exporting-and-importing-themes"></a>Exportar e importar temas

 Dado que los temas no se incluyen como parte de una solución, si desea transferir temas de una organización a otra puede usar la herramienta Configuration Migration para generar un esquema, exportar los datos del tema e importarlos a otra organización. Para obtener más información sobre cómo usar esta herramienta, consulte [transferir datos de configuración mediante la herramienta Configuration Migration](/dynamics365/customer-engagement/admin/manage-configuration-data).  

### <a name="see-also"></a>Vea también

 [Entidad de tema](../common-data-service/reference/entities/theme.md) <br/>
 [Crear un tema](/dynamics365/customer-engagement/customize/change-color-scheme-add-logo-match-organizations-brand) <br/>
 [Guía para programadores para la personalización](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)
