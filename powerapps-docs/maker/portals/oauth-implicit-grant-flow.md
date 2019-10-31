---
title: Use flujo de concesión implícito de OAuth 2.0 en el portal | MicrosoftDocs
description: Aprenda a realizar llamadas del lado del cliente a API externas y protegerlas mediante flujo de concesión implícito de OAuth en los portales de Dynamics 365.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>Use flujo de concesión implícito de OAuth 2.0 en el portal 

Esta característica permite que un cliente realice llamadas del lado del cliente a API externas y las proteja mediante flujo de concesión implícito de OAuth. Proporciona un extremo para obtener tokens de acceso seguro que contendrán información de identidad de usuario para uso de API externas para autorización después de flujo de concesión implícito de OAuth 2.0. La información de identidad de un usuario que ha iniciado sesión se pasa de forma segura a llamadas AJAX externas. Esto no solo ayudará a los desarrolladores a pasar contexto de autenticación sino también ayudará a los usuarios a proteger sus API mediante este mecanismo.

El flujo de concesión implícito de OAuth 2.0 admite extremos a los que un cliente puede llamar para obtener un token de Id. Dos extremos se usan con este fin: [autorizar](#authorize-endpoint-details) y [token](#token-endpoint-details).

## <a name="authorize-endpoint-details"></a>Autorizar detalles del extremo 

La dirección URL para el extremo autorizar es: `<portal_url>/_services/auth/authorize`. El extremo autorizar admite los siguientes parámetros:

| Parámetro   | ¿Obligatorio? | Descripción                             |
|---------------|-----------|---------------------------------------|
| client_id      | Sí       | Una cadena que se pasa al realizar una llamada al extremo autorizar. Debe asegurarse de el identificador del cliente está [registrado en el portal](#register-client-id-for-implicit-grant-flow). De lo contrario, se muestra un error. El identificador de cliente se agrega en notificaciones en el token `aud` además del `appid` parámetro y lo pueden usar clientes para validar que el token devuelto es para su aplicación.<br>La longitud máxima es de 36 caracteres. Solo se admiten caracteres alfanuméricos y guiones. |
| redirect_uri      | Sí       | Dirección URL del portal donde se pueden enviar y recibir respuestas de autenticación. Debe estar registrado para el `client_id` específico usado en la llamada y debe ser exactamente el mismo valor que el registrado.            |
| estado       | No        | Un valor incluido en la solicitud que también se devuelve en la respuesta del token. Puede ser una cadena de cualquier contenido que desee usar. Generalmente, se usa un valor único generado de forma aleatoria para evitar ataques de falsificación de solicitudes entre sitios.<br>La longitud máxima es de 20 caracteres.              |
| nonce   | No        | Un valor de cadena enviado por el cliente que se incluye en el token de identificador resultante como notificación. El cliente puede entonces comprobar este valor para mitigar los ataques de repetición de token. La longitud máxima es de 20 caracteres.      |
| response_type         | No        | Este parámetro sólo admite `token` como valor. Esto permite a la aplicación inmediatamente recibir un token de acceso del extremo autorizar, sin realizar una segunda solicitud al extremo autorizar.                               |
|||

### <a name="successful-response"></a>Respuesta correcta

El extremo autorizar devuelve los siguientes valores en la dirección URL de respuesta como fragmento:

- **token**: El token se devuelve como token web JSON (JWT) firmado digitalmente por la clave privada del portal.
- **state**: Si un parámetro de estado se incluye en la solicitud, el mismo valor debe aparecer en la respuesta. La aplicación debe comprobar que los valores de estado de la solicitud y la respuesta sean idénticos.
- **expires_in**: El periodo de tiempo que el token de acceso es válido (en segundos).

Por ejemplo, una respuesta correcta tiene este aspecto:

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>Respuesta de error

El error en el extremo autorizar se devuelve como documento de JSON con los siguientes valores:

- **Id. de error**: Identificador único del error.
- **Mensaje de error**: Un mensaje de error específico que puede ayudarle a identificar la causa raíz de un error de autenticación.
- **Id. de correlación**: Un GUID que se usa para fines de depuración. Si ha habilitado el registro de diagnóstico, el id. de correlación estaría presente en registros de errores del servidor.
- **Marca de tiempo**: Fecha y hora en que se generó el error.

El mensaje de error se muestra en el idioma predeterminado del usuario que ha iniciado sesión. Si el usuario no ha iniciado sesión, la página de inicio de sesión se muestra para que el usuario inicie sesión. Por ejemplo, una respuesta de error tiene este aspecto:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>Detalles del extremo de token

También puede ir un token realizando una solicitud al extremo `/token`. Es diferente del extremo de autorización en que este se encarga de la lógica del token en página aparte (redirect_uri), mientras que el extremo token controla la lógica de token en la misma página. La dirección URL para el extremo token es: `<portal_url>/_services/auth/token`. El extremo token admite los siguientes parámetros:

| Parámetro   | ¿Obligatorio? | Descripción                             |
|---------------|-----------|---------------------------------------|
| client_id      | No       | Una cadena que se pasa al realizar una llamada al extremo autorizar. Debe asegurarse de el identificador del cliente está [registrado en el portal](#register-client-id-for-implicit-grant-flow). De lo contrario, se muestra un error. El identificador de cliente se agrega en notificaciones en el token `aud` además del `appid` parámetro y lo pueden usar clientes para validar que el token devuelto es para su aplicación.<br>La longitud máxima es de 36 caracteres. Solo se admiten caracteres alfanuméricos y guiones. |
| redirect_uri      | No       | Dirección URL del portal donde se pueden enviar y recibir respuestas de autenticación. Debe estar registrado para el `client_id` específico usado en la llamada y debe ser exactamente el mismo valor que el registrado.            |
| estado       | No        | Un valor incluido en la solicitud que también se devuelve en la respuesta del token. Puede ser una cadena de cualquier contenido que desee usar. Generalmente, se usa un valor único generado de forma aleatoria para evitar ataques de falsificación de solicitudes entre sitios.<br>La longitud máxima es de 20 caracteres.              |
| nonce   | No        | Un valor de cadena enviado por el cliente que se incluye en el token de identificador resultante como notificación. El cliente puede entonces comprobar este valor para mitigar los ataques de repetición de token. La longitud máxima es de 20 caracteres.      |
| response_type         | No        | Este parámetro sólo admite `token` como valor. Esto permite a la aplicación inmediatamente recibir un token de acceso del extremo autorizar, sin realizar una segunda solicitud al extremo autorizar.                               |
|||

> [!NOTE]
> Aunque los parámetros `client_id`, `redirect_uri`, `state` y `nonce` son opcionales, se recomienda usarlos para asegurarse de que las integraciones son seguras.

### <a name="successful-response"></a>Respuesta correcta

El extremo token devuelve state expires_in como encabezados de respuesta, y token en el cuerpo del formulario.

### <a name="error-response"></a>Respuesta de error

El error en el extremo token se devuelve como documento de JSON con los siguientes valores:

- **Id. de error**: Identificador único del error.
- **Mensaje de error**: Un mensaje de error específico que puede ayudarle a identificar la causa raíz de un error de autenticación.
- **Id. de correlación**: Un GUID que se usa para fines de depuración. Si ha habilitado el registro de diagnóstico, el id. de correlación estaría presente en registros de errores del servidor.
- **Marca de tiempo**: Fecha y hora en que se generó el error.

El mensaje de error se muestra en el idioma predeterminado del usuario que ha iniciado sesión. Si el usuario no ha iniciado sesión, una página de inicio de sesión se muestra para que el usuario inicie sesión. Por ejemplo, una respuesta de error tiene este aspecto:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>Validar token de identificador

No basta con obtener un token de identificador para autenticar al usuario; también debe validar la firma del token y comprobar las notificaciones en el token según los requisitos de la aplicación. El extremo del token pública proporciona la clave pública del portal, que puede usarse para validar la firma del token proporcionado por el portal. La dirección URL para el extremo token público es: `<portal_url>/_services/auth/publickey`.

## <a name="turn-implicit-grant-flow-on-or-off"></a>Activar o desactivar flujo de concesión implícito

De forma predeterminada, flujo de concesión implícito está habilitado. Si desea desactivar el flujo de concesión implícito, establezca el valor del ajuste **Connector/ImplicitGrantFlowEnabled** en **Falso**.

Si la configuración del sitio no está disponible en el portal, debe [crear una nueva configuración del sitio](configure-site-settings.md#manage-portal-site-settings) con el valor apropiado.

## <a name="configure-token-validity"></a>Configure validez de token

De forma predeterminada, el token es válido durante 15 minutos. Si desea cambiar la validez del token, establezca el valor del sitio **ImplicitGrantFlow/TokenExpirationTime** con el valor necesario. El valor debe especificarse en segundos. El valor máximo puede ser 1 hora, y el valor mínimo debe ser 1 minuto. Si se especifica un valor incorrecto (por ejemplo, caracteres alfanuméricos), se usa el valor predeterminado de 15 minutos. Si especifica un valor mayor que el valor máximo o inferior al valor mínimo, se usarán los valores máximo y mínimo respectivamente de forma predeterminada.

Por ejemplo, para establecer la validez del token a 30 minutos, establezca el valor del sitio **ImplicitGrantFlow/TokenExpirationTime** en **1800**. Para establecer la validez del token a 1 hora, establezca el valor del sitio **ImplicitGrantFlow/TokenExpirationTime** en **3600**.

## <a name="register-client-id-for-implicit-grant-flow"></a>Registrar el identificador del cliente para flujo de concesión implícito

Debe registrar el identificador de cliente con el portal para el que está permitido este flujo. Para registrar un identificador del cliente, debe crear los siguientes valores del sitio:

|Configuración del sitio|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|Los valores de identificador de cliente válidos que se permiten para este portal. Los valores deben ir separados por punto y coma y pueden contener caracteres alfanuméricos y guiones. La longitud máxima es de 36 caracteres.|
|ImplicitGrantFlow/{ClientId}/RedirectUri|La redirección válida URI que se permite para un identificador de cliente específico. Los valores deben separar por punto y coma. La dirección URL proporcionada debe ser de una página web válida del portal.|
|||

## <a name="sample-code"></a>Código de ejemplo

Puede usar el código siguiente para empezar a usar la concesión implícita de OAuth 2.0 con Dynamics 365 para las API de Portales de Dynamics 365.

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>Use el token de OAuth del portal con una API web externa

Este ejemplo es un proyecto basado en ASP.NET y se usa para validar el token de id. emitido por Portales de Dynamics 365. El código de ejemplo completo se puede encontrar aquí: [Use el token de OAuth del portal con una API web externa](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample).

### <a name="authorize-endpoint-sample"></a>Ejemplo de Autorizar el extremo

En este ejemplo se muestra cómo autorizar el extremo devuelve el token de id. como fragmento en la dirección URL redirigida. También se explica la validación de estado compatible en la concesión implícita. El ejemplo se puede encontrar aquí: [Ejemplo de Autorizar el extremo](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js).

### <a name="token-endpoint-sample"></a>Ejemplo de extremo de token

Este ejemplo le muestra cómo puede usar la función getAuthenticationToken para capturar un token de id. mediante el extremo de token en Portales de Dynamics 365. El ejemplo se puede encontrar aquí: [Ejemplo de extremo de token](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js).
