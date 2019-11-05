---
title: Configurar la autenticación del portal | MicrosoftDocs
description: Obtenga información sobre cómo configurar la autenticación para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b285ce6e3a93efb72ed867149ce0740f7ee96579
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542763"
---
# <a name="configure-portal-authentication"></a>Configuración de la autenticación del portal

En una aplicación de portal, un usuario del portal autenticado está asociado a un contacto o usuario del sistema. La configuración predeterminada de portales se basa en el contacto. Para iniciar sesión, un contacto debe tener configurada la información de autenticación Web adecuada. Los usuarios del portal deben estar asignados a un rol Web para obtener permisos más allá de los usuarios no autenticados. Para configurar permisos para un rol Web, configure el acceso a la página web y las reglas de control de acceso a sitios Web.

La última experiencia de autenticación del portal permite a los usuarios del portal iniciar sesión con su elección de una cuenta local basada en el proveedor de pertenencia de contactos o una cuenta externa basada en [ASP.net Identity](https://www.asp.net/identity).   

- **Autenticación local**: la autenticación local es la que usa los registros de contacto de un entorno de Common Data Service para la autenticación. Para compilar experiencias de autenticación personalizadas, los desarrolladores pueden usar la API de identidad de ASP.Net para crear páginas y herramientas de inicio de sesión personalizadas.
- **Autenticación externa**: la API de ASP.net Identity proporciona la autenticación externa. En este caso, las credenciales de la cuenta y la administración de contraseñas se controlan mediante un proveedor de identidades de terceros. Esto incluye proveedores basados en OpenID, como Yahoo! y los proveedores basados en Google y OAuth 2,0, como Twitter, Facebook y [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]. Los usuarios se suscriben al portal seleccionando una identidad externa para registrarse en el portal. Una vez registrada, una identidad externa tiene acceso a las mismas características que una cuenta local. 

Tanto el registro de la cuenta local como la externa pueden usar códigos de invitación para suscribirse, así como el flujo de trabajo de confirmación por correo electrónico. Además, los administradores del portal pueden optar por habilitar o deshabilitar cualquier combinación de opciones de autenticación a través de la configuración del sitio del portal.

> [!NOTE]
> Los usuarios del portal deben tener una dirección de correo electrónico única. Si dos o más registros de contacto (incluidos los registros de contactos desactivados) tienen la misma dirección de correo electrónico, los contactos no podrán autenticarse en el portal.

## <a name="account-sign-up-registration"></a>Registro de cuenta (registro)

Los administradores del portal tienen varias opciones para controlar el comportamiento de inicio de sesión de la cuenta. Open registration es la configuración de registro menos restrictiva, donde el portal permite registrar una cuenta de usuario con solo proporcionar una identidad de usuario. Las configuraciones alternativas pueden requerir que los usuarios proporcionen un código de invitación o una dirección de correo electrónico válida para registrarse en el portal. Independientemente de la configuración del registro, las cuentas locales y externas participan igualmente en el flujo de trabajo de registro. Es decir, los usuarios tienen la opción de elegir el tipo de cuenta que desea registrar.

## <a name="open-registration"></a>Abrir registro

Durante el registro, el usuario tiene la opción de crear una cuenta local (proporcionando un nombre de usuario y una contraseña) o seleccionar una identidad externa en una lista de proveedores de identidades. Si se selecciona una identidad externa, el usuario deberá iniciar sesión a través del proveedor de identidades elegido para demostrar que posee la cuenta externa. En cualquier caso, el usuario se registra y se autentica inmediatamente con el portal. Al suscribirse, se crea un nuevo registro de contacto en el entorno de Common Data Service.

Con el registro abierto habilitado, no es necesario que los usuarios proporcionen un código de invitación para completar el proceso de registro.

### <a name="see-also"></a>Vea también

[Establecimiento de la identidad de autenticación para un portal](set-authentication-identity.md)  
