---
title: Agregar la pestaña Documentos al formulario principal de una entidad | MicrosoftDocs
description: Aprender a agregar la pestaña Documentos al formulario principal de una entidad
s.custom: ''
ms.date: 09/05/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: fae464925ea755a1f9fd0cd77426bfdbaad6141c
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909348"
---
# <a name="add-the-sharepoint-documents-tab-to-the-main-form-for-an-entity"></a>Agregar la pestaña documentos de SharePoint al formulario principal de una entidad
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Agregar una pestaña en un formulario de entidad principal para documentos de SharePoint ayuda a los usuarios a detectar y usar las características de integración de SharePoint que están disponibles en una aplicación basada en modelo. 

![Pestaña de archivos de documento](media/document-files-tab.png)

> [!IMPORTANT]
> Debe habilitar la administración de documentos para usar esta característica. Más información: [Administrar los documentos utilizando SharePoint](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)

## <a name="add-the-documents-tab-in-the-formxml"></a>Agreguar la pestaña de documentos en FormXML 
1.  Cree una nueva solución. Inicio sesión en Power Apps y vaya a **Soluciones**, seleccione **Nueva solución** y especifique la información necesaria y opcional. Más información: [Crear una solución](../common-data-service/create-solution.md)
2. Agregue la entidad a la solución donde desee agregar la pestaña de documentos en el formulario principal. Se admiten todas las entidades estándar y personalizadas. Más información: [Agreguar un componente existente a una solución](/powerapps/maker/common-data-service/use-solution-explorer#add-an-existing-component-to-a-solution)
3. Incluya el formulario de la entidad en la solución, como el formulario principal para la entidad de cuenta. Junto a la entidad, seleccione **...** y a continuación seleccione **Editar**. Seleccione la pestaña **Formularios**. Si el formulario que desea falta, agréguelo.   

4. Agregue una pestaña de una columna al formulario principal. Para ello, en el diseñador de formularios seleccione el área en el lienzo del formulario, seleccione **Agregar componente**y, a continuación seleccione **1 Pestaña de 1 columna**.  
   ![Insertar pestaña de una columna](media/insert-one-column-tab.png)

5. En el diseñador de formularios seleccione **Nueva pestaña** en el lienzo del diseñador de formularios, seleccione **Agregar campo**, y agregue el campo como *Dirección 1: Ciudad* desde el panel izquierdo. Puede usar cualquier campo numérico o de texto para la pestaña. ![Agregar un campo a la pestaña](media/add-field-to-tab.png)
6. Cambiar el nombre de la etiqueta de la pestaña. Para ello, seleccione **Nueva pestaña** y, en el panel derecho de propiedades reemplace **Nueva pestaña** con algo más descriptivo, como *Archivos*.
7. Seleccione **Guardar** y **Publicar**, y luego cierre el editor de formularios. 
8. En la página principal del fabricante de Power Apps, seleccione **Soluciones**, seleccione la solución y seleccione **Exportación** para exportar la solución como una solución no administrada. Más información: [Exportar soluciones](../common-data-service/export-solutions.md) 
9. Extraiga la solución y abra el archivo customization.xml con un editor de XML o texto. 
10. En customization.xml busque **label description="Files"** (o el nombre que dio a la etiqueta de la pestaña en el paso anterior).
11. Desplácese hasta el elemento *field name*” del id de control, como **control id="address1_city"** y reemplace el elemento completo con el [Ejemplo de XML](#xml-sample-for-adding-the-documents-tab-to-a-form) en este tema. 

    > [!div class="mx-imgBorder"] 
    > ![](media/form-xml.png "XML sample insertion point")

12. Cree estas modificaciones en el ejemplo XML. 
    
     a. Localice el elemento **RelationshipName** y reemplácelo con el nombre de esquema que aparece como *entityLogicalName*_SharePointDocument. Por ejemplo, para la entidad de cuentas el nombre de esquema para la relación es Account_SharePointDocument, que es el nombre de esquema para el ejemplo de XML de este tema. Para buscar el nombre para una entidad distinta, vaya a **Configuración** > **Personalizaciones** > **Personalizar el sistema** > **Entidades** > seleccione la entidad > seleccione **Relaciones de 1: N**. Busque **Entidad relacionada** de tipo **SharePointDocument**. 

      ![Documento SharePoint de relación de cuenta](media/account-sharepointdocument.png)

     b. Cree un identificador global único (guid) y reemplace el guid **uniqueid** existente ubicado en el elemento **control** que pegó en el paso anterior al tiempo que conserva las llaves {}.  
       ![Id. único del elemento de control](media/control-unique-id.png). Guarde los cambios en customizations.xml. 
13. Abra el archivo solution.xml y aumente el valor de elemento **Versión**. Por ejemplo, cambie de *1.1.0.0* a *1.2.0.0*. 
14. Empaquete todos los archivos de solución en una carpeta comprimida e impórtela en su entorno. Si recibe un error que debe eliminar la solución anterior, hágalo. Más información: [Importar, actualizar y actualizar soluciones](../common-data-service/import-update-export-solutions.md) 

## <a name="xml-sample-for-adding-the-documents-tab-to-a-form"></a>Ejemplo de XML para agregar la pestaña de documentos a un formulario
```xml
  <control id="DocumentSubGrid" classid="{E7A81278-8635-4d9e-8D4D-59480B391C5B}" indicationOfSubgrid="true" uniqueid="{9cd66b5c-8b7a-6433-c5a5-46a7245dd534}"> 
    <parameters> 
      <ViewId>{0016F9F3-41CC-4276-9D11-04308D15858D}</ViewId> 
      <IsUserView>false</IsUserView>         
      <RelationshipName>Account_SharepointDocument</RelationshipName>
      <TargetEntityType>sharepointdocument</TargetEntityType> 
      <AutoExpand>Fixed</AutoExpand> 
      <EnableQuickFind>false</EnableQuickFind> 
      <EnableViewPicker>true</EnableViewPicker> 
      <ViewIds /> 
      <EnableJumpBar>false</EnableJumpBar> 
      <ChartGridMode>Grid</ChartGridMode> 
      <VisualizationId /> 
      <IsUserChart>false</IsUserChart> 
      <EnableChartPicker>false</EnableChartPicker> 
      <RecordsPerPage>10</RecordsPerPage> 
      <HeaderColorCode>#F3F3F3</HeaderColorCode> 
    </parameters> 
  </control> 
```

### <a name="see-also"></a>Vea también
[Administrar los documentos con SharePoint](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)