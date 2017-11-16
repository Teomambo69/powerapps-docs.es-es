---
title: "Administración de datos de entidad | Microsoft Docs"
description: Trabajar con datos en el servicio y en Excel
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: n6RizzixvxM
courseduration: 7m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 807284f05d4233ccf9180f8648f219a4e1eee2b6
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="manage-entity-data"></a>Administración de datos de entidad
En este tema, se describe la administración de datos en Common Data Service. Ya hemos visto brevemente cómo importar y exportar datos en otros temas, pero ahora dedicaremos más tiempo a trabajar con datos en Excel.

## <a name="import-data-from-excel-or-csv"></a>Importación de datos desde Excel o CSV
En este ejemplo, importaremos datos de Excel en la entidad Product review que creamos en el último tema. También puede importar datos de archivos CSV, que es un formato común para mover datos. Este es un recordatorio del aspecto de la entidad; en este tema nos centraremos en el área resaltada.

![Entidad Product review](./media/learning-common-data-service-manage/product-review-entity.png)

En una entidad, haga clic en **Importar datos** y, a continuación, vaya hasta el archivo desde el que desea importar. Haga clic en **Mostrar asignación** y asegúrese de que las columnas en el archivo de Excel están asociadas a los campos correctos de la entidad. Cuando esté satisfecho con las asignaciones, haga clic en **Guardar cambios**. En la pantalla de importación principal, haga clic en **Importar**.

![Importación de datos desde Excel](./media/learning-common-data-service-manage/import-data.png)

## <a name="export-data-to-excel"></a>Exportar datos a Excel
Exporte los datos si necesita acceder a ellos fuera de Common Data Service. En una entidad, haga clic en **Exportar datos** y, a continuación, espere a que el archivo zip se genere. Abra el archivo zip y verá los datos exportados. 
![Exportar datos a Excel](./media/learning-common-data-service-manage/export-data.png)

## <a name="export-a-template-to-excel"></a>Exportar una plantilla a Excel
Además de descargar datos, puede descargar una plantilla. Una plantilla es un archivo de Excel con una estructura que coincide con los campos de una entidad, pero sin los datos. Después de descargar la plantilla, rellénela manualmente o mediante programación, y vuelva a importarla al servicio. En una entidad, haga clic en **Exportar plantilla** y, a continuación, especifique los campos que desee (en este caso, seleccioné un solo campo). Haga clic en **Exportar a Excel** y espere a que el archivo de Excel se genere. Abra el archivo de Excel y verá la plantilla exportada con los campos seleccionados.

![Exportar una plantilla a Excel](./media/learning-common-data-service-manage/export-template.png)

## <a name="open-and-work-with-data-in-excel"></a>Abrir y trabajar con datos en Excel
Es la última cosa que veremos es la opción **Abrir en Excel**. Si tiene instalado el complemento PowerApps, puede usar esta opción para explorar y editar los datos en Excel. En una entidad, haga clic en **Abrir en Excel** y, a continuación, abra el archivo. Habilite la edición; el complemento establecerá una conexión activa con la entidad en el servicio y rellenará el libro. Puede editar el libro directamente, así como agregar y eliminar filas. Haga clic en **Publicar** para guardar los cambios. También puede actualizar los datos para asegurarse de tener una copia actualizada, así como filtrar los datos, lo que resulta especialmente útil si una entidad contiene una gran cantidad de datos.

![Abrir en Excel](./media/learning-common-data-service-manage/open-excel.png)

Así concluye el tema sobre cómo administrar datos en Common Data Service (importar, exportar y trabajar con datos en Excel). En el tema siguiente, hablaremos acerca de cómo administrar la seguridad de los datos.

