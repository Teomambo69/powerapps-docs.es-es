---
title: Colección de controles (referencia de la API de cliente) | MicrosoftDocs
description: Obtenga información sobre cómo obtener acceso a controles asociados con atributos.
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d5f3c0c5-b267-42a8-82e8-8c4a1cda3752
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="controls-collection-client-api-reference"></a>Colección de controles (referencia de la API de cliente)



Utilice la colección de controles para obtener acceso a los controles asociados con atributos. 

Dado que cada atributo se puede representar más de una vez en la página, la colección de controles proporciona acceso a todos los controles que representan ese atributo. Si el atributo es representado sólo por un campo en la página, la longitud de esta colección será 1. Al usar el método getName del control, el nombre del primer control coincidirá con el nombre del atributo. La segunda instancia de un control para ese atributo será **\<attributeName>1**. El patrón **\<attributeName>+N** continuará para cada control adicional agregado al formulario para un atributo específico.

Cuando un formulario muestra un control de flujo de proceso de negocio en el encabezado, se agregarán controles adicionales para cada atributo que se muestra en el flujo de proceso de negocio. Estos controles tienen un nombre único como el siguiente: **header\_process\_\<attribute name>**.

Cuando realice acciones en los controles que están ligados a un atributo siempre debe considerar que el control puede estar incluido en la página más de una vez y normalmente debe realizar las mismas acciones para cada control para el atributo. Puede hacerlo recorriendo la colección de controles de atributo y realizar las acciones en cada control.

### <a name="related-topics"></a>Temas relacionados

[Atributos (referencia de la API de cliente)](../attributes.md)


