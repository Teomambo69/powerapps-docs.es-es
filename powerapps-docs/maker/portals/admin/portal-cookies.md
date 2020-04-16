---
title: Cookies en portales de Power Apps | MicrosoftDocs
description: Conozca las cookies que usan los portales de Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/10/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 13730a4faa284890136cc04d2f56ff50c46d42e2
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136673"
---
# <a name="cookies-in-power-apps-portals"></a>Cookies en portales de Power Apps

Una cookie es un pequeño archivo enviado desde el sitio web al dispositivo del visitante por el navegador. Una sola sesión web puede usar múltiples cookies.

Los portales de Power Apps también usan cookies para almacenar información para diversos fines. La siguiente sección enumera y describe las cookies que usan los portales de Power Apps:

## <a name="names-and-descriptions-of-cookies-used-by-portals"></a>Nombres y descripciones de cookies utilizadas por los portales

#### <a name="arraffinity"></a>ARRAffinity

Agregada automáticamente por los sitios web de Azure y garantiza que las solicitudes tengan un equilibrio de carga entre diferentes sitios. No almacena ninguna información del usuario.

####  <a name="aspnet-session-id"></a>ASP.Net Session Id

Se usa para mantener la sesión de un usuario conectado para evitar el inicio de sesión repetido. La cookie no es persistente y se elimina después del cierre de la sesión.

#### <a name="dynamics-365-portal-analytics"></a>Análisis de portal de Dynamics 365

Cookie de servicio crítico para analizar el uso del servicio de forma anónima y agregada con fines estadísticos.

#### <a name="contextlanguagecode"></a>ContextLanguageCode

Almacena el idioma predeterminado del usuario que accede al portal dentro de una sesión y en páginas web. La cookie se elimina después de que se cierra la sesión.

#### <a name="aspnetapplicationcookie"></a>.AspNet.ApplicationCookie

Se usa para identificar sesiones de usuario. Una sesión de usuario comienza cuando un usuario navega por el portal por primera vez. Y termina cuando se cierra la sesión. [Configuración del sitio de autenticación](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity) se puede usar para cambiar el período de vencimiento de la sesión.

#### <a name="__requestverificationtoken"></a>__RequestVerificationToken 

Usada por el sistema [antiforgery](https://docs.microsoft.com/dotnet/api/system.web.helpers.antiforgeryconfig.cookiename).

#### <a name="adxpreviewunpublishedentities"></a>adxPreviewUnpublishedEntities

Tiene vista previa del modo **ENCENDIDO APAGADO** utilizado en el sistema CMS clásico para administradores de portal.

#### <a name="adx-notification"></a>adx-notification

Se utiliza en acciones de formulario de entidad para almacenar mensajes de alerta que se mostrarán en la redirección.

#### <a name="timezonecode"></a>timezoneCode

Contiene el valor de campo *timezonecode* de la entidad *CRM timezonedefinition* para la zona horaria actual.

#### <a name="timezoneoffset"></a>timezoneoffset

Contiene la [diferencia de zona horaria](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getTimezoneOffset) entre UTC y la hora del navegador local.

#### <a name="isdstsupport"></a>isDSTSupport

Indica si una fecha y hora especificadas se encuentran en el rango de horario de verano.

#### <a name="isdstobserved"></a>isDSTObserved

Almacena un valor para indicar si el momento actual está en el horario de verano.

### <a name="see-also"></a>Vea también

[Configuración del sitio de autenticación de cookies](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity#cookie-authentication-site-settings)

