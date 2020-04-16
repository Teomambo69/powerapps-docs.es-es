---
title: Implemente y configure la aplicación Hospital Emergency Response | Microsoft Docs
description: Proporciona proporciona instrucciones detalladas para que los administradores de TI del hospital implementen y configuren la aplicación de muestra para su organización.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/05/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- GetStarted
- PowerApps
ms.openlocfilehash: 624c465ea812e4fe650dda3750259acf91476bb0
ms.sourcegitcommit: 83b35be5df4864e15be9122647b17465e050284c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2020
ms.locfileid: "3229085"
---
# <a name="deploy-and-configure-the-hospital-emergency-response-app"></a>Implemente y configure la aplicación Hospital Emergency Response

La aplicación Hospital Emergency Response requiere una pequeña cantidad de configuración para adaptarse a sus necesidades. Este artículo proporciona proporciona instrucciones paso a paso para que los administradores de TI del hospital implementen y configuren la aplicación para su organización.

Tiempo estimado para completar estos pasos: **35–40 minutos**.

## <a name="demo-deploy-and-configure-the-hospital-emergency-response-app"></a>Demostración: Implemente y configure la aplicación Hospital Emergency Response

Vea cómo puede implementar y configurar la aplicación Hospital Emergency Response.

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="deploy-the-hospital-emergency-response-app"></a>Implemente la aplicación Hospital Emergency Response

Realice los siguientes pasos para implementar la aplicación de ejemplo Hospital Emergency Response para su organización.

- [Paso 1: Regístrese en Power Apps y cree un entorno](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [Paso 2: Descargue el paquete de implementación](#step-2-download-the-deployment-package)
- [Paso 3: Importe el archivo de solución a su entorno](#step-3-import-the-solution-file-into-your-environment)
- [Paso 4: Cargue la configuración y los datos maestros para su organización](#step-4-load-configuration-and-master-data-for-your-organization)
    - [Paso 4.1: Cargue los datos de configuración obligatorios](#step-41-load-mandatory-configuration-data)
    - [Paso 4.2: Cargue los datos maestros](#step-42-load-master-data)
- [Paso 5: Actualice la marca de la aplicación móvil](#step-5-update-the-mobile-app-branding)
- [Paso 6: Omita el consentimiento para aplicaciones móviles](#step-6-bypass-consent-for-mobile-apps)
- [Paso 7: Agregue la clave Azure Application Insights para aplicaciones móviles para telemetría](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry)
- [Paso 8: Comparta aplicaciones de lienzo con los usuarios de su organización](#step-8-share-canvas-apps-with-users-in-your-organization)
- [Paso 9: Configure su aplicación móvil como héroe y aplicación destacada](#step-9-set-your-mobile-app-as-hero-and-featured-app)
- [Paso 10: Comparta la aplicación basada en modelos con los administradores de su organización](#step-10-share-model-driven-app-with-admins-in-your-organization)

### <a name="step-1-sign-up-for-power-apps-and-create-an-environment"></a>Paso 1: Regístrese en Power Apps y cree un entorno

Si aún no tiene Power Apps, regístrese en Power Apps y compre una licencia apropiada.

Más información:

-   [Power AppsPrecios](https://powerapps.microsoft.com/pricing/)
-   [ComprarPower Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Después de haber comprado Power Apps, cree un entorno con una base de datos Common Data Service.

1.  Inicie sesión en el [Centro de administración de Power Platform](https://aka.ms/ppac).

2.  Cree un entorno Common Data Service con la base de datos. Más información: [Crear y administrar entornos](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT]
    > Al crear la base de datos, si selecciona un grupo de seguridad para la base de datos, las aplicaciones se pueden compartir *solamente* con usuarios que son miembros del grupo de seguridad.

3.  Cree usuarios apropiados en su entorno. Más información: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>Paso 2: Descargue el paquete de implementación

Obtenga el último paquete de implementación (.zip) de <https://aka.ms/emergency-response-solution> que contiene el archivo de la solución, las imágenes y los archivos de datos para configurar las aplicaciones y la lógica empresarial de la aplicación Hospital Emergency Response.

Para comenzar el proceso de implementación, extraiga el archivo de implementación (.zip) en una ubicación de su computadora. Esta carpeta extraída contendrá las siguientes carpetas:

| **Carpeta/Archivo**       | **Descripción**  |
|-----------------------|------------------|
| **Íconos de aplicaciones**         | Contiene los iconos de aplicaciones predeterminados para las aplicaciones móviles (aplicaciones de lienzo)|
| **Archivos de datos**        | Contiene los archivos de datos maestros y de muestra (.xlsx) para que la solución / aplicación funcione. Puede importar datos de estos archivos para comenzar a trabajar en la aplicación. Más información: vea [Paso 4: Cargar la configuración y los datos maestros para su organización](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BIPlantilla** | Contiene el Archivo de plantilla de informe (.pbit) Power BI que usará para configurar los informes para su organización. Más información: [Obtener información con los paneles de Power BI](#get-insights-using-power-bi-dashboards)|
| **PowerShell**        | Contiene scripts que usará para configurar sus aplicaciones móviles (aplicaciones de lienzo). |
| **Archivo de solución**     | Contiene el archivo de solución Common Data Service que crea las aplicaciones y los metadatos necesarios para la aplicación Hospital Emergency Response.  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>Paso 3: Importe el archivo de solución a su entorno

1.  Navegue a la ubicación donde extrajo el archivo de implementación (.zip); encontrará la carpeta **Archivo de soluciones**. Importaremos el archivo solución administrada (.zip) en la carpeta **Archivo de soluciones** a nuestro entorno.

2.  Inicie sesión en [Power Apps](https://make.powerapps.com).

3.  Seleccione su entorno desde la esquina superior derecha.

4.  En el panel de la izquierda, seleccione **Soluciones** y después seleccione **Importar**.

    > [!div class="mx-imgBorder"] 
    > ![Importar solución](media/conf-import-solution.png "Importar solución")

5.  En el cuadro de diálogo **Importar Solución**, seleccione el archivo de solución mencionado en el paso 1 y luego siga los pasos del asistente para importar la solución.

6.  Una vez que la solución se haya importado correctamente, seleccione **Cerrar** en el cuadro de diálogo de importación.

Ahora, verá nuevas aplicaciones en **Aplicaciones**:

> [!div class="mx-imgBorder"] 
> ![Nuevas aplicaciones](media/conf-apps-new-apps.png "Nuevas aplicaciones")

Seleccione el **Aplicación de administración** para abrir la aplicación basada en modelos que le permite configurar el resto de la configuración de implementación. Más información: [¿Qué son las aplicaciones basadas en modelo?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![Abra la aplicación de administración](media/conf-admin-app-open.png "Abrir la aplicación de administrador")

La aplicación de administración tiene una serie de entidades donde puede agregar y administrar datos para su sistema hospitalario. Puede usar el selector de área en la parte inferior del panel de navegación izquierdo para seleccionar un área diferente.

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>Paso 4: Cargue la configuración y los datos maestros para su organización

Todos los datos necesarios para la aplicación Hospital Emergency Response están disponibles bajo la carpeta **Archivos de datos** debajo de la carpeta de implementación extraída.

La carpeta **Archivos de datos** tiene los siguientes archivos y carpetas:

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Descripción</th>
</tr>
<tr>
<td>En la raíz; los siguientes archivos están disponibles:
<ul>
<li>00 - Acuities Import.xlsx</li>
<li>00 - App Config Import.xlsx</li>
<li>00 - App Import.xlsx</li>
<li>00 - Request Roles Import.xlsx</li>
<li>00 - Supplies Import.xlsx</li>
</ul>
</td>
<td>Estos son los archivos de datos de configuración que deben importarse a las siguientes entidades mediante la aplicación de administración:
<ul>
<li>Acuidades</li>
<li>Configuración de aplicación</li>
<li>Aplicaciones</li>
<li>Solicitar Roles</li>
<li>Importar suministros</li>
</ul>
<br/>La importación de datos a estas entidades creará registros para estas entidades que son necesarios para que la aplicación Hospital Emergency Response funcione.
<br/>
<br/>
<strong>Precaución</strong>: asegúrese de no actualizar los valores de configuración en estas entidades, excepto para las entidades <strong>Aplicaciones</strong> y <strong>Configuración de aplicación</strong> como se explica más adelante.</td>
</tr>
<tr>
<td>Carpeta <strong>Datos de ejemplo</strong></td>
<td><p>La carpeta contiene los archivos de datos de muestra (.xlsx) que puede importar para completar los datos de muestra en su aplicación. Los archivos se nombran para indicar la secuencia en la que los datos deben importarse a su aplicación. </p>
<p>Debe importar datos para las siguientes entidades que contienen los datos maestros de muestra para la aplicación Hospital Emergency Response:
<ul>
<li>Sistemas</li>
<li>Regiones</li>
<li>Instalaciones</li>
<li>Ubicaciones</li>
<li>Departamentos</li>
</ul>
<p>Si desea importar los datos de su organización en lugar de los datos de muestra, puede reemplazar los datos de muestra en estos archivos de Excel con los datos de su organización y luego importar los datos en la aplicación.</p>
<p>También puede introducir datos manualmente para estas entidades. Para obtener información sobre cada una de estas entidades y campos en estas entidades, vea <a href="#manually-configure-and-manage-master-data-for-your-organization">Configure y administre manualmente los datos maestros para su organización</a></p></td>
</tr>
<tr>
<td>Carpeta <strong>Archivo de plantilla de datos para datos maestros </strong></td>
<td><p>La carpeta contiene archivos de datos "vacíos" (.xlsx) para entidades maestras que puede usar para completar los datos de su organización y luego importarlos a la aplicación.</p>
<p>Los archivos se nombran para indicar la secuencia en la que los datos deben importarse a su aplicación. Es la misma lista de entidades que se menciona anteriormente para la carpeta <strong>Data de muestra</strong>.</p>
<p>También puede introducir datos manualmente para estas entidades. Para obtener información sobre cada una de estas entidades y campos en estas entidades, vea <a href="#manually-configure-and-manage-master-data-for-your-organization">Configure y administre manualmente los datos maestros para su organización</a></p>
</td>
</tr>
</table>

#### <a name="step-41-load-mandatory-configuration-data"></a>Paso 4.1: Cargue los datos de configuración obligatorios

Importar los datos de configuración en las siguientes entidades en la aplicación de administración es **obligatorio** antes de pasar al siguiente paso:

| Nombre del área | Nombre de entidad| Nombre de archivo
|-|-|-
| Ubicaciones | Acuidades | 00 - Acuities Import.xlsx
| Administración | Configuración de aplicaciones | 00 - App Config Import.xlsx
| Administración | Aplicaciones | 00 - App Import.xlsx
| Personal | Solicitar Roles | 00 - Request Roles Import.xlsx
| Ubicaciones | Suministros | 00 - Supplies Import.xlsx

##### <a name="how-to-load-data-from-data-files"></a>¿Cómo cargar datos de archivos de datos?

Para importar datos de uno de los archivos de datos a una entidad:

1.  En el panel de navegación izquierdo de la aplicación de administración, seleccione una entidad para la que desea cargar los datos. Por ejemplo, seleccione **Administración** desde el selector de área y luego seleccione **Acuidades**.

2.  Seleccione **Importar desde Excel** y seleccione el archivo **00 - Acuities Import.xlsx** de la carpeta **Archivos de información**.

    > [!div class="mx-imgBorder"]
    > ![Importar desde Excel](media/conf-import-from-excel.png "Importar desde Excel")

3.  Continúe con los pasos del asistente de importación para importar los datos.

4.  Después de importar los datos, verá el registro importado en la entidad:

    > [!div class="mx-imgBorder"] 
    > ![Registro de entidad](media/conf-entity-record.png "Registro en la entidad tras la importación")

Repita los pasos anteriores con otras entidades de datos de configuración.

Alternativamente, si desea ingresar los datos maestros manualmente, vea [Configure y administre manualmente los datos maestros para su organización](#manually-configure-and-manage-master-data-for-your-organization).

#### <a name="step-42-load-master-data"></a>Paso 4.2: Cargue los datos maestros

Como se explicó anteriormente:
- Puede utilizar los archivos de datos de muestra para entidades de datos maestros en la carpeta **Archivos de datos / Datos de muestra** para importar los datos de muestra en las entidades requeridas. 

- Puede utilizar los archivos de datos "vacíos" para las entidades maestras en la carpeta **Archivos de datos / Archivo de plantilla de datos para datos maestros** que puede usar para completar los datos de su organización y luego importar los datos en las entidades requeridas.

También puede agregar manualmente datos maestros más tarde. Más información: [Configurar manualmente y administrar los datos maestros para su organización](#manually-configure-and-manage-master-data-for-your-organization)

### <a name="step-5-update-the-mobile-app-branding"></a>Paso 5: Actualice la marca de la aplicación móvil

Puede cambiar el ícono de la aplicación, el esquema de color o nombre de las aplicaciones móviles para que coincida con la marca de su organización.

Haces esto usando las entidades **Aplicación** y **Configuración de aplicación** en el área **Administración** importantado la aplicación y los datos de configuración de la aplicación de los archivos de Excel disponibles en la carpeta **Archivos de datos** y archivos de iconos en la carpeta **Iconos de aplicaciones** del paquete de implementación como se explica en [Paso 2: Descargue el paquete de implementación](#step-2-download-the-deployment-package).

> [!div class="mx-imgBorder"] 
> ![Aplicaciones y entidades de configuración de aplicaciones](media/conf-app-app-config-entities.png "Aplicaciones y entidades de configuración de aplicaciones")

1.  Asegúrese de haber importado los datos de configuración para las entidades **Aplicaciones** y **Configuración de aplicación** que utilizan los archivos **App Import.xlsx** y **App Config Import.xlsx**, respectivamente.

1.  Ahora, copiaremos los Id. de las aplicaciones de lienzo para que podamos completarlas en los registros **Aplicaciones** que importamos. Inicie sesión en [Power Apps](https://make.powerapps.com).

1.  Seleccione su entorno desde la esquina superior derecha.

1.  En el panel izquierdo, seleccione **Aplicaciones**, y luego seleccione los puntos suspensivos (...) para una aplicación de lienzo seguido de **Detalles**.

    > [!div class="mx-imgBorder"] 
    > ![Detalles de aplicaciones](media/conf-environments-apps-details.png "Detalles de la aplicación")

1.  El id. de la aplicación aparece en la parte inferior del panel **Detalles** para la aplicación. Copie el id. de la aplicación junto con su nombre en un archivo del Bloc de notas.

    > [!div class="mx-imgBorder"] 
    > ![Detalles id. de la aplicación](media/conf-details-app-id.png "Detalles id. de la aplicación")

1.  Repita los pasos 4 y 5 para cada aplicación de lienzo.

1.  Abra la aplicación de administración y, en el panel de navegación izquierdo de la aplicación de administración, seleccione **Administración** desde el selector de área, y luego seleccione **Aplicaciones**. Esto mostrará todos los registros de la aplicación de lienzo que importó del archivo **App Import.xlsx**.

    > [!div class="mx-imgBorder"] 
    > ![Aplicaciones de administrador](media/conf-admin-app-records.png "Aplicaciones de administrador")

1.  Abra uno de los registros de la aplicación seleccionándolo. Tenga en cuenta que el campo **Id. de Power App** está en blanco.

    > [!div class="mx-imgBorder"] 
    > ![Campo Id. de Power App ](media/conf-powerapp-id-field.png "Campo Id. de Power App")

1.  En la página de detalles de la aplicación:

    1. Copie el id. de la aplicación desde el bloc de notas (donde lo copió anteriormente) al campo **Id. de Power App**.

    2. Haga doble clic en el icono de la aplicación y seleccione un archivo de icono para la aplicación desde la carpeta **Iconos de aplicaciones**. Los archivos de imagen tienen nombres intuitivos para que pueda seleccionar fácilmente el icono correcto. Por ejemplo, seleccione el archivo "Emergency Response App.png" para la **aplicación Emergency Response**. También puede seleccionar una imagen personalizada según la marca de su organización.

    3. Si es necesario, actualice la **Descripción** o **Nombre para mostrar** de la aplicación.

    4. Si es necesario, actualice el valor **Ocultar aplicación del menú** para establecer si la aplicación debe mostrarse en la lista de aplicaciones. Como la **aplicación Emergency Response** es una aplicación de contenedor, el valor se establece en **No** por defecto.

    5. Si es necesario, actualice el valor **Rango de visualización de la aplicación** para establecer la posición de visualización de la aplicación en la lista de aplicaciones.

    6. Seleccione **Guardar**.

1.  Repita los pasos 8 y 9 para cada registro de aplicación de lienzo en **Aplicaciones**.

1.  En el panel izquierdo, seleccione **Configuración de aplicación**.

1.  Seleccione el registro **Aplicación Emergency Response** para abrirlo para editarlo.

    1.  Si es necesario, actualice los colores para su aplicación.

    2.  Seleccione **Sí** o **No** en el campo **Dispositivo compartido habilitado** para especificar si la opción **Desconectar** estará disponible en aplicaciones móviles o no. Seleccionando **Sí** hará que la opción **Desconectar** esté disponible. Más información: [Fin de turno: cerrar sesión](use.md#end-shift---sign-out) en la guía del usuario.

    > [!div class="mx-imgBorder"] 
    > ![Campo para compartir dispositivos habilitado](media/conf-device-sharing-enabled-field.png "Campo para compartir dispositivos habilitado")

1.  Seleccione **Guardar** en la esquina inferior derecha para guardar sus cambios.

### <a name="step-6-bypass-consent-for-mobile-apps"></a>Paso 6: Omita el consentimiento para aplicaciones móviles

Debe ser un administrador de inquilinos para completar este paso. Además, antes de realizar este paso, necesitará el id. de la aplicación de cada aplicación móvil (aplicación de lienzo).

Para obtener el id. de la aplicación para su aplicación, en el panel de navegación izquierdo de la aplicación de administración, seleccione **Administración** desde el selector de área, y luego seleccione **Aplicaciones**. Esto muestra todas las aplicaciones móviles (aplicaciones de lienzo). Seleccione una aplicación móvil para ver la id. de la aplicación. Copie el id. de la aplicación para cada aplicación en un archivo de bloc de notas.

> [!div class="mx-imgBorder"] 
> ![Obtener el id. de la aplicación](media/conf-admin-get-app-id.png "Obtener el id. de la aplicación")

A continuación haga lo siguiente:

1.  Abra el bloc de notas y copiae el siguiente script de PowerShell:

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

2.  Reemplace el valor `APPGUIDHERE` con el id. de aplicación real de una aplicación de lienzo.

3.  Guarde el archivo como un archivo .ps.

4.  Ejecute PowerShell como Administrador y ejecute el archivo .ps que acaba de crear.

5.  Repita los pasos 2 - 4 para cada aplicación de lienzo.

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry"></a>Paso 7: Agregue la clave Azure Application Insights para aplicaciones móviles para telemetría

Puede usar Azure Application Insights para recopilar telemetría detallada para sus aplicaciones móviles (aplicaciones de lienzo) para obtener información sobre el uso de la aplicación. Para obtener información detallada sobre esto, vea [Analice la telemetría de la aplicación usando Application Insights](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights)

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>Paso 8: Comparta aplicaciones de lienzo con los usuarios de su organización

Para que los usuarios de primera línea utilicen y consuman datos utilizando las aplicaciones de lienzo en sus dispositivos móviles, las aplicaciones deben compartirse con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con grupos de usuarios.

> [!IMPORTANT]
> Asegúrese de que el usuario o grupo con el que planea compartir las aplicaciones *ya* tiene acceso a su entorno. Por lo general, ya habría agregado usuarios o grupos al [configurar su entorno](#step-1-sign-up-for-power-apps-and-create-an-environment). Alternativamente, puede seguir los pasos aquí para agregar usuarios a su entorno y proporcionar el acceso adecuado antes de compartir aplicaciones con ellos: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1.  Iniciar sesión en [Power Apps](https://make.powerapps.com)

2.  En el panel de navegación izquierdo, seleccione **Aplicaciones** para ver una lista de todas tus aplicaciones.

3.  Seleccione una aplicación móvil (aplicación de lienzo) y seleccione **Compartir** en el banner.

    > [!div class="mx-imgBorder"] 
    > ![Compartir aplicaciones de lienzo](media/conf-share-canvas-apps.png "Compartir aplicaciones de lienzo")

4.  Especifica el grupo Azure AD o usuarios con los que desea compartir esta aplicación. A medida que la aplicación se conecta a los datos Common Data Service, también deberá proporcionar permisos a las entidades. El panel para compartir le solicita que administre la seguridad de las entidades. Asigne los roles de seguridad **Usuario de Emergency Response** y **Usuario de Common Data Service** para las entidades utilizadas por esta aplicación y seleccione **Compartir**.

    > [!div class="mx-imgBorder"] 
    > ![Compartir aplicación con grupo Azure AD o usuarios](media/conf-share-app-groups-users.png "Compartir con grupo Azure AD o usuarios")

5.  Repita los pasos 3 y 4 para cada aplicación móvil.

Información detallada sobre cómo compartir sus aplicaciones: [Comparte una aplicación de lienzo](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

### <a name="step-9-set-your-mobile-app-as-hero-and-featured-app"></a>Paso 9: Configure su aplicación móvil como héroe y aplicación destacada

Este paso le permite configurar su aplicación móvil como héroe y aplicación destacada dentro de la aplicación móvil **Power Apps**. Debe ser un administrador de inquilinos para completar este paso.

Antes de realizar este paso, necesitará el id. de la aplicación de cada aplicación móvil (aplicación de lienzo) que desea establecer como héroe y aplicación destacada. Para obtener información sobre cómo obtener el id. de la aplicación para una aplicación de lienzo, vea [Paso 6: omita el consentimiento para aplicaciones móviles](#step-6-bypass-consent-for-mobile-apps)

A continuación haga lo siguiente:

1.  Abra el bloc de notas y copiae el siguiente script de PowerShell:


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

2.  Reemplace el valor `APPGUIDHERE` en el script con el id. de la aplicación real para la aplicación que desea establecer como destacado y héroe respectivamente.

3.  Guarde el archivo como un archivo .ps.

4.  Ejecute PowerShell como Administrador y ejecute el archivo .ps que acaba de crear.
 

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>Paso 10: Comparta la aplicación basada en modelos con los administradores de su organización

Para que los usuarios administradores utilicen la aplicación de administración (aplicación basada en modelos), se debe compartir con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con un grupo de usuarios administradores.

> [!IMPORTANT]
> Asegúrese de que el usuario o grupo con el que planea compartir la aplicación *ya* tiene acceso a su entorno. Por lo general, ya habría agregado usuarios o grupos al [configurar su entorno](#step-1-sign-up-for-power-apps-and-create-an-environment). Alternativamente, puede seguir los pasos aquí para agregar usuarios a su entorno y proporcionar el acceso adecuado antes de compartir la aplicación con ellos: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

2. En el panel de navegación izquierdo, seleccione Aplicaciones para ver una lista de todas tus aplicaciones.

3. Seleccione la aplicación basada en modelos (**Aplicación de administración: aplicación Emergency Respone**) y seleccione **Compartir** en el banner.

4. Especifica el grupo de Azure AD o usuarios administradores con los que desea compartir esta aplicación, asigne el rol de seguridad **Administrador de Emergency Response**, y seleccione **Compartir**.


## <a name="manually-configure-and-manage-master-data-for-your-organization"></a>Configurar manualmente y administrar los datos maestros para su organización

Los administradores pueden usar la aplicación basada en modelos en [Power Apps](https://make.powerapps.com) para crear y administrar datos maestros para su organización. Estos datos son necesarios para que la aplicación Hospital Emergency Response funcione.

> [!NOTE]
> También puede importar los datos de su organización en los archivos de datos disponibles en el paquete de implementación y luego importarlos a estas entidades. Más información: [Paso 4: Cargar la configuración y los datos maestros para su organización](#step-4-load-configuration-and-master-data-for-your-organization)

Debe agregar datos maestros en estas entidades en la siguiente secuencia:

1. [Sistemas](#systems-data)

1. [Regiones](#regions-data)

1. [Instalaciones](#facilities-data)

1. [Ubicaciones](#locations-data)

1. [Departamentos](#departments-data)

Los datos maestros se gestionan desde el área **Ubicaciones** en la navegación izquierda en la aplicación de administración:

> [!div class="mx-imgBorder"]
> ![área ubicaciones](media/locations-area.png)

Las entidades bajo el área **Jerarquía** se enumeran en el orden en que debe completar los datos.

### <a name="systems-data"></a>Datos del sistema

La entidad **Sistemas** le permite crear y administrar entradas para Hospital Systems. Esto le permite administrar múltiples sistemas hospitalarios dentro de la misma organización.

Para crear un registro:

1. Seleccione **Sistemas** en el panel izquierdo y seleccione **Nuevo**:  
    > [!div class="mx-imgBorder"]
    > ![seleccionar-sistemas-nuevo](media/select-systems-new.png)

2. En la página **Sistema nuevo**, especifique los valores apropiados:  
   > [!div class="mx-imgBorder"]
   > ![introducir-detalles-sistema-nuevo](media/enter-details-new-system.png)

   | **Campo**            | **Descripción**                                    |
   |----------------------|----------------------------------------------------|
   | Nombre del sistema          | Escriba un nombre para su Hospital.                     |
   | Descripción          | Escriba una descripción opcional.                      |
   | Fecha de datos efectiva | Escriba la fecha y hora de inicio de este sistema hospitalario. |
   | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de este sistema hospitalario.   |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Sistemas**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="regions-data"></a>Datos de regiones

La entidad **Regiones** le permite administrar las regiones geográficas de sus sistemas hospitalarios.

Para crear un registro:

1. Seleccione **Regiones** en el panel izquierdo y seleccione **Nuevo**.

2. En la página **Región nueva**, especifique los valores apropiados:  

    > [!div class="mx-imgBorder"]
    > ![introducir-detalles-región-nueva](media/enter-details-new-region.png)

    | **Campo**            | **Descripción**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | Sistema               | Seleccionar un sistema hospitalario. Esta lista se llena en función de los datos de **Sistemas** que ha creado anteriormente. |
    | Nombre de región          | Escriba el nombre de la región. Por ejemplo, Seattle.                                                              |
    | Descripción          | Escriba una descripción opcional.                                                                            |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de esta región.                                                       |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de esta región.                                                         |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Regiones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="facilities-data"></a>Datos de instalaciones

La entidad **Instalaciones** le permite administrar las ubicaciones de los hospitales dentro de cada región. Por ejemplo, las instalaciones **Redmond** y **Bellevue** dentro de la región **Seattle**.

Para crear un registro:

1. Seleccione **Instalaciones** en el panel izquierdo y seleccione **Nuevo**.

2. En la página **Instalaciones nuevas**, especifique los valores apropiados: 

    > [!div class="mx-imgBorder"] 
    > ![introducir-detalles-instalaciones-nuevas](media/enter-details-new-facility.png)

    | **Campo**            | **Descripción**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Región               | Seleccione una región. Esta lista se llena en función de los datos de **Regiones** que ha creado anteriormente. |
    | Nombre de las instalaciones        | Escriba el nombre de las instalaciones. Por ejemplo, Bellevue.                                                  |
    | Descripción          | Escriba una descripción opcional.                                                                   |
    | Respiradores totales          | Escriba el número total de respiradores disponibles en las instalaciones                                  |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de estas instalaciones.                                                     |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de estas instalaciones.                                                       |

    Si es necesario, introduzca la dirección de las instalaciones.

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Instalaciones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="locations-data"></a>Datos de ubicaciones

La entidad **Ubicaciones** le permite administrar ubicaciones específicas de cada instalación hospitalaria.

> [!NOTE]
> Antes de crear un registro **Ubicaciones**, asegúrese de haber importado los datos de acuidad utilizando el archivo **00 - Acuities Import.xlsx** como se explicó anteriormente en [Paso 4: Cargue la configuración y los datos maestros para su organización](#step-4-load-configuration-and-master-data-for-your-organization). Esto se debe a que se requiere información de acuidad para crear un registro **Ubicación**.

Para crear un registro:

1. Seleccione **Ubicaciones** en el panel izquierdo y seleccione **Nuevo**.

2. En la página **Ubicación nueva**, especifique los valores apropiados:  
 
    > [!div class="mx-imgBorder"]
    > ![introducir-detalles-ubicación-nueva](media/enter-details-new-location.png)

    | **Campo**            | **Descripción**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Nombre de la ubicación        | Escriba el nombre de la ubicación.                                                                       |
    | Instalación             | Seleccione unas instalaciones. Esta lista se llena en función de los datos de **Instalaciones** que ha creado anteriormente. |
    | Suelo                | Escriba la información del piso para la instalación.                                                         |
    | Unidad                 | Escriba la información de unidad para las instalaciones                                                           |
    | Acuidad      | Seleccione el registro de acuidad asociado con esta ubicación.                                                                                                     |
    | Ubicación COVID      | Seleccione si esta ubicación se usa para tratar pacientes con COVID (**Sí** o **No**).                                                                                                      |
    | Camas totales           | Escriba el número total de camas en las instalaciones.                                                       |
    | Camas supletorias           | Escriba el número de camas supletorias en las instalaciones. Las camas supletorias son aquellas que pueden tener personal por encima y más allá de la capacidad de cama con licencia si los pacientes necesitan ser admitidos.                                                      |
    | Camas bloqueadas         | Escriba el número de camas bloqueadas en las instalaciones.                                                     |
    | Último censo          | Poblaciones basadas en el último registro censal que se creó.                                             |
    | Porcentaje de ocupación | Calculado automáticamente según el último censo y el total de camas                                         |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de esta ubicación.                                                   |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de esta ubicación.                                                     |
    | Orden de ubicación       | Escriba un número que clasifique la ubicación en las listas desplegables de ubicación.                               |
    | Indicador de sitio alternativo  | Para uso interno.                                                                                     |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Ubicaciones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="departments-data"></a>Datos de departamentos

La entidad **Departamentos** le permite administrar la información de los departamentos de un hospital.

Para crear un registro:

1. Seleccione **Departamentos** en el panel izquierdo y seleccione **Nuevo**.

2. En la página **Departamento nuevo**, especifique los valores apropiados:

    > [!div class="mx-imgBorder"]
    > ![introducir-detalles-departamento-nuevo](media/enter-details-new-department.png)

    | **Campo**            | **Descripción**                                    |
    |----------------------|----------------------------------------------------|
    | Nombre del departamento      | Escriba un nombre del departamento.                            |
    | Descripción          | Escriba una descripción opcional.                      |
    | Fecha de datos efectiva | Escriba la fecha y hora de inicio de este departamento. |
    | Fecha de finalización efectiva   | Escriba la fecha y hora de finalización de este departamento.   |

3. Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Departamentos**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

## <a name="get-insights-using-common-data-service-dashboards"></a>Obtenga información utilizando los paneles Common Data Service

Los siguientes paneles están disponibles de forma predeterminada en la aplicación de administración de Hospital Emergency Response (basada en modelo):

- **Administración de camas**

   Muestra la disponibilidad de camas, el porcentaje de ocupación y el número total de camas en diferentes instalaciones.

- **Equipamiento y suministro**

  Muestra equipos críticos en uso y suministros disponibles en diferentes instalaciones.

- **Administración de personal**

  Muestra el número de miembros del personal solicitados, asignados y disponibles en diferentes instalaciones.

- **Pacientes con COVID**

  Muestra el número de pacientes bajo investigación y que dieron positivo de COVID-19 en diferentes instalaciones.

- **Altas**

  Muestra el número de pacientes previstos para el alta y el alta real.

También puede crear sus propios paneles además de los paneles disponibles de forma predeterminada.

### <a name="manage-dashboards"></a>Administrar paneles

Para administrar paneles:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y navegue hasta su aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Paneles** en el selector de área:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-paneles](media/select-dashboards.png)

3. Seleccione un nombre de panel en la navegación izquierda para ver los gráficos:

    > [!div class="mx-imgBorder"]
    > ![ver-gráficos](media/view-charts.png)

    > [!NOTE]
    > Puede filtrar datos en la parte inferior de la pantalla y los gráficos en la parte superior se actualizan automáticamente con valores filtrados.

4. Seleccione la opción **Expandir** para ver un gráfico en modo de pantalla completa:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-expandir](media/select-expand.png)

### <a name="additional-analysis"></a>Análisis adicional

- **Explorar en profundidad**: puede seleccionar el área del gráfico para explorar en profundidad aún más con atributos adicionales (campos) para una entidad:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-área-gráfico-explorar-en-profundidad](media/select-chart-area-drill-down.png)

- **Actualizar**: puede actualizar los paneles para reflejar los datos actualizados. Puede actualizar todos los gráficos en un tablero específico con **Actualizar todo** o un gráfico seleccionado con **Actualizar**:

    > [!div class="mx-imgBorder"]
    > ![actualizar-paneles](media/refresh-dashboards.png)

- **Ver registros**: seleccione **Más comandos** (**...**) y después **Ver registros** para ver todos los registros asociados a un gráfico dado:

    > [!div class="mx-imgBorder"]
    > ![seleccionar-más-comandos](media/select-more-commands.png)

    > [!NOTE] 
    > Cuando seleccione **Ver registros**, verá la vista de la entidad dividida entre el gráfico y los registros. Cualquier cambio en los filtros para registros en el lado derecho se refleja con actualizaciones automáticas en el gráfico en el lado izquierdo de la pantalla.

Para obtener más información sobre cómo editar un panel existente y actualizar las propiedades de los gráficos, lea [editar un panel existente](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Crear paneles nuevos

También puede crear sus propios paneles y personalizarlos para satisfacer sus necesidades. Para crear un panel nuevo, seleccione **Nuevo** y luego seleccione **Panel de Dynamics 365**:

> [!div class="mx-imgBorder"]
> ![seleccionar-nuevo-panel-dynamics](media/select-new-dynamics-dashboard.png)

Para más información acerca de cómo crear un panel nuevo, lea [crear un panel nuevo](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="get-insights-using-power-bi-dashboards"></a>Obtenga información utilizando los paneles Power BI

Publique el panel Power BI y compártalo con los usuarios de su organización para que puedan usar el panel de control para obtener información y tomar decisiones.

### <a name="prerequisites"></a>Requisitos previos

- Power BI capacidad Premium o licencias Power BI profesionales asignadas a usuarios que acceden al informe. 

- Cree un espacio de trabajo en Power BI donde publicar el informe. Inicie sesión en Power BI y cree un espacio de trabajo. Más información: [Crear los espacios de trabajo nuevos en Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Instalar Power BI Desktop desde la tienda de aplicaciones de Windows: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Si ha instalado Power BI descargándolo directamente desde el sitio de Power BI como un ejecutable en el pasado, elimínelo y use el de la tienda de aplicaciones. La versión de la tienda de aplicaciones se actualizará automáticamente a medida que haya nuevas versiones disponibles.

- Después de instalar Power BI Desktop desde la tienda de aplicaciones, ejecútelo, inicie sesión con una cuenta que tenga permiso para publicar aplicaciones Power BI en su organización.

### <a name="publish-the-power-bi-dashboard"></a>Publique el panel Power BI

1. Desplácese hasta la ubicación en la que ha extraído el paquete de implementación. Encontrará el archivo **Emergency Response App.pbit** archivo bajo la carpeta **Plantilla Power BI**.

2. Abra el archivo **Emergency Response App.pbit** en Power BI Desktop. Se le pedirá que escriba los siguientes valores:

    - **Nombre de la organización** : escriba el nombre de su organización que se completará en la esquina superior izquierda de cada página del informe.
    - **CDS_base_solution_URL**: escriba la URL de su instancia de entorno Common Data Service. Por ejemplo: https://*[myenv]*.crm.dynamics.com

    > [!div class="mx-imgBorder"]
    > ![especifique el nombre de la organización y la URL base](media/pbi-pub-rep1.png)

    Seleccione **Cargar**.

3. Se le pedirá que introduzca las credenciales para conectarse a su entorno Common Data Service. Seleccione **Cuenta organizacional** > **Iniciar sesión** para especificar sus credenciales de Common Data Service.  

    > [!div class="mx-imgBorder"]
    > ![seleccionar-cuenta-organizacional](media/select-organizational-account.png)

4. Después de iniciar sesión, seleccione **Conectar** para conectarse a sus datos en Common Data Service.

5. En una conexión exitosa, sus datos se mostrarán en el informe Power BI. Se le solicitará que aplique los cambios pendientes a su consulta; seleccione **Aplicar cambios**.

6. Seleccione **Publicar** para publicar datos en su espacio de trabajo Power BI. Se le pedirá que guarde sus cambios; seleccione **Guardar**.

    > [!div class="mx-imgBorder"]
    > ![seleccionar-actualizar-publicar](media/select-refresh-publish.png)

7. Se le pedirá que guarde el archivo como un archivo .pbix junto con su información del entorno Common Data Service. Proporcione un nombre y guárdelo en su computadora.

8. Después de guardar el archivo .pbix, se le pedirá que publique el informe. En la página **Publicar en Power BI**, seleccione el espacio de trabajo donde desea publicar y luego haga clic en **Seleccionar**.

12. El informe estará disponible en su espacio de trabajo. Ahora, configuraremos la configuración de actualización de datos para conjunto de datos. Seleccione el conjunto de datos en su espacio de trabajo y seleccione el icono **Programar actualización**.  
    
    > [!div class="mx-imgBorder"]
    > ![programar-actualización](media/schedule-refresh.png)

13. La primera vez que intente establecer la configuración de actualización de datos, verá la página **Configuración** con un mensaje que indica que sus credenciales no son válidas. En **Credenciales de origen de datos**, seleccione **Editar credenciales** para especificar sus credenciales.  

    > [!div class="mx-imgBorder"]
    > ![seleccionar-editar-credenciales](media/select-edit-credentials.png)

14. En la pantalla siguiente:
    - Seleccione el **Método de autenticación** como **OAuth2**.
    - Seleccione **Configuración del nivel de privacidad para este origen de datos** como **Organizativo**.
    - Seleccione **Iniciar sesión**.

    Se le pedirá que especifique sus credenciales e inicie sesión. Después de iniciar sesión correctamente, volverá a la página **Configuración**.

15. En la página **Configuración**, expanda **Actualización programada** y especifique los detalles necesarios para actualizar los datos en función de una programación. Seleccione **Aplicar**.

    > [!div class="mx-imgBorder"]
    > ![Actualización programada](media/refresh-schedule.png)

    > [!NOTE] 
    > Existen límites sobre cuántas veces se pueden actualizar los datos. Power BI limita los conjuntos de datos en capacidad compartida a ocho actualizaciones diarias. Si conjunto de datos reside en una capacidad Premium, puede programar hasta 48 actualizaciones por día en la configuración de conjunto de datos. Más información: [Actualizar datos](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

16. Seleccione el nombre de su espacio de trabajo en el panel izquierdo y luego seleccione **Crear aplicación** en la esquina superior derecha.  

    > [!div class="mx-imgBorder"]
    > ![seleccionar-crear-aplicación](media/select-create-app.png)

17. En la página de publicación de aplicación:

    1. En la pestaña **Configurar**, especifique el nombre y la descripción de su aplicación.

    2. En la pestaña **Navegación**, especifique la ubicación del panel donde lo publicará.

    3. En la pestaña **Permisos**, especifique los usuarios o grupos que podrán ver esta aplicación. Asegúrese de seleccionar la casilla de verificación **Instalar esta aplicación automáticamente** para instalar esta aplicación automáticamente para usuarios finales. Más información: [Instalar automáticamente aplicaciones para usuarios finales](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![seleccionar-instalar-aplicaciones-automáticamente](media/select-install-apps-automatically.png)

18. Seleccione **Publicar aplicación** Para obtener información detallada sobre la publicación de aplicaciones en Power BI, consulte [Publicar su aplicación](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).

### <a name="view-the-power-bi-dashboard"></a>Ver el panel de Power BI

Inicie sesión en [Power BI](https://apps.powerbi.com) para acceder y ver el panel de Power BI.

> [!div class="mx-imgBorder"]
> ![Ver el panel de Power BI](media/view-power-dashboard.png)

Puede usar los filtros en la parte superior del informe para filtrar datos para sistemas, regiones e instalaciones hospitalarias. También puede filtrar por ubicaciones COVID.

> [!div class="mx-imgBorder"]
> ![Filtros de informes](media/report-filters.png)

#### <a name="system-at-a-glance-page"></a>Página Sistema de un vistazo 

La **página Sistemas de un vistazo** es la predeterminada o de nivel superior que proporciona una vista general.  

La página muestra una vista resumida de lo siguiente: 

- **Pacientes con COVID**: muestra el número total de pacientes con COVID, el número de pacientes que resultaron positivos con COVID-19 y el número de pacientes bajo investigación. 

- **Administración de camas**: muestra la disponibilidad de camas, el porcentaje de ocupación, el número de camas supletorias y el número total de camas. También puede usar la cuadrícula a continuación para ver los números por unidades agudas. 

- **Gestión de personal de enfermería**: muestra el número de pacientes en la UCI, enfermeras asignadas y la relación enfermera / paciente.  

- **Altas**: muestra el número total de pacientes de larga estancia, el número de pacientes previstos para el alta y el alta real. 

- **Equipamiento**: muestra el número total de respiradores, el número de respiradores en uso y los respiradores disponibles. 

- **Suministros**: muestra el número de suministros disponibles por días.

> [!NOTE]
> - Seleccionar el ícono de información (i) en cualquiera de las áreas resumidas lo lleva a la página de detalles correspondiente para el área. 
> - También puede realizar otras acciones en informes como filtrar y ordenar datos, exportar el informe a PDF y PowerPoint, agregar un foco de atención, etc. Para obtener información detallada sobre las características del informe en Power BI, vea [Informes en Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports)
> - Las columnas más recientes o actualizadas en algunos de estos informes muestran la fecha y la hora en que se actualizaron los datos por última vez. También es fácil identificar la frescura al ver el color de los valores de fecha y hora en estas columnas:
>    - Negro: los datos se actualizaron hace menos de 20 horas
>    - Gris: los datos se actualizaron hace 20 - 24 horas
>    - Rojo: los datos se actualizaron hace más de 24 horas 
 
#### <a name="system-view-page"></a>Página Vista del sistema

La página **Vista del sistema** muestra gráficos con la siguiente información para un sistema hospitalario:
- Respiradores en uso y respiradores disponibles
- Disponibilidad de camas y camas de cuidados intensivos y porcentaje de ocupación
- Total de personal solicitado, número de pacientes (censo), relación enfermera / paciente.
- Suministros disponibles en días

> [!div class="mx-imgBorder"]
> ![Vista del sistema](media/report-system-view.png)

#### <a name="location-details-page"></a>Página de detalles de ubicación 

Para explorar en profundidad el informe por ubicación, haga clic en **Detalles de ubicación** en la esquina superior derecha. La página **Detalles de ubicación** muestra datos por ubicación, como el número total de camas, camas disponibles, camas supletorias, pacientes con COVID, etc. 

> [!div class="mx-imgBorder"]
> ![Detalles de ubicación](media/report-location-details.png) 

#### <a name="covid-patient-details-page"></a>Página de detalles del paciente COVID 

La página **Detalles del paciente COVID** proporciona información detallada sobre los pacientes con COVID, como los pacientes en cada ubicación, la tendencia del paciente a lo largo del tiempo que muestra picos y valles de la cantidad de pacientes bajo investigación (PUI) y la cantidad de pacientes que se encontraron positivos y tener una idea de dónde se encuentran los pacientes en el hospital.

> [!div class="mx-imgBorder"]
> ![Detalles del paciente COVID](media/report-covid-details.png)

#### <a name="bed-management-page"></a>Página de gestiónde camas 

La página **Gestión de camas** proporciona información en profundidad por ubicación, como el total de camas disponibles y el porcentaje de ocupación.

> [!div class="mx-imgBorder"]
> ![Administración de camas](media/report-bed-details.png)

#### <a name="staff-details-page"></a>Página detalles del personal  

La página **Detalles del personal** proporciona detalles sobre el personal por ubicación, número de enfermeras asignadas, número total de pacientes y número de pacientes con COVID. También muestra la relación enfermera / paciente y la relación UCI enfermera / paciente durante un período de tiempo.

> [!div class="mx-imgBorder"]
> ![Detalles del personal](media/report-staff-details.png)

#### <a name="equipment-details-page"></a>Página detalles del equipamiento 

La página **Detalles del equipamiento** proporciona detalles sobre el equipamiento por ubicación, el número total de respiradores en uso, superpuestos por el número de pacientes con COVID y otros equipos, como cinturones, cargadores y capuchas en uso.

> [!div class="mx-imgBorder"]
> ![Detalles del equipamiento](media/report-equipment-details.png)

#### <a name="discharge-details-page"></a>Página Detalles de alta 

La página **Detalles de alta** proporciona detalles sobre los pacientes a largo plazo, las barreras al alta durante un período y la variación en términos de altas reales y anticipadas.

> [!div class="mx-imgBorder"]
> ![Detalles del equipamiento](media/report-discharge-details.png)

#### <a name="supplies-on-hand-details-page"></a>Página Detalles de suministros en mano 

La página **Detalles de suministros en mano** proporciona detalles sobre los suministros por ubicación y suministro; también proporciona datos sobre el suministro disponible durante un período de tiempo.

> [!div class="mx-imgBorder"]
> ![Detalles del equipamiento](media/report-discharge-details.png)

## <a name="view-and-manage-app-feedback"></a>Ver y administrar comentarios de la aplicación

Todos los comentarios proporcionados por el personal de primera línea que utilizan aplicaciones de lienzo en sus dispositivos móviles se almacenan en la entidad **Comentarios sobre la aplicación** y los administradores pueden ver y administrar esto usando el área **Administración** en el panel de navegación izquierdo en la aplicación de administración.

Para ver y administrar comentarios de la aplicación:

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y navegue hasta su aplicación de administración.

2. En el panel de navegación izquierdo, seleccione **Administración** en el selector de área.

3. Seleccione **Comentarios sobre la aplicación** para ver una lista de comentarios de aplicaciones enviados por los usuarios. Puede hacer clic en un registro para ver los detalles y marcarlos como revisados o no.  

    > [!div class="mx-imgBorder"]
    > ![seleccionar-comentario-aplicación](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-issues>.

- Para comentarios sobre la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Paso siguiente

[Usar la aplicación Hospital Emergency Response](use.md)
