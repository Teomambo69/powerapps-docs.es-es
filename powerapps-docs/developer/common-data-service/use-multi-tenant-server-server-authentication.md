---
title: Usar autenticación multiempresa entre servidores (Common Data Service para aplicaciones) | Microsoft Docs
description: Describe cómo configurar un usuario de la aplicación para la autenticación entre servidores con Common Data Service para aplicaciones.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
# <a name="use-multi-tenant-server-to-server-authentication"></a>Usar autenticación multiempresa entre servidores

Es el escenario más común y el que se usa para las aplicaciones distribuidas con Microsoft AppSource, pero también puede usar multiempresa sin enumerar su aplicación con Microsoft AppSource.  
  
Cada CDS para aplicaciones está asociado a un inquilino de Azure Active Directory. Su aplicación o servicio web se registra con su propio inquilino de Azure AD.  
  
En este escenario cualquier inquilino de CDS para aplicaciones puede usar potencialmente la aplicación multiempresa después de conceder consentimiento para que la aplicación acceda a los datos.  
  
<a name="bkmk_Requirements"></a>   

## <a name="requirements"></a>Requisitos  

 Para crear y probar una aplicación multiempresa que usa autenticación entre servidores (S2S) necesitará:  
  
- Un inquilino de Azure AD que usará para publicar la aplicación o el servicio.  
  
- 2 suscripciones a CDS para aplicaciones  
  
  -   Una debe asociarse con el inquilino de Azure AD que usará para publicar la aplicación o el servicio.  
  
  -   La otra puede ser una suscripción de prueba para usar para comprobar cómo un suscriptor tendrá acceso a la aplicación.  
  
<a name="bkmk_DevelopAndTest"></a>  
 
## <a name="overview-develop-and-test-your-application"></a>Información general: Desarrolle y pruebe su aplicación  

 La aplicación que creará se debe registrar con el inquilino de Azure AD que usará cuando publique la aplicación.  
  
 En un nivel alto, el proceso consistirá en:  
  
1. Crear una aplicación web multiempresa registrada con el inquilino de Azure AD.  
  
2. Crear un usuario de la aplicación asociado con la aplicación registrada en el inquilino de CDS para aplicaciones  
  
3. Crear un rol de seguridad personalizado y asignarlo al usuario de la aplicación en su inquilino de CDS para aplicaciones  
  
4. Probar la aplicación con el inquilino de CDS para aplicaciones  
  
5. Probar la aplicación con un inquilino de CDS para aplicaciones distinto  
  
   Para ver un ejemplo completo de este proceso, consulte [Tutorial: Autenticación multiempresa entre servidores](/dynamics365/customer-engagement/developer/walkthrough-multi-tenant-server-server-authentication).  
  
<a name="bkmk_CreateAMultitenantWebApp"></a>
   
## <a name="create-a-multi-tenant-web-application-registered-with-your-azure-ad-tenant"></a>Crear una aplicación web multiempresa registrada con el inquilino de Azure AD 
 
 Debe crear una aplicación o servicio web multiempresa que use Azure AD como proveedor de autenticación.  
  
 Este tema no se centrará la manera exacta de hacer esto. Existen varias opciones posibles para abordar esto y realizar selecciones que se ajusten a sus requisitos o sus preferencias. Consulte los siguientes vínculos para obtener más información y ejemplos:  
  
- [Crear una aplicación web SaaS multiempresa mediante Azure AD &amp; OpenID Connect](https://azure.microsoft.com/en-us/documentation/samples/active-directory-dotnet-webapp-multitenant-openidconnect/)  
  
- [Crear una aplicación web SaaS multiempresa que llame a la API web utilizando Azure AD](https://azure.microsoft.com/en-us/documentation/samples/active-directory-webapp-webapi-multitenant-openidconnect-aspnetcore/)  
  
  Azure AD requiere los siguientes valores para registrar la aplicación:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**URI de Id. de aplicación**|El identificador para una aplicación. Este valor se envía a Azure AD durante la autenticación para indicar para qué aplicación desea un símbolo el autor de la llamada. Además, este valor se incluye en el símbolo para que la aplicación sepa que era el destino deseado.|  
|**Dirección URL de respuesta y URI de redireccionamiento**|En el caso de una API web o una aplicación web, la dirección URL de respuesta es la ubicación a la que Azure AD enviará la respuesta de autenticación, incluido un símbolo si la autenticación se realizó correctamente.|  
|**Id. de cliente**|El identificador para una aplicación, que es generado por Azure AD cuando se registra la aplicación. Al solicitar un símbolo o código de autorización, el identificador y la clave de cliente se envían a Azure AD durante la autenticación.|  
|**Clave**|La clave que se envía junto con un Id. de cliente al autenticar en Azure AD para llamar a una API web.|  
  
 Cuando se registra la aplicación se le asignará un **Id. de objeto de Azure Active Directory**, un identificador único para la aplicación registrada.  
  
 Si crea una nueva aplicación ASP.NET MVC con Visual Studio tendrá opciones para especificar que la aplicación admitirá la funcionalidad multiempresa. La plantilla para una aplicación MVC proporciona la opción de especificar el tipo de autenticación que aparece. Tendrá la opción de elegir el método de autenticación configurando las propiedades del proyecto cuando lo cree. En el siguiente diagrama se muestran las opciones disponibles:  
  
 ![Diálogo Cambiar autenticación MVC de ASP.NET](media/mvc-change-authentication-dialog.png "Diálogo Cambiar autenticación MVC de ASP.NET")  
  
 Cuando se configura un proyecto con estas opciones se configurará para usar el software intermedio y el andamio de OWIN para una aplicación básica que admita este escenario. Con unas modificaciones básicas puede ser adaptado para funcionar con CDS para aplicaciones. Este es el método demostrado en [Tutorial: Autenticación multiempresa entre servidores](/dynamics365/customer-engagement/developer/walkthrough-multi-tenant-server-server-authentication).  
  
 En el proceso de crear y registrar la aplicación para desarrollo probablemente usará `http://localhost` como valores de **Dirección URL de inicio de sesión** y **Dirección URL de respuesta** para que pueda probar y depurar su aplicación localmente antes de publicarla. Necesitará cambiar estos valores antes de publicar la aplicación.  
  
 Cuando registre la aplicación debe generar una clave, también denominada `ClientSecret`. Estas claves se pueden configurar para una duración de 1 ó 2 años. Como host de la aplicación debe tratar este valor como una contraseña y es su responsabilidad administrar la renovación de las claves antes de que expiren. La conviene utilizar Key Vault. Más información: [https://azure.microsoft.com/en-us/services/key-vault/](https://azure.microsoft.com/en-us/services/key-vault/)  
  
<a name="bkmk_GrantApplicationRights"></a>
   
## <a name="grant-your-application-rights-to-access-cds-for-apps-data"></a>Conceda a la aplicación derechos para tener acceso a los datos de CDS para aplicaciones
  
 Ésta es la razón por la que su instancia de CDS para aplicaciones debe estar asociada al inquilino de Azure AD. Si el inquilino de Azure AD no está asociado con un inquilino de CDS para aplicaciones, no podrá realizar los pasos siguientes.  
  
1. Vaya a [https://portal.azure.com](https://portal.azure.com) y seleccione **Azure Active Directory**.  
  
2. Haga clic en **Registros de la aplicación** y busque la aplicación que ha creado mediante Visual Studio.  
  
3. Debe proporcionar los privilegios de la aplicación para tener acceso a los datos de CDS para aplicaciones. En el área **Acceso de API** haga clic en **Permisos requeridos**. Debe ver que ya tiene permisos para **Windows Azure Active Directory**.  
  
4. Haga clic en **Agregar** y, a continuación, en **Seleccionar una API**. En la lista, seleccione **Dynamics 365** y luego haga clic en el botón **Seleccionar**.  
  
5. En **Seleccionar permisos**, seleccione **Acceso a Dynamics 365 como usuarios de la organización**. A continuación, haga clic en el botón **Seleccionar**.  
  
6. Haga clic en **Hecho** para agregar estos permisos. Cuando finalice deberá ver los permisos aplicados.  
  
   ![Conceder permisos de Dynamics 365 a la aplicación](media/grant-crm-permissions-to-application.png "Conceder permisos de Dynamics 365 a la aplicación")  
  
<a name="bkmk_CreateAppUser"></a>
   
## <a name="create-an-application-user--associated-with-the-registered-application--in-cds-for-apps"></a>Crear un usuario de la aplicación asociado con la aplicación registrada en CDS para aplicaciones  
 Cuando su aplicación tiene acceso a los datos de CDS para aplicaciones de uno de los suscriptores de su aplicación, necesitará un usuario de la aplicación en la organización de CDS para aplicaciones del suscriptor. Como cualquier usuario de CDS para aplicaciones, este usuario de la aplicación debe estar asociado al menos a un rol de seguridad que defina los datos a los que el usuario tiene acceso.  
  
 La [entidad SystemUser](reference/entities/systemuser.md) tiene tres nuevos atributos para almacenar estos datos.  
  
|Nombre del esquema|Nombre|Tipo|Descripción|  
|-----------------|------------------|----------|-----------------|  
|[ApplicationId](reference/entities/systemuser.md#BKMK_ApplicationId)|**Id. de aplicación**|UniqueIdentifierType|El identificador para la aplicación. Se usa para tener acceso a los datos en otra aplicación.|  
|[ApplicationIdUri](reference/entities/systemuser.md#BKMK_ApplicationIdUri)|**URI de Id. de aplicación**|StringType|El URI usado como identificador lógico único para la aplicación externa. Se puede usar para validar la aplicación|  
|[AzureActiveDirectoryObjectId](reference/entities/systemuser.md#BKMK_AzureActiveDirectoryObjectId)|**Id. de objeto de Azure AD**|UniqueIdentifierType|Es el Id. de objeto del directorio de la aplicación|  
  
 Este valor de la propiedad `systemuser``AzureActiveDirectoryObjectId` debe ser una referencia al Id. de objeto de Azure Active Directory de la aplicación registrada. Esta referencia se establecerá en CDS para aplicaciones cuando se crea el usuario de la aplicación basándose en el valor de `ApplicationId`.  
  
> [!NOTE]
>  Cuando está desarrollando inicialmente la aplicación con su propio inquilino de CDS para aplicaciones y el inquilino de Azure AD asociado con él, puede crear simplemente el usuario de la aplicación porque la aplicación registrada ya forma parte del inquilino de Azure AD.  
> 
>  Sin embargo, para crear el usuario de la aplicación en otra organización para probar, o cuando un suscriptor usará su aplicación, primero deben conceder consentimiento para su aplicación, por lo que los pasos del proceso son diferentes. Para obtener más información, consulte [Probar la aplicación mediante un inquilino de Dynamics 365 independiente](#bkmk_TestUsingSeparateTenant).  
  
<a name="bkmk_CreateSecurityRole"></a>  
 
### <a name="create-a-security-role-for-the-application-user"></a>Crear un rol de seguridad para el usuario de la aplicación  

 En el siguiente paso creará un usuario de la aplicación de CDS para aplicaciones. Los privilegios y derechos de acceso para este usuario serán definidos por un rol de seguridad personalizado que establezca. Antes de crear el usuario de la aplicación, debe crear un rol de seguridad personalizado para poder asociar el usuario con él. Más información: [Creación o edición de roles de seguridad](https://technet.microsoft.com/library/dn531130.aspx)  
  
> [!NOTE]
>  El usuario de la aplicación no puede estar asociado con uno de los roles de seguridad de CDS para aplicaciones predeterminados. Debe crear un rol de seguridad personalizado para asociar con el usuario de la aplicación.  
  
<a name="bkmk_ManuallyCreateUser"></a>   

### <a name="manually-create-a-cds-for-apps-application-user"></a>Cree manualmente un usuario de aplicación de CDS para aplicaciones  

 El procedimiento para crear este usuario es diferente de crear un usuario con licencia. Lleve a cabo los pasos siguientes:  
  
1. Vaya a **Configuración** > **Seguridad** > **Usuarios**  
  
2. En la lista desplegable de vistas, seleccione **Usuarios de la aplicación**.  
  
3. Haga clic en **Nuevo**. A continuación compruebe que está usando el formulario **Usuario de la aplicación**.  
  
    Si no ve los campos **Identificador de la aplicación**, **URI del Id. la aplicación** e **Id. del objeto de Azure AD** en el formulario, debe seleccionar el formulario **Usuario de la aplicación** de la lista:  
  
   ![Seleccionar formulario de usuario de la aplicación](media/select-application-user-form.PNG "Seleccionar formulario de usuario de la aplicación")  
  
4. Agregue los valores correspondientes a los campos:  
  
   |Campo|Value|  
   |-----------|-----------|  
   |**Id. de aplicación**|El valor del Id. de la aplicación para la aplicación registrada con Azure AD.|  
   |**Nombre completo**|Nombre de la aplicación.|  
   |**Correo electrónico principal**|La dirección de correo electrónico que desea que usen los suscriptores para contactarle.|  
  
    Los campos **Nombre de usuario**, **URI del Id. de la aplicación** e **Id. del objeto de Azure AD** están bloqueados y no puede establecer los valores para estos campos.  
  
    Cuando crea un este usuario los valores de estos campos se recuperarán de Azure AD en función del valor de **Identificador de la aplicación** al guardar el usuario.  
  
5. Asociar el usuario de la aplicación al rol de seguridad personalizado que creó en [Crear un rol de seguridad para el usuario de la aplicación](#bkmk_CreateSecurityRole). Más información: [Crear usuarios en Dynamics 365 (online) y asignar roles de seguridad](/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles)  
  
<a name="bkmk_TestUsingYourTenant"></a>  
 
## <a name="test-your-application-using-your-cds-for-apps-tenant"></a>Probar la aplicación con el inquilino de CDS para aplicaciones 
 
 Puesto que la aplicación se ha registrado con el inquilino de Azure AD y el usuario de la aplicación en su organización de desarrollo ya está configurado, puede continuar desarrollando su aplicación con su propio inquilino de CDS para aplicaciones. Pero esto no es una prueba válida de la capacidad multiempresa. Debe probar la aplicación con un inquilino de CDS para aplicaciones distinto.  
  
<a name="bkmk_TestUsingSeparateTenant"></a>   

## <a name="test-your-application-using-a-separate-cds-for-apps-tenant"></a>Probar la aplicación con un inquilino de CDS para aplicaciones distinto  

 Antes de probar su aplicación con un inquilino de CDS para aplicaciones aparte, un administrador para el inquilino de Azure AD debe conceder consentimiento para la aplicación. El administrador concede consentimiento navegando a la aplicación con un explorador. La primera vez que tiene acceso a la aplicación, verá un diálogo como éste:  
  
 ![Conceder consentimiento para acceder a datos de Dynamics 365](media/grant-consent-to-access-crm-data.PNG "Conceder consentimiento para acceder a datos de Dynamics 365")  
  
 Cuando concede consentimiento, su aplicación registrada se agregará a la lista de aplicaciones de Azure AD Enterprise y está disponible para los usuarios del inquilino de Azure AD.  
  
 Solo después de que un administrador haya concedido consentimiento, debe crear el usuario de la aplicación en el inquilino de CDS para aplicaciones del suscriptor. Puede crear manualmente el usuario de la aplicación mediante los pasos que se describen en [Crear manualmente un usuario de la aplicación de Dynamics 365](#bkmk_ManuallyCreateUser).  
  
 Para las pruebas iniciales es posible que desee realizar manualmente estos pasos. Cuando esté listo para poner su aplicación o servicio disponible para suscriptores necesitará un procedimiento más eficiente. Esto se cubre en la siguiente sección.  
  
<a name="bkmk_PrepareMethodToDeployAppUser"></a>
   
## <a name="prepare-a-method-to-deploy-the-application-user"></a>Preparar un método para implementar el usuario de la aplicación  

 Después de que los suscriptores concedan su consentimiento a la aplicación o servicio necesitará una forma fácil y fiable para que agreguen el usuario de la aplicación y cualquier otro componente requerido a su organización de CDS para aplicaciones.  
  
 Debe incluir un rol de seguridad personalizado que defina qué privilegios requiere su aplicación y después asegurarse de que el usuario de la aplicación está asociado con ese rol de seguridad personalizado. Dado que un rol de seguridad personalizado se puede incluir en una solución, debe preparar una solución administrada que contiene la definición del rol de seguridad personalizado y cualquier otro componente de la solución que requiera su aplicación.  
  
 Para obtener información sobre la creación de roles de seguridad personalizados, vea  
  
- [Creación o edición de roles de seguridad](/dynamics365/customer-engagement/admin/create-edit-security-role)  
- [Copia de roles de seguridad](/dynamics365/customer-engagement/admin/copy-security-role)  
- [Agregar componentes de la solución](/dynamics365/customer-engagement/customize/create-solution.md#add-solution-components)
  
  Para obtener información sobre la creación de una solución de CDS para aplicaciones, vea los temas siguientes:
  
- [Usar soluciones para las personalizaciones](../../maker/common-data-service/use-solutions-for-your-customizations.md)  
- [Empaquetar y distribuir las extensiones con soluciones](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)  
  
  Sin embargo, el usuario de la aplicación no se puede incluir con una solución, por lo que deberá proporcionar una forma de crear este usuario de la aplicación y asociarlo con el rol de seguridad personalizado.  
  
  Existen varias formas de conseguirlo, incluida la escritura de su propio programa mediante los servicios web y haciendo que el suscriptor ejecute el programa.  
  
  El Dynamics 365 Package Deployer es una aplicación que se puede usar para preparar un paquete para automatizar la transferencia de soluciones y datos a otra organización de CDS para aplicaciones. Más información: [Crear paquetes para Dynamics 365 Package Deployer](/dynamics365/customer-engagement/developer/create-packages-package-deployer)  
  
### <a name="see-also"></a>Vea también  
 [Tutorial: Autenticación multiempresa entre servidores](/dynamics365/customer-engagement/developer/walkthrough-multi-tenant-server-server-authentication)   
 [Usar autenticación entre servidores de una sola empresa](use-single-tenant-server-server-authentication.md)   
 [Crear aplicaciones web mediante autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md)   
 [Conectar con Dynamics 365](/dynamics365/customer-engagement/developer/connect-customer-engagement)
