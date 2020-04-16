---
title: Crear un panel (aplicaciones basadas en modelos) | Microsoft Docs
description: Se pueden crear paneles propiedad de la orgqanización utilizando los servicios web (SDK) de Common Data Service o mediante la personalización del formulario de entidad en Common Data Service al modificar el archivo customizations.xml.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: da41f997-1f61-7ea8-db83-5d670d708d67
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 02b8e2b80821e3a59f3522f25f455d6cc3b4a083
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115916"
---
# <a name="create-a-dashboard"></a>Crear un panel

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/create-dashboard -->

Los paneles de propiedad de la organización se pueden crear usando los Common Data Service o personalizando el formulario de entidad en Common Data Service mediante la edición del archivo customizations.xml.  
  
> [!NOTE]
>  Algunos paneles que están creados mediante el SDK o a través de la personalización del formulario de entidad no son compatibles con el diseñador de paneles en la aplicación web. Para obtener más información, consulte [Limitaciones: Creación de paneles mediante el SDK o a través de la personalización del formulario](#Limitations) más adelante en este tema.  
  
 Antes de crear un panel, tenga en cuenta lo siguiente:  
  
- **Tipo de panel**: Si desea que los paneles estén disponibles en la organización y no desea administrar los niveles de acceso en un nivel más detallado, puede crear un panel de propiedad de la organización. Sin embargo, si está preocupado por los privilegios de acceso y la seguridad de su panel, considere la posibilidad de crear un panel propiedad del usuario donde tenga más control sobre quién puede obtener acceso a éste.  
  
     Para crear paneles de propiedad de la organización, debe tener el rol de Administrador del sistema o Personalizador del sistema.  
  
- **Diseño de panel**: Cuando cree los paneles, tendrá que usar FormXML para definir los componentes y el diseño del panel. Para obtener información sobre cómo trabajar con FormXML para definir un panel, vea [Componentes del panel y elementos de FormXML](understand-dashboards-dashboard-components-formxml.md#DashboardComponentsandFormXML). Para ver algunos FormXML de ejemplo para diferentes tipos de paneles, consulte [Paneles de ejemplo](sample-dashboards.md).  
  
<a name="UsingSDK"></a>   
## <a name="create-a-dashboard-by-using-the-sdk"></a>Crear un panel mediante el SDK  
 Para crear un panel, cree una instancia de `SystemForm` para un panel que pertenece a una organización o `UserForm` para un panel propiedad del usuario. El siguiente ejemplo muestra cómo crear un panel de propiedad de una organización.  
  
 ```csharp
 //This is the language code for U.S. English. If you are running this code
//in a different locale, you will need to modify this value.
int languageCode = 1033;

//We set up our dashboard and specify the FormXml. Refer to the
//FormXml schema in the Microsoft Dynamics CRM SDK for more information.
SystemForm dashboard = new SystemForm
{
    Name = "Sample Dashboard",
    Description = "Sample organization-owned dashboard.",
    FormXml = String.Format(@"<form>
            <tabs>
                <tab name='Test Dashboard' verticallayout='true'>
                    <labels>
                        <label description='Sample Dashboard' languagecode='{0}' />
                    </labels>
                    <columns>
                        <column width='100%'>
                            <sections>
                                <section name='Information Section'
                                    showlabel='false' showbar='false'
                                    columns='111'>
                                    <labels>
                                        <label description='Information Section'
                                            languagecode='{0}' />
                                    </labels>
                                    <rows>
                                        <row>
                                            <cell colspan='1' rowspan='10' 
                                                showlabel='false'>
                                                <labels>
                                                    <label description='Top Opportunitiess - 1'
                                                    languagecode='{0}' />
                                                </labels>
                                                <control id='TopOpportunities'
                                                    classid='{{E7A81278-8635-4d9e-8D4D-59480B391C5B}}'>
                                                    <parameters>
                                                        <ViewId>{1}</ViewId>
                                                        <IsUserView>false</IsUserView>
                                                        <RelationshipName />
                                                        <TargetEntityType>opportunity</TargetEntityType>
                                                        <AutoExpand>Fixed</AutoExpand>
                                                        <EnableQuickFind>false</EnableQuickFind>
                                                        <EnableViewPicker>false</EnableViewPicker>
                                                        <EnableJumpBar>false</EnableJumpBar>
                                                        <ChartGridMode>Chart</ChartGridMode>
                                                        <VisualizationId>{2}</VisualizationId>
                                                        <EnableChartPicker>false</EnableChartPicker>
                                                        <RecordsPerPage>10</RecordsPerPage>
                                                    </parameters>
                                                </control>
                                            </cell>
                                            <cell colspan='1' rowspan='10' 
                                                showlabel='false'>
                                                <labels>
                                                    <label description='Top Opportunities - 2'
                                                    languagecode='{0}' />
                                                </labels>
                                                <control id='TopOpportunities2'
                                                    classid='{{E7A81278-8635-4d9e-8D4D-59480B391C5B}}'>
                                                    <parameters>
                                                        <ViewId>{1}</ViewId>
                                                        <IsUserView>false</IsUserView>
                                                        <RelationshipName />
                                                        <TargetEntityType>opportunity</TargetEntityType>
                                                        <AutoExpand>Fixed</AutoExpand>
                                                        <EnableQuickFind>false</EnableQuickFind>
                                                        <EnableViewPicker>false</EnableViewPicker>
                                                        <EnableJumpBar>false</EnableJumpBar>
                                                        <ChartGridMode>Grid</ChartGridMode>
                                                        <VisualizationId>{2}</VisualizationId>
                                                        <EnableChartPicker>false</EnableChartPicker>
                                                        <RecordsPerPage>10</RecordsPerPage>
                                                    </parameters>
                                                </control>
                                            </cell>
                                        </row>
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                    </rows>
                                </section>
                            </sections>
                        </column>
                    </columns>
                </tab>
            </tabs>
        </form>",
    languageCode,
    defaultOpportunityQuery.SavedQueryId.Value.ToString("B"),
    visualization.SavedQueryVisualizationId.Value.ToString("B")),
    IsDefault = false
};
_dashboardId = _serviceProxy.Create(dashboard);
 ``` 
  
 Para ver un ejemplo completo, vea [Ejemplo: Crear, recuperar, actualizar y eliminar (CRUD) un panel](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard) Para obtener un ejemplo para crear un panel de propiedad del usuario y asignarlo a otro usuario, consulte [Ejemplo: Asignar un panel propiedad del usuario a otro usuario](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-user-owned-dashboard-another-user).  <!-- TODO relevant powerapps repo topic must be linked> 
  
<a name="UsingFormCustomization"></a>   
## <a name="create-an-organization-owned-dashboard-by-customizing-the-entity-form"></a>Crear un panel de propiedad de la organización al personalizar el formulario de entidad  
 El archivo customizations.xml que se exporta con una solución no administrada contiene las definiciones de los paneles y los formularios de entidad. Puede agregar o modificar el archivo customizations.xml para agregar o actualizar un panel.  
  
#### <a name="create-a-dashboard-by-customizing-an-entity-form"></a>Cree un panel al personalizar el formulario de entidad  
  
1. Inicie sesión en Common Data Service.  
  
2. Exporte una solución. Para obtener información sobre cómo hacerlo, vea [Exportar, preparar para editar e importar la cinta de opciones](export-prepare-edit-import-ribbon.md).  
  
3. Explore el archivo customizations.xml en la carpeta de la solución exportada y, ábrala para editar.  
  
4. Explore detalladamente el área de paneles en el archivo customizations.xml y busque la siguiente etiqueta: `</Dashboards>`  
  
5. Antes de la etiqueta `</Dashboards>` , agregue lo siguiente para definir un nuevo panel:  
  
   ```xml  
   <Dashboard>  
      <LocalizedNames>  
         <LocalizedName description="Dashboard_Name" languagecode="1033" />  
      </LocalizedNames>     
      <IsCustomizable>1</IsCustomizable>  
      <IsDefault>0</IsDefault>  
      <FormXml>  
         <forms type="dashboard">  
   *** Dashboard definition goes here. *** // See “Sample Dashboards” topic for the FormXML content to be used here.  
         </forms>  
      </FormXml>  
   </Dashboard>  
   ```  
  
6. Guarde el archivo customizations.xml.  
  
7. Importe el archivo .zip como una solución en Common Data Service. Más información: [Exportar, preparar para editar e importar la cinta de opciones](export-prepare-edit-import-ribbon.md).  
  
<a name="Limitations"></a>   

## <a name="limitations-creating-dashboards-by-using-the-sdk-or-through-form-customization"></a>Limitaciones: Creación de paneles mediante el SDK o a través de la personalización del formulario  

 Algunos paneles que están creados o modificados mediante el Common Data Service o a través de la personalización del formulario de entidad no son compatibles con el diseñador de paneles en la aplicación web. Evite lo siguiente mientras crea o edita un panel mediante el SDK o a través de la personalización del formulario.  
  
### <a name="general"></a>General  
  
- **Problema**: Puede crear un panel que contenga una pestaña sin ninguna sección definida en el FormXML.  
  
  **Resolución**: Asegúrese de crear un panel con al menos una sección definida para cada pestaña del FormXML.  
  
- **Problema**: Puede crear un panel que no tenga el mismo número de elementos de `<row>` para una sección como se especifica en la propiedad de `rowspan` de un elemento de `<cell>` de la sección en el FormXML. En el mejor de los casos, el valor de propiedad de `rowspan` de un elemento de `<cell>` y el número de elementos de `<row>` en una sección deben ser la misma.  
  
  **Problema**: Asegúrese de crear un panel que tenga el mismo número de elementos de `<row>` para una sección como se especifica en la propiedad de `rowspan` de un elemento de `<cell>` de la sección.  
  
### <a name="grids"></a>Cuadrículas  
 **Problema**: Puede crear un panel que contiene las cuadrículas con el valor de parámetro de `<AutoExpand>` establecido en `Auto` para la cuadrícula.  
  
 **Resolución**: Asegúrese de especificar el valor de parámetro de `<AutoExpand>` como `Fixed` para las cuadrículas en el FormXML mientras crea un panel.  
  
### <a name="iframes"></a>IFRAME  
 **Problema**: Puede crear un panel que contenga un IFRAME. Esto ocurre si no especifica un valor del parámetro de `<Url>` para el control de IFRAME en el FormXML.  
  
 **Resolución**: Asegúrese de especificar un valor para el parámetro de `<Url>` mientras crea un IFRAME en el FormXML.  
  
### <a name="see-also"></a>Vea también  
 [Paneles](analyze-data-with-dashboards.md)   
 [Uso de FormXML para paneles](understand-dashboards-dashboard-components-formxml.md)   
 [Acciones en los paneles](actions-dashboards.md)   
 [Paneles de ejemplo](sample-dashboards.md)   
 [Ejemplo: crear, recuperar, actualizar y eliminar (CRUD) un panel](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard)   <!-- TODO relevant powerapps repo topic must be linked-->
 [Personalizar formularios de entidad](customize-entity-forms.md)
