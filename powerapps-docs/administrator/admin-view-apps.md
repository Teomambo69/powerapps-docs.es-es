---
title: Descargar una lista de aplicaciones creadas en los entornos | Microsoft Docs
description: En este inicio rápido, obtendrá información sobre cómo descargar una lista de aplicaciones creadas en los entornos.
author: jimholtz
ms.service: powerapps
ms.component: pa-admin
ms.topic: quickstart
ms.date: 03/21/2018
ms.author: jimholtz
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 8a94439a1f3de2d269600ed1894c8c3bf991d030
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42845324"
---
# <a name="download-a-list-of-apps-created-in-your-environments"></a>Descargar una lista de aplicaciones creadas en los entornos
Si es un Administrador de entorno, puede ver y descargar una lista de aplicaciones creadas en los entornos que está administrando. Si es un Administrador global de Office 365 o de inquilinos de Azure Active Directory, puede ver y descargar la lista de aplicaciones creadas en todos los entornos de la organización.

En este tutorial, aprenderá a descargar una lista de aplicaciones creadas en un entorno a un archivo .csv y luego ver esa lista en Excel.

## <a name="prerequisites"></a>Requisitos previos
 Para seguir los pasos se requieren los elementos siguientes:
 * Licencia de Plan 2 de PowerApps o Plan 2 de Microsoft Flow. Como alternativa, se puede suscribir a una [evaluación gratuita del Plan 2 de PowerApps](https://web.powerapps.com/signup?redirect=marketing&email=).
 * Los permisos Administrador de entorno de PowerApps, Administrador global de Office 365 o Administrador de inquilinos de Azure Active Directory. Para obtener más información, vea [Administración de entornos en PowerApps](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Iniciar sesión en el Centro de administración de PowerApps
Inicie sesión en el Centro de administración en [https://admin.powerapps.com]([https://admin.powerapps.com).

## <a name="download-the-list-of-apps"></a>Descarga de la lista de aplicaciones
1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, pulse o haga clic en el entorno para el que quiera descargar la lista de aplicaciones.

    ![Archivo y Compartir](./media/admin-view-apps/environment.png)
2. En la pestaña **Recursos**, pulse o haga clic en **Aplicaciones** y después en **Download the list of apps** (Descargar la lista de aplicaciones).

    ![Archivo y Compartir](./media/admin-view-apps/resources-app.png)

    La lista de aplicaciones se descarga a un archivo .csv. Este proceso podría tardar varios minutos. Asegúrese de no cerrar la ventana antes de que la lista se descargue completamente o es posible que tenga que reiniciar el proceso.

## <a name="view-the-list"></a>Ver la lista
Una vez creado el archivo .csv, ábralo en Excel. La lista contiene el nombre para mostrar de la aplicación, el propietario de la aplicación, todos los conectores que la aplicación usa para conectarse a orígenes de datos y otra información.

![Archivo y Compartir](./media/admin-view-apps/excel-view.png)

## <a name="next-steps"></a>Pasos siguientes
En este tema, ha aprendido a descargar y ver una lista de aplicaciones creadas en un entorno dentro de la organización. A continuación, obtendrá información sobre cómo administrar las aplicaciones creadas en la organización.

> [!div class="nextstepaction"]
> [Administración de las aplicaciones creadas en la organización](admin-manage-apps.md)
