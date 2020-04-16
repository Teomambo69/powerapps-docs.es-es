---
title: Aplicar lógica de negocios con código (Common Data Service)| Microsoft Docs
description: Aprenda cómo los desarrolladores pueden usar código para aplicar lógica de negocio en Common Data Service.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ac1f673b927280cd2cdedb967a1f504f4ce68688
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "3126491"
---
# <a name="apply-business-logic-using-code"></a>Aplicar la lógica de negocios usando código

Siempre que sea posible, primero debe considerar aplicar una de las diversas opciones de proceso declarativas para definir o aplicar la lógica de negocios. Más información: [Aplicar lógica de negocios en Common Data Service para aplicaciones](../../maker/common-data-service/cds-processes.md)

Cuando un proceso declarativo no cumple un requisito, como un desarrollador tiene varias opciones. Este tema introducirá opciones comunes de escribir código.

## <a name="create-a-plug-in"></a>Crear un complemento

Puede escribir un ensamblado de .NET para ejecutar como complemento en la transacción de datos para aplicar lógica empresarial en el servidor. Con Common Data Service puede usar un marco para registrar eventos específicos de ejecución de código definido en una clase en un ensamblado. 

Más información: [Escriba complementos para ampliar los procesos de negocio](plug-ins.md)

## <a name="create-a-workflow-extension"></a>Creación de una extensión de flujo

Puede escribir un ensamblado de .NET para proporcionar nuevas opciones en el diseñador del proceso. Este método proporciona una nueva opción para las personas que usan el diseñador de flujo de trabajo para aplicar una condición o para realizar una nueva acción. Una extensión del flujo de trabajo se puede volver a usar por personas que no son programadores para aplicar la lógica de su código.

Más información: [Extensiones de flujo de trabajo](workflow/workflow-extensions.md)

### <a name="see-also"></a>Vea también

[Información general para desarrolladores de Common Data Service](overview.md)
