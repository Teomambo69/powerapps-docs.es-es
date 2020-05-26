---
title: Borrar la memoria caché del servidor para un portal | MicrosoftDocs
description: Instrucciones para forzar el portal para que actualice la memoria caché inmediatamente.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/23/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 614ee17fdbf9a5104c51ff918df8bf8c66fccd98
ms.sourcegitcommit: 504bf052f7fe276484fa8c9b1ea04b19ad63484f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3288308"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>Borrar la memoria caché del servidor para un portal

Como administrador de portal, puede borrar la memoria caché de servidor de todo el portal para reflejar los datos actualizados de Common Data Service inmediatamente en el portal. Las actualizaciones de Common Data Service se comunican al portal en modo asincrónico, por lo que puede haber conflictos entre la hora en que se actualizan los datos en Common Data Service y la hora en que los datos actualizados aparecen en el portal. Para eliminar este retardo&mdash;por ejemplo cuando interfiere con la configuración del portal&mdash;puede forzar una actualización inmediata de la memoria caché.

> [!NOTE]
> La actualización del SLA de la memoria caché (transferencia de datos entre Common Data Service y el portal) dura 15 minutos.

## <a name="steps-to-clear-portal-server-side-cache"></a>Pasos para borrar la memoria caché del portal desde el servidor

> [!IMPORTANT]
> Borrar la memoria caché del servidor de portal producirá una degradación temporal del rendimiento del portal mientras los datos se vuelven a cargar desde Common Data Service.

Para borrar la memoria caché del servidor:

1. Iniciar sesión en el portal como administrador.

1. Navegue a la dirección URL de la siguiente manera: `<portal_path>/_services/about`.

1. Seleccionar **Borrar caché**.

Se elimina la memoria caché del servidor, y los datos se vuelven a cargar de Common Data Service. 

![Borrar la memoria caché del portal](media/clear-server-side-cache/clear-portal-cache.png)

## <a name="configuration-entity-caching-portals-with-capacity-based-licenses"></a>Portales de almacenamiento en caché de entidades de configuración con licencias basadas en capacidad

Los portales [basados en la capacidad](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals) tienen más opciones en `<portal_path>/_services/about`:

![Borrar caché del portal con licencia basada en capacidad](media/clear-server-side-cache/clear-config-capacity-license.png)

Para aprender más sobre las diferencias entre portales Power Apps y complementos de portal, lea [Preguntas más frecuentes del portal Power Apps](../faq.md#what-is-the-difference-between-power-apps-portals-dynamics-365-portals-and-add-on-portals).

Los metadatos del portal se almacenan en entidades llamadas *entidades de configuración*. Si cambia las entidades de configuración utilizando la *Aplicación Interfaz unificada*, usted **debe** seleccionar **Borrar configuración** para borrar la caché de configuración para que los cambios se reflejen en su Portal.  

### <a name="list-of-configuration-entities-refreshed-when-you-clear-config"></a>Lista de entidades de configuración actualizadas cuando borra la configuración

Borrar el caché de configuración del lado del servidor para un portal incluye actualizar los datos de las siguientes *entidades de configuración*:

| Entidades de configuración:| | |
|-------------------------------------------|---------------------------|--------------------------------------|
| adx_contentaccesslevel                    | adx_redirect              | adx_webpage_tag                      |
| adx_contentsnippet                        | adx_setting               | adx_webpageaccesscontrolrule         |
| adx_entityform                            | adx_shortcut              | adx_webpageaccesscontrolrule_webrole |
| adx_entityformmetadata                    | adx_sitemarker            | adx_webpagehistory                   |
| adx_entitylist                            | adx_sitesetting           | adx_webpagelog                       |
| adx_entitypermission_webrole              | adx_webfile               | adx_webrole_systemuser               |
| adx_externalidentity                      | adx_webfilelog            | adx_website                          |
| adx_pagealert                             | adx_webform               | adx_website_list                     |
| adx_pagenotification                      | adx_webformmetadata       | adx_website_sponsor                  |
| adx_pagetag                               | adx_webformsession        | adx_websiteaccess                    |
| adx_pagetag_webpage                       | adx_webformstep           | adx_websiteaccess_webrole            |
| adx_pagetemplate                          | adx_weblink               | adx_websitebinding                   |
| adx_portallanguage                        | adx_weblinkset            | adx_websitelanguage                  |
| adx_publishingstate                       | adx_webnotificationentity | adx_webtemplate                      |
| adx_publishingstatetransitionrule         | adx_webnotificationurl    | adx_urlhistory                       |
| adx_publishingstatetransitionrule_webrole | adx_webpage               | adx_entitypermission                 |
