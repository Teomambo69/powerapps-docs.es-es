---
title: Crear o editar una vista de aplicación controlada por modelos en Power Apps | MicrosoftDocs
description: Aprenda a crear o editar una vista
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0835e35f5815e7704cfe3d0de24ad4429600512b
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868795"
---
# <a name="understand-model-driven-app-views"></a>Conocer las vistas de las aplicaciones controladas por modelos

<a name="BKMK_CreatingAndEditingViews"></a>   

Con las aplicaciones de Power Apps, utilice vistas para definir cómo se muestra una lista de registros para una entidad específica en la aplicación. Las vistas definen:

- Las columnas que aparecen
- Qué ancho debe tener cada columna
- Cómo debe ordenarse la lista de registros de forma predeterminada
- Qué filtros predeterminados se deben aplicar para limitar los registros que aparecerán en la lista

Una lista desplegable de vistas con frecuencia se muestra en la aplicación para que la gente tiene distintas opciones para vistas de datos de la entidad.

Los registros que están visibles en vistas individuales se muestran en una lista, a veces denominada cuadrícula, que a menudo proporciona opciones para que los usuarios puedan cambiar el orden predeterminado, el ancho de columna, y filtros para ver más fácilmente los datos importantes para ellos. Las vistas definen también el origen de datos para los gráficos que se usan en la aplicación.  
  
## <a name="types-of-views"></a>Tipos de vistas  
  
Existen tres tipos de vistas: *personales*, del *sistema* y *públicas*.

Este tema aborda cómo los administradores y personalizadores del sistema trabajan con vistas del sistema y públicas. 
  
### <a name="personal-views"></a>Vistas personales  
  
 Usted y cualquiera que tenga al menos el nivel de acceso Usuario a las acciones de la entidad Vista guardada también pueden crear vistas personales. Como administrador del sistema, usted puede modificar el nivel de acceso de cada acción en el rol de seguridad para controlar la profundidad a la que los usuarios pueden crear, leer, escribir, eliminar, asignar o compartir vistas personales.

Las vistas personales son propiedad de personas individuales y debido a su acceso predeterminado de nivel de usuario, solo son visibles para esas personas o cualquiera que hayan elegido para compartir sus vistas personales. Puede crear vistas personales guardando una consulta que defina mediante Búsqueda avanzada o mediante las opciones Guardar filtros como vistas nuevas y Guardar filtros en la vista actual en la lista de vistas. Estas vistas suelen incluirse en la parte inferior de las listas de vistas del sistema o públicas que estén disponibles en la aplicación. Aunque puede crear una vista personal nueva basada en una vista del sistema o pública, no puede crear una vista del sistema o pública basada en una vista personal.
  
### <a name="system-views"></a>Vistas del sistema
Como administrador o personalizador del sistema, puede editar vistas del sistema. Las vistas del sistema son vistas especiales de las que depende la aplicación, que existen para entidades del sistema o se crean automáticamente cuando se crean entidades personalizadas. Estas vistas tienen finalidades específicas y algunas funcionalidades adicionales. 


|Vistas del sistema  |Descripción  |
|---------|---------|
|Búsqueda rápida     | La vista predeterminada que se usa cuando se realizan búsquedas mediante Búsqueda rápida. Esta vista también define los campos en los que se busca al usar las capacidades de búsqueda de las vistas de Búsqueda rápida y Búsqueda.        |
|Búsqueda avanzada     |  La vista predeterminada usada para mostrar los resultados cuando se utiliza Búsqueda avanzada. Esta vista también define las columnas que se usan de forma predeterminada cuando se crean nuevas vistas ni vistas personales o públicas personalizadas sin definir una vista para usar como plantilla.       |
|Asociadas     |  La vista predeterminada que muestra las entidades relacionadas para un registro.       |
|Búsqueda     | La vista que ve al seleccionar un registro para definir para un campo de búsqueda.        |

Estas vistas no aparecen en el selector de la vista y no puede usarlas en sublistas en un formulario o como una lista en un panel. No puede eliminar o desactivar estas vistas. Más información: [Quitar vistas](remove-views.md)

Las vistas del sistema son propiedad de la organización, por lo que todos puedan verlas. Por ejemplo, todos tienen acceso a nivel de organización a registros de lectura para la entidad Vista (savedquery). Estas vistas están asociadas con entidades específicas y son visibles en el explorador de soluciones. Puede incluir estas vistas en soluciones porque están asociadas con la entidad.

### <a name="public-views"></a>Vistas públicas

Las vistas públicas son vistas de uso general que puede personalizar como desee. Estas vistas están disponibles en el selector de vistas y puede utilizarlas en subcuadrículas en un formulario o como lista en un panel. Algunas vistas públicas existen de forma predeterminada para entidades del sistema y para cualquier entidad personalizada. Por ejemplo, al crear una nueva entidad personalizada, tendrá la siguiente combinación de vistas públicas y del sistema.


|Nombre  |Escriba  |
|---------|---------|
|*Nombre plural de entidad* activo     |  Pública       |
|*Nombre plural de entidad* inactivo    |  Pública       |
|Búsqueda rápida de *nombre plural de entidad* activa     | Búsqueda rápida        |
|Vista de búsqueda avanzada de *nombre de entidad*     | Búsqueda avanzada        |
|Vista asociada de *nombre de entidad*     |  Asociadas       |
|Vista de búsqueda de *nombre de entidad*     | Búsqueda        |

Puede crear vistas públicas personalizadas. Puede eliminar cualquier vista pública personalizada creada en una solución no administrada. No puede eliminar ninguna vista pública definida por el sistema. Las vistas públicas personalizadas agregadas importando una solución administrada pueden tener propiedades administradas establecidas que pueden impedir que se eliminen, excepto desinstalando la solución administrada.

## <a name="places-where-you-can-access-the-view-editor-to-create-or-edit-views"></a>Lugares donde puede acceder al editor de vistas para crear o editar vistas

- Sitio de Power Apps: puede acceder al diseñador de vistas en el área **Controlado por modelos** > pestaña **Datos** > **Entidades** > **Vista**. Abra una vista existente o cree una nueva. Más información: [Crear o editar una vista](create-and-edit-views.md)
- Diseñador de aplicaciones: si está trabajando con una aplicación, puede que desee usar el diseñador de aplicaciones, que ofrece una IU intuitiva y simple con capacidades de arrastrar y colocar para las vistas creadas. Más información: [Tutorial: Crear y editar vistas públicas o del sistema usando el diseñador de aplicaciones](create-edit-views-app-designer.md)
- Explorador de soluciones: si ya tiene experiencia con Dynamics 365, es posible que desee utilizar el explorador de soluciones. Más información: [Navegar a áreas de creación y personalización avanzadas de aplicaciones](advanced-navigation.md#solution-explorer)
 
## <a name="customize-views"></a>Personalizar vistas

Como personalizador del sistema, puede personalizar las vistas a través de controles haciendo que las cuadrículas (listas) sean editables y compatibles para Interfaz unificada. Se usan los controles siguientes:

- Cuadrícula editable Permite a los usuarios editar en línea con gran detalle directamente desde cuadrículas y subcuadrículas tanto si usan una aplicación web, tableta o teléfono. Más información: [Crear cuadrículas editables mediante el control personalizado Cuadrículas editables](make-grids-lists-editable-custom-control.md)
- Cuadrícula de solo lectura: Ofrece una experiencia de visualización e interacción óptima para cualquier tamaño de pantalla u orientación, como móviles y tabletas, usando principios de diseño receptivos. Más información: [Especificar propiedades para aplicaciones de Interfaz unificada](specify-properties-for-unified-interface-apps.md)

## <a name="next-steps"></a>Pasos siguientes

[Creación o edición de vistas](create-and-edit-views.md)
