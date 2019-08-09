---
title: Usar autenticación entre servidores de una sola empresa (Common Data Service) | Microsoft Docs
description: Describe cómo acceder a los datos de D365 desde otra aplicación o servicio sin autenticación explícita de usuario.
ms.custom: ''
ms.date: 2/21/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-single-tenant-server-to-server-authentication"></a>Usar autenticación entre servidores de una sola empresa

El escenario entre servidores de una sola empresa suele aplicarse a organizaciones empresariales que tienen varios entornos de Common Data Service utilizando Servicios de federación de Active Directory (AD FS) para autenticación. Sin embargo, también lo pueden aplicar entornos cuando la aplicación no se distribuirá a otros entornos.  
  
 Una empresa puede crear una aplicación web o servicio para conectarse a cualquier entorno Common Data Service asociado con un único inquilino de Azure Active Directory (AD).
  
## <a name="differences-from-multi-tenant-scenario"></a>Diferencias con el escenario multiempresa  
 Crear una aplicación o un servicio web para autenticación entre servidores de una sola empresa es similar a lo que se usa para una organización multiempresa, aunque hay algunas diferencias importantes.  
  
-   Puesto que todas las organizaciones se encuentran en la misma empresa, no es necesario que un administrador de inquilinos conceda consentimiento para cada organización. La aplicación se registra simplemente una vez para el inquilino.
  
-   Tiene la posibilidad de usar certificados en lugar de claves si lo prefiere. 

En la sección [Vea también](#bkmk_seealso) al final de este artículo, hay vínculos a información sobre actualizar una aplicación de un solo inquilino a multiinquilino.  

<a name="bkmk_Requirements"></a>
## <a name="requirements"></a>Requisitos  

 Para crear y probar una aplicación de un solo inquilino que usa autenticación entre servidores (S2S) necesitará:  
  
- Un inquilino de Azure AD para usar el registrar la aplicación de ejemplo suministrada.
- Una suscripción de Common Data Service que está asociada con el inquilino de Azure AD.
- Privilegios de administrador en el inquilino de Azure AD y la organización de D365.

<a name="bkmk_registration"></a>
## <a name="azure-application-registration"></a>Registro de la aplicación de Azure
Para crear un registro de la aplicación en Azure AD, siga estos pasos.

1. Navegue a https://admin.microsoft.com e inicie sesión, desde la página web de su organización D365 seleccione el iniciador de la aplicación en la esquina superior izquierda.
2. Elija **Administración** > **Centros de administración** > **Azure Active Directory**
3. En el panel izquierdo, elija **Azure Active Directory** > **Registros de la aplicación (vista previa)**
4. Elija **+ Nuevo registro imagen**
5. En el formulario **Registrar una aplicación** proporcione un nombre para la aplicación, seleccione **Cuentas en este directorio de organización solo**, y elija **Registro**. El URI de redirección no es necesario para este tutorial y el código de ejemplo proporcionado.<br /> ![Registrar un formulario de aplicación](media/S2S-app-registration-started.PNG)
6. En la página **Información general**, seleccione **Permisos de API** <br >![Permisos de registro de aplicación](media/S2S-app-registration-completed.PNG)
7. Elija **+ Agregar un permiso**
8. En la pestaña **API de Microsoft**, elija **Dynamics CRM**
9. En el formulario **Solicitar permiso de API**, seleccione **Permisos delegados**, active **user_impersonation** y seleccione **Agregar permisos** <br />![Establecer permisos de API](media/S2S-api-permission-started.PNG)
10. En la página **Permisos de API** bajo **Conceder permiso**, seleccione **Conceder consentimiento de administrador para “nombre de organización”** y cuando se le solicite elija **Sí** <br />![Conceder permisos de API](media/S2S-api-permission-completed.PNG)
11. Seleccione **Información general** en el panel de navegación, registre los valores de **Nombre para mostrar**, **Identificador de la aplicación** e **Identificador del directorio** del registro de la aplicación. Proporcionará estos más adelante en el ejemplo de código.
12. En el panel de navegación, seleccione **Certificados y secretos**
13. Debajo **Secretos de cliente**, elija **+ Nuevo secreto de cliente** para crear un secreto
14. En el formulario, escriba una descripción y seleccione **Agregar**. Registrar la cadena de secreto. No podrá ver el secretos cuando salga de la pantalla actual.

<a name="bkmk_appuser"></a>
## <a name="application-user-creation"></a>Creación de usuario de la aplicación
Para crear un “usuario de la aplicación” sin licencia en su organización de Dynamics 365, siga estos pasos. Este usuario de la aplicación recibirá acceso a los datos de la organización en nombre del usuario final que usa su aplicación.

1. Acceda al centro de administración de Azure Active Directory
2. En el panel izquierdo de navegación, elija **Usuarios**
3. Seleccione **+ Nuevo usuario**
4. En el formulario **Usuario**, escriba un nombre y un nombre de usuario del nuevo usuario y seleccione **Crear**. Asegúrese de que el nombre de usuario contiene la dirección URL del dominio de la organización del inquilino D365 (es decir, someuser@myorg.onmicrosoft.com). Ahora puede salir de Azure AD.
5. Navegue hasta su organización de D365.
6. Vaya a **Configuración** > **Seguridad** > **Usuarios**
7. Elija **Usuarios de la aplicación** en el filtro de la vista
8. Seleccione **+ Nuevo**
9. En el formulario **Nuevo usuario**, especifique la información necesaria. Estos valores deben ser idénticos a los valores para el nuevo usuario creado en el inquilino de Azure. <br />![Nuevo usuario de aplicación](media/S2S-new-appuser.PNG)
10. Si va todo bien, después de seleccionar **GUARDAR**, los campos **URI de Id. de aplicación** e **Id. de objeto de Azure AD** se rellenarán automáticamente con la configuración correcta
11. Antes de salir del formulario de usuario, elija **ADMINISTRAR ROLES** y asigne un rol de seguridad a este usuario de la aplicación de modo que el usuario de la aplicación pueda obtener acceso a los datos deseados de la organización.

> [!IMPORTANT]
> Cuando se desarrolla una aplicación real con S2S, debe usar un rol de seguridad personalizado que se pueda almacenar en una solución y distribuir junto con la aplicación.

<a name="bkmk_coding"></a>
## <a name="application-coding-and-execution"></a>Codificación y ejecución de la aplicación

Siga estos pasos para descargar, crear, y ejecutar la aplicación de ejemplo. El ejemplo llama a la WebAPI para devolver una lista de las cuentas 3 principales (por nombre) en la organización.

1. Descargue el [ejemplo](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/SingleTenantS2S) de Visual Studio 2017 SingleTenantS2S
2. Actualice el archivo App.config con los valores de registro de la aplicación y la clave del servidor.
3. Genere y ejecute la aplicación.

### <a name="expected-results"></a>Resultados esperados
Una respuesta de OData que muestra una lista de los nombres de las cuentas 3 principales de la organización D365.

### <a name="example-console-output"></a>Salida de la consola de ejemplo
A continuación se muestra una consola de ejemplo obtenida de una organización D365 que sólo tenía dos cuentas llamadas “Cuenta de prueba 1" y “Cuenta de prueba 2".

```json
{
"@odata.context":"https://crmue2.api.crm.dynamics.com/api/data/v9.1/$metadata#accounts(name)",
"@Microsoft.Dynamics.CRM.totalrecordcount":-1,
"@Microsoft.Dynamics.CRM.totalrecordcountlimitexceeded":false,

"value":[
{"@odata.etag":"W/\"4648334\"","name":"Test Account 1","accountid":"28630624-cac9-e811-a964-000d3a3ac063"},
{"@odata.etag":"W/\"4648337\"","name":"Test Account 2","accountid":"543fd72a-cac9-e811-a964-000d3a3ac063"}]
}
```

<a name="bkmk_seealso"></a>

### <a name="see-also"></a>Vea también

[Usar autenticación multiempresa entre servidores](use-multi-tenant-server-server-authentication.md)   
[Crear aplicaciones web mediante autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md)  
[Cómo: Iniciar sesión en cualquier usuario de Azure Active Directory mediante el patrón de la aplicación multiempresa](https://docs.microsoft.com/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant)
