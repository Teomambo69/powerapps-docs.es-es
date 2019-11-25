---
title: Información general del Centro de administración de portales de PowerApps | MicrosoftDocs
description: Información general sobre el Centro de administración de portales de PowerApps
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6f8434a6a395931fc4edfe02913f47536b4a709d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756188"
---
# <a name="powerapps-portals-admin-center"></a>Centro de administración de portales de PowerApps

El Centro de administración de portales de PowerApps permite realizar acciones administrativas avanzadas en portales. El Centro de administración está disponible cuando un portal se aprovisiona correctamente.

## <a name="open-powerapps-portals-admin-center"></a>Abrir Centro de administración de portales de PowerApps

1. Vaya a la sección **Aplicaciones recientes** en la página principal de PowerApps y busque el portal.

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

1. Vaya al centro de administración de los portales de PowerApps y abra la pestaña **Detalles del portal**.

2. Copie el valor del campo **Id. de la aplicación**.

    > [!div class=mx-imgBorder]
    > ![Pestaña Detalles del portal](../media/portal-details-admin.png "Pestaña Detalles del portal")

3. Vaya a Azure AD asociada a su inquilino. [!include[](../../../includes/proc-more-information.md)] [Tome el control de un directorio no administrado como administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. En Azure AD, busque el registro de aplicaciones mediante el identificador de la aplicación que copió. Puede que deba cambiar de **Mis aplicaciones** a **Todas las aplicaciones**.

5. Agregue usuarios o grupos como propietarios de este registro de aplicación. [!include[](../../../includes/proc-more-information.md)] [Administrar el acceso a aplicaciones](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > Esta tarea la puede realizar el administrador global de su organización o el propietario existente de esta aplicación.

6. Una vez que se haya agregado como propietario, vuelva a abrir la página del centro de administración de portales de PowerApps.