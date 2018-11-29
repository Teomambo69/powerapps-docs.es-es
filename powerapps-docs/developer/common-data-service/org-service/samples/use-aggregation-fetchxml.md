---
title: 'Ejemplo: Usar agregación en FetchXML (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar datos de registros agregados mediante FetchXML.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-use-aggregation-in-fetchxml"></a>Ejemplo: uso de agregación en FetchXML

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-use-aggregation-fetchxml -->

Este ejemplo muestra cómo recuperar datos de registros agregados mediante FetchXML.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

La consulta `FetchXML` está diseñada para usarse en un escenario donde crea consultas para obtener los datos.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. La clase `CreateRequiredRecords` crea 3 registros de oportunidades y registro de cuenta.

### <a name="demonstrate"></a>Demostración

1. La `estimatedvalue_avg` recupera el promedio de estimatedvalue para todas las oportunidades. El método `EntityCollection` devuelve los resultados de la solicitud `RetrieveMultiple`.
1. El `opportunity_count` recupera el recuento de todas las oportunidades.
1. El `estimatedvalue_max` recupera el estimatedvalue máximo de todas las oportunidades.
1. El `estimatedvalue_min` recupera el estimatedvalue mínimo de todas las oportunidades.
1. El `estimatedvalue_sum` recupera la suma de estimatedvalue de todas las oportunidades.
1. El `estimatedvalue_avg2` recupera los distintos valores globales en una sola consulta.
1. El `groupby1` recupera una lista de usuarios con un recuento de todos los oportunidades que poseen usando groupby.
1. El `byyear` recupera la información agregada sobre todas las oportunidades que han obtenido por año.
1. El `byquarter` recupera la información agregada sobre las oportunidades que han obtenido por trimestre.
1. El `bymonth` recupera la información agregada sobre las oportunidades que han obtenido por mes.
1. El `byweek` recupera la información agregada sobre las oportunidades que han obtenido por semana.
1. El `byday` recupera la información agregada sobre las oportunidades que han obtenido por día.
1. El `byyrqtr` recupera la información agregada sobre las oportunidades que han obtenido por año y trimestre.
1. El `byyrqtr2` especifica el orden de resultados. 


### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar todos los datos creados en el ejemplo.

La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datps para obtener los mismos resultados.
