---
title: Crear soluciones que admitan varios idiomas (Common Data Service) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5c020c483c3517375934e68d202401a37b2d5db7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156324"
---
# <a name="create-solutions-that-support-multiple-languages"></a>Crear soluciones que admitan varios idiomas

Common Data Service admite varios idiomas. Si desea que su solución se instale para organizaciones que incluyen distintos idiomas base o que disponen de varios idiomas aprovisionados, tenga esto en cuenta al planear su solución. En la siguiente tabla se enumeran tácticas para usar junto con los componentes de la solución para incluir en una solución que admita varios idiomas.  
  
|Táctica|Tipo de componente de la solución|  
|------------|-----------------------------|  
|[Recursos web de cadena (RESX)](#BKMK_Localizable_Web_Resources)|Recursos web|  
|[Etiquetas insertadas](#BKMK_EmbeddedLabels)|Navegación de la aplicación (mapa del sitio) <br />Cintas|  
|[Desplazamientos de exportación e importación](#BKMK_ExportAndImportTranslations)|Atributos<br />Gráficos<br />Paneles<br />Entity<br />Relaciones de entidades<br />Formularios<br />Mensajes<br />Conjuntos de opciones<br />Vistas|  
|[Localización en cadenas del idioma base](#BKMK_LocalizationInBaseLanguageStrings)|Plantillas de contrato<br /> Roles de conexión<br />Procesos (flujo de trabajo)<br />Roles de seguridad<br />Perfiles de seguridad de campo|  
|[No se requiere localización](#BKMK_LocalizationNotRequired)|Pasos de procesamiento de mensajes del SDK<br />Extremos de servicio|  
|[Componente independiente para cada idioma](#BKMK_SeparateComponentForEachLanguage)|Plantillas de artículo<br />Plantillas de correo electrónico<br />Plantillas de combinación de correspondencia<br />Informes<br />Diálogos|  
|[Utilice recursos web XML como recursos de idioma](#BKMK_UseXMLWebResourcesAsLanguageResources)|Ensamblados de complementos|  
  
 En las siguientes secciones se proporcionan detalles adicionales para cada táctica.  

 <a name="BKMK_Localizable_Web_Resources"></a>

 ## <a name="string-resx-web-resources"></a>Recursos web de cadena (RESX)
 Al añadir los recursos web de cadena (RESX) a Common Data Service, los desarrolladores tienen una opción más eficaz para crear recursos web que admiten varios idiomas. Más información [Recursos web de cadenas (RESX)](/dynamics365/customer-engagement/developer/resx-web-resources).

 Para versiones anteriores, vea [Opción de desarrollador](https://msdn.microsoft.com/library/hh670609(v=crm.8).aspx#BKMK_DeveloperOption)
  
<a name="BKMK_EmbeddedLabels"></a>   

## <a name="embedded-labels"></a>Etiquetas insertadas  
 Cada uno de los componentes de la solución que usan esta táctica requieren que el texto localizado se incluya en el componente de la solución.  
  
### <a name="ribbons"></a>Cintas  
 Cuando se instala un paquete de idioma, la cinta de aplicaciones muestra automáticamente texto localizado para todo el texto predeterminado en la cinta. Las etiquetas del sistema se definen en un valor de atributo de `ResourceId` que es solo para uso interno. Cuando agregue su propio texto deberá usar el elemento de `<LocLabels>` para proporcionar texto localizado para los idiomas que admite. Más información: [Usar etiquetas localizadas con cintas de opciones](/dynamics365/customer-engagement/developer/customize-dev/use-localized-labels-ribbons)  
  
### <a name="sitemap"></a>Mapa del sitio  
 Cuando se instala un paquete de idioma, el texto predeterminado de la barra de navegación de la aplicación muestra automáticamente texto localizado. Para reemplazar el texto predeterminado o para proporcionar su propio texto, use el elemento de `<Titles>`. El elemento de `Titles` debe contener un elemento de `<Title>` que contenga texto localizado para cualquier idioma que admita su solución. Si un elemento de `Title` no está disponible para el idioma preferido del usuario, se mostrará el título que corresponda al idioma base de la organización.  
  
 El elemento de `<SubArea>` permite pasar la preferencia de idioma del usuario mediante el parámetro `userlcid` de modo que el contenido que es el destino del atributo `SubArea.Url` pueda conocer de la preferencia de idioma del usuario y ajustarse en consecuencia. Más información: [Pasar parámetros a una dirección URL con el mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/pass-parameters-url-using-sitemap)  
  
<a name="BKMK_ExportAndImportTranslations"></a>   

## <a name="export-and-import-translations"></a>Desplazamientos de exportación e importación  
 Las etiquetas localizables para los componentes de la solución de la siguiente tabla se pueden exportar para la localización.  
  
||||  
|-|-|-|  
|Entidades|Atributos|Relaciones|  
|Conjuntos de opciones globales|Mensajes de la entidad|Formularios de entidad|  
|Vistas de entidad (SavedQuery)|Gráficos|Paneles|  
  
### <a name="translating-labels-and-display-strings"></a>Desplazamiento de etiquetas y mostrar cadenas  
 Solo puede realizar personalizaciones en la aplicación mediante el idioma base. Por lo tanto, cuando se desea proporcionar etiquetas localizadas y mostrar cadenas para estas personalizaciones, se debe exportar el texto de las etiquetas de modo que puedan ser localizas para otros idiomas habilitados para la organización. Lleve a cabo los pasos siguientes:  
  
1. Asegúrese de que la organización en la que está trabajando disponga de todos los paquetes MUI instalados y los idiomas aprovisionados para los idiomas para los que desee proporcionar traducciones.  
  
2. Cree su solución y modifique los componentes.  
  
3. Una vez que haya terminado de desarrollar su solución, utilice la funcionalidad de "Exportar traducciones". Esto genera una hoja de cálculo de Office Excel (CrmTranslations.xml) que contiene todas las etiquetas que necesitan traducción.  
  
4. En la hoja de cálculo, proporcione las traducciones correspondientes.  
  
5. Vuelva a importar traducciones a la misma organización de Common Data Service con la funcionalidad de "Importar traducciones" y publique sus cambios.  
  
6. La próxima vez que exporte la solución, contendrá todas las traducciones que haya proporcionado.  
  
   Cuando se importa una solución, las etiquetas para idiomas que no están disponibles en el sistema de destino de descartan y se registra una advertencia.  
  
   Si las etiquetas del idioma base del sistema de destino no se incluyen en el paquete de solución, las etiquetas del idioma base del origen se usan en su lugar. Por ejemplo, si importa una solución que contenga etiquetas para inglés y francés con el inglés como idioma base, pero el sistema de destino tiene el japonés y el francés con el japonés como idioma base, se utilizarán las etiquetas en inglés en lugar de las etiquetas en japonés. Las etiquetas de los idiomas base no pueden ser **null** o estar vacías.  
  
#### <a name="exporting-translations"></a>Exportación de traducciones  
 Antes de exportar traducciones primero debe instalar los paquetes de idiomas y aprovisionar todos los idiomas que desee localizar. Puede exportar las traducciones en la aplicación web o con el mensaje <xref:Microsoft.Crm.Sdk.Messages.ExportTranslationRequest>. Para obtener más información, consulte [Exportación de texto personalizado de entidades y campos para su traducción](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).  
  
#### <a name="translating-text"></a>Traducción de texto  
 Cuando abra el archivo CrmTranslations.xml en Office Excel verá las tres hojas de cálculo que aparecen en la siguiente tabla.  
  
|Hoja de cálculo|Descripción|  
|---------------|-----------------|  
|Información|Muestra información acerca de la organización y solución desde la que se exportaron las etiquetas y cadenas.|  
|Cadenas para mostrar|Muestre las cadenas que representen el texto de los mensajes asociados con un componente de metadatos. Esta tabla incluye los mensajes de error y cadenas usados para los elementos de la cinta del sistema.|  
|Etiquetas localizadas|Muestra todo el texto de cualquier etiqueta de componente de metadatos.|  
  
 Puede enviar este archivo a un lingüista experto, a una agencia de traducción o a una empresa de localización. Estos deberán proporcionar las cadenas localizadas de las celdas vacías.  
  
> [!NOTE]
>  Para las entidades personalizadas hay algunas etiquetas comunes que se comparten con entidades del sistema, como **Fecha de creación** o **Autor**. Debido a que tiene instalados y aprovisionados los idiomas, si exporta idiomas para la solución predeterminada podrá hacer que coincidan algunas etiquetas de sus entidades personalizadas con texto localizado para las etiquetas idénticas usadas por otras entidades. Esto puede ralentizar los costes de localización y mejorar la coherencia.  
  
 Una vez localizado el texto de las hojas de cálculo, agregue los archivos CrmTranslations.xml y [Content_Types].xml a un único archivo .zip comprimido. Ahora podrá importar este archivo.  
  
 Si prefiere trabajar con los archivos exportados mediante programación como un documento XML, consulte [Esquemas de referencia XML de Office 2003](https://www.microsoft.com/downloads/details.aspx?FamilyID=fe118952-3547-420a-a412-00a2662442d9) para obtener más información acerca de los esquemas que utilizan estos archivos.  
  
#### <a name="importing-translated-text"></a>Importación de texto traducido  
  
> [!IMPORTANT]
>  Solo se puede importar texto traducido nuevamente a la misma organización desde la que se exportó.  
  
 Después de exportar el texto personalizado de las entidades o atributos y traducirlo, puede importar las cadenas de texto traducidas en la aplicación web con el mensaje <xref:Microsoft.Crm.Sdk.Messages.ImportTranslationRequest>. El archivo que importe debe ser un archivo comprimido que contiene los archivos CrmTranslations.xml y [Content_Types].xml en la raíz. Para obtener más información, consulte [Importar entidad traducida y texto de campo](/dynamics365/customer-engagement/customize/import-translated-entity-field-text).  
  
 Una vez importadas las traducciones, el texto personalizado aparece para los usuarios que trabajan en los idiomas a los que tradujo el texto.  
  
> [!NOTE]
> Common Data Service no puede importar texto traducido que tenga más de 500 caracteres. Si alguno de los elementos del archivo de traducción tiene más de 500 caracteres, se producirá un error en el proceso de importación. Si esto sucede, revise la línea que provocó el error, reduzca el número de caracteres e intente de nuevo la importación.  
  
 Puesto que solo se permite personalizar texto en el idioma base, puede trabajar en Common Data Service con el idioma base establecido como preferencia de idioma. Para comprobar que aparece el texto traducido, debe cambiar su preferencia de idioma para la interfaz de usuario de Common Data Service. Para realizar tareas de personalización adicionales, debe volver a cambiar al idioma base.  
  
<a name="BKMK_LocalizationInBaseLanguageStrings"></a>   

## <a name="localization-in-base-language-strings"></a>Localización en cadenas del idioma base  
 Algunos componentes de la solución no admiten varios idiomas. Estos nombres incluyen nombres o texto que solamente pueden tener significado en un idioma específico. Si crea una solución para un idioma específico, defina estos componentes de la solución en el idioma base de la organización planteada.  
  
 Si necesita admitir varios idiomas, una táctica es incluir la solución en las cadenas de idioma base. Por ejemplo, si tiene un rol de conexión con el nombre "Amigo" y necesita admitir inglés, español y alemán, puede utilizar el texto "Amigo (Amigo/Freund)" como nombre del rol de conexión. Debido a problemas de longitud de texto, existen limitaciones sobre el número de idiomas que se pueden admitir utilizando esta táctica.  
  
 Algunos componentes de la solución de este grupo solo son visibles para los administradores. Debido a que la personalización del sistema solamente puede efectuarse en el idioma base de la organización no es necesario proporcionar versiones en varios idiomas. Los componentes **Roles de seguridad** y **Perfil de seguridad de campo** pertenecen a este grupo.  
  
 **Plantillas de contrato** proporcionan una descripción de un tipo de contrato de servicio. Estas requieren texto para los campos **Nombre** y **Abreviatura**. Deberá considerar la posibilidad de usar nombres y abreviaturas que sean únicos y adecuados para todos los usuarios de la organización.  
  
 **Roles de conexión** dependen de una persona que selecciona categorías y nombres de roles de conexión descriptivos. Debido a que estos pueden ser relativamente cortos, es recomendable incluir la localización en cadenas de idioma base.  
  
 Los **procesos (flujos de trabajo)** que se inician para eventos pueden funcionar correctamente mientras no necesiten actualizar registros con texto que se deba localizar. Es posible usar un ensamblado de flujo de trabajo de modo que la lógica que se aplique al texto localizado pueda usar la misma estrategia que ensamblados de complementos ([Utilizar recursos web XML como recursos de idiomas](#BKMK_UseXMLWebResourcesAsLanguageResources)).  
  
 Los **flujos de trabajo a petición** requieren un nombre para que la gente pueda elegirlos. Además de incluir la localización con el nombre del flujo de trabajo a petición, otra táctica es crear varios flujos de trabajo con nombres localizados que cada uno recupere el mismo proceso secundario. Sin embargo, todos los usuarios verán la lista completa de los flujos de trabajo a petición, no solo los que se encuentran en el idioma de la interfaz de usuario preferido.  
  
<a name="BKMK_LocalizationNotRequired"></a>   
## <a name="localization-not-required"></a>No se requiere localización  
 **El paso de procesamiento del mensaje del SDK** y los componentes de la solución del **Extremo de servicio** no exponen el texto localizable a los usuarios. Si es importante que estos componentes tengan nombres y descripciones que se correspondan al idioma base de la organización, puede crear y exportar una solución administrada con nombres y descripciones en ese idioma.  
  
<a name="BKMK_SeparateComponentForEachLanguage"></a>   
## <a name="separate-component-for-each-language"></a>Componente independiente para cada idioma  
 Los siguientes componentes de la solución pueden contener cada uno una cantidad considerable de texto para localizar:  
  
- Plantillas de artículo  
  
- Plantillas de correo electrónico  
  
- Plantillas de combinación de correspondencia  
  
- Informes  
  
- Diálogos  
  
  Para estos tipos de componentes de la solución, la táctica recomendada es crear componentes independientes para cada idioma. Esto significa que generalmente crea una solución administrada base que contiene los componentes de la solución centrales y luego una solución administrada independiente que contiene esos componentes de la solución para cada idioma. Una vez que los clientes instalan la solución base, pueden instalar las soluciones administradas para los idiomas que han aprovisionado para la organización.  
  
  A diferencia de los **Procesos (flujos de trabajo)**, puede crear **Diálogos** que reflejarán los valores actuales de preferencia de idioma del usuario y mostrarán los diálogos solo a los usuarios de ese idioma.  
  
#### <a name="create-a-localized-dialog-box"></a>Crear un cuadro de diálogo localizado  
  
1. Instale el paquete de idioma correcto y proporcione el idioma.  
  
    Para obtener más información, consulte [Instrucciones de instalación de paquetes de idioma](https://technet.microsoft.com/library/hh699674.aspx).  
  
2. Cambiar sus opciones personales para especificar **Idioma de interfaz de usuario** del idioma que desee para el diálogo.  
  
3. Vaya a **Configuración** y, en el grupo **Centro de procesos** , seleccione **Procesos**.  
  
4. Haga clic en **Nueva** y crea el diálogo en el idioma especificado.  
  
5. Una vez creado el diálogo, cambie sus opciones personales para especificar el idioma base de la organización.  
  
6. Mientras usa el idioma base de la organización se puede navegar al área **Soluciones** en **Configuración** y agregar el diálogo localizado como parte de una solución.  
  
   El diálogo creado en el otro idioma se mostrará solo a los usuarios que ven Common Data Service con ese idioma.  
  
<a name="BKMK_UseXMLWebResourcesAsLanguageResources"></a>   

## <a name="use-xml-web-resources-as-language-resources"></a>Utilice recursos web XML como recursos de idioma  
 Los componentes de la solución del ensamblado del complemento pueden enviar mensajes a un usuario final lanzando un <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> y creando y actualizando los registros. A diferencia de los recursos web de Silverlight, los complementos no pueden usar los archivos de recursos.  
  
 Cuando un complemento requiere texto localizado, puede usar un recurso web XML para almacenar las cadenas localizadas para que el complemento pueda acceder a ellas cuando sea necesario. La estructura del XML depende de usted, pero es posible que desee seguir la estructura usada por los archivos del recurso ASP.NET (.resx) para crear recursos web XML independientes para cada idioma. Por ejemplo, a continuación se facilita un recurso web XML llamado **localizedString.en_US** que sigue el patrón usado por los archivos .resx.  
  
```xml  
<root>  
 <data name="ErrorMessage">  
  <value>There was an error completing this action. Please try again.</value>  
 </data>  
 <data name="Welcome">  
  <value>Welcome</value>  
 </data>  
</root>  
```  
  
 El siguiente código muestra cómo se puede pasar un mensaje localizado en un complemento para mostrar un mensaje a un usuario. Es para la fase de validación previa de un evento de `Delete` de la entidad de `Account`:  
  
```csharp  
protected void ExecutePreValidateAccountDelete(LocalPluginContext localContext)  
  {  
   if (localContext == null)  
   {  
    throw new ArgumentNullException("localContext");  
   }  
   int OrgLanguage = RetrieveOrganizationBaseLanguageCode(localContext.OrganizationService);  
   int UserLanguage = RetrieveUserUILanguageCode(localContext.OrganizationService,  
 localContext.PluginExecutionContext.InitiatingUserId);  
   String fallBackResourceFile = "";  
   switch (OrgLanguage)  
   {  
    case 1033:  
     fallBackResourceFile = "new_localizedStrings.en_US";  
     break;  
    case 1041:  
     fallBackResourceFile = "new_localizedStrings.ja_JP";  
     break;  
    case 1031:  
     fallBackResourceFile = "new_localizedStrings.de_DE";  
     break;  
    case 1036:  
     fallBackResourceFile = "new_localizedStrings.fr_FR";  
     break;  
    case 1034:  
     fallBackResourceFile = "new_localizedStrings.es_ES";  
     break;  
    case 1049:  
     fallBackResourceFile = "new_localizedStrings.ru_RU";  
     break;  
    default:  
     fallBackResourceFile = "new_localizedStrings.en_US";  
     break;  
   }  
   String ResourceFile = "";  
   switch (UserLanguage)  
   {  
    case 1033:  
     ResourceFile = "new_localizedStrings.en_US";  
     break;  
    case 1041:  
     ResourceFile = "new_localizedStrings.ja_JP";  
     break;  
    case 1031:  
     ResourceFile = "new_localizedStrings.de_DE";  
     break;  
    case 1036:  
     ResourceFile = "new_localizedStrings.fr_FR";  
     break;  
    case 1034:  
     ResourceFile = "new_localizedStrings.es_ES";  
     break;  
    case 1049:  
     ResourceFile = "new_localizedStrings.ru_RU";  
     break;  
    default:  
     ResourceFile = fallBackResourceFile;  
     break;  
   }  
   XmlDocument messages = RetrieveXmlWebResourceByName(localContext, ResourceFile);  
   String message = RetrieveLocalizedStringFromWebResource(localContext, messages, "ErrorMessage");  
   throw new InvalidPluginExecutionException(message);  
  }  
  protected static int RetrieveOrganizationBaseLanguageCode(IOrganizationService service)  
  {  
   QueryExpression organizationEntityQuery = new QueryExpression("organization");  
   organizationEntityQuery.ColumnSet.AddColumn("languagecode");  
   EntityCollection organizationEntities = service.RetrieveMultiple(organizationEntityQuery);  
   return (int)organizationEntities[0].Attributes["languagecode"];  
  }  
  protected static int RetrieveUserUILanguageCode(IOrganizationService service, Guid userId)  
  {  
   QueryExpression userSettingsQuery = new QueryExpression("usersettings");  
   userSettingsQuery.ColumnSet.AddColumns("uilanguageid", "systemuserid");  
   userSettingsQuery.Criteria.AddCondition("systemuserid", ConditionOperator.Equal, userId);  
   EntityCollection userSettings = service.RetrieveMultiple(userSettingsQuery);  
   if (userSettings.Entities.Count > 0)  
   {  
    return (int)userSettings.Entities[0]["uilanguageid"];  
   }  
   return 0;  
  }  
  protected static XmlDocument RetrieveXmlWebResourceByName(LocalPluginContext context, string webresourceSchemaName)  
  {  
   context.TracingService.Trace("Begin:RetrieveXmlWebResourceByName, webresourceSchemaName={0}", webresourceSchemaName);  
   QueryExpression webresourceQuery = new QueryExpression("webresource");  
   webresourceQuery.ColumnSet.AddColumn("content");  
   webresourceQuery.Criteria.AddCondition("name", ConditionOperator.Equal, webresourceSchemaName);  
   EntityCollection webresources = context.OrganizationService.RetrieveMultiple(webresourceQuery);  
   context.TracingService.Trace("Webresources Returned from server. Count={0}", webresources.Entities.Count);  
   if (webresources.Entities.Count > 0)  
   {  
    byte[] bytes = Convert.FromBase64String((string)webresources.Entities[0]["content"]);  
    // The bytes would contain the ByteOrderMask. Encoding.UTF8.GetString() does not remove the BOM.  
    // Stream Reader auto detects the BOM and removes it on the text  
    XmlDocument document = new XmlDocument();  
    document.XmlResolver = null;  
    using (MemoryStream ms = new MemoryStream(bytes))  
    {  
     using (StreamReader sr = new StreamReader(ms))  
     {  
      document.Load(sr);  
     }  
    }  
    context.TracingService.Trace("End:RetrieveXmlWebResourceByName , webresourceSchemaName={0}", webresourceSchemaName);  
    return document;  
   }  
   else  
   {  
    context.TracingService.Trace("{0} Webresource missing. Reinstall the solution", webresourceSchemaName);  
    throw new InvalidPluginExecutionException(String.Format("Unable to locate the web resource {0}.", webresourceSchemaName));  
    return null;  
 // This line never reached  
   }  
  }  
  protected static string RetrieveLocalizedStringFromWebResource(LocalPluginContext context, XmlDocument resource, string resourceId)  
  {  
   XmlNode valueNode = resource.SelectSingleNode(string.Format(CultureInfo.InvariantCulture, "./root/data[@name='{0}']/value", resourceId));  
   if (valueNode != null)  
   {  
    return valueNode.InnerText;  
   }  
   else  
   {  
    context.TracingService.Trace("No Node Found for {0} ", resourceId);  
    throw new InvalidPluginExecutionException(String.Format("ResourceID {0} was not found.", resourceId));  
   }  
  }  
```  
  
### <a name="see-also"></a>Vea también  
 [Empaquetar y distribuir extensiones con soluciones de Dynamics 365](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Introducción a las soluciones](introduction-solutions.md)   
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Seguimiento de las dependencias de los componentes de la solución](dependency-tracking-solution-components.md)   
 [Crear, exportar o importar una solución no administrada](create-export-import-unmanaged-solution.md)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Desinstalar o eliminar una solución](uninstall-delete-solution.md)   
 [Entidades de solución](/dynamics365/customer-engagement/developer/solution-entities)   
 [Localizar los valores de propiedad del producto](/dynamics365/customer-engagement/developer/localize-product-property-values)
