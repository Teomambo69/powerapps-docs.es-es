---
title: Usar recursos web | Microsoft Docs
description: Aprenda cómo los desarrolladores utilizan recursos web en aplicaciones basadas en modelos.
services: ''
suite: powerapps
documentationcenter: na
author: Nkrb
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: nabuthuk
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0985b9248887246b55f8796d88c4db7c31bdb75b
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115808"
---
# <a name="use-web-resources"></a>Usar recursos web

Hay una carpeta virtual denominada `webresources` en cada instancia de Common Data Service donde puede solicitar HTML, JS, CSS, imagen, y otros archivos por nombre y acceder a ellos en el explorador. Puede cargar estos archivos mediante la aplicación o mediante programación agregarlos como registros [Entidad WebResource](../common-data-service/reference/entities/webresource.md). El [Administrador de XrmToolBox WebResources](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/) es una herramienta de la comunidad que puede facilitar el trabajo con estos registros.

Estos registros pueden hacer referencia unos a otros mediante nombres de ruta de acceso relativa en su contenido. Esta funcionalidad de cargar archivos y de solicitarlos por nombre proporciona todos los bloques de creación que necesita para crear aplicaciones web con archivos que se procesan en la sesión autenticada del explorador. Utilizando solo código del lado cliente con técnicas AJAX, puede crear aplicaciones completas que pueden ejecutarse en una ventana del explorador o en un IFrame de un formulario o un panel. 

Lo más frecuente es que use recursos web JavaScript para agregar funciones de controlador de eventos a formularios y los comandos.

Más información:
- [Scripting de cliente con aplicaciones basadas en modelos](client-scripting.md)
- [Recursos web](/dynamics365/customer-engagement/developer/web-resources)
