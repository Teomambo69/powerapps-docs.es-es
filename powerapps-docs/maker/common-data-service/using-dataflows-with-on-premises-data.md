---
title: Uso de una puerta de enlace de datos local en flujos de datos de Power Platform | MicrosoftDocs
description: Aprenda a usar una puerta de enlace de datos local en flujos de datos de Power Platform
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4a47f082520b4680c9045209f85c26beb3586875
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752258"
---
# <a name="using-an-on-premises-data-gateway-in-power-platform-dataflows"></a>Uso de una puerta de enlace de datos local en flujos de datos de Power Platform
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Instale una puerta de enlace de datos local para transferir los datos de forma rápida y segura entre un flujo de datos de Power Platform y un origen de datos que no está en la nube, como una base de datos de SQL Server local o un sitio SharePoint local.
Se pueden ver todas las puertas de enlace para las cuales dispone de permisos administrativos y administrar los permisos y las conexiones de estas puertas de enlace.

Con una puerta de enlace, puede conectarse a los datos locales a través de estas conexiones:

-   SharePoint

-   SQL Server

-   Oracle

-   Informix

-   Filesystem

-   DB2

## <a name="prerequisites"></a>Requisitos previos

-   Una cuenta de PowerApps. ¿No tiene una? [Suscribirse durante 30 días gratis](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps).

-   Se requieren permisos administrativos sobre una puerta de enlace. Estos permisos se proporcionan de forma predeterminada para las puertas de enlace que instale. Los administradores pueden conceder permisos a otros usuarios para puertas de enlace. 

-   Una licencia que admite datos locales de acceso mediante una puerta de enlace local. Para obtener más información, consulte la sección “Conectar con los datos y sistemas" de [Buscar la página del plan de PowerApps adecuado](https://powerapps.microsoft.com/pricing/)”.

-   Las puertas de enlace y las conexiones locales se pueden crear y usar solo en el entorno predeterminado del usuario. Más información: [Trabajar con entornos y Microsoft PowerApps](../canvas-apps/working-with-environments.md).

## <a name="install-a-gateway"></a>Instalar una puerta de enlace
1.  En el panel de navegación de la izquierda de [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Puertas de enlace**.

    ![Puertas de enlace en barra de navegación izquierda](media/nav-pane-gateways.png)

2.  Seleccione una puerta de enlace de la lista. Si no tiene permisos administrativos para una puerta de enlace, seleccione [Instale ahora una puerta de enlace](https://go.microsoft.com/fwlink/?LinkID=820931) y, a continuación siga las indicaciones del asistente.

     ![Instalación de puertas de enlace](media/install-gateway-now.png)

     Para obtener más información sobre cómo instalar una puerta de enlace, consulte [Comprender las puertas de enlace de datos locales](../canvas-apps/gateway-reference.md).

## <a name="use-an-on-premises-data-source-in-a-dataflow"></a>Usar un origen de datos local en un flujo de datos
1. Seleccione un origen de datos local de la lista de orígenes de datos.

   ![Elija un origen de datos local](media/on-premises-data-sources.png)

2. Proporcione los detalles de la conexión para la puerta de enlace de empresa que se usará para tener acceso a los datos locales. Debe seleccionar la propia puerta de enlace, y proporcionar credenciales para la puerta de enlace seleccionada. Solo aparecen en la lista las puertas de enlace para las que es administrador.

    ![Proporcionar detalles de conexiones](media/connection-creds.png)

Puede cambiar la puerta de enlace de empresa usada para un flujo de datos determinado y cambiar la puerta de enlace asignada a todas las consultas con la herramienta de creación de flujos de datos.

> [!NOTE]
> El flujo de datos intentará encontrar o crear los orígenes de datos requeridos mediante la nueva puerta de enlace. Si no puede hacerlo, no podrá cambiar la puerta de enlace hasta que todos los flujos de datos necesarios estén disponibles desde la puerta de enlace seleccionada.


## <a name="view-and-manage-gateway-permissions"></a>Ver y administrar permisos de puerta de enlace
1.  En el panel de navegación de la izquierda de [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Puertas de enlace** y seleccione la puerta de enlace que desee.

2.  Para agregar un usuario a una puerta de enlace, seleccione **Usuarios**, especifique un usuario o un grupo, y después especifique un nivel de permisos:

    -   **Puede usar.** Los usuarios con este permiso pueden crear conexiones en la puerta de enlace para usar para aplicaciones y flujos, pero no pueden compartir la puerta de enlace. Use este permiso para usuarios que ejecutarán aplicaciones pero no las comparten.

    -   **Puede usar + compartir.** Los usuarios con este permiso pueden crear una conexión en la puerta de enlace para usar para aplicaciones y flujos, y compartir automáticamente la puerta de enlace cuando compartan una aplicación. Use este permiso para los usuarios que necesiten compartir aplicaciones con otros usuarios o con la organización.

    -   **Administración.** Los administradores tienen control total de puerta de enlace, incluido agregar usuarios, establecer permisos, crear conexiones a todos los orígenes de datos disponibles, y eliminar la puerta de enlace.

      Para los niveles de permisos **Puede usar** y **Puede usar + compartir**, seleccione los orígenes de datos con los que el usuario puede conectarse a través de puerta de enlace.

## <a name="view-and-manage-gateway-connections"></a>Ver y administrar conexiones de puerta de enlace
1.  En la barra de navegación de la izquierda de *powerapps.com*, seleccione **Puertas de enlace** y elija la puerta de enlace que desee.

2.  Realice la acción que desee: 
    - Para ver detalles, editar valores, o eliminar una puerta de enlace, seleccione **Conexiones** y luego seleccione una conexión.
    - Para compartir una conexión, seleccione **Compartir** y agregue o elimine usuarios.

      > [!NOTE]
      > Puede compartir solo algunos tipos de conexiones, como una conexión SQL Server. Para obtener más información, consulte [Compartir recursos de aplicación de lienzo en PowerApps](../canvas-apps/share-app-resources.md). <br />
      >
      > Para obtener más información acerca de cómo administrar una conexión, consulte [Administrar conexiones de aplicación de lienzo en PowerApps](../canvas-apps/add-manage-connections.md).


## <a name="limitations"></a>Limitaciones
Hay algunas limitaciones conocidas al usar puertas de enlace y flujos de datos de empresa.

-   Cada flujo de datos puede usar únicamente una puerta de enlace. Por lo tanto, todas las consultas deben configurarse con la misma puerta de enlace.

-   Cambiar la puerta de enlace afecta al flujo de datos completo.

-   Si se necesitan varias puertas de enlace, la práctica recomendada es crear varios flujos de datos (uno para cada puerta de enlace) y usar las funcionalidades de referencia de cálculo o entidad para unificar los datos.

-   Los flujos de datos solo se admiten usando puertas de enlace de empresa. Las puertas de enlace personales no estarán disponibles para selección en las listas desplegables y las pantallas de configuración.

Para obtener información sobre solucionar los problemas con puertas de enlace, o configurar servicio de puerta de enlace para la red, consulte [Comprender las puertas de enlace de datos locales](../canvas-apps/gateway-reference.md).

## <a name="next-steps"></a>Pasos siguientes

- [Creación y uso de flujos de datos en PowerApps](create-and-use-dataflows.md)

- [Agregar datos a una entidad en Common Data Service con Power Query](data-platform-cds-newentity-pq.md)

- [Conexión a Azure Data Lake Storage Gen2 para el almacenamiento del flujo de datos](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)


