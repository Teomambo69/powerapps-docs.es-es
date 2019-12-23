---
title: 'Tutorial: Registrar y configurar la aplicación SimpleSPA con adal.js (Common Data Service) | Microsoft Docs'
description: En este tutorial se describe el proceso para registrar y configurar la Aplicación de una sola página (SPA) más sencilla para tener acceso a los datos en Common Data Service usando adal.js y Uso compartido de recursos de origen cruzado(CORS).
keywords: ''
ms.date: 08/26/2019
ms.service: powerapps
ms.topic: article
ms.assetid: a327d2ff-e252-61cf-1190-6a974130ef19
author: paulliew
ms.author: nabuthuk
manager: ryjones
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 874fb17ddb2911f1464b07e7dacd597f89fc8c75
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2859937"
---
# <a name="walkthrough-registering-and-configuring-a-spa-application-with-adaljs"></a>Tutorial: Registrar y configurar una aplicación SPA con adal.js

En este tutorial se describe el proceso para registrar y configurar la Aplicación de una sola página (SPA) más sencilla para tener acceso a los datos en Common Data Service usando adal.js y Uso compartido de recursos de origen cruzado(CORS). Más información: [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página a Common Data Service](oauth-cross-origin-resource-sharing-connect-single-page-application.md).
  
## <a name="prerequisites"></a>Requisitos previos  
  
- Power Apps Common Data Service  
  
- Debe tener una cuenta de usuario del sistema de Common Data Service con el rol administrador para Office 365.  
  
- Una suscripción de Azure para registrar su aplicación. Una cuenta de prueba también funcionará.  
  
- Visual Studio 2017  
  
<a name="bkmk_goal"></a>

## <a name="goal-of-this-walkthrough"></a>Objetivo de este tutorial

Al completar este tutorial podrá ejecutar una aplicación SPA sencilla en Visual Studio que proporcione la capacidad para que un usuario se autentique y recupere datos de Common Data Service. Esta aplicación consta de una página HTML de ejemplo.  

Cuando se depura la aplicación inicialmente solo habrá un botón **Iniciar sesión**.  

Haga clic en **Iniciar sesión** y pasará a una página de inicio de sesión para escribir sus credenciales.  

Tras escribir sus credenciales volverá a la página HTML donde encontrará que el botón **Iniciar sesión** está oculto y un botón **Cerrar sesión** y **Obtener cuentas** están visibles. También verá un saludo con información de su cuenta de usuario.  

Haga clic en el botón **Obtener cuentas** para recuperar 10 registros de cuenta de su organización de Common Data Service. El botón **Obtener cuentas** está deshabilitado como se muestra en la captura de pantalla siguiente:  
  
![La página SimpleSPA](media/simple-spa.png "La página SimpleSPA")  

> [!NOTE]
> La carga inicial de datos de Common Data Service puede ser lenta mientras se realizan las operaciones para permitir la autenticación, pero las operaciones posteriores son mucho más rápidas.  

Por último, puede hacer clic en el botón **Cerrar sesión** para cerrar la sesión.  

> [!NOTE]
> Esta aplicación SPA no está diseñada para representar un modelo para desarrollar aplicaciones SPA robustas. Está simplificada para centrarse en el proceso de registrar y configurar la aplicación.  

<a name="bkmk_createwebapp"></a>

## <a name="create-a-web-application-project"></a>Crear un proyecto de aplicación web  
  
1. Usando Visual Studio 2017, cree un nuevo proyecto **Aplicación web ASP.NET** y use la plantilla **Vacío**. Puede dar el nombre que desee al proyecto.  
  
    Deberá poder usar versiones anteriores de Visual Studio también, pero estos pasos describirán el uso de Visual Studio 2017.  
  
2. Agregue una nueva página HTML llamada `SimpleSPA.html` al proyecto y pegue el siguiente código:  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
     <title>Simple SPA</title>  
     <meta charset="utf-8" />  
     <script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.17/js/adal.min.js"></script>  
     <script type="text/javascript">  
      "use strict";  
  
      //Set these variables to match your environment  
      var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL of your Common Data Service organization  
      var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
      var clientId = "[client id]"; //The ClientId you got when you registered the application  
      var pageUrl = "https://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
      var user, authContext, message, errorMessage, loginButton, logoutButton, getAccountsButton, accountsTable, accountsTableBody;  
  
      //Configuration data for AuthenticationContext  
      var endpoints = {  
       orgUri: organizationURI  
      };  
  
      window.config = {  
       tenant: tenant,  
       clientId: clientId,  
       postLogoutRedirectUri: pageUrl,  
       endpoints: endpoints,  
       cacheLocation: 'localStorage', 
      };  
  
      document.onreadystatechange = function () {  
       if (document.readyState == "complete") {  
  
        //Set DOM elements referenced by scripts  
        message = document.getElementById("message");  
        errorMessage = document.getElementById("errorMessage");  
        loginButton = document.getElementById("login");  
        logoutButton = document.getElementById("logout");  
        getAccountsButton = document.getElementById("getAccounts");  
        accountsTable = document.getElementById("accountsTable");  
        accountsTableBody = document.getElementById("accountsTableBody");  
  
        //Event handlers on DOM elements  
        loginButton.addEventListener("click", login);  
        logoutButton.addEventListener("click", logout);  
        getAccountsButton.addEventListener("click", getAccounts);  
  
        //call authentication function  
        authenticate();  
  
        if (user) {  
         loginButton.style.display = "none";  
         logoutButton.style.display = "block";  
         getAccountsButton.style.display = "block";  
  
         var helloMessage = document.createElement("p");  
         helloMessage.textContent = "Hello " + user.profile.name;  
         message.appendChild(helloMessage)  
  
        }  
        else {  
         loginButton.style.display = "block";  
         logoutButton.style.display = "none";  
         getAccountsButton.style.display = "none";  
        }  
  
       }  
      }  
  
      // Function that manages authentication  
      function authenticate() {  
       //OAuth context  
       authContext = new AuthenticationContext(config);  
  
       // Check For & Handle Redirect From AAD After Login  
       var isCallback = authContext.isCallback(window.location.hash);  
       if (isCallback) {  
        authContext.handleWindowCallback();  
       }  
       var loginError = authContext.getLoginError();  
  
       if (isCallback && !loginError) {  
        window.location = authContext._getItem(authContext.CONSTANTS.STORAGE.LOGIN_REQUEST);  
       }  
       else {  
        errorMessage.textContent = loginError;  
       }  
       user = authContext.getCachedUser();  
  
      }  
  
      //function that logs in the user  
      function login() {  
       authContext.login();  
      }  
      //function that logs out the user  
      function logout() {  
       authContext.logOut();  
       accountsTable.style.display = "none";  
       accountsTableBody.innerHTML = "";  
      }  
  
    //function that initiates retrieval of accounts  
      function getAccounts() {  
  
       getAccountsButton.disabled = true;  
       var retrievingAccountsMessage = document.createElement("p");  
       retrievingAccountsMessage.textContent = "Retrieving 10 accounts from " + organizationURI + "/api/data/v9.1/accounts";  
       message.appendChild(retrievingAccountsMessage)  
  
       // Function to perform operation is passed as a parameter to the acquireToken method  
       authContext.acquireToken(organizationURI, retrieveAccounts)  
  
      }  
  
    //Function that actually retrieves the accounts  
      function retrieveAccounts(error, token) {  
       // Handle ADAL Errors.  
       if (error || !token) {  
        errorMessage.textContent = 'ADAL error occurred: ' + error;  
        return;  
       }  
  
       var req = new XMLHttpRequest()  
       req.open("GET", encodeURI(organizationURI + "/api/data/v9.1/accounts?$select=name,address1_city&$top=10"), true);  
       //Set Bearer token  
       req.setRequestHeader("Authorization", "Bearer " + token);  
       req.setRequestHeader("Accept", "application/json");  
       req.setRequestHeader("Content-Type", "application/json; charset=utf-8");  
       req.setRequestHeader("OData-MaxVersion", "4.0");  
       req.setRequestHeader("OData-Version", "4.0");  
       req.onreadystatechange = function () {  
        if (this.readyState == 4 /* complete */) {  
         req.onreadystatechange = null;  
         if (this.status == 200) {  
          var accounts = JSON.parse(this.response).value;  
          renderAccounts(accounts);  
         }  
         else {  
          var error = JSON.parse(this.response).error;  
          console.log(error.message);  
          errorMessage.textContent = error.message;  
         }  
        }  
       };  
       req.send();  
      }  
      //Function that writes account data to the accountsTable  
      function renderAccounts(accounts) {  
       accounts.forEach(function (account) {  
        var name = account.name;  
        var city = account.address1_city;  
        var nameCell = document.createElement("td");  
        nameCell.textContent = name;  
        var cityCell = document.createElement("td");  
        cityCell.textContent = city;  
        var row = document.createElement("tr");  
        row.appendChild(nameCell);  
        row.appendChild(cityCell);  
        accountsTableBody.appendChild(row);  
       });  
       accountsTable.style.display = "block";  
      }  
  
     </script>  
     <style>  
      body {  
       font-family: 'Segoe UI';  
      }  
  
      table {  
       border-collapse: collapse;  
      }  
  
      td, th {  
       border: 1px solid black;  
      }  
  
      #errorMessage {  
       color: red;  
      }  
  
      #message {  
       color: green;  
      }  
     </style>  
    </head>  
    <body>  
     <button id="login">Login</button>  
     <button id="logout" style="display:none;">Logout</button>  
     <button id="getAccounts" style="display:none;">Get Accounts</button>  
     <div id="errorMessage"></div>  
     <div id="message"></div>  
     <table id="accountsTable" style="display:none;">  
      <thead><tr><th>Name</th><th>City</th></tr></thead>  
      <tbody id="accountsTableBody"></tbody>  
     </table>  
    </body>  
    </html>  
  
    ```  
  
3. Haga clic con el botón secundario en el archivo SimpleSPA.html y seleccione **Establecer como página de inicio** para establecer esta página como la página de inicio para el proyecto.  
  
4. En las propiedades del proyecto, seleccione **Web** y en **Servidores** anote la **Dirección URL del proyecto**. Debe ser algo como `https://localhost:62111/`. Observe el número de puerto generado. Necesitará esto en el siguiente paso.  
  
5. En la página SimpleSPA.html, busque las siguientes variables de configuración y establézcalas en consecuencia. Podrá establecer el `clientId` después de completar la parte siguiente de tutorial.  
  
    ```javascript  
    //Set these variables to match your environment  
    var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL to connect to Power Apps Common Data Service  
    var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
    var clientId = "[client id]"; //The ClientId you got when you registered the application  
    var pageUrl = "https://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
    ```  
  
## <a name="register-the-application"></a>Registrar la aplicación  
  
1. Iniciar sesión en el [portal de Azure](https://go.microsoft.com/fwlink/?linkid=2083908) con una cuenta con permiso de administrador. Debe usar una cuenta en la misma suscripción de Office 365 (empresa) con la que pretenda registrar la aplicación. También puede obtener acceso al portal de Azure a través del centro de administración de Microsoft 365 expandiendo el elemento **ADMIN** en el panel de navegación de la izquierda y seleccionando **Azure AD**.  
  
    > [!NOTE]
    > Si no tiene una empresa de Azure (cuenta) o tiene una pero su suscripción a Office 365 con Common Data Service no está disponible en su suscripción de Azure, siga las instrucciones en el tema [Configurar acceso a Azure Active Directory para el sitio de desarrollador](https://docs.microsoft.com/office/developer-program/office-365-developer-program) para asociar las dos cuentas.<br/><br/> Si no tiene una cuenta, puede registrarse para obtener una cuenta utilizando una tarjeta de crédito. No obstante, la cuenta es gratuita para el registro de aplicaciones y no se cargará en su tarjeta de crédito si sigue los procedimientos indicados en este tema para registrar una o varias aplicaciones. Más información: [Detalles de precios de Active Directory](https://azure.microsoft.com/pricing/details/active-directory/)  
  
2. Haga clic en **Azure Active Directory** en la columna de la izquierda de la página. Es posible que deba desplazarse por la columna izquierda para ver el icono y la etiqueta de **Azure Active Directory**.  
  
3. Ahora seleccione **Aplicaciones empresariales** en el panel que se abre.

   ![Seleccione Aplicaciones empresariales](media/register-spa-app-registration.PNG)

4. Seleccione **Nueva aplicación**(cerca de la parte superior de la página) y en **Agregar su propia aplicación** seleccione **Aplicación que está desarrollando**.  

   ![Seleccione Aplicación que está desarrollando](media/register-spa-app-you-developing.PNG)
  
5. Ahora haga clic en **Ir a los registros de aplicación para registrar mi nueva aplicación**.

   ![Seleccione Ir a los registros de aplicación](media/register-spa-take-me-app-reg.PNG)

6. Ahora haga clic en **Registrar aplicación nueva**(cerca de la parte superior de la página).  

   ![Seleccione Nuevo registro de aplicación](media/register-spa-new-reg.PNG)
  
7. Escriba la siguiente información:  
  
   - **Nombre**<br />El nombre de la aplicación.

   - **Tipos de cuenta admitidos**<br />Seleccione **Cuentas en cualquier directorio de organización**.

   - **URL de redireccionamiento**<br />Se trata de la dirección URL a la que el usuario debe ser redirigido después de que inicie sesión. Seleccionar **Web** en la lista desplegable. A efectos de depuración en Visual Studio debe ser `https://localhost:####/SimpleSPA.html` donde #### representa el número de puerto que obtuvo en el paso 4 del procedimiento [Crear un proyecto de aplicación web](#bkmk_createwebapp). Haga clic en **Registrar** al final de la página.

   ![Especifique los detalles](media/new-app-registration-page.png)

8. En la pestaña de la aplicación recién registrada, copie el **Identificador de la aplicación (cliente)**. Establezca la variable `clientId` en la página SimpleSPA.html con este valor. Consulte al paso 5 del procedimiento **Crear un proyecto de aplicación web**.  

9. Ahora haga clic en **Permisos de API** y después seleccione **Agregar un permiso**.

   ![Seleccione Permisos requeridos](media/azure-api-permissions-page.png)

10. Seleccione **Dynamics CRM** en la pestaña **API de Microsoft**.

    ![Seleccione Dynamics CRM Online en Seleccionar una API](media/app-registration-select-api-page.png)

11. Haga clic en **Permisos delegados**, seleccione todos los permisos y haga clic en **Agregar permisos** al final de la página.

    ![Seleccione todos los permisos delegados](media/app-registration-delegate-permissions-page.png)

12. A continuación, seleccione **Hecho**. Aparecerá una fila para **Dynamics CRM** agregado.

13. Ahora cierra la pestaña **Permisos de API**. En la pestaña registrada de la aplicación, seleccione **Manifiesto**.

14. Busque la línea: `"oauth2AllowImplicitFlow": false,` y cambie `false` a `true` y haga clic en **Guardar** para guardar el archivo.

    ![Establezca oauth2AllowImplicitFlow en True en el archivo de manifiesto](media/register-spa-edit-manifest.PNG)

15. Para la ejecución correcta de la aplicación, también necesitará concederle consentimiento de administrador. Para ello, inicie sesión como Administrador de inquilinos en el portal de Azure de administración y seleccione **Azure Active Directory**. Haga clic en **Aplicaciones empresariales** y en la lista de aplicaciones que aparece seleccione la aplicación que acaba de crear.

    ![Conceda su consentimiento de administrador a su aplicación](media/simple-spa-admin-consent.PNG)

16. Ahora seleccione **Permisos de API** como se muestra arriba, y haga clic **Conceder consentimiento de administrador para**`<your AAD Org name>`.

    ![Haga clic en el botón Conceder consentimiento de administrador](media/simple-spa-admin-consent-button.PNG)

17. Una vez que se hace clic en este botón, se abrirá una ventana de inicio de sesión y le preguntará si desea conceder los permisos solicitados a la aplicación. Haga clic en **Aceptar** para continuar.

    ![Haga clic en Aceptar para conceder los permisos solicitados](media/simple-spa-admin-consent-click-accept.PNG)

18. A continuación, deberá pasar a la depuración de la aplicación.

> [!NOTE]
> Debe habilitar la opción **Testigos de Id** en la pestaña **Autenticación** de la aplicación que ha registrado.

## <a name="debugging-the-application"></a>Depurar la aplicación  
  
1.  Establezca el explorador para usar Microsoft Edge o Google Chrome.  
  
    > [!NOTE]
    > Internet Explorer no funcionará para depuración en esta situación.  
  
2.  Pulse F5 para iniciar la depuración. Debe esperar el comportamiento descrito en [Objetivo de este tutorial](walkthrough-registering-configuring-simplespa-application-adal-js.md#bkmk_goal).  
  
Si no obtiene los resultados deseados, compruebe dos veces los valores que estableció al registrar la aplicación y configurar el código `SimpleSPA.html`.  
  
## <a name="see-also"></a>Vea también  
 [Crear aplicaciones cliente](connect-cds.md)<br />
 [Tutorial: Registrar una aplicación con Azure Active Directory](walkthrough-register-app-azure-active-directory.md) <br />
 [Crear aplicaciones web mediante autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md)<br />
 [Usar OAuth con Uso compartido de recursos de origen cruzado para conectar una aplicación de una sola página a Common Data Service](oauth-cross-origin-resource-sharing-connect-single-page-application.md)