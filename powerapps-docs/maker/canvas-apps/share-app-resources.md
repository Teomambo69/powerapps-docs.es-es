---
title: Uso compartido de los recursos utilizados en la aplicación | Microsoft Docs
description: Comprender cómo se comparten los recursos usados en su aplicación cuando se comparte una aplicación
author: archnair
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/28/2016
ms.author: archanan
ms.openlocfilehash: 09d4f26139ae33195c666a2eb71d70e02b035f69
ms.sourcegitcommit: 0e9af8cace2bdc04750f4c5a70a3c4af8e3d2292
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2018
ms.locfileid: "39194907"
---
# <a name="share-app-resources"></a>Compartir los recursos de la aplicación
Antes de [compartir una aplicación](share-app.md), tenga en cuenta los tipos de recursos en los que se basa, por ejemplo, uno o varios de los siguientes:

* una conexión a un origen de datos
* una puerta de enlace de datos local
* un conector personalizado
* un libro de Excel u otro servicio
* un flujo

Algunos de estos recursos se comparten automáticamente cuando se comparte la aplicación. Otros recursos requieren que usted o las personas con quienes se comparte la aplicación realicen pasos adicionales para que la aplicación funcione según lo esperado.

También puede compartir las conexiones, los conectores personalizados y la puerta de enlace de datos local con toda la organización.

## <a name="connections"></a>Conexiones
Algunos tipos de conexiones, como SQL Server, se comparten automáticamente, pero otras requieren que los usuarios creen sus propias conexiones a los orígenes de datos de la aplicación.

En [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), puede determinar si una conexión se compartirá automáticamente y puede actualizar los permisos de uso compartido. En la barra de navegación izquierda, haga clic o pulse **Manage** (Administrar), haga clic o pulse **Connections** (Conexiones) y luego haga clic o pulse una conexión. Si aparece la pestaña **Share** (Recurso compartido), la conexión se compartirá automáticamente.

  ![Pestaña de recurso compartido de la página de detalles de la conexión](./media/share-app-resources/shared-connections.png)

## <a name="on-premises-data-gateways"></a>Puerta de enlace de datos local
Si crea y comparte una aplicación que incluye datos de un origen local, la propia [puerta de enlace de datos](gateway-management.md) local y determinados tipos de conexiones se compartirán automáticamente. En el caso de conexiones que no se comparten automáticamente, puede compartirlas manualmente (como se muestra en la sección anterior) o dejar que la aplicación pregunte a los usuarios si quieren crear sus propias conexiones. Para mostrar las conexiones o las conexiones con las que se ha configurado una puerta de enlace:

1. Abra [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), haga clic o pulse **Administrar** en la barra de navegación izquierda y luego haga clic o pulse **Puertas de enlace**.
2. Pulse o haga clic en una puerta de enlace y luego pulse o haga clic en la ficha **Connections** (Conexiones).

> [!NOTE]
> Si comparte una o varias conexiones manualmente, puede que tenga que volver a compartirlas en estas circunstancias:

* Si agrega una puerta de enlace de datos local a una aplicación que ya ha compartido.
* Si cambia el conjunto de personas o grupos con quienes ha compartido una aplicación que tiene una puerta de enlace de datos local.

## <a name="custom-connectors"></a>Conectores personalizados
Cuando se comparte una aplicación que utiliza un conector personalizado, se comparte automáticamente, pero los usuarios deben crear sus propias conexiones a ella.

En [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), puede ver o actualizar los permisos de un conector personalizado. En la barra de navegación izquierda, pulse o haga clic en **Manage** (Administrar), pulse o haga clic en **Connections** (Conexiones) y luego pulse o haga clic en **New connection** (Nueva conexión) (en la esquina superior derecha). Pulse o haga clic en **Personalizado** y luego en un conector personalizado para mostrar información detallada sobre él.

## <a name="excel-workbooks"></a>Libros de Excel
Si una aplicación compartida usa datos a los que no todos los usuarios tienen acceso (por ejemplo, un libro de Excel en una cuenta de almacenamiento en la nube), [comparta los datos](share-app-data.md).

## <a name="flows"></a>Flujos
Si comparte una aplicación que incluye un flujo, a los usuarios que ejecuten la aplicación se les pedirá que confirmen o actualicen las conexiones en las que se basa el flujo. Además, solo la persona que ha creado el flujo puede personalizar sus parámetros. Por ejemplo, puede crear un flujo en el que se envíe correo a una dirección especificada pero otros usuarios no puedan cambiar esa dirección.

