---
title: Preguntas más frecuentes | Documentos de Microsoft
description: Preguntas más frecuentes en portales de PowerApps
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 10/02/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="powerapps-portals-faq"></a>Preguntas más frecuentes sobre Portales de PowerApps

Hemos recopilado una lista de preguntas frecuentes con respuestas breves para que obtenga la información que necesita con rapidez.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Recibo un error de que sólo un portal pueda ser creado.

Actualmente, puede crear solo un portal de cada tipo en un entorno por idioma. Si intenta crear más de un portal, verá un mensaje de error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de portales máximos creados](media/portal-max-error.png "Error de portales máximos creados")

Para crear más portales, debe crear un nuevo entorno mediante el vínculo **crear nuevo entorno** en el mensaje de error. Para obtener más información sobre crear un portal, consulte [Crear un portal](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Recibo un error de que no puedo eliminar mi portal.

Si no tiene suficientes privilegios para eliminar un portal, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de eliminar portal](media/portal-delete-error.png "Error de eliminar portal")

Para obtener información sobre eliminar un portal y los privilegios necesarios, vea [Eliminar un portal](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Recibo un error de que no puedo crear un portal.

Si no tiene suficientes privilegios para crear un portal en un entorno, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de crear portal](media/portal-create-error.png "Error de crear portal")

Para obtener información sobre crear un portal y los privilegios necesarios, vea [Crear un portal](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Recibo el mensaje: “Sus datos no están listos”.

Algunas veces la creación de la base de datos puede tardar un tiempo y el estado correcto puede no reflejarse en la página principal. En este caso verá el mensaje siguiente:

> [!div class=mx-imgBorder]
> ![Los datos no están listos](media/data-not-ready.png "Los datos no están listos")

Si sigue recibiendo el mensaje de crear base de datos o los datos no están listos, puede intentar actualizar la página principal de PowerApps antes de seleccionar la ventana Portal en blanco (vista previa).

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Recibo un error de que no tengo los permisos necesarios para crear aplicaciones de Azure Active Directory.

Al crear un portal, el portal como nueva aplicación se registra en Azure Active Directory asociado al inquilino. Si no tiene suficientes privilegios para registrar una aplicación con el inquilino de Azure Active Directory, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de Azure Active Directory](media/azure-ad-error.png "Error de Azure Active Directory")

Para crear y registrar aplicaciones en Azure Active Directory, debe ponerse en contacto con el administrador de inquilinos para activar la configuración **Registros de aplicación** para su inquilino. Para obtener información, consulte [Permisos requeridos](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Recibo un error de que la creación del portal es bloqueada en este inquilino por el administrador global

Si la creación del portal está bloqueada en un inquilino por el administrador global, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de bloqueo de creación de portal](media/portal-create-blocked-error.png "Error de bloqueo de creación de portal")

Debe ponerse en contacto con el administrador global para habilitar la creación de portales por no administradores.

Si usted es un administrador global, debe deshabilitar el valor del nivel de inquilino de `disablePortalsCreationByNonAdminUsers` con PowerShell. Ejecute el siguiente comando en una ventana de PowerShell (ejecute PowerShell como administrador).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Más información: [Deshabilitar creación de portal en un inquilino](create-portal.md#disable-portal-creation-in-a-tenant)
