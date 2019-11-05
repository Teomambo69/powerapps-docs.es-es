---
title: Migrar la configuración del portal | MicrosoftDocs
description: Obtenga información sobre cómo migrar la configuración del portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0aa057594b500c7019a4d645c70cafcfff183608
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543047"
---
# <a name="migrate-portal-configuration"></a>Migración de la configuración del portal

El desarrollo del portal implica varias configuraciones y personalizaciones para lograr una experiencia deseada para los usuarios finales del portal.

Una vez completado el desarrollo o la configuración de la instancia del portal, es posible que desee migrar la configuración del portal más reciente desde el desarrollo hasta el entorno de prueba o de producción. La migración implica la exportación de la configuración existente desde el entorno de Common Data Service de origen y, a continuación, su importación en el entorno de Common Data Service de destino.

Para exportar los datos de configuración, debe usar la herramienta de migración de configuración y un archivo de esquema de configuración específico del portal. Para obtener más información acerca de esta herramienta, vea [administrar datos de configuración](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data).

> [!NOTE]
> - Se recomienda usar la versión más reciente de la herramienta de migración de configuración. La herramienta de migración de configuración se puede descargar desde NuGet. Más información para descargar la herramienta: [Descargar herramientas de NuGet](https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget).
> - La versión de solución mínima de portales compatible con los archivos de esquema para la migración de configuración es 8.4.0.275. Sin embargo, se recomienda usar la versión más reciente de la solución.

Los archivos de esquema están disponibles para los siguientes tipos de portal:
- [Portal de la comunidad](https://go.microsoft.com/fwlink/p/?linkid=2019704)
- [Portal de autoservicio del cliente](https://go.microsoft.com/fwlink/p/?linkid=2019705)
- [Portal de Partners](https://go.microsoft.com/fwlink/p/?linkid=2019803)
- [Portal de autoservicio para empleados](https://go.microsoft.com/fwlink/p/?linkid=2019802)
- [Portal personalizado](https://go.microsoft.com/fwlink/p/?linkid=2019804)

Los archivos de esquema predeterminados contienen información sobre las entidades del portal, las relaciones y las definiciones de unicidad de cada entidad. Más información: [exportación de datos de configuración del portal](#export-portal-configuration-data)

Después de exportar los datos de configuración, debe importarlos en el entorno de destino. Más información: [importar datos de configuración del portal](#import-portal-configuration-data)

> [!NOTE]
> Los archivos de esquema se proporcionan para reducir el esfuerzo necesario para generar un esquema desde cero. El esquema se puede adaptar a su implementación mediante las maneras estándar que proporciona la herramienta. Los archivos de esquema se pueden cargar en la herramienta de migración de configuración y modificarse para agregar, quitar y modificar entidades, atributos, etc.

## <a name="export-portal-configuration-data"></a>Exportar datos de configuración del portal

Puede exportar los datos de configuración del portal desde un sistema de origen mediante archivos de esquema de configuración específicos del portal.

1.  Descargue la herramienta de migración de configuración y extráigalo en la carpeta que desee.

2.  Descargue un archivo de esquema de configuración del portal mediante los vínculos proporcionados anteriormente para el tipo de portal.

3.  Haga doble clic en el archivo **DataMigrationUtility. exe** de la carpeta `<your_folder>\Tools\ConfigurationMigration` para ejecutar la herramienta de migración de configuración, elija **exportar datos** en la pantalla principal y, a continuación, seleccione **continuar**.
    
    > [!div class=mx-imgBorder]
    > ![Exportar datos de configuración](../media/export-config-data.png "Exportar datos de configuración")

4.  En la pantalla de **Inicio de sesión** , proporcione los detalles de autenticación para conectarse a su entorno de Common Data Service desde donde desea exportar los datos. Si tiene varias organizaciones en el entorno de Common Data Service desde donde exportar los datos, active la casilla **Mostrar lista de organizaciones disponibles** y, a continuación, seleccione **Inicio de sesión**.

    > [!div class=mx-imgBorder]
    > ![Proporcione los detalles de autenticación para conectarse a su entorno de Common Data Service desde el que desea exportar los datos.](../media/export-config-login.png "Proporcione los detalles de autenticación para conectarse a su entorno de Common Data Service desde el que desea exportar los datos.")

5.  Si tiene varias organizaciones y ha seleccionado la casilla **Mostrar lista de organizaciones disponibles** en el paso anterior, la siguiente pantalla le permite elegir la organización a la que desea conectarse. Seleccione un entorno de Common Data Service al que conectarse. 

    > [!NOTE]
    > Si no tiene varias organizaciones, no se muestra esta pantalla.

6.  En **archivo de esquema**, busque y seleccione el archivo de esquema de configuración específico del portal que se usará para la exportación de datos.

7.  En **Guardar en archivo de datos**, especifique el nombre y la ubicación del archivo de datos que se va a exportar.

    > [!div class=mx-imgBorder]
    > ![Especificar archivos de esquema y de destino](../media/export-config-file-name.png "Especificar archivos de esquema y de destino")

8.  Seleccione **exportar datos**. La pantalla muestra el estado de progreso de la exportación y la ubicación del archivo exportado en la parte inferior de la pantalla una vez completada la exportación.

    > [!div class=mx-imgBorder]
    > ![Progreso de la exportación de datos de configuración](../media/export-config-status.png "Progreso de la exportación de datos de configuración")

    > [!IMPORTANT]
    > La herramienta de migración de configuración no admite el filtrado de registros en una entidad. De forma predeterminada, se exportarán todos los registros de la entidad seleccionada. Por lo tanto, si ha creado más de un registro de sitio web, se exportarán todos los registros de sitios Web.

9.  Seleccione **salir** para cerrar la herramienta.

## <a name="import-portal-configuration-data"></a>Importar datos de configuración del portal

1.  Ejecute la herramienta de migración de configuración y elija **importar datos** en la pantalla principal y, a continuación, seleccione **continuar**.

    > [!div class=mx-imgBorder]
    > ![Importar datos de configuración](../media/import-config-data.png "Importar datos de configuración")

2.  En la pantalla de **Inicio de sesión** , proporcione los detalles de autenticación para conectarse a su entorno de Common Data Service desde donde desea exportar los datos. Si tiene varias organizaciones en el entorno de Common Data Service desde donde exportar los datos, active la casilla **Mostrar lista de organizaciones disponibles** y, a continuación, seleccione **Inicio de sesión**.

3.  Si tiene varias organizaciones y ha seleccionado la casilla **Mostrar lista de organizaciones disponibles** en el paso anterior, la siguiente pantalla le permite elegir la organización a la que desea conectarse. Seleccione un entorno de Common Data Service al que conectarse. 

    > [!NOTE]
    > - Si no tiene varias organizaciones, no se muestra esta pantalla.
    > - Asegúrese de que la solución de portal ya está instalada para la organización en la que planea importar las configuraciones.

4.  En la pantalla siguiente se le pide que proporcione el archivo de datos (. zip) que se va a importar. Busque el archivo de datos, selecciónelo y, a continuación, seleccione **importar datos**. 

    > [!div class=mx-imgBorder]
    > ![Progreso de la importación de datos de configuración](../media/import-config-status.png "Progreso de la importación de datos de configuración")

5.  En la pantalla siguiente se muestra el estado de importación de los registros. La importación de datos se realiza en varios pasos para importar primero los datos de la base durante la puesta en cola de los datos dependientes y, a continuación, importar los datos dependientes en los pasos siguientes para controlar las dependencias de datos o los vínculos. Esto garantiza la importación de datos limpios y coherentes. 

6.  Seleccione **salir** para cerrar la herramienta. 
