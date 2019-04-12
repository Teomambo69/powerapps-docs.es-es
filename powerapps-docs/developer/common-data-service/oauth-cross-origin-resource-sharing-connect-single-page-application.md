---
title: Usar OAuth con Uso compartido de recursos de origen cruzado para conectar una aplicación de una sola página (Common Data Service) | Microsoft Docs
description: Aprenda a usar OAuth con Uso compartido de recursos de origen cruzado para conectar una aplicación de una sola página
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: oauth-cross-origin-resource-sharing-connect-single-page-application
caps.latest.revision: 11
author: paulliew
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/oauth-cross-origin-resource-sharing-connect-single-page-application 

-->
# <a name="use-oauth-with-cross-origin-resource-sharing-to-connect-a-single-page-application"></a>Usar OAuth con uso compartido de recursos de origen cruzado para conectar una aplicación de una sola página

Puede crear aplicaciones de una sola página (SPA) que usen JavaScript para trabajar con datos de Common Data Service. Para proporcionar esto, Uso compartido de recursos de origen cruzado (CORS) se habilita de forma que las SPA puedan superar las restricciones de explorador que evitan normalmente las solicitudes que cruzan límites de dominio.  
  
> [!NOTE]
>  La compatibilidad de CORS se proporciona sólo al usar la API web. No puede usar el servicio de la organización o el servicio de datos de la organización obsoleto.  
  
<a name="bkmk_Spas_and_same_origin_policy"></a> 
  
## <a name="spas-and-same-origin-policy"></a>SPA y Directiva de mismo origen  

Las SPA dependen de un uso amplio de JavaScript del lado del cliente para crear una sola página dinámica que no necesite cargar nuevas páginas. En su lugar usan XMLHTTPRequests para recuperar datos y otros recursos del servidor. Las SPA funcionan bien cuando los datos y recursos existen en el mismo dominio que la aplicación. Pero para proteger el acceso a los datos y recursos de otros dominios, todos los exploradores modernos aplican una directiva de Mismo origen para evitar que los sitios usen datos y recursos de sitios en un dominio distinto. CORS proporciona una forma de tener acceso a los recursos en otro dominio. Crear un SPA para tener acceso a datos de Common Data Service sin CORS no es una opción viable.  
  
<a name="bkmk_use_cors"></a>

## <a name="use-cors-with-common-data-service"></a>Usar CORS con Common Data Service 
 
La [especificación de uso compartido de recursos entre orígenes](http://www.w3.org/TR/cors/) proporciona una descripción detallada de cómo implementar y usar CORS. Explica todo sobre los diferentes encabezados y las solicitudes de preparación que necesita aplicar para que CORS funcione. La buena noticia es que no necesita convertirse en un experto en CORS para usarla con Common Data Service. La parte del lado del servidor se ha realizado para usted y lo único que necesita es saber cómo consumirlo.  No necesita comprender el funcionamiento interno de CORS para usarla con Common Data Service. En su lugar puede usar la [Biblioteca de autenticación de Azure Active Directory para JavaScript](https://github.com/AzureAD/azure-activedirectory-library-for-js) (adal.js), que se ocupará de gran parte de la complejidad de CORS por usted. Dado que Common Data Service se autentica con Azure Active Directory, ADAL.js es la forma compatible para autenticar usuarios de SPA.  
  
<a name="bkmk_how_adaljs_works"></a>

## <a name="how-adaljs-works"></a>Cómo funciona adal.js

La biblioteca central es `adal.js`. Puede acceder a la versión minimizada de esta biblioteca en [https://secure.aadcdn.microsoftonline-p.com/lib/1.0.0/js/adal.min.js](https://secure.aadcdn.microsoftonline-p.com/lib/1.0.0/js/adal.min.js). El proyecto de GitHub y la documentación están en [https://github.com/AzureAD/azure-activedirectory-library-for-js](https://github.com/AzureAD/azure-activedirectory-library-for-js).  
  
La biblioteca adal.js contiene las capacidades de bajo nivel para autenticarse mediante OAuth2. Adal.js se ha diseñado para poder usarse con otros marcos de trabajo, por ejemplo, hay una biblioteca `adal-angular.js` diseñada para usarse con el marco de trabajo Angular. La forma de trabajar con esta biblioteca es establecer determinadas propiedades de configuración y después esperar hasta que se produzcan eventos que desencadenen el flujo de interacción. Esto podría ser simplemente llamando a la función `login` o si su aplicación tiene comportamientos de enrutamiento, la autenticación podría ser iniciada en función de la configuración del controlador de esa ruta.  
  
Cuando se requiere autenticación, el usuario pasa a la página de inicio de sesión donde pueden introducir a sus credenciales. Después de autenticarse correctamente, se reenvían a la página de llamada con la información de token adjuntada como fragmento (usando `#`) a la dirección URL. Esto permite que SPA adquiera el token y lo almacena en caché en almacenamiento local o de sesión en el explorador. Esto significa que la página completa se recarga tras la autenticación, pero esta vez la información sobre el usuario autorizado está disponible y la aplicación puede continuar realizando llamadas a la API web de Common Data Service o a otros recursos.  
  
Cuando llama a la API web de Common Data Service, debe incluir el valor del token en un encabezado Authorization con la solicitud XMLHTPPRequest. Sin embargo, dado que los tokens tienen una expiración debe estar seguro de que no expirará mientras los usuarios usan su SPA. Recuerde, la introducción de nuevas credenciales requiere que el contenido completo de su página SPA se transfiera a la página de inicio de sesión. Esto produciría una experiencia de usuario muy mala si ocurriera mientras los usuarios están en medio de una tarea. Para asegurarse de que esto no ocurre, envuelva las llamadas de la API web en una función `acquireToken` de modo que la validez del token se pueda comprobar y actualizar si es necesario sin llevar al usuario a una página de inicio de sesión.  
  
<a name="bkmk_preparing_to_use_adaljs"></a>

## <a name="preparing-to-use-adaljs-with-a-spa"></a>Preparación para usar ADAL.js con una SPA

 Para configurar su SPA para que funcione con adal.js deberá:  
  
1.  Registrar su aplicación con el inquilino de Azure Active Directory  
2.  Exporte el manifiesto de la aplicación registrada y edítelo para permitir OAuth2 Implicit Flow y luego vuelva a importar el archivo JSON al registro de la aplicación.  
3.  Establezca variables de configuración en su SPA con información de ese registro.  
     Deberá incluir lo siguiente:  
  
    -   La dirección URL de la organización de Common Data Service  
    -   El nombre del inquilino de Active Directory que usa la organización para autenticarse  
    -   El identificador del cliente que obtiene al registrar la aplicación  
    -   La dirección URL donde se implementará o depurará la SPA durante el desarrollo  


 El conjunto de pasos necesarios se describe en [Tutorial: Registrar y configurar la aplicación SPA con adal.js](walkthrough-registering-configuring-simplespa-application-adal-js.md).  
  
### <a name="see-also"></a>Vea también

[Usar OAuth para conectarse a servicios web de Common Data Service](connect-web-services-using-oauth.md)   


