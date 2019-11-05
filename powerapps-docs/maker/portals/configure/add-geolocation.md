---
title: Agregar ubicación geográfica a un formulario administrado en un portal | MicrosoftDocs
description: Instrucciones para agregar geolocation a un formulario administrado.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a3c583658a5593d8e6c5f6c139a5c967e9581626
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553564"
---
# <a name="add-geolocation"></a>Agregar ubicación geográfica

*Geolocation* es la identificación de la ubicación geográfica real de un objeto. La geolocalización está estrechamente relacionada con el uso de sistemas de colocación, pero supone un mayor énfasis en la determinación de una ubicación significativa (por ejemplo, una dirección postal) en lugar de un conjunto de coordenadas geográficas. La ubicación de la palabra también puede significar las coordenadas de latitud y longitud de una ubicación determinada.

Un formulario administrado puede configurarse para mostrar un control de mapa para mostrar una ubicación existente como un PIN en un mapa o para proporcionar a los usuarios la posibilidad de especificar una ubicación.

![Datos de ubicación en un formulario.](../media/location-data-form.png "Datos de ubicación en un formulario")

Si el campo de la línea de formulario o dirección es editable y este campo está en blanco, cuando la página se cargue, se solicitará al usuario que le pregunte si desea compartir su ubicación. Si optan por compartir su ubicación, el mapa se actualizará con la ubicación detectada actualmente. El usuario puede perfeccionar la ubicación del PIN arrastrándolo. Si el usuario decide no compartir su ubicación, puede especificar manualmente la ubicación en los campos proporcionados y se consultará el servicio de asignación para encontrar la ubicación, actualizar la latitud y la longitud, y cambiar la posición del PIN en el mapa en consecuencia.

## <a name="add-geolocation"></a>Agregar ubicación geográfica
Para agregar la funcionalidad de ubicación geográfica a un formulario administrado, se deben completar las siguientes tareas.

### <a name="form-customization"></a>Personalización de formularios
Edite el formulario de la entidad mediante el diseñador de formularios y realice las modificaciones siguientes:

1. Cree una nueva sección y proporcione una etiqueta adecuada, por ejemplo, **map**. Esta sección contendrá la asignación.
2. Establezca el nombre de la sección en la **sección\_asignación** o un nombre que termine en la _sección mapa de\__ , por ejemplo, **contoso\_sección\_asignación**. Este nombre es importante porque el motor de formulario busca una sección con este nombre para determinar cuándo se debe representar un mapa. 
3. Agregue un campo nuevo o existente que almacenará la dirección con formato y agréguelo a la sección de **mapa** creada en el paso anterior.
4. Cree una nueva sección y proporcione una etiqueta adecuada, por ejemplo **Ubicación**. Esta sección contiene los campos de dirección de la ubicación seleccionada.
5. Agregue los campos de dirección necesarios a la sección **Ubicación** creada en el paso anterior: 
    - Línea de dirección
    - Ciudad
    - Ciudad
    - Estado o provincia
    - País o región
    - Código postal
    - Latitude
    - Longitud

El formulario resultante debe ser similar al siguiente. Puede elegir nombres para mostrar diferentes para estos campos. También puede diseñar estas secciones de la forma que prefiera.

![Formulario de ubicación geográfica personalizado.](../media/custom-geolocation-form.png "Formulario de ubicación geográfica personalizado")

### <a name="site-settings"></a>Configuración del sitio
La funcionalidad de asignación geográfica con asignaciones en formularios administrados requiere la configuración para completar las solicitudes con el punto de conexión de REST del servicio de asignación. La siguiente configuración del sitio se usa para configurar el servicio de ubicación.

|Nombre|Value|
|---|---|
|Bingmaps/credenciales|Clave única para autenticar las solicitudes a la API de mapas de Bing. Visite [www.bingmapsportal.com](https://www.bingmapsportal.com) para crear una cuenta de Bing Maps y obtener una clave. Obligatorio.|
|Bingmaps/restURL|Dirección URL de la API de REST de Bing Maps. Opcional. Si no se especifica un valor, se utiliza el https://dev.virtualearth.net/REST/v1/Locations predeterminado.|
| |

### <a name="field-configurations"></a>Configuraciones de campo
El control de mapa requiere una configuración adicional para indicarle qué son los identificadores de los distintos campos de ubicación, por lo que puede asignarles valores o recuperar valores de ellos. La configuración depende del tipo de formulario administrado.

- Para los formularios de entidad, consulte [configuración de geolocalización para formularios de entidad](entity-forms.md#geolocation-configuration-for-entity-forms).

- Para formularios Web Forms, vea [configuración de geolocalización para formularios Web Forms](web-form-properties.md#geolocation-configuration-for-web-form).
