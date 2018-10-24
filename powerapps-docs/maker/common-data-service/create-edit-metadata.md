---
title: Entidades y metadatos en Common Data Service for Apps | Microsoft Docs
description: Información sobre las entidades y metadatos en Common Data Service for Apps
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 88b18946-474c-4c94-8e4c-27532f930757
caps.latest.revision: 28
ms.author: matp
manager: kvivek
ms.openlocfilehash: ef2f92865205fa7c97ada356edc70ac69a637e0f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712823"
---
# <a name="entities-and-metadata-in-common-data-service-for-apps"></a>Entidades y metadatos en Common Data Service for Apps

Common Data Service for Apps está diseñado para que el usuario pueda crear de manera rápida y sencilla un modelo de datos para la aplicación. Habitualmente, no debería tener que preocuparse de algunos de los detalles sobre los metadatos que se presentan en este tema. Pero si desea desarrollar una comprensión más profunda sobre cómo funcionan las aplicaciones que usan CDS for Apps o si está evaluando lo que es posible, comprender los metadatos que usa CDS for Apps puede brindar información detallada.

Los *metadatos* se refieren a datos sobre los datos. CDS for Apps proporciona una plataforma flexible para el usuario, porque es relativamente fácil de editar las definiciones de los datos que el entorno usará. En CDS for Apps, los metadatos son una colección de entidades. Las entidades describen los tipos de datos que se almacenan en la base de datos.  Cada entidad corresponde a una tabla de base de datos y cada campo (también conocido como atributo) dentro de una entidad representa una columna de esa tabla. Los metadatos de la entidad son lo que controla los tipos de registros que se pueden crear y el tipo de acciones que se pueden realizar en ellos. Cuando se usan las herramientas de personalización para crear o editar las entidades, los campos y las relaciones de entidad, lo que se edita son estos metadatos. 
  
Los distintos clientes que los usuarios utilizan con los datos en el entorno dependen de los metadatos de la entidad y se adaptan cuando se personalizan los metadatos. Pero estos clientes también dependen de otros datos para controlar los elementos visuales que se van a mostrar, cualquier lógica personalizada que se vaya a aplicar y cómo aplicar la seguridad. Estos datos del sistema también se almacenan dentro de las entidades, pero estas no están disponibles para personalizarlas.

Para información sobre las entidades, los atributos y las relaciones de entidad estándar que se incluyen de manera predeterminada en CDS for Apps, consulte el artículo sobre la [referencia de entidades](/powerapps/developer/common-data-service/reference/about-entity-reference).

> [!TIP]
> En los diseñadores disponibles para modificar los metadatos no se pueden mostrar todos los detalles encontrados en los metadatos. Se puede instalar una aplicación controlada por modelos denominada **Explorador de metadatos** que permite ver todas las propiedades de metadatos y las entidades que se encuentran en el sistema. Más información: [Exploración de los metadatos de su organización](https://docs.microsoft.com/dynamics365/customer-engagement/developer/browse-your-metadata).
  
<a name="BKMK_CreateNewOrUseExistingMetadata"></a>

## <a name="create-new-metadata-or-use-existing-metadata"></a>Creación de metadatos o uso de metadatos existentes

CDS for Apps incluye varias entidades estándar que admiten las funcionalidades básicas de una aplicación empresarial. Por ejemplo, se espera que los datos sobre los clientes o clientes potenciales se almacenen con las entidades de cuenta o contacto.  
  
Cada una de estas entidades también contiene diversos campos que representan los datos comunes que el sistema podría necesitar para almacenar la entidad correspondiente.  
  
Para la mayoría de las organizaciones es la ventaja de usar entidades y atributos estándar para los objetivos que se proporcionaron. 
  
Si instala una solución, puede esperar que el programador de la solución haya aprovechado las entidades y los atributos estándar. Crear una entidad personalizada que reemplace un atributo o entidad del sistema significará que es posible que cualquier solución disponible no funcione para la organización.  
  
Es por estas razones que se recomienda que busque y use las entidades, los campos y las relaciones de entidad estándar cuando sean adecuadas para la organización. Si no lo son y no se pueden editar para que coincidan con sus necesidades, debe evaluar si es necesario crear una nueva entidad, campo o relaciones de entidad. 

<!--  Can we say this yet? 
    
> [!NOTE]
> The [Common Data Model](/powerapps/common-data-model/overview) will provide a capability to add additional standard entities. 

-->

Recuerde que puede cambiar el nombre para mostrar de una entidad para que coincida con la nomenclatura que la organización usa. Por ejemplo, es muy común que los usuarios cambien el nombre para mostrar de la entidad Cuenta a *Empresa* o el nombre de la entidad Contacto a *Individuo*. Esto se puede hacer en entidades o atributos sin cambiar el comportamiento de la entidad. Para más información sobre cómo cambiar el nombre de las entidades, consulte [Cambio del nombre de una entidad](edit-entities.md#change-the-name-of-an-entity).
  
Las entidades, los campos o las relaciones de entidad estándar no se pueden eliminar. Se consideran parte de la solución del sistema y se espera que estén presentes en cada organización. Si quiere ocultar una entidad estándar, cambie los privilegios de rol de seguridad de su organización para quitar el privilegio de lectura de esa entidad. De este modo, se quitará la entidad de la mayoría de las partes de la aplicación. Si hay un campo del sistema que no es necesario, quítelo del formulario y de cualquier vista que lo use. Cambie el valor **Searchable** en las definiciones de campo y relación de entidad para que no aparezcan en la búsqueda avanzada. 
  
<a name="BKMK_LimitationsOnMetadata"></a>   

## <a name="limitations-on-creating-metadata-items"></a>Limitaciones en la creación de elementos de metadatos  

Hay un límite en el número de entidades que puede crear. Puede encontrar información sobre el número máximo en la página **[Settings](../model-driven-apps/advanced-navigation.md#settings)** > **Administration** > **Resources In Use** (Configuración > Administración > Recursos en uso). Si necesita más entidades personalizadas, póngase en contacto con soporte técnico. Es posible ajustar este límite superior.  
  
Dentro de cada entidad, hay un límite superior en el número de campos que puede crear. Este límite se basa en las limitaciones técnicas respecto de la cantidad de datos que se pueden almacenar en una fila de una tabla de base de datos. Es difícil proporcionar un número específico, porque cada tipo de campo puede usar una cantidad de espacio distinta. El límite superior depende del espacio total que usan todos los campos para la entidad.  
  
La mayoría de los usuarios no crean campos personalizados suficientes para alcanzar el límite, pero si planea agregar cientos de campos personalizados a una entidad, debería considerar si este es el mejor diseño. ¿Todos los campos que planea agregar describen las propiedades de un registro de esa entidad? ¿Realmente espera que quienes usan su organización puedan administrar un formulario que incluye un número tan alto de campos? El número de campos que agrega a un formulario aumenta la cantidad de datos que se deben transferir cada vez que se edita un registro y afectará el rendimiento del sistema. Considere estos factores al agregar campos personalizados a una entidad.  
  
Los campos de conjuntos de opciones brindan un conjunto de opciones que se mostrará en un control desplegable de un formulario o en un control de lista desplegable al usar la búsqueda avanzada. El entorno puede admitir miles de opciones dentro de un conjunto de opciones, pero no debe considerarlo como el límite superior. Los estudios sobre la facilidad de uso han mostrado que los usuarios tienen problemas para utilizar un sistema donde un control desplegable proporciona muchas opciones. Use el campo de conjunto de opciones para definir las categorías de los datos. No use los campos de conjuntos de opciones para seleccionar las categorías que realmente representan elementos de datos independientes. Por ejemplo, en lugar de mantener un campo de conjunto de opciones que almacena cada uno de los cientos de posibles fabricantes de un tipo de equipo, considere la posibilidad de crear una entidad que almacene las referencias a cada fabricante y use un campo de búsqueda en lugar de un conjunto de opciones.  
  
## <a name="next-steps"></a>Pasos siguientes 

[Create or edit entities (record types)](create-edit-entities.md) (Creación o edición de entidades [tipos de registro])<br />
[Create and edit relationships between entities](create-edit-entity-relationships.md) (Creación y edición de relaciones entre entidades)

