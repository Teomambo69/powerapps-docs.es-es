---
title: Editar el archivo XML de personalizaciones con la validación de esquema (aplicaciones basadas en modelos) | MicrosoftDocs
description: El archivo customizations.xml se incluye en el archivo .zip comprimido exportado como solución. Determinadas partes del archivo customizations.xml se pueden editar manualmente. La información sobre el esquema ayuda a confirmar que cualquier modificación que cree es válida.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
- ''
ms.topic: article
ms.assetid: b77d962e-6e3c-bd28-d03c-cf2e23cd742d
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 39948d6193a156fe67ec282bbdea4310105f016b
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276152"
---
# <a name="edit-the-customizations-xml-file-with-schema-validation"></a>Editar el archivo XML de personalizaciones con la validación de esquema

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/edit-customizations-xml-file-schema-validation -->

El archivo customizations.xml se incluye en el archivo .zip comprimido exportado como solución. Determinadas partes del archivo customizations.xml se pueden editar manualmente. La información sobre el esquema ayuda a confirmar que cualquier modificación que cree es válida.  
  
## <a name="xsd-schema-files"></a>Archivos de esquema XSD:  
 [!INCLUDE[schema_download](../../includes/schema-download.md)] para los archivos de esquema XSD utilizados para validar el archivo customization.xml en una solución. Los archivos necesarios son:  
  
- CustomizationsSolution.xsd  
  
- fetch.xsd  
  
- FormXml.xsd  
  
- isv.config.xsd  
  
- RibbonCore.xsd  
  
- RibbonTypes.xsd  
  
- RibbonWSS.xsd  
  
- SiteMap.xsd  
  
- SiteMapType.xsd  
  
- VisualizationDataDescription.xsd  
  
  
<a name="BKMK_UseSchemaValidation"></a>

## <a name="using-schema-validation"></a>Usar la validación de esquema  
 Como el archivo XML exportado es un archivo de texto, puede modificarlo con un editor de texto como [!INCLUDE[pn_Notepad](../../includes/pn-notepad.md)]. Sin embargo, se recomienda usar una aplicación que admita validación de esquema XSD como [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)]. Validación de XSD en [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)] <!-- TODO - need to fix this link. The page is not available (or [Visual Studio Express 2012 for Web](https://www.microsoft.com/visualstudio/eng/products/visual-studio-express-for-web))--> proporciona información de [!INCLUDE[pn_IntelliSense](../../includes/pn-intellisense.md)] y comprobación de esquemas para evitar errores.  
  
 Los archivos de esquema XSD utilizados para validar el archivo customization.xml en una solución están disponibles aquí. [!INCLUDE[schema_download](../../includes/schema-download.md)]. Asegúrese de copiar todos los archivos de esa carpeta en el mismo directorio. Necesitará asociar el archivo customizations.xml al archivo CustomizationsSolution.xsd. Ese archivo contiene vínculos al resto de archivos XSD en la carpeta.  
  
1. Descargue los archivos de esquema XSD y cópielos todos en su equipo. Guárdelos en la ubicación que [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)] usa para los archivos de validación XSD. Esta ubicación probablemente es `[install drive]\Program Files (x86)\Microsoft Visual Studio X.0\Xml\Schemas` donde `X` representa la versión de [!INCLUDE[pn_Visual_Studio_short](../../includes/pn-visual-studio-short.md)].  
  
2. Haga clic con el botón secundario en el archivo customizations.xml y seleccione **Abrir con** y, a continuación, la versión de [!INCLUDE[pn_Visual_Studio_short](../../includes/pn-visual-studio-short.md)].  
  
3. Seleccione **Ver** y luego seleccione **Ventana Propiedades**.  
  
4. En la ventana **Propiedades**, en el campo **Esquemas**, haga clic en el botón de puntos suspensivos [**...**].  
  
5. En el cuadro de diálogo **Esquemas XML** debería aparecer customizationsSolution.xsd. En la columna **Usar**, seleccione **Use este esquema**.  
  
   > [!NOTE]
   >  Si no lo ve, haga clic en **Agregar** y busque donde lo guardó.  
  
6. Haga clic en **Aceptar**.  
  
   Ya está listo para empezar a editar el XML con validación de XSD.  
  
### <a name="see-also"></a>Vea también

[Cuándo modificar el archivo de personalizaciones para Common Data Service](when-edit-customization-file.md)<br/> 
[Esquema central de cinta de opciones](ribbon-core-schema.md)<br/>
[Esquema de tipos de cinta](ribbon-types-schema.md)<br/>
[Esquema WSS de cinta](ribbon-wss-schema.md)<br/>
[Esquema de mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/sitemap-schema)<br/>   <!-- TODO need to fix link relevant to the topic in powerapps repo-->
[Esquema XML de formulario](form-xml-schema.md)     
[Esquema de archivo de configuración ISV](/dynamics365/customer-engagement/developer/customize-dev/isv-configuration-file-schema)<br/>   <!-- TODO need to fix link relevant to the topic in powerapps repo-->
[Crear consultas con FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml) <!-- TODO need to fix link relevant to the topic in powerapps repo-->
