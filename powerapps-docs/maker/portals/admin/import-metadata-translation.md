---
title: Importar traducción de metadatos | MicrosoftDocs
description: Instrucciones para importar la traducción de metadatos.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f05a0dfb6424b11e71cf5bf4324d5e3db03a7897
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72977988"
---
# <a name="import-metadata-translation"></a>Importar traducción de metadatos

Al aprovisionar un portal, las soluciones relacionadas con el portal se instalan en la organización. Durante la instalación de soluciones, las traducciones de metadatos de la solución (por ejemplo, el nombre del campo, el nombre del formulario y el nombre de la vista) solo se instalan para los idiomas activados actualmente en la organización. Si activa un nuevo idioma en el futuro, los metadatos no se instalarán automáticamente para el idioma recién activado. Para obtener la traducción de metadatos para el idioma recién activado, debe importar la traducción de metadatos desde el centro de administración de portales de PowerApps.

## <a name="to-import-metadata-translation"></a>Para importar la traducción de metadatos

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **acciones del Portal** > **obtener traducciones de metadatos más recientes**. Aparecerá una ventana de confirmación en la que se le preguntará si desea actualizar las soluciones del portal.

3.  Seleccione **Actualizar**. Las soluciones de portal se actualizarán con la traducción de metadatos más reciente.

> [!Note]
> - Si la versión más reciente de un paquete de portal está disponible, no se actualiza. Las soluciones del portal se actualizan en la misma versión. Para actualizar las soluciones de portal basadas en los últimos paquetes disponibles, debe tener acceso al centro de administración de soluciones.
> - Si un usuario ha modificado los datos en Common Data Service, los datos existentes no se sobrescribirán durante la actualización.
> - Si se están instalando las soluciones del portal, no se puede desencadenar la actualización de la solución.