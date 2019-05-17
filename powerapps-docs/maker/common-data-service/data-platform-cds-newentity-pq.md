---
title: Agregar datos a una entidad en Common Data Service usando Power Query | Microsoft Docs
description: Instrucciones paso a paso para ver cómo se usa Power Query para agregar datos a una entidad nueva o existente en Common Data Service desde otro origen de datos.
author: mllopis
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 03/21/2018
ms.author: millopis
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="add-data-to-an-entity-in-common-data-service-by-using-power-query"></a>Agregar datos a una entidad en Common Data Service usando Power Query
En este procedimiento, creará una entidad en [Common Data Service](data-platform-intro.md) y la rellenará con datos de una fuente de OData usando Power Query. Puede usar las mismas técnicas para integrar datos desde estos orígenes en línea y locales, entre otros:

* SQL Server
* Salesforce
* IBM DB2
* Acceso
* Excel
* API web
* Fuentes de OData
* Archivos de texto

También puede filtrar, transformar y combinar datos antes de cargarlos en una entidad nueva o existente.

Si no tiene una licencia de PowerApps, puede [suscribirse para obtener una gratuita](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Requisitos previos
Para seguir este tema, debe cambiar a un [entorno](../canvas-apps/working-with-environments.md) en el que pueda crear entidades.

## <a name="specify-the-source-data"></a>Especificar los datos de origen

1. Inicie sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y haga clic o pulse en la flecha hacia abajo para **Datos** cerca del borde izquierdo.

    ![Página principal de PowerApps](./media/data-platform-cds-newentity-pq/sign-in.png)

1. En la lista que aparece, haga clic o pulse en **Integración de datos** y haga clic o pulse en **Nuevo proyecto** cerca de la esquina superior derecha de la ventana.

1. En la lista de orígenes de datos, haga clic o pulse en **OData**.

    ![Elija el conector de OAuth](./media/data-platform-cds-newentity-pq/choose-odata.png)

1. En **Configuración de conexión**, escriba o pegue esta dirección URL y, a continuación, seleccione **Siguiente**:<br>
`http://services.odata.org/V4/Northwind/Northwind.svc/`

1. En la lista de tablas, seleccione la casilla **Clientes** y haga clic o pulse en **Siguiente**.

    ![Seleccionar la tabla de clientes](./media/data-platform-cds-newentity-pq/select-table.png)

1. (opcional) Modifique el esquema para adaptarlo a sus necesidades eligiendo qué columnas se incluirán, transformando la tabla de una o varias maneras, agregando un índice o una columna condicional o realizando otros cambios.

1. En la esquina inferior derecha haga clic o pulse en **Siguiente**.

## <a name="specify-the-target-entity"></a>Especificar la entidad de destino
1. En **Configuración de carga**, seleccione **Cargar en nueva entidad**.

    ![Especificar el nombre de la nueva entidad](./media/data-platform-cds-newentity-pq/new-entity-name.png)

    Puede asignar a la nueva entidad un nombre distinto o un nombre para mostrar, pero mantenga los valores predeterminados para seguir este tutorial exactamente.

1. En el lista de **Campos de nombre principal**, haga clic o pulse en **ContactName** y, a continuación, haga clic o pulse en **Siguiente** en la esquina inferior derecha.

    Puede especificar otro campo de nombre principal diferente, asignar una columna diferente de la tabla de origen a cada campo de la entidad que está creando, o ambas cosas. También puede especificar si las columnas de texto del resultado de la consulta se deben crear como Texto multilínea o Texto de una línea en Common Data Service. Para seguir este tutorial de forma precisa, deje la asignación de columnas predeterminada.

1. Cuando el **Estado de carga** sea **Completado**, seleccione **Hecho** en la esquina inferior derecha.

1. En **Datos** (cerca del borde izquierdo), seleccione **Entidades** para mostrar la lista de entidades en la base de datos.

    La entidad **Clientes** que creó de una fuente de OData aparece como entidad personalizada.

    ![Lista de entidades estándar y personalizadas](./media/data-platform-cds-newentity-pq/entity-list.png)

> [!WARNING]
> Si usa Power Query para agregar datos a una entidad existente, todos los datos de esa entidad se sobrescribirán.

Si selecciona **Cargar en entidad existente**, puede especificar la entidad a la que agregará datos desde la tabla **Clientes**. Podría, por ejemplo, agregar los datos a la entidad **Cuenta** con la que se suministra Common Data Service. En **Columna de origen**, puede especificar con mayor detalle que los datos de la columna **ContactName** de la tabla **Clientes** se deben agregar a la columna **Nombre** en la entidad **Cuentas**.

![Especificar el nombre de la nueva entidad](./media/data-platform-cds-newentity-pq/existing-entity.png)

Estamos encantados con esta funcionalidad y estamos deseando oír sus comentarios. [Envíenos sus sugerencias y comentarios](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) sobre esta función.

Si aparece un [mensaje de error sobre permisos](data-platform-cds-newentity-troubleshooting-mashup.md), consulte con el administrador.
