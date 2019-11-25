---
title: 'Tutorial: Registrar una aplicación con Azure Active Directory (Common Data Service) | Microsoft Docs'
description: Este tutorial describe cómo registrar una aplicación con Azure Active Directory de modo que puede conectarse en el entorno de Common Data Service, autenticarse mediante OAuth y obtener acceso a los servicios web.
keywords: ''
ms.date: 04/01/2019
ms.service: powerapps
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
ms.openlocfilehash: 79773316bd5ff4e6d2652e7dfae53add0a782dc3
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749769"
---
# <a name="walkthrough-register-an-app-with-azure-active-directory"></a>Tutorial: Registrar una aplicación con Azure Active Directory

Este tutorial describe cómo registrar una aplicación con Azure Active Directory, lo que permite a un usuario con cuenta de usuario de PowerApps conectarse a su entorno de Common Data Service desde aplicaciones de cliente externo mediante la autenticación de OAuth.

> [!IMPORTANT]
> PowerApps también proporciona la opción de autenticación entre servidores (S2S) para conectarse al entorno de Common Data Service desde aplicaciones y servicios externos mediante la cuenta usuario de la aplicación especial. La autenticación S2S es la forma común que las aplicaciones registradas en Microsoft AppSource usan para tener acceso a los datos de sus suscriptores. Más información: [Crear aplicaciones web mediante la autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md).

Normalmente el registro de aplicaciones en Azure Active Directory se hace mediante ISV que desean desarrollar aplicaciones cliente externas para leer y escribir datos en Common Data Service. Si registra una aplicación en Azure Active Directory obtendrá valores de **identificador de aplicación** y de **URI de redirección** que los ISV pueden usar en su código de autenticación de la aplicación cliente. Cuando los usuarios finales utilizan la aplicación de ISV por *primera vez* para conectarse a su entorno de Common Data Service proporcionando sus credenciales de Common Data Service, se muestra un formulario de consentimiento al usuario final. Después de autorizar el uso de su cuenta de Common Data Service con la aplicación del ISV, los usuarios finales pueden conectarse al entorno de Common Data Service desde la aplicación externa. El formulario de consentimiento no se vuelve a mostrar a otros usuarios después del primer usuario que ya ha dado su consentimiento a usar la aplicación del ISV. Las aplicaciones registradas en Azure Active Directory son multiinquilino, lo que indica que otros usuarios de Common Data Service de otros inquilinos pueden conectarse a su entorno mediante aplicaciones de ISV. 

El registro de la aplicación también lo puede hacer un desarrollador de aplicaciones o un usuario individual que esté creando una aplicación cliente para conectarse a Customer Engagement y leer y escribir datos en Common Data Service. Utilice los valores de **identificador de aplicación** y **URI de redirección de la aplicación** registrada en el código de autenticación de su aplicación cliente para conectarse al entorno de Common Data Service desde la aplicación cliente y llevar a cabo las operaciones necesarias. Tenga en cuenta que si la aplicación está registrada en el mismo inquilino que el entorno de Common Data Service, no se le presentará un formulario de consentimiento cuando se conecte desde la aplicación cliente al entorno de Common Data Service.

## <a name="prerequisites"></a>Requisitos previos  

-   El usuario que se registra la aplicación debe tener una cuenta de usuario con el rol de seguridad de administrador del sistema y el rol de administrador global para la suscripción Office 365.  
  
-   Una suscripción de Azure para el registro de aplicaciones. Una cuenta de prueba también funcionará.  
  
## <a name="create-an-application-registration"></a>Crear un registro de la aplicación 
  
1. Iniciar sesión en el [portal de Azure](https://go.microsoft.com/fwlink/?linkid=2083908) con una cuenta con permiso de administrador. Debe usar una cuenta en la misma suscripción de Office 365 (empresa) con la que pretenda registrar la aplicación. También puede obtener acceso al portal de Azure a través del Office 365 [centro de administración](https://admin.microsoft.com/adminportal) expandiendo el elemento **Centros de administración** en el panel de navegación de la izquierda y seleccionando **Azure Active Directory**.  
  
   > [!NOTE]
   > Si no tiene un inquilino de Azure (cuenta) o tiene uno pero su suscripción a Office 365 con Common Data Service no está disponible en su suscripción de Azure, siga las instrucciones en el tema [Configurar acceso a Azure Active Directory para el sitio de desarrollador](https://msdn.microsoft.com/office/office365/HowTo/setup-development-environment) para asociar las dos cuentas.<br><br> Si no tiene una cuenta, puede registrarse para obtener una cuenta utilizando una tarjeta de crédito. No obstante, la cuenta es gratuita para el registro de aplicaciones y no se cargará en su tarjeta de crédito si sigue los procedimientos indicados en este tema para registrar una o varias aplicaciones. Más información: [Detalles de precios de Active Directory](https://azure.microsoft.com/pricing/details/active-directory/)  
  
2. En el portal de Azure, seleccione **Azure Active Directory** en el panel izquierdo y seleccione **Registros de la aplicación** y haga clic en **Nuevo registro**.
    
    ![Registro de aplicación de Azure](media/azure-app-registrations-page.png "Registro de aplicación de Azure")  

3. En la página **Registrar una aplicación**, especifique la información de registro de la aplicación:
   - En la sección **Nombre**, escriba un nombre descriptivo de la aplicación que se mostrará a los usuarios.
   - Seleccione la opción **Cuentas en cualquier directorio de organización** en la sección **Tipos de cuenta admitidos**.
   - Establezca el **URI de redireccionamiento**.
   - Haga clic en **Registrar** para crear la aplicación.

      ![Página de registro de nueva aplicación](media/new-app-registration-page.png "Página de registro de nueva aplicación")

5. En la página de **Información general** de la aplicación, mantenga el puntero sobre el valor **Identificador de aplicación (cliente)** y seleccione el icono **Copiar en portapapeles** para copiar el valor ya que deberá especificarlo en el código de autenticación de la aplicación o el archivo app.config si procede.

    ![Copiar identificador de aplicación](media/app-registration-overview-page.png "Copiar identificador de aplicación")
  
5. Seleccione la pestaña **Manifiesto**, en el editor de manifiesto, establezca la propiedad *allowPublicClient* en **true** y haga clic en **Guardar**.
   
    ![Manifiesto de registro de la aplicación](media/app-registration-manifest-page.png "Manifiesto de registro de la aplicación")

6. Seleccione la pestaña **Permisos de API**, haga clic en **Agregar un permiso**. 

    ![Agregar permiso de aplicación](media/azure-api-permissions-page.png "Agregar permiso de aplicación")

7. Seleccione **Dynamics CRM** en la pestaña **API de Microsoft**.
    
    ![Seleccionar API](media/app-registration-select-api-page.png "Seleccionar API")    

8. Haga clic en **Permisos delegados** y active las opciones y haga clic en **Agregar permisos**. 
    
    ![Delegar permisos](media/app-registration-delegate-permissions-page.png "Delegar permiso")

Esto completa el registro de la aplicación en Azure Active Directory.

## <a name="additional-configuration-options"></a>Opciones de configuración adicionales

Si su aplicación será una aplicación de una sola página (SPA) que depende de CROS debe configurar el registro de la aplicación para admitir el flujo implícito. Más información: [Tutorial: Registrar y configurar una aplicación SPA con adal.js](walkthrough-registering-configuring-simplespa-application-adal-js.md)

Si su aplicación es compatible con conexiones entre servidores, consulte [Usar autenticación multiinquilino entre servidores](use-multi-tenant-server-server-authentication.md)
  
### <a name="see-also"></a>Vea también  
 [Registro de aplicación en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)    
 [Autenticar usuarios con los servicios web de Common Data Service](authentication.md)
