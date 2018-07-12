---
title: Creación de un informe de Power BI | Microsoft Docs
description: Conectarse a los datos de Power BI Desktop con el conector de Common Data Service for Apps.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: bb0bec7cf459eb9084aea4db7264350b7913e578
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37898774"
---
# <a name="create-a-power-bi-report"></a>Crear un informe de Power BI
Common Data Service for Apps le permite conectarse directamente a los datos mediante Power BI Desktop para crear informes y publicarlos en Power BI. Desde Power BI, se puede usar los informes en los paneles, compartirlos con otros usuarios y acceder a distintas plataformas de aplicaciones móviles de Power BI.

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>Requisitos previos

Para usar Power BI con Common Data Service for Apps, necesita lo siguiente:

* Descargar e instalar Power BI Desktop, que es una aplicación gratuita que se ejecuta en el equipo local. Puede descargar Power BI Desktop [aquí](https://powerbi.microsoft.com/desktop/).
* Entorno de Common Data Service for Apps con permisos de creador para acceder al portal y a los permisos de lectura para tener acceso a los datos dentro de las entidades.

## <a name="finding-your-common-data-service-for-apps-environment-url"></a>Buscar la dirección URL del entorno de Common Data Service for Apps

1. Abra [PowerApps](https://web.powerapps.com) y seleccione el entorno al que se va a conectar y haga clic en el **engranaje de configuración** en la esquina superior derecha y haga clic en **Personalizaciones avanzadas**.

    ![Entorno de CDS for Apps](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "Entorno de CDS for Apps")

2. Haga clic en **Recursos** en la sección de recursos para desarrolladores, lo que abrirá una nueva pestaña.

    ![Entorno de CDS for Apps](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "Entorno de CDS for Apps")

3. Copie la raíz de la dirección URL de la pestaña nueva, esta es la dirección URL única para su entorno. La dirección URL tendrá el formato **https://yourenvironmentid.crm.dynamics.com/**; asegúrese de que no copia el resto de la dirección URL. Téngala a mano para poder usarla al crear el informe de Power BI.

    ![Entorno de CDS for Apps](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "Entorno de CDS for Apps")

## <a name="connecting-to-common-data-service-for-apps-from-power-bi-desktop"></a>Conectarse a Common Data Service for Apps desde Power BI Desktop

1. Inicie **Power BI Desktop**, si es la primera vez, se le mostrará una pantalla de bienvenida o directamente un lienzo en blanco; en cualquier caso, haga clic en **Obtener datos** y seleccione **Más** para abrir la lista completa de los orígenes de datos disponibles para Power BI Desktop.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. Haga clic en **Online Services** y **Common Data Service for Apps (Beta)** en la lista de conectores. Haga clic en **Conectar**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. Pegue la **dirección URL del entorno de Common Data Service for Apps** en el campo **URL del servidor** y haga clic en **Aceptar**. Si se trata de la primera vez, se le pedirá que inicie sesión con las mismas credenciales que use para conectarse a PowerApps y Common Data Service for Apps.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. El explorador mostrará todas las entidades disponibles para su entorno agrupadas en tres carpetas. Expanda la carpeta **Common Data Model**.

   * Common Data Model: se trata de entidades estándares que normalmente están disponibles y se usan en todos los entornos como parte de Common Data Model.
   * Entidades personalizadas: son entidades que ha creado o importado en su entorno.
   * Sistema: contiene todas las entidades en su entorno, incluidas las entidades personalizadas y de Common Data Model.

     ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. Seleccione la entidad **Cuenta** para obtener una vista previa de los datos en el panel derecho y haga clic en **Cargar**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. La entidad se carga entonces en el informe y puede empezar a crear informes, o bien repetir este proceso para agregar más entidades.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. Haga clic en el campo **Nombre** en el panel Campos para agregar una nueva visualización en el lienzo de informes. Ahora puede repetir este proceso y cambiar las visualizaciones para generar el informe.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>Uso de los conjuntos de opciones

Los conjuntos de opciones se usan en las entidades para proporcionar una lista desplegable de valores a un usuario en aplicaciones y flujos. Cuando se usa el conector de Power BI los campos de los conjuntos de opciones se presentarán en dos columnas para mostrar tanto el valor único como el valor para mostrar.

Por ejemplo, si tiene un conjunto de opciones en la entidad denominada ApprovalStatus, verá dos campos en Power BI:

* ApprovalStatus: mostrará un valor entero único para cada elemento en el conjunto de opciones, se trata de una ayuda al aplicar filtros para que no se vean afectados si realiza futuros cambios en el nombre para mostrar.
* ApprovalStatus_display: mostrará el nombre para mostrar descriptivo del elemento y se usa normalmente cuando se presenta la opción en una tabla o gráfico.

    |ApproalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|Enviado
    2|En revisión
    3|Approved
    4|Rechazado

## <a name="navigating-relationships"></a>Exploración de las relaciones

Las relaciones en Common Data Service for Apps requieren que cree una relación en Power BI Desktop entre las dos entidades mediante un campo GUID; se trata de un identificador único generado por el sistema que garantiza que las relaciones se crean para crear registros donde podría existir ambigüedad o duplicación con otros campos. Puede leer más sobre la administración de relaciones en Power BI Desktop [aquí](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships).

Aunque puede que algunas relaciones se creen automáticamente, puede revisar y asegurarse de que se establecen las relaciones correctas al crear el informe:

* El campo de búsqueda en la entidad contiene el GUID del registro en la entidad relacionada.
* La entidad relacionada tendrán un campo con el formato "[EntityName]id", que contiene el GUID; por ejemplo, Accountid o MyCustomEntityid
* Con la característica Administrar relaciones de Power BI Desktop, crearía una nueva relación entre el campo de búsqueda y el campo de identificador de la entidad relacionada.


## <a name="next-steps"></a>Pasos siguientes
* [Administrar campos de una entidad](data-platform-manage-fields.md)
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)


