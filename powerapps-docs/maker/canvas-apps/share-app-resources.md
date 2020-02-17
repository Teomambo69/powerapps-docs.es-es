---
title: Compartir recursos utilizados en la aplicación de lienzo | Microsoft Docs
description: Comprender cómo compartir los recursos que usa la aplicación de lienzo en Power apps
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a1385e45fbbd932e0575c5c5b69b051dc292c824
ms.sourcegitcommit: eda3382ade50efe66611518c8f36e3a2ada7a91d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77282333"
---
# <a name="share-canvas-app-resources-in-power-apps"></a>Uso compartido del lienzo: recursos de la aplicación en Power apps

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

Algunas conexiones (como SQL Server con autenticación de Windows o SQL) se [comparten implícitamente](share-app-resources.md#implicit-sharing) con la aplicación cuando se comparte con otros usuarios. Otras conexiones requieren que los usuarios creen sus propias conexiones (como OneDrive para la empresa o SQL Server con la autenticación de Azure AD).

Puede determinar si una conexión se comparte automáticamente como parte de la aplicación cuando se comparte con otros usuarios. permite actualizar los permisos de uso compartido. Para ello, vaya a make.powerapps.com y seleccione **datos** -> **conexiones** desde el panel de navegación izquierdo. A continuación, seleccione la conexión necesaria. Si el botón **compartir** aparece en la navegación superior o si se muestra la opción **compartir** al seleccionar *más comandos* (...), la conexión seleccionada puede compartirse con otros usuarios.

  ![No hay recursos compartidos para OneDrive para la empresa](./media/share-app-resources/shared-connections-odb.png)

  ![Compartir conexión de autenticación de SQL con SQL Server](./media/share-app-resources/shared-connections-sqlauth.png)

### <a name="implicit-sharing"></a>Uso compartido implícito

Cuando comparte una aplicación que usa una conexión que se puede compartir, la conexión de la aplicación se **comparte implícitamente** junto con la aplicación. Por ejemplo, aparece el siguiente mensaje cuando vaya a make.powerapps.com, seleccione **aplicaciones**, elija una aplicación que use dicha conexión, seleccione *más comandos* (...) y, luego, seleccione **compartir**:

  ![ADVERTENCIA implícita de permisos](./media/share-app-resources/share-app-implicit-permission.png)

Si selecciona **confirmar** y compartir la aplicación elegida con otros usuarios, la conexión de la aplicación se comparte implícitamente con esos usuarios junto con la aplicación.

## <a name="on-premises-data-gateways"></a>Puertas de enlace de datos locales
Si crea y comparte una aplicación que incluye datos de un origen local, la propia [puerta de enlace de datos](gateway-management.md) local y determinados tipos de conexiones se compartirán automáticamente. En el caso de conexiones que no se comparten automáticamente, puede compartirlas manualmente (como se muestra en la sección anterior) o dejar que la aplicación pregunte a los usuarios si quieren crear sus propias conexiones. Para mostrar las conexiones o las conexiones con las que se ha configurado una puerta de enlace:

1. Abra [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), haga clic o pulse **Administrar** en la barra de navegación izquierda y luego haga clic o pulse **Puertas de enlace**.
2. Pulse o haga clic en una puerta de enlace y luego pulse o haga clic en la ficha **Connections** (Conexiones).

> [!NOTE]
> Si comparte una o varias conexiones manualmente, puede que tenga que volver a compartirlas en estas circunstancias:

* Si agrega una puerta de enlace de datos local a una aplicación que ya ha compartido.
* Si cambia el conjunto de personas o grupos con quienes ha compartido una aplicación que tiene una puerta de enlace de datos local.

## <a name="custom-connectors"></a>Conectores personalizados.
Cuando se comparte una aplicación que utiliza un conector personalizado, se comparte automáticamente, pero los usuarios deben crear sus propias conexiones a ella.

En [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), puede ver o actualizar los permisos de un conector personalizado. En la barra de navegación izquierda, pulse o haga clic en **Manage** (Administrar), pulse o haga clic en **Connections** (Conexiones) y luego pulse o haga clic en **New connection** (Nueva conexión) (en la esquina superior derecha). Pulse o haga clic en **Personalizado** y luego en un conector personalizado para mostrar información detallada sobre él.

## <a name="excel-workbooks"></a>libros de Excel
Si una aplicación compartida usa datos a los que no todos los usuarios tienen acceso (por ejemplo, un libro de Excel en una cuenta de almacenamiento en la nube), [comparta los datos](share-app-data.md).

## <a name="flows"></a>Flujos
Si comparte una aplicación que incluye un flujo, a los usuarios que ejecuten la aplicación se les pedirá que confirmen o actualicen las conexiones en las que se basa el flujo. Además, solo la persona que ha creado el flujo puede personalizar sus parámetros. Por ejemplo, puede crear un flujo en el que se envíe correo a una dirección especificada pero otros usuarios no puedan cambiar esa dirección.

