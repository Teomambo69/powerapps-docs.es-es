---
title: Respuesta a las solicitudes de derechos del interesado (DSR) para exportar datos de cliente de PowerApps | Microsoft Docs
description: Tutorial de cómo responder las solicitudes de derechos del interesado (DSR) para exportar datos de cliente de PowerApps.
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: 1b9318bcf4624af48e6be95fd22c12c14bf75dff
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-to-export-powerapps-customer-data"></a>Respuesta a solicitudes de derechos del interesado (DSR) para exportar datos de cliente de PowerApps
El "derecho a la portabilidad de los datos" permite al interesado solicitar una copia de sus datos personales en formato electrónico (es decir, en un formato estructurado, comúnmente utilizado, legible por máquina e interoperable) que pueda ser transmitido a otro poseedor de los datos:

* Acceso al sitio web: [PowerApps](https://web.powerapps.com), [Centro de administración de PowerApps](https://admin.powerapps.com/) y [Portal de confianza de servicios de Office 365](https://servicetrust.microsoft.com/)

* Acceso de PowerShell: cmdlets de PowerApps [cmdlet de creadores](https://go.microsoft.com/fwlink/?linkid=871448), [cmdlets de administración](https://go.microsoft.com/fwlink/?linkid=871804) y [cmdlets de puerta de enlace local](https://go.microsoft.com/fwlink/?linkid=872238)

A continuación se muestra un resumen de los tipos de datos personales que PowerApps puede almacenar para un usuario específico y qué experiencias puede usar para buscarlos y exportarlos.

Recursos que contienen datos personales | Acceso al sitio web |   Acceso de PowerShell
--- | --- | --
Entorno | Centro de administración de PowerApps |  Cmdlets de PowerApps
Permisos de entorno**   | Centro de administración de PowerApps    | Cmdlets de PowerApps
Aplicaciones de lienzo  | Centro de administración de PowerApps <br> Portal de creadores de PowerApps |  Cmdlets de PowerApps
Permisos de la aplicación de lienzo  | Centro de administración de PowerApps <br> Portal de creadores de PowerApps    | Cmdlets de PowerApps
Puerta de enlace | Portal de creadores de PowerApps*** | Cmdlets de puerta de enlace local
Permisos de puerta de enlace | Portal de creadores de PowerApps*** |
Conector personalizado | |    Creador: disponible <br> Administrador: en desarrollo
Permisos del conector personalizado | |    Creador: disponible <br> Administrador: En desarrollo
Conexión | | Creador: disponible <br> Administrador: en desarrollo
Permisos de conexión  | | Creador: disponible <br> Administrador: en desarrollo
Configuración de usuario de PowerApps, configuración de la aplicación de usuario y notificaciones | | Creador: disponible <br> Administrador: En desarrollo

> ** Con la introducción de Common Data Service (CDS) for Apps, si se crea una base de datos dentro del entorno, los permisos de entorno y los permisos de aplicaciones controladas por modelos se almacenan como registros dentro de la instancia de base de datos CDS para aplicaciones. Para instrucciones sobre cómo responder a solicitudes DSR para usuarios que utilizan CDS for Apps, consulte [Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de Common Data Service for Apps](common-data-service-gdpr-dsr-guide.md).

> *** Un administrador puede acceder a estos recursos desde [PowerApps ](https://web.powerapps.com) solo si el propietario del recurso le ha concedido explícitamente el acceso. Si no es así, deberá aprovechar los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804).

## <a name="prerequisites"></a>Requisitos previos

### <a name="for-users"></a>Para usuarios
Cualquier usuario con una licencia válida de PowerApps puede realizar las operaciones de usuario descritas en este documento mediante cmdlets de [PowerApps ](https://web.powerapps.com) o [de creadores](https://go.microsoft.com/fwlink/?linkid=871448).

### <a name="for-admins"></a>Para administradores
Para hacer las operaciones de administración que se describen en este documento mediante el Centro de administración de PowerApps, el Centro de administración de Microsoft Flow o los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804), necesitará lo siguiente:

* Una licencia de PowerApps plan 2 de pago o una licencia de prueba PowerApps plan 2. También puede registrarse para obtener una licencia de evaluación gratuita de 30 días en [http://web.powerapps.com/trial](http://web.powerapps.com/trial). Las licencias de evaluación gratuita se pueden renovar si han caducado.

* Permisos de [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o de [Azure Active Directory ](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) si tiene que buscar en los recursos de otro usuario. (Tenga en cuenta que los administradores de entorno solo tienen acceso a los entornos y los recursos de entorno para los cuales tienen permisos).

## <a name="step-1-export-personal-data-contained-within-environments-created-by-the-user"></a>Paso 1: Exportación de datos personales contenidos en entornos creados por el usuario

### <a name="powerapps-admin-center"></a>Centro de administración de PowerApps
Los administradores pueden exportar todos los entornos creados por un usuario específico en el [Centro de administración de PowerApps](https://admin.powerapps.com/) siguiendo estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Si el entorno lo ha creado el usuario a partir de la solicitud DSR, vaya a la página **Detalles**, copie los detalles y péguelos en un editor de documentos, como Microsoft Word.

    ![Detalles del entorno](./media/powerapps-gdpr-export-dsr/environment-details.png)

### <a name="powerapps-maker-powershell-cmdlets"></a>Cmdlets de PowerShell para creadores de PowerApps
Los usuarios pueden exportar los entornos a los que tienen acceso en PowerApps mediante la función **Get-PowerAppsEnvironment** de los [cmdlets de PowerShell para creadores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871448):

~~~~
Add-PowerAppsAccount
Get-PowerAppsEnvironment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
Los administradores pueden exportar todos los entornos creados por un usuario mediante la función **Get-AdminEnvironment** en los [cdmlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

~~~~
Add-PowerAppsAccount
$userId = "7557f390-5f70-4c93-8bc4-8c2faabd2ca0"
Get-AdminEnvironment -CreatedBy $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~
 
## <a name="step-2-export-the-users-environment-permissions"></a>Paso 2: Exportación de los permisos de entorno del usuario
A los usuarios se les pueden asignar permisos (como administrador de entornos o creador de entornos) en un entorno, que se almacenan en PowerApps como una *asignación de roles*. Con la introducción de CDS for Apps, si se crea una base de datos dentro del entorno, las asignaciones de roles se almacenan como registros dentro de la instancia de base de datos de CDS for Apps. Para más información, consulte [Administrar entornos en PowerApps](environments-administration.md).

### <a name="for-environments-without-a-cds-for-apps-database"></a>Para entornos sin una base de datos de CDS for Apps

#### <a name="powerapps-admin-center"></a>Centro de administración de PowerApps
Los administradores pueden exportar todos los permisos de entorno de un usuario en el [Centro de administración de PowerApps](https://admin.powerapps.com/) siguiendo estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización. Hay que ser [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o [administrador global de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) para poder revisar todos los entornos que se han creado en la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Seleccione **Seguridad**.

    Si el entorno no tiene una base de datos de CDS for Apps, verá una sección dedicada a los **roles de entorno.**

3. Seleccione el **administrador de entornos** y **el creador de entornos** por separado y, después, mediante la barra de búsqueda, busque el nombre del usuario.

    ![Página de roles de entorno](./media/powerapps-gdpr-export-dsr/admin-environment-role-share-page.png)

4. Si el usuario tiene acceso a cualquiera de los dos roles, vaya a la página **Usuarios**, copie los detalles y péguelos en un editor de documentos, como Microsoft Word.

#### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
Los administradores pueden exportar todas las asignaciones de roles de entorno para un usuario a todos los entornos sin una base de datos de CDS for Apps mediante la función **Get-AdminEnvironmentRoleAssignment** en los cdmlets [de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminEnvironmentRoleAssignment -UserId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

> [!IMPORTANT]
>  Esta función solo funciona para entornos que no tienen una instancia de base de datos de CDS for Apps.
>
>

### <a name="for-environments-with-a-cds-for-apps-database"></a>Para entornos con una base de datos de CDS for Apps
Con la introducción de CDS for Apps, si se crea una base de datos dentro del entorno, estas asignaciones de roles se almacenan como registros dentro de la instancia de base de datos de CDS for Apps. Para obtener información sobre cómo eliminar datos personales de una instancia de base de datos de CDS for Apps, consulte el artículo sobre la [eliminación de datos personales del usuario de Common Data Service](https://go.microsoft.com/fwlink/?linkid=871886).
 
## <a name="step-3-export-personal-data-contained-within-canvas-apps-created-by-the-user"></a>Paso 3: Exportación de datos personales contenidos en aplicaciones de lienzo creadas por el usuario

### <a name="powerapps-maker-portal"></a>Portal de creadores de PowerApps
Los usuarios pueden exportar una aplicación desde [PowerApps](https://web.powerapps.com). Para obtener instrucciones paso a paso sobre cómo exportar una aplicación, consulte [Exportación de una aplicación](environment-and-tenant-migration.md#exporting-an-app).

### <a name="powerapps-admin-center"></a>Centro de administración de PowerApps
Un administrador puede exportar las aplicaciones creadas por un usuario en el [Centro de administración de PowerApps](https://admin.powerapps.com/) con estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización. Hay que ser [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o [administrador global de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) para poder revisar todos los entornos que se han creado en la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Seleccione **Recursos** y, después, seleccione **Aplicaciones**.

3. Con la barra de búsqueda, busque el nombre del usuario, que muestra cualquier aplicación que el usuario ha creado dentro de este entorno:

    ![Buscar aplicaciones](./media/powerapps-gdpr-export-dsr/search-apps.png)

4. Seleccione **Compartir**  para cada una de las aplicaciones creadas por ese usuario y dese el acceso **Puede editar** a la aplicación:

    ![Seleccionar un recurso compartido de la aplicación](./media/powerapps-gdpr-export-dsr/select-share.png)

    ![Dar acceso al usuario](./media/powerapps-gdpr-export-dsr/grant-access.png)

5. Cuando tenga acceso a cada una de las aplicaciones del usuario, podrá exportar una aplicación desde [PowerApps](https://web.powerapps.com). Para obtener instrucciones paso a paso sobre cómo exportar una aplicación, consulte [Exportación de una aplicación](environment-and-tenant-migration.md#exporting-an-app).

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
Los administradores pueden exportar aplicaciones creadas por un usuario mediante la función **Get-AdminApp** en los [cdmlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminApp -Owner $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-4-export-the-users-permissions-to-canvas-apps"></a>Paso 4: Exportación de los permisos del usuario a las aplicaciones de lienzo
Siempre que se comparte una aplicación con un usuario, PowerApps almacena un registro denominado *asignación de roles*  que describe los permisos del usuario (CanEdit o CanUser) a la aplicación. Para más información, consulte cómo [compartir una aplicación](../maker/canvas-apps/share-app.md#share-an-app).

### <a name="powerapps-maker-powershell-cmdlets"></a>Cmdlets de PowerShell para creadores de PowerApps
Los usuarios pueden exportar las asignaciones de roles de aplicación a todas las aplicaciones que tienen acceso mediante la función **Get-RoleAssignment** de los [cmdlets de PowerShell para creadores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871448):

~~~~
Add-PowerAppsAccount
Get-AppRoleAssignment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-center"></a>Centro de administración de PowerApps
Los administradores pueden exportar las asignaciones de roles de aplicación de un usuario en el [Centro de administración de PowerApps](https://admin.powerapps.com/) siguiendo estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización. Hay que ser [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o [administrador global de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) para poder revisar todos los entornos que se han creado en la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Para cada entorno, seleccione **Recursos** y, después, seleccione **Aplicaciones**.

3. Seleccione **Compartir**  para cada una de las aplicaciones del entorno.

    ![Seleccionar un recurso compartido de la aplicación](./media/powerapps-gdpr-export-dsr/select-admin-share-nofilter.png)

4. Si el usuario tiene acceso a la aplicación, vaya a la página **Compartir** de la aplicación, copie los detalles y péguelos en un editor de documentos, como Microsoft Word.

    ![Página de recursos compartidos de la aplicación de administración](./media/powerapps-gdpr-export-dsr/admin-share-page.png)

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
Los administradores pueden exportar todas las asignaciones de roles de aplicación para un usuario a todas las aplicaciones de su inquilino mediante la función **Get-AdminAppRoleAssignment** en los [cdmlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminAppRoleAssignment -UserId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-5-export-personal-data-contained-within-connections-created-by-the-user"></a>Paso 5: Exportación de datos personales contenidos en conexiones creadas por el usuario
Las conexiones se utilizan junto con los conectores al establecer la conectividad con otras API y sistemas SaaS. Las conexiones incluyen referencias al usuario que las creó y, como resultado, se pueden eliminar para quitar cualquier referencia al usuario.

### <a name="powerapps-maker-powershell-cmdlets"></a>Cmdlets de PowerShell para creadores de PowerApps
Los usuarios pueden exportar todas las conexiones a las que tienen acceso mediante la función **Get-Connection** de los [cmdlets de PowerShell para creadores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871448):

~~~~
Add-PowerAppsAccount
Get-Connection | ConvertTo-Json | out-file -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
La función para que un administrador exporte las conexiones creadas por un usuario mediante los [cdmlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) está en desarrollo.
 
## <a name="step-6-export-the-users-permissions-to-shared-connections"></a>Paso 6: Exportación de los permisos del usuario a las conexiones compartidas

### <a name="powerapps-maker-powershell-cmdlets"></a>Cmdlets de PowerShell para creadores de PowerApps
Los usuarios pueden exportar las asignaciones de roles de conexión a todas las conexiones a las que tienen acceso mediante la función **Get-ConnectionRoleAssignment** de los [cmdlets de PowerShell para creadores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871448):

~~~~
Add-PowerAppsAccount
Get-ConnectionRoleAssignment | ConvertTo-Json | out-file -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
La función para que un administrador exporte las asignaciones de roles de conexión para un usuario mediante los [cdmlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) está en desarrollo.

## <a name="step-7-export-personal-data-contained-within-custom-connectors-created-by-the-user"></a>Paso 7: Exportación de datos personales contenidos en conectores personalizados creados por el usuario
Los conectores personalizados complementan los conectores ya existentes y permiten la conectividad con otras API, SaaS y sistemas desarrollados a medida.

### <a name="powerapps-maker-powershell-cmdlets"></a>Cmdlets de PowerShell para creadores de PowerApps
Los usuarios pueden exportar todos los conectores que han creado mediante la función **Get-Connector** de los [cmdlets de PowerShell para creadores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871448):

~~~~
Add-PowerAppsAccount  
Get-Connector -FilterNonCustomConnectors | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
La función para que un administrador exporte los conectores personalizados creados por un usuario mediante los [cdmlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) está en desarrollo.

## <a name="step-8-export-the-users-permissions-to-custom-connectors"></a>Paso 8: Exportación de los permisos del usuario a los conectores personalizados

### <a name="powerapps-maker-powershell-cmdlets"></a>Cmdlets de PowerShell para creadores de PowerApps
Los usuarios pueden exportar todas las asignaciones de roles de conector para todos los conectores personalizados a los que tienen acceso mediante la función **Get-ConnectorRoleAssignment** de los [cmdlets de PowerShell para creadores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871448):

~~~~
Add-PowerAppsAccount  
Get-ConnectorRoleAssignment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
La función para que un administrador exporte las asignaciones de roles de conectores personalizados para un usuario mediante los [cdmlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) está en desarrollo.
 
## <a name="step-9-export-powerapps-notifications-user-settings-and-user-app-settings"></a>Paso 9: Exportación de notificaciones de PowerApps, configuración de usuario y configuración de aplicaciones de usuario
PowerApps envía varios tipos de notificaciones a los usuarios, incluyendo cuando se comparte una aplicación con ellos y cuando se ha completado una operación de exportación de CDS for Apps. El historial de notificaciones de un usuario está visible en [PowerApps](https://web.powerapps.com).

PowerApps también almacena varias preferencias y configuraciones de usuario diferentes que se utilizan para ofrecer el tiempo de ejecución y las experiencias de portal de PowerApps, como la última vez que un usuario abrió una aplicación o ancló una aplicación, entre otras.

### <a name="powerapps-maker-powershell-cmdlets"></a>Cmdlets de PowerShell para creadores de PowerApps
La función para exportar las notificaciones de PowerApps de un usuario, la configuración de usuario y la configuración de la aplicación del usuario mediante los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) está en desarrollo.

### <a name="powerapps-admin-powershell-cmdlets"></a>Cmdlets de Powershell para administradores de PowerApps
La función para que un administrador exporte las notificaciones de PowerApps de un usuario, la configuración de usuario y la configuración de la aplicación del usuario mediante los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) está en desarrollo.

## <a name="step-10-export-personal-data-contained-for-a-user-stored-gateway-or-in-the-users-gateway-permissions"></a>Paso 10: Exportación de datos personales contenidos en una puerta de enlace almacenada por el usuario o en los permisos de la puerta de enlace del usuario

### <a name="powerapps-maker-portal"></a>Portal de creadores de PowerApps
Los usuarios pueden exportar los datos personales almacenados en el servicio de puerta de enlace de [PowerApps](https://web.powerapps.com) siguiendo estos pasos:

1. En [PowerApps ](https://web.powerapps.com), dentro del entorno predeterminado para el inquilino, seleccione **Puertas de enlace** y, después, seleccione **Detalles** para cada puerta de enlace a la que tenga acceso.

    ![Página de destino de la puerta de enlace](./media/powerapps-gdpr-export-dsr/gateway-select-details.png)

2. En la página **Detalles**, si los detalles de la puerta de enlace contienen datos personales, cópielos y péguelos en un editor de documentos, como Microsoft Word.

    ![Detalles de la puerta de enlace](./media/powerapps-gdpr-export-dsr/gateway-details-drillin.png)

3. Seleccione **Compartir** , copie el contenido de la página y péguelo en un editor de documentos, como Microsoft Word.

    ![Detalles de la puerta de enlace](./media/powerapps-gdpr-export-dsr/gateway-details-share.png)

### <a name="gateway-powershell-cmdlets"></a>Cmdlets de PowerShell de la puerta de enlace
También hay cmdlets de PowerShell que permiten recuperar, administrar y eliminar las puertas de enlace personales. Para más información, consulte los [cmdlets de puerta de enlace local](https://go.microsoft.com/fwlink/?linkid=872238).

## <a name="step-11-export-the-users-personal-data-in-microsoft-flow"></a>Paso 11: Exportación de los datos personales del usuario en Microsoft Flow
Las licencias de PowerApps siempre incluyen funcionalidades de Microsoft Flow. Además de que se incluirse en PowerApps, Microsoft Flow también está disponible como servicio independiente. Para instrucciones sobre cómo responder solicitudes DSR de los usuarios que utilizan el servicio Microsoft Flow, consulte [Respuesta a solicitudes del titular de los datos de acuerdo con el RGPD para Microsoft Flow](https://go.microsoft.com/fwlink/?linkid=872250).

> [!IMPORTANT] 
>  Se recomienda que los administradores completen este paso para los usuarios de PowerApps.
>
>

## <a name="step-12-export-the-users-personal-data-in-cds-for-apps-instances"></a>Paso 12: Exportación de los datos personales del usuario en instancias de CDS for Apps
Algunas licencias de PowerApps permiten a los usuarios de su organización crear instancias de CDS for Apps y crear y compilar aplicaciones en CDS para aplicaciones, incluido el Plan de comunidad de PowerApps, que es una licencia gratuita que permite a los usuarios probar CDS for Apps en un entorno individual. Para ver qué funcionalidades de CDS for Apps están incluidas en cada licencia de PowerApps, consulte la página [Precios de PowerApps](https://powerapps.microsoft.com/pricing).

Para instrucciones sobre cómo responder a solicitudes DSR para usuarios que utilizan CDS for Apps, consulte [Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de Common Data Service for Apps](common-data-service-gdpr-dsr-guide.md).

> [!IMPORTANT]
>  Se recomienda que los administradores completen este paso para los usuarios de PowerApps.
>
>
