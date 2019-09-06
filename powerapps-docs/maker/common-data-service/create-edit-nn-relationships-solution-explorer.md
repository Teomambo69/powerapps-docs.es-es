---
title: 'Crear relaciones entre entidades N:N (varios a varios) en Common Data Service mediante el explorador de soluciones | MicrosoftDocs'
description: Aprender a crear relaciones de varios a varios
ms.custom: ''
ms.date: 05/29/2018
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
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-nn-many-to-many-entity-relationships-in-common-data-service-using-solution-explorer"></a>Crear relaciones entre entidades N:N (varios a varios) en Common Data Service mediante el explorador de soluciones

El explorador de soluciones proporciona una forma de crear y editar relaciones N:N (varios a varios) para Common Data Service.

El [portal PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. Más información:
- [Crear relaciones entre entidades de varios a varios (N:N)](create-edit-nn-relationships.md)
- [Crear relaciones varios a varios entre entidades en Common Data Service con el portal PowerApps](create-edit-nn-relationships-portal.md)

  
## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier relación personalizada que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entity-relationships"></a>Ver relaciones entre entidades

En el explorador de soluciones, expanda **Entidades** y seleccione una entidad. En esa entidad, seleccione **Relaciones N:N**.

![Ver relaciones entre entidades N:N](media/view-nn-entity-relationships-solution-explorer.png)

## <a name="create-relationships"></a>Crear relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione **Nueva relación de varios a varios** de la barra de comandos.

> [!NOTE]
> Si el comando no está disponible, la entidad no es válida para crear una relación personalizada.

![Formulario Nueva relación de varios a varios](media/new-nn-entity-relationship-form-solution-explorer.png)

En el grupo **Otra entidad**, en el campo **Nombre de entidad**, elija la entidad con la que desea crear la relación. De este modo se rellenarán los campos **Nombre** y **Nombre de entidad de relación** en el grupo **Definición de relación**.

Puede hacer clic en ![Botón Guardar relación entre entidades](media/save-entity-icon-solution-explorer.png) para guardar la entidad y para continuar editando. Más información: [Editar relaciones](#edit-relationships)

> [!NOTE]
> Si los valores de **Nombre** o **Nombre de entidad de relación** ya existen en el sistema se mostrará un error cuando guarde. Edite los valores de modo que sean únicos y vuelva a intentarlo.

## <a name="edit-relationships"></a>Editar relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione la entidad que desea editar. 

> [!NOTE]
> El editor de una solución administrada puede evitar personalizaciones de relaciones que forman parte de la solución.

Las siguientes propiedades de relación entre entidades pueden editarse una vez creada la relación.

> [!IMPORTANT]
> Después de editar estas propiedades debe publicar personalizaciones para que surtan efecto en aplicaciones basadas en modelos.

### <a name="edit-display-options"></a>Editar opciones de visualización

Para **Entidad actual** y **Otra entidad**, puede editar los campos de opción de visualización que controlan cómo se muestran las entidades relacionadas para las aplicaciones basadas en modelos.

|Campo|Descripción|
|--|--|
|**Opción de visualización**|Cómo se debe mostrar la lista de entidades relacionadas. Más información: [Opciones de visualización](#display-options)|
|**Etiqueta personalizada**|Especifique el texto localizable que se usará en lugar del nombre plural cuando seleccione **Usar etiqueta personalizada** como **Opción de visualización**.|
|**Área de visualización**|Seleccione una de las agrupaciones disponibles para mostrar esta lista. Las opciones disponibles son: **Detalles** (para el grupo *Común* ), **Marketing**, **Ventas** y **Servicio**. |
|**Orden de visualización**|Controla dónde se incluirá el elemento de navegación en el área de visualización seleccionada. El intervalo de números admitidos empieza con 10.000. Los elementos del panel de navegación con un valor inferior aparecerán encima de otras relaciones con un valor más alto.|

<!-- TODO: Not sure whether Display Area or Display Order are still used anymore. Might only be used in the Outlook client?-->

#### <a name="display-options"></a>Opciones de visualización

Estas son las opciones de visualización disponibles:

|Opción|Descripción|
|--|--|
|**No mostrar**|No muestra las entidades relacionadas para esta relación.|
|**Usar etiqueta personalizada**|Cuando se selecciona esta opción, se habilita el campo **Etiqueta personalizada** para que pueda especificar el texto localizable que se usará en lugar del nombre plural.|
|**Usar nombre plural**|Use el nombre plural para mostrar definido para la entidad relacionada.|

### <a name="searchable"></a>Búsqueda

Puede ocultar relación desde **Búsqueda avanzada** en aplicaciones basadas en modelos estableciendo el campo **Búsqueda** como **No**.

## <a name="delete-relationships"></a>Eliminar relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione la relación entre entidades que desea eliminar y haga clic en el comando ![Eliminar comando](media/delete.gif).

Al eliminar la relación se eliminará la entidad de relación creada. Se perderán a todas las entidades de conexión de datos que usen la relación.

### <a name="see-also"></a>Vea también

[Crear relaciones entre entidades de varios a varios (N:N)](create-edit-nn-relationships.md)<br />
[Crear relaciones varios a varios entre entidades en Common Data Service con el portal PowerApps](create-edit-nn-relationships-portal.md)<br />
[Crear y editar relaciones de entidad de 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)
