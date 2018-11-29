---
title: Recursos web de cadena (RESX) (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo usar recursos web de cadena para dejar disponibles para su uso las cadenas traducidas
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
# <a name="resx-web-resources"></a>Recursos web RESX

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/resx-web-resources -->

Utilice estos recursos web para administrar cadenas traducidas en cualquier interfaz de usuario que se defina o con mensajes de error visibles. 

# <a name="using-resx-web-resources"></a>Uso de recursos web RESX

Los recursos web RESX contienen las claves y los valores de cadena traducidos para un único lenguaje definido con el formato XML RESX. RESX es un formato común para definir recursos traducidos para aplicaciones de Windows, de manera que haya herramientas comunes disponibles para trabajar con este tipo de archivos y los proveedores de localización estén correctamente familiarizados para trabajar con ellos. Cuando se publica el archivo como un recursos web en CRM, este se convierte a formato JSON que se descargará en la aplicación cuando sea necesario.

Cuando se crean recursos web RESX es necesario establecer explícitamente el valor de idioma e incluir el identificador local (LCID) para el idioma correspondiente en el nombre del recurso web. Por ejemplo, `new_/strings/MyAppResources.1033.resx` contendría recursos para el idioma inglés. Consulte [Valores de identificadores de configuración regional de Microsoft](https://msdn.microsoft.com/library/ms912047(WinEmbedded.10).aspx) para ver la lista de valores LCID.

Para extraer el valor traducido, sírvase de la función [Xrm.Utility.getResourceString](clientapi/reference/Xrm-Utility/getResourceString.md). Esta función acepta dos parámetros: `WebResourceName`y `keyValue`. 

Por ejemplo, `Xrm.Utility.getResourceString("new_/strings/MyAppResources","hello")` devolverá el valor de la cadena traducida para la clave del recurso "hello" dentro del recurso web `new_/strings/MyAppResources.1033.resx` si el idioma preferido del usuario es el inglés. Tenga en cuenta que la función no hace referencia a ningún idioma específico o ningún nombre completo de recurso web RESX. Esta funcionalidad depende del recurso web RESX que se esté asociando al recurso web JavaScript que realiza la llamada como dependencia. Más información: [Dependencias de recursos web](web-resource-dependencies.md).

El valor de cadena correspondiente vendrá determinado por la preferencia de idioma del usuario y los idiomas disponibles en la organización. Si no se encuentra una cadena traducida que coincida con las preferencias de idioma del usuario, la cadena traducida se revertirá automáticamente al idioma base de la organización. Si no se encuentra ninguna cadena traducida que coincida con el idioma base de la organización, se devolverá un valor nulo.

### <a name="see-also"></a>Vea también
[Recursos web](web-resources.md)<br />
[Crear recursos web accesibles](create-accessible-web-resources.md)<br />
[Crear recursos web y contenido de IFrame para uso con el cliente de Dynamics 365 para clientes de móviles](/dynamics365/customer-engagement/developer/create-web-resources-iframe-mobile)<br />
[Dependencias de recursos web](web-resource-dependencies.md)<br />
[Recursos web de página web (HTML)](webpage-html-web-resources.md)<br />
[Recursos web de Silverlight (XAP)](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)<br />
[Recursos web de script (JScript)](script-jscript-web-resources.md)<br />
[Recursos web de imagen (JPG, PNG, GIF, ICO)](image-web-resources.md)<br />
[Recursos web de hoja de estilo (XSL)](stylesheet-xsl-web-resources.md)<br />
[Recursos web (XML) de datos](data-xml-web-resources.md)<br />
[Recursos web CSS](css-web-resources.md)<br />
[Mensajes y métodos de la entidad WebResource](/dynamics365/customer-engagement/developer/webresource-entity-messages-methods)<br />
[Ejemplo: pasar varios valores a un recurso web mediante el parámetro de datos](sample-pass-multiple-values-web-resource-through-data-parameter.md)<br />
[Ejemplo: importar archivos como recursos web](sample-import-files-web-resources.md)<br />