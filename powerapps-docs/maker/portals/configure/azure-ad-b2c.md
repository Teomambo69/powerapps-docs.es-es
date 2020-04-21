---
title: Configuración del proveedor Azure AD B2C para portales | MicrosoftDocs
description: Instrucciones de habilitar los ajustes del proveedor de Azure AD B2C para portales.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/03/2020
ms.author: tapanm
ms.reviewer: tapanm
ms.openlocfilehash: 37a515486afd2c57fa07cea24905584e9515ba60
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "3238522"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>Azure AD B2C configuración del proveedor para portales

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) activa Office 365 y los servicios de Dynamics 365 para la autenticación interna o de empleados. [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C es una extensión al modelo de autenticación que habilita los inicios de sesión de clientes externos mediante las credenciales locales y de federación los distintos proveedores de identidad sociales comunes.

Un propietario de portal puede configurar el portal para aceptar [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C como proveedor de identidad. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C admite Open ID Connect para federación.

Durante la configuración de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C como proveedor de identidad del portal, varios valores se generan que usará más adelante cuando configure el portal. Puede anotar estos valores en la tabla siguiente. Mientras configura el portal, reemplace el nombre de variable por los valores que escriba aquí.

| Nombre de variable     | Valor | Descripción                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| Nombre de la aplicación  |       | Nombre de la aplicación que representa el portal como un usuario de confianza |
| Id. de aplicación    |       | El identificador de la aplicación asociado a la aplicación creada en Azure Active Directory B2C.  |
| Issuer-URL |       | La dirección URL del emisor (iss) definida en el extremo de metadatos.                |
| Nombre de la federación   |       | Un nombre único para identificar el tipo de proveedor de federación como “B2C”. Se usará en los nombres de configuración de sitio para agrupar las opciones de configuración de este proveedor específico.                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Use Azure AD AD B2C como proveedor de identidad para el portal

1. Inicie sesión en el [portal Azure](https://portal.azure.com/).
1. [Crear un inquilino de Azure AD B2C](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started).
1. Seleccione **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** en la barra de navegación más a la izquierda.
1. [Cree la aplicación Azure](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application).

   > [!Note]
   > Debe elegir **Sí** para el campo **Permitir el flujo implícito** y especificar la dirección URL de portal en el campo **Dirección URL de respuesta**. El valor en el campo **Dirección URL de respuesta** debe tener el formato [dominio de portal]/inicio de sesión-[Nombre de la federación]. Por ejemplo, `https://contosocommunity.microsoftcrmportals.com/signin-B2C`.

1. Copie el nombre de la aplicación, e incorpórelo como el valor del nombre de la aplicación en la tabla precedente.
1. Copie el id. de (cliente) de la aplicación e incorpórelo como el valor del id. de la aplicación en la tabla precedente.
1. [Crear una directiva de registro o inicio de sesión](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy).
1. Navegue al recurso **Azure AD B2C**.
1. Seleccione **Flujos de usuarios** bajo Directivas.
1. Elija la política de suscripción e inicio de sesión recién creada.
1. En la lista **Configuraciones**, seleccione **Propiedades**
1. En **Configuración de compatibilidad de token**, en la lista **Notificación de emisor (iss)**, seleccione la URL que tiene **/tfp** en la ruta.
1. Guarde la directiva.
1. Seleccione la dirección URL en el campo **Extremo de metadatos para esta directiva**.
1. Copie el valor del campo de emisor e incorpórelo como el valor de Issuer-URL en la tabla precedente. 

## <a name="portal-configuration"></a>Configuración de portal

Después de crear y configurar el suscriptor de B2C en [!include[Azure](../../../includes/pn-azure-shortest.md)], debe configurar el portal para federar con [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C mediante el protocolo Open ID Connect. Debe crear un nombre único para la federación a [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C&mdash;por ejemplo B2C&mdash;y almacenarlo como el valor de la variable *Nombre de federación* en la tabla anterior.

### <a name="configure-your-portal"></a>Configure su portal
1. Abra la aplicación Administración del portal.
2. Vaya a **Portales** > **Páginas web**.
3. Seleccione el registro de la página web para el que debe habilitarse [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C.
4. Vaya a **Configuración del sitio**.
5. Cree la siguiente configuración del sitio:
   -   **Nombre**: Autenticación/OpenIdConnect/[Nombre de federación]/Autoridad

       **Valor**: [Issuer-URL]
   -   **Nombre**: Autenticación/OpenIdConnect/[Nombre de federación]/ClientId

       **Valor**: [ID de aplicación]
   -   **Nombre**: Autenticación/OpenIdConnect/[Nombre de federación]/RedirectUri

       **Valor**: [dominio de portal]/inicio de sesión-[Nombre de federación]

       Por ejemplo, `https://mysite.com/signin-b2c` 
6. Para admitir un inicio de sesión federado, cree la siguiente configuración del sitio:
   - **Nombre**: Authentication/OpenIdConnect/[Nombre de federación]/ExternalLogoutEnabled

     **Valor**: verdadero
7. Para codificar de forma rígida su portal para un solo proveedor de identidad, cree la siguiente configuración del sitio:
   - **Nombre**: Authentication/Registration/LoginButtonAuthenticationType

     **Valor**: [Issuer-URL]

8. Para admitir la restauración de la contraseña, cree la configuración necesaria descrita [aquí](#password-reset).
9. Para admitir la asignación de notificaciones, cree la configuración necesaria descrita [aquí](#claims-mapping).

Para obtener una lista completa de la configuración del sitio, consulte [aquí](#related-site-settings).

### <a name="password-reset"></a>Restablecimiento de contraseña

Se requiere la siguiente configuración del sitio si desea admitir la restauración de la contraseña más con cuentas locales de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C.

| Configuración del sitio                                                        | Descripción                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[Nombre de federación]/PasswordResetPolicyId | Identificador de la directiva de restauración de contraseña.                                                                                     |
| Authentication/OpenIdConnect/[Nombre de federación]/ValidIssuers         | Una lista delimitada por comas de emisores que incluye [Issuer-URL] y el emisor de la directiva de restablecimiento de contraseña. |
|Authentication/OpenIdConnect/[Nombre de federación]/DefaultPolicyId | Identificador de la directiva de inicio de sesión o suscripción.|
|||

### <a name="related-site-settings"></a>Configuración del sitio relacionada

Puede crear o configurar la siguiente configuración del sitio en portales para admitir [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C como proveedor de identidad:


| Configuración del sitio                                                         | Descripción                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ProfileRedirectEnabled                   | Especifica si el portal puede redirigir a usuarios a la página del perfil después de iniciar sesión correctamente. De forma predeterminada, se establece como verdadero.                                                                                                                                            |
| Authentication/Registration/EmailConfirmationEnabled                 | Especifica si la validación de correo electrónico es necesaria. De forma predeterminada, se establece como verdadero.                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | Especifica si se necesita un inicio de sesión local. De forma predeterminada, se establece como verdadero.                                                                        |
| Authentication/Registration/ExternalLoginEnabled                     | Habilita o deshabilita la autenticación externa.       |
| Authentication/Registration/AzureADLoginEnabled                      | Habilita o deshabilita [!include[Azure](../../../includes/pn-azure-shortest.md)] AD como proveedor de identidad externo. De forma predeterminada, se establece como verdadero.                                                                                                                                                                      |
| Authentication/OpenIdConnect/[Nombre de federación]/ExternalLogoutEnabled | Habilita o deshabilita el inicio de sesión federado. Si se establece en verdadero, los usuarios se redirigen a la experiencia de usuario de inicio de sesión federado al cerrar sesión en el portal. Si se establece en falso, los usuarios cierran sesión solo del portal. De forma predeterminada, se establece en falso.               |
| Authentication/LoginTrackingEnabled                                  | Habilita o deshabilita el seguimiento del último inicio de sesión del usuario. Si se establece en verdadero, se muestran la fecha y la hora en el campo **Último inicio de sesión correcto** en el registro de contacto. De manera predeterminada, el valor es falso.                                                            |
| Authentication/OpenIdConnect/[Nombre de federación]/RegistrationEnabled   | Habilita o deshabilita el requisito de registro para el proveedor de identidad existente. Si se establece en verdadero, se habilita el registro del proveedor existente solo si Authentication/Registration/Enabled también se establece en verdadero. De forma predeterminada, se establece como verdadero. |
|Authentication/OpenIdConnect/[Nombre de federación]/PostLogoutRedirectUri |Especifica la dirección URL en el portal a la que se va a redirigir a después de que los usuarios cierren sesión. |
| | |

### <a name="related-content-snippet"></a>Fragmento de contenido relacionado

Si el registro está deshabilitado para un usuario después de que el usuario haya redimido una invitación, aparece un mensaje con el siguiente fragmento de contenido:

**Nombre**: Account/Register/RegistrationDisabledMessage

**Valor**: El registro se ha deshabilitado.

## <a name="customize-the-includeazure-ad-b2c-user-interface"></a>Personalizar la interfaz de usuario de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C admite la personalización de la interfaz de usuario. Puede personalizar la experiencia del usuario para el registro y el inicio de sesión.

### <a name="step-1-create-a-web-template"></a>Paso 1: Crear una plantilla web
Cree una plantilla web mediante los siguientes valores:

**Nombre**: página personalizada de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

**Origen**: Use el siguiente HTML de origen de plantilla web de ejemplo.

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
### <a name="step-2-create-a-page-template"></a>Paso 2: Crear una plantilla de página

Cree la plantilla de página siguiente:
- **Nombre**: página personalizada de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C
- **Tipo**: plantilla web
- **Plantilla web**: Página personalizada de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C
- **Encabezado y pie de página de la página web de uso**: Desactive esta casilla

### <a name="step-3-create-a-webpage"></a>Paso 3: Crear un página web

Cree la siguiente página web:
- **Nombre**: Inicio de sesión
- Página **principal**: Inicio
- **URL parcial**: azure-ad-b2c-sign-in
- **Plantilla de página**: Página personalizada de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C
- **Estado de publicación**: Publicado

### <a name="step-4-create-site-settings"></a>Paso 4: Crear configuraciones de sitio

La configuración de sitio es necesaria para configurar el uso compartido de recursos (CORS) de origen cruzado para permitir que [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C solicite la página personalizada y que inserte la interfaz de usuario de registro o de inicio de sesión. Cree la siguiente configuración del sitio.

| Nombre                              | Valor                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control-Allow-Methods | OBTENER, OPCIONES                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

Para obtener una lista completa de otros valores de configuración CORS, consulte [Soporte de protocolo CORS](../add-web-resource.md#cors-protocol-support).

### <a name="step-5-includeazure-configuration"></a>Paso 5: Configuración [!include[Azure](../../../includes/pn-azure-shortest.md)]

1. Inicie sesión en su [!include[Azure portal](../../../includes/pn-azure-portal.md)].
2. Desplácese hasta la hoja **Administración de suscriptores de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C**.
3. Vaya a **Configuración** > **Directivas de registro e inicio de sesión**. Aparecerá la lista de directivas disponibles.
4. Seleccione la directiva que desea editar.
5. Seleccione **Editar**.
6. Seleccione **Editar directiva** > **Personalización de interfaz de página** > **Página de registro o inicio de sesión unificada**
7. Establezca **Usar la página personalizada** **Sí**.
8. Establezca **URL personalizada de página** en la URL de la página web de página personalizada de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C creada en el paso 3 del procedimiento. Por ejemplo, `https://mydomain.com/azure-ad-b2c-sign-in`.
9. Seleccione **Aceptar**.

## <a name="claims-mapping"></a>Asignación de notificaciones

Cuando los usuarios inicien sesión, por primera vez o posteriormente, el proveedor de identidad federado proporciona notificaciones según su base de datos sobre el inicio de sesión de los usuarios. Estas notificaciones se pueden configurar en el proveedor de identidad.

### <a name="includeazure-ad-b2c-email-claims"></a>Notificaciones de correo electrónico de [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C envía la notificación de correo electrónico como una recopilación. El portal acepta el primer correo electrónico de la recopilación como la dirección de correo electrónico principal del contacto.

### <a name="claims-to-support-sign-up-scenarios"></a>Reclamaciones para admitir escenarios de registro

Si se aprovisiona un nuevo cliente que no existe en Common Data Service las notificaciones entrantes se pueden usar para propagar el nuevo registro de contacto que creará el portal. Las notificaciones comunes pueden incluir el nombre y el apellido, dirección de correo electrónico, y número de teléfono, pero son configurables. Se necesita la siguiente configuración de sitio:

**Nombre**: Authentication/OpenIdConnect/[Nombre de federación]/RegistrationClaimsMapping

**Descripción**: Lista de pares de nombre lógico y de notificación que se van a usar para asignar valores de notificaciones a atributos en el registro de contacto creado durante el registro.

**Formato**: atributo1=notificación1, atributo2=notificación2, atributo3=notificación3

Por ejemplo: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> Asegúrese de que asigna la dirección de correo electrónico para el mensaje principal (emailaddress1) del contacto. Si ha agregado un correo electrónico secundario (emailaddress2) o alternativo (emailaddress3) al registro de contacto y lo ha asignado al correo electrónico, la información de identidad no se agregará al contacto y se creará una nueva con la dirección de correo electrónico que se usó para el registro establecido en el correo electrónico principal (emailaddress1).

### <a name="claims-to-support-sign-in-scenarios"></a>Reclamaciones para admitir escenarios de registro

Los datos de Common Data Service y en el proveedor de identidad no se vinculan directamente, por lo que los datos pueden desincronizarse. El portal debe tener una lista de notificaciones que desee aceptar de cualquier evento de inicio de sesión para actualizar en Common Data Service. Estas notificaciones pueden ser un subconjunto o iguales a las notificaciones que proceden de un escenario de inicio de sesión. Esto se debe configurar por separado de la asignación de notificaciones de inicio de sesión, porque es posible que no desee sobrescribir algunos atributos de portal clave. Se necesita la siguiente configuración de sitio:

**Nombre**: Authentication/OpenIdConnect/[Nombre de federación]/LoginClaimsMapping

**Descripción**: Lista de pares de nombre lógico y de notificación que se van a usar para asignar valores de notificaciones a atributos en el registro de contacto creado tras el inicio de sesión.

**Formato**: atributo1=notificación1, atributo2=notificación2, atributo3=notificación3

Por ejemplo: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

El nombre de notificación es el campo TIPO DE NOTIFICACIÓN indicado junto al atributo de las directivas de inicio de sesión Notificaciones de aplicación.

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>Permitir la asociación automática a un registro de contacto en función de correo electrónico 

Los clientes que tienen registros de contactos con correos electrónicos asociados lanzan una página web donde los usuarios externos iniciarán sesión con [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C mediante un mecanismo de validación de correo electrónico. El nuevo inicio de sesión debe estar asociado al registro de contacto existente en lugar de crear un registro duplicado. Esta funcionalidad asigna solo correctamente un contacto que no tiene una identidad activa, y la dirección de correo electrónico debe ser única (no relacionada con varios registros de contacto). Se necesita la siguiente configuración de sitio:

**Nombre**: Authentication/[Protocolo]/[Proveedor]/AllowContactMappingWithEmail

**Descripción**: Especifica si los contactos están asignados al correo electrónico correspondiente. Si se establece en verdadero, el valor se asocia a un registro de contacto único con una dirección de correo electrónico coincidente, y después asigna automáticamente el proveedor de identidad externo al contacto una vez que el usuario ha iniciado sesión correctamente. De forma predeterminada, se establece en *falso*.

**Nombre**: Authentication/UserManager/UserValidator/RequireUniqueEmail

**Descripción**: Especifica si se necesita un correo electrónico único para validar el usuario. Cuando se utiliza una dirección de correo electrónico de contacto existente para iniciar sesión, la configuración debe establecerse en falso. De manera predeterminada, se establece en *verdadero*, lo que puede causar que los intentos de inicio de sesión fallen para los registros de contacto con la dirección de correo electrónico ya presente.
