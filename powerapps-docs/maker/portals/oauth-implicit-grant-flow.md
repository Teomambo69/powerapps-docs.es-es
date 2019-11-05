---
title: Usar el flujo de concesión implícita de OAuth 2,0 en el portal | MicrosoftDocs
description: Obtenga información sobre cómo realizar llamadas del lado cliente a las API externas y protegerlas mediante el flujo de concesión implícita de OAuth en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 38a1ac18a5c978c7b39d6dee85afcb9adf334534
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542416"
---
# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>Usar el flujo de concesión implícita de OAuth 2,0 en el portal 

Esta característica permite a los clientes realizar llamadas del lado cliente a API externas y protegerlas mediante el flujo de concesión implícita de OAuth. Proporciona un punto de conexión para obtener tokens de acceso seguro que contendrán la información de identidad de usuario que usarán las API externas para la autorización siguiendo el flujo de concesión implícita de OAuth 2,0. La información de identidad de un usuario que ha iniciado sesión se pasa de forma segura a las llamadas AJAX externas. Esto no solo ayudará a los desarrolladores a pasar el contexto de autenticación, sino que también ayudará a los usuarios a proteger sus API mediante este mecanismo.

El flujo de concesión implícita de OAuth 2,0 admite puntos de conexión a los que un cliente puede llamar para obtener un token de identificador. Para este propósito, se usan dos extremos: [Authorize](#authorize-endpoint-details) y [token](#token-endpoint-details).

## <a name="authorize-endpoint-details"></a>Autorización de los detalles del extremo 

La dirección URL del punto de conexión de autorización es: `<portal_url>/_services/auth/authorize`. El punto de conexión de autorización admite los parámetros siguientes:

| Parámetro   | ¿Obligatorio? | Descripción                             |
|---------------|-----------|---------------------------------------|
| client_id      | Sí       | Cadena que se pasa al realizar una llamada al extremo de autorización. Debe asegurarse de que el identificador de cliente está [registrado con el portal](#register-client-id-for-implicit-grant-flow). De lo contrario, se muestra un error. El ID. de cliente se agrega en las notificaciones del token como `aud`, así como `appid` parámetro y los clientes pueden usar para validar que el token devuelto es para su aplicación.<br>La longitud máxima es de 36 caracteres. Solo se admiten caracteres alfanuméricos y guiones. |
| redirect_uri      | Sí       | Dirección URL del portal donde se pueden enviar y recibir las respuestas de autenticación. Debe registrarse para el `client_id` determinado que se usa en la llamada y debe ser exactamente el mismo valor que el registrado.            |
| State       | No        | Un valor incluido en la solicitud que también se devuelve en la respuesta del token. Puede ser una cadena de cualquier contenido que desee usar. Normalmente, se usa un valor único generado de forma aleatoria para evitar los ataques de falsificación de solicitudes entre sitios.<br>La longitud máxima es de 20 caracteres.              |
| emisor   | No        | Un valor de cadena enviado por el cliente que se incluye en el token de identificador resultante como una demanda. A continuación, el cliente puede comprobar este valor para mitigar los ataques de reproducción de tokens. La longitud máxima es de 20 caracteres.      |
| response_type         | No        | Este parámetro solo admite `token` como valor. Esto permite que la aplicación reciba inmediatamente un token de acceso del punto de conexión de autorización, sin realizar una segunda solicitud al punto de conexión de autorización.                               |
|||

### <a name="successful-response"></a>Respuesta correcta

El punto de conexión Authorize devuelve los siguientes valores en la dirección URL de respuesta como un fragmento:

- **token**: el token se devuelve como un JSON Web Token (JWT) firmado digitalmente por la clave privada del portal.
- **Estado**: si se incluye un parámetro de estado en la solicitud, debe aparecer el mismo valor en la respuesta. La aplicación debe comprobar que los valores de estado de la solicitud y la respuesta son idénticos.
- **expires_in**: la cantidad de tiempo que el token de acceso es válido (en segundos).

Por ejemplo, una respuesta correcta tiene el siguiente aspecto:

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>Respuesta de error

El error del punto de conexión de autorización se devuelve como un documento JSON con los siguientes valores:

- **Identificador de error**: identificador único del error.
- **Mensaje de error**: un mensaje de error específico que puede ayudarle a identificar la causa raíz de un error de autenticación.
- **Identificador de correlación**: GUID que se usa para la depuración. Si ha habilitado el registro de diagnóstico, el identificador de correlación estará presente en los registros de errores del servidor.
- **Timestamp**: fecha y hora en que se generó el error.

El mensaje de error se muestra en el idioma predeterminado del usuario que inició sesión. Si el usuario no ha iniciado sesión, se muestra la página de inicio de sesión para que el usuario inicie sesión. Por ejemplo, una respuesta de error tiene el siguiente aspecto:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>Detalles del extremo del token

También puede obtener un token realizando una solicitud al punto de conexión de `/token`. Es diferente del punto de conexión de autorización en la forma en que el punto de conexión de autorización controla la lógica del token en una página independiente (redirect_uri), mientras que el punto de conexión del token controla la lógica del token en la misma página. La dirección URL del punto de conexión del token es: `<portal_url>/_services/auth/token`. El punto de conexión del token admite los parámetros siguientes:

| Parámetro   | ¿Obligatorio? | Descripción                             |
|---------------|-----------|---------------------------------------|
| client_id      | No       | Cadena que se pasa al realizar una llamada al extremo de autorización. Debe asegurarse de que el identificador de cliente está [registrado con el portal](#register-client-id-for-implicit-grant-flow). De lo contrario, se muestra un error. El ID. de cliente se agrega en las notificaciones del token como `aud`, así como `appid` parámetro y los clientes pueden usar para validar que el token devuelto es para su aplicación.<br>La longitud máxima es de 36 caracteres. Solo se admiten caracteres alfanuméricos y guiones. |
| redirect_uri      | No       | Dirección URL del portal donde se pueden enviar y recibir las respuestas de autenticación. Debe registrarse para el `client_id` determinado que se usa en la llamada y debe ser exactamente el mismo valor que el registrado.            |
| State       | No        | Un valor incluido en la solicitud que también se devuelve en la respuesta del token. Puede ser una cadena de cualquier contenido que desee usar. Normalmente, se usa un valor único generado de forma aleatoria para evitar los ataques de falsificación de solicitudes entre sitios.<br>La longitud máxima es de 20 caracteres.              |
| emisor   | No        | Un valor de cadena enviado por el cliente que se incluye en el token de identificador resultante como una demanda. A continuación, el cliente puede comprobar este valor para mitigar los ataques de reproducción de tokens. La longitud máxima es de 20 caracteres.      |
| response_type         | No        | Este parámetro solo admite `token` como valor. Esto permite que la aplicación reciba inmediatamente un token de acceso del punto de conexión de autorización, sin realizar una segunda solicitud al punto de conexión de autorización.                               |
|||

> [!NOTE]
> Aunque los parámetros `client_id`, `redirect_uri`, `state`y `nonce` son opcionales, se recomienda usarlos para asegurarse de que sus integraciones son seguras.

### <a name="successful-response"></a>Respuesta correcta

El punto de conexión del token devuelve State y expires_in como encabezados de respuesta y token en el cuerpo del formulario.

### <a name="error-response"></a>Respuesta de error

El error en un punto de conexión de token se devuelve como un documento JSON con los siguientes valores:

- **Identificador de error**: identificador único del error.
- **Mensaje de error**: un mensaje de error específico que puede ayudarle a identificar la causa raíz de un error de autenticación.
- **Identificador de correlación**: GUID que se usa para la depuración. Si ha habilitado el registro de diagnóstico, el identificador de correlación estará presente en los registros de errores del servidor.
- **Timestamp**: fecha y hora en que se generó el error.

El mensaje de error se muestra en el idioma predeterminado del usuario que inició sesión. Si el usuario no ha iniciado sesión, se muestra una página de inicio de sesión para que el usuario inicie sesión. Por ejemplo, una respuesta de error tiene el siguiente aspecto:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>Validar el token de identificador

Simplemente obtener un token de identificador no es suficiente para autenticar al usuario; también debe validar la firma del token y comprobar las notificaciones en el token en función de los requisitos de la aplicación. El punto de conexión del token público proporciona la clave pública del portal, que se puede usar para validar la firma del token proporcionado por el portal. La dirección URL del punto de conexión del token público es: `<portal_url>/_services/auth/publickey`.

## <a name="turn-implicit-grant-flow-on-or-off"></a>Activar o desactivar el flujo de concesión implícita

De forma predeterminada, el flujo de concesión implícita está habilitado. Si desea desactivar el flujo de concesión implícita, establezca el valor de la configuración del sitio **Connector/ImplicitGrantFlowEnabled** en **false**.

Si esta configuración del sitio no está disponible en el portal, debe [crear una nueva configuración del sitio](configure/configure-site-settings.md#manage-portal-site-settings) con el valor adecuado.

## <a name="configure-token-validity"></a>Configuración de la validez del token

De forma predeterminada, el token es válido durante 15 minutos. Si desea cambiar la validez del token, establezca el valor de la configuración del sitio **ImplicitGrantFlow/TokenExpirationTime** en el valor requerido. El valor debe especificarse en segundos. El valor máximo puede ser 1 hora y el valor mínimo debe ser de 1 minuto. Si se especifica un valor incorrecto (por ejemplo, caracteres alfanuméricos), se usa el valor predeterminado de 15 minutos. Si especifica un valor mayor que el valor máximo o menor que el valor mínimo, se usan los valores máximo y mínimo, respectivamente, de forma predeterminada.

Por ejemplo, para establecer la validez del token en 30 minutos, establezca el valor de la configuración del sitio **ImplicitGrantFlow/TokenExpirationTime** en **1800**. Para establecer la validez del token en 1 hora, establezca el valor de la configuración del sitio **ImplicitGrantFlow/TokenExpirationTime** en **3600**.

## <a name="register-client-id-for-implicit-grant-flow"></a>Registrar el identificador de cliente para el flujo de concesión implícito

Debe registrar el identificador de cliente con el portal para el que se permite este flujo. Para registrar un identificador de cliente, debe crear la siguiente configuración del sitio:

|Configuración del sitio|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|Los valores de ID. de cliente válidos que se permiten para este portal. Los valores deben estar separados por un punto y coma y pueden contener caracteres alfanuméricos y guiones. La longitud máxima es de 36 caracteres.|
|ImplicitGrantFlow/{ClientId}/RedirectUri|Los URI de redirección válidos que se permiten para un identificador de cliente específico. Los valores deben estar separados por un punto y coma. La dirección URL proporcionada debe ser una página web válida del portal.|
|||

## <a name="sample-code"></a>Código de ejemplo

Puede usar el siguiente código de ejemplo para empezar a usar la concesión implícita OAuth 2,0 con las API de portales de PowerApps.

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>Uso del token de OAuth del portal con una API web externa

Este ejemplo es un proyecto basado en ASP.NET y se usa para validar el token de identificador emitido por los portales de PowerApps. El ejemplo completo se puede encontrar aquí: [usar el token de OAuth del portal con una API web externa](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample).

### <a name="authorize-endpoint-sample"></a>Ejemplo de autorización de punto de conexión

Este ejemplo muestra cómo autorizar el punto de conexión devuelve el token de identificador como un fragmento en la dirección URL redirigida. También se incluye la validación de estado admitida en la concesión implícita. El ejemplo se puede encontrar aquí: [Authorize Endpoint Sample](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js).

### <a name="token-endpoint-sample"></a>Ejemplo de punto de conexión de token

En este ejemplo se muestra cómo se puede usar la función getAuthenticationToken para capturar un token de identificador mediante el punto de conexión de token en los portales de PowerApps. El ejemplo se puede encontrar aquí: [token Endpoint Sample](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js).
