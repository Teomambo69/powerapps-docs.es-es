---
title: Importar traducción de metadatos | MicrosoftDocs
description: Instrucciones para importar traducción de metadatos.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a648efdea5538dbedc431f0c3299b23948d39eb2
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978037"
---
# <a name="import-metadata-translation"></a>Importar traducción de metadatos

Cuando se aprovisiona un portal, las soluciones relacionadas con el portal se instalan en la organización. Durante la instalación de las soluciones, las traducciones de los metadatos de la solución (por ejemplo: el nombre de campo, el nombre del formulario, el nombre de vista, etc.) se instalan solo en los idiomas activados actualmente en la organización. Si posteriormente se activa un nuevo idioma, los metadatos no se instalarán automáticamente en el idioma recién activado. Para obtener la traducción de los metadatos al idioma recién activado, debe importar la traducción de los metadatos desde el Centro de administración de portales de Power Apps.

## <a name="to-import-metadata-translation"></a>Para importar la traducción de metadatos

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Acciones del portal** > **Obtener las traducciones de metadatos más recientes**. Una ventana de confirmación que se muestra pregunta si desea actualizar las soluciones de portal.

3.  Seleccione **Actualizar**. Las soluciones de portal se actualizan a la última traducción de metadatos.

> [!Note]
> - Si la versión más reciente del paquete de portal está disponible, no se actualizará. Las soluciones de portal se actualizan en la misma versión. Para actualizar sus soluciones de portal según los últimos paquetes disponibles, debe tener acceso al Centro de administración de soluciones.
> - Si un usuario modificó todos los datos en Common Data Service, los datos existentes no se sobrescriben durante la actualización.
> - Si las soluciones de portal se están instalando, la actualización de una solución no puede ser desencadenada.