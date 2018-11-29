---
title: 'Comprender paneles: Componentes de paneles y FormXML (aplicaciones basadas en modelos) | Microsoft Docs'
description: Los paneles son uno de los diferentes tipos de formularios en aplicaciones basadas en modelos. Puede usar los atributos SystemForm.Type o UserForm.Type para determinar si el formulario es un panel.
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
# <a name="understand-dashboards-dashboard-components-and-formxml"></a>Comprender los paneles: FormXML y componentes de panel

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/understand-dashboards-dashboard-components-formxml -->

Los paneles son uno de los diferentes tipos de formularios en aplicaciones basadas en modelos. Puede usar el atributo de `SystemForm.Type` o de `UserForm.Type` para determinar si el formulario es un panel. Un formulario de tipo de panel tiene el valor de propiedad "0".  

 La definición del contenido y la presentación del formulario se almacena en FormXML. Más información: [Esquema XML de formularios](form-xml-schema.md)  

 Para ver ejemplos de cadenas FormXML para diferentes tipos de paneles, consulte [Ejemplos de panel](sample-dashboards.md).  

<a name="DashboardComponents"></a>   
## <a name="dashboard-components"></a>Componentes de los paneles  
 Un panel puede contener gráficos, cuadrículas, IFRAME o recursos web. De forma predeterminada, un solo panel puede contener hasta seis de estos componentes.  

<!-- In the [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] on-premises version, you can change the number of components to be displayed on a dashboard using [!INCLUDE[pn_PowerShell](../../includes/pn-powershell.md)]. More information: [Set the Number of Dashboard Controls](understand-dashboards-dashboard-components-formxml.md#set_controls_limit)-->

<!--[!INCLUDE[cc_sdk_onpremises_note](../../includes/cc-sdk-onpremises-note.md)]-->

### <a name="charts"></a>Gráficos  
 Un panel propiedad de una organización solo puede contener gráficos propiedad de una organización. Sin embargo, un panel que pertenece a un usuario puede contener gráficos que pertenecen al usuario y a la organización. Más información [Gráficos (visualizaciones) para aplicaciones basadas en modelos](view-data-with-visualizations-charts.md).  

### <a name="grids"></a>Cuestionarios  
 Las cuadrículas capturan datos de las consultas (vistas) en aplicaciones basadas en modelos. Un panel que pertenece a una organización solo puede contener cuadrículas que capturen datos de las consultas guardadas. Sin embargo, un panel que pertenece a un usuario puede contener cuadrículas que capturen datos del usuario y de las cuadrículas guardadas. Más información: [Entidad SavedQuery](../common-data-service/reference/entities/savedquery.md) 

### <a name="iframes"></a>IFRAME  
 Cuando se agrega un IFRAME de un panel que pertenece a la organización, puede especificar si desea restringir o permitir el scripting entre marcos. Para ello, tendrá que usar el parámetro de `<Security>` en el control del IFRAME en FormXML. Sin embargo, para los paneles de propiedad del usuario, se restringe el scripting entre marcos para los IFRAME y no se puede cambiar. Si intenta crear un panel de propiedad del usuario que contiene un IFRAME con scripting entre marcos habilitado, se mostrará un mensaje de error.  

### <a name="web-resources"></a>Recursos web  
 Solo los recursos web habilitados del formulario pueden incluirse en un panel. Aunque esta restricción se aplica cuando agrega un recurso web mediante el diseñador de paneles en la aplicación web, no se aplica cuando se agrega un recurso web a un panel mediante el SDK. Más información [Recursos web para aplicaciones basadas en modelos](web-resources.md)

<a name="DashboardComponentsandFormXML"></a>   
## <a name="dashboard-components-and-formxml-elements"></a>Componentes del panel y elementos de FormXML  
 Los componentes del panel se muestran en aplicaciones basadas en modelos según los valores especificados en el FormXML. La siguiente imagen muestra un ejemplo de un panel. Cada panel puede incluir varias pestañas. Las pestañas son una pila vertical que separa el cuerpo del panel, y pueden expandirse o contraerse. Una pestaña puede contener varias secciones. Las secciones permiten agrupar y distribuir los componentes del panel. 

 <!-- TODO: image not found ![Dashboard components layout](../media/crm-v5s-dashboards-components.png "Dashboard components layout")   -->

<a name="SupportedFormXMLElements"></a>   
## <a name="formxml-elements-supported-for-dashboards"></a>Elementos de FormXML admitidos por los paneles  
 Si bien los paneles son un tipo de formulario, no todos los elementos y atributos de FormXML son compatibles con los paneles. La siguiente tabla brinda información acerca de los elementos de FormXML, elementos secundarios y atributos compatibles con paneles.

 Para ver ejemplos de cadenas FormXML para diferentes tipos de paneles, consulte [Ejemplos de panel](sample-dashboards.md).  


|    Elemento     |                                                                                                                                                                                                                          Elementos secundarios                                                                                                                                                                                                                          |                                          Atributos de los elementos                                          |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
|    `<form>`    |                                                                                                                                                                                                                             `<tabs>`                                                                                                                                                                                                                             |                                                  -                                                   |
|    `<tabs>`    |                                                                                                                                                                                                                             `<tab>`                                                                                                                                                                                                                              |                                                  -                                                   |
|    `<tab>`     |                                                                                                                                                                                                               -   `<labels>`<br />-   `<columns>`                                                                                                                                                                                                                | -   id.<br />-   nombre<br />-   expandido<br />-   verticallayout<br />-   showlabel<br />-   locklevel |
|   `<labels>`   |                                                                                                                                                                                                                            `<label>`                                                                                                                                                                                                                             |                                                  -                                                   |
|   `<label>`    |                                                                                                                                                                                                                                -                                                                                                                                                                                                                                 |                                -   descripción<br />-   languagecode                                 |
|  `<columns>`   |                                                                                                                                                                                                                            `<column>`                                                                                                                                                                                                                            |                                                  -                                                   |
|   `<column>`   |                                                                                                                                                                                                                           `<sections>`                                                                                                                                                                                                                           |                                                width                                                 |
|  `<sections>`  |                                                                                                                                                                                                                           `<section>`                                                                                                                                                                                                                            |                                               addedby                                                |
|  `<section>`   |                                                                                                                                                                                                                 -   `<labels>`<br />-   `<rows>`                                                                                                                                                                                                                 |              -   id.<br />-   nombre<br />-   showlabel<br />-   showbar<br />-   columns               |
|    `<rows>`    |                                                                                                                                                                                                                             `<row>`                                                                                                                                                                                                                              |                                               addedby                                                |
|    `<row>`     |                                                                                                                                                                                                                             `<cell>`                                                                                                                                                                                                                             |                                               addedby                                                |
|    `<cell>`    |                                                                                                                                                                                                               -   `<labels>`<br />-   `<control>`                                                                                                                                                                                                                |      -   automático<br />-   addedby<br />-   id.<br />-   showlabel<br />-   rowspan<br />-   colspan      |
|  `<control>`   |                                                                                                                                                                                                                          `<parameters>`                                                                                                                                                                                                                          |                                       -   id.<br />-   classid                                        |
| `<parameters>` | -   `<Url>`<br />-  `<PassParameters>`<br />-   `<Security>`<br />-   `<Scrolling>`<br />-   `<Border>`<br />-   `<ViewIds>`<br />-   `<ViewId>`<br />-   `<IsUserView>`<br />-   `<IsUserChart>`<br />-   `<TargetEntityType>`<br />-   `<AutoExpand>`<br />-   `<RecordsPerPage>`<br />-   `<EnableQuickFind>`<br />-   `<EnableJumpBar>`<br />-   `<EnableChartPicker>`<br />-   `<EnableViewPicker>`<br />-   `<ChartGridMode>`<br />-   `<VisualizationId>` |                                                  -                                                   |

<a name="set_controls_limit"></a>   
## <a name="set-the-number-of-dashboard-controls"></a>Establece el número de controles del panel  
 Puede usar Windows PowerShell para ajustar el número de controles del panel que se describió aquí. El valor máximo es 20.  

#### <a name="to-retrieve-and-set-the-dashboard-limit"></a>Para recuperar y establecer el límite de panel  

1. Abra una ventana de comando de Windows PowerShell.  

2. Agregue el complemento WindowsPowerShell de aplicaciones basadas en modelos:  

   ```powershell  
   Add-PSSnapin Microsoft.Crm.PowerShell  
   ```  

3. Recupere la configuración actual:  

   ```powershell  
   $setting = Get-CrmSetting -SettingType DashboardSettings  
   ```  

4. Modifique la configuración actual:  

   ```powershell  
   $setting.MaximumControlsLimit = 5  
   ```  

   ```powershell  
   Set-CrmSetting -Setting $setting  
   ```  

### <a name="see-also"></a>Vea también  
 [Paneles](analyze-data-with-dashboards.md)   
 [Acciones en los paneles](actions-dashboards.md)   
 [Crear un panel](create-dashboard.md)   
