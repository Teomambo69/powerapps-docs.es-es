---
title: Recursos web (XML) de datos (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtener información sobre el uso de recursos web de datos (XML) para guardar y obtener acceso a los datos.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 2bf0d49f-8b6d-6d5b-0af5-edf6dd485fed
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8d6669c644b3ecc9419f7900030eb663cf25ebe1
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115652"
---
# <a name="data-xml-web-resources"></a>Recursos web (XML) de datos

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/data-xml-web-resources -->

Use recursos web de datos (XML) para guardar y obtener acceso a los datos.  
  
## <a name="capabilities-of-xml-web-resources"></a>Capacidades de los recursos web XML  
 Use los recursos web XML para almacenar en caché datos que desee usar en su solución.  
  
### <a name="limitations-of-xml-web-resources"></a>Limitaciones de los recursos web XML  
 Use los recursos web XML para almacenar en caché las opciones de configuración o los metadatos de sus soluciones.  
  
 Un recurso web XML no representa una solución robusta para los datos que a menudo actualizan varios usuarios. Cuando un usuario actualiza un recurso web XML, otro usuario (o un proceso automatizado) puede actualizar el recurso web, de manera que los datos se perderían cuando el primer usuario guardase sus cambios.  
  
 Todos los archivos XML deben usar la extensión de nombre de archivo .xml. Los archivos que usan datos XML, pero no usan la extensión de nombre de archivo .xml, no se pueden cargar como recursos web a menos que se cambie la extensión de nombre de archivo.  
  
### <a name="see-also"></a>Vea también  
 [Recursos web](web-resources.md)   
 [Uso de recursos web de página web (HTML)](webpage-html-web-resources.md)   
 [Uso de recursos web de hojas de estilo (CSS)](css-web-resources.md)   
 [Usar recursos web de script (JScript)](script-jscript-web-resources.md)   
 [Uso de recursos web de imagen (JPG, PNG, GIF)](image-web-resources.md)   
 [Usar recursos web Silverlight (XAP)](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)<br/>   <!-- TODO need to update the relevant link from the powerapps repo-->
 [Uso de recursos web de hoja de estilo (XSL)](/dynamics365/customer-engagement/developer/stylesheet-xsl-web-resources) <!-- TODO need to update the relevant link from the powerapps repo-->
