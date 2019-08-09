---
title: Referencia XML de personalización (aplicaciones basadas en modelos) | Microsoft Docs
description: El archivo customizations.xml es uno de los archivos incluidos en una solución no administrada exportada. El archivo contiene todas las partes o partes seleccionadas de las personalizaciones y configuraciones para el sistema.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 864699de-c22f-3504-f120-84ca5a4aeca6
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="customization-xml-reference"></a>Referencia de XML de personalización

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customization-xml-reference -->

El archivo customizations.xml es uno de los archivos incluidos en una solución no administrada exportada. El archivo contiene todas o partes seleccionadas de las personalizaciones y configuraciones para el sistema. 
  
 El archivo de soluciones se exporta como archivo .zip comprimido. El contenido del archivo de soluciones no administradas debe extraerse antes de que se pueda editar el archivo de personalización. Todos los archivos de la solución no administrada deben agregarse a un archivo .zip comprimido antes de que se puedan volver a importar.  

> [!NOTE]
> - No se admite la edición de un archivo de solución administrada.  
> - No todos los elementos del archivo customizations.xml se pueden editar. Más información: [Soporte para editar el archivo de personalización](../common-data-service/when-edit-customization-file.md).

## <a name="in-this-section"></a>En esta sección

 [Esquema central de cinta de opciones](ribbon-core-schema.md) [Esquema de tipos de cinta de opciones](ribbon-types-schema.md)  
 [Esquema WSS de cinta de opciones](ribbon-wss-schema.md)  
 [Esquema de mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/sitemap-schema)<br/> <!-- TODO need to fix the link--> 
 [Esquema XML de formulario](form-xml-schema.md)<br/> 
 [Esquema FetchXML](../common-data-service/fetchxml-schema.md) 

## <a name="related-sections"></a>Secciones relacionadas

 [Esquemas utilizados en Dynamics 365](/dynamics365/customer-engagement/developer/schemas-used-dynamics-365)<br/> <!-- TODO need to fix the link--> 
 [Cuándo editar el archivo de personalizaciones](../common-data-service/when-edit-customization-file.md)  
[Editar el archivo de personalizaciones con la validación de esquema](edit-customizations-xml-file-schema-validation.md)  
 [Personalizar la cinta de opciones para Dynamics 365](customize-commands-ribbon.md)  
 [Cambiar la navegación de la aplicación con el mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap) <!-- TODO need to fix the link--> 
