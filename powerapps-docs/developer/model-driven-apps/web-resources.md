---
title: Uso de recursos web | Microsoft Docs
description: Obtenga información sobre cómo usan los desarrolladores los recursos web dentro de las aplicaciones controladas por modelos.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/17/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 88e51e4547732bed2d3e7ef3290bc8d933afded3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849920"
---
# <a name="use-web-resources"></a>Uso de recursos web

En cada instancia de Common Data Service for Apps se incluye una carpeta virtual denominada `webresources` donde se pueden solicitar archivos HTML, JS, CSS, de imagen y otros por nombre y tener acceso a ellos en el explorador. Estos archivos se pueden cargar con la aplicación o agregarlos mediante programación como registros de [entidad WebResource](../common-data-service/reference/entities/webresource.md). [XrmToolBox WebResources Manager](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/) es una herramienta de la comunidad que puede facilitar el trabajo con estos registros.

Estos registros se pueden hacer referencia entre ellos mediante nombres de ruta de acceso relativa en su contenido. Esta capacidad para cargar archivos y solicitarlos por nombre proporciona todos los bloques de creación que se necesitan para crear aplicaciones web mediante archivos que se procesan en la sesión autenticada del explorador. Mediante el uso de código del lado cliente con técnicas de AJAX, se pueden crear aplicaciones completas que se pueden ejecutar en una ventana del explorador o en un IFrame en un formulario o panel. 

Normalmente, se usarán recursos web de JavaScript para agregar funciones de controlador de eventos a los formularios y comandos.

Más información:
- [Client scripting with model-driven apps](client-scripting.md) (Scripting del lado cliente con aplicaciones controladas por modelos)
- [Recursos web para Dynamics 365 Customer Engagement (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/web-resources)
