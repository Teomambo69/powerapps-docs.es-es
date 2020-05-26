---
title: Implementar la solución de supervisión y respuesta de emergencia de la administración pública regional | Documentos de Microsoft
description: Proporciona instrucciones detalladas para que los administradores de TI regionales implementen la solución de Supervisión y Respuesta de Emergencia de la administración pública Regional para su organización.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 7c2d72201e9ae45e6d8957434aa9d4014cb593a6
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342087"
---
# <a name="deploy-the-regional-governmentemergency-response-and-monitoring-solution"></a>Implementar la solución de supervisión y respuesta de emergencia de la administración pública regional

Los administradores de TI de las organizaciones regionales pueden usar este artículo para implementar la solución de Supervisión y Respuesta ante Emergencias del Gobierno Regional. Al final de este proceso de implementación, tendrá lo siguiente:

- Una aplicación de administración (aplicación basada en modelos) que le permite configurar y ver datos maestros para las organizaciones principales y sus sistemas hospitalarios, agregar y administrar usuarios administradores de las organizaciones principales para que puedan usar el portal para informar datos de sus sistemas hospitalarios.

- Un portal web que permite a las organizaciones primarias individuales agregar y administrar datos relacionados con sus usuarios, sistemas hospitalarios, regiones, instalaciones, pacientes, suministros y personal.

- Un panel de control de Power BI al que sus administradores regionales pueden acceder en su inquilino de Power BI para ver los datos clave y las ideas de todas las organizaciones primarias que informan los datos a su organización regional. El mismo panel de control está incrustado en el portal para que los administradores de la organización principal vean datos clave y conocimientos solo para sus organizaciones primarias y sistemas hospitalarios.

Siga los pasos siguientes para implementar la solución de Supervisión y Respuesta ante Emergencias del Gobierno Regional para su organización.

Tiempo estimado para completar estos pasos: 35–40 minutos.

> [!IMPORTANT]
> Si tiene una instalación existente de esta solución, siga estos pasos para actualizar a la última versión: [Actualizar la solución](upgrade.md)

## <a name="service-urls-for-us-government-customers"></a>URL de servicio para clientes del gobierno de EE. UU.

Hay un conjunto diferente de URL para acceder a entornos del de la administración pública de EE. UU. en Power Apps e inquilinos Power BI de la administración pública en EE. UU. en lugar de en la versión comercial. La versión comercial de la URL del servicio se utiliza en este artículo. Si es cliente de una organización de la administración pública de Estados Unidos, use la URL correspondiente de la administración pública de Estados Unidos para su implementación como se menciona aquí:

| **Dirección URL comercial de la versión**                | **Dirección URL de la versión para la Administración Pública de Estados Unidos**  |
|-------------------------------------------|--------------------------------|
| [https://make.powerapps.com](https://make.powerapps.com)                | [https://make.gov.powerapps.us](https://make.gov.powerapps.us) (GCC)<br/><br/>[https://make.high.powerapps.us](https://make.high.powerapps.us) (GCC High)                |
| [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) | [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us) (GCC)<br/><br/>[https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us) (GCC High) |
| [https://app.powerbi.com/](https://app.powerbi.com/)                  | [https://app.powerbigov.us](https://app.powerbigov.us) (GCC)<br/><br/>[https://app.high.powerbigov.us](https://app.high.powerbigov.us) (GCC High)                 |

Para obtener información detallada sobre los planes del gobierno de EE. UU. para Power Apps y Power BI, vea:

- [Power Apps para la Administración pública de Estados Unidos](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI para la Administración pública de Estados Unidos](https://docs.microsoft.com/power-bi/service-govus-overview)

## <a name="step-1-download-the-deployment-package"></a>Paso 1: Descargue el paquete de implementación

> [!IMPORTANT]
> Si es un usuario de versión comercial, puede usar la opción AppSource en lugar de usar el paquete de implementación para instalar la aplicación y el panel Power BI. Aún necesita descargar el paquete de implementación para usar los [datos de ejemplo](configure.md##add-and-manage-master-data).

Descargue el último paquete de implementación (.zip) de <https://aka.ms/rer-solution>.

Antes de extraer el archivo .zip, asegúrese de desbloquearlo.

1.  Haga clic con el botón secundario en el archivo .zip y seleccione **Propiedades**.

2.  En el cuadro de diálogo de propiedades, seleccione **Desbloquear** y luego seleccione **Aplicar** seguido de **Aceptar**.

    > [!div class="mx-imgBorder"] 
    > ![Paquete de propiedades de la solución](media/deploy-deployment-package.png "Paquete de propiedades de la solución")

Al extraer el archivo .zip, verá lo siguiente en la carpeta extraída:

|**Carpeta**  |**Descripción**  |
|---------|---------|
|**Paquete**     |  La carpeta contiene la herramienta Package Deployer y el paquete que importará más adelante para configurar la solución en su entorno.       |
|**Power BIPlantilla**     | Contiene el Archivo de plantilla de informe Power BI (.pbit) que usará para configurar los informes. Más información: [Paso 5: configurar y publicar el panel Power BI](#step-5-configure-and-publish-power-bi-dashboard)        |
|**SampleData**     |   Contiene los archivos de datos maestros de muestra (.xlsx) que puede usar para importar datos de ejemplo. Más información: [Importar datos usando archivos de ejemplo](configure.md#import-data-using-sample-files)      |

## <a name="step-2-sign-up-for-power-apps-and-create-an-environment"></a>Paso 2: Regístrese en Power Apps y cree un entorno

Si aún no tiene Power Apps, regístrese en Power Apps y compre una licencia apropiada.
Más información:

- [Power AppsPrecios](https://powerapps.microsoft.com/pricing/)

- [ComprarPower Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Después de haber comprado Power Apps, cree un entorno con una base de datos Common Data Service.

1.  Inicie sesión en el [Centro de administración de Power Platform](https://aka.ms/ppac).

2.  Cree un entorno Common Data Service con la base de datos. Más información: [Crear y administrar entornos](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT] 
    > Al crear la base de datos, si selecciona un grupo de seguridad para la base de datos, las aplicaciones se pueden compartir solamente con usuarios que son miembros del grupo de seguridad.

3.  Cree usuarios apropiados en su entorno. Más información: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

Después de haber creado su entorno, puede acceder a él utilizando la siguiente URL: https://[myenv].crm.dynamics.com, donde [myenv] es el nombre de su entorno. Anote la URL de este entorno.

## <a name="step-3-create-a-power-apps-portal-in-your-environment"></a>Paso 3: cree un portal Power Apps en su entorno

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  Asegúrese de que su entorno recién creado esté seleccionado en la esquina superior derecha.

3.  En el panel izquierdo, seleccione **Aplicaciones** y luego seleccione **Nueva aplicación** \> **Portal**.

    > [!div class="mx-imgBorder"] 
    > ![Crear un portal Power Apps](media/deploy-create-powerapps-portal.png "Crear un portal Power Apps")

4.  En la página **Portal desde cero**, especifique los valores apropiados y luego seleccione **Crear**.

    > [!div class="mx-imgBorder"] 
    > ![Crear un portal desde cero](media/deploy-portal-from-blank.png "Crear un portal desde cero")

Power Apps comenzará a aprovisionar el portal para usted y el mensaje de progreso se mostrará en la esquina superior derecha de la página.

> [!NOTE]
> Puede llevar un tiempo aprovisionar su portal.

Después de aprovisionar el portal, aparecerá en su lista **Aplicaciones** en Power Apps. Puede seleccionar los puntos suspensivos (...) para su registro de portal y seleccionar **Examinar** para ver el portal de inicio.

> [!div class="mx-imgBorder"] 
> ![Ver portal de inicio](media/deploy-view-starter-portal.png "Ver portal de inicio")

  > [!IMPORTANT]
  > Espere a que el portal se aprovisione antes de pasar al siguiente paso.

## <a name="step-4-install-the-app"></a>Paso 4: Instalar la aplicación

Después de aprovisionar su portal, instale la aplicación de supervisión y respuesta de emergencia de la administración pública regional para configurar el portal que creó anteriormente e instale la aplicación de administración (aplicación basada en modelos).

Puede instalar la aplicación usando una de las 3 opciones siguientes:

- Microsoft AppSource (solo para clientes de Power Apps gobierno de EE. UU.). Ver [Opción A: instalar la aplicación desde Microsoft AppSource (Clientes del gobierno de EE. UU.)](#option-a-install-the-app-from-microsoft-appsource-us-govt-customers)

- Microsoft AppSource (para clientes con la versión comercial de Power Apps). Ver [Opción B: instalar la aplicación desde Microsoft AppSource](#option-b-install-the-app-from-microsoft-appsource)

- Paquete de implementación que descargó anteriormente. Ver [Opción C: instalar la aplicación desde el paquete de implementación](#option-c-install-the-app-from-the-deployment-package)

### <a name="option-a-install-the-app-from-microsoft-appsource-us-govt-customers"></a>Opción A: instalar la aplicación desde Microsoft AppSource (Clientes del gobierno de EE. UU.)

1.  Inicie sesión en el Centro de administración de Power Platform. Use la URL apropiada para iniciar sesión:
    - **GCC**: [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us)
    - **GCC High**: [https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us).

2.  En el panel izquierdo, seleccione **Entornos** y luego seleccione el nombre del entorno que creó anteriormente.

3. En la página de detalles del entorno, seleccione **Administrar aplicaciones de Dynamics 365**.

    > [!div class="mx-imgBorder"] 
    > ![Configuración del entorno](media/ppac-env-setting.png "Configuración del entorno")

3.  En la página de aplicaciones de Dynamics 365, seleccione **Instalar aplicación**. Después seleccione **Supervisión y respuesta de emergencia de la administración pública regional** en el panel derecho y seleccione **Siguiente**.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/ppac-install-app.png "Instalar aplicación")

4.  En la página siguiente, acepte los términos y seleccione **Instalar**.

5.  La instalación comenzará y puede seguir el progreso de la instalación de su aplicación en la página de aplicaciones de Dynamics 365.

    > [!div class="mx-imgBorder"] 
    > ![Progreso de la instalación de la aplicación de supervisión](media/ppac-app-install-progress.png "Progreso de la instalación de la aplicación de supervisión")

    > [!IMPORTANT]
    > La aplicación puede tardar un tiempo en instalarse.

6.  Después de instalar la aplicación, vaya hasta [Power Apps](https://make.powerapps.com) y seleccione su entorno en la esquina superior derecha. Encontrará una nueva aplicación de administración en su lista **Aplicaciones**.

    > [!div class="mx-imgBorder"] 
    > ![Nueva aplicación de administrador en la lista de aplicaciones](media/deploy-new-admin-app.png "Nueva aplicación de administrador en la lista de aplicaciones")

### <a name="option-b-install-the-app-from-microsoft-appsource"></a>Opción B: instalar la aplicación desde Microsoft AppSource

1.  Vaya a [AppSource](https://appsource.microsoft.com/) y busque "Respuesta de emergencia del gobierno regional".<br/>Alternativamente, navegue directamente a la aplicación en AppSource usando este enlace: <https://appsource.microsoft.com/product/dynamics-365/mscrm.pprersapp>

2.  En la página de Respuesta y seguimiento de emergencia del gobierno regional, seleccione **Conseguir ahora**.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/deploy-appsource-01.png "Aplicación en AppSource")

3.  Se le solicita que revise los términos del acuerdo de AppSource. El cuadro de diálogo también muestra la cuenta que se está utilizando para iniciar sesión. Seleccione **Continuar**. Es posible que se le solicite que verifique sus credenciales.

4.  En la página siguiente, seleccione el entorno donde quiera instalar la aplicación. Seleccione las casillas de verificación de términos legales y declaraciones de privacidad, y seleccione **De acuerdo**.

    > [!div class="mx-imgBorder"] 
    > ![Seleccionar un entorno](media/deploy-appsource-02.png "Seleccionar un entorno")

5.  Se lo dirigirá al Centro de administración de Dynamics 365 donde puede seguir el progreso de la instalación de su aplicación.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/deploy-appsource-03.png "Progreso de la instalación de la aplicación de supervisión")

    > [!IMPORTANT]
    > La aplicación puede tardar un tiempo en instalarse.

6. Después de instalar la aplicación, vaya hasta [Power Apps](https://make.powerapps.com) y seleccione su entorno en la esquina superior derecha. Encontrará una nueva aplicación de administración en su lista **Aplicaciones**.

    > [!div class="mx-imgBorder"] 
    > ![Nueva aplicación de administrador en la lista de aplicaciones](media/deploy-new-admin-app.png "Nueva aplicación de administrador en la lista de aplicaciones")

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

8.  La siguiente pantalla valida si hay un portal de inicio disponible en su entorno. Seleccione **Siguiente** para continuar con la instalación.

    > [!div class="mx-imgBorder"] 
    > ![Validar portal de inicio](media/deploy-validate-starter-portal.png "Validar portal de inicio")

9.  La siguiente pantalla muestra el estado de instalación del paquete. Tenga en cuenta que puede llevar un tiempo completar la instalación del paquete.

10. Después de completar la instalación, seleccione **Siguiente**.

11.  En la siguiente pantalla, seleccione **Terminar** para completar y cerrar la configuración.

12. Después de instalar la aplicación, vaya hasta [Power Apps](https://make.powerapps.com) y seleccione su entorno en la esquina superior derecha. Encontrará una nueva aplicación de administración en su lista **Aplicaciones**.

    > [!div class="mx-imgBorder"] 
    > ![Nueva aplicación de administrador en la lista de aplicaciones](media/deploy-new-admin-app.png "Nueva aplicación de administrador en la lista de aplicaciones")

## <a name="step-5-configure-and-publish-power-bi-dashboard"></a>Paso 5: Configurar y publicar el panel de Power BI

En este paso, configuraremos y publicaremos el panel de Power BI para que pueda integrarse en el portal. Al final de este paso, tendrá una URL de informe que se utilizará para incrustar el informe en el portal.

Puede publicar el panel de Power BI usando cualquiera de las siguientes opciones: usando la aplicación de plantilla de AppSource o utilizando el archivo .pbit disponible en el paquete de implementación.

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>Opción A: publicar usando la aplicación de plantilla de AppSource (opción preferida)

Dispone de información detallada sobre el uso de la aplicación de plantilla del AppSource aquí: [Conectarse al panel de soporte de decisiones de regional Emergency Response](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-regional-emergency-response)

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>Opción B: publicar usando el archivo .pbit en el paquete de implementación

Esta sección proporciona información sobre cómo puede usar el archivo **Regional Emergency Response App.pbit**, disponible en el paquete de implementación para publicar el panel de control.

#### <a name="prerequisites"></a>Requisitos previos

-   Debe ser un administrador global y debe tener una licencia Power BI Pro para configurar y publicar informes.

-   Cree un área de trabajo en Power BI donde publicará el informe. Inicie sesión en Power BI y cree un espacio de trabajo. Más información:  [Crear los espacios de trabajo nuevos en Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

-   Instalar Power BI Desktop desde Microsoft Store: <https://aka.ms/pbidesktop>

    > [!NOTE]
    > Si en el pasado instaló Power BI Desktop descargándolo directamente de la página del Centro de descargas como un ejecutable, elimínelo y use el de Microsoft Store. La versión de Microsoft Store se actualiza automáticamente a medida que hay nuevas versiones disponibles.
    >
    > Si no puede instalar desde Microsoft Store, instale la última versión que no sea de Microsoft Store en la [página del Centro de descargas](https://www.microsoft.com/download/details.aspx?id=58494).

#### <a name="the-process"></a>El proceso

1.  Ejecute Power BI Desktop e inicie sesión usando su cuenta.

2.  Vaya a la ubicación donde extrajo el [paquete de implementación](#step-1-download-the-deployment-package) (.zip). En la carpeta Power BI Plantilla encontrará **Regional Emergency Response App.pbit**.

3.  Abra el archivo **Regional Emergency Response App.pbit** en Power BI Desktop. Se le pedirá que escriba el siguiente valor: **CDS_base_solution_URL**. Escriba la URL de su instancia del entorno de Common Data Service. Por ejemplo: https://*[myenv]*. crm.dynamics.com, donde *[myenv]* es el nombre de su entorno. Seleccione **Cargar**.

    > [!div class="mx-imgBorder"] 
    > ![Configurar el panel de Power BI](media/deploy-config-dashboard.png "Configurar el panel de Power BI") 

4.  Se le pedirá que introduzca las credenciales para conectarse a su entorno Common Data Service. Seleccione  **Cuenta organizacional** \> **Iniciar sesión** para especificar sus credenciales de Common Data Service.

    > [!div class="mx-imgBorder"] 
    > ![Conectarse al entorno de Common Data Service](media/deploy-connect-cds.png "Conectarse al entorno de Common Data Service")

5.  Después de iniciar sesión, seleccione  **Conectar** para conectarse a sus datos en Common Data Service.

6.  En una conexión con éxito, Power BI mostrará el informe. Se le solicitará que aplique los cambios pendientes a su consulta; seleccione **Aplicar cambios**.

    > [!NOTE]
    > El informe está en blanco porque aún no ha agregado datos en el sistema.

7.  Seleccione  **Publicar** para publicar datos en su espacio de trabajo Power BI. Se le pedirá que guarde sus cambios; seleccione **Guardar**.

     > [!div class="mx-imgBorder"] 
     > ![Guardar área de trabajo Power BI](media/deploy-save-workspace.png "Guardar área de trabajo Power BI")

8.  Se le pedirá que guarde el archivo como un archivo .pbix junto con su información del entorno Common Data Service. Proporcione un nombre y guárdelo en su computadora.

9.  Después de guardar el archivo .pbix, se le pedirá que publique el informe. En la página **Publicar en Power BI**, seleccione el espacio de trabajo donde desea publicar y luego haga clic en **Seleccionar**.

    > [!div class="mx-imgBorder"] 
    > ![Publicar en Power BI](media/deploy-publish-workspace.png "Publicar en Power BI")

10.  El informe estará disponible en su espacio de trabajo. Ahora, configuraremos la configuración de actualización de datos para conjunto de datos. Bajo la pestaña **Conjuntos de datos** de su espacio de trabajo, seleccione el icono **Programar actualización** del conjunto de datos de su informe que acaba de publicar.

      > [!div class="mx-imgBorder"] 
      > ![Informe disponible en el área de trabajo](media/deploy-report-workspace.png "Informe disponible en el área de trabajo")

11.  La primera vez que intente establecer la configuración de actualización de datos, verá la página  **Configuración** con un mensaje que indica que sus credenciales no son válidas. En  **Credenciales de origen de datos**, seleccione  **Editar credenciales** para especificar sus credenciales.

      > [!div class="mx-imgBorder"] 
      > ![Credenciales del origen de datos](media/deploy-datasource-credentials.png "Credenciales del origen de datos")

12.  En la pantalla siguiente:

      1.  Seleccione el **Método de autenticación** como **OAuth2**.

      2.  Seleccione **Configuración del nivel de privacidad para este origen de datos** como **Organizativo**.

      3.  Seleccione **Iniciar sesión**.

13.  Se le pedirá que especifique sus credenciales e inicie sesión. Después de iniciar sesión correctamente, volverá a la página **Configuración**.

14.  En la página **Configuración**, expanda **Actualización programada** y especifique los detalles necesarios para actualizar los datos en función de una programación. Seleccione **Aplicar**.

      > [!div class="mx-imgBorder"] 
      > ![Actualización de datos programada](media/deploy-schedule-refresh-data.png "Actualización de datos programada")

      > [!NOTE]
      > - Existen límites sobre cuántas veces se pueden actualizar los datos. Power BI limita los conjuntos de datos en capacidad compartida a ocho actualizaciones diarias. Si conjunto de datos reside en una capacidad Premium, puede programar hasta 48 actualizaciones por día en la configuración de conjunto de datos. Más información:  [Actualizar datos](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)
      >- Recomendamos configurar los datos para actualizar cada 30 minutos.

15.  Luego, regrese a su área de trabajo, seleccione la pestaña **Informes** y luego seleccione el informe para abrirlo en el navegador.

        > [!div class="mx-imgBorder"] 
        > ![Abrir informe en explorador](media/deploy-open-report.png "Abrir informe en explorador")

16.  El URL debe tener el formato siguiente: https://app.powerbi.com/groups/3d6db5d0-22c7-4674-b957-0605c021511d/reports/bf9cd5a1-c176-4786-9c4e-684a79678575/ReportSection?redirectedFromSignup=1<br/>
    Copie la URL del informe Power BI a un Bloc de notas, ya que lo necesitará en la siguiente sección para incrustarlo en el portal.

17. Si quiere que este informe de Power BI esté disponible para otros usuarios dentro de su inquilino Power BI, considere publicar el informe como una aplicación. Seleccione el nombre de su espacio de trabajo en el panel izquierdo y luego seleccione **Crear aplicación** en la esquina superior derecha.  

18. En la página de publicación de aplicación:

    1. En la pestaña **Configurar**, especifique el nombre y la descripción de su aplicación.

    2. En la pestaña **Navegación**, especifique la ubicación en la que se publicará.

    3. En la pestaña **Permisos**, especifique los usuarios o grupos que podrán ver esta aplicación. Asegúrese de seleccionar la casilla de verificación **Instalar esta aplicación automáticamente** para instalar esta aplicación automáticamente para usuarios finales. Más información: [Instalar automáticamente aplicaciones para usuarios finales](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![seleccionar-instalar-aplicaciones-automáticamente](media/select-install-apps-automatically.png)

18. Seleccione **Publicar aplicación** Para obtener información detallada sobre la publicación de aplicaciones en Power BI, consulte [Publicar su aplicación](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).


## <a name="step-6-embed-power-bi-report-in-portal"></a>Paso 6: Insertar el informe Power BI en el portal

En este paso, insertaremos el informe Power BI (publicado en el paso anterior) en su portal.

### <a name="prerequisites"></a>Requisitos previos

- Debe tener el rol de Administrador global para realizar este paso.

- Antes de poder insertar un informe Power BI en un portal Power Apps, **Power BI visualización** y el servicio **Power BI Embedded** deben estar habilitados para su portal utilizando el [Centro de administración de Power Apps Portals](https://docs.microsoft.com/powerapps/maker/portals/admin/admin-overview).

  > [!div class="mx-imgBorder"] 
  > ![Centro de administración de Power Apps](media/deploy-admin-center.png "Centro de administración de portales de Power Apps")

Para obtener instrucciones paso a paso, consulte lo siguiente en los documentos de portales Power Apps:

-   [Habilitar visualización de Power BI](https://docs.microsoft.com/powerapps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-visualization)

-   [Habilitar el servicio Power BI Embedded](https://docs.microsoft.com/powerapps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-embedded-service)

### <a name="the-process"></a>El proceso

Ahora que ha habilitado Power BI visualización y el servicio Power BI Embedded, agregaremos la URL del informe para insertar en su portal. Asegúrese de tener a mano la URL de su informe Power BI del paso anterior.

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  En el panel izquierdo, seleccione **Aplicaciones** y seleccione la aplicación **Administración del portal** para abrirlo.

    > [!div class="mx-imgBorder"] 
    > ![Abrir la aplicación de administración del portal](media/deploy-open-mgmt-app.png "Abrir la aplicación de administración del portal")

3.  En el panel izquierdo seleccione **Configuración del sitio** y seleccione **Nuevo**:

    > [!div class="mx-imgBorder"] 
    > ![Nueva configuración del sitio](media/deploy-site-settings.png "Nueva configuración del sitio")

4.  En la página **Nueva configuración del sitio**, especifique los siguientes valores:

    1.  **Nombre** : Ruta de PowerBI

    2.  **Sitio web**: seleccione **Portal de inicio**

    3.  **Valor**: copie la URL del informe de Power BI del paso anterior.

        > [!div class="mx-imgBorder"] 
        > ![Valores de configuración del sitio](media/deploy-site-setting-values.png "Valores de configuración del sitio")

5.  Seleccione **Guardar y cerrar** para guardar el registro.

### <a name="restart-the-portal"></a>Reiniciar el portal

Ahora reiniciaremos el portal para que los cambios surjan efecto.

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  En el panel izquierdo, seleccione **Aplicaciones**, seleccione el menú de puntos suspensivos (...) para su portal y seleccione **Configuración**.

    > [!div class="mx-imgBorder"] 
    > ![Menú del portal de aplicaciones](media/deploy-portal-menu.png "Menú del portal de aplicaciones")

3.  En el panel **Configuración del portal** , seleccione **Administración**.

    > [!div class="mx-imgBorder"] 
    > ![Administración de configuración del portal](media/deploy-settings-admin.png "Administración de configuración del portal")

4.  En el centro de administración de Power Apps Portals, seleccione **Acciones del portal** \> **Reiniciar**.

    > [!div class="mx-imgBorder"] 
    > ![Reiniciar acciones de portal](media/deploy-portal-restart.png "Reiniciar acciones de portal")

5.  Seleccione **Reiniciar** en el mensaje de confirmación para reiniciar el portal.

  > [!NOTE]
  > Opcionalmente, también puede configurar una URL personalizada para su portal utilizando un nombre de dominio personalizado. Un dominio personalizado puede ayudar a sus clientes a encontrar los recursos de soporte más fácilmente y mejorar su marca. Para obtener información detallada para hacerlo, consulte [Agregar un dominio personalizado](https://docs.microsoft.com/powerapps/maker/portals/admin/add-custom-domain) en los documentos de portales.

## <a name="step-7-add-a-custom-title-and-logo-for-your-portal"></a>Paso 7: Agregue un título y logotipo personalizados para su portal

Puede agregar un logotipo y título personalizados a su portal para alinearlos con la marca de su organización.

> [!NOTE]
> Para la imagen de logotipo personalizada, el color recomendado es blanco transparente con un tamaño de marco de icono de 40x40px y un tamaño de icono de 24x24px con relleno de 8px en formato SVG. Si está utilizando el formato PNG / JPG para el logotipo, use un tamaño de marco de icono de 80x80px y un tamaño de icono de 48x48px con relleno de 16px.

### <a name="the-process"></a>El proceso

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  Abra la aplicación **Administración del portal** de su lista de aplicaciones.

3.  En el panel izquierdo seleccione **Configuración del sitio** y seleccione **Nuevo**.

4.  En la página **Nueva configuración del sitio**, especifique los siguientes valores:

    1.  **Nombre**: título del sitio

    2.  **Sitio web**: seleccione **Portal de inicio**

    3.  **Valor**: cadena que desea que aparezca en la esquina superior izquierda de su portal.

        > [!div class="mx-imgBorder"] 
        > ![Configuración del sitio de administración del portal](media/deploy-portal-site-settings.png "Configuración del sitio de administración del portal")
        
5.  Seleccione **Guardar** para guardar el registro de configuración del sitio.

6.  Seleccione **Nuevo** para crear otro registro de configuración del sitio.

7.  En la página **Nueva configuración del sitio**, especifique los siguientes valores:

    1.  **Nombre**: SiteLogoPath

    2.  **Sitio web**: seleccione **Portal de inicio**

    3.  **Valor**: nombre del archivo de imagen de su logotipo. Por ejemplo, especificar mylogo.png hará que el portal busque este archivo en la raíz del portal. Más tarde cargaremos el archivo del logotipo en nuestro portal.

        > [!div class="mx-imgBorder"] 
        > ![Crear nuevo registro de configuración del sitio](media/deploy-create-new-settings.png "Crear nuevo registro de configuración del sitio")       

8.  Seleccione **Guardar y cerrar** para guardar este registro y cerrar la página.

9.  Ahora, cargaremos el archivo de imagen del logotipo. En el panel izquierdo, seleccione **Archivos Web** y seleccione **Nuevo**:

10. Abra la pantalla **Nuevo archivo Web** y especifique los valores siguientes:

    1.  **Nombre**: mylogo.png

    2.  **Sitio web**: seleccione **Portal de inicio**

    3.  **Página primaria:** seleccione **Elegir instalación**

    4.  **URL parcial:** mylogo.png

        > [!IMPORTANT]
        > Asegúrese de que este valor coincida con el valor que especificó anteriormente para la configuración del sitio **SiteLogoPath**.

    5.  **Estado de publicación**: seleccione **Publicado**

        > [!div class="mx-imgBorder"] 
        > ![Nuevo archivo web](media/deploy-new-web-file.png "Nuevo archivo web")

11.  Seleccione **Guardar** para guardar el registro.

12.  Seleccione la pestaña **Notas** y luego seleccione **+** seguido por **Nota**.

      > [!div class="mx-imgBorder"] 
      > ![Notas de archivo web](media/deploy-web-file-notes.png "Notas de archivo web")

13.  En el campo **Título** introduzca mylogo.png. Seleccione el icono de archivo adjunto para seleccionar el archivo de imagen del logotipo de su ordenador.

      > [!div class="mx-imgBorder"] 
      > ![Adjuntar imagen del logotipo](media/deploy-attach-logo.png "Adjuntar imagen del logotipo")

14.  Seleccione la imagen de logotipo apropiada de su ordenador (en formato .PNG).
    La imagen seleccionada aparece en la página.

15.  Seleccione **Agregar nota**.

16.  Seleccione Guardar en la esquina inferior derecha de la página para guardar el registro.

Ya está. Puede llevar un tiempo hasta que el último título y logotipo aparezcan en su portal. Actualice su portal en los próximos 5-10 minutos para ver su último título y logotipo.

## <a name="step-8-add-a-custom-about-page-in-your-portal"></a>Paso 8: Agregar una página Acerca de personalizada en su portal

Puede agregar una página Acerca de personalizada en su portal para agregar / presentar información o recursos para sus usuarios.

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  En el panel izquierdo, seleccione **Aplicaciones**, seleccione el menú de puntos suspensivos (...) para su portal y seleccione **Editar**. Esto abrirá la página de configuración del portal.

3.  Seleccione **Nueva pagina** \> **Diseños fijos** \> **Plantilla de página Sobre nosotros.**

    > [!div class="mx-imgBorder"] 
    > ![Página Sobre nosotros](media/deploy-aboutus-page.png "Página Sobre nosotros")
    

4.  En la nueva página web, asegúrese de usar **acerca de** en el campo **URL parcial** en el panel derecho. Puede usar un nombre de su elección en el campo **Nombre**; nosotros usaremos **Acerca de Contoso**.

    > [!div class="mx-imgBorder"] 
    > ![Usar acerca de en la URL parcial](media/deploy-partial-url.png "Usar acerca de en la URL parcial")    

5.  Haga clic en el panel izquierdo para editar los contenidos. Puede usar el editor predeterminado o seleccionar **\</\>** en la esquina inferior derecha para abrir el editor HTML.

    > [!div class="mx-imgBorder"] 
    > ![Editar la página Sobre nosotros](media/deploy-edit-aboutus.png "Editar la página Sobre nosotros")    

6.  Después de realizar los cambios necesarios en la página Acerca de, guárdela y seleccione **Configuración de sincronización** en la esquina superior derecha.

Los usuarios de su portal pueden acceder a la página Acerca de recién creada utilizando el enlace **Acerca de** en el encabezado del portal.

## <a name="step-9-set-up-server-side-synchronization-of-emails"></a>Paso 9: Configurar sincronización del lado del servidor de correos electrónicos

La sincronización del lado del servidor le permite sincronizar correos electrónicos en Common Data Service con Microsoft Exchange Online, Microsoft Exchange Server (local) y un servidor de correo electrónico POP3 para correo electrónico alojado en la web como Gmail o Outlook.com.

> [!div class="mx-imgBorder"] 
> ![Configurar la sincronización de correo electrónico](media/deploy-email-synchronization.png "Configurar la sincronización de correo electrónico")

Para conocer los pasos detallados sobre cómo configurar la sincronización del lado del servidor; vea los siguientes recursos:

-   [Configurar la sincronización del lado del servidor](https://docs.microsoft.com/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks)

-   [Conectarse a Exchange Online](https://docs.microsoft.com/power-platform/admin/connect-exchange-online)

-   [Conectar con Exchange Server (local)](https://docs.microsoft.com/power-platform/admin/connect-exchange-server-on-premises)

    > [!WARNING]
    > Asegúrese de que este usuario no esté configurado para la sincronización del lado del servidor en ningún otro entorno Common Data Service o Dynamics 365. Si tiene una sincronización del lado del servidor configurada en otro entorno, habilitar la sincronización del lado del servidor aquí la deshabilitará en el entorno utilizado anteriormente.

## <a name="step-10-fix-the-send-invitation-process"></a>Paso 10: Corregir el proceso de envío de invitación

En este paso, arreglaremos el proceso **Enviar invitación** proceso para especificar la dirección de correo electrónico desde la cual se enviará la invitación del portal a los administradores de hospitales individuales y la URL de la invitación enviada en el correo electrónico de invitación.

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  Seleccione el icono de rueda dentada en la esquina superior derecha y después seleccione **Configuración avanzada.**

3.  En la página de Configuración, seleccione la flecha desplegable situada junto a **Configuración** y, a continuación, seleccione **Procesos**.

    > [!div class="mx-imgBorder"] 
    > ![Arreglar proceso de envío de invitación](media/deploy-settings-processes.png "Arreglar proceso de envío de invitación")
    

4.  En la página **Procesos**, busque "Enviar invitación" y seleccione el proceso **Enviar invitación** para abrirlo.

5.  En la página de definición de procesos:

    1.  Seleccione **Desactivar** en la barra de comandos para desactivar el proceso. Confirmar desactivación.

    2.  Debajo del área de pasos, seleccione **Establecer propiedades** para el paso **Crear correo electrónico**:

        > [!div class="mx-imgBorder"] 
        > ![Establecer propiedades para Crear correo electrónico](media/deploy-email-properties.png "Establecer propiedades para Crear correo electrónico")

6.  En la página de definición del paso **Crear correo electrónico**:

    1.  Seleccione el identificador de correo electrónico en el campo **Desde** que se utilizará para enviar los enlaces de invitación del portal. La cuenta de usuario especificada aquí debe tener la sincronización del lado del servidor habilitada para que se envíe el correo electrónico.

        > [!TIP]
        >  Es posible que desee configurar una cuenta en su entorno con la sincronización del lado del servidor habilitada y una dirección de correo electrónico como sin respuesta\@[*dominio de cliente*].com para enviar correos electrónicos de invitación al portal.

    2.  Actualice la cadena "https://**regionaldev**.powerappsportals.com" en el cuerpo del correo electrónico con la URL real de su portal. Además, asegúrese de no cambiar el contenido **Codificar código de invitación** resaltado en amarillo.

        Puede realizar otros cambios según sea necesario en el cuerpo del correo electrónico para alinearse con la marca de su organización.

    3.  Seleccione **Guardar y cerrar** para guardar los cambios.

        > [!div class="mx-imgBorder"] 
        > ![Actualizar la URL de su portal](media/deploy-update-url.png "Actualizar la URL de su portal")
        

3.  Volverá a la página de definición de proceso. Guarda los cambios y **Active** el proceso.

    > [!div class="mx-imgBorder"] 
    > ![Activar el proceso](media/deploy-activate-process.png "Activar el proceso")    

## <a name="step-11-fix-the-send-password-reset-to-contact-process"></a>Paso 11: Arreglar el proceso Enviar restablecimiento de contraseña al contacto

En este paso, arreglaremos el proceso **Enviar restablecer contraseña a contacto** para especificar la dirección de correo electrónico desde la cual se enviará el correo electrónico de restablecimiento de contraseña del portal al usuario del portal cuando este solicite restablecer la contraseña utilizando el enlace **Se te olvidó tu contraseña** en el portal.

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  Seleccione el icono de rueda dentada en la esquina superior derecha y después seleccione **Configuración avanzada.**

3.  En la página de Configuración, seleccione la flecha desplegable situada junto a **Configuración** y, a continuación, seleccione **Procesos**.

    > [!div class="mx-imgBorder"] 
    > ![Enviar restablecimiento de contraseña al contacto](media/deploy-password-reset.png "Enviar restablecimiento de contraseña al contacto")
    <!-- ![](media/2ff3f6344a7ea9aa564592a15833fcb3.png) -->

4.  En la página **Procesos**, busque "Enviar restablecer contraseña al contacto" y seleccione el proceso **Enviar restablecer contraseña a contacto** en el resultado de búsqueda para abrirlo.

5.  En la página de definición de procesos:

    1.  Seleccione **Desactivar** en la barra de comandos para desactivar el proceso.
        Confirmar desactivación.

    2.  Debajo del área de pasos, seleccione **Establecer propiedades** para el paso **Enviar correo electrónico**:

        > [!div class="mx-imgBorder"] 
        > ![Establecer propiedades para Enviar correo electrónico](media/deploy-set-email-properties.png "Establecer propiedades para Enviar correo electrónico")
        <!-- ![](media/4a3c0bbf3785cdb7bad4c671964f0220.png) -->

6.  En la página de definición del paso **Enviar correo electrónico**, elimine el valor dinámico (resaltado en amarillo) en el campo **Desde**.

    > [!div class="mx-imgBorder"] 
    > ![Definición del paso Enviar correo electrónico](media/deploy-email-step-definition.png "Definición del paso Enviar correo electrónico")
    <!-- ![](media/8838a0341e240cfe49741d64e761555d.png) -->

7.  Seleccione el identificador de correo electrónico en el campo **Desde** que se utilizará para enviar los enlaces de invitación del portal. La cuenta de usuario especificada aquí debe tener la sincronización del lado del servidor habilitada para que se envíe el correo electrónico.

    > [!TIP]
    > Es posible que desee configurar una cuenta en su entorno con la sincronización del lado del servidor habilitada y una dirección de correo electrónico como sin respuesta\@[*dominio de cliente*].com para enviar correos electrónicos de restablecimiento de contraseña.
    > Asegúrese de no actualizar los valores dinámicos resaltados en amarillo. Opcionalmente, puede actualizar el contenido del cuerpo del correo electrónico según lo requiera su organización en el cuerpo del correo electrónico.

    > [!div class="mx-imgBorder"] 
    > ![No actualice los valores dinámicos](media/deploy-dynamic-values.png "No actualice los valores dinámicos")
    <!-- ![](media/35a0f7a386b2e5345158def083c62402.png) -->

8.  Seleccione **Guardar y cerrar** para guardar los cambios.

9.  Volverá a la página de definición de proceso. Guarda los cambios y **Active** el proceso.

    > [!div class="mx-imgBorder"] 
    > ![Guarda los cambios y active el proceso](media/deploy-save-activate-process.png "Guarda los cambios y active el proceso")    

## <a name="step-12-verify-assign-web-roles-to-new-users-process-is-enabled"></a>Paso 12: Verifique que el proceso Asignar roles web a nuevos usuarios esté habilitado

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  Seleccione el icono de rueda dentada en la esquina superior derecha y después seleccione **Configuración avanzada.**

3.  En la página de Configuración, seleccione la flecha desplegable situada junto a **Configuración** y, a continuación, seleccione **Procesos**.

    > [!div class="mx-imgBorder"] 
    > ![Asignar roles web a nuevos usuarios](media/deploy-assign-webroles.png "Asignar roles web a nuevos usuarios")    

4.  En la página **Procesos**, busque "Asignar web" y asegúrese de que el proceso **Asignar roles web a nuevos usuarios** está habilitado.

    > [!div class="mx-imgBorder"] 
    > ![Asegúrese de que el proceso esté habilitado](media/deploy-process-enabled.png "Asegúrese de que el proceso esté habilitado")    

5.  Si no está habilitado, seleccione el nombre del proceso para abrir el registro y luego seleccione **Activar**. Confirme para activar el proceso.

## <a name="step-13-enable-the-flow-supply-tracking-flow"></a>Paso 13: Habilite el flujo de seguimiento del suministro de Flow

1.  Inicie sesión en [Power Automate](https://flow.microsoft.com/).

2.  En el panel izquierdo, seleccione **Soluciones**. De la lista de soluciones, seleccione **Solución regional de respuesta a emergencias** para abrir la solución.

    > [!div class="mx-imgBorder"] 
    > ![Abrir la solución](media/deploy-open-solution.png "Abrir la solución")

3.  En la solución, filtre **Flow** para encontrar el registro **Seguimiento del suministro de Flow**.

    > [!div class="mx-imgBorder"] 
    > ![Encuentre el registro de seguimiento de suministro de Flow](media/deploy-find-record.png "Encuentre el registro de seguimiento de suministro de Flow")

4.  Seleccione el nombre del flujo para abrir la definición del flujo. En la definición de flujo, seleccione **Editar** en la barra de herramientas.

5.  Arregle la conexión para conectarse a Common Data Service y guarde la información de conexión.

6. En la definición de flujo, seleccione **Encender**.

## <a name="step-14-update-the-details-of-flows-for-sending-emails"></a>Paso 14: Actualice los detalles de los flujos para enviar correos electrónicos

En este paso, haremos lo siguiente:

|Nombre de flujo|Cambios|
|--|--|
|**Solicitud de usuario del portal: enviar correo electrónico al rechazarse la solicitud**|Actualice la conexión para conectarse a Common Data Service y luego especifique una cuenta de usuario para enviar correos electrónicos.|
|**Solicitud de usuario del portal: enviar correo electrónico a los administradores al crearse la solicitud**|Actualice la conexión para conectarse a Common Data Service y luego especifique una cuenta de usuario para enviar correos electrónicos. Además, actualice la URL del portal en el cuerpo del correo electrónico según su URL del portal.| 

1.  Inicie sesión en [Power Automate](https://flow.microsoft.com/).

2.  En el panel izquierdo, seleccione **Soluciones**. De la lista de soluciones, seleccione **Solución regional de respuesta a emergencias** para abrir la solución.

    > [!div class="mx-imgBorder"] 
    > ![Abrir la solución](media/deploy-open-solution.png "Abrir la solución")

3.  En la solución, filtre **Flow**para encontrar los flujos. 

    > [!div class="mx-imgBorder"] 
    > ![Encuentre el registro de seguimiento de suministro de Flow](media/deploy-find-record1.png "Encontrar los flujos")

4.  Selecciona el nombre **Solicitud de usuario del portal: Enviar correo electrónico en solicitud de rechazo** para abrir la definición de flujo. Seleccione **Editar** en la barra de herramientas.

5.  Especifique la conexión para conectarse a Common Data Service seleccionando **Conexiones** y luego usando la conexión existente o usando una nueva credencial seleccionando **Agregar nueva conexión**.  

    > [!div class="mx-imgBorder"] 
    > ![Arreglar credencial](media/deploy-specify-cred.png "Arreglar credenciales")

6.  Después de arreglar la conexión para conectarse a Common Data Service, seleccione **IfRequestState ==** y especifique la cuenta de usuario que tiene una cuenta habilitada para el buzón para enviar correos electrónicos.

    > [!div class="mx-imgBorder"] 
    > ![Especificar credenciales de Outlook](media/deploy-fix-cred2.png "Especificar credenciales de Outlook")

7. Seleccione **Guardar** para guardar los cambios y seleccione **Encender**.

8.  A continuación, vaya a la lista de flujos y seleccione el nombre **Solicitud del usuario del portal: envíe un correo electrónico a los administradores al crear la solicitud** para abrir la definición de flujo. Seleccione **Editar** en la barra de comandos.

9.  Arregle la conexión para conectarse a Common Data Service seleccionando **Conexiones** y luego usando la conexión existente o usando una nueva credencial seleccionando **Agregar nueva conexión**.

10. Después de arreglar la conexión para conectarse a Common Data Service:
     1. Seleccione **IfRequestState ==**
     2. Seleccione **Conexiones** para especificar la conexión para conectarse a Common Data Service 
     3. Seleccione **Conexiones** para especificar las credenciales de la cuenta de usuario que tiene una cuenta habilitada para buzón para enviar correos electrónicos

    > [!div class="mx-imgBorder"] 
    > ![Especificar credenciales de Outlook](media/deploy-fix-cred3.png "Especificar credenciales de Outlook")

11. En **Enviar un correo electrónico**, asegúrese de corregir la URL según la URL de su portal. Por ejemplo, en este caso, cambie rer6 a su valor de URL.

    > [!div class="mx-imgBorder"] 
    > ![Especificar credenciales de Outlook](media/deploy-fix-cred4.png "Especificar credenciales de Outlook")

12. Seleccione **Guardar** para guardar los cambios y seleccione **Encender**.

## <a name="step-15-share-admin-app-with-other-admin-users"></a>Paso 15: Comparta la aplicación de administración con otros usuarios de administración

Para que los usuarios administradores empresariales usen la aplicación de administración (aplicación controlada por modelos) para introducir y administrar datos, debe compartirse con ellos. Es más fácil usar grupos de Azure AD para compartir fácilmente aplicaciones con un grupo de usuarios administradores.

> [!IMPORTANT]
> Asegúrese de que el usuario o grupo con el que planea compartir la aplicación ya tiene acceso a su entorno. Por lo general, ya habría agregado usuarios o grupos al configurar su entorno. Alternativamente, puede seguir los pasos aquí para agregar usuarios a su entorno y proporcionar el acceso adecuado antes de compartir la aplicación con ellos: [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  En el panel de navegación izquierdo, seleccione **Aplicaciones**, seleccione la aplicación basada en modelos (**Aplicación de administración: aplicación de respuesta de emergencia regional**) y seleccione **Compartir** en el banner.

    > [!div class="mx-imgBorder"] 
    > ![Compartir una aplicación de administración](media/deploy-share-admin-app.png "Compartir una aplicación de administración")

3.  Especifique el grupo de Azure AD o los usuarios administradores con los que desea compartir esta aplicación, asigne el rol de seguridad **Regional Emergency Response Admin** (Administrador regional de respuesta ante emergencias) y seleccione **Compartir**.

    > [!div class="mx-imgBorder"] 
    > ![Especificar grupo o usuarios administradores de Azure AD](media/deploy-specify-share.png "Especificar grupo o usuarios administradores de Azure AD")

## <a name="next-steps"></a>Pasos siguientes

Los pasos de implementación ya están completos. Los administradores de empresas pueden consultar el tema [configuración](configure.md) para realizar los siguientes pasos:

-  Configurar y gestionar los datos maestros

-   Cree usuarios de portal para invitar a usuarios administradores de hospitales individuales para que puedan usar portales para agregar y administrar datos y usuarios.

- Ver el panel Power BI en su inquilino.

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-issues>.

- Para comentar la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-feedback>.
