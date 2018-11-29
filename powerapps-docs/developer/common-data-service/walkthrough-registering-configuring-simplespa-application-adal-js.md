---
title: 'Tutorial: Registrar y configurar aplicación SimpleSPA con adal.js (Common Data Service para aplicaciones) | Microsoft Docs'
description: En este tutorial se describe el proceso para registrar y configurar la Aplicación de una sola página (SPA) más sencilla para tener acceso a los datos en Dynamics 365 Customer Engagement usando adal.js y Uso compartido de recursos de origen cruzado (CORS).
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: a327d2ff-e252-61cf-1190-6a974130ef19
author: paulliew
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="walkthrough-registering-and-configuring-a-spa-application-with-adaljs"></a>Tutorial: Registrar y configurar una aplicación SPA con adal.js

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-registering-configuring-simplespa-application-adal-js -->

En este tutorial se describe el proceso para registrar y configurar la Aplicación de una sola página (SPA) más sencilla para tener acceso a los datos en Dynamics 365 Common Data Service para aplicaciones usando adal.js y Uso compartido de recursos de origen cruzado (CORS). Más información: [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página a Dynamics 365 (online)](oauth-cross-origin-resource-sharing-connect-single-page-application.md).
  
## <a name="prerequisites"></a>Requisitos previos  
  
- Dynamics 365  
  
-   Debe tener una cuenta de usuario del sistema de Dynamics 365 (online) con el rol administrador para Office 365.  
  
-   Una suscripción de Azure para el registro de aplicaciones. Una cuenta de prueba también funcionará.  
  
- Visual Studio 2015  
  
<a name="bkmk_goal"></a>

## <a name="goal-of-this-walkthrough"></a>Objetivo de este tutorial

Al completar este tutorial podrá ejecutar una aplicación SPA sencilla en Visual Studio que proporcione la capacidad para que un usuario se autentique y recupere datos de Dynamics 365 (online). Esta aplicación consta de una sola página HTML.  

Cuando se depura la aplicación inicialmente solo habrá un botón **Iniciar sesión**.  

Haga clic en **Iniciar sesión** y pasará a una página de inicio de sesión para escribir sus credenciales.  

Tras escribir sus credenciales volverá a la página HTML donde encontrará que el botón **Iniciar sesión** está oculto y un botón **Cerrar sesión** y **Obtener cuentas** están visibles. También verá un saludo con información de su cuenta de usuario.  

Haga clic en el botón **Obtener cuentas** para recuperar 10 registros de cuenta de su organización de Dynamics 365. El botón **Obtener cuentas** está deshabilitado como se muestra en la captura de pantalla siguiente:  
  
![La página SimpleSPA](media/simple-spa.png "La página SimpleSPA")  

> [!NOTE]
>  La carga inicial de datos de Dynamics 365 puede ser lenta mientras se realizan las operaciones para permitir la autenticación, pero las operaciones posteriores son mucho más rápidas.  

Por último, puede hacer clic en el botón **Cerrar sesión** para cerrar la sesión.  

> [!NOTE]
>  Esta aplicación SPA no está diseñada para representar un modelo para desarrollar aplicaciones SPA robustas. Está simplificada para centrarse en el proceso de registrar y configurar la aplicación.  
  
### <a name="create-a-web-application-project"></a>Crear un proyecto de aplicación web  
  
1.  Usando Visual Studio 2015, cree un nuevo proyecto **Aplicación web ASP.NET** y use la plantilla **Vacío**. Puede dar el nombre que desee al proyecto.  
  
    Deberá poder usar versiones anteriores de Visual Studio también, pero estos pasos describirán el uso de Visual Studio 2015.  
  
2.  Agregue una nueva página HTML llamada SimpleSPA.html al proyecto y péguela en el siguiente código:  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
     <title>Simple SPA</title>  
     <meta charset="utf-8" />  
     <script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.0/js/adal.min.js"></script>  
     <script type="text/javascript">  
      "use strict";  
  
      //Set these variables to match your environment  
      var organizationURI = "https:// [organization name].crm.dynamics.com"; //The URL to connect to CRM (online)  
      var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
      var clientId = "[client id]"; //The ClientId you got when you registered the application  
      var pageUrl = "http://localhost: [PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
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
       cacheLocation: 'localStorage', // enable this for IE, as sessionStorage does not work for localhost.  
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
       retrievingAccountsMessage.textContent = "Retrieving 10 accounts from " + organizationURI + "/api/data/v8.0/accounts";  
       message.appendChild(retrievingAccountsMessage)  
  
       // Function to perform operation is passed as a parameter to the aquireToken method  
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
       req.open("GET", encodeURI(organizationURI + "/api/data/v8.0/accounts?$select=name,address1_city&$top=10"), true);  
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
  
3.  Establezca esta página como página de inicio para el proyecto  
  
4.  En las propiedades del proyecto, seleccione **Web** y en **Servidores** anote la **Dirección URL del proyecto**. Debe ser algo como `http://localhost:46575/`. Observe el número de puerto generado. Necesitará esto en el siguiente paso.  
  
5.  En la página SimpleSPA.html, busque las siguientes variables de configuración y establézcalas en consecuencia. Podrá establecer el `clientId` después de completar la parte siguiente de tutorial.  
  
    ```javascript  
    //Set these variables to match your environment  
    var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL to connect to CRM (online)  
    var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
    var clientId = "[client id]"; //The ClientId you got when you registered the application  
    var pageUrl = "http://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
    ```  
  
### <a name="register-the-application"></a>Registrar la aplicación  
  
1.  [Iniciar sesión](http://manage.windowsazure.com) en el portal de administración de Azure con una cuenta con permiso de administrador. Debe usar una cuenta en la misma suscripción de Office 365 (empresa) con la que pretenda registrar la aplicación. También puede obtener acceso al portal de Azure a través del centro de administración de Office 365 expandiendo el elemento **ADMIN** en el panel de navegación de la izquierda y seleccionando **Azure AD**.  
  
     Si no tiene un inquilino de Azure (cuenta) o tiene una pero su suscripción a Office 365 con Dynamics 365 (online) no está disponible en su suscripción de Azure, siga las instrucciones en el tema [Configurar acceso a Azure Active Directory para el sitio de desarrollador](https://docs.microsoft.com/en-us/office/developer-program/office-365-developer-program) para asociar las dos cuentas.  
  
     Si no tiene una cuenta, puede registrarse para obtener una cuenta utilizando una tarjeta de crédito. No obstante, la cuenta es gratuita para el registro de aplicaciones y no se cargará en su tarjeta de crédito si sigue los procedimientos indicados en este tema para registrar una o varias aplicaciones. Más información: [Detalles de precios de Active Directory](http://azure.microsoft.com/pricing/details/active-directory/)  
  
2.  Haga clic en **Active Directory** en la columna de la izquierda de la página. Es posible que deba desplazarse por la columna izquierda para ver el icono y la etiqueta de **Active Directory**.  
  
3.  Haga clic en el directorio de empresas que desee en la lista de directorio.  
  
    ![Lista de entradas de Active Directory disponibles](media/azure-active-directory.PNG "Lista de entradas de Active Directory disponibles")  
  
    Si el directorio de empresas de Azure no aparece en la lista de directorios, haga clic en **Agregar** y luego seleccione **Use el directorio existente** en el cuadro de diálogo. Siga las indicaciones e instrucciones proporcionados, y vuelva al paso 1.  
  
4.  Con el directorio de destino seleccionado, haga clic en **Aplicaciones** (cerca de la parte superior de la página) y, a continuación, haga clic en **Agregar**.  
  
5.  En el cuadro de diálogo **¿Qué desea hacer?**, haga clic en **Agregue una aplicación que mi organización está desarrollando**.  
  
6.  Cuando se le solicite, escriba el nombre de la aplicación, por ejemplo, ‘SimpleSPA’, elija un tipo: **Aplicación web y/o API web** y, a continuación, haga clic en la flecha derecha para continuar. Haga clic en un signo de interrogación **?** para obtener más información sobre los valores adecuados para cada campo de entrada.  
  
7.  Escriba la siguiente información:  
  
    **Dirección URL de inicio de sesión**  
    Se trata de la dirección URL a la que el usuario debe ser redirigido después de que inicie sesión. A efectos de depuración en Visual Studio debe ser `http://localhost:####/SimpleSPA.html` donde #### representa el número de puerto que obtuvo en el paso 4 del procedimiento **Crear un proyecto de aplicación web**.  
  
    **URI de Id. de la aplicación**  
    Debe ser un identificador único para la aplicación. Use `https://XXXX.onmicrosoft.com/SimpleSPA` donde XXXX es el inquilino de Active Directory.  
  
8.  Con la pestaña de la aplicación recién registrada seleccionada, haga clic en **Configurar**, busque **Id. de cliente** y cópielo.  
  
    Establezca la variable `clientId` en la página SimpleSPA.html con este valor. Consulte al paso 5 del procedimiento **Crear un proyecto de aplicación web**.  
  
9. Desplácese hasta la parte inferior de la página y haga clic en **Agregar aplicación**. En el cuadro de diálogo seleccione **Dynamics 365 Online** y cierre el cuadro de diálogo.  
  
10. En permisos para otras aplicaciones, encontrará una fila para **Dynamics 365 Online** y **Permisos delegados: 0**. Seleccione esto opción y agregue **Acceso a Dynamics 365 (online) como usuarios de la organización**.  
  
11. Guarde el registro de la aplicación  
  
12. En la parte inferior, seleccione **Administrar manifiesto** y elija **Descargar manifiesto**.  
  
13. Abra el archivo JSON que ha descargado y busque la línea: `"oauth2AllowImplicitFlow": false,` y cambie `false` a `true` y guarde el archivo.  
  
14. Vuelva a **Administrar manifiesto** de nuevo. Elija **Cargar manifiesto** y cargue el archivo JSON que acaba de guardar.  
  
### <a name="debugging-the-application"></a>Depurar la aplicación  
  
1.  Establezca el explorador para usar Microsoft Edge, Google Chrome, o Mozilla Firefox.  
  
    > [!NOTE]
    > Internet Explorer no funcionará para depuración en esta situación.  
  
2.  Pulse F5 para iniciar la depuración. Debe esperar el comportamiento descrito en [Objetivo de este tutorial](walkthrough-registering-configuring-simplespa-application-adal-js.md#bkmk_goal).  
  
     Si no obtiene los resultados deseados, compruebe dos veces los valores que estableció al registrar la aplicación y configurar el código SimpleSPA.html.  
  
### <a name="see-also"></a>Vea también  
 [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página a Dynamics 365 (online)](oauth-cross-origin-resource-sharing-connect-single-page-application.md)