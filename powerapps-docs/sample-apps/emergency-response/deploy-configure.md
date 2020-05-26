---
title: Mostrar la aplicación Hospital Emergency Response | Microsoft Docs
description: Proporciona proporciona instrucciones detalladas para que los administradores de TI del hospital implementen y configuren la aplicación de muestra para su organización.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/29/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 40cd65d4017573689e98381269a50cfcc4000cb0
ms.sourcegitcommit: 4c7c213dd1d10523c84013ab78f02c260e6b6388
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2020
ms.locfileid: "3324845"
---
# <a name="deploy-the-hospital-emergency-response-app"></a>Implemente la aplicación Hospital Emergency Response

La aplicación Hospital Emergency Response requiere una pequeña cantidad de configuración para adaptarse a sus necesidades. Este artículo proporciona proporciona instrucciones paso a paso para que los administradores de TI del hospital implementen y configuren la aplicación para su organización.

Tiempo estimado para completar estos pasos: **35–40 minutos**.

## <a name="service-urls-for-us-government-customers"></a>URL de servicio para clientes del gobierno de EE. UU.

La solución Hospital Emergency Response también está disponible para clientes del gobierno de los EE. UU. Hay un conjunto diferente de URL para acceder a entornos del gobierno de EE. UU. en Power Apps y Power BI que en la versión comercial.

La versión comercial de la URL del servicio se utiliza en este artículo. Si es cliente del gobierno de los EE. UU., use la URL correspondiente del gobierno de los EE. UU. para su implementación como se menciona aquí:


| **Dirección URL comercial de la versión**                | **Dirección URL de la versión para la Administración Pública de Estados Unidos**  |
|-------------------------------------------|--------------------------------|
| [https://make.powerapps.com](https://make.powerapps.com)                | [https://make.gov.powerapps.us](https://make.gov.powerapps.us) (GCC) <br/><br/>[https://make.high.powerapps.us](https://make.high.powerapps.us) (GCC High)                |
| [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) | [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us) (GCC)<br/><br/>[https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us) (GCC High)|
| [https://app.powerbi.com/](https://app.powerbi.com/)                  | [https://app.powerbigov.us](https://app.powerbigov.us) (GCC)<br/><br/>[https://app.high.powerbigov.us](https://app.high.powerbigov.us) (GCC High)                 |

Para obtener información detallada sobre los planes del gobierno de EE. UU. para Power Apps y Power BI, vea:
- [Power Apps para la Administración pública de Estados Unidos](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI para la Administración pública de Estados Unidos](https://docs.microsoft.com/power-bi/service-govus-overview)


## <a name="step-1-download-the-deployment-package"></a>Paso 1: Descargue el paquete de implementación

> [!IMPORTANT]
> Si es un usuario de versión comercial, puede saltarse este paso y usar la opción AppSource en lugar de instalar la aplicación y el panel Power BI. 

Descargue el último paquete de implementación (.zip) de <https://aka.ms/emergency-response-solution>.

Antes de extraer el archivo .zip, asegúrese de desbloquearlo.

1.  Haga clic con el botón secundario en el archivo .zip y seleccione **Propiedades**.

2.  En el cuadro de diálogo de propiedades, seleccione **Desbloquear** y luego seleccione **Aplicar** seguido de **Aceptar**.

Al extraer el archivo .zip, verá lo siguiente en la carpeta extraída:

|**Carpeta**  |**Descripción**  |
|---------|---------|
|**Paquete**     |  Contiene la herramienta Package Deployer y el paquete que implementará más adelante para configurar la solución en su entorno. Más información: [Opción C: instalar la aplicación desde el paquete de implementación](#option-c-install-the-app-from-the-deployment-package)     |
|**Power BIPlantilla**     | Contiene el Archivo de plantilla de informe Power BI (.pbit) que usará para configurar los informes. Más información: [Paso 10: Publicar el panel de Power BI](#step-10-publish-the-power-bi-dashboard)        |

## <a name="step-2-sign-up-for-power-apps-and-create-an-environment"></a>Paso 2: Regístrese en Power Apps y cree un entorno

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

## <a name="step-3-install-the-app"></a>Paso 3: Instalar la aplicación

Siga los pasos a continuación para instalar la aplicación Hospital Emergency Response junto con la configuración y los datos de muestra.

> [!NOTE]
> La configuración y los datos de ejemplo se instalan solo para una nueva instalación. Si tiene una instalación previa de esta aplicación en su entorno, la configuración y los datos de ejemplo no se instalarán durante la instalación para garantizar que no se sobrescriban sus datos existentes.

Puede instalar la aplicación usando una de las 3 opciones siguientes:

- Microsoft AppSource (solo para clientes de Power Apps gobierno de EE. UU.). Ver [Opción A: instalar la aplicación desde Microsoft AppSource (Clientes del gobierno de EE. UU.)](#option-a-install-the-app-from-microsoft-appsource-us-govt-customers)

- Microsoft AppSource (para clientes con la versión comercial de Power Apps). Ver [Opción B: instalar la aplicación desde Microsoft AppSource](#option-b-install-the-app-from-microsoft-appsource)

- Paquete de implementación que descargó anteriormente. Ver [Opción C: instalar la aplicación desde el paquete de implementación](#option-c-install-the-app-from-the-deployment-package)

### <a name="option-a-install-the-app-from-microsoft-appsource-us-govt-customers"></a>Opción A: instalar la aplicación desde Microsoft AppSource (Clientes del gobierno de EE. UU.)

1.  Inicie sesión en el Centro de administración de Power Platform. Use la URL apropiada para iniciar sesión:
    - **GCC**: [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us)
    - **GCC High**: [https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us)

2.  En el panel izquierdo, seleccione **Entornos** y luego seleccione el nombre del entorno que en el paso anterior.

3. En la página de detalles del entorno, seleccione **Administrar aplicaciones de Dynamics 365**.

    > [!div class="mx-imgBorder"] 
    > ![Configuración del entorno](media/ppac-env-setting.png "Configuración del entorno")

3.  En la página de aplicaciones de Dynamics 365, seleccione **Instalar aplicación**. Después seleccione **Aplicación Power Platform de respuesta de emergencia** en el panel derecho y seleccione **Siguiente**.

    > [!div class="mx-imgBorder"] 
    > ![Instalar aplicación](media/ppac-install-app.png "Instalar aplicación")

4.  En la página siguiente, acepte los términos y seleccione **Instalar**.

5.  La instalación comenzará y puede seguir el progreso de la instalación de su aplicación en la página de aplicaciones de Dynamics 365.

    > [!div class="mx-imgBorder"] 
    > ![Progreso de la instalación de la aplicación de supervisión](media/ppac-app-install-progress.png "Progreso de la instalación de la aplicación de supervisión")

    > [!IMPORTANT]
    > La aplicación puede tardar un tiempo en instalarse.

6.  Después de instalar la aplicación, vaya hasta [Power Apps](https://make.powerapps.com) y seleccione su entorno en la esquina superior derecha. Verá las aplicaciones nuevas en **Aplicaciones**:

    > [!div class="mx-imgBorder"] 
    > ![Nuevas aplicaciones](media/conf-apps-new-apps.png "Nuevas aplicaciones")

    La instalación también agrega la configuración y datos de ejemplo para la aplicación Hospital Emergency Response.

### <a name="option-b-install-the-app-from-microsoft-appsource"></a>Opción B: instalar la aplicación desde Microsoft AppSource

1.  Vaya a [AppSource](https://appsource.microsoft.com/) y busque "Aplicación Hospital Emergency Response".<br/>Alternativamente, navegue directamente a la aplicación en AppSource usando este enlace: <https://appsource.microsoft.com/product/dynamics-365/mscrm.pphersapp>

2.  En la página de la aplicación Hospital Emergency Response, seleccione **Conseguir ahora**.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/appsource-01.png "Aplicación en AppSource")

3.  Se le solicita que revise los términos del acuerdo de AppSource. El cuadro de diálogo también muestra la cuenta que se está utilizando para iniciar sesión. Seleccione **Continuar**. Es posible que se le solicite que verifique sus credenciales.

4.  En la página siguiente, seleccione el entorno donde quiera instalar la aplicación. Seleccione las casillas de verificación de términos legales y declaraciones de privacidad, y seleccione **De acuerdo**.

    > [!div class="mx-imgBorder"] 
    > ![Seleccionar un entorno](media/appsource-02.png "Seleccionar un entorno")

5.  Se lo dirigirá al Centro de administración de Dynamics 365 donde puede seguir el progreso de la instalación de su aplicación.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/appsource-03.png "Progreso de la instalación de la aplicación de supervisión")

    > [!IMPORTANT]
    > La aplicación puede tardar un tiempo en instalarse.

6.  Después de instalar la aplicación, vaya hasta [Power Apps](https://make.powerapps.com) y seleccione su entorno en la esquina superior derecha. Verá las aplicaciones nuevas en **Aplicaciones**:

    > [!div class="mx-imgBorder"] 
    > ![Nuevas aplicaciones](media/conf-apps-new-apps.png "Nuevas aplicaciones")

    La instalación también agrega la configuración y datos de ejemplo para la aplicación Hospital Emergency Response.

### <a name="option-c-install-the-app-from-the-deployment-package"></a>Opción C: instalar la aplicación desde el paquete de implementación

1.  Vaya a la ubicación donde extrajo el [paquete de implementación](#step-1-download-the-deployment-package) (.zip); encontrará una carpeta **Package**. En la carpeta **Package**, ejecute el archivo **PackageDeployer.exe** para ejecutar la herramienta para implementar el paquete.

2.  En la pantalla siguiente, seleccione **Continuar**.

3.  Se le pedirá que se conecte a su entorno. Seleccione **Office 365** como el **Tipo de implementación**, seleccione **Mostrar avanzado** y luego escriba sus credenciales para conectarse a su entorno.

    > [!div class="mx-imgBorder"] 
    > ![Implementar paquete](media/deploy-connect-to-environment.png "Implementar paquete")

4.  Seleccione **Iniciar sesión** para continuar.

5.  Si tiene acceso a más de un entorno Common Data Service, la siguiente pantalla le pedirá que seleccione el entorno donde desea instalar el paquete. Seleccione un entorno y después seleccione **Iniciar sesión**.

    > [!div class="mx-imgBorder"] 
    > ![Seleccionar un entorno](media/deploy-select-environment.png "Seleccionar un entorno")

6.  En la pantalla siguiente, seleccione **Siguiente**.

7.  La siguiente pantalla muestra el nombre del entorno donde se instalará el paquete. Revise la información y seleccione **Siguiente**.

8.  La siguiente pantalla valida si el paquete se puede instalar en su entorno. Seleccione **Siguiente** para continuar con la instalación.

    > [!div class="mx-imgBorder"] 
    > ![Validar entorno](media/conf-validate-env.png "Validar entorno")

9.  La siguiente pantalla muestra el estado de instalación del paquete. Después de completar la instalación, seleccione **Siguiente**.

    > [!div class="mx-imgBorder"] 
    > ![Estado de la instalación](media/conf-package-install.png "Estado de la instalación")

    > [!NOTE]
    > Puede llevar un tiempo completar la instalación del paquete. 

10.  En la siguiente pantalla, seleccione **Terminar** para completar y cerrar la configuración.

11.  Después de instalar la aplicación, vaya hasta [Power Apps](https://make.powerapps.com) y seleccione su entorno en la esquina superior derecha. Verá las aplicaciones nuevas en **Aplicaciones**:

        > [!div class="mx-imgBorder"] 
        > ![Nuevas aplicaciones](media/conf-apps-new-apps.png "Nuevas aplicaciones")

        La instalación también agrega la configuración y datos de ejemplo para la aplicación Hospital Emergency Response.

Seleccione el **Aplicación de administración** para abrir la aplicación basada en modelos que le permite configurar el resto de la configuración de implementación. La aplicación de administración tiene una serie de entidades donde puede agregar y administrar datos para su sistema hospitalario. Puede usar el selector de área en la parte inferior del panel de navegación izquierdo para seleccionar un área diferente.

> [!div class="mx-imgBorder"] 
> ![Abra la aplicación de administración](media/conf-admin-app-open.png "Abrir la aplicación de administrador")

## <a name="step-4-update-the-mobile-app-branding-and-tracking-level"></a>Paso 4: actualice la marca de la aplicación móvil y el nivel de seguimiento

Puede cambiar el ícono de la aplicación, el esquema de color o nombre de las aplicaciones móviles para que coincida con la marca de su organización. También puede especificar si los trabajadores de primera línea pueden rastrear la información por ubicación o instalaciones utilizando las aplicaciones móviles. Para estos usted usa las entidades **Aplicación** y **Configuración de aplicación** en el área **Administración**.

1.  Abra la aplicación de administración y, en el panel de navegación izquierdo de la aplicación de administración, seleccione **Administración** desde el selector de área, y luego seleccione **Aplicaciones**. Esto mostrará todos los registros de la aplicación de lienzo que importó del archivo **App Import.xlsx**.

    > [!div class="mx-imgBorder"] 
    > ![Aplicaciones de administrador](media/conf-admin-app-records.png "Aplicaciones de administrador")

1.  Abra uno de los registros de la aplicación seleccionándolo. 

    > [!div class="mx-imgBorder"] 
    > ![Campo Id. de Power App ](media/conf-powerapp-id-field.png "Actualizar la información de la aplicación")

1.  En la página de detalles de la aplicación:
 
    1. Haga doble clic en el icono de la aplicación y seleccione un archivo de icono para la aplicación desde la carpeta **Iconos de aplicaciones**. Los archivos de imagen tienen nombres intuitivos para que pueda seleccionar fácilmente el icono correcto. Por ejemplo, seleccione el archivo "Emergency Response App.png" para la **aplicación Emergency Response**. También puede seleccionar una imagen personalizada según la marca de su organización.

    3. Si es necesario, actualice la **Descripción** o **Nombre para mostrar** de la aplicación.

    4. Si es necesario, actualice el valor **Ocultar aplicación del menú** para establecer si la aplicación debe mostrarse en la lista de aplicaciones. Como la **aplicación Emergency Response** es una aplicación de contenedor, el valor se establece en **No** por defecto.

    5. Si es necesario, actualice el valor **Rango de visualización de la aplicación** para establecer la posición de visualización de la aplicación en la lista de aplicaciones.

    6. Si es necesario, seleccione un valor en el campo **Nivel de seguimiento** para especificar si desea realizar un seguimiento de los datos en esta aplicación móvil en el nivel de **Ubicación** o **Instalaciones**. Más información: [Administrar el nivel de seguimiento de aplicaciones móviles](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

    7. Seleccione **Guardar**.

1.  Repita los pasos 2 y 3 para cada registro de aplicación de lienzo en **Aplicaciones**.

1.  En el panel izquierdo, seleccione **Configuración de aplicación**.

1.  Seleccione el registro **Aplicación Emergency Response** para abrirlo para editarlo.

    1.  Si es necesario, actualice los colores para su aplicación.

    2.  Seleccione **Sí** o **No** en el campo **Dispositivo compartido habilitado** para especificar si la opción **Desconectar** estará disponible en aplicaciones móviles o no. Seleccionando **Sí** hará que la opción **Desconectar** esté disponible. Más información: [Fin de turno: cerrar sesión](use.md#end-shift---sign-out) en la guía del usuario.

    > [!div class="mx-imgBorder"] 
    > ![Campo para compartir dispositivos habilitado](media/conf-device-sharing-enabled-field.png "Campo para compartir dispositivos habilitado")

1.  Seleccione **Guardar** en la esquina inferior derecha para guardar sus cambios.

## <a name="step-5-bypass-consent-for-mobile-apps-optional"></a>Paso 5: omita el consentimiento para aplicaciones móviles (opcional)

Opcionalmente, puede configurar omitir el consentimiento del usuario para sus aplicaciones móviles para que los usuarios no tengan permisos de ubicación. Debe ser un administrador de inquilinos para completar este paso. Además, antes de realizar este paso, necesitará el id. de la aplicación de cada aplicación móvil (aplicación de lienzo).

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

## <a name="step-6-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional"></a>Paso 6: agregar la clave de Azure Application Insights para aplicaciones móviles para telemetría (opcional)

Opcionalmente, puede usar Azure Application Insights para recopilar telemetría detallada para sus aplicaciones móviles (aplicaciones de lienzo) para obtener información sobre el uso de la aplicación. Para obtener información detallada sobre esto, vea [Analice la telemetría de la aplicación usando Application Insights](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights)

## <a name="step-7-share-canvas-apps-with-users-in-your-organization"></a>Paso 7: Comparta aplicaciones de lienzo con los usuarios de su organización

Para que los usuarios de primera línea utilicen y consuman datos utilizando las aplicaciones de lienzo en sus dispositivos móviles, las aplicaciones deben compartirse con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con grupos de usuarios.

> [!IMPORTANT]
> Asegúrese de que el usuario o grupo con el que planea compartir las aplicaciones *ya* tiene acceso a su entorno. Por lo general, ya habría agregado usuarios o grupos al [configurar su entorno](#step-2-sign-up-for-power-apps-and-create-an-environment). Alternativamente, puede seguir los pasos aquí para agregar usuarios a su entorno y proporcionar el acceso adecuado antes de compartir aplicaciones con ellos: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

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

## <a name="step-8-set-your-mobile-app-as-hero-and-featured-app-optional"></a>Paso 8: Establecer su aplicación móvil como aplicación destacada y prominente (opcional)

Opcionalmente, puede configurar su aplicación móvil como principal y aplicación destacada dentro de la aplicación móvil de **Power Apps**. Debe ser un administrador de inquilinos para completar este paso.

Antes de realizar este paso, necesitará el id. de la aplicación de cada aplicación móvil (aplicación de lienzo) que desea establecer como héroe y aplicación destacada. Para obtener información sobre cómo obtener el identificador de aplicación de una aplicación de lienzo, consulte 

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
 

## <a name="step-9-share-model-driven-app-with-admins-in-your-organization"></a>Paso 9: Comparta la aplicación basada en modelos con los administradores de su organización

Para que los usuarios administradores utilicen la aplicación de administración (aplicación basada en modelos), se debe compartir con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con un grupo de usuarios administradores.

> [!IMPORTANT]
> Asegúrese de que el usuario o grupo con el que planea compartir la aplicación *ya* tiene acceso a su entorno. Por lo general, ya habría agregado usuarios o grupos al [configurar su entorno](#step-2-sign-up-for-power-apps-and-create-an-environment). Alternativamente, puede seguir los pasos aquí para agregar usuarios a su entorno y proporcionar el acceso adecuado antes de compartir la aplicación con ellos: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

2. En el panel de navegación izquierdo, seleccione Aplicaciones para ver una lista de todas tus aplicaciones.

3. Seleccione la aplicación basada en modelos (**Aplicación de administración: aplicación Emergency Respone**) y seleccione **Compartir** en el banner.

4. Especifica el grupo de Azure AD o usuarios administradores con los que desea compartir esta aplicación, asigne el rol de seguridad **Administrador de Emergency Response**, y seleccione **Compartir**.

## <a name="step-10-publish-the-power-bi-dashboard"></a>Paso 10: Publicar el panel Power BI

Publique el panel Power BI y compártalo con los usuarios de su organización para que puedan usar el panel de control para obtener información y tomar decisiones.

Puede publicar el panel de Power BI usando cualquiera de las siguientes opciones: usando la aplicación de plantilla de AppSource *o* utilizand el archivo **.pbit** disponible en el paquete de implementación.

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>Opción A: publicar usando la aplicación de plantilla de AppSource (opción preferida)

Dispone de información detallada sobre el uso de la aplicación de plantilla del AppSource aquí: [Conectarse al panel de soporte de decisiones de Hospital Emergency Response](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-health-emergency-response)

> [!IMPORTANT]
> Esta es una manera más fácil de publicar el panel de Power BI que usar la opción de archivo .pbit para publicar. Recomendamos a los clientes que usen esta opción en lugar de publicar con la opción de archivo .pbit. 

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>Opción B: publicar usando el archivo .pbit en el paquete de implementación

Esta sección proporciona información sobre cómo puede usar el archivo **Emergency Response App.pbit**, disponible en el paquete de implementación para publicar el panel de control.

#### <a name="prerequisites"></a>Requisitos previos

- Descargue el último paquete de implementación (archivo .zip) de <https://aka.ms/emergency-response-solution>. Después de descargar, extraiga el archivo .zip en su computadora. El archivo .pbit estará disponible en la carpeta **Power BI Template**

- Power BI capacidad Premium o licencias Power BI profesionales asignadas a usuarios que acceden al informe. 

- Cree un espacio de trabajo en Power BI donde publicar el informe. Inicie sesión en Power BI y cree un espacio de trabajo. Más información: [Crear los espacios de trabajo nuevos en Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Instalar Power BI Desktop desde la tienda de aplicaciones de Windows: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Si en el pasado instaló Power BI Desktop descargándolo directamente de la página del Centro de descargas como un ejecutable, elimínelo y use el de Microsoft Store. La versión de Microsoft Store se actualiza automáticamente a medida que hay nuevas versiones disponibles.
   >
   > Si no puede instalar desde Microsoft Store, instale la última versión que no sea de Microsoft Store en la [página del Centro de descargas](https://www.microsoft.com/download/details.aspx?id=58494).

- Después de instalar Power BI Desktop desde la tienda de aplicaciones, ejecútelo, inicie sesión con una cuenta que tenga permiso para publicar aplicaciones Power BI en su organización.

#### <a name="publish-the-dashboard-using-the-pbit-file"></a>Publicar el panel usando el archivo .pbit

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

### <a name="after-publishing-the-dashboard"></a>Después de publicar el panel

Para ver el panel de Power BI publicado, consulte [Ver el panel de Power BI](configure-data-reporting.md#view-power-bi-dashboard)

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-issues>.

- Para comentarios sobre la aplicación de muestra Hospital Emergency Response, visite <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Paso siguiente

[Usar la aplicación Hospital Emergency Response](use.md)
