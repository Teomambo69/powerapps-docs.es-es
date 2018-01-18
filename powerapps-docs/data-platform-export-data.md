---
title: "Importación o exportación de datos | Microsoft Docs"
description: Importe o exporte una entidad.
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 880881b31362d38ed0d44126245dd96d2a74150f
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="import-or-export-data-from-the-common-data-service"></a>Importar o exportar datos a partir de Common Data Service
Puede mover datos a Common Data Service o desde este, de una de estas dos maneras:

* Si desea realizar una única importación o exportación masiva de datos, puede usar Microsoft Excel para varias entidades.
* Si desea realizar una importación o exportación continua de datos de una sola entidad a otro servicio, como Dynamics 365 o Salesforce, o incluso a un archivo de Excel. Para configurar una importación o exportación en curso, puede usar [Microsoft Flow](https://flow.microsoft.com).

## <a name="import-or-export-data-once"></a>Importación o exportación de datos una sola vez
### <a name="import-data-from-excel"></a>Importación de datos desde Excel
1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo.
2. Junto a **Nueva entidad**, haga clic o pulse el botón de puntos suspensivos y, a continuación, haga clic o pulse en **Importar datos**.
3. Seleccione la entidad a la que desea importar los datos y, a continuación, haga clic o pulse en **Siguiente**.
4. Pulse o haga clic en **Buscar**. Seleccione el archivo a partir del que desea importar los datos.
5. Si el valor de **Estado de asignación** no es **Coincidencia** con una marca de verificación verde, deberá especificar la asignación entre los campos de la entidad y las columnas del archivo de Excel. Para asignar las columnas:
   1. Haga clic o pulse en **Show Mapping** (Mostrar asignación).
   2. Para cada campo de entidad, seleccione la columna coincidente en el archivo de Excel.
   3. Haga clic o pulse en **Guardar cambios**.
6. Haga clic en **Importar**.

### <a name="export-data-to-excel"></a>Exportar datos a Excel
Puede realizar una única exportación de datos desde una entidad estándar o una personalizada, y puede exportar datos de más de una entidad a la vez. Si exporta datos de más de una entidad, cada entidad se exporta a su propio archivo de Microsoft Excel.

1. En [powerapps.com](https://web.powerapps.com), pulse o haga clic en **Entidades** en el panel de navegación izquierdo.
2. Junto a **Nueva entidad**, haga clic o pulse el botón de puntos suspensivos y, a continuación, haga clic o pulse en **Exportar datos**.
3. Seleccione las entidades desde las que desea exportar los datos y, a continuación, haga clic o pulse en **Exportar a Excel**.
4. Cuando aparezca el mensaje **Exportación completada**, haga clic o pulse en **Download exported data** (Descargar datos exportados) para descargar los datos.

## <a name="use-microsoft-flow-to-set-up-ongoing-import-or-export"></a>Use Microsoft Flow para configurar una importación o exportación en curso.
Puede configurar una importación o exportación en curso para una única entidad estándar o personalizada a la vez. Entre los posibles lugares a los que se puede conectar se incluyen:

* Dynamics 365
* Salesforce
* Archivos de Microsoft Excel almacenados en cualquier proveedor de archivos en la nube
* Una base de datos de Microsoft SQL en la nube o una local
* Un conector personalizado que defina para conectarse a sus propios sistemas

En la actualidad, cuando utiliza Microsoft Flow para importar o exportar datos, no se trata de un servicio de sincronización completo. Cuando se agrega un objeto a un servicio, este se importa en el otro sistema. Sin embargo, esto significa que si se elimina un objeto de un sistema, este no se eliminará del otro.

La configuración de la importación depende de si ya existe una plantilla para el objeto que desea importar. Si existe una plantilla, puede configurarla para copiar datos desde un sistema a otro. Para más información, consulte [Crear un flujo que use Microsoft Common Data Service](https://flow.microsoft.com/documentation/common-data-model-intro/). Sin embargo, si no existe esa plantilla, debe crear un flujo que pueda usar la base de datos. Para más detalles, consulte [cómo crear un flujo desde cero](https://flow.microsoft.com/documentation/get-started-logic-flow/).

