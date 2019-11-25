---
title: Entidades y metadatos en Common Data Service | MicrosoftDocs
description: Obtener información sobre metadatos y entidades en Common Data Service
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3aeb07c29178570ca17426cca46dd7cbc73a2aca
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707007"
---
# <a name="entities-and-metadata-in-common-data-service"></a>Entidades y metadatos en Common Data Service

Common Data Service está diseñado de modo que pueda crear de forma rápida y sencilla un modelo de datos para su aplicación. Normalmente, no será necesario que se preocupe con algunos de los detalles sobre los metadatos que este tema introducirá. Pero si desea desarrollar conocimientos más profundos sobre cómo funcionan las aplicaciones que usan Common Data Service o si usted está evaluando lo que es posible, la comprensión de los metadatos que usa Common Data Service puede proporcionarle información detallada.

*Metadatos* significa datos acerca de datos. Common Data Service le proporciona una plataforma flexible porque es relativamente fácil editar las definiciones de los datos que usará el entorno. En Common Data Service, los metadatos son una colección de entidades. Las entidades describen las clases de datos que se almacenan en la base de datos.  Cada entidad corresponde a una tabla de la base de datos y cada campo (también denominado atributo) en una entidad representa una columna de la tabla. Los metadatos de la entidad controlan los tipos de registros que puede crear y el tipo de acciones que se pueden realizar en ellos. Cuando utiliza las herramientas de personalización para crear o editar entidades, campos y relaciones entre entidades, está editando estos metadatos. 
  
Los distintos clientes que los usuarios usan para interactuar con los datos del entorno dependen de los metadatos de la entidad y se adaptan cuando usted personaliza los metadatos. Estos clientes también dependen de otros datos para controlar los elementos visuales que se van a mostrar, la lógica personalizada que se va a aplicar y cómo se aplicará la seguridad. Estos datos del sistema también se almacenan en las entidades, pero las entidades propiamente dichas no están disponibles para la personalización.

Puede obtener información sobre entidades estándar, atributos, y las relaciones entre entidades incluidas de forma predeterminada en Common Data Service revisando la [Referencia de entidad](/powerapps/developer/common-data-service/reference/about-entity-reference).

> [!TIP]
> Los diseñadores disponibles para editar metadatos no pueden mostrar todos los detalles encontrados en los metadatos. Puede instalar una aplicación basada en modelos llamada **Explorador de metadatos** que le permitirá todas las entidades y propiedades de metadatos que se encuentran en el sistema. Más información: [Examinar los metadatos para su entorno](https://docs.microsoft.com/dynamics365/customer-engagement/developer/browse-your-metadata).
  
<a name="BKMK_CreateNewOrUseExistingMetadata"></a>

## <a name="create-new-metadata-or-use-existing-metadata"></a>¿Crear nuevos metadatos o usar los metadatos existentes?

Common Data Service incluye varias entidades estándar que admiten las principales capacidades de aplicación de negocios. Por ejemplo, los datos sobre los clientes o clientes potenciales están destinados a almacenarse mediante las entidades de cuenta o contacto.  
  
Cada una de estas entidades también contiene varios campos que representan los datos comunes que el sistema puede necesitar para almacenar la entidad respectiva.  
  
Para la mayoría de las organizaciones es una ventaja para usted utilizar las entidades y los atributos estándar para los fines para los que se han diseñado. 
  
Si instala una solución, puede esperar a que el desarrollador de la solución haya aprovechado las entidades y los atributos estándar. La creación de una entidad personalizada que sustituya una entidad o un atributo del sistema significará que las soluciones disponibles podrían no funcionar en su organización.  
  
Por estas razones, se recomienda buscar y usar las entidades, campos y relaciones entre entidades estándar proporcionados cuando resulten apropiadas para la organización. Si no tienen sentido y no se pueden editar para adaptarlos a sus necesidades, debe evaluar si se necesita crear una nueva entidad, campo o relación entre entidades. 

<!--  Can we say this yet? 
    
> [!NOTE]
> The [Common Data Model](/powerapps/common-data-model/overview) will provide a capability to add additional standard entities. 

-->

Recuerde que puede cambiar el nombre para mostrar de una entidad para que coincida con la nomenclatura que se usa en la organización. Por ejemplo, es muy común que los usuarios cambien el nombre para mostrar de la entidad de Cuenta por *Compañía* o el nombre de la entidad de Contacto por *Individual*. Esto se puede hacer en las entidades o los atributos sin cambiar el comportamiento de la entidad. Para obtener más información sobre cómo cambiar el nombre de las entidades, consulte [Cambiar el nombre de una entidad](edit-entities.md#change-the-name-of-an-entity).
  
No puede eliminar entidades, campos o relaciones entre entidades estándar. Se consideran parte de la solución del sistema y se espera que cada organización los tenga. Si desea ocultar una entidad estándar, cambie los privilegios del rol de seguridad de su organización para quitar el privilegio de lectura para la entidad. Esto quitará la entidad de la mayoría de las partes de la aplicación. Si existe un campo del sistema que no necesita, quítelo del formulario y de cualquier vista que lo utilice. Cambie el valor **Se puede buscar** en las definiciones del campo y la relación entre entidades de forma que no aparezcan en la búsqueda avanzada. 
  
<a name="BKMK_LimitationsOnMetadata"></a>   

## <a name="limitations-on-creating-metadata-items"></a>Limitaciones para crear elementos de metadatos  

Hay un límite en el número de entidades que puede crear. Puede encontrar información sobre el número máximo en la página **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Administración** > **Recursos en uso**. Si necesita más entidades personalizadas, póngase en contacto con el soporte técnico. Este límite superior se puede ajustar.  
  
Dentro de cada entidad hay un límite superior en el número de campos que puede crear. Este límite se basa en las limitaciones técnicas de la cantidad de datos que se pueden almacenar en una fila de una tabla de la base de datos. Es difícil proporcionar un número específico porque para cada tipo de campo puede usar una cantidad de espacio diferente. El límite superior depende del espacio total usado por todos los campos de la entidad.  
  
La mayoría de las personas no crean suficientes campos personalizados para alcanzar el límite, pero si tiene previsto agregar cientos de campos personalizados a una entidad, debe considerar si este es el mejor diseño. ¿Todos los campos que prevé agregar describen las propiedades de un registro de dicha entidad? ¿Tiene previsto que los usuarios que utilicen su organización puedan administrar un formulario que incluya un número tan elevado de campos? El número de campos que agrega a un del formulario incrementa la cantidad de datos que deberán transferirse cada vez que un registro se modifique, lo que afectará al rendimiento del sistema. Tenga en cuenta estos factores cuando esté agregando campos personalizados a una entidad.  
  
Los campos de conjunto de opciones ofrecen un conjunto de opciones que se mostrará en un control desplegable en un formulario o un control de lista desplegable al usar la búsqueda avanzada. Su entorno puede admitir miles de opciones en un conjunto de opciones, pero no debería considerar esta característica como el límite superior. Los estudios de capacidad de uso demuestran que los usuarios tienen problemas para utilizar un sistema donde un control desplegable proporciona un gran número de opciones. Utilice el campo de conjunto de opciones para definir categorías de datos. No use los campos de conjunto de opciones para seleccionar categorías que representen realmente elementos de datos diferentes. Por ejemplo, en lugar de mantener un campo de conjunto de opciones que almacene cientos de fabricantes posibles de un tipo de equipamiento, considere crear una entidad que almacene referencias a cada fabricante y use un campo de búsqueda en lugar de un conjunto de opciones.  
  
## <a name="next-steps"></a>Pasos siguientes 

[Crear o editar entidades (tipos de registros)](create-edit-entities.md)<br />
[Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)

