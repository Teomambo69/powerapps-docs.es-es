---
title: Descargar una lista de usuarios activos en el inquilino | Microsoft Docs
description: En este inicio rápido, obtendrá información sobre cómo descargar una lista de usuarios activos en el inquilino.
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
ms.openlocfilehash: 41f557b7b4def385a505e3bc3047354add81955e
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42832457"
---
# <a name="download-a-list-of-active-users-in-your-tenant"></a>Descargar una lista de usuarios activos en el inquilino
Si es administrador global de Office 365 o administrador de inquilinos de Azure Active Directory, puede descargar una lista de usuarios activos en el inquilino, para poder ver no solo quién ha obtenido acceso a PowerApps, Microsoft Flow o ambos, sino también las licencias asignadas a esos usuarios.

En estos temas, aprenderá a descargar una lista de usuarios activos en un archivo .csv y luego ver esa lista en Excel.

Para seguir los pasos, necesitará permisos de Administrador global de Office 365 o de Administrador de inquilinos de Azure Active Directory.

## <a name="sign-in-to-the-powerapps-admin-center"></a>Iniciar sesión en el Centro de administración de PowerApps
Inicie sesión en el Centro de administración en [https://admin.powerapps.com]([https://admin.powerapps.com).

## <a name="download-the-list-of-users"></a>Descarga de la lista de usuarios
En el panel de navegación, pulse o haga clic en **Licencias de usuario** y, después, en **Descargar una lista de licencias de usuarios activos**.

![Archivo y Compartir](./media/admin-view-user-licenses/download-list.png)

La lista de usuarios se descarga a un archivo .csv. Este proceso podría tardar varios minutos. Asegúrese de no cerrar la ventana antes de que la lista se descargue completamente o es posible que tenga que reiniciar el proceso.

## <a name="view-the-list"></a>Ver la lista
Una vez creado el archivo .csv, ábralo en Excel. La lista contiene el nombre de cada usuario, la dirección de correo electrónico, el tipo de licencia y otra información.

Un usuario que ha tenido acceso a un producto al menos una vez se considera un *usuario activo*. Como esta es una lista de usuarios activos, no contiene usuarios que tienen licencias para PowerApps y Microsoft Flow pero que nunca han tenido acceso a ellos. Puede ver todas las licencias de usuario en el [Centro de administración de Office 365](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

En el ejemplo siguiente se muestran dos usuarios que tienen licencias para PowerApps y Microsoft Flow. Julia López tiene acceso a través de una suscripción a Office 365 y Juan García tiene una licencia de prueba para cada producto.

![Archivo y Compartir](./media/admin-view-user-licenses/table2.png)

Si un usuario ha dejado la organización, la lista mostrará **Desconocido** en las columnas **Nombre de usuario** y **Dirección de correo electrónico**. Si la lista muestra **Desconocido** pero nadie ha dejado la organización, espere unos minutos y vuelva a descargar la lista.

Para agregar licencias de usuario, abra el [Centro de administración de Office 365](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

## <a name="next-steps"></a>Pasos siguientes
En este tema, ha aprendido a descargar y ver una lista de usuarios activos en el inquilino. Para aprender a descargar y ver una lista de aplicaciones que se crearon en los entornos, continúe con el tema siguiente.

> [!div class="nextstepaction"]
> [Descargar una lista de aplicaciones que se crearon en los entornos](admin-view-apps.md)
