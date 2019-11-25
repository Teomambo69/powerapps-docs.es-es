---
title: Autenticación para usar la API de Online Management para Common Data Service| MicrosoftDocs
description: Proporciona información sobre la autenticación en la API de Online Management para realizar operaciones relacionadas con entornos.
ms.date: 11/27/2017
ms.service: crm-online
ms.topic: conceptual
ms.assetid: c292c148-01f0-41f6-a2fe-7ed05a01a733
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: 7243f2fccc8356ecac5eedba2b740bc39df1913a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752940"
---
# <a name="authenticate-to-use-the-online-management-api"></a>Autenticación para usar la API de Online Management

La API de Online Management admite el protocolo OAuth 2.0 para la autenticación. Use [Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) para autenticarse obteniendo un token de acceso válido de OAuth 2.0 y páselo mediante el encabezado **Autorización** en las solicitudes a la API de Online Management.

La API de autenticación recomendada para usar con la API de Online Management es [Azure Active Directory Authentication Library (ADAL)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries), que está disponible para una gran variedad de plataformas y lenguajes de programación. 

## <a name="how-to-authenticate"></a>¿Cómo autenticarse?

Estos son los pasos generales para autenticarse en el servicio de la API de Online Management. 

1. Registre una aplicación en Azure Active Directory para obtener los valores de *clientId* y *redirectUrl* para su aplicación. Para obtener más información, consulte la sección “Registro de aplicaciones para autenticación OAuth” en [Tutorial: Registrar una aplicación con Azure Active Directory](/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)

1. Especifique los valores obtenidos en el paso 1 en el [código auxiliar](sample-authentication-helper.md) de autenticación:

    ```csharp
    // TODO: Substitute your app registration values here.
    // These values are obtained on registering your application with the 
    // Azure Active Directory.
    private static string _clientId = "<GUID>";    //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    private static string _redirectUrl = "<Url>";  //e.g. "app://s7cf7712-b773-4f16-92b3-34cs97a25cc7"
    ```

1. Descubra la información de autoridad de la API de Online Management según la dirección URL del servicio. Para la región de Norte América, la dirección URL del servicio es: **https://admin.services.crm.dynamics.com**. Para la dirección URL específica del área del servicio, consulte [Nombres la dirección URL](get-started-online-management-api.md#service-url)<br /> Use el formato de reto de Azure Active Directory para determinar la información de autoridad según la dirección URL del servicio de la API.<br />También estamos determinando el recurso para la API de Online Management (diferente de la dirección URL del servicio), que se usará en el siguiente paso para adquirir el token de acceso.

    ```csharp
    public static async Task<string> DiscoverAuthority(string _serviceUrl)
    {
        try
        {
            AuthenticationParameters ap = await AuthenticationParameters.CreateFromResourceUrlAsync(
                    new Uri(_serviceUrl + "/api/aad/challenge"));
            _resource = ap.Resource;
            return ap.Authority;
        }
        catch (HttpRequestException e)
        {
            throw new Exception("An HTTP request exception occurred during authority discovery.", e);
        }
        catch (Exception e)
        {
            throw e;
        }
    }
    ```
1. Use el recurso que detectó en el paso anterior junto con los valores de la dirección URL de redireccionamiento e id. de cliente de su aplicación cliente para adquirir un token de acceso. Tenga en cuenta que debe usar el recurso, y no la dirección URL del servicio, para adquirir o actualizar el token de acceso.

    ```csharp
    public AuthenticationResult AcquireToken()
    {
        return _authContext.AcquireToken(_resource, _clientId, new Uri(_redirectUrl),
                PromptBehavior.Always);
    }        
    ```

1. Una vez que tenga el token de acceso, debe establecer el encabezado de **Autorización** de la solicitud de mensaje en el valor del token de acceso y especificar el tipo de token en **Portador**. Además, establezca el encabezado de **aceptación de idioma** para especificar el idioma preferido para la respuesta. El método `SendAsync` en la autenticación establece estos valores de encabezado para todas las solicitudes de mensajes:

    ```csharp
    protected override Task<HttpResponseMessage> SendAsync(
                HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)
    {
        // It is a best practice to refresh the access token before every message request is sent. Doing so
        // avoids having to check the expiration date/time of the token. This operation is quick.
        request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", _auth.AcquireToken().AccessToken);
        
        // Set the "Accept-Language" header
        request.Headers.Add("Accept-Language", "en-US");

        return base.SendAsync(request, cancellationToken);
    }
    ```

Está listo para ejecutar mensajes con la API de Online Management. Para un código de ejemplo que demuestra cómo recuperar todos los entornos de Common Data Service en el inquilino de Office 365, consulte [Ejemplo de inicio rápido: Recuperar entornos en el inquilino](sample-quick-start.md)


### <a name="related-topics"></a>Temas relacionados  

[Ejemplo: Código auxiliar de autenticación para la API de Online Management](sample-authentication-helper.md)

[Introducción a la API de Online Management](get-started-online-management-api.md)

[Referencia de la API de Online Management](/rest/api/admin.services.crm.dynamics.com)
