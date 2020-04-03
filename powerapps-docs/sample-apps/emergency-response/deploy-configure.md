---
title: Implementación y configuración de la aplicación de respuesta ante emergencias | Microsoft Docs
description: Proporciona instrucciones detalladas para que los administradores de TI de hospitales implementen y configuren la aplicación de ejemplo para su organización.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/26/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- GetStarted
- PowerApps
ms.openlocfilehash: e58b23503e1730c8606a833cb05f7253b5b96f49
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2020
ms.locfileid: "80327682"
---
# <a name="deploy-and-configure-the-emergency-response-app"></a>Implementación y configuración de la aplicación de respuesta ante emergencias

La aplicación de respuesta ante emergencias requiere el ajuste de algunos parámetros para adaptarse a sus necesidades. Este artículo proporciona instrucciones paso a paso para que los administradores de TI de hospitales implementen y configuren la aplicación para su organización.

Tiempo estimado para completar estos pasos: **35–40 minutos**.

## <a name="demo-deploy-and-configure-the-emergency-response-app"></a>Demostración: Implementación y configuración de la aplicación de respuesta ante emergencias

Vea cómo puede implementar y configurar la aplicación de respuesta ante emergencias.

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="deploy-the-emergency-response-app"></a>Implementación de la aplicación de respuesta ante emergencias

Siga estos pasos para implementar la aplicación de ejemplo de respuesta ante emergencias para su organización.

- [Paso 1: Registrarse en Power Apps y crear un entorno](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [Paso 2: Descargar el paquete de implementación](#step-2-download-the-deployment-package)
- [Paso 3: Importar el archivo de solución en el entorno](#step-3-import-the-solution-file-into-your-environment)
- [Paso 4: Cargar la configuración y los datos maestros de la organización](#step-4-load-configuration-and-master-data-for-your-organization)
    - [Paso 4.1: ¿Cómo se cargan los datos de los archivos de datos?](#step-41-how-to-load-data-from-data-files)
    - [Paso 4.2: Importar datos de configuración obligatorios](#step-42-import-mandatory-configuration-data)
- [Paso 5: Actualizar la personalización de marca de la aplicación móvil](#step-5-update-the-mobile-app-branding)
- [Paso 6: Omitir el consentimiento para aplicaciones móviles](#step-6-bypass-consent-for-mobile-apps)
- [Paso 7: Agregar la clave de Application Insights a aplicaciones móviles para telemetría](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry)
- [Paso 8: Compartir aplicaciones de lienzo con los usuarios de la organización](#step-8-share-canvas-apps-with-users-in-your-organization)
- [Paso 9: Establecer la aplicación móvil como aplicación destacada y prominente](#step-9-set-your-mobile-app-as-hero-and-featured-app)
- [Paso 10: Compartir una aplicación controlada por modelos con administradores de la organización](#step-10-share-model-driven-app-with-admins-in-your-organization)

### <a name="step-1-sign-up-for-power-apps-and-create-an-environment"></a>Paso 1: Registrarse en Power Apps y crear un entorno

Si aún no tiene Power Apps, suscríbase con una licencia adecuada.

Más información:

-   [Precios de Power Apps](https://powerapps.microsoft.com/pricing/)
-   [Compra de Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Una vez que haya adquirido Power Apps, cree un entorno con una base de datos de Common Data Service.

1.  Inicie sesión en el [Centro de administración de Power Platform](https://aka.ms/ppac).

2.  Cree un entorno de Common Data Service con la base de datos. Más información: [Creación y administración de entornos](https://docs.microsoft.com/power-platform/admin/create-environment)

3.  Cree los usuarios adecuados en su entorno. Más información: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>Paso 2: Descargar el paquete de implementación

Obtenga el paquete de implementación (.zip) más reciente de <https://aka.ms/emergency-response-solution> que contiene el archivo de solución, las imágenes y los archivos de datos para configurar las aplicaciones y la lógica de negocios de la aplicación de respuesta ante emergencias.

Para comenzar el proceso de implementación, extraiga el archivo de implementación (. zip) en una ubicación del equipo. La carpeta extraída contendrá las siguientes carpetas:

| **Carpeta/Archivo**       | **Descripción**  |
|-----------------------|------------------|
| **Iconos de aplicación**         | Contiene los iconos de aplicación predeterminados para las aplicaciones móviles (aplicaciones de lienzo).|
| **Archivos de datos**        | Contiene los archivos de datos maestros y de ejemplo (.xlsx) para que funcione la solución o la aplicación. Puede importar datos desde estos archivos para empezar a trabajar en la aplicación. Para más información, consulte [Paso 4: Cargar la configuración y los datos maestros de la organización](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Plantilla de Power BI** | Contiene el archivo de plantilla de informe Power BI (.pbit) que utilizará para configurar los informes para su organización. Más información: [Obtención de información mediante paneles de Power BI](#get-insights-using-power-bi-dashboards)|
| **PowerShell**        | Contiene scripts que usará para configurar las aplicaciones móviles (aplicaciones de lienzo). |
| **Archivo de soluciones**     | Contiene el archivo de soluciones de Common Data Service que crea las aplicaciones y los metadatos necesarios para la aplicación de respuesta ante emergencias.  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>Paso 3: Importar el archivo de solución en el entorno

1.  Vaya a la ubicación donde extrajo el archivo de implementación (.zip); encontrará una carpeta **Archivo de soluciones**. Importaremos el archivo de solución administrada (. zip) en la carpeta **Archivos de soluciones** de nuestro entorno.

2.  Inicie sesión en [Power Apps](https://make.powerapps.com).

3.  Seleccione el entorno en la esquina superior derecha.

4.  En el panel izquierdo, seleccione **Soluciones** y, después, seleccione **Importar**.

    > [!div class="mx-imgBorder"] 
    > ![Importación de la solución](media/conf-import-solution.png "Importación de la solución")

5.  En el cuadro de diálogo **Importación de la solución**, seleccione el archivo de soluciones mencionado en el paso 1 y, a continuación, siga los pasos del asistente para importar la solución.

6.  Una vez que la solución se haya importado correctamente, seleccione **Cerrar** en el cuadro de diálogo de importación y, a continuación, seleccione **Public all customizations** (Todas las personalizaciones públicas). Esta operación puede tardar varios minutos en completarse.

Ahora verá las aplicaciones nuevas en **Aplicaciones**:

> [!div class="mx-imgBorder"] 
> ![Nuevas aplicaciones](media/conf-apps-new-apps.png "Nuevas aplicaciones")

Seleccione la **aplicación de administración** para abrir la aplicación controlada por modelos que le permite configurar el resto de las opciones de implementación. Más información: [¿Qué son las aplicaciones basadas en modelos?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![Abrir aplicación de administración](media/conf-admin-app-open.png "Apertura de la aplicación de administración")

La aplicación de administración tiene varias entidades donde puede agregar y administrar los datos de su sistema hospitalario. Puede usar el selector de área en la parte inferior del panel de navegación izquierdo para seleccionar un área diferente.

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>Paso 4: Cargar la configuración y los datos maestros de la organización

Todos los datos necesarios para la aplicación de respuesta ante emergencias están disponibles en la carpeta **Archivos de datos** en la carpeta de implementación extraída.

La carpeta **Archivos de datos** tiene los siguientes archivos y carpetas:

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Descripción</th>
</tr>
<tr>
<td>En la raíz; están disponibles los siguientes archivos:
<ul>
<li>00 - Acuities Import.xlsx (Importación de triaje)</li>
<li>00 - App Config Import.xlsx (Importación de la configuración de aplicación)</li>
<li>00 - App Import.xlsx (Importación de la aplicación)</li>
<li>00 - Request Roles Import.xlsx (Importación de roles de solicitud)</li>
<li>00 - Supplies Import.xlsx (Importación de suministros)</li>
</ul>
</td>
<td>Estos son los archivos de datos de configuración que se deben importar a las siguientes entidades mediante la aplicación de administración:
<ul>
<li>Acuities (Triaje)</li>
<li>App Config (Configuración de la aplicación)</li>
<li>Aplicaciones</li>
<li>Request Roles (Roles de solicitud)</li>
<li>Supplies Import (Importación de suministros)</li>
</ul>
<br/>La importación de datos a estas entidades creará registros para estas entidades que son necesarios para que funcione la aplicación de respuesta ante emergencias.
<br/>
<br/>
<strong>Precaución</strong>: Asegúrese de que no actualiza los valores de configuración en estas entidades, excepto en las entidades <strong>Apps</strong> (Aplicaciones) y <strong>App Config</strong> (Configuración de aplicaciones), como se explica más adelante.</td>
</tr>
<tr>
<td>Carpeta de <strong>datos de ejemplo</strong></td>
<td><p>La carpeta contiene los archivos de datos de ejemplo (.xlsx) que se pueden importar para rellenar los datos de ejemplo de la aplicación. Los nombres de los archivos sirven para indicar la secuencia en la que los datos se deben importar en la aplicación. </p>
<p>Debe importar datos para las siguientes entidades que contienen los datos de ejemplo maestros de la aplicación de respuesta ante emergencias:
<ul>
<li>Sistemas</li>
<li>regiones</li>
<li>Facilities (Instalaciones)</li>
<li>Ubicaciones</li>
<li>Departamentos</li>
</ul>
<p>Si desea importar los datos de la organización en lugar de los datos de ejemplo, puede reemplazar los datos de ejemplo de estos archivos de Excel por los datos de la organización y, a continuación, importar los datos en la aplicación.</p>
<p>También puede escribir manualmente los datos para estas entidades. Para obtener información sobre cada una de estas entidades y los campos de estas entidades, vea <a href="#manually-configure-and-manage-master-data-for-your-organization">Configuración y administración manual de los datos maestros de la organización</a>.</p></td>
</tr>
<tr>
<td>Carpeta <strong>Archivo de plantilla de datos para datos maestros</strong></td>
<td><p>La carpeta contiene archivos de datos "vacíos" (.xlsx) para las entidades maestras que puede usar para rellenar los datos de la organización y, a continuación, importarlos a la aplicación.</p>
<p>Los nombres de los archivos sirven para indicar la secuencia en la que los datos se deben importar en la aplicación. Se trata de la misma lista de entidades que se mencionó anteriormente para la carpeta de <strong>datos maestros</strong>.</p>
<p>También puede escribir manualmente los datos para estas entidades. Para obtener información sobre cada una de estas entidades y los campos de estas entidades, vea <a href="#manually-configure-and-manage-master-data-for-your-organization">Configuración y administración manual de los datos maestros de la organización</a>.</p>
</td>
</tr>
</table>

#### <a name="step-41-how-to-load-data-from-data-files"></a>Paso 4.1: ¿Cómo se cargan los datos de los archivos de datos?

Para cargar datos de ejemplo de uno de los archivos de datos en una entidad:

1.  En el panel de navegación izquierdo de la aplicación de administración, seleccione una entidad para cargar datos en ella. Por ejemplo, seleccione **Location** (Ubicación) en el selector de área y, a continuación, seleccione **Systems** (Sistemas).

2.  Seleccione **Importar desde Excel** y seleccione el archivo **01 - Load Systems.xlsx** (Cargar sistemas) de la carpeta de **datos de ejemplo**.

    > [!div class="mx-imgBorder"] 
    > ![Importar desde Excel](media/conf-import-from-excel.png "Importar desde Excel")

3.  Continúe con los pasos del asistente de importación para importar los datos.

4.  Una vez importados los datos de ejemplo, verá el registro importado en la entidad:

    > [!div class="mx-imgBorder"] 
    > ![Registro de entidad](media/conf-entity-record.png "Registro en la entidad después de la importación")

Repita los pasos anteriores con otras entidades.

Como alternativa, si desea escribir los datos maestros manualmente, consulte [Configuración y administración manual de los datos maestros de la organización](#manually-configure-and-manage-master-data-for-your-organization).

#### <a name="step-42-import-mandatory-configuration-data"></a>Paso 4.2: Importar datos de configuración obligatorios

La importación de los datos de configuración en las siguientes entidades de la aplicación de administración es **obligatoria** antes de pasar al siguiente paso:

| Nombre del área | Nombre de entidad| Nombre de archivo
|-|-|-
| Ubicaciones | Acuities (Triaje) | 00 - Acuities Import.xlsx (Importación de triaje)
| Administración | Apps Config (Configuración de aplicaciones) | 00 - App Config Import.xlsx (Importación de la configuración de aplicación)
| Administración | Aplicaciones | 00 - App Import.xlsx00 - App Import.xlsx (Importación de la aplicación)
| Staffing (Personal) | Request Roles (Roles de solicitud) | 00 - Request Roles Import.xlsx (Importación de roles de solicitud)
| Ubicaciones | Supplies (Suministros) | 00 - Supplies Import.xlsx (Importación de suministros)

Los datos de otras entidades se pueden agregar [manualmente](#manually-configure-and-manage-master-data-for-your-organization) más adelante o mediante los archivos de datos de ejemplo explicados anteriormente.

### <a name="step-5-update-the-mobile-app-branding"></a>Paso 5: Actualizar la personalización de marca de la aplicación móvil

Puede cambiar el icono o la combinación de colores de las aplicaciones móviles para que coincidan con la personalización de marca de la organización.

Para ello, use las entidades **App** (Aplicación) y **App Config** (Configuración de aplicaciones) del área de **administración** importando los datos de la aplicación y de configuración de la aplicación desde el archivo de Excel disponible en la carpeta **Archivos de datos** del paquete de implementación, tal como se explicó en el paso anterior.

> [!div class="mx-imgBorder"] 
> ![Entidades Apps (Aplicaciones) y App Config (Configuración de aplicaciones)](media/conf-app-app-config-entities.png "Entidades Apps (Aplicaciones) y App Config (Configuración de aplicaciones)")

1.  Asegúrese de que ha importado los datos de configuración para las entidades **Apps** (Aplicaciones) y **App Config** (Configuración de aplicaciones) desde los archivos **App Import.xlsx** (Importación de la aplicación) y **App Config Import.xlsx** (Importación de la configuración de aplicación) respectivamente en el paquete de implementación extraído.

1.  Ahora, se copiarán los identificadores de aplicación de las aplicaciones de lienzo para que podamos rellenarlos en los registros de **aplicaciones** importados. Inicie sesión en [Power Apps](https://make.powerapps.com).

1.  Seleccione el entorno en la esquina superior derecha.

1.  En el panel izquierdo, seleccione **Aplicaciones** y, después, seleccione los puntos suspensivos (...) de una aplicación de lienzo. Finalmente, haga clic en **Detalles**.

    > [!div class="mx-imgBorder"] 
    > ![Detalles de aplicaciones](media/conf-environments-apps-details.png "Detalles de la aplicación")

1.  El identificador de la aplicación aparece en la parte inferior del panel  **Detalles**  para la aplicación. Copie el identificador de la aplicación junto con su nombre en el archivo del Bloc de notas.

    > [!div class="mx-imgBorder"] 
    > ![Identificador de la aplicación de detalles](media/conf-details-app-id.png "Identificador de la aplicación de detalles")

1.  Repita los pasos 3 y 4 para cada una de las aplicaciones de lienzo.

1.  Abra la aplicación de administración y, en el panel de navegación izquierdo, seleccione **Administración** en el selector de área y, a continuación, **Aplicaciones**. Se mostrarán todos los registros de la aplicación de lienzo importados del archivo **App Import.xlsx** (Importación de aplicaciones).

    > [!div class="mx-imgBorder"] 
    > ![Aplicaciones de administración](media/conf-admin-app-records.png "Aplicaciones de administración")

1.  Para abrir uno de los registros de la aplicación, selecciónelo. Observe que el campo del identificador de Power Apps está en blanco.

    > [!div class="mx-imgBorder"] 
    > ![Campo del identificador de aplicación de Power Apps](media/conf-powerapp-id-field.png "Campo del identificador de Power Apps")

1.  Copie el identificador de la aplicación del Bloc de notas (donde lo copió anteriormente en los pasos 2-6) en el campo del **identificador de Power Apps**. También puede actualizar el icono de la aplicación si hace doble clic en el icono en él y especifica otra imagen. Guarde el registro.

1.  Repita el paso 9 para cada registro de la aplicación de lienzo en **Aplicaciones** para agregar el valor del **identificador de Power Apps**.

1.  En el panel izquierdo, seleccione **App Config** (Configuración de aplicaciones).

1.  Seleccione el registro de la **aplicación de respuesta ante emergencias** para abrirlo para su edición.

    1.  Haga doble clic en el icono para especificar una nueva imagen como icono de la aplicación.

    2.  Actualice los nombres de aplicación y sus colores.

    3.  Seleccione **Yes** (Sí) o **No** en el campo **Device Sharing Enabled** (Uso compartido de dispositivos habilitado) para especificar si una la opción de **cerrar sesión** estará disponible en las aplicaciones móviles. Si selecciona **Yes** (Sí), habrá una opción para **cerrar sesión** disponible.

    > [!div class="mx-imgBorder"] 
    > ![Campo de uso compartido de dispositivos habilitado](media/conf-device-sharing-enabled-field.png "Campo de uso compartido de dispositivos habilitado")

1.  Seleccione **Guardar** en la esquina inferior derecha para guardar los cambios.

### <a name="step-6-bypass-consent-for-mobile-apps"></a>Paso 6: Omitir el consentimiento para aplicaciones móviles

Debe ser un administrador de inquilinos para completar este paso. Además, antes de realizar este paso, necesitará el identificador de aplicación de cada aplicación móvil (aplicación de lienzo).

Para obtener el identificador de aplicación, en el panel de navegación izquierdo, seleccione **Administración** en el selector de área y, a continuación, **Aplicaciones**. Esto muestra todas las aplicaciones móviles (aplicaciones de lienzo). Seleccione una aplicación móvil para ver su identificador de aplicación. Copie el identificador de la aplicación de cada aplicación en un archivo del Bloc de notas.

> [!div class="mx-imgBorder"] 
> ![Obtención del identificador de aplicación](media/conf-admin-get-app-id.png "Obtener el identificador de aplicación")

A continuación, haga lo siguiente:

1.  Abra el Bloc de notas y copie este script de PowerShell:

    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell
    
    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount
    
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppApisToBypassConsent -AppName APPGUIDHERE
    ```

2.  Reemplace el valor `APPGUIDHERE` de cada línea por el identificador de aplicación real de una aplicación de lienzo.

3.  Guarde el archivo con la extensión .ps.

4.  Ejecute PowerShell como administrador y luego el archivo .ps que acaba de crear.

5.  Repita los pasos 2 y 4 para cada una de las aplicaciones de lienzo.

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry"></a>Paso 7: Agregar la clave de Application Insights a aplicaciones móviles para telemetría

Puede usar Azure Application Insights para recopilar información detallada de la telemetría de las aplicaciones móviles (aplicaciones de lienzo) con el fin de obtener información sobre el uso de la aplicación. Para obtener información detallada al respecto, consulte [Registro de telemetría para las aplicaciones con Azure Application Insights](https://powerapps.microsoft.com/blog/log-telemetry-for-your-apps-using-azure-application-insights/).

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>Paso 8: Compartir aplicaciones de lienzo con los usuarios de la organización

Para que los usuarios de primera línea puedan usar y consumir datos mediante las aplicaciones de lienzo en sus dispositivos móviles, las aplicaciones deben compartirse con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con grupos de usuarios.

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  En el panel de navegación izquierdo, seleccione **Aplicaciones** para ver una lista de todas las aplicaciones.

3.  Seleccione una aplicación móvil (aplicación de lienzo) y seleccione **Compartir** en el banner.

    > [!div class="mx-imgBorder"] 
    > ![Compartir aplicaciones de lienzo](media/conf-share-canvas-apps.png "Compartir aplicaciones de lienzo")

4.  Especifique el grupo o los usuarios de Azure AD con los que desea compartir esta aplicación. A medida que la aplicación se conecte a los datos de Common Data Service, también deberá proporcionar permisos a las entidades. El panel para compartir le pide que administre la seguridad de las entidades. Asigne los roles de seguridad **COVID 19 End User** (Usuario final de COVID 19) y **Usuario de Common Data Service** a las entidades utilizadas por esta aplicación y seleccione **Compartir**.

    > [!div class="mx-imgBorder"] 
    > ![Compartir la aplicación con grupo o usuarios de Azure AD](media/conf-share-app-groups-users.png "Compartir la aplicación con grupo o usuarios de Azure AD")

5.  Repita los pasos 3 y 4 para cada una de las aplicaciones móviles.

Información detallada sobre el uso compartido de las aplicaciones: [Uso compartido de una aplicación de lienzo](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

### <a name="step-9-set-your-mobile-app-as-hero-and-featured-app"></a>Paso 9: Establecer la aplicación móvil como aplicación destacada y prominente

Este paso le permite establecer la aplicación móvil como destacada y prominente en la aplicación móvil de **Power Apps**. Debe ser un administrador de inquilinos para completar este paso.

Antes de realizar este paso, necesitará el identificador de aplicación de cada aplicación móvil (aplicación de lienzo) que desee establecer como aplicación destacada y prominente. Para obtener información sobre cómo obtener el identificador de aplicación de una aplicación de lienzo, consulte [Paso 6: Omitir el consentimiento para aplicaciones móviles](#step-6-bypass-consent-for-mobile-apps)

A continuación, haga lo siguiente:

1.  Abra el Bloc de notas y copie este script de PowerShell:


    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell

    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount

    # Use the "Emergency Response App" App ID
    # To clear a featured app use Clear-AdminPowerAppAsFeatured

    #Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsFeatured -AppName APPGUIDHERE

    # To clear a hero app use Clear-AdminPowerAppAsHero
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsHero -AppName APPGUIDHERE
    ```

2.  Reemplace el valor de `APPGUIDHERE` en cada línea por el identificador de aplicación real de la aplicación que desea establecer como destacada y prominente, respectivamente.

3.  Guarde el archivo con la extensión .ps.

4.  Ejecute PowerShell como administrador y luego el archivo .ps que acaba de crear.

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>Paso 10: Compartir una aplicación controlada por modelos con administradores de la organización

Para que los usuarios administradores usen la aplicación de administración (aplicación controlada por modelos), debe compartirse con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con un grupo de usuarios administradores.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

2. En el panel de navegación izquierdo, seleccione Aplicaciones para ver una lista de todas las aplicaciones.

3. Seleccione la aplicación controlada por modelos (**Admin App – Emergency Response App**) (Aplicación de administración - Aplicación de respuesta ante emergencias) y seleccione **Compartir** en el banner.

4. Especifique el grupo de Azure AD o los usuarios administradores con los que desea compartir esta aplicación, asigne el rol de seguridad **Emergency Response Admin** (Administrador de respuesta ante emergencias) y seleccione **Compartir**.


## <a name="manually-configure-and-manage-master-data-for-your-organization"></a>Configuración y administración manual de los datos maestros de la organización

Los administradores pueden usar la aplicación controlada por modelos en [Power Apps](https://make.powerapps.com) para crear y administrar los datos maestros de su organización. Estos datos son necesarios para que funcione la aplicación de respuesta ante emergencias.

> [!NOTE]
> También puede importar los datos de la organización en archivos de datos disponibles en el paquete de implementación y, a continuación, importarlos en estas entidades. Más información: [Paso 4: Cargar la configuración y los datos maestros de la organización](#step-4-load-configuration-and-master-data-for-your-organization)

Debe agregar datos maestros en estas entidades en la secuencia siguiente:

1. [Systems](#systems-data) (Sistemas)

1. [Regiones](#regions-data)

1. [Facilities](#facilities-data) (Instalaciones)

1. [Ubicaciones](#locations-data)

1. [Departments](#departments-data) (Departamentos)

Los datos maestros se administran desde el área **Locations** (Ubicaciones) en el panel de navegación izquierdo de la aplicación de administración:

> [!div class="mx-imgBorder"]
> ![locations-area](media/locations-area.png)

Las entidades del área **Hierarchy** (Jerarquía) se muestran en el orden en que se deben rellenar los datos.

### <a name="systems-data"></a>Datos de sistemas

La entidad **Systems** (Sistemas) le permite crear y administrar entradas para sistemas hospitalarios. Puede administrar varios sistemas hospitalarios dentro de la misma organización.

Para crear un registro:

1. Seleccione **Systems** (Sistemas) en el panel izquierdo y luego **Nuevo**:  
    > [!div class="mx-imgBorder"]
    > ![select-systems-new](media/select-systems-new.png)

2. En la página **New System** (Nuevo sistema), especifique los valores adecuados:  
   > [!div class="mx-imgBorder"]
   > ![enter-details-new-system](media/enter-details-new-system.png)

   | **Campo**            | **Descripción**                                    |
   |----------------------|----------------------------------------------------|
   | Nombre del sistema          | Escriba un nombre para el hospital.                     |
   | Descripción          | Escriba una descripción opcional.                      |
   | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de este sistema hospitalario. |
   | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de este sistema hospitalario.   |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Systems** (Sistemas).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="regions-data"></a>Datos de regiones

La entidad **Regions** (Regiones) permite administrar las regiones geográficas de los sistemas hospitalarios.

Para crear un registro:

1. Seleccione **Regions** (Regiones) en el panel izquierdo y luego **Nuevo**:

2. En la página **New Region** (Nueva región), especifique los valores adecuados:  

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-region](media/enter-details-new-region.png)

    | **Campo**            | **Descripción**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | Sistema               | Seleccione un sistema hospitalario. Esta lista se rellena en función de los datos de **Systems** (Sistemas) que ha creado anteriormente. |
    | Nombre de región          | Escriba el nombre de la región. Por ejemplo, Seattle.                                                              |
    | Descripción          | Escriba una descripción opcional.                                                                            |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de este sistema hospitalario.                                                       |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de este sistema hospitalario.                                                         |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Regions** (Regiones).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="facilities-data"></a>Datos de instalaciones

La entidad **Facilities** (Instalaciones) permite administrar las ubicaciones de los centros hospitalarios dentro de cada región. Por ejemplo, las instalaciones de **Redmond** y **Bellevue** en la región de **Seattle**.

Para crear un registro:

1. Seleccione **Facilities** (Instalaciones) en el panel izquierdo y luego **Nuevo**:

2. En la página **New Facility** (Nueva instalación), especifique los valores adecuados: 

    > [!div class="mx-imgBorder"] 
    > ![enter-details-new-facility](media/enter-details-new-facility.png)

    | **Campo**            | **Descripción**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Región               | Seleccione una región. Esta lista se rellena en función de los datos de **Regions** (Regiones) que ha creado anteriormente. |
    | Facility Name (Nombre de la instalación)        | Escriba el nombre de la instalación. Por ejemplo, Bellevue.                                                  |
    | Descripción          | Escriba una descripción opcional.                                                                   |
    | Total Vents (Respiradores totales)          | Escriba el número total de respiradores disponibles en la instalación                                  |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de esta instalación.                                                     |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de esta instalación.                                                       |

    Si es necesario, escriba la dirección de la instalación.

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Facilities** (Instalaciones).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="locations-data"></a>Datos de ubicaciones

La entidad **Locations** (Ubicaciones) permite administrar ubicaciones específicas dentro de cada instalación hospitalaria.

> [!NOTE]
> Antes de crear un registro de **Locations** (Ubicaciones), asegúrese de que ha importado los datos del triaje mediante el archivo**00 - Acuities Import.xlsx** (Importación de triaje) como se explicó anteriormente en [Paso 4: Cargar la configuración y los datos maestros de la organización](#step-4-load-configuration-and-master-data-for-your-organization). Esto se debe a que la información del triaje es necesaria para crear un registro relativo a la **ubicación**.

Para crear un registro:

1. Seleccione **Locations** (Ubicaciones) en el panel izquierdo y luego **Nuevo**.

2. En la página **New Location** (Nueva ubicación), especifique los valores adecuados:  
 
    > [!div class="mx-imgBorder"]
    > ![enter-details-new-location](media/enter-details-new-location.png)

    | **Campo**            | **Descripción**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Nombre de la ubicación        | Escriba el nombre de la ubicación.                                                                       |
    | Facility             | Seleccione una instalación. Esta lista se rellena en función de los datos de **Facilities** (Instalaciones) que ha creado anteriormente. |
    | Floor                | Escriba la información de la planta de la instalación.                                                         |
    | Unidad                 | Escriba la información de la unidad de la instalación.                                                           |
    | Location Acuity (Triaje de la ubicación)      | Seleccione el registro de triaje asociado a esta ubicación.                                                                                                     |
    | Total Beds (Camas totales)           | Escriba el número total de camas de la instalación.                                                       |
    | Blocked beds (Camas bloqueadas)         | Escriba el número de camas bloqueadas de la instalación.                                                     |
    | Last Census (Último censo)          | Se rellena basándose en el último registro del censo que se está creando.                                             |
    | Occupancy Percentage (Porcentaje de ocupación) | Se calcula automáticamente según el último censo y el total de camas.                                         |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de este sistema hospitalario.                                                   |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de este sistema hospitalario.                                                     |
    | Location Order (Orden de la ubicación)       | Escriba un número que ordene la ubicación en las listas desplegables de ubicación.                               |
    | Alternate Site Flag (Marca de sitio alternativo)  | Para uso interno                                                                                     |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Locations** (Ubicaciones).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="departments-data"></a>Datos de departamentos

La entidad **Departments** (Departamentos) le permite administrar la información de los departamentos de un hospital.

Para crear un registro:

1. Seleccione **Departments** (Departamentos) en el panel izquierdo y luego **Nuevo**.

2. En la página **New Departments** (Nuevo departamento), especifique los valores adecuados:    

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-department](media/enter-details-new-department.png)

    | **Campo**            | **Descripción**                                    |
    |----------------------|----------------------------------------------------|
    | Nombre de departamento      | Escriba el nombre de un departamento.                            |
    | Descripción          | Escriba una descripción opcional.                      |
    | Effective Start Date (Fecha de inicio efectiva) | Escriba la fecha y hora de inicio de este sistema hospitalario. |
    | Effective End Date (Fecha de fin efectiva)   | Escriba la fecha y hora de fin de este sistema hospitalario.   |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Departments** (Departamentos).

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

## <a name="get-insights-using-common-data-service-dashboards"></a>Obtención de información mediante paneles de Common Data Service

Los siguientes paneles están disponibles de forma predeterminada en la aplicación del administrador de respuesta ante emergencias (controlada por modelos):

- **Bed Management** (Administración de camas)

   Muestra la disponibilidad de las camas, el porcentaje de ocupación y el número total de camas en diferentes instalaciones.

- **Equipment and Supply** (Equipos y suministro)

  Muestra el equipo crítico en uso y los suministros disponibles en diferentes instalaciones.

- **Staff Management** (Administración de personal)

  Muestra el número de miembros de trabajadores solicitados, asignados y disponibles en diferentes instalaciones.

- **COVID Patients** (Pacientes COVID)

  Muestra el número de pacientes en investigación y confirmados positivos en COVID-19 en diferentes instalaciones.

- **Discharges** (Altas)

  Muestra el número de pacientes previstos para alta y las altas reales.

También puede crear sus propios paneles además de los paneles disponibles de forma predeterminada.

### <a name="manage-dashboards"></a>Administración de paneles

Para administrar paneles:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y vaya a la aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Paneles** desde el selector de áreas:

    > [!div class="mx-imgBorder"]
    > ![select-dashboards](media/select-dashboards.png)

3. Seleccione un nombre de panel en el panel de navegación izquierdo para ver los gráficos:

    > [!div class="mx-imgBorder"]
    > ![view-charts](media/view-charts.png)

    > [!NOTE]
    > Puede filtrar los datos en la parte inferior de la pantalla y los gráficos de la parte superior se actualizan automáticamente con los valores filtrados.

4. Seleccione la opción de **expandir** para ver un gráfico en modo de pantalla completa:

    > [!div class="mx-imgBorder"]
    > ![select-expand](media/select-expand.png)

### <a name="additional-analysis"></a>Análisis adicional

- **Explorar en profundidad**: Puede seleccionar el área del gráfico para profundizar con atributos (campos) adicionales de una entidad:

    > [!div class="mx-imgBorder"]
    > ![select-chart-area-drill-down](media/select-chart-area-drill-down.png)

- **Actualizar**: Puede actualizar los paneles para reflejar los datos actualizados. Puede actualizar todos los gráficos en un panel específico con **Actualizar todo** o un gráfico seleccionado con **Actualizar**:

    > [!div class="mx-imgBorder"]
    > ![refresh-dashboards](media/refresh-dashboards.png)

- **Ver registros** Seleccione **Más comandos** ( **...** ) y, a continuación, **Ver registros** para ver todos los registros asociados a un gráfico determinado:

    > [!div class="mx-imgBorder"]
    > ![select-more-commands](media/select-more-commands.png)

    > [!NOTE] 
    > Al seleccionar **Ver registros**, verá la vista de la división de entidades entre el gráfico y los registros. Cualquier cambio en los filtros de los registros del lado derecho se refleja con actualizaciones automáticas del gráfico en el lado izquierdo de la pantalla.

Para obtener más información sobre la edición de un panel existente y la actualización de las propiedades de los gráficos, lea [Editar un panel existente](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Creación de paneles

También puede crear sus propios paneles y personalizarlos para adaptarse a sus necesidades. Para crear un panel, seleccione **Nuevo** y luego **Panel de Dynamics 365**.

> [!div class="mx-imgBorder"]
> ![select-new-dynamics-dashboard](media/select-new-dynamics-dashboard.png)

Para obtener más información sobre la creación de un nuevo panel, lea [Crear un panel](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="get-insights-using-power-bi-dashboards"></a>Obtención de información mediante paneles de Power BI

Publique el panel de Power BI y compártalo con los usuarios de su organización para que puedan usarlo para obtener información y tomar decisiones.

### <a name="prerequisites"></a>Requisitos previos

- Licencias de capacidad premium de Power BI o Power BI Pro asignadas a los usuarios que tienen acceso al informe. 

- Cree un área de trabajo en Power BI donde publicar el informe. Inicie sesión en Power BI y cree un área de trabajo. Más información: [Crear las nuevas áreas de trabajo en Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Instale Power BI Desktop desde la Tienda de aplicaciones de Windows: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Si ha instalado Power BI mediante la descarga directa desde el sitio de Power BI como un archivo ejecutable en algún momento anterior, quítelo y use el de la Tienda de aplicaciones. La versión de la Tienda de aplicaciones se irá actualizando automáticamente a medida que estén disponibles nuevas versiones.

- Después de instalar Power BI Desktop desde la Tienda de aplicaciones, ejecútelo e inicie sesión con una cuenta que tenga permiso para publicar aplicaciones de Power BI en su organización.

### <a name="publish-the-power-bi-dashboard"></a>Publicación del panel de Power BI

1. Vaya a la ubicación donde extrajo el paquete de implementación. Encontrará el archivo **Emergency Response App.pbit** en la carpeta **Plantilla de Power BI**.

2. Abra el archivo **Emergency Response App.pbit** en Power BI Desktop. Cuando este archivo se abra en Power BI Desktop, verá un cuadro de diálogo **Actualizar** que indica que se ha producido un error en la actualización de los datos. Esto se debe a que aún no se han especificado los detalles de conexión en el entorno de Common Data Service.

3. Seleccione **Transformar datos** para especificar la conexión con su entorno de Common Data Service.  
    
    > [!div class="mx-imgBorder"]
    > ![select-transform-data](media/select-transform-data.png)

4. En el editor de consultas, actualice el parámetro **CDSBaseURL** con la dirección URL de su entorno de Common Data Service. Haga clic con el botón derecho en **CDSBaseURL**, seleccione **Editor avanzado** y, a continuación, especifique el valor adecuado.  

    > [!div class="mx-imgBorder"]
    > ![select-advanced-editor](media/select-advanced-editor.png)

5. Guarde los cambios. Aparece un mensaje que le pide que aplique los cambios pendientes a la consulta. Seleccione **Aplicar**.

6. Se le pedirá que escriba las credenciales para conectarse a su entorno de Common Data Service. Seleccione **Cuenta de organización** > **Inicio de sesión** para especificar las credenciales de Common Data Service.  

    > [!div class="mx-imgBorder"]
    > ![select-organizational-account](media/select-organizational-account.png)

7. Seleccione **Conectar** para establecer una conexión.

8. Si la conexión se realiza correctamente, se le pedirá que guarde el archivo como un archivo .pbix junto con la información del entorno de Common Data Service. Proporcione un nombre y guárdelo en el equipo.

9. En la pestaña **Inicio**, seleccione **Cerrar y aplicar**.

10. Seleccione **Actualizar** para actualizar los datos desde el entorno de Common Data Service. Seleccione **Publicar** para publicar datos en el área de trabajo de Power BI.  
    
    > [!div class="mx-imgBorder"]
    > ![select-refresh-publish](media/select-refresh-publish.png)

11. En la página **Publicar en Power BI**, seleccione el área de trabajo en la que desea publicar.

12. El informe estará disponible en el área de trabajo. Ahora, configuraremos la actualización de datos para el conjunto de datos. Seleccione el conjunto de datos en el área de trabajo y seleccione el icono **Programar actualización**.  
    
    > [!div class="mx-imgBorder"]
    > ![schedule-refresh](media/schedule-refresh.png)

13. En la página de configuración del conjunto de datos, expanda **Credenciales del origen de datos** y seleccione **Editar credenciales** para asegurarse de que los detalles de conexión para conectarse a su origen de datos son correctos.  

    > [!div class="mx-imgBorder"]
    > ![select-edit-credentials](media/select-edit-credentials.png)

14. Expanda **Actualización programada** y especifique los detalles necesarios para actualizar los datos en función de una programación.

    > [!NOTE] 
    > Hay límites en el número de veces que se pueden actualizar los datos. Power BI limita los conjuntos de datos en la capacidad compartida a ocho actualizaciones diarias. Si el conjunto de datos reside en una capacidad Premium, puede programar hasta 48 actualizaciones al día en la configuración de dicho conjunto de datos. Más información: [Actualización de datos](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

15. Seleccione el nombre del área de trabajo en el panel izquierdo y, a continuación, seleccione **Crear aplicación** en la esquina superior derecha.  

    > [!div class="mx-imgBorder"]
    > ![select-create-app](media/select-create-app.png)

16. En la página de publicación de aplicaciones:

    1. En la pestaña **Configuración**, especifique el nombre y la descripción de la aplicación.

    2. En la pestaña **Navegación**, especifique la ubicación del panel en el que se publicará.

    3. En la pestaña **Permisos**, especifique los usuarios o el grupo que podrán ver esta aplicación. Asegúrese de activar la casilla **Instalar esta aplicación automáticamente** para instalar esta aplicación automáticamente para los usuarios finales. Más información: [Instalar aplicaciones para usuarios finales de forma automática](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![select-install-apps-automatically](media/select-install-apps-automatically.png)

17. Seleccione **Publicar aplicación**. Para obtener información detallada sobre cómo publicar aplicaciones en Power BI, consulte [Publicar la aplicación](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).

### <a name="view-the-power-bi-dashboard"></a>Visualización del panel de Power BI

Inicie sesión en [Power BI](https://apps.powerbi.com) para obtener acceso al panel de Power BI y verlo.

> [!div class="mx-imgBorder"]
> ![view-power-dashboard](media/view-power-dashboard.png)

## <a name="view-and-manage-app-feedback"></a>Visualización y administración de los comentarios de la aplicación

Todos los comentarios que proporciona el personal de primera línea que utiliza las aplicaciones de lienzo en sus dispositivos móviles se almacenan en la entidad **App Feedback** (Comentarios de la aplicación), y los administradores pueden verlos y administrarlos mediante el área de **administración** del panel de navegación izquierdo de la aplicación de administración.

Para ver y administrar los comentarios de la aplicación:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y vaya a la aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Administración** desde el selector de áreas:

3. Seleccione **App Feedback** (Comentarios de la aplicación) para ver una lista de los comentarios de la aplicación enviados por los usuarios. Puede hacer clic en un registro para ver los detalles y marcarlos como revisados o no.  

    > [!div class="mx-imgBorder"]
    > ![select-app-feedback](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para notificar un problema con la aplicación de ejemplo de respuesta ante emergencias, visite <https://aka.ms/emergency-response-issues>.

- Para ofrecer comentarios sobre la aplicación de ejemplo de respuesta ante emergencias, visite <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Siguiente paso

[Uso de la aplicación de respuesta ante emergencias](use.md)