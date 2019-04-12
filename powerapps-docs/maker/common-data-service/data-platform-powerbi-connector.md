---
title: Crear un informe de PowerBI | Microsoft Docs
description: Conectarse a sus datos desde PowerBI Desktop usando el conector de Common Data Service.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-power-bi-report"></a>Cree un informe de Power BI
Common Data Service le permite conectarse directamente a sus datos usando Power BI Desktop para crear informes y publicarlos en Power BI. Desde Power BI, los informes se pueden usar en paneles, se pueden compartir con otros usuarios y se puede acceder a ellos desde varias plataformas en las aplicaciones móviles de Power BI.

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>Requisitos previos

Para usar Power BI con Common Data Service, necesita lo siguiente:

* Descargar e instalar Power BI Desktop, que es una aplicación gratuita que se ejecuta en su ordenador local. Puede descargar Power BI Desktop [aquí](https://powerbi.microsoft.com/desktop/).
* Un entorno de Common Data Service con permisos de creador para acceder al portal y permisos de lectura para acceder a los datos de las entidades.

## <a name="finding-your-common-data-service-environment-url"></a>Buscar la dirección URL de su entorno de Common Data Service

1. Abra [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione el entorno al que se va a conectar, haga clic en **engranaje de configuración** en la esquina superior derecha y haga clic en **Personalizaciones avanzadas**

    ![Entorno de Common Data Service](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "Entorno de Common Data Service")

2. Haga clic en **Recursos** en la sección de recursos para desarrolladores, que se abrirá una nueva pestaña.

    ![Entorno de Common Data Service](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "Entorno de Common Data Service")

3. Copie la raíz de la dirección URL en la nueva pestaña, ésta es la dirección URL única para el entorno. La dirección URL tendrá el formato **https://yourenvironmentid.crm.dynamics.com/**, asegúrese de no copiar el resto de la dirección URL. Téngala a mano para que pueda usarla cuando cree su informe de PowerBI.

    > [!div class="mx-imgBorder"] 
    > ![Entorno de Common Data Service](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "Entorno de Common Data Service")

## <a name="connecting-to-common-data-service-from-power-bi-desktop"></a>Conectarse a Common Data Service desde Power BI Desktop

1. Inicie **Power BI Desktop**. Si es la primera vez, se le presentará una pantalla de bienvenida o se le redirigirá directamente a un lienzo en blanco. En cualquier caso, haga clic en **Obtener datos** y seleccione **Más** para abrir la lista completa de orígenes de datos disponibles para Power BI Desktop.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. Haga clic en **Servicios en línea** y en **Common Data Service (Beta)** de la lista de conectores. Haga clic en **Conectar**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. Pegue la **Dirección URL de entorno de Common Data Service** en el campo **Dirección URL del servidor** y haga clic en **Aceptar**. Si ésta es la primera vez, se le pedirá que inicie sesión usando las mismas credenciales que usa para conectarse a PowerApps y a Common Data Service.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. El explorador mostrará todas las entidades disponible para su entorno agrupadas en tres carpetas. Amplíe la carpeta **Modelo común de datos**.

    * Modelo común de datos: son las entidades estándar que se suelen usar y que están disponibles en todos los entornos como parte del modelo común de datos.
    * Entidades personalizadas: son las entidades que ha creado o importado en el entorno.
    * Sistema: contiene todas las entidades de su entorno, incluido el modelo común de datos y las entidades personalizadas.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. Seleccione la entidad **Cuenta** para obtener una vista previa de los datos en el panel derecho y haga clic en **Cargar**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. La entidad ahora se carga en el informe y puede empezar a crear informes o puede repetir este proceso para agregar entidades adicionales.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. Haga clic en el campo **Nombre** en panel Campo para agregar una nueva visualización al lienzo de informes. Ahora puede repetir este proceso y cambiar las visualizaciones para crear el informe.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>Uso de conjuntos de opciones

Los conjuntos de opciones se usan en entidades para ofrecer una lista desplegable de valores a un usuario en aplicaciones y flujos. Cuando se usa el conector de Power BI, los campos del conjunto de opciones se presentarán como dos columnas para mostrar tanto el valor único como el valor de visualización.

Como ejemplo, si tuviera un conjunto de opciones en la entidad llamado ApprovalStatus, vería dos campos en Power BI:

* ApprovalStatus: mostrará un valor entero único para cada elemento del conjunto de opciones, esto resulta útil al aplicar filtros, de modo que no se verá afectado si realiza cambios futuros en el nombre para mostrar.
* ApprovalStatus_display: mostrará el nombre para mostrar fácil de usar del elemento y se usa con mayor frecuencia al mostrar la opción en una tabla o un gráfico.

    |ApprovalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|Enviado
    2|En revisión
    3|Aprobado
    4|Rechazado

## <a name="navigating-relationships"></a>Navegar por las relaciones

Para las relaciones de Common Data Service es necesario que cree una relación en PowerBI Desktop entre las dos entidades usando un campo GUID, que es un identificador único generado por el sistema que garantiza que las relaciones se crean para los registros creados en los que puede haber ambigüedad o duplicación con otros campos. Puede leer más acerca de la administración de relaciones en Power BI Desktop [aquí](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships).

Mientras algunas relaciones pueden crearse automáticamente, puede revisar y asegurarse de que se han establecido las relaciones correctas al crear el informe:

* El campo de búsqueda en la entidad incluirá el GUID del registro en la entidad relacionada.
* La entidad relacionada tendrá un campo con el formato “[EntityNameid]id”, que contiene el GUID, como Accountid o MyCustomEntityid
* Con la función de administración de relaciones de PowerBI Desktop, crearía una nueva relación entre el campo de búsqueda y el campo de id. en la entidad relacionada.


## <a name="next-steps"></a>Pasos siguientes
* [Administrar campos de una entidad](data-platform-manage-fields.md)
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)


