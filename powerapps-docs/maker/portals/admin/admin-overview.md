---
title: Información general sobre el centro de administración de portales de PowerApps | MicrosoftDocs
description: Información sobre el centro de administración de portales de PowerApps.
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543071"
---
# <a name="powerapps-portals-admin-center"></a>Centro de administración de portales de PowerApps

El centro de administración de portales de PowerApps permite realizar acciones administrativas avanzadas en los portales. El centro de administración está disponible cuando se aprovisiona un portal correctamente.

## <a name="open-powerapps-portals-admin-center"></a>Abrir el centro de administración de portales de PowerApps

1. Vaya a la sección **aplicaciones recientes** en la Página principal de PowerApps y busque el portal.

    > [!div class=mx-imgBorder]
    > ![Aplicaciones recientes](../media/recent-apps.png "Aplicaciones recientes")  

2. Seleccione **más comandos (...)**  > **configuración**.

    > [!div class=mx-imgBorder]
    > ![Opción de configuración del portal](../media/portal-settings-option.png "Opción de configuración del portal")

3. En el panel **configuración del portal** , seleccione **Administración**.

    > [!div class=mx-imgBorder]
    > ![Panel de configuración del portal](../media/portal-settings-admin.png "Panel de configuración del portal")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>Agregarse como propietario de la aplicación Azure AD

Si no es un administrador global e intenta administrar un portal que ya se ha aprovisionado, o si se vuelve a enviar el aprovisionamiento en caso de error, debe ser el propietario de la aplicación Azure Active Directory (Azure AD) conectada a su portal.

1. Vaya al centro de administración de portales de PowerApps y abra la pestaña **detalles del portal** .

2. Copie el valor del campo **ID** . de aplicación.

    > [!div class=mx-imgBorder]
    > ![Pestaña detalles del portal](../media/portal-details-admin.png "Pestaña detalles del portal")

3. Vaya a Azure AD asociado a su inquilino. [!include[](../../../includes/proc-more-information.md)] [asumir un directorio no administrado como administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. En Azure AD, busque el registro de la aplicación con el identificador de aplicación que ha copiado. Es posible que tenga que cambiar de **mis aplicaciones** a **todas las aplicaciones**.

5. Agregar usuarios o grupos como propietarios de este registro de aplicaciones. [!include[](../../../includes/proc-more-information.md)] [administrar el acceso a las aplicaciones](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > Esta tarea la puede realizar un administrador global de su organización o el propietario existente de esta aplicación.

6. Después de agregarse como propietario, vuelva a abrir la página del centro de administración de portales de PowerApps.