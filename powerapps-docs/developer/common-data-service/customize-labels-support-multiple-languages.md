---
title: Personalizar etiquetas para admitir varios idiomas (Common Data Service) | Microsoft Docs
description: Obtenga información sobre cómo personalizar etiquetas para que admitan varios idiomas.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 759dcce9d209a904a1c8f0705414eccb88216e26
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753000"
---
# <a name="customize-labels-to-support-multiple-languages"></a>Personalizar etiquetas para admitir varios idiomas

Cuando se crean personalizaciones en Common Data Service, se puede admitir varios idiomas con etiquetas.  

<a name="BKMK_UsingLabels"></a>   

## <a name="using-labels"></a>Usar etiquetas  

|Microsoft.Xrm.Sdk.dll|API web|
|----------------|----------------|
|Clase de <xref:Microsoft.Xrm.Sdk.Label>|<xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" />|
|Clase de <xref:Microsoft.Xrm.Sdk.LocalizedLabel>|<xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" />|

 Las etiquetas son cadenas localizadas que se muestran a los usuarios en las aplicaciones cliente. Se implementan mediante `Label` (clase <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> o <xref:Microsoft.Xrm.Sdk.Label>), que admite paquetes de idiomas. Las cadenas que se muestran a los usuarios, como nombres de entidades u opciones de un conjunto de opciones, se pueden almacenar en varios idiomas. Los usuarios pueden seleccionar el idioma que desean mostrar en los formularios y vistas en Common Data Service.  

 En la siguiente tabla se enumeran todos los metadatos que usan `Label`.  

|Propiedad de metadatos|Descripción|  
|-----------------------|-----------------|  
|AttributeMetadata.Description|Descripción de un atributo.|  
|AttributeMetadata.DisplayName|Muestra el nombre de un atributo.|  
|EntityMetadata.Description|Descripción de una entidad.|  
|EntityMetadata.DisplayCollectionName|Nombre plural de una entidad.|  
|EntityMetadata.DisplayName|Nombre de una entidad.|  
|AssociatedMenuConfiguration.Label|Etiqueta usada para una entidad en una relación de entidad.|  
|OptionMetadata.Label|Etiqueta usada para una opción en una lista desplegable, estado o atributo de estado.|  

 `Label` puede almacenar una cadena para cada idioma instalado. Esta matriz es la propiedad `LocalizedLabels`. Siempre debe haber una etiqueta almacenada para el idioma base. Las etiquetas para otros idiomas pueden ser **null**. Si el usuario desea mostrar la interfaz de usuario en un idioma y la etiqueta no tiene una cadena para ese idioma, se usará la etiqueta del idioma base.  

 Puede usar la propiedad `UserLocalizedLabel` para recuperar la etiqueta del idioma seleccionado por el usuario.  

<a name="BKMK_MessagesToWorkWithLabels"></a>   

## <a name="messages-to-use-with-labels"></a>Mensajes para usar con las etiquetas  
 En la siguiente tabla se enumeran los mensajes que se pueden usar para trabajar con etiquetas localizadas que admiten varios idiomas. Al importar traducciones se puede generar un informe basado en el trabajo de importación de la misma forma que se genera cuando se importa una solución. Para obtener más información, consulte [Instalar o actualizar una solución](work-solutions.md#BKMK_InstallUpgradeSolution).  


|                                                                                          Mensaje                                                                                          |                                                    Operación de la API web                                                     |                                Ensamblado del SDK                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
|                                               ExportTranslation</br>Exporta todas las traducciones para una solución específica a un archivo comprimido.                                                |                  <xref href="Microsoft.Dynamics.CRM.ExportTranslation?text=ExportTranslation Action" />                  |         <xref:Microsoft.Crm.Sdk.Messages.ExportTranslationRequest>         |
|                                                          ImportTranslation</br>Importa todas las traducciones de un archivo comprimido.                                                           |                  <xref href="Microsoft.Dynamics.CRM.ImportTranslation?text=ImportTranslation Action" />                  |         <xref:Microsoft.Crm.Sdk.Messages.ImportTranslationRequest>         |
| RetrieveFormattedImportJobResults</br>Recupera los resultados de ImportJob como un documento XML diseñado para ser abierto mediante Office Excel. | <xref href="Microsoft.Dynamics.CRM.RetrieveFormattedImportJobResults?text=RetrieveFormattedImportJobResults Function" /> | <xref:Microsoft.Crm.Sdk.Messages.RetrieveFormattedImportJobResultsRequest> |
|                                                     RetrieveLocLabels</br>Recupera las etiquetas localizadas para el atributo especificado.                                                     |                 <xref href="Microsoft.Dynamics.CRM.RetrieveLocLabels?text=RetrieveLocLabels Function" />                 |         <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest>         |
|                                                          SetLocLabels</br>Establece las etiquetas localizadas para el atributo especificado.                                                          |                       <xref href="Microsoft.Dynamics.CRM.SetLocLabels?text=SetLocLabels Action" />                       |           <xref:Microsoft.Crm.Sdk.Messages.SetLocLabelsRequest>            |

<a name="BKMK_CustomizingLabelsInBaseLanguage."></a>
   
## <a name="customize-labels-in-the-base-language"></a>Personalizar las etiquetas en el idioma base  
 Las herramientas de personalización proporcionan varias formas de editar nombres de la entidad y esas propiedades se pueden personalizar mediante programación. También se pueden editar los mensajes de la entidad. Pero no está expuesto cada mensaje. Otra forma de encontrar y de personalizar el texto usado en la aplicación es exportar las traducciones, modificar la configuración del idioma base e importar las traducciones de nuevo. Aunque éste no es el propósito de esta característica, es una forma compatible identificar y personalizar el texto usado en la aplicación. Para obtener más información, consulte [Modificar los mensajes de una entidad](/dynamics365/customer-engagement/developer/modify-messages-entity).  

<a name="BKMK_TranslatingCustomizedEntityAndAttributeText"></a>   

## <a name="translate-customized-entity-and-attribute-text"></a>Traducir texto de entidad y atributo personalizado  
 Debido a que solo se pueden realizar personalizaciones en la aplicación utilizando el idioma base, cuando se desea proporcionar etiquetas localizadas para estas personalizaciones se debe exportar el texto de las etiquetas de modo que puedan ser localizas para otros idiomas habilitados para la organización.  

### <a name="export-customized-text-for-translation"></a>Exportar el texto personalizado para traducción  
 Puede exportar las traducciones en la aplicación web o con el mensaje `ExportTranslation` (clase <xref href="Microsoft.Dynamics.CRM.ExportTranslation?text=ExportTranslation Action" /> o <xref:Microsoft.Crm.Sdk.Messages.ExportTranslationRequest>).  

 El texto exportado se guarda como archivo comprimido que contiene un CrmTranslations.xml y que puede abrir con Office Excel. Puede enviar este archivo a un lingüista experto, a una agencia de traducción o a una empresa de localización.  

 Para obtener más información, consulte [Esquemas de referencia XML de Office 2003](https://www.microsoft.com/downloads/details.aspx?FamilyID=fe118952-3547-420a-a412-00a2662442d9).  

### <a name="import-translated-text"></a>Importar el texto traducido  
 Después de exportar el texto personalizado de las entidades o atributos y de traducirlo, puede importar las cadenas de texto traducidas en la aplicación web con el mensaje `ImportTranslation` (clase <xref href="Microsoft.Dynamics.CRM.ImportTranslation?text=ImportTranslation Action" /> o <xref:Microsoft.Crm.Sdk.Messages.ImportTranslationRequest>). El archivo que se importa debe ser un archivo comprimido que contengan los archivos CrmTranslations.xml y [Content_Types].xml tal como se han exportado.  

 Una vez importadas las traducciones, el texto personalizado aparece para los usuarios que trabajan en los idiomas a los que tradujo el texto.  

> [!NOTE]
> Common Data Service no puede importar texto traducido que tenga más de 500 caracteres. Si alguno de los elementos del archivo de traducción tiene más de 500 caracteres, se producirá un error en el proceso de importación. Si esto sucede, revise la línea que provocó el error, reduzca el número de caracteres e intente de nuevo la importación.  

 Puesto que solo se permite personalizar texto en el idioma base, puede trabajar en Common Data Service con el idioma base establecido como preferencia de idioma. Para comprobar que aparece el texto traducido, debe cambiar su preferencia de idioma para la interfaz de usuario de Common Data Service. Para realizar tareas de personalización adicionales, debe volver a cambiar al idioma base.  

<a name="BKMK_ManagingLanguages"></a>   

## <a name="manage-languages-for-your-organization"></a>Administrar idiomas para la organización  
 Common Data Service permite instalar el paquete de varios idiomas en un servidor y permite al usuario seleccionar un paquete de idioma. Para obtener más información acerca de cómo instalar paquetes de idiomas, consulte [Habilitar idiomas](/dynamics365/customer-engagement/admin/enable-languages). Esta sección contiene información acerca de los mensajes que se usan para administrar los idiomas ya instalados para la organización.  

 En la siguiente tabla se enumeran los mensajes que se pueden usar para trabajar con los paquetes de idiomas. Use estos mensajes con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .  

|Mensaje|Operación de la API web|Ensamblado del SDK|  
|-------------|-----------------|----------------|  
|DeprovisionLanguage</br>Contiene los datos necesarios para desaprovisionar un idioma.|<xref href="Microsoft.Dynamics.CRM.DeprovisionLanguage?text=DeprovisionLanguage Action" />|<xref:Microsoft.Crm.Sdk.Messages.DeprovisionLanguageRequest>|  
|ProvisionLanguage</br>Contiene los datos necesarios para aprovisionar un idioma nuevo.|<xref href="Microsoft.Dynamics.CRM.ProvisionLanguage?text=ProvisionLanguage Action" />|<xref:Microsoft.Crm.Sdk.Messages.ProvisionLanguageRequest>|  
|RetrieveAvailableLanguages</br>Recupera la lista de los idiomas disponibles.|<xref href="Microsoft.Dynamics.CRM.RetrieveAvailableLanguages?text=RetrieveAvailableLanguages Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveAvailableLanguagesRequest>|  
|RetrieveDeprovisionedLanguages</br>Recupera la lista de los paquetes de idiomas instalados en el servidor que se han deshabilitado.|<xref href="Microsoft.Dynamics.CRM.RetrieveDeprovisionedLanguages?text=RetrieveDeprovisionedLanguages Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDeprovisionedLanguagesRequest>|  
|RetrieveInstalledLanguagePacks</br>Contiene los datos necesarios para recupera la lista de los paquetes de idiomas instalados en el servidor.|<xref href="Microsoft.Dynamics.CRM.RetrieveInstalledLanguagePacks?text=RetrieveInstalledLanguagePacks Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveInstalledLanguagePacksRequest>|  
|RetrieveInstalledLanguagePackVersion</br>Contiene los datos necesarios para recupera la versión de un paquete de idioma instalado.|<xref href="Microsoft.Dynamics.CRM.RetrieveInstalledLanguagePacks?text=RetrieveLicenseInfo Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveInstalledLanguagePackVersionRequest>|  
|RetrieveProvisionedLanguages</br>Recupera la lista de los paquetes de idiomas instalados en el servidor que están habilitados.|<xref href="Microsoft.Dynamics.CRM.RetrieveProvisionedLanguages?text=RetrieveProvisionedLanguages Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveProvisionedLanguagesRequest>|  
|RetrieveProvisionedLanguagePackVersion</br>Recupera la versión de los paquetes de idiomas instalados en el servidor.|<xref href="Microsoft.Dynamics.CRM.RetrieveProvisionedLanguagePackVersion?text=RetrieveProvisionedLanguagePackVersion Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveProvisionedLanguagePackVersionRequest>|  

### <a name="see-also"></a>Vea también  
 [Ampliar el modelo de metadatos de Dynamics 365](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)   
 [Personalizar Dynamics 365](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)   
 [Modificar los mensajes de una entidad](/dynamics365/customer-engagement/developer/modify-messages-entity)     
 <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>   
 <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>    
 <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata> 
