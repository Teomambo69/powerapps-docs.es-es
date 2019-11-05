---
title: Compartir recursos utilizados en la aplicación de lienzo | Microsoft Docs
description: Comprenda cómo compartir recursos que su aplicación de lienzo usa en PowerApps.
author: archnair
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/28/2016
ms.author: archanan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2160855d1b5ce67a4c11f5e227eb4d889d927d08
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542350"
---
# <a name="share-canvas-app-resources-in-powerapps"></a>Compartir recursos de aplicaciones de lienzo en PowerApps

Antes de [compartir una aplicación de lienzo](share-app.md), tenga en cuenta los tipos de recursos en los que se basa, por ejemplo, uno o varios de los siguientes:

* entidades en Common Data Service

    Para obtener información sobre cómo dar acceso a los usuarios a estos datos, vea [Administrar permisos de entidad](share-app.md#manage-entity-permissions).
    
* una conexión a un origen de datos
* una puerta de enlace de datos local
* un conector personalizado
* un libro de Excel u otro servicio
* un flujo

Algunos de estos recursos se comparten automáticamente cuando se comparte la aplicación. Otros recursos requieren que usted o las personas con quienes se comparte la aplicación realicen pasos adicionales para que la aplicación funcione según lo esperado.

También puede compartir las conexiones, los conectores personalizados y la puerta de enlace de datos local con toda la organización.

## <a name="connections"></a>Conexiones

Algunos tipos de conexiones, como SQL Server, se comparten automáticamente, pero otras requieren que los usuarios creen sus propias conexiones a los orígenes de datos de la aplicación.

En [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), puede determinar si una conexión se compartirá automáticamente y puede actualizar los permisos de uso compartido. En la barra de navegación izquierda, haga clic o pulse **Manage** (Administrar), haga clic o pulse **Connections** (Conexiones) y luego haga clic o pulse una conexión. Si aparece la pestaña **Share** (Recurso compartido), la conexión se compartirá automáticamente.

  ![Pestaña de recurso compartido de la página de detalles de la conexión](./media/share-app-resources/shared-connections.png)

## <a name="on-premises-data-gateways"></a>Puerta de enlace de datos local
Si crea y comparte una aplicación que incluye datos de un origen local, la propia [puerta de enlace de datos](gateway-management.md) local y determinados tipos de conexiones se compartirán automáticamente. En el caso de conexiones que no se comparten automáticamente, puede compartirlas manualmente (como se muestra en la sección anterior) o dejar que la aplicación pregunte a los usuarios si quieren crear sus propias conexiones. Para mostrar las conexiones o las conexiones con las que se ha configurado una puerta de enlace:

1. Abra [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), haga clic o pulse **Administrar** en la barra de navegación izquierda y luego haga clic o pulse **Puertas de enlace**.
2. Pulse o haga clic en una puerta de enlace y luego pulse o haga clic en la ficha **Connections** (Conexiones).

> [!NOTE]
> Si comparte una o varias conexiones manualmente, puede que tenga que volver a compartirlas en estas circunstancias:

* Si agrega una puerta de enlace de datos local a una aplicación que ya ha compartido.
* Si cambia el conjunto de personas o grupos con quienes ha compartido una aplicación que tiene una puerta de enlace de datos local.

## <a name="custom-connectors"></a>Conectores personalizados
Cuando se comparte una aplicación que utiliza un conector personalizado, se comparte automáticamente, pero los usuarios deben crear sus propias conexiones a ella.

En [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), puede ver o actualizar los permisos de un conector personalizado. En la barra de navegación izquierda, pulse o haga clic en **Manage** (Administrar), pulse o haga clic en **Connections** (Conexiones) y luego pulse o haga clic en **New connection** (Nueva conexión) (en la esquina superior derecha). Pulse o haga clic en **Personalizado** y luego en un conector personalizado para mostrar información detallada sobre él.

## <a name="excel-workbooks"></a>Libros de Excel
Si una aplicación compartida usa datos a los que no todos los usuarios tienen acceso (por ejemplo, un libro de Excel en una cuenta de almacenamiento en la nube), [comparta los datos](share-app-data.md).

## <a name="flows"></a>Flujos
Si comparte una aplicación que incluye un flujo, a los usuarios que ejecuten la aplicación se les pedirá que confirmen o actualicen las conexiones en las que se basa el flujo. Además, solo la persona que ha creado el flujo puede personalizar sus parámetros. Por ejemplo, puede crear un flujo en el que se envíe correo a una dirección especificada pero otros usuarios no puedan cambiar esa dirección.

