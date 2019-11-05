---
title: Preguntas más frecuentes | Microsoft Docs
description: Preguntas más frecuentes en los portales de PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 810829b58d666b66bd2cac7235d013a4bfdcd806
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542544"
---
# <a name="powerapps-portals-faq"></a>Preguntas más frecuentes sobre portales de PowerApps

Hemos compilado una lista de las preguntas más frecuentes y hemos proporcionado breves respuestas para ayudarle a llegar a su información rápidamente.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Obtengo un error que solo se puede crear un portal.

Actualmente, solo puede crear un portal de cada tipo en un entorno por idioma. Si intenta crear más de un portal, verá un mensaje de error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error del portal máximo creado](media/portal-max-error.png "Error del portal máximo creado")

Para crear más portales, debe crear un nuevo entorno mediante el vínculo **crear nuevo entorno** en el mensaje de error. Para más información sobre la creación de un portal, consulte [creación de un portal](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Obtengo un error que no puedo eliminar mi portal.

Si no tiene privilegios suficientes para eliminar un portal, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error al eliminar el portal](media/portal-delete-error.png "Error al eliminar el portal")

Para obtener información sobre cómo eliminar un portal y los privilegios necesarios, consulte [eliminación de un portal](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Obtengo un error que no se puede crear un portal.

Si no tiene privilegios suficientes para crear un portal en un entorno, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error al crear el portal](media/portal-create-error.png "Error al crear el portal")

Para obtener información sobre cómo crear un portal y los privilegios necesarios, consulte [creación de un portal](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Obtengo el mensaje: "los datos no están bastante listos".

A veces, la creación de la base de datos puede tardar un tiempo y el estado correcto podría no reflejarse en la Página principal. En este caso, verá el siguiente mensaje:

> [!div class=mx-imgBorder]
> ![Datos no listos](media/data-not-ready.png "Datos no listos")

Si sigue recibiendo el mensaje de solicitud de creación de base de datos o el aviso los datos no están listos, puede intentar actualizar la Página principal de PowerApps antes de seleccionar el icono **del portal en blanco** .

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Obtengo un error que no tengo los permisos necesarios para crear Azure Active Directory aplicaciones.

Al crear un portal, el portal como una nueva aplicación se registra en Azure Active Directory asociado al inquilino. Si no tiene permisos suficientes para registrar una aplicación en el inquilino de Azure Active Directory, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de Azure Active Directory](media/azure-ad-error.png "Error de Azure Active Directory")

Para crear y registrar aplicaciones en Azure Active Directory, debe ponerse en contacto con el administrador de inquilinos para activar la configuración de **registros de aplicaciones** de su inquilino. Para obtener más información, consulte [permisos necesarios](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Obtengo un error en el que el administrador global bloquea la creación del portal en este inquilino

Si el administrador global bloquea la creación del portal en un inquilino, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de creación del portal bloqueada](media/portal-create-blocked-error.png "Error de creación del portal bloqueada")

Debe ponerse en contacto con el administrador global para habilitar también la creación de portales por parte de usuarios que no sean administradores.

Si es un administrador global, debe deshabilitar la configuración de nivel de inquilino `disablePortalsCreationByNonAdminUsers` a través de PowerShell. Ejecute el siguiente comando en una ventana de PowerShell (ejecute PowerShell como administrador).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Más información: [deshabilitar la creación del portal en un inquilino](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Obtengo un error que no tengo la licencia adecuada para tener acceso a este sitio Web.

Los usuarios internos de una organización que usan portales para tener acceso a las páginas autenticadas requieren que las licencias se asignen al entorno al que está conectado un portal. Puede leer más acerca de los derechos de usuario para los portales para los usuarios internos [aquí](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users). Cuando un entorno no tiene licencias asignadas, los usuarios internos recibirán un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de inicio de sesión del portal](media/portal-login-error.png "Error de inicio de sesión del portal")

