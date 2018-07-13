---
title: Respuesta a solicitudes de derechos del interesado (DSR) para eliminar datos de cliente | Microsoft Docs
description: Tutorial de cómo responder las solicitudes de derechos del interesado (DSR) para eliminar datos de cliente de PowerApps.
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: d518cbf398d0f29b25da9dafcfa6e9026fcee88e
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37897188"
---
# <a name="responding-to-data-subject-rights-dsr-requests-to-delete-powerapps-customer-data"></a>Respuesta a solicitudes de derechos del interesado (DSR) para eliminar datos de cliente de PowerApps

El "derecho al olvido" mediante la eliminación de datos personales de los datos de cliente de una organización es una protección de clave en el Reglamento general de protección de datos (RGDP) de la Unión Europea (UE). La eliminación de datos personales incluye la eliminación de registros generados por el sistema, pero no de información del registro de auditoría.

PowerApps permite a los usuarios compilar aplicaciones de línea de negocio que sean parte fundamental de las operaciones diarias de su organización. Cuando un usuario deja la organización, habrá que realizar una revisión manual y determinar si se deben eliminar determinados datos y recursos que el usuario haya creado. Otros datos personales se eliminarán automáticamente cuando se elimine la cuenta del usuario de Azure Active Directory.

Esta la distribución de los datos personales que se eliminarán automáticamente y los datos que requerirán la revisión y eliminación manual:

Requieren revisión y eliminación manual |   Se eliminan automáticamente al eliminar el usuario de Azure Active Directory
--- | ---
Entorno\** | Puerta de enlace
Permisos de entorno\*** | Permisos de puerta de enlace
Aplicaciones de lienzo\** | Notificaciones de PowerApps
Permisos de aplicaciones de lienzo | Configuración de usuario de PowerApps
Conexión\** | Configuración de aplicaciones de usuario de PowerApps
Permisos de conexión |
Conector personalizado\** |
Permisos de conector personalizado |  

\** Cada uno de estos recursos contiene registros "Creado por" y "Modificado por" que incluyen datos personales. Por motivos de seguridad, estos registros se conservarán hasta que se elimine el recurso.

\*** Para entornos que incluyen una base de datos de Common Data Service (CDS) for Apps, los permisos de entorno (es decir, los usuarios a los que se les asignan roles de administrador y de creador de entorno) se almacenan como registros en esa base de datos. Para instrucciones sobre cómo responder a solicitudes DSR para usuarios de CDS for Apps, consulte [Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de Common Data Service for Apps](common-data-service-gdpr-dsr-guide.md).

En el caso de los datos y recursos que requieren una revisión manual, PowerApps ofrece las siguientes experiencias para reasignar (si es necesario) o eliminar datos personales de un usuario concreto:

* Acceso al sitio web: [sitio de PowerApps](https://web.powerapps.com), [Centro de administración de PowerApps](https://admin.powerapps.com/) y [Portal de confianza de servicios de Office 365](https://servicetrust.microsoft.com/)

* Acceso de PowerShell: cmdlets de PowerApps [para creadores de aplicaciones](https://go.microsoft.com/fwlink/?linkid=871448) y [administradores](https://go.microsoft.com/fwlink/?linkid=871804) y cmdlets de [puertas de enlace locales](https://go.microsoft.com/fwlink/?linkid=872238).

Esta la distribución de las experiencias que están disponibles para eliminar cada tipo de recurso que pueda contener datos personales:

Recursos que contienen datos personales | Acceso al sitio web | Acceso de PowerShell
--- | --- | ---
Entorno | Centro de administración de PowerApps |  Cmdlets de PowerApps
Permisos de entorno**   | Centro de administración de PowerApps | Cmdlets de PowerApps
Aplicaciones de lienzo  | Centro de administración de PowerApps <br> PowerApps| Cmdlets de PowerApps
Permisos de aplicaciones de lienzo  | Centro de administración de PowerApps | Cmdlets de PowerApps
Conexión | | Creador de aplicaciones: Disponible <br> Administrador: disponible
Permisos de conexión | | Creador de aplicaciones: Disponible <br> Administrador: disponible
Conector personalizado | | Creador de aplicaciones: Disponible <br> Administrador: disponible
Permisos de conector personalizado | | Creador de aplicaciones: Disponible <br> Administrador: disponible

\** Con la introducción de CDS for Apps, si se crea una base de datos en el entorno, los permisos de entorno y los permisos de aplicación basados en modelos se almacenan como registros en la instancia de la base de datos. Para instrucciones sobre cómo responder a solicitudes DSR para usuarios de CDS for Apps, consulte [Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de Common Data Service for Apps](common-data-service-gdpr-dsr-guide.md).

## <a name="prerequisites"></a>Requisitos previos

### <a name="for-users"></a>Para usuarios
Cualquier usuario con una licencia válida de PowerApps puede realizar las operaciones de usuario descritas en este documento mediante [PowerApps ](https://web.powerapps.com) o los [cmdlets de PowerShell para creadores de aplicaciones](https://go.microsoft.com/fwlink/?linkid=871448).

#### <a name="unmanaged-tenant"></a>Inquilino no administrado
Si es miembro de un [inquilino no administrado](https://docs.microsoft.com/azure/active-directory/domains-admin-takeover), lo que significa que el inquilino de Azure AD no tiene un administrador global, todavía podrá seguir los pasos descritos en esta imagen para quitar sus propios datos personales.  Pero como no hay ningún administrador global para el inquilino, debe seguir las instrucciones que se describen en [Paso 11: Eliminación del usuario de Azure Active Directory](#step-11-delete-the-user-from-azure-active-directory) a continuación para eliminar su propia cuenta del inquilino.

Para determinar si es un miembro de un inquilino no administrado, siga estos pasos:

1. Abra la dirección URL siguiente en un explorador y asegúrese de reemplazar la dirección de correo electrónico en la dirección URL: https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1.

2. Si es miembro de un **inquilino no administrado**, verá `"IsViral": true` en la respuesta.
   ```
   {
   ...
   "Login": "foobar@unmanagedcontoso.com",
   "DomainName": "unmanagedcontoso.com",
   "IsViral": true,
   ...
   }
   ```

3. En caso contrario, pertenece a un **inquilino administrado**.

### <a name="for-administrators"></a>Para administradores
Para ejecutar las operaciones administrativas descritas en este documento con el [Centro de administración de PowerApps](https://admin.powerapps.com/), el Centro de administración de Microsoft Flow o los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804), necesitará lo siguiente:

* Una licencia de PowerApps plan 2 de pago o una licencia de prueba PowerApps plan 2. También puede registrarse para obtener una licencia de evaluación gratuita de 30 días en [http://web.powerapps.com/trial](http://web.powerapps.com/trial). Las licencias de evaluación gratuita se pueden renovar si han caducado.

* Permisos de [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o de [Azure Active Directory ](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) si tiene que buscar en los recursos de otro usuario. (Tenga en cuenta que los administradores de entorno solo tienen acceso a los entornos y los recursos de entorno para los cuales tienen permisos).

## <a name="step-1-delete-or-reassign-all-environments-created-by-the-user"></a>Paso 1: Eliminación o reasignación de todos los entornos creados por el usuario
Como administrador, tiene que tomar dos decisiones al procesar una solicitud de eliminación de DSR para cada entorno creado por el usuario:

1. Si determina que el entorno no lo utiliza ninguna otra persona de la organización, puede eliminarlo.

2. Si determina que el entorno sigue siendo necesario, puede optar por no eliminarlo y agregarse a sí mismo (o agregar otro usuario de la organización) como administrador de entorno.

> [!IMPORTANT]
> Al eliminar un entorno se eliminarán permanentemente todos los recursos en el entorno, incluidas todas las aplicaciones, todos los flujos, todas las conexiones, etcétera. Así que revise el contenido de un entorno antes de eliminarlo.

### <a name="give-access-to-a-users-environments-from-the-powerapps-admin-center"></a>Concesión de acceso a los entornos de un usuario desde el Centro de administración de PowerApps
Un administrador puede conceder acceso administrativo a un entorno creado por un usuario concreto desde el [Centro de administración de PowerApps](https://admin.powerapps.com/) con estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Si el entorno lo ha creado el usuario de la solicitud DSR, seleccione **Seguridad** y continúe con los pasos descritos en [Administrar entornos](environments-administration.md) para concederse privilegios de administrador a sí mismo o concederlos a otro usuario de la organización.

    ![Seguridad del entorno](./media/powerapps-gdpr-delete-dsr/share-environment.png)

### <a name="delete-environments-created-by-a-user-from-the-powerapps-admin-center"></a>Eliminación de los entornos creados por un usuario desde el Centro de administración de PowerApps
Un administrador puede revisar y eliminar entornos creados por un usuario concreto desde el [Centro de administración de PowerApps](https://admin.powerapps.com/) con estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Si el entorno lo ha creado el usuario de la solicitud DSR, seleccione **Eliminar** y luego continúe con los pasos para eliminar el entorno:

    ![Eliminación del entorno](./media/powerapps-gdpr-delete-dsr/delete-environment.png)

### <a name="give-access-to-a-users-environments-using-powershell"></a>Concesión de acceso a los entornos de un usuario con PowerShell
Un administrador puede asignarse a sí mismo (o asignarlo a otro usuario de la organización) acceso a todos los entornos creados por un usuario mediante la función **Set-AdminEnvironmentRoleAssignment** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$myUserId = $global:currentSession.UserId

#Assign yourself as an admin to each environment created by the user
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Set-AdminEnvironmentRoleAssignment -RoleName EnvironmentAdmin -PrincipalType User -PrincipalObjectId $myUserId

#Retrieve the environment role assignments to confirm
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Get-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> Esta función solo opera en entornos que no tengan una instancia de una base de datos de CDS for Apps.

### <a name="delete-environments-created-by-a-user-using-powershell"></a>Eliminación de entornos creados por un usuario con PowerShell
 Un administrador puede eliminar todos los entornos creados por un usuario mediante la función **Remove-AdminEnvironment** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

# Retrieve all environments created by the user and then delete them
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Remove-AdminEnvironment
```

## <a name="step-2-delete-the-users-permissions-to-all-other-environments"></a>Paso 2: Eliminación de los permisos del usuario en los demás entornos
A los usuarios se les pueden asignar permisos (como administrador de entorno y de creador de entorno) en un entorno, que se almacenan en PowerApps como "asignación de roles".
Con la introducción de CDS for Apps, si se crea una base de datos en el entorno, estas "asignaciones de roles" se almacenan como registros en la instancia de esa base de datos.
Para obtener más información, vea [Administrar entornos](environments-administration.md).

### <a name="for-environments-without-a-cds-for-apps-database"></a>Para entornos sin una base de datos de CDS for Apps

#### <a name="powerapps-admin-center"></a>Centro de administración de PowerApps
Un administrador puede eliminar permisos de entorno de un usuario a partir del [Centro de administración de PowerApps](https://admin.powerapps.com/) con estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización.

    Hay que ser [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o [administrador global de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) para poder revisar todos los entornos que se han creado en la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Seleccione **Seguridad**.

    Si el entorno no tiene una base de datos de CDS for Apps, verá una sección dedicada a los **roles de entorno.**

3. En **Environment Roles**, seleccione ambos roles **Administrador de entorno** y **Creador de entorno** por separado y luego, mediante la barra de búsqueda, busque el nombre del usuario.

    ![Página de roles de entorno](./media/powerapps-gdpr-delete-dsr/admin-environment-role-share-page.png)

5.  Si el usuario tiene acceso a alguno de los roles, en la pantalla **Usuarios**, quite los permisos y seleccione **Guardar**.

#### <a name="powershell"></a>PowerShell
Un administrador puede eliminar todas las asignaciones de roles de entorno de un usuario en todos los entornos sin una base de datos de CDS for Apps mediante la función **Remove-AdminEnvironmentRoleAssignment** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all environment role assignments for the user for environments without a CDS for Apps instance and delete them
Get-AdminEnvironmentRoleAssignment -UserId $deleteDsrUserId | Remove-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> Esta función solo opera en entornos que no tengan una instancia de una base de datos de CDS for Apps.

### <a name="for-environments-with-a-cds-for-apps-database"></a>Para entornos CON una base de datos de CDS for Apps
Con la introducción de CDS for Apps, si se crea una base de datos en el entorno, estas "asignaciones de roles" se almacenan como registros en la instancia de esa base de datos. Consulte el artículo sobre la eliminación de datos personales del usuario de Common Data Service para obtener información sobre cómo eliminar datos personales de una instancia de base de datos de CDS for Apps.

## <a name="step-3-delete-or-reassign-all-canvas-apps-owned-by-a-user"></a>Paso 3: Eliminación o reasignación de todas las aplicaciones de lienzo propiedad de un usuario

### <a name="reassign-a-users-canvas-apps-using-the-powerapps-admin-powershell-cmdlets"></a>Reasignación de aplicaciones de lienzo de un usuario con los cmdlets de PowerShell para administradores de PowerApps
Si un administrador decide no eliminar aplicaciones de lienzo de un usuario, puede reasignar las aplicaciones que son propiedad de un usuario mediante la función **Set-AdminAppOwner** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$newAppOwnerUserId = "72c272b8-14c3-4f7a-95f7-a76f65c9ccd8"

#find all apps owned by the DSR user and assigns them a new owner
Get-AdminApp -Owner $deleteDsrUserId | Set-AdminAppOwner -AppOwner $newAppOwnerUserId
```

### <a name="delete-a-users-canvas-app-using-the-powerapps-site"></a>Eliminación de la aplicación de lienzo de un usuario mediante el sitio de PowerApps
Un usuario puede eliminar una aplicación desde el [sitio de PowerApps](https://web.powerapps.com). Para obtener los pasos completos sobre cómo eliminar una aplicación, vea cómo eliminar una aplicación.

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-center"></a>Eliminación de una aplicación de lienzo de un usuario mediante el Centro de administración de PowerApps
Un administrador puede eliminar las aplicaciones creadas por un usuario en el [Centro de administración de PowerApps](https://admin.powerapps.com/) con estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización.

    Hay que ser [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o [administrador Global de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) para poder revisar todos los entornos que se han creado en la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Seleccione **Recursos** > **Aplicaciones**.

3. Con la barra de búsqueda, busque el nombre del usuario, lo que muestra todas las aplicaciones que el usuario ha creado en este entorno:

    ![Buscar aplicaciones](./media/powerapps-gdpr-delete-dsr/search-apps.png)

4. Seleccione **Detalles** para cada una de las aplicaciones propiedad del usuario:

    ![Selección de detalles de la aplicación](./media/powerapps-gdpr-delete-dsr/select-app-details.png)

5. Seleccione **Eliminar** para eliminar cada aplicación:

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-powershell-cmdlets"></a>Eliminación una aplicación de lienzo de un usuario con los cmdlets de PowerShell para administradores de PowerApps
Si un administrador decide eliminar todas las aplicaciones de lienzo propiedad de un usuario, puede hacerlo mediante la función **Remove-AdminApp** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all apps owned by the DSR user and deletes them
Get-AdminApp -Owner "0ecb1fcc-6782-4e46-a4c4-738c1d3accea" | Remove-AdminApp
```

## <a name="step-4-delete-the-users-permissions-to-canvas-apps"></a>Paso 4: Eliminación de los permisos del usuario en las aplicaciones de lienzo
Siempre que se comparte una aplicación con un usuario, PowerApps almacena un registro denominado "asignación de roles" que describe los permisos del usuario (CanEdit o CanUse) en la aplicación. Para obtener más información, vea el artículo sobre cómo compartir una aplicación.

> [!NOTE]
> Las asignaciones de roles de una aplicación se eliminarán cuando se elimina la aplicación.

> [!NOTE]
> La asignación de roles del propietario de la aplicación solo puede eliminarse asignando un nuevo propietario a la aplicación.

### <a name="powerapps-admin-center"></a>Centro de administración de PowerApps
Un administrador puede eliminar las asignaciones de roles de aplicación para un usuario a partir del [Centro de administración de PowerApps](https://admin.powerapps.com/) con estos pasos:

1. En el [Centro de administración de PowerApps](https://admin.powerapps.com/), seleccione cada entorno de la organización.

    Hay que ser [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o [administrador global de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) para poder revisar todos los entornos que se han creado en la organización.

    ![Página de aterrizaje del Centro de administración](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Para cada entorno, seleccione **Recursos** > **Apps**.

3. Seleccione **Compartir**  para cada una de las aplicaciones del entorno:

    ![Seleccionar un recurso compartido de la aplicación](./media/powerapps-gdpr-delete-dsr/select-admin-share-nofilter.png)

4. Si el usuario tiene acceso la aplicación, en la pantalla **Recurso compartido**, quite los permisos y seleccione **Guardar**.

    ![Página de recursos compartidos de la aplicación de administración](./media/powerapps-gdpr-delete-dsr/admin-share-page.png)

### <a name="powershell-cmdlets-for-admins"></a>Cmdlets de PowerShell para administradores
Un administrador puede eliminar todas las asignaciones de roles de aplicación de lienzo de un usuario mediante la función **Remove-AdminAppRoleAssignmnet** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all app role assignments for the DSR user and deletes them
Get-AdminAppRoleAssignment -UserId $deleteDsrUserId | Remove-AdminAppRoleAssignment
```

## <a name="step-5-delete-connections-created-by-a-user"></a>Paso 5: Eliminación de las conexiones creadas por un usuario
Las conexiones se utilizan junto con los conectores al establecer la conectividad con otras API y sistemas SaaS.  Las conexiones incluyen referencias al usuario que las creó y, por consiguiente, se pueden eliminar para quitar las referencias al usuario.

### <a name="powershell-cmdlets-for-app-creators"></a>Cmdlets de PowerShell para creadores de aplicaciones
Un usuario puede eliminar todas sus conexiones mediante la función Remove-Connection de los [cmdlets de PowerShell para creadores de aplicaciones](https://go.microsoft.com/fwlink/?linkid=871448):

```
Add-PowerAppsAccount

#Retrieves all connections for the calling user and deletes them
Get-Connection | Remove-Connection
```

### <a name="powershell-cmdlets-for-powerapps-administrators"></a>Cmdlets de PowerShell para administradores de PowerApps
Un administrador puede eliminar todas las conexiones de un usuario mediante la función **Remove-AdminConnection** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all connections for the DSR user and deletes them
Get-AdminConnection -CreatedBy $deleteDsrUserId | Remove-AdminConnection
```

## <a name="step-6-delete-the-users-permissions-to-shared-connections"></a>Paso 6: Eliminación de los permisos del usuario en conexiones compartidas

### <a name="powershell-cmdlets-for-app-creators"></a>Cmdlets de PowerShell para creadores de aplicaciones
Un usuario puede eliminar todas sus asignaciones de roles de conexión mediante la función Remove-ConnectionRoleAssignment de los [cmdlets de PowerShell para creadores de aplicaciones](https://go.microsoft.com/fwlink/?linkid=871448):

```
Add-PowerAppsAccount

#Retrieves all connection role assignments for the calling users and deletes them
Get-ConnectionRoleAssignment | Remove-ConnectionRoleAssignment
```
> [!NOTE]
> Las asignaciones de roles de propietario no se pueden eliminar sin eliminar el recurso de conexión.

### <a name="powershell-cmdlets-for-admins"></a>Cmdlets de PowerShell para administradores
Un administrador puede eliminar todas las asignaciones de roles de conexión de un usuario mediante la función **Remove-AdminConnectionRoleAssignment** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all connection role assignments for the DSR user and deletes them
Get-AdminConnectionRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectionRoleAssignment
```

## <a name="step-7-delete-custom-connectors-created-by-the-user"></a>Paso 7: Eliminación de conectores personalizados creados por el usuario
Los conectores personalizados complementan los conectores de serie ya existentes y permiten la conectividad con otras API, SaaS y sistemas desarrollados a medida. Puede que quiera transferir la propiedad del conector personalizado a otros usuarios de la organización o eliminar el conector personalizado.

### <a name="powershell-cmdlets-for-app-creators"></a>Cmdlets de PowerShell para creadores de aplicaciones
Un usuario puede eliminar todos sus conectores personalizados mediante la función Remove-Connector de los [cmdlets de PowerShell para creadores de aplicaciones](https://go.microsoft.com/fwlink/?linkid=871448):

```
Add-PowerAppsAccount

#Retrieves all custom connectors for the calling user and deletes them
Get-Connector -FilterNonCustomConnectors | Remove-Connector
```

### <a name="powershell-cmdlets-for-admins"></a>Cmdlets de PowerShell para administradores
Un administrador puede eliminar todos los conectores personalizados creados por un usuario mediante la función **Remove-AdminConnector** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all custom connectors created by the DSR user and deletes them
Get-AdminConnector -CreatedBy $deleteDsrUserId | Remove-AdminConnector
```

## <a name="step-8-delete-the-users-permissions-to-shared-custom-connectors"></a>Paso 8: Eliminación de los permisos de usuario en conectores personalizados compartidos

### <a name="powershell-cmdlets-for-app-creators"></a>Cmdlets de PowerShell para creadores de aplicaciones
Un usuario puede eliminar todas sus asignaciones de roles de conector para conectores personalizados compartidos mediante la función Remove-ConnectorRoleAssignment de los [cmdlets de PowerShell para creadores de aplicaciones](https://go.microsoft.com/fwlink/?linkid=871448):

```
Add-PowerAppsAccount

#Retrieves all connector role assignments for the calling users and deletes them
Get-ConnectorRoleAssignment | Remove-ConnectorRoleAssignment
```

> [!NOTE]
> Las asignaciones de roles de propietario no se pueden eliminar sin eliminar el recurso de conexión.

### <a name="powershell-cmdlets-for-admins"></a>Cmdlets de PowerShell para administradores
Un administrador puede eliminar todas las asignaciones de roles de conector personalizado para un usuario mediante la función **Remove-AdminConnectorRoleAssignment** de los [cmdlets de PowerShell para administradores de PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all custom connector role assignments for the DSR user and deletes them
Get-AdminConnectorRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectorRoleAssignment
```

## <a name="step-9-delete-the-users-personal-data-in-microsoft-flow"></a>Paso 9: Eliminación de los datos personales del usuario en Microsoft Flow
Las licencias de PowerApps siempre incluyen funcionalidades de Microsoft Flow. Además de que se incluirse en PowerApps, Microsoft Flow también está disponible como servicio independiente. Para instrucciones sobre cómo responder solicitudes DSR de los usuarios que utilizan el servicio Microsoft Flow, consulte [Respuesta a solicitudes del titular de los datos de acuerdo con el RGPD para Microsoft Flow](https://go.microsoft.com/fwlink/?linkid=872250).

> [!IMPORTANT]
> Se recomienda que los administradores completen este paso para un usuario PowerApps

## <a name="step-10-delete-the-users-personal-data-in-instances-of-cds-for-apps"></a>Paso 10: Exportación de los datos personales del usuario en instancias de CDS for Apps
Ciertas licencias PowerApps, incluido el Plan de la comunidad de PowerApps, ofrecen la posibilidad de que los usuarios de su organización creen instancias de CDS for Apps y creen y compilen aplicaciones en CDS for Apps. El Plan de la comunidad de PowerApps es una licencia gratuita que permite que los usuarios prueben CDS for Apps en un entorno individual. Vea la página de precios de PowerApps para saber qué funcionalidades se incluyen en cada licencia de PowerApps.

Para instrucciones sobre cómo responder a solicitudes DSR para usuarios que utilizan CDS for Apps, consulte [Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de Common Data Service for Apps](common-data-service-gdpr-dsr-guide.md).

> [!IMPORTANT]
> Se recomienda que los administradores completen este paso para un usuario PowerApps

## <a name="step-11-delete-the-user-from-azure-active-directory"></a>Paso 11: Eliminación del usuario de Azure Active Directory
Una vez completados los pasos anteriores, el último paso consiste en eliminar la cuenta del usuario para Azure Active Directory.

### <a name="managed-tenant"></a>Inquilino administrado
Como un administrador de un inquilino de Azure AD administrado, puede eliminar la cuenta del usuario siguiendo los pasos descritos en la documentación de Azure sobre solicitudes del interesado del RGPD que se encuentra en el [Portal de confianza de servicios de Office 365](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

### <a name="unmanaged-tenant"></a>Inquilino no administrado
Si es miembro de un inquilino no administrado, tendrá que seguir estos pasos para poder eliminar la cuenta del inquilino de Azure AD:

> [!NOTE]
> Vea la [sección Inquilino no administrado](#unmanaged-tenant) anterior para ver cómo detectar si es miembro de un inquilino administrado o no administrado.

1. Navegue hasta la [página de privacidad profesional y educativa](https://go.microsoft.com/fwlink/?linkid=87312) e inicie sesión con la cuenta de Azure AD.

2. Seleccione **Cerrar cuenta** y siga las instrucciones para eliminar la cuenta del inquilino de Azure AD.

    ![Seleccionar un recurso compartido de la aplicación](./media/powerapps-gdpr-delete-dsr/close-account.png)
