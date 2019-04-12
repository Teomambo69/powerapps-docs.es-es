---
title: 'Tutorial: Registrar una aplicación con Azure Active Directory (Common Data Service) | Microsoft Docs'
description: 'Este tutorial describe cómo registrar una aplicación con Azure Active Directory de modo que puede conectarse al entorno de Common Data Service, autenticarse mediante OAuth y obtener acceso a los servicios web.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 86c4a8a8-7401-6d75-7979-3b04b506eb0c
author: paulliew
ms.author: jdaly
manager: ryjones
ms.reviewer: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="walkthrough-register-an-app-with-azure-active-directory"></a>Tutorial: Registrar una aplicación con Azure Active Directory

Este tutorial describe cómo registrar una aplicación con Azure Active Directory, lo que permite a un usuario con cuenta de usuario de PowerApps conectarse a su entorno de Common Data Service de las aplicaciones del cliente externo mediante la autenticación de OAuth.

> [!IMPORTANT]
> PowerApps también proporciona la opción de autenticación entre servidores (S2S) para conectarse al entorno de Common Data Service desde aplicaciones y servicios externos mediante la cuenta usuario de la aplicación especial. La autenticación S2S es la forma común que las aplicaciones registradas en Microsoft AppSource usan para tener acceso a los datos de sus suscriptores. Más información:. Más información: [Crear aplicaciones web mediante la autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md).


Normalmente el registro de aplicaciones en Azure Active Directory se hace mediante ISV que desean desarrollar aplicaciones cliente externas para leer y escribir datos en Common Data Service. Si registra una aplicación en Azure Active Directory obtendrá valores de **identificador de aplicación** y de **URI de redirección** que los ISV pueden usar en su código de autenticación de la aplicación cliente. Cuando los usuarios finales utilizan la aplicación de ISV por *primera vez* para conectarse a su entorno de Common Data Service proporcionando sus credenciales de Common Data Service, se muestra un formulario de consentimiento al usuario final. Después de dar su consentimiento para utilizar su cuenta de Common Data Service con la aplicación del ISV, los usuarios finales pueden conectarse al entorno de Common Data Service desde la aplicación externa. El formulario de consentimiento no se vuelve a mostrar a otros usuarios después del primer usuario que ya ha dado su consentimiento a usar la aplicación del ISV. Las aplicaciones registradas en Azure Active Directory son multiinquilino, lo que indica que otros usuarios de Common Data Service de otros inquilinos pueden conectarse a su entorno mediante aplicaciones de ISV. 

El registro de la aplicación también lo puede hacer un desarrollador de aplicaciones o un usuario individual que esté creando una aplicación cliente para conectarse a Customer Engagement y leer y escribir datos en Common Data Service. Utilice los valores de **identificador de aplicación** y **URI de redirección** de la aplicación registrada en el código de autenticación de su aplicación cliente para conectarse al entorno de Common Data Service desde la aplicación cliente y llevar a cabo las operaciones necesarias. Tenga en cuenta que si la aplicación está registrada en el mismo inquilino que el entorno de Common Data Service, no se le presentará un formulario de consentimiento cuando se conecte desde la aplicación cliente al entorno de Common Data Service.

## <a name="prerequisites"></a>Requisitos previos  
-   El usuario que se registra la aplicación debe tener una cuenta de usuario con el rol de seguridad de administrador del sistema y el rol de administrador global para la suscripción de Office 365.  
  
-   Una suscripción de Azure para el registro de aplicaciones. Una cuenta de prueba también funcionará.  
  
    

## <a name="create-an-application-registration"></a>Crear un registro de la aplicación 
  
1.  [Iniciar sesión](http://manage.windowsazure.com) en el portal de administración de Azure con una cuenta con permiso de administrador. Debe usar una cuenta en la misma suscripción de Office 365 (empresa) con la que pretenda registrar la aplicación.<br><br> También puede obtener acceso al portal de administración de Azure a través del [centro de administración](https://admin.microsoft.com/adminportal) de Office 365 expandiendo el elemento **Centros de administración** en el panel de navegación de la izquierda y seleccionando **Azure AD**.  
  
    > [!NOTE]
    > Si no tiene un inquilino de Azure (cuenta) o tiene una pero su suscripción a Office 365 con Dynamics 365 (online) no está disponible en su suscripción de Azure, siga las instrucciones en el tema [Configurar acceso a Azure Active Directory para el sitio de desarrollador](https://docs.microsoft.com/office/developer-program/office-365-developer-program) para asociar las dos cuentas.<br><br> Si no tiene una cuenta, puede registrarse para obtener una cuenta utilizando una tarjeta de crédito. No obstante, la cuenta es gratuita para el registro de aplicaciones y no se cargará en su tarjeta de crédito si sigue los procedimientos indicados en este tema para registrar una o varias aplicaciones. Más información: [Detalles de precios de Active Directory](http://azure.microsoft.com/pricing/details/active-directory/)  
  
1. En el portal de administración de Azure, siga los pasos tal como se explica en la sección [agregar una aplicación](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#adding-an-application) de la Guía de desarrolladores de Azure Active Directory para crear una aplicación. 
  
1. Al crear una aplicación de Azure Active Directory, se genera un único **identificador de aplicación** (anteriormente denominado **identificador de cliente**) para la aplicación, y la aplicación recién registrada aparece en la página de aplicaciones registradas. Haga clic en la aplicación para abrir la página de información de la aplicación.

1. En la página de información de la aplicación, mantenga el mouse sobre el valor de **identificador de aplicación** (anteriormente denominado **Id. de cliente**) y seleccione el icono **Hacer clic para copiar** para copiar el valor ya que deberá especificarlo en el código de autenticación de la aplicación o el archivo app.config si procede.

    ![Copie el identificador de aplicación](media/Azure-copy-app-id.png "Copie el identificador de aplicación")
  
1. Seleccione **configuración** en la página de información de la aplicación y utilice la opción **URI de redirección** de la página **Configuración** para copiar el valor de la URI de redirección de la aplicación. También puede cambiar y agregar URI adicionales si es necesario. Para una aplicación del tipo **aplicaciones Web o API** se muestra la opción **direcciones URL de respuesta** en lugar de la opción **URI de redirección**.

## <a name="apply-permissions"></a>Aplicar permisos

1. En la página **configuración**, seleccione **permisos requeridos** > **agregar** para agregar permisos para la aplicación registrada.

    ![Agregar permiso de aplicaciones](media/Azure-add-app-permission.png "agregar permiso de aplicaciones")
  
1. En la página **agregar acceso de API**:
    - Seleccione **Seleccionar una API** > **Dynamics CRM Online** y haga clic en **seleccionar**.

      ![Agregar permiso de aplicaciones](media/Azure-add-api-access.png "agregar permiso de aplicaciones")  
   
    - Seleccione **seleccionar permisos** > **Acceso a CRM Online como usuarios de la organización**y haga clic en **Seleccionar**.
  
      ![Agregar permiso delegado](media/azure-add-permission.PNG "agregar permiso delegado")  

    - Seleccione **listo** para agregar el permiso delegado a la aplicación registrada.

Esto completa el registro de la aplicación en Azure Active Directory.

## <a name="additional-configuration-options"></a>Opciones de configuración adicionales

Si su aplicación será una aplicación de una sola página (SPA) que depende de CROS debe configurar el registro de la aplicación para admitir el flujo implícito. Más información: [Tutorial: Registrar y configurar una aplicación SPA con adal.js](walkthrough-registering-configuring-simplespa-application-adal-js.md)

Si su aplicación es compatible con conexiones entre servidores, consulte [Usar autenticación multiinquilino entre servidores](use-multi-tenant-server-server-authentication.md)

  
### <a name="see-also"></a>Vea también  
 [Registrar una aplicación en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)    
 [Autenticar usuarios con los servicios web de Dynamics 365](authentication.md)