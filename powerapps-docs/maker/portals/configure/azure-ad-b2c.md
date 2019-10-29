---
title: Configuración del proveedor de Azure AD B2C para portales | MicrosoftDocs
description: Instrucciones para habilitar la configuración del proveedor de Azure AD B2C para los portales.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: aead447bbab7f6e5758cdea0a9c6be5c0e8f41e2
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978402"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>Configuración del proveedor de Azure AD B2C para portales

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) alimenta los servicios de Office 365 y Dynamics 365 para la autenticación interna o de empleado. [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C es una extensión de ese modelo de autenticación que permite inicios de sesión de clientes externos a través de credenciales locales y Federación con varios proveedores de identidades sociales comunes.

Un propietario del portal puede configurar el portal para que acepte [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C como proveedor de identidades. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C admite Open ID Connect para la Federación.

En el proceso de configuración de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C como proveedor de identidades para el portal, se generan varios valores que usará más adelante mientras configura el portal. Puede anotar estos valores en la tabla siguiente. Mientras configura el portal, reemplace el nombre de la variable por los valores que se indican aquí.

| Nombre de variable     | Value | Descripción                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| Nombre de la aplicación  |       | Nombre de la aplicación que representa el portal como usuario de confianza |
| IDENTIFICADOR de la aplicación    |       | IDENTIFICADOR de la aplicación asociado a la aplicación creada en Azure Active Directory B2C.  |
| Directiva: Inicio de sesión: URL |       | La dirección URL del emisor (ISS) definida en el extremo de metadatos.                |
| Nombre de Federación   |       | Un nombre único para identificar el tipo de proveedor de Federación como ' B2C '. Se usará en los nombres de configuración del sitio para los valores de configuración de grupo para este proveedor específico.                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Uso de Azure AD B2C como proveedor de identidades para el portal

1. Inicie sesión en su [Azure portal](https://portal.azure.com/).
2. [Cree un inquilino de Azure ad B2C](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started).
3. Seleccione **[!include[Azure](../../../includes/pn-azure-shortest.md)] ad B2C** en la barra de navegación de la izquierda.
4. [Cree una aplicación de Azure](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application).

   > [!Note]
   > Debe elegir **sí** en el campo **permitir flujo implícito** y especificar la dirección URL del portal en el campo **URL de respuesta** . El valor del campo **dirección URL de respuesta** debe tener el formato [dominio del portal]/signin-[nombre-Federación]. Por ejemplo, `https://contosocommunity.microsoftcrmportals.com/signin-B2C`.

5. Copie el nombre de la aplicación y escríbalo como el valor de nombre de la aplicación en la tabla anterior.
6. Copie el identificador de la aplicación y escríbalo como el valor de Application-ID en la tabla anterior.
7. [Cree una directiva de registro o de inicio de sesión](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy).
8. Seleccione la Directiva y, a continuación, seleccione **Editar**.
9. Seleccione **token, sesión & configuración de SSO**.
10. En la lista de **notificaciones del emisor (ISS)** , seleccione la dirección URL que tiene **/TFP** en su ruta de acceso.
11. Guarde la Directiva.
12. Seleccione la dirección URL en el **punto de conexión de metadatos para este campo de directiva** .
13. Copie el valor del campo issuer y escríbalo como el valor de Policy-Sign-URL en la tabla anterior. 

## <a name="portal-configuration"></a>Configuración del portal

Después de crear y configurar el inquilino de B2C en [!include[Azure](../../../includes/pn-azure-shortest.md)], debe configurar el portal para que se federe con [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C mediante el protocolo Open ID Connect. Debe crear un nombre único para la Federación a [!include[Azure](../../../includes/pn-azure-shortest.md)]&mdash;de AD B2C, por ejemplo, B2C&mdash;y almacenarlo como el valor de la variable de *nombre de Federación* en la tabla anterior.

### <a name="configure-your-portal"></a>Configuración del portal
1. Abra la aplicación administración del portal.
2. Vaya a **portales** > **sitios web**.
3. Seleccione el registro del sitio web para el que se debe habilitar [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C.
4. Vaya a **configuración del sitio**.
5. Cree la siguiente configuración del sitio:
   -   **Nombre**: autenticación/OpenIdConnect/[Federation-Name]/Authority

       **Valor**: [Policy-Signing-URL]
   -   **Nombre**: autenticación/OpenIdConnect/[Federation-Name]/ClientID

       **Valor**: [Application-ID]
   -   **Nombre**: autenticación/OpenIdConnect/[Federation-Name]/RedirectUri

       **Valor**: [dominio del portal]/signin-[nombre-Federación]

       Por ejemplo, `https://mysite.com/signin-b2c` 
6. Para admitir el cierre de sesión federado, cree la siguiente configuración del sitio:
   - **Nombre**: autenticación/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled

     **Valor**: true
7. Para codificar el portal en un solo proveedor de identidades, cree la siguiente configuración del sitio:
   - **Nombre**: autenticación/registro/LoginButtonAuthenticationType

     **Valor**: [Policy-Signing-URL]

8. Para admitir el restablecimiento de contraseña, cree la configuración de sitio necesaria que se describe [aquí](#password-reset).
9. Para admitir la asignación de notificaciones, cree la configuración de sitio necesaria que se describe [aquí](#claims-mapping).

Para obtener una lista completa de la configuración de sitio relacionada, consulte [aquí](#related-site-settings).

### <a name="password-reset"></a>Restablecimiento de contraseña

Se requiere la siguiente configuración del sitio si desea admitir el restablecimiento de contraseña con [!include[Azure](../../../includes/pn-azure-shortest.md)] cuentas locales de AD B2C:

| Configuración del sitio                                                        | Descripción                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[Federation-Name/PasswordResetPolicyId | IDENTIFICADOR de la Directiva de restablecimiento de contraseña.                                                                                     |
| Authentication/OpenIdConnect/[Federation-Name]/ValidIssuers         | Una lista delimitada por comas de emisores que incluye [Policy-Sign-URL] y el emisor de la Directiva de restablecimiento de contraseña. |
|Authentication/OpenIdConnect/[Federation-Name]/DefaultPolicyId | IDENTIFICADOR de la Directiva de inicio de sesión o de registro.|
|||

### <a name="related-site-settings"></a>Configuración del sitio relacionado

Puede crear o configurar los siguientes valores del sitio en portales para admitir [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C como proveedor de identidades:


| Configuración del sitio                                                         | Descripción                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autenticación/registro/ProfileRedirectEnabled                   | Especifica si el portal puede redirigir a los usuarios a la página de perfil después del inicio de sesión correcto. De forma predeterminada, se establece en true.                                                                                                                                            |
| Autenticación/registro/EmailConfirmationEnabled                 | Especifica si es necesaria la validación del correo electrónico. De forma predeterminada, se establece en true.                                                                                     |
| Autenticación/registro/LocalLoginEnabled                        | Especifica si es necesario el inicio de sesión local. De forma predeterminada, se establece en true.                                                                        |
| Autenticación/registro/ExternalLoginEnabled                     | Habilita o deshabilita la autenticación externa.       |
| Autenticación/registro/AzureADLoginEnabled                      | Habilita o deshabilita [!include[Azure](../../../includes/pn-azure-shortest.md)] AD como proveedor de identidades externo. De forma predeterminada, se establece en true.                                                                                                                                                                      |
| Authentication/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled | Habilita o deshabilita el cierre de sesión federado. Cuando se establece en true, los usuarios se redirigen a la experiencia del usuario de cierre de sesión federado cuando cierren sesión en el portal. Cuando se establece en false, los usuarios solo se cerran desde el portal. De forma predeterminada, se establece en false.               |
| Autenticación/LoginTrackingEnabled                                  | Habilita o deshabilita el seguimiento del último inicio de sesión del usuario. Cuando se establece en true, la fecha y la hora se muestran en el último campo de **Inicio de sesión correcto** en el registro de contacto. De forma predeterminada, se establece en false.                                                            |
| Authentication/OpenIdConnect/[Federation-Name]/RegistrationEnabled   | Habilita o deshabilita el requisito de registro para el proveedor de identidades existente. Cuando se establece en true, el registro está habilitado para el proveedor existente solo si la configuración del sitio autenticación/registro/habilitado también está establecida en true. De forma predeterminada, se establece en true. |
|Authentication/OpenIdConnect/[Federation-Name]/PostLogoutRedirectUri |Especifica la dirección URL en el portal a la que redirigirse después de que un usuario cierra la sesión. |
| | |

### <a name="related-content-snippet"></a>Fragmento de contenido relacionado

Si el registro está deshabilitado para un usuario después de que el usuario haya canjeado una invitación, muestre un mensaje mediante el siguiente fragmento de código:

**Nombre**: cuenta/registro/RegistrationDisabledMessage

**Valor**: se ha deshabilitado el registro.

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>Personalización de la interfaz de usuario de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C admite la personalización de la interfaz de usuario. Puede personalizar la experiencia del usuario para escenarios de registro e inicio de sesión.

### <a name="step-1-create-a-web-template"></a>Paso 1: crear una plantilla Web
Cree una plantilla Web con los siguientes valores:

**Nombre**: [!include[Azure](../../../includes/pn-azure-shortest.md)] página personalizada de ad B2C

**Origen**: Use el código HTML de ejemplo de la plantilla Web siguiente.

```html
<!DOCTYPE html>
<html lang=en-US>
  <head>
    <meta charset=utf-8>
    <meta name=viewport content=width=device-width, initial-scale=1.0>
    <meta http-equiv=X-UA-Compatible content=IE=edge>
    <title>
      {{ page.title | h }}
    </title>
                        <link href={{ request.url | base }}/bootstrap.min.css rel=stylesheet>
                        <link href={{ request.url | base }}/theme.css rel=stylesheet>
                        <style>
                          .page-heading {
            padding-top: 20px;
      }
      .page-copy {
            margin-bottom: 40px;
      }
      .highlightError {
        border: 1px solid #cb2027!important;
        background-color: #fce8e8!important;
      }
      .attrEntry .error.itemLevel {
        display: none;
        color: #cb2027;
        font-size: .9em;
      }
      .error {
        color: #cb2027;
      }
      .entry {
        padding-top: 8px;
        padding-bottom: 0!important;
      }
      .entry-item {
        margin-bottom: 20px;
      }
      .intro {
        display: inline;
        margin-bottom: 5px;
      }
      .pageLevel {
          width: 293px;
          text-align: center;
          margin-top: 5px;
          padding: 5px;
          font-size: 1.1em;
          height: auto;
      }
      #panel, .pageLevel, .panel li, label {
          display: block;
      }
      #forgotPassword {
          font-size: .75em;
          padding-left: 5px;
      }
      #createAccount {
          margin-left: 5px;
      }
      .working {
          display: none;
          background: url(data:image/gif;base64,R0lGODlhbgAKAPMAALy6vNze3PTy9MTCxOTm5Pz6/Ly+vNTS1Pz+/�N0Jp6BUJ9EBIISAQAh+QQJCQAKACxRAAIABgAGAAAEE1ClYU4RIIMTdCaegVCfRASCEgEAOw==) no-repeat;
          height: 10px;
          width: auto;
      }
      .divider {
        margin-top: 20px;
        margin-bottom: 10px;
      }
      .divider h2 {
        display: table;
        white-space: nowrap;
        font-size: 1em;
        font-weight: 700;
      }
      .buttons {
        margin-top: 10px;
      }
      button {
            width:auto;
            min-width:50px;
            height:32px;
            margin-top:2px;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%;
            padding:0 2px
      }

      button:hover {
            background:#0F3E83;
            border:1px solid #3079ed;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .password-label label {
        display: inline-block;
        vertical-align: baseline;
      }
      img {
            border:0
      }
      .divider {
            margin-top:20px;
            margin-bottom:10px
      }
      .divider h2 {
            display:table;
            white-space:nowrap;
            font-size:1em;
            font-weight:700
      }
      .divider h2:after,.divider h2:before {
            border-top:1px solid #B8B8B8;
            content:'';
            display:table-cell;
            position:relative;
            top:.7em;
            width:50%
      }
      .divider h2:before {
            right:1.8%
      }
      .divider h2:after {
            left:1.8%
      }
      .verificationErrorText {
            color:#D63301
      }
      .options div {
            display:inline-block;
            vertical-align:top;
            margin-top:7px
      }
      .accountButton,.accountButton:hover {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAh1BMVEX///9QUFBOTk5LS0tERERCQkI/Pz9ISEg6OjpGRkZNTU08PDyAgID09PSlpaWWlpZxcXFgYGBZWVlUVFT6+vrx8fHt7e3s7Ozo6Oji4uLJycnGxsa4uLiqqqqgoKCNjY2JiYmGhoZra2tmZmb7+/vu7u7d3d3U1NTNzc2+vr67u7usrKx7e3vprNQnAAAA8klEQVQ4y63Q127DMAxAUZpDwyMeSdqsNqu7/f/va6zahgGJKAr0vgk6DyQh+6V/BiTOOeNRA9zuAWBdM6WBlPDTvaUUoAuMrT0mgNvA1IJjQB3MKjACvp6DK0WAH+agtH8H9jQHLUUgz7Uhx8xOXzNESxirLCYA2mw8tacI5FyIYXq8A9ge2Qs6oTnw2e2ruho2rjBcXJ4ADh3jBOQLQnVhRFx2gNDZ4ACogbHXj/ft9Dj5AcgbJFu5AThQWuYBIGmgtAFQo4EFB+CPGthJAPypgY3BHsheA5UNwLyAvsYNoDyroKUe4EoFTQ/yDtTONvsGUJ8KTUYyH+UAAAAASUVORK5CYII=);
            background-repeat:no-repeat
      }
      .accountButton {
            border:1px solid #FFF;
            color:#FFF;
            margin-left:0;
            margin-right:2px;
            transition:background-color 1s ease 0s;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            text-align:center;
            word-wrap:break-word;
            height:34px;
            width:158px;
            padding-left:30px;
            background-color:#505050;
      }
      .accountButton:hover {
            background-color:#B9B9B9;
            border:1px solid #FFF;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .accountButton:focus {
            outline:gold solid 1px
      }
      #MicrosoftAccountExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAPFBMVEU1pe/////t+v4uoe5btvNixPVVwfUsoe9tyfXU7/y95vu24vrd9f5NtfLH6/ys3/o/sPE6qfD2/f+f2vnAysuQAAAAaElEQVQ4y93SORKAIAwFUEGCsoT1/nd1JkkDFhY24qt+8VMkk20lu6DAaVBOBsVKsuO8aYo08IqlYyxoRTQExfyKheRIgu5Yl4KoVhSUgNOhoiYRsmb5g2u+LtzXDNOhjKgoAZ9/8k8uZWsGqcIav5wAAAAASUVORK5CYII=);
            background-color:#33A7F2
      }
      #MicrosoftAccountExchange:hover {
            background-color:#ADDBF9
      }
      #GoogleExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEXcTkH////cTD/bSj3ZQDLYOyzaRDbeV0vbSDrZPS/66Obyv7rsnpfpkorjcWfgZlvXOCr++Pj5393haFz88/L88fD67Or319T1zsv1zsrxuLPuqaLuqKLoi4LlfXTgYlbWMyTWMiPwtrHwta/fXVH/sCIIAAAAmElEQVQ4y+2RyQ7DIBBDMcwAIXvovqXb/39jRaX0AEmr5px3tSV7PGLhX6TVRFpN61l9zPNS6kn9gDcXO67zDnCnO2BCiNIyMtgKKJgyY2zQ68JEDtqju0nFTcOsxPUMw1GDDUqt+tY51/YNVlhvacTgEfCDIY0Q/lkBSg4RaUmmDo4/JdMzHy1Q2ejMeCj6PrXQP5+1MI8X0Y4HL4c826EAAAAASUVORK5CYII=);
            background-color:#DC4E41
      }
      #GoogleExchange:hover {
            background-color:#F1B8B3
      }
      #TwitterExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAdVBMVEVgqd3///9Ypdtdp9xaptxSotpQodlNn9lWo9pUo9rX6Pa+2vGTw+iLvuZlqt79/P7K4PO62O+y0+6hyutysuD2+fzi7vne6/fT5PTE3fKs0O2lzeuZx+l7tuJqrd71+Pzz9vzn8PnQ4/SCueSAueNsrt9InNh7sQwBAAAAwklEQVQ4y92PRw6EMAwAXeIkdBbY3uv/n7gSAoLDD5hbPCPZgZVihEgYgNSUpmfS7bfbtHS2nReyL2Qoc+yp8ZRAwCEWjgGAPQ7sssKoAGsWBrrgyMZCwD77Uel+59E3Tt14xZ7qlY7BRf1CDgeMKMw8sBXGlKxWtLGvHCgkQ80m0YHpjjq4sQ74pn1mISLJVSAMiwJO98l/TWSNF1eGKzqKfZ7Vj0mnHHwodpP+WIYlZP373DTtVWxYr2FD3pOBdfIHhOAHYHQI9VgAAAAASUVORK5CYII=);
            background-color:#60A9DD
      }
      #TwitterExchange:hover {
            background-color:#BFDCF1
      }
      #FacebookExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAaVBMVEU7W5z///85Wps3WJsiRo8xU5fw8vYyUpY0VZiAj70pS5OBkb0vUpb7+fwsTpTR1ud6irllerBPaqX09fnx8vfs7fSQoMZxg7VsgLNGY6FCX58ZP4v++/7r7vTZ3OupstGIlsFWcalDYaCK3qwDAAAAnklEQVQ4y+XQyw7CIBAFUBgc5VUoWGtb3/7/RyoYkyZAiSsXvdt7kstA/hRg/B0GpZ6byQ3Dw0NBaH+lMYRle3T0kwayACRdBrr/gnN+QtpQWv8cR4DswiUAjozlz4RdF8AmlnmwjaDQImoZwQkRedoToUS7D+ColGoTwQidx8oEQDMHN1MBva5MOL70SCHuE1TOhOpHrRt0FWAOP4IX8PsG2qEOR30AAAAASUVORK5CYII=);
            background-color:#3B5B9C
      }
      #FacebookExchange:hover {
            background-color:#B0BDD7
      }
      #LinkedInExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEUAe7b///8AdrMklscAc7EAeLUAcbB5ttifzeMqmckAdLIAaqz7+/6PxeAShr0CgLkAba4nmMctksTv9Puw1eij0OWGvNtfrNJNo80YjMAeib/D4vGt3Oy82+yfzOOCvtyJvdx3tddirtI/ncoxmMj9KsrQAAAAw0lEQVQ4y9WSVw7DIAxAG8CkjJDVzO5x/zMWk0RNJaB/kfo+sGUeCMvstgI4J7F9aS5NxSLnTWLpZVDgexTqIiycUNBhgTxRyCKPYJ3dl7sITCkO+FyLXaWU310DscASOesf3ahWChGJ5cb4ASO5Joiu2EegWEmZa1c3yUwOHmHNuQgJup4CgF8YlKpcMhKvkNmb1REz6hdetsyziIBldv8lpH8ouGm28zQFCu2SOSAXlJYGYCgpFThEMFPm/zCryja8Acy7CRfMrcKPAAAAAElFTkSuQmCC);
            background-color:#0077B5
      }
      #LinkedInExchange:hover {
            background-color:#99CAE1
      }
      #AmazonExchange {
            background-image:url(https://images-na.ssl-images-amazon.com/images/G/01/lwa/btnLWA_gold_156x32.png);
            background-color:#FFF;
            color:transparent
      }

      #next {
            -moz-user-select:none;
            user-select:none;
            cursor:pointer;
            width:auto;
            padding-left:10px;
            padding-right:10px;
            height:30.5px;
            -moz-border-radius:0;
           -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%
      }
      #next:hover {
            background:#0F3E83;
            border:1px solid #FFF;
            box-shadow:0 0 0
      }
      #next:hover,.accountButton:hover {
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0;
      }
                        </style>
  </head>
  <body>
    <div class=navbar navbar-inverse navbar-static-top role=navigation>
      <div class=container>
        <div class=navbar-header>
          <div class=visible-xs-block>
            {{ snippets[Mobile Header] }}
          </div>
          <div class=visible-sm-block visible-md-block visible-lg-block navbar-brand>
            {{ snippets[Navbar Left] }}
          </div>
        </div>
      </div>
    </div>
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          <li>
            <a href={{ request.url | base }} title=Home>Home</a>
          </li>
          <li class=active>{{ page.title | h}}</li>
        </ul>
        {% include 'Page Header' %}
     </div>
     <div class=row>
      <div class=col-md-12>
        {% include 'Page Copy' %}
        <div id=api></div>
      </div>
     </div>
    </div>
    <footer role=contentinfo>
      <div class=footer-top hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-6 col-sm-12 col-xs-12 text-left>
               {{ snippets[About Footer] }}
            </div>
            <div class=col-md-6 col-sm-12 col-xs-12 text-right>
              <ul class=list-social-links>
                <li><a href=#><span class=sprite sprite-facebook_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-twitter_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-email_icon></span></a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class=footer-bottom hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-4 col-sm-12 col-xs-12 text-left>
               {{ snippets[Footer] | liquid }}
            </div>
            <div class=col-md-8 col-sm-12 col-xs-12 text-left >
            </div>   
          </div>
        </div>
      </div>
    </footer>
  </body>
</html>
```
### <a name="step-2-create-a-page-template"></a>Paso 2: creación de una plantilla de página

Cree la siguiente plantilla de página:
- **Nombre**: [!include[Azure](../../../includes/pn-azure-shortest.md)] página personalizada de ad B2C
- **Tipo**: plantilla Web
- **Plantilla Web**: [!include[Azure](../../../includes/pn-azure-shortest.md)] página personalizada de ad B2C
- **Usar encabezado y pie de página del sitio web**: Desactive esta casilla

### <a name="step-3-create-a-webpage"></a>Paso 3: crear una página web

Cree la siguiente página web:
- **Nombre**: Inicio de sesión
- **Elemento primario** Página: Inicio
- **Dirección URL parcial**: Azure-ad-B2C-inicio de sesión
- **Plantilla de página**: [!include[Azure](../../../includes/pn-azure-shortest.md)] página personalizada de ad B2C
- **Estado de publicación**: publicado

### <a name="step-4-create-site-settings"></a>Paso 4: crear la configuración del sitio

La configuración del sitio es necesaria para configurar el uso compartido de recursos entre orígenes (CORS) para permitir que [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C solicite la página personalizada e inserte la interfaz de usuario de inicio de sesión o de registro. Cree la siguiente configuración del sitio.

| Nombre                              | Value                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control-Allow-Methods | GET, OPCIONES                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

Para obtener una lista completa de otras opciones de CORS, consulte [compatibilidad del protocolo CORS](../add-web-resource.md#cors-protocol-support).

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>Paso 5: configuración de [!include[Azure](../../../includes/pn-azure-shortest.md)]

1. Inicie sesión en su [!include[Azure portal](../../../includes/pn-azure-portal.md)].
2. Vaya a la hoja de **Administración de inquilinos de ad B2C[!include[Azure](../../../includes/pn-azure-shortest.md)]** .
3. Vaya a **configuración** > **directivas de registro o de inicio de sesión**. Se muestra una lista de directivas disponibles.
4. Seleccione la Directiva que desea editar.
5. Seleccione **Editar**.
6. Seleccione **Editar directiva** > **Personalización** de la interfaz de usuario de la página > la página de inicio de sesión **o Registro Unificado**
7. Establezca **usar página personalizada** en **sí**.
8. Establezca **URI de página personalizada** en la dirección URL de la Página Web de la página personalizada de [!include[Azure](../../../includes/pn-azure-shortest.md)] ad B2C creada en el paso 3 de este procedimiento. Por ejemplo, `https://mydomain.com/azure-ad-b2c-sign-in`.
9. Seleccione **Aceptar**.

## <a name="claims-mapping"></a>Asignación de notificaciones

Cuando los usuarios inician sesión, ya sea por primera vez o posteriormente, el proveedor de identidades federado proporciona notificaciones basadas en su base de datos con respecto al inicio de sesión de los usuarios. Estas notificaciones se pueden configurar en el proveedor de identidades.

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] de notificaciones de correo electrónico de AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C envía la notificaciones de correo electrónico como una colección. El portal acepta el primer correo electrónico proporcionado en la colección como dirección de correo electrónico principal del contacto.

### <a name="claims-to-support-sign-up-scenarios"></a>Notificaciones para admitir escenarios de registro

Cuando se aprovisiona un nuevo cliente que no existe en Common Data Service, se pueden usar las notificaciones entrantes para inicializar el nuevo registro de contacto que creará el portal. Las notificaciones comunes pueden incluir el nombre y el apellido, la dirección de correo electrónico y el número de teléfono, pero se pueden configurar. Se requiere la siguiente configuración del sitio:

**Nombre**: autenticación/OpenIdConnect/[Federation-Name]/RegistrationClaimsMapping

**Descripción**: lista de pares de nombre lógico o de notificaciones que se usarán para asignar valores de notificaciones a los atributos del registro de contacto creado durante el registro.

**Formato**: atributo1 = claim1, attribute2 = claim2, attribute3 = claim3

Por ejemplo: firstname =<http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> Asegúrese de asignar la dirección de correo electrónico al correo electrónico principal (emailaddress1) del contacto. Si ha agregado correo electrónico secundario (emailaddress2) o correo electrónico alternativo (emailaddress3) al registro de contacto y lo ha asignado al correo electrónico, la información de identidad no se agregará al contacto y se creará una nueva con la dirección de correo electrónico utilizada para el registro establecido en el correo electrónico principal (emailaddress1).

### <a name="claims-to-support-sign-in-scenarios"></a>Notificaciones para admitir escenarios de inicio de sesión

Los datos de Common Data Service y del proveedor de identidades no se vinculan directamente, por lo que los datos pueden no estar sincronizados. El portal debe tener una lista de notificaciones que desea aceptar desde cualquier evento de inicio de sesión para actualizar en Common Data Service. Estas notificaciones pueden ser un subconjunto de las notificaciones procedentes de un escenario de inicio de sesión, o es igual a ellas. Debe configurarse de forma independiente de la asignación de notificaciones de inicio de sesión, ya que es posible que no desee sobrescribir algunos atributos clave del portal. Se requiere la siguiente configuración del sitio:

**Nombre**: autenticación/OpenIdConnect/[Federation-Name]/LoginClaimsMapping

**Descripción**: lista de pares de nombre lógico o de notificaciones que se usarán para asignar valores de notificaciones a los atributos del registro de contacto creado después del inicio de sesión.

**Formato**: atributo1 = claim1, attribute2 = claim2, attribute3 = claim3

Por ejemplo: firstname =<http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

El nombre de la notificación es el campo de tipo de notificación que se muestra junto al atributo en las notificaciones de aplicación de directivas de inicio de sesión.

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>Permitir Asociación automática a un registro de contacto basado en el correo electrónico 

Los clientes que tengan registros de contacto con correos electrónicos asociados iniciarán un sitio web donde sus usuarios externos iniciarán sesión con [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C a través de un mecanismo de validación de correo electrónico. El nuevo inicio de sesión se debe asociar al registro de contacto existente en lugar de crear un registro duplicado. Esta funcionalidad solo asigna correctamente un contacto que no tiene una identidad activa y la dirección de correo electrónico debe ser única (no relacionada con varios registros de contactos). Se requiere la siguiente configuración del sitio:

**Nombre**: autenticación/[Protocolo]/[proveedor]/AllowContactMappingWithEmail

**Descripción**: especifica si los contactos están asignados a un correo electrónico correspondiente. Cuando se establece en true, esta configuración asocia un registro de contacto único con una dirección de correo electrónico coincidente y, a continuación, asigna automáticamente el proveedor de identidad externo al contacto después de que el usuario haya iniciado sesión correctamente. De forma predeterminada, se establece en false.
