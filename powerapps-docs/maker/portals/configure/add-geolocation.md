---
title: Agregar ubicación geográfica a un formulario administrado en un portal | MicrosoftDocs
description: Instrucciones para agregar ubicación geográfica a un formulario administrado.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 44619bfdb6d09221a6a23164a9627b4e06ebb0d7
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979485"
---
# <a name="add-geolocation"></a>Agregar ubicación geográfica

La *ubicación geográfica* es el identificador de la ubicación geográfica del mundo real de un objeto. La ubicación geográfica está estrechamente relacionada con el uso de los sistemas de posicionamiento, pero pone un mayor énfasis en determinar una ubicación completa (por ejemplo, la dirección de la calle) en lugar de simplemente un conjunto de coordenadas geográficas. La palabra ubicación geográfica también puede significar las coordenadas de latitud y longitud de una ubicación específica.

Un formulario administrado se puede configurar para mostrar un control de mapa para que se muestre una ubicación existente como una chincheta en un mapa o proporcionar la capacidad de que el usuario especifique una ubicación.

![Datos de ubicación en un formulario.](../media/location-data-form.png "Datos de ubicación en un formulario")

Si el formulario o el campo de línea de dirección son editables y este campo está en blanco, cuando se cargue la página se preguntará al usuario si deseará compartir la ubicación. Si elije compartir la ubicación, el mapa se actualizará con su ubicación detectada actualmente. El usuario puede refinar la ubicación de la chincheta arrastrándola. Si el usuario elige no compartir la ubicación puede especificar manualmente la ubicación en los campos proporcionados y se pedirá al servicio de asignación que busque la ubicación y actualice la latitud y la longitud, así como que recoloque la chincheta en el mapa.

## <a name="add-geolocation"></a>Agregar ubicación geográfica
Para agregar la funcionalidad de ubicación geográfica a un formulario administrado, las siguientes tareas se deben completar.

### <a name="form-customization"></a>Personalización de formularios
Edite el formulario de entidad con el diseñador de formularios y realice las modificaciones siguientes:

1. Cree una sección nueva y proporcione una etiqueta adecuada, por ejemplo, **Mapa**. Esta sección contendrá el mapa.
2. Establezca el nombre de la sección en **sección\_mapa** o un nombre que termine con _sección\_mapa_, por ejemplo, el **contoso\_sección\_mapa**. Este nombre es importante ya que el motor de formularios busca una sección con este nombre para determinar cuándo generar un mapa. 
3. Agregue un campo nuevo o existente que guardará la dirección con formato y la agregará a la sección **Mapa** creada en el paso anterior.
4. Cree una sección nueva y proporcione una etiqueta adecuada, por ejemplo, **Ubicación**. Esta sección contendrá los campos de dirección para la ubicación seleccionada.
5. Agregue los campos de dirección necesarios en la sección **Ubicación** creada en el paso anterior: 
    - Línea de dirección
    - Ciudad
    - Condado
    - Estado o provincia
    - País o región
    - Código postal
    - Latitud
    - Longitud

El formulario resultante debe parecerse al siguiente. Puede elegir diferentes nombres para mostrar de estos campos. También puede elegir diseñar estas secciones si lo prefiere.

![Formulario de ubicación geográfica personalizado.](../media/custom-geolocation-form.png "Formulario de ubicación geográfica personalizado")

### <a name="site-settings"></a>Configuraciones de sitios
La ubicación geográfica con la funcionalidad de mapa en los formularios administrados requiere configuración para completar solicitudes con el punto de conexión de REST de servicio de asignación. La siguiente configuración de ubicaciones se usa para configurar el servicio de ubicación.

|Nombre|Valor|
|---|---|
|Mapas de Bing/credenciales|Clave exclusiva para autentificar solicitudes a API de Mapas de Bing. Visite [www.bingmapsportal.com](https://www.bingmapsportal.com) para crear una cuenta de mapas de Bing y para obtener una clave. Requerido.|
|Mapas de Bing/URL rest|Dirección URL de API de REST de Mapas de Bing. Opcional. Si no se especifica un valor, se utiliza el https://dev.virtualearth.net/REST/v1/Locations predeterminado.|
| |

### <a name="field-configurations"></a>Configuraciones de campos
El control de mapa requiere configuración adicional para indicarle cuáles son los ID de los diferentes campos de ubicación para poder asignarles valores o recuperar valores. La configuración depende del tipo de formulario administrado.

- Para los formularios de entidad, consulte [Configuración de ubicación geográfica para formularios de entidad](entity-forms.md#geolocation-configuration-for-entity-forms).

- Para formularios web, consulte [Configuración de ubicación geográfica para formularios web](web-form-properties.md#geolocation-configuration-for-web-form).
