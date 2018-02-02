---
title: "Creación de nuevas entidades en Common Data Service (CDs) con Power Query | Microsoft Docs"
description: Instrucciones detalladas para crear una nueva entidad en los CDS mediante Power Query.
services: 
suite: powerapps
documentationcenter: na
author: mllopis
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/18/2017
ms.author: millopis
ms.openlocfilehash: 18f580c06412968b27a279a526b562e27cb89e26
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="create-new-entities-in-the-common-data-service-cds-using-power-query"></a>Creación de nuevas entidades en Common Data Service (CDs) con Power Query
Con la integración de **Power Query**, los desarrolladores de aplicaciones empresariales pueden crear nuevas entidades en Common Data Service (CD) desde una amplia gama de orígenes de datos.

**Common Data Service** permite a los usuarios almacenar y administrar de forma segura los datos en un conjunto de entidades estándar y personalizadas. Una *entidad* es un conjunto de campos que se usan para almacenar datos, se parece a una tabla en una base de datos. Una vez que los datos se almacenan en Common Data Service, puede usar **Microsoft PowerApps** para crear aplicaciones completas que utilizan los datos almacenados.

Con la integración de **Power Query**, los desarrolladores de aplicaciones empresariales que usan PowerApps pueden crear nuevas entidades en **Common Data Service** en función de los datos procedentes de orígenes de datos externos, como orígenes de datos locales como las bases de datos relacionales (SQL Server, IBM DB2, etc.), archivos de Excel, de Access y de texto, así como servicios en línea como Salesforce,Azure SQL Database y Data Warehouse, Web API, fuentes de OData y muchos más orígenes. Además de la amplia gama de orígenes de datos a los que se puede conectar, **Power Query** también le permite filtrar, transformar y combinar los datos antes de cargarlos en Common Data Service.

![Nueva entidad de datos](media/data-platform-cds-newentity-pq/data-platform-cds-pq-01.jpg)

## <a name="enabling-the-cds-new-entities-from-power-query-feature"></a>Habilitación de las nuevas entidades de CDS a partir de la característica de Power Query
Esta característica está disponible en su inquilino de PowerApps, pero no está activada de forma predeterminada. Puede habilitarla en [web.powerapps.com](https://aka.ms/pqocds).

> [!NOTE]
> Solo puede crear nuevas entidades personalizadas en las bases de datos que haya creado.

En el portal de PowerApps, siga los pasos que se indican a continuación para habilitar esta característica:

1. Vaya a la pestaña **Common Data Service > Entidades**, en el panel de navegación izquierdo.

2. En la lista **Entidades**, seleccione la lista desplegable **Nueva entidad**.

3. En la lista que aparece en el menú desplegable, seleccione **Nuevas entidades de datos (Technical Preview)**, como se muestra en la siguiente imagen.
   
    ![Nueva entidad de datos](media/data-platform-cds-newentity-pq/data-platform-cds-pq-02.jpg)
4. Una vez que se selecciona **Nuevas entidades de datos (Technical Preview)** en el menú, aparece un cuadro de diálogo con la lista de conectores disponibles en esta versión preliminar técnica, como se muestra en la siguiente imagen.
   
   ![Conectores disponibles](media/data-platform-cds-newentity-pq/data-platform-cds-pq-03.jpg)
5. Una vez que ha seleccionado el conector que desea usar, puede dirigirse a los pasos siguientes para especificar los detalles y las credenciales de la conexión del origen de datos, seleccionar las tablas que se van a importar, etc. También puede acceder al **Editor de consultas** (mediante el botón **Editar** de la vista **Navegador**) y, por tanto, aplicar filtros o pasos de transformación de datos antes de importar datos en CDS.
   
    ![](media/data-platform-cds-newentity-pq/data-platform-cds-pq-04.jpg)

## <a name="adjust-load-settings-and-other-behavior"></a>Ajuste de configuración de carga y otro comportamiento
Una vez que ha completado los pasos descritos en la sección anterior y que tiene un origen de datos listo para su uso para crear nuevas entidades en CDS mediante **Power Query**, puede ajustar una configuración de carga adicional, como actualizar el comportamiento actualización y la configuración específica de la entidad (como el nombre para mostrar, las claves principales, etc.).

![](media/data-platform-cds-newentity-pq/data-platform-cds-pq-05.jpg)

Una vez que haya completados esos pasos y que seleccione **Cargar**, habrá creado nuevas entidades personalizadas en CDS. También puede editar las consultas después de la carga inicial. Para ello, acceda al menú **Entidad** de una entidad específica.

Esta funcionalidad nos entusiasma y estamos ansiosos por recibir sus comentarios. [Envíenos sus sugerencias y comentarios](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) acerca de esta característica.

