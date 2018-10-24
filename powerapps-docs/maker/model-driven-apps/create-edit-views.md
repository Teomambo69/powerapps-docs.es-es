---
title: Creación o edición de una vista de aplicación controlada por modelos en PowerApps | Microsoft Docs
description: Aprenda a crear o editar una vista.
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
ms.openlocfilehash: 215f927b68decac864a2f1b667f64a7649827682
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39702837"
---
# <a name="understand-model-driven-app-views"></a>Comprensión de las vistas de la aplicación controlada por modelos

<a name="BKMK_CreatingAndEditingViews"></a>   

Con las aplicaciones de PowerApps, utilice las vistas para definir cómo se muestra una lista de registros para una entidad específica en la aplicación. Una vista define:

- Las columnas para mostrar
- El ancho que debe tener cada columna
- Cómo se debe ordenar la lista de registros de forma predeterminada
- Qué filtros predeterminados deben aplicarse para restringir los registros que aparecerán en la lista

Una lista desplegable de vistas se muestra con frecuencia en la aplicación para que las personas tengan opciones para diferentes vistas de los datos de la entidad.

Los registros que son visibles en vistas individuales se muestran en una lista, a veces llamada cuadrícula, que con frecuencia proporciona opciones para que los usuarios puedan cambiar la ordenación predeterminada, los anchos de columna y los filtros para ver más fácilmente los datos que son importantes para ellos. Las vistas también definen el origen de datos de los gráficos que se utilizan en la aplicación.  
  
## <a name="types-of-views"></a>Tipos de vistas  
  
Hay tres tipos de vistas: *personales*, *del sistema* y *públicas*.

En este tema se trata cómo trabajan los administradores de sistema y los personalizadores de sistema con vistas públicas y del sistema. 
  
### <a name="personal-views"></a>Vistas personales  
  
 Usted y cualquier otro usuario que tenga al menos acceso a nivel de usuario a las acciones de la entidad Saved View también puede crear vistas personales. Como administrador del sistema, puede modificar el nivel de acceso para cada acción del rol de seguridad para controlar la profundidad a la que los usuarios pueden crear, leer, escribir, eliminar, asignar o compartir vistas personales.

Las vistas personales son propiedad de individuos y, debido a su acceso predeterminado al nivel de usuario, solo son visibles para ese usuario o cualquier otro usuario con el que elijan compartir sus vistas personales. Puede crear vistas personales al guardar una consulta que defina mediante la búsqueda avanzada o con las opciones de guardar filtros como nuevas vistas y de guardar filtros en la vista actual de la lista de vistas. Estas vistas se incluyen normalmente en la parte inferior de las listas de vistas del sistema o públicas que están disponibles en la aplicación. Aunque puede crear una nueva vista personal basada en una vista pública o de sistema, no puede crear una vista pública o de sistema basada en una vista personal.
  
### <a name="system-views"></a>Vistas del sistema
Como administrador del sistema o personalizador del sistema, puede modificar las vistas del sistema. Las vistas del sistema son vistas especiales de las que depende la aplicación, que existen para las entidades del sistema o que se crean automáticamente cuando se crean entidades personalizadas. Estas vistas tienen propósitos específicos y algunas funcionalidades adicionales. 


|Vistas del sistema  |Descripción  |
|---------|---------|
|Búsqueda rápida     | La vista predeterminada que se utiliza cuando las búsquedas se realizan con Búsqueda rápida. Esta vista también define qué campos se buscan cuando se utilizan las funcionalidades de búsqueda de las vistas Búsqueda rápida y Búsqueda.        |
|Búsqueda avanzada     |  La vista predeterminada utilizada para mostrar los resultados cuando se utiliza la búsqueda avanzada. Esta vista también define las columnas que se utilizan de forma predeterminada cuando se crean nuevas vistas públicas personalizadas o vistas personales sin definir una vista para utilizar como plantilla.       |
|Asociado     |  La vista predeterminada que enumera las entidades relacionadas para un registro.       |
|Búsqueda     | La vista que se ve cuando se selecciona un registro para establecer un campo de búsqueda.        |

Estas vistas no se muestran en el selector de vistas y no se pueden utilizar en sublistas en un formulario o como una lista en un panel. No se puede eliminar o desactivar estas vistas. Para más información: [Eliminar o desactivar una vista](remove-views.md)

Las vistas del sistema son propiedad de la organización para que todos puedan verlas. Por ejemplo, todo el mundo tiene acceso a nivel de organización para leer los registros de la entidad View (savedquery). Estas vistas están asociadas a entidades específicas y son visibles dentro del explorador de soluciones. Puede incluir estas vistas en las soluciones ya que están asociadas con la entidad.

### <a name="public-views"></a>Vistas públicas

Las vistas públicas son vistas de uso general que se pueden personalizar según estime oportuno. Estas vistas están disponibles en el selector de vistas y no se pueden utilizar en subcuadrículas en un formulario o como una lista en un panel. Algunas vistas públicas existen de forma predeterminada para las entidades del sistema y para cualquier entidad personalizada. Por ejemplo, cuando cree una nueva entidad personalizada, tendrá la siguiente combinación de vistas pública y del sistema.


|Nombre  |Tipo  |
|---------|---------|
|*Nombre plural de la entidad* activos     |  Público       |
|*Nombre plural de la entidad* inactivos    |  Público       |
|Búsqueda rápida de *nombre plural de la entidad* activos     | Búsqueda rápida        |
|Vista de búsqueda avanzada de *nombre de la entidad*     | Búsqueda avanzada        |
|Vista asociada de *nombre de la entidad*     |  Asociado       |
|Vista de búsqueda de *nombre de la entidad*     | Búsqueda        |

Puede crear vistas públicas personalizadas. Puede eliminar cualquier vista pública personalizada que cree en una solución no administrada. No puede eliminar ninguna vista pública definida por el sistema. Las vistas públicas personalizadas que se agregan al importar una solución administrada pueden tener un conjunto de propiedades administradas que pueden evitar que se eliminen, excepto mediante la desinstalación de la solución administrada.

## <a name="places-where-you-can-access-the-view-editor-to-create-or-edit-views"></a>Lugares donde puede acceder al editor de vistas para crear o editar vistas

- Sitio de PowerApps: puede acceder al diseñador de vistas en el área **controlada por modelos** > pestaña **Datos** > **Entidades** > **Vista**. Abra una vista existente o cree una nueva. Más información: [Crear o editar una vista](create-and-edit-views.md)
- Diseñador de aplicaciones: si está trabajando en una aplicación, es posible que desee utilizar el Diseñador de aplicaciones, que proporciona una interfaz de usuario simple e intuitiva con funciones de arrastrar y colocar para las vistas creadas. Más información: [Tutorial: Create and edit public or system views by using the app designer](create-edit-views-app-designer.md) (Tutorial: Creación y edición de vistas públicas o del sistema mediante el diseñador de aplicaciones)
- Explorador de soluciones: si ya tiene experiencia con Dynamics 365, es posible que desee usar el Explorador de soluciones. Más información: [Navigate to advanced model-driven app making and customization areas](advanced-navigation.md#solution-explorer) (Navegación a las áreas de personalización y creación de aplicaciones basadas en modelos)
 
## <a name="customize-views"></a>Personalizar vistas

Como personalizador del sistema, puede personalizar las vistas mediante controles para que las cuadrículas (listas) se puedan editar y sean compatibles con la interfaz unificada. Se utilizan los siguientes controles:

- Cuadrícula editable: permite a los usuarios realizar una edición enriquecida en línea directamente desde las cuadrículas y subcuadrículas, ya sea que estén utilizando una aplicación web, una tableta o un teléfono. Más información: [Make model-driven app grids (lists) editable using the Editable Grid custom control](make-grids-lists-editable-custom-control.md) (Conversión de las cuadrículas (listas) de aplicaciones controladas por modelos en editables mediante el control personalizado Cuadrícula editable)
- Cuadrícula de solo lectura: proporciona a los usuarios una experiencia de visualización e interacción óptima para cualquier tamaño de pantalla u orientación, como móviles y tabletas, mediante el uso de principios de diseño sensibles. Más información: [Specify properties for model-driven unified interface apps](specify-properties-for-unified-interface-apps.md) (Especificación de propiedades de aplicaciones de interfaz unificada controladas por modelos)

## <a name="next-steps"></a>Pasos siguientes

[Comprender las vistas](create-and-edit-views.md)
