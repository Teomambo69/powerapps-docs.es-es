---
title: Usar la aplicación de administración y el panel de la solución de supervisión y respuesta de emergencia de la administración pública regional | Documentos de Microsoft
description: Proporciona instrucciones detalladas para los administradores de empresas de organizaciones regionales para configurar datos maestros, administrar usuarios del portal y ver paneles para obtener información clave.
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
ms.openlocfilehash: 7797e66766d68117cc88b151e8faa14e660ec7d4
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342131"
---
# <a name="use-the-admin-app-and-dashboard"></a>Uso de la aplicación y panel de administración

Este artículo está destinado a que los administradores de empresas de organizaciones médicas regionales utilicen la aplicación de administración (aplicación basada en modelos) para realizar las siguientes actividades:

-   Agregar y administrar datos maestros en entidades requeridas para la solución

-   Creación y administración de usuarios del portal (contactos). Estos usuarios suelen ser administradores de organizaciones médicas primarias que administran uno o más sistemas hospitalarios.

- Ver aprobar y rechazar las solicitudes de los usuarios del portal.

- Ver los paneles Power BI en su inquilino.

## <a name="prerequisites"></a>Requisitos previos

-   Asegúrese de tener el rol de seguridad apropiado y acceso a la aplicación de administración (aplicación basada en modelos). Póngase en contacto con su administrador de TI si no puede acceder o usar la aplicación de administración.

-   Asegúrese de tener acceso a los datos de ejemplo. Los datos de ejemplo están disponibles en el paquete de implementación en la carpeta **SampleData**.

## <a name="add-and-manage-master-data"></a>Agregar y administrar datos maestros

Cuando inicie sesión en la aplicación de administración (basada en modelos), verá las entidades en el panel izquierdo donde debe completar los datos maestros. Seleccione la entidad en el panel de navegación izquierdo para ver o administrar los datos.

> [!div class="mx-imgBorder"] 
> ![Relleno de los datos maestros](media/config-entities-master-data.png "Relleno de los datos maestros")

-   **Área de jerarquía**: los datos para entidades en esta área se pueden agregar importando datos de los archivos de datos de muestra o manualmente. Las entidades bajo el área **Jerarquía** se enumeran en el orden en que debe completar los datos. Además, los administradores de la organización principal (administradores del hospital) pueden ver y administrar datos en las siguientes entidades para su hospital desde el portal: **Sistemas**, **Regiones** e **Instalaciones**.

-   **Área de entidades administrativas**: los datos en la entidad **Suministros** se agregan al importar datos del archivo de datos de ejemplo. Puede agregar y administrar manualmente los datos de suministros más adelante.

-   **Área de clientes**: usa **Usuarios del portal** para [gestionar usuarios del portal](#manage-portal-users) y **Solicitudes de usuario** para [gestionar solicitudes de usuarios del portal](#manage-portal-user-requests).

-   **Área de recursos**: seleccione **Documentación** para ver este documento.

Hay dos formas de agregar datos maestros a entidades en la aplicación:

-  Importación de datos usando los archivos de datos de ejemplo.

-  Configurar y gestionar manualmente los datos.

### <a name="import-data-using-sample-files"></a>Importar datos usando archivos de ejemplo

Los archivos de datos de ejemplo están disponibles en el paquete de implementación (.zip). Cuando extrae el archivo .zip, los archivos de datos de ejemplo están disponibles en la carpeta **SampleData**.

En la carpeta **SampleData**, los nombres de los archivos sirven para indicar la secuencia en la que los datos se deben importar en la aplicación. De lo contrario, la importación de datos fallará.

-   0_Supplies.xlsx

-   1_Counties.xlsx

-   2_Regional Organization.xlsx

-   3_Parent Organizations.xlsx

-   4_Systems.xlsx

-   5_Regions.xlsx

-   6_Facilities.xlsx

> [!NOTE]
> Proporcionamos el nombre y el código FIPS para todos los condados del estado de Washington como datos de ejemplo que puede importar. Debes importar los datos **Condados** utilizando el archivo de datos de ejemplo en su sistema antes de proceder a importar o administrar datos en cualquier otra entidad.
> 
> Para obtener datos sobre condados en otros estados, visite <https://www.census.gov/geographies/reference-files/2018/demo/popest/2018-fips.html>

#### <a name="how-to-load-data-from-data-files"></a>Cómo cargar datos de archivos de datos

Para cargar datos de ejemplo del archivo Excel a una entidad: 

1.  En el panel de navegación izquierdo de la aplicación de administración, seleccione seleccionar una entidad.Por ejemplo, seleccione **Org primaria**. 

2.  Seleccione **Importar desde Excel** para seleccionar el archivo de datos. 

       > [!div class="mx-imgBorder"] 
       > ![Importar desde Excel](media/config-import-excel.png "Importar desde Excel")

3.  Navegue hasta la carpeta **SampleData** y seleccione el archivo **3__Parent Organizations.xlsx** y continúe con los pasos del asistente para importar los datos.  

4.  Una vez importados los datos de ejemplo, verá los registros importados en la entidad:

       > [!div class="mx-imgBorder"] 
       > ![Registros importados en entidad](media/config-imported-records.png "Registros importados en entidad")

### <a name="manually-configure-and-manage-master-data-for-your-organization"></a>Configurar manualmente y administrar los datos maestros para su organización

Los administradores pueden usar la aplicación basada en modelos en [Power Apps](https://make.powerapps.com) para crear y administrar datos maestros para su organización. Estos datos son necesarios para que funcione la solución de respuesta ante emergencias.

Para empezar, debe agregar datos maestros en las entidades siguientes:

-   [Suministros](#supplies-and-counties-data)

-   [Provincias](#supplies-and-counties-data)

-   [Organización regional](#regional-org-data)

-   [Organización principal](#parent-org-data)

-   [Sistemas hospitalarios](#systems-data) administrado por cada organización primaria

-   [Regiones](#regions-data) para cada sistema hospitalario

-   [Instalaciones](#facilities-data) dentro de cada región de un sistema hospitalario

Inicie sesión en la aplicación de administración utilizando la URL proporcionada por su administrador de TI para agregar y administrar datos.

#### <a name="supplies-and-counties-data"></a>Datos de suministros y condados

Use los archivos de datos de ejemplo (**0_Supplies.xlsx** y **1_Counties.xlsx**) en el paquete de implementación para importar datos para las entidades **Suministros** y **Condados**.

#### <a name="regional-org-data"></a>Datos de organización regional

Esta es la organización de red regional que implementará la solución y administrará los datos de varias organizaciones principales.

Para crear un registro:

1.  En el panel izquierdo, seleccione **Organización regional** y seleccione **Nuevo**:

    > [!div class="mx-imgBorder"] 
    > ![Datos de la organización regional](media/config-region-org.png "Datos de la organización regional")

2.  En la página **Nueva organización regional**, especifique el nombre de la organización:

    > [!div class="mx-imgBorder"] 
    > ![Nueva organización regional](media/config-new-region-org.png "Nueva organización regional")

3.  Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Organización regional**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

#### <a name="parent-org-data"></a>Datos de la organización primaria

La entidad **Organización primaria** almacena la organización primaria que utilizará los portales establecidos por la organización regional para ver y administrar los datos relacionados con los sistemas hospitalarios de la organización primaria.

Para crear un registro:

1.  En el panel izquierdo, seleccione **Organización primaria** y seleccione **Nuevo**:

2.  En la página **Nueva organización primaria**, especifique los valores adecuados:

     > [!div class="mx-imgBorder"] 
     > ![Nueva organización primaria](media/config-new-parent-org.png "Nueva organización primaria")

    | **Campo**                |**Descripción** |
    |--------------------------|------------------------------------------------------|
    | Organización regional    | Seleccione una organización regional. Esta lista se completa en función de los datos de **Organización regional** que ha creado anteriormente. |
    | Nombre de la organización principal | Especifique el nombre de la organización primaria.      |
    | Descripción              | Escriba una descripción opcional.        |
    | Fecha de datos efectiva     | Escriba la fecha y hora de inicio de esta organización primaria.    |
    | Fecha de finalización efectiva       | Escriba la fecha y hora de final de esta organización primaria.         |

3.  Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Organización primaria**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

#### <a name="systems-data"></a>Datos del sistema

La entidad **Sistemas** le permite crear y administrar entradas para Hospital Systems. Puede administrar varios sistemas hospitalarios dentro de la misma organización primaria.

Para crear un registro:

1.  Seleccione **Sistemas** en el panel izquierdo y seleccione **Nuevo**.

2.  En la página **Sistema nuevo**, especifique los valores apropiados:

    > [!div class="mx-imgBorder"] 
    > ![Crear sistemas de datos](media/config-system-data.png "Crear sistemas de datos")

    | **Campo**           | **Descripción**        |
    |---------------------|---------------------------------------|
    | Nombre del sistema         | Escriba un nombre para su Hospital.    |
    | Organización principal | Seleccione una organización principal a la que asociar. Esta lista se rellena en función de los datos de **Organización primaria** que ha creado anteriormente. |
    | Descripción         | Escriba una descripción opcional.    |

3.  Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Sistemas**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

#### <a name="regions-data"></a>Datos de regiones

La entidad **Regiones** le permite administrar las regiones geográficas de sus sistemas hospitalarios.

Para crear un registro:

1.  Seleccione **Regiones** en el panel izquierdo y seleccione **Nuevo**.

2.  En la página **Región nueva**, especifique los valores apropiados:

    > [!div class="mx-imgBorder"] 
    > ![Crear región nueva](media/config-create-region.png "Crear región nueva")

    | **Campo**   | **Descripción**                                  |
    |-------------|---------------------------|
    | Sistema      | Seleccione un sistema hospitalario al que esté asociado esta región. Esta lista se llena en función de los datos de **Sistemas** que ha creado anteriormente. |
    | Nombre de región | Escriba el nombre de la región. Por ejemplo, Seattle.  |
    | Descripción | Escriba una descripción opcional. 

3.  Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Regiones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

### <a name="facilities-data"></a>Datos de instalaciones

La entidad **Instalaciones** le permite administrar las ubicaciones de los hospitales dentro de cada región. Por ejemplo, las instalaciones **Redmond** y **Bellevue** dentro de la región **Seattle**.

Para crear un registro:

1.  Seleccione **Instalaciones** en el panel izquierdo y seleccione **Nuevo**.

2.  En la página **Instalaciones nuevas**, especifique los valores apropiados:

    > [!div class="mx-imgBorder"] 
    > ![Creación de una nueva instalación](media/config-new-facility.png "Creación de una nueva instalación")

    | **Campo**                    | **Descripción**            |
    |------------------------------|---------------------------------------------------|
    | Región    | Seleccione una región a la que esté asociada esta instalación. Esta lista se llena en función de los datos de **Regiones** que ha creado anteriormente.          |
    | Nombre de las instalaciones | Escriba el nombre de las instalaciones.                 |
    | Número de DOH    | Escriba el número del Departamento de Salud para esta instalación.     |
    | Sigue el protocolo droplet     | Indica si la instalación sigue las Precauciones Droplet para pacientes que se sabe o se sospecha que están infectados con patógenos transmitidos por gotas respiratorias, como en los casos COVID-19. Seleccione **Sí** o **No**. |
    | Descripción    | Escriba una descripción opcional.              |
    | Fecha de datos efectiva         | Escriba la fecha y hora de inicio de estas instalaciones.    |
    | Capacidad de camas autorizadas    | Escriba la capacidad total de camas con licencia.    |
    | Capacidad de cuidados intensivos SAITA     | Escriba el número total de camas de cuidados agudos en AIIR (Airborne Infection Isolation Room).     |
    | Capacidad de UCI SAITA            | Escriba el número total de camas UCI en AIIR.       |
    | Respiradores totales       | Escriba el número total de respiradores en la instalación.   |
    | Fecha de finalización efectiva           | Escriba la fecha y hora de finalización de estas instalaciones.       |
    | Capacidad de camas suplementarias           | Escriba el número de camas supletorias que puede tener la instalación. Las camas supletorias son aquellas que pueden tener personal por encima y más allá de la capacidad de cama con licencia si los pacientes necesitan ser admitidos.                                              |
    | Capacidad de cuidados intensivos no SAITA | Escriba el número total de camas de cuidados agudos en no AIIR (Airborne Infection Isolation Room).|
    | Capacidad de UCI no SAITA        | Escriba el número total de camas UCI en no AIIR.              |
    |Capacidad mortuoria total       | Escriba la capacidad mortuoria total de la instalación.|
    | Dirección del centro    | Escriba la calle, ciudad, condado, estado, código postal, latitud y longitud de la instalación.   |

3.  Seleccione **Guardar y cerrar**. El registro recién creado estará disponible en la lista **Instalaciones**.

Para editar el registro, seleccione el registro, actualice los valores según sea necesario y seleccione **Guardar y cerrar**.

También puede ver y administrar los datos asociados al **Censo**, **COVID**, **Equipo**, **Dotación de personal** y **Suministros** introducidos por las organizaciones primarias para una instalación abriendo un registro de la instalación y utilizando las pestañas respectivas en el registro.

> [!div class="mx-imgBorder"] 
> ![Abrir un registro de instalación](media/config-facility-record.png "Abrir un registro de instalación")

## <a name="manage-portal-users"></a>Administrar usuarios de portal

Use la entidad **Usuarios del portal** para agregar y administrar usuarios del portal. Estos usuarios del portal son los administradores de las diversas organizaciones primarias que informan los datos de sus sistemas hospitalarios a las organizaciones regionales y también administran a otros administradores, trabajadores de la salud o espectadores de informes que utilizan los portales.

### <a name="create-a-portal-user"></a>Creación de un usuario del portal

1.  Inicie sesión en la aplicación de administración utilizando la URL proporcionada por su administrador de TI.

2.  En el panel de navegación izquierdo, seleccione **Usuarios del portal**. Verá una lista de usuarios del portal, si ya han sido agregados por otros administradores en su organización. Al seleccionar un usuario, se abrirán los detalles sobre el usuario.

3.  Seleccione **Nuevo** para crear un usuario del portal nuevo. En la página **Nuevo contacto**, especifique los valores adecuados

    > [!div class="mx-imgBorder"] 
    > ![Creación de un usuario del portal](media/config-portal-user.png "Creación de un usuario del portal")

    | **Campo**           | **Descripción**  |
    |---------------------|-------------------|
    | Nombre          | Nombre de pila del usuario.                           |
    | Apellidos           | Apellidos del usuario  |
    | Enviar por correo electrónico     | Correo electrónico del usuario donde se enviará la invitación.    |
    | Organización principal | Seleccione una organización primaria con la que este usuario del portal estará asociado. Esto garantiza que el usuario tenga acceso solo a los datos de los sistemas del hospital en la organización primaria seleccionada. Si no especifica una organización primaria para el usuario, tendrá acceso a los datos de todas las organizaciones principales en la organización regional. |
    | Sistema hospitalario     | Seleccione un hospital con el que este usuario del portal estará asociado. |
    | Región  | Seleccione una región con la que este usuario del portal estará asociado.  |
    | Instalaciones            | Seleccione unas instalaciones con las que este usuario del portal estará asociado. |

4.  Guarde el registro. Al guardar el registro, el área **Roles web** queda disponible. Seleccione **Agregar rol web existente**.

5.  En la página de registros de búsqueda, presione Entrar para mostrar los roles web existentes.

    > [!div class="mx-imgBorder"] 
    > ![Seleccione un rol](media/config-select-portal-role.png "Seleccione un rol")

6. Seleccione los roles según el acceso al portal que debe proporcionar al usuario. Para dar acceso a todas las funciones del portal, seleccione los tres roles: **Trabajador de organización sanitaria**, **Administrador de organización primaria** y **Visor de informes**.

    Para obtener información sobre el acceso al portal que proporciona cada uno de estos roles, consulte la sección [Crear usuario](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#create-user) en el tema de administración del portal.

    Para otorgar un rol, seleccione el rol y seleccione **Agregar**.

7. Guarde el registro de usuario del portal.

Dependiendo del rol (o roles) que le haya otorgado al usuario, este verá las áreas respectivas en el portal. Más información: [Portal para administradores y visores de informes](portals-admin-reporting.md) y [Portal para trabajadores sanitarios](portals-user.md)

Se enviará un correo electrónico automáticamente al usuario recién creado con un código de invitación para unirse a los portales. El usuario del portal puede canjear la invitación para iniciar sesión y comenzar a usar el portal. Más información: [Empezar en el portal](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#getting-started-with-the-portal)

## <a name="manage-portal-user-requests"></a>Administrar solicitudes de usuario del portal

Puede ver, aprobar y rechazar las solicitudes de los usuarios del portal utilizando la opción **Solicitudes de usuario**.

Use la vista adecuada para ver una lista de solicitudes de usuario aprobadas, rechazadas, inactivas y pendientes.

> [!div class="mx-imgBorder"] 
> ![Seleccionar vista](media/configure-portal-request-views.png "Seleccionar vista")

### <a name="approve-or-decline-user-request"></a>Aprobar o rechazar solicitudes de usuario

Para aprobar o rechazar solicitudes de usuario:

1.  Inicie sesión en la aplicación de administración utilizando la URL proporcionada por su administrador de TI.

2.  En el panel izquierdo, seleccione **Solicitudes de usuario**y luego seleccione la vista **Solicitudes de usuario del portal pendientes**. Verá una lista de solicitudes de usuarios del portal pendientes de aprobación.

3.  Haga doble clic en una solicitud de usuario para abrirla.

4.  En el formulario solicitud de usuario:

    1. Seleccione los roles apropiados para el usuario en la zona **Elegir roles para el usuario**. Para otorgar o denegar un rol, seleccione **Sí** o **No** respectivamente para cada rol.

    1. Desde la lista **Estado de solicitud**, seleccione **Aprobar** o **Rechazar**.

    1. Seleccione el icono guardar en la esquina inferior derecha.

        > [!div class="mx-imgBorder"] 
        > ![Aprobación o rechazo de una solicitud de usuario](media/user-request-manage.png "Aprobación o rechazo de una solicitud de usuario")

Basado en la aprobación o rechazo, sucede lo siguiente:

- Si *aprueba* la solicitud de acceso, el registro de usuario se crea con los roles seleccionados y el usuario recibe un correo electrónico con un código de invitación. El usuario del puede canjear el código de invitación para iniciar sesión en el portal. Más información: [Canjear invitación](portals-admin-reporting.md#redeem-invitation)

- Si *rechaza* la solicitud de acceso, el registro de usuario no se crea y el usuario recibe un correo electrónico informándole de que la solicitud se ha rechazado.

## <a name="view-the-power-bi-dashboard"></a>Ver el panel de Power BI

Los administradores de empresas de la organización regional pueden ver el panel Power BI en su inquilino de Power BI si el administrador regional de TI publicó el informe como una aplicación y le otorgó acceso a administradores comerciales. Más información: [Paso 5: configurar y publicar el panel Power BI](deploy.md#step-5-configure-and-publish-power-bi-dashboard) 

Para ver el panel de Power BI:

1. Inicie sesión en [Power BI](https://app.powerbi.com).

2. El espacio de trabajo donde se publicó la aplicación estará disponible para que pueda acceder al panel.

3. El panel de Power BI que está disponible para usted en su inquilino de Power BI es el mismo que el disponible para los usuarios del portal. La **diferencia principal** es que, como administrador comercial de una organización regional, puede ver los datos de todas las organizaciones primarias que informan a la organización regional, mientras que los usuarios que ven el panel integrado en el portal solo pueden ver los datos de su organización primaria y los sistemas hospitalarios asociados.

Para información detallada presentada en el panel de Power BI, vea [Obtenga ideas](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights) en el tema del portal.

## <a name="issues-and-feedback"></a>Problemas y comentarios

- Para informar un problema con la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-issues>.

- Para comentar la solución de seguimiento y respuesta de emergencia de la administración pública regional, visite <https://aka.ms/rer-feedback>.

