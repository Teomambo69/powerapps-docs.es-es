---
title: Introducción a la conexión de Power BI | Microsoft Docs
description: Consultar las conexiones de Power BI disponibles
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/12/2016
ms.author: lanced
ms.openlocfilehash: 3f90a3b7fc7914caf61cc33abcf6baec87328ece
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39015625"
---
# <a name="connect-to-power-bi-from-powerapps"></a>Conectar al Power BI desde PowerApps
![Power BI](./media/connection-powerbi/powerbiicon.png)

Power BI es un conjunto de herramientas de análisis de negocios destinado a analizar datos y compartir información. Supervise su negocio y obtenga respuestas rápidamente con paneles muy completos disponibles en todos los dispositivos. En su aplicación, puede comprobar el estado de las alertas de datos que ha configurado en el servicio Power BI. Para más información sobre las alertas de datos en Power BI, vaya a la [página de documentación](https://https://docs.microsoft.com/power-bi/service-set-data-alerts).

En este tema se muestra cómo utilizar la conexión de Power BI en una aplicación y se enumeran las funciones disponibles.

## <a name="prerequisites"></a>Requisitos previos
* [Registrarse](https://web.powerapps.com)
* Agregar la [conexión](https://powerapps.microsoft.com/tutorials/add-manage-connections/) de Power BI
* Crear una aplicación a partir de una [plantilla](https://powerapps.microsoft.com/tutorials/get-started-test-drive/), de [datos](https://powerapps.microsoft.com/tutorials/get-started-create-from-data/) o desde [el principio](https://powerapps.microsoft.com/tutorials/get-started-create-from-blank/)

## <a name="use-the-power-bi-connection-in-your-app"></a>Uso de la conexión de Power BI en la aplicación
### <a name="list-the-alerts-that-youve-set-up-in-the-power-bi-service"></a>Enumerar las alertas que ha configurado en el servicio Power BI
1. En el menú **Insert** (Insertar), seleccione **Gallery** (Galería) y agregue algunas de las **galerías de texto**.
2. Para mostrar las alertas del usuario actual, establezca la propiedad [Items](../controls/properties-core.md) de la galería en la siguiente fórmula:

   `PowerBI.GetAlerts()`

La galería se actualizará con la lista de alertas. Para cada alerta, recibirá su nombre, número identificador e id. del espacio de trabajo del grupo en el que se configuró la alerta. Necesitará el id. de la alerta para obtener más información sobre ella.

### <a name="view-the-status-of-an-alert"></a>Visualización del estado de una alerta
Para ver el estado de la alerta, llame a la función CheckAlertStatus con el id. de alerta obtenido en el paso anterior.

El id. de la alerta se puede pasar como una cadena literal (por ejemplo, "1234") o como una referencia a una sección de la galería rellenada mediante la llamada a GetAlerts() (por ejemplo, Gallery1.Selected.alertId).

Para continuar, agregue una etiqueta y establezca su propiedad [Texto](../controls/properties-core.md) en una de estas fórmulas:

* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertTitle`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).currentTileValue`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertThreshold`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).isAlertTriggered`

La etiqueta se actualizará con el estado actual de la alerta.

## <a name="view-the-available-functions"></a>Visualización de las funciones disponibles
Esta conexión incluye las siguientes funciones:

| Nombre de la función | Descripción |
| --- | --- |
| GetAlerts |Muestra las alertas que ha configurado en el servicio Power BI. |
| CheckAlertStatus |Comprueba el estado de una alerta determinada. |

## <a name="getalerts"></a>GetAlerts
Muestra las alertas que ha configurado en el servicio Power BI.

#### <a name="input-properties"></a>Propiedades de entrada
Ninguna

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| value |array |No |Una matriz de las alertas de datos que ha configurado en el servicio Power BI. Cada elemento de la matriz incluirá: <ul><li>alertTitle: el título de la alerta.</li><li>alertId: el id. de la alerta.</li><li>groupId: el id. del grupo en el que se creó la alerta.</li></ul> |

## <a name="checkalertstatus"></a>CheckAlertStatus
Comprueba el estado de una alerta.

> [!NOTE]
> Las solicitudes que se realicen a este punto de conexión se limitarán por alerta si se llama con demasiada frecuencia.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| alertId |integer |Sí |El id. de la alerta que devuelve GetAlerts. |

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| tileValue |number |No |El valor del icono cuando se desencadenó la alerta. |
| tileUrl |string |No |Dirección URL del icono con la alerta. |
| alertTitle |string |No |Nombre de la alerta. |
| isAlertTriggered |boolean |No |Si la alerta se desencadenó ahora. |
| alertThreshold |number |No |El umbral en el que se desencadenó la alarma. |

## <a name="helpful-links"></a>Vínculos útiles
Consulte todas las [conexiones disponibles](../connections-list.md).  
Aprenda a [agregar conexiones](../add-manage-connections.md) a sus aplicaciones.

