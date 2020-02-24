---
title: Configurar autenticación de un portal | MicrosoftDocs
description: Aprender a configurar la autenticación de un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: acae3e962ed23e9cdff9cf74c1b6c5b7706c23be
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979181"
---
# <a name="configure-portal-authentication"></a>Configurar la autenticación del portal

En una aplicación de portal, un usuario del portal autenticado se asocia con un contacto o un usuario del sistema. La configuración de portales predeterminada se basa en contactos. Para iniciar sesión, un contacto debe tener la información de autenticación web adecuada configurada. Los usuarios del portal deben asignarse a roles web para obtener permisos por encima de los usuarios no autenticados. Para configurar permisos para un rol web, configure su acceso a páginas web y reglas de control de acceso a sitios web.

La experiencia más reciente de autenticación en el portal permite a los usuarios iniciar sesión con proveedor local de suscripciones de contacto que prefiera o con una cuenta externa basada en [Identidad de ASP.NET](https://www.asp.net/identity).   

- **Autenticación local**: La autenticación local es la autenticación basada en formularios común que usa registros de contacto de una organización de entorno Common Data Service para autenticación. Para crear experiencias de autenticación personalizadas, los desarrolladores pueden usar la API de identidad ASP.Net para crear páginas y herramientas de inicio de sesión personalizadas.
- **Autenticación externa**: La autenticación externa se proporciona mediante la API de identidad de ASP.NET. En este caso, las credenciales de cuenta y la administración de contraseñas se controlan mediante un proveedor de identidad de terceros. Esto incluye proveedores basados en OpenID como Yahoo! y proveedores basados en Google y OAuth 2.0 como Twitter, Facebook y [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]. Los usuarios se suscriben al portal seleccionando una identidad externa para registrarse en el portal. Una vez registrada, una identidad externa tiene acceso a las mismas características que una cuenta local. 

El registro de cuentas locales y externas puede usar de códigos de invitación para iniciar sesión, así como del flujo de trabajo de confirmación de correo electrónico. Además, los administradores del portal pueden habilitar o deshabilitar cualquier combinación de opciones de autenticación mediante la configuración de sitios del portal.

> [!NOTE]
> Los usuarios del portal deben tener una dirección de correo electrónico única. Si hay dos o más registros de contactos (incluidos registros de contactos desactivados) con la misma dirección de correo electrónico, los contactos no podrán autenticarse en el portal.

## <a name="account-sign-up-registration"></a>Suscripción de cuenta (registro)

Los administradores del portal tienen varias opciones para controlar el comportamiento de suscripción a cuentas. El registro abierto es la configuración de suscripción menos restrictiva, donde el portal permite registrar una cuenta de usuario simplemente proporcionando una identidad del usuario. Las configuraciones alternativas pueden requerir que los usuarios proporcionen un código de invitación o una dirección de correo electrónico válida para registrarse con el portal. Independientemente de la configuración del registro, las cuentas locales y externas participan por igual en el flujo de trabajo del registro. Es decir, los usuarios tienen la opción de elegir el tipo de cuenta al que desean registrarse.

## <a name="open-registration"></a>Registro abierto

Durante la suscripción, el usuario tiene la opción de crear una cuenta local (mediante un nombre de usuario y una contraseña) o de seleccionar una identidad externa de una lista de proveedores de identidad. Si selecciona una identidad externa, el usuario debe iniciar sesión a través del proveedor de identidad elegido para probar que posee la cuenta externa. En cualquier caso, el usuario inmediatamente se registra y autentica en el portal. Un nuevo registro de contacto se crea en el entorno de Common Data Service tras la suscripción.

Con el registro abierto habilitado, no es necesario que los usuarios proporcionen un código de invitación para completar el proceso de suscripción.

### <a name="see-also"></a>Vea también

[Establecer identidad de autenticación para un portal](set-authentication-identity.md)  
