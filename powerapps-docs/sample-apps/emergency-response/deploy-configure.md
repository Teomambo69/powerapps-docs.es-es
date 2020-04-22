---
title: Implementación de la aplicación de respuesta ante emergencias hospitalarias | Microsoft Docs
description: Proporciona instrucciones detalladas para que los administradores de TI de hospitales implementen y configuren la aplicación de ejemplo para su organización.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/15/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 132276b88fe23e9ea4a69caeff330c10f7d32daf
ms.sourcegitcommit: 371fb08328f88f8bae7335db413d52b5c961c3e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544024"
---
# <a name="deploy-the-hospital-emergency-response-app"></a>Implementación de la aplicación Respuesta ante emergencias hospitalarias

La aplicación Respuesta ante emergencias hospitalarias requiere el ajuste de algunos parámetros para adaptarse a sus necesidades. Este artículo proporciona instrucciones paso a paso para que los administradores de TI de hospitales implementen y configuren la aplicación para su organización.

Tiempo estimado para completar estos pasos: **35–40 minutos**.

## <a name="demo-deploy-the-hospital-emergency-response-app"></a>Demostración: Implementación de la aplicación Respuesta ante emergencias hospitalarias

Vea cómo puede implementar y configurar la aplicación Respuesta ante emergencias hospitalarias.

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="service-urls-for-us-government-customers"></a>Direcciones URL de servicio para clientes de la Administración Pública

La solución Respuesta ante emergencias hospitalarias también está disponible para los clientes de la Administración Pública de EE. UU. Hay un conjunto diferente de direcciones URL para acceder a los entornos de Power Apps para la Administración Pública de Estados Unidos que el que contiene la versión comercial.

En este artículo se usa la versión comercial de la dirección URL del servicio. Si es un cliente de la Administración pública de Estados Unidos, use la dirección URL de dicha entidad para la implementación, tal y como se menciona aquí:


| **Dirección URL de la versión comercial**                | **Dirección URL de la versión de la Administración Pública de Estados Unidos**  |
|-------------------------------------------|--------------------------------|
| https://make.powerapps.com                | https://make.gov.powerapps.us (GCC)<br/><br/>https://make.high.powerapps.us (GCC High)                |
| https://admin.powerplatform.microsoft.com | https://gcc.admin.powerplatform.microsoft.us (GCC)<br/><br/>https://high.admin.powerplatform.microsoft.us (GCC High) |
| https://app.powerbi.com/                  | <https://app.powerbigov.us> (GCC)<br/><br/>https://app.high.powerbigov.us (GCC High)                  |

Para más información sobre los planes de la Administración Pública de Estados Unidos para Power Apps y Power BI, consulte:
- [Power Apps para la Administración Pública de Estados Unidos](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI para la Administración Pública de Estados Unidos](https://docs.microsoft.com/power-bi/service-govus-overview)


## <a name="deploy-the-hospital-emergency-response-app"></a>Implementación de la aplicación Respuesta ante emergencias hospitalarias

Siga estos pasos para implementar la aplicación de ejemplo Respuesta ante emergencias hospitalarias para su organización.

- [Paso 1: Registrarse en Power Apps y crear un entorno](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [Paso 2: Descargar el paquete de implementación](#step-2-download-the-deployment-package)
- [Paso 3: Importar el archivo de solución en el entorno](#step-3-import-the-solution-file-into-your-environment)
- [Paso 4: Cargar la configuración y los datos maestros de la organización](#step-4-load-configuration-and-master-data-for-your-organization)
    - [Paso 4.1: Cargar datos de configuración obligatorios](#step-41-load-mandatory-configuration-data)
    - [Paso 4.2: Cargar datos maestros](#step-42-load-master-data)
- [Paso 5: Actualizar la personalización de marca de la aplicación móvil](#step-5-update-the-mobile-app-branding)
- [Paso 6: Omitir el consentimiento para aplicaciones móviles](#step-6-bypass-consent-for-mobile-apps)
- [Paso 7: Agregar la clave de Azure Application Insights a las aplicaciones móviles para obtener la telemetría (opcional)](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional)
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

    > [!IMPORTANT]
    > Si selecciona un grupo de seguridad para la base de datos al crearla, las aplicaciones se podrán compartir *solo* con usuarios que sean miembros del grupo de seguridad.

3.  Cree los usuarios adecuados en su entorno. Más información: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>Paso 2: Descargar el paquete de implementación

Obtenga el paquete de implementación (.zip) más reciente de <https://aka.ms/emergency-response-solution> que contenga el archivo de solución, las imágenes y los archivos de datos para configurar las aplicaciones y la lógica de negocios de la aplicación Respuesta ante emergencias hospitalarias.

> [!IMPORTANT]
> Antes de extraer el paquete de implementación (archivo .zip), asegúrese de desbloquear el archivo. Para desbloquearlo:
> 1. Haga clic con el botón derecho en el archivo .zip y seleccione **Propiedades**.
> 2. En el cuadro de diálogo Propiedades, seleccione **Desbloquear** y, luego, elija **Aplicar** seguido de **Aceptar**.

<br/>

Después de desbloquear el archivo de implementación (archivo .zip), extraiga el archivo en una ubicación del equipo. La carpeta extraída contendrá las siguientes carpetas:

| **Carpeta/Archivo**       | **Descripción**  |
|-----------------------|------------------|
| **Iconos de aplicación**         | Contiene los iconos de aplicación predeterminados para las aplicaciones móviles (aplicaciones de lienzo).|
| **Archivos de datos**        | Contiene los archivos de datos maestros y de ejemplo (.xlsx) para que funcione la solución o la aplicación. Puede importar datos desde estos archivos para empezar a trabajar en la aplicación. Para más información, consulte [Paso 4: Cargar la configuración y los datos maestros de la organización](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Plantilla de Power BI** | Contiene el archivo de plantilla de informe Power BI (.pbit) que utilizará para configurar los informes para su organización. Más información: [Publicación del panel de Power BI](#publish-the-power-bi-dashboard)|
| **PowerShell**        | Contiene scripts que usará para configurar las aplicaciones móviles (aplicaciones de lienzo). |
| **Archivo de soluciones**     | Contiene el archivo de soluciones de Common Data Service que crea las aplicaciones y los metadatos necesarios para la aplicación Respuesta ante emergencias hospitalarias.  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>Paso 3: Importar el archivo de solución en el entorno

1.  Vaya a la ubicación donde extrajo el archivo de implementación (.zip); encontrará una carpeta **Archivo de soluciones**. Importaremos el archivo de solución administrada (. zip) en la carpeta **Archivos de soluciones** de nuestro entorno.

2.  Inicie sesión en [Power Apps](https://make.powerapps.com).

3.  Seleccione el entorno en la esquina superior derecha.

4.  En el panel izquierdo, seleccione **Soluciones** y, después, seleccione **Importar**.

    > [!div class="mx-imgBorder"] 
    > ![Importación de la solución](media/conf-import-solution.png "Importación de la solución")

5.  En el cuadro de diálogo **Importación de la solución**, seleccione el archivo de soluciones mencionado en el paso 1 y, a continuación, siga los pasos del asistente para importar la solución.

6.  Una vez que la solución se haya importado correctamente, seleccione **Cerrar** en el cuadro de diálogo de importación.

Ahora verá las aplicaciones nuevas en **Aplicaciones**:

> [!div class="mx-imgBorder"] 
> ![Nuevas aplicaciones](media/conf-apps-new-apps.png "Nuevas aplicaciones")

Seleccione la **aplicación de administración** para abrir la aplicación controlada por modelos que le permite configurar el resto de las opciones de implementación. Más información: [¿Qué son las aplicaciones basadas en modelos?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![Abrir aplicación de administración](media/conf-admin-app-open.png "Apertura de la aplicación de administración")

La aplicación de administración tiene varias entidades donde puede agregar y administrar los datos de su sistema hospitalario. Puede usar el selector de área en la parte inferior del panel de navegación izquierdo para seleccionar un área diferente.

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>Paso 4: Cargar la configuración y los datos maestros de la organización

Todos los datos necesarios para la aplicación Respuesta ante emergencias hospitalarias están disponibles en la carpeta **Archivos de datos** en la carpeta de implementación extraída.

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
<br/>La importación de datos a estas entidades creará para ellas registros que son necesarios para que funcione la aplicación Respuesta ante emergencias hospitalarias.
<br/>
<br/>
<strong>Precaución</strong>: Asegúrese de que no actualiza los valores de configuración en estas entidades, excepto en las entidades <strong>Apps</strong> (Aplicaciones) y <strong>App Config</strong> (Configuración de aplicaciones), como se explica más adelante.</td>
</tr>
<tr>
<td>Carpeta de <strong>datos de ejemplo</strong></td>
<td><p>La carpeta contiene los archivos de datos de ejemplo (.xlsx) que se pueden importar para rellenar los datos de ejemplo de la aplicación. Los nombres de los archivos sirven para indicar la secuencia en la que los datos se deben importar en la aplicación. </p>
<p>Importe datos para las siguientes entidades que contengan los datos de ejemplo maestros de la aplicación Respuesta ante emergencias hospitalarias:
<ul>
<li>Sistemas</li>
<li>regiones</li>
<li>Facilities (Instalaciones)</li>
<li>Ubicaciones</li>
<li>Departamentos</li>
</ul>
<p>Si desea importar los datos de la organización en lugar de los datos de ejemplo, puede reemplazar los datos de ejemplo de estos archivos de Excel por los datos de la organización y, a continuación, importar los datos en la aplicación.</p>
<p>También puede escribir manualmente los datos para estas entidades. Para obtener información sobre cada una de estas entidades y los campos de estas entidades, vea <a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">Configuración y administración de los datos maestros de la organización</a>.</p></td>
</tr>
<tr>
<td>Carpeta <strong>Archivo de plantilla de datos para datos maestros</strong></td>
<td><p>La carpeta contiene archivos de datos "vacíos" (.xlsx) para las entidades maestras que puede usar para rellenar los datos de la organización y, a continuación, importarlos a la aplicación.</p>
<p>Los nombres de los archivos sirven para indicar la secuencia en la que los datos se deben importar en la aplicación. Se trata de la misma lista de entidades que se mencionó anteriormente para la carpeta de <strong>datos maestros</strong>.</p>
<p>También puede escribir manualmente los datos para estas entidades. Para obtener información sobre cada una de estas entidades y los campos de estas entidades, vea <a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">Configuración y administración de los datos maestros de la organización</a>.</p>
</td>
</tr>
</table>

#### <a name="step-41-load-mandatory-configuration-data"></a>Paso 4.1: Cargar datos de configuración obligatorios

La importación de los datos de configuración en las siguientes entidades de la aplicación de administración es **obligatoria** antes de pasar al siguiente paso:

| Nombre del área | Nombre de entidad| Nombre de archivo
|-|-|-
| Ubicaciones | Acuities (Triaje) | 00 - Acuities Import.xlsx (Importación de triaje)
| Administración | Apps Config (Configuración de aplicaciones) | 00 - App Config Import.xlsx (Importación de la configuración de aplicación)
| Administración | Aplicaciones | 00 - App Import.xlsx00 - App Import.xlsx (Importación de la aplicación)
| Staffing (Personal) | Request Roles (Roles de solicitud) | 00 - Request Roles Import.xlsx (Importación de roles de solicitud)
| Ubicaciones | Supplies (Suministros) | 00 - Supplies Import.xlsx (Importación de suministros)

##### <a name="how-to-load-data-from-data-files"></a>¿Cómo se cargan los datos de los archivos de datos?

Para importar datos de uno de los archivos de datos en una entidad:

1.  En el panel de navegación izquierdo de la aplicación de administración, seleccione una entidad para cargar datos en ella. Por ejemplo, seleccione **Administration** (Administración) en el selector de área y, a continuación, **Acuities** (Triaje).

2.  Seleccione **Importar desde Excel** y seleccione el archivo **00 - Acuities Import.xlsx** (Importación de triaje) de la carpeta **Archivos de datos**.

    > [!div class="mx-imgBorder"]
    > ![Importar desde Excel](media/conf-import-from-excel.png "Importar desde Excel")

3.  Continúe con los pasos del asistente de importación para importar los datos.

4.  Una vez importados los datos, verá el registro importado en la entidad:

    > [!div class="mx-imgBorder"] 
    > ![Registro de entidad](media/conf-entity-record.png "Registro en la entidad después de la importación")

Repita los pasos anteriores con otras entidades de datos de configuración.

Como alternativa, si desea escribir los datos maestros manualmente, consulte [Configuración y administración de los datos maestros de la organización](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization).

#### <a name="step-42-load-master-data"></a>Paso 4.2: Cargar datos maestros

Tal y como se ha explicado anteriormente:
- Puede usar los archivos de datos de ejemplo para las entidades de datos maestros en la carpeta **Archivos de datos/Datos de ejemplo** para importar los datos de ejemplo en las entidades necesarias. 

- Puede usar los archivos de datos "vacíos" para las entidades de datos maestros en la carpeta **Archivos de datos/Archivo de plantilla de datos para datos maestros**, que puede emplear para rellenar los datos de la organización y, a continuación, importar los datos en las entidades necesarias.

También puede agregar los datos maestros de forma manual más adelante. Más información: [Configuración y administración de los datos maestros de la organización](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization)

### <a name="step-5-update-the-mobile-app-branding"></a>Paso 5: Actualizar la personalización de marca de la aplicación móvil

Puede cambiar el icono, la combinación de colores o el nombre para mostrar de las aplicaciones móviles para que coincidan con la personalización de marca de la organización.

Para ello, use las entidades **App** (Aplicación) y **App Config** (Configuración de aplicaciones) del área de **administración** importando los datos de la aplicación y de configuración de la aplicación desde los archivos de Excel disponibles en la carpeta **Archivos de datos** y desde los archivos de iconos en la carpeta **Iconos de aplicación** del paquete de implementación, tal como se explica en el [Paso 2: Descargar el paquete de implementación](#step-2-download-the-deployment-package).

> [!div class="mx-imgBorder"] 
> ![Entidades Apps (Aplicaciones) y App Config (Configuración de aplicaciones)](media/conf-app-app-config-entities.png "Entidades Apps (Aplicaciones) y App Config (Configuración de aplicaciones)")

1.  Asegúrese de que ha importado los datos de configuración para las entidades **Apps** (Aplicaciones) y **App Config** (Configuración de aplicaciones) mediante los archivos **App Import.xlsx** (Importación de la aplicación) y **App Config Import.xlsx** (Importación de la configuración de aplicación), respectivamente.

1.  Ahora, se copiarán los identificadores de aplicación de las aplicaciones de lienzo para que podamos rellenarlos en los registros de **aplicaciones** importados. Inicie sesión en [Power Apps](https://make.powerapps.com).

1.  Seleccione el entorno en la esquina superior derecha.

1.  En el panel izquierdo, seleccione **Aplicaciones** y, después, seleccione los puntos suspensivos (...) de una aplicación de lienzo. Finalmente, haga clic en **Detalles**.

    > [!div class="mx-imgBorder"] 
    > ![Detalles de aplicaciones](media/conf-environments-apps-details.png "Detalles de la aplicación")

1.  El identificador de la aplicación aparece en la parte inferior del panel  **Detalles**  para la aplicación. Copie el identificador de la aplicación junto con su nombre en un archivo del Bloc de notas.

    > [!div class="mx-imgBorder"] 
    > ![Identificador de la aplicación de detalles](media/conf-details-app-id.png "Identificador de la aplicación de detalles")

1.  Repita los pasos 4 y 5 para cada una de las aplicaciones de lienzo.

1.  Abra la aplicación de administración y, en el panel de navegación izquierdo, seleccione **Administración** en el selector de área y, a continuación, **Aplicaciones**. Se mostrarán todos los registros de la aplicación de lienzo importados del archivo **App Import.xlsx** (Importación de aplicaciones).

    > [!div class="mx-imgBorder"] 
    > ![Aplicaciones de administración](media/conf-admin-app-records.png "Aplicaciones de administración")

1.  Para abrir uno de los registros de la aplicación, selecciónelo. Observe que el campo del **identificador de Power Apps** está en blanco.

    > [!div class="mx-imgBorder"] 
    > ![Campo del identificador de aplicación de Power Apps](media/conf-powerapp-id-field.png "Actualización de la información de la aplicación")

1.  En la página de detalles de la aplicación:

    1. Copie el identificador de la aplicación del Bloc de notas (donde lo copió anteriormente) en el campo del **identificador de Power Apps**.

    2. Haga doble clic en el icono de la aplicación y seleccione un archivo de icono para la aplicación en la carpeta **Iconos de aplicación**. Los archivos de imagen tienen nombres intuitivos para que pueda seleccionar fácilmente el icono correcto. Por ejemplo, seleccione el archivo "Emergency Response App.png" para la **aplicación de respuesta ante emergencia**. También puede seleccionar una imagen personalizada de acuerdo con la personalización de marca de su organización.

    3. Si es necesario, actualice los campos **Description** (Descripción) o **Display Name** (Nombre para mostrar) de la aplicación.

    4. Si es necesario, actualice el valor del campo **Hide App from Menu** (Ocultar la aplicación en el menú) para determinar si la aplicación se debe mostrar en la lista de aplicaciones. Como la **aplicación de respuesta ante emergencias** es una aplicación contenedora, el valor se establece en **No** de forma predeterminada.

    5. Si es necesario, actualice el valor del campo **App Display Rank** (Clasificación de visualización de la aplicación) para establecer la posición en la que aparece la aplicación en la lista de aplicaciones.

    6. Si es necesario, seleccione un valor en el campo **Tracking Level** (Nivel de seguimiento) para especificar si desea realizar un seguimiento de los datos de esta aplicación móvil a nivel de **ubicación** o **instalación** Más información: [Administración del nivel de seguimiento de aplicaciones móviles](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

    7. Seleccione **Guardar**.

1.  Repita los pasos 8 y 9 para cada uno de los registros de las aplicaciones de lienzo en **Aplicaciones**.

1.  En el panel izquierdo, seleccione **App Config** (Configuración de aplicaciones).

1.  Seleccione el registro de la **aplicación de respuesta ante emergencias** para abrirlo para su edición.

    1.  Si es necesario, actualice los colores de la aplicación.

    2.  Seleccione **Yes** (Sí) o **No** en el campo **Device Sharing Enabled** (Uso compartido de dispositivos habilitado) para especificar si una opción **Sign Out** (Cerrar sesión) estará disponible en las aplicaciones móviles. Si selecciona **Yes** (Sí), habrá una opción para **cerrar sesión** disponible. Más información: [Fin de turno - cierre de sesión](use.md#end-shift---sign-out) en la guía del usuario.

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

2.  Reemplace el valor `APPGUIDHERE` por el identificador de aplicación real de una aplicación de lienzo.

3.  Guarde el archivo con la extensión .ps.

4.  Ejecute PowerShell como administrador y luego el archivo .ps que acaba de crear.

5.  Repita los pasos 2 y 4 para cada una de las aplicaciones de lienzo.

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional"></a>Paso 7: Agregar la clave de Azure Application Insights a las aplicaciones móviles para obtener la telemetría (opcional)

Tiene la opción de usar Azure Application Insights para recopilar telemetría detallada de las aplicaciones móviles (aplicaciones de lienzo) con el fin de obtener información sobre el uso de la aplicación. Para obtener información detallada al respecto, consulte [Analizar la telemetría de las aplicaciones mediante Application Insights](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights).

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>Paso 8: Compartir aplicaciones de lienzo con los usuarios de la organización

Para que los usuarios de primera línea puedan usar y consumir datos mediante las aplicaciones de lienzo en sus dispositivos móviles, las aplicaciones deben compartirse con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con grupos de usuarios.

> [!IMPORTANT]
> Asegúrese de que el usuario o grupo con el que piensa compartir las aplicaciones *ya* tenga acceso a su entorno. Normalmente, ya habrá agregado usuarios o grupos al [configurar el entorno](#step-1-sign-up-for-power-apps-and-create-an-environment). Si no es así, puede seguir los pasos que se indican aquí para agregar usuarios al entorno y proporcionar el acceso adecuado antes de compartir aplicaciones con ellos: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  En el panel de navegación izquierdo, seleccione **Aplicaciones** para ver una lista de todas las aplicaciones.

3.  Seleccione una aplicación móvil (aplicación de lienzo) y seleccione **Compartir** en el banner.

    > [!div class="mx-imgBorder"] 
    > ![Compartir aplicaciones de lienzo](media/conf-share-canvas-apps.png "Compartir aplicaciones de lienzo")

4.  Especifique el grupo o los usuarios de Azure AD con los que desea compartir esta aplicación. A medida que la aplicación se conecte a los datos de Common Data Service, también deberá proporcionar permisos a las entidades. El panel para compartir le pide que administre la seguridad de las entidades. Asigne los roles de seguridad **Emergency Response User** (Usuario de respuesta ante emergencias) y **Usuario de Common Data Service** a las entidades que usa esta aplicación y seleccione **Compartir**.

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

2.  Reemplace el valor de `APPGUIDHERE` por el identificador de aplicación real de la aplicación que quiere establecer como destacada y prominente, respectivamente.

3.  Guarde el archivo con la extensión .ps.

4.  Ejecute PowerShell como administrador y luego el archivo .ps que acaba de crear.
 

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>Paso 10: Compartir una aplicación controlada por modelos con administradores de la organización

Para que los usuarios administradores usen la aplicación de administración (aplicación controlada por modelos), debe compartirse con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con un grupo de usuarios administradores.

> [!IMPORTANT]
> Asegúrese de que el usuario o grupo con el que va a compartir la aplicación *ya* tenga acceso a su entorno. Normalmente, ya habrá agregado usuarios o grupos al [configurar el entorno](#step-1-sign-up-for-power-apps-and-create-an-environment). Si no es así, puede seguir los pasos que se indican aquí para agregar usuarios al entorno y proporcionar el acceso adecuado antes de compartir la aplicación con ellos: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

2. En el panel de navegación izquierdo, seleccione Aplicaciones para ver una lista de todas las aplicaciones.

3. Seleccione la aplicación controlada por modelos (**Admin App – Emergency Response App**) (Aplicación de administración - Aplicación de respuesta ante emergencias) y seleccione **Compartir** en el banner.

4. Especifique el grupo de Azure AD o los usuarios administradores con los que desea compartir esta aplicación, asigne el rol de seguridad **Emergency Response Admin** (Administrador de respuesta ante emergencias) y seleccione **Compartir**.

## <a name="publish-the-power-bi-dashboard"></a>Publicación del panel de Power BI

Publique el panel de Power BI y compártalo con los usuarios de su organización para que puedan usarlo para obtener información y tomar decisiones.

Puede publicar el panel de Power BI mediante cualquiera de las siguientes opciones: con la aplicación de plantilla desde AppSource *o* con el archivo **.pbit** disponible en el paquete de implementación.

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>Opción A: Publicar mediante la aplicación de plantilla desde AppSource (opción preferida)

Puede encontrar información detallada sobre el uso de la aplicación de plantilla de AppSource aquí: [Conexión al Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-health-emergency-response)

> [!IMPORTANT]
> Esta es una manera más fácil de publicar el panel de Power BI que el uso de la opción del archivo .pbit. Por lo tanto, esta es la opción recomendada para los clientes. 

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>Opción B: Publicar mediante el archivo .pbit en el paquete de implementación

En esta sección se proporciona información sobre cómo puede usar el archivo **.pbit de la aplicación de respuesta ante emergencias** disponible en el paquete de implementación para publicar el panel.

#### <a name="prerequisites"></a>Requisitos previos

- Licencias de capacidad premium de Power BI o Power BI Pro asignadas a los usuarios que tienen acceso al informe. 

- Cree un área de trabajo en Power BI donde publicar el informe. Inicie sesión en Power BI y cree un área de trabajo. Más información: [Crear las nuevas áreas de trabajo en Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Instale Power BI Desktop desde la Tienda de aplicaciones de Windows: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Si ha instalado Power BI Desktop mediante la descarga directa desde la página del Centro de descarga como un archivo ejecutable en algún momento anterior, quítela y use la de Microsoft Store. La versión de Microsoft Store se irá actualizando automáticamente a medida que estén disponibles nuevas versiones.
   >
   > Si no puede realizar la instalación desde Microsoft Store, instale la última versión que no sea de Microsoft Store desde la [página del Centro de descarga](https://www.microsoft.com/download/details.aspx?id=58494).

- Después de instalar Power BI Desktop desde la Tienda de aplicaciones, ejecútelo e inicie sesión con una cuenta que tenga permiso para publicar aplicaciones de Power BI en su organización.

#### <a name="publish-the-dashboard-using-the-pbit-file"></a>Publicación del panel mediante el archivo .pbit

1. Vaya a la ubicación donde extrajo el paquete de implementación. Encontrará el archivo **Emergency Response App.pbit** en la carpeta **Plantilla de Power BI**.

2. Abra el archivo **Emergency Response App.pbit** en Power BI Desktop. Se le pedirá que escriba los valores siguientes:

    - **Organization_name**: escriba el nombre de la organización que se rellenará en la esquina superior izquierda de cada página del informe.
    - **CDS_base_solution_URL**: escriba la dirección URL de la instancia de entorno de Common Data Service. Por ejemplo: https:// *[myenv]* .crm.dynamics.com

    > [!div class="mx-imgBorder"]
    > ![Especificación del nombre y la dirección URL base de la organización](media/pbi-pub-rep1.png)

    Seleccione **Cargar**.

3. Se le pedirá que escriba las credenciales para conectarse a su entorno de Common Data Service. Seleccione **Cuenta de organización** > **Inicio de sesión** para especificar las credenciales de Common Data Service.  

    > [!div class="mx-imgBorder"]
    > ![select-organizational-account](media/select-organizational-account.png)

4. Después de iniciar sesión, seleccione **Conectar** para conectarse a los datos en Common Data Service.

5. Si la conexión es correcta, los datos se mostrarán en el informe de Power BI. Se le pedirá que aplique los cambios pendientes a la consulta; seleccione **Aplicar cambios**.

6. Seleccione **Publicar** para publicar datos en el área de trabajo de Power BI. Se le pedirá que guarde los cambios; seleccione **Guardar**.

    > [!div class="mx-imgBorder"]
    > ![select-refresh-publish](media/select-refresh-publish.png)

7. Se le pedirá que guarde el archivo como un archivo .pbix junto con la información del entorno de Common Data Service. Proporcione un nombre y guárdelo en el equipo.

8. Después de guardar el archivo .pbix, se le pedirá que publique el informe. En la página **Publicar en Power BI**, seleccione el área de trabajo en la que quiere publicarlo y, luego, haga clic en **Seleccionar**.

12. El informe estará disponible en el área de trabajo. Ahora, configuraremos la actualización de datos para el conjunto de datos. Seleccione el conjunto de datos en el área de trabajo y seleccione el icono **Programar actualización**.  
    
    > [!div class="mx-imgBorder"]
    > ![schedule-refresh](media/schedule-refresh.png)

13. La primera vez que intente establecer la configuración de la actualización de datos, verá la página **Configuración** con un mensaje que indica que las credenciales no son válidas. En **Credenciales de origen de datos**, seleccione **Editar credenciales** para especificar las credenciales.  

    > [!div class="mx-imgBorder"]
    > ![select-edit-credentials](media/select-edit-credentials.png)

14. En la siguiente pantalla:
    - En **Método de autenticación**, seleccione **OAuth2**.
    - En **Privacy level setting for this data source** (Configuración del nivel de privacidad de este origen de datos), elija **Organizativo**.
    - Seleccione **Iniciar sesión**.

    Se le pedirá que especifique sus credenciales y que inicie sesión. Tras iniciar sesión correctamente, volverá a la página **Configuración**.

15. En la página **Settings** (Configuración), expanda **Scheduled refresh** (Actualización programada) y especifique los detalles necesarios para actualizar los datos en función de una programación. Seleccione **Aplicar**.

    > [!div class="mx-imgBorder"]
    > ![Actualización programada](media/refresh-schedule.png)

    > [!NOTE] 
    > Hay límites en el número de veces que se pueden actualizar los datos. Power BI limita los conjuntos de datos en la capacidad compartida a ocho actualizaciones diarias. Si el conjunto de datos reside en una capacidad Premium, puede programar hasta 48 actualizaciones al día en la configuración de dicho conjunto de datos. Más información: [Actualización de datos](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

16. Seleccione el nombre del área de trabajo en el panel izquierdo y, a continuación, seleccione **Crear aplicación** en la esquina superior derecha.  

    > [!div class="mx-imgBorder"]
    > ![select-create-app](media/select-create-app.png)

17. En la página de publicación de aplicaciones:

    1. En la pestaña **Configuración**, especifique el nombre y la descripción de la aplicación.

    2. En la pestaña **Navegación**, especifique la ubicación del panel en el que se publicará.

    3. En la pestaña **Permisos**, especifique los usuarios o el grupo que podrán ver esta aplicación. Asegúrese de activar la casilla **Instalar esta aplicación automáticamente** para instalar esta aplicación automáticamente para los usuarios finales. Más información: [Instalar aplicaciones para usuarios finales de forma automática](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![select-install-apps-automatically](media/select-install-apps-automatically.png)

18. Seleccione **Publicar aplicación**. Para obtener información detallada sobre cómo publicar aplicaciones en Power BI, consulte [Publicar la aplicación](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).

### <a name="after-publishing-the-dashboard"></a>Después de publicar el panel

Para ver el panel de Power BI publicado, consulte [Visualización del panel de Power BI](configure-data-reporting.md#view-power-bi-dashboard).

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para notificar un problema con la aplicación de ejemplo Respuesta ante emergencias hospitalarias, visite <https://aka.ms/emergency-response-issues>.

- Para ofrecer comentarios sobre la aplicación de ejemplo Respuesta ante emergencias hospitalarias, visite <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Siguiente paso

[Uso de la aplicación Respuesta ante emergencias hospitalarias](use.md)
