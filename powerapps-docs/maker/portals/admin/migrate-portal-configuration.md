---
title: Migrar la configuración del portal | MicrosoftDocs
description: Aprenda a migrar la configuración del portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 80f9cc89b0da2eec5d134f282507e68658e42a96
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "2816403"
---
# <a name="migrate-portal-configuration"></a>Migrar la configuración del portal

El desarrollo del portal implica varias configuraciones y personalizaciones para lograr una experiencia deseada para los usuarios finales del portal.

Después de completar el desarrollo o la configuración de su instancia del portal es posible que desee migrar los datos más recientes de configuración del portal del entorno de desarrollo al de prueba o al de producción. La migración implica la exportación de los datos de configuración existentes desde el entorno de Common Data Service de origen y, a continuación, importarlos en el entorno de Common Data Service de destino.

Para exportar datos de instalación, deberá usar la herramienta Migración de la configuración y un archivo de esquema de configuración específico del portal. Para obtener más información acerca de esta herramienta, consulte [Administrar datos de configuración](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data).

> [!NOTE]
> - Se recomienda usar la versión más reciente de la herramienta Migración de la configuración. La herramienta Migración de la configuración se puede descargar de NuGet. Más información para descargar la herramienta: [Descargar herramientas de NuGet](https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget).
> - La versión mínima de la solución de portales que admiten los archivos de esquema para la migración de la configuración es 8.4.0.275. Sin embargo, se recomienda que use la versión más reciente de la solución.

Los archivos de esquema están disponibles para los tipos de portal siguientes:

- **Portales creados en un entorno con Common Data Service**
    - [Portal personalizado (portal vacío)](https://go.microsoft.com/fwlink/p/?linkid=2110477)

- **Portales creados en un entorno que contiene aplicaciones basadas en modelo en Dynamics 365**
    - [Portal personalizado (portal vacío)](https://go.microsoft.com/fwlink/p/?linkid=2019804)
    - [Portal de la comunidad](https://go.microsoft.com/fwlink/p/?linkid=2019704)
    - [Portal de autoservicio de clientes](https://go.microsoft.com/fwlink/p/?linkid=2019705)
    - [Portal de asociados](https://go.microsoft.com/fwlink/p/?linkid=2019803)
    - [Portal de autoservicio de empleados](https://go.microsoft.com/fwlink/p/?linkid=2019802)

El archivo de esquema predeterminado contiene información sobre las entidades, relaciones y definiciones de la exclusividad del portal para cada entidad. Más información: [Exportar datos de configuración del portal](#export-portal-configuration-data)

Después de exportar los datos de configuración, debe importarlos en el entorno de destino. Más información: [Importar datos de configuración del portal](#import-portal-configuration-data)

> [!NOTE]
> Los archivos de esquema se proporcionan para reducir el esfuerzo necesario para crear un esquema desde cero. El esquema se puede adaptar para implementación mediante los métodos estándar que proporciona la herramienta. Los archivos de esquema se pueden cargar en la herramienta Migración de la configuración y modificar para agregar, quitar y modificar entidades, atributos, etc.

## <a name="export-portal-configuration-data"></a>Exportar datos de configuración del portal

Puede exportar los datos de configuración del portal desde un sistema de origen utilizando archivos predeterminados de esquema de configuración específicos del portal.

1.  Descargue la herramienta Migración de la configuración y extráigala en la carpeta deseada.

2.  Descargue un archivo de esquema de configuración del portal con los vínculos proporcionados anteriormente para el tipo de portal.

3.  Haga doble clic en el archivo de **DataMigrationUtility.exe** en la carpeta `<your_folder>\Tools\ConfigurationMigration` para ejecutar la herramienta Migración de la configuración, elija **Exportar datos** en la pantalla principal y luego seleccione **Continuar**.
    
    > [!div class=mx-imgBorder]
    > ![Exportar datos de configuración](../media/export-config-data.png "Exportar datos de configuración")

4.  En la pantalla **Iniciar sesión**, proporcione los detalles de autenticación para conectarse al entorno de Common Data Service desde donde desea exportar los datos. Si tiene varias organizaciones en el entorno de Common Data Service desde donde exportar los datos, active la casilla **Mostrar la lista de organizaciones disponibles** y después seleccione **Iniciar sesión**.

    > [!div class=mx-imgBorder]
    > ![Proporcionar detalles de autenticación para conectarse al entorno de Common Data Service desde donde desea exportar datos](../media/export-config-login.png "Proporcionar detalles de autenticación para conectarse al entorno de Common Data Service desde donde desea exportar datos")

5.  Si tiene varias organizaciones y había activado la casilla **Mostrar la lista de organizaciones disponibles** en el paso anterior, la próxima pantalla le permitirá elegir la organización con la que desea conectarse. Seleccione un entorno de Common Data Service para conectarse. 

    > [!NOTE]
    > Si no tiene varias organizaciones, no se muestra esta pantalla.

6.  En **Archivo de esquema**, busque y seleccione el archivo de esquema de configuración específico del portal que se usará para exportación de datos.

7.  En **Guardar en archivo de datos**, especifique el nombre y la ubicación de archivo de datos que desea exportar.

    > [!div class=mx-imgBorder]
    > ![Especifique los archivos de esquema y de destino](../media/export-config-file-name.png "Especifique los archivos de esquema y de destino")

8.  Seleccione **Exportar datos**. La pantalla muestra el estado de progreso de la exportación y la ubicación del archivo exportado en la parte inferior de la pantalla una vez terminada la exportación.

    > [!div class=mx-imgBorder]
    > ![Progreso de la exportación de datos de configuración](../media/export-config-status.png "Progreso de la exportación de datos de configuración")

    > [!IMPORTANT]
    > La herramienta Configuration Migration no admite el filtrado de registros en una entidad. De forma predeterminada, se exportarán todos los registros de la entidad seleccionada. Por tanto, si ha creado más de un registro de sitio web, todos los registros de sitio web se exportarán.

9.  Seleccione **Salir** para cerrar la herramienta.

## <a name="import-portal-configuration-data"></a>Importar datos de configuración del portal

1.  Ejecute la herramienta Migración de la configuración y seleccione **Importar datos** en la pantalla principal y, a continuación seleccione **Continuar**.

    > [!div class=mx-imgBorder]
    > ![Importe datos de configuración](../media/import-config-data.png "Importe datos de configuración")

2.  En la pantalla **Iniciar sesión**, proporcione los detalles de autenticación para conectarse al entorno de Common Data Service desde donde desea exportar los datos. Si tiene varias organizaciones en el entorno de Common Data Service desde donde exportar los datos, active la casilla **Mostrar la lista de organizaciones disponibles** y después seleccione **Iniciar sesión**.

3.  Si tiene varias organizaciones y había activado la casilla **Mostrar la lista de organizaciones disponibles** en el paso anterior, la próxima pantalla le permitirá elegir la organización con la que desea conectarse. Seleccione un entorno de Common Data Service para conectarse. 

    > [!NOTE]
    > - Si no tiene varias organizaciones, no se muestra esta pantalla.
    > - Asegúrese de que la solución de portal ya está instalada para la organización donde tenga previsto importar las configuraciones.

4.  La siguiente pantalla le pide que facilite el archivo de datos (.zip) que se importa. Busque el archivo de datos, selecciónelo y, a continuación, seleccione **Importar datos**. 

    > [!div class=mx-imgBorder]
    > ![Progreso de la importación de datos de configuración](../media/import-config-status.png "Progreso de la importación de datos de configuración")

5.  La pantalla siguiente muestra el estado de importación de sus registros. La importación de datos se realiza en múltiples pasos para importar primero los datos de base mientras se sitúan en cola los datos dependientes, y después se importan los datos dependientes en las pasadas posteriores para administrar las vinculaciones o dependencias de datos. Esto asegura una importación limpia y coherente de los datos. 

6.  Seleccione **Salir** para cerrar la herramienta. 
