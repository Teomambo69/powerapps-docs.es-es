---
title: Información general del Centro de administración de portales de Power Apps | MicrosoftDocs
description: Información general sobre el Centro de administración de portales de Power Apps
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 21e27be0c5c60d6c992c58839980283088f1c2b4
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977993"
---
# <a name="power-apps-portals-admin-center"></a>Centro de administración de portales de Power Apps

El Centro de administración de portales de Power Apps permite realizar acciones administrativas avanzadas en portales. El Centro de administración está disponible cuando un portal se aprovisiona correctamente.

## <a name="open-power-apps-portals-admin-center"></a>Abrir Centro de administración de portales de Power Apps

1. Vaya a la sección **Aplicaciones recientes** en la página principal de Power Apps y busque el portal.

    > [!div class=mx-imgBorder]
    > ![Aplicaciones recientes](../media/recent-apps.png "Aplicaciones recientes")  

2. Seleccione **Más comandos (...)** > **Configuración**.

    > [!div class=mx-imgBorder]
    > ![Opción de configuración del portal](../media/portal-settings-option.png "Opción de configuración del portal")

3. En el panel **Configuración del portal**, seleccione **Administración**.

    > [!div class=mx-imgBorder]
    > ![Panel de configuración del portal](../media/portal-settings-admin.png "Panel de configuración del portal")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>Agréguese como propietario de la aplicación de Azure AD

Si no es administrador global e intenta administrar un portal ya aprovisionado o quiere reenviar el aprovisionamiento si se crearon errores, debe ser el propietario de la aplicación de Azure Active Directory (Azure AD) que está conectada al portal.

1. Vaya al centro de administración de los portales de Power Apps y abra la pestaña **Detalles del portal**.

2. Copie el valor del campo **Id. de la aplicación**.

    > [!div class=mx-imgBorder]
    > ![Pestaña Detalles del portal](../media/portal-details-admin.png "Pestaña Detalles del portal")

3. Vaya a Azure AD asociada a su inquilino. [!include[](../../../includes/proc-more-information.md)] [Tome el control de un directorio no administrado como administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. En Azure AD, busque el registro de aplicaciones mediante el identificador de la aplicación que copió. Puede que deba cambiar de **Mis aplicaciones** a **Todas las aplicaciones**.

5. Agregue usuarios o grupos como propietarios de este registro de aplicación. [!include[](../../../includes/proc-more-information.md)] [Administrar el acceso a aplicaciones](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > Esta tarea la puede realizar el administrador global de su organización o el propietario existente de esta aplicación.

6. Una vez que se haya agregado como propietario, vuelva a abrir la página del centro de administración de portales de Power Apps.