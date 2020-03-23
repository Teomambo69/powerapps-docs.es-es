---
title: Creación y edición de relaciones entre entidades uno a varios o varios a uno utilizando el portal de Power Apps | MicrosoftDocs
description: Aprenda a crear relaciones entre entidades de uno a varios o de varios a uno con el portal de Power Apps
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 415b613fbbafa5f3b1b54827a1aa59272cdc4b7d
ms.sourcegitcommit: d98dd90a7dda11f434a13a7f8976459856d6142b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/29/2020
ms.locfileid: "3093836"
---
# <a name="create-and-edit-one-to-many-or-many-to-one-entity-relationships-using-power-apps-portal"></a>Creación y edición de relaciones entre entidades uno a varios o varios a uno utilizando el portal de Power Apps

El [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) proporciona una forma de crear y editar relaciones de 1:N (uno a varios) o N:1 (varios a uno) para Common Data Service.

El portal permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. Más información: 
- [Crear y editar relaciones 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)
- [Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones](create-edit-1n-relationships-solution-explorer.md).

## <a name="view-entity-relationships"></a>Ver relaciones entre entidades

1. En el [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione el modo de diseño **Controlado por modelos** o **Lienzo**.
2. Seleccione **Datos** > **Entidades** y seleccione la entidad que tiene las relaciones que desea ver.
3. Con la pestaña **Relaciones** seleccionada, seleccione las vistas siguientes: 

 |Vista|Descripción|
 |--|--|
 |**Todo**| Muestra todas las relaciones para la entidad|
 |**Personalizada**|Muestra solo relaciones personalizadas para la entidad|
 |**Predeterminado**|Muestra solo relaciones estándar para la entidad|
<!-- TODO: What is the actual difference between All and Default? -->

![Relaciones entre entidades de cuenta](media/view-account-relationships-portal.png)

## <a name="create-relationships"></a>Crear relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), en la barra de comandos, seleccione **Agregar relación** y elija **Varios a uno** o **Uno a varios**.

![Seleccione el tipo de relación](media/add-relationship-menu-portal.png)

> [!NOTE]
> Para obtener información acerca de las relaciones **Varios a varios** consulte [Crear relaciones N:N (varios a varios)](create-edit-nn-relationships.md)

<!-- This may change going forward, but this is the way it is now. #2534972 -->
> [!Important]
> El portal usa terminología diferente que el explorador de soluciones. La **Entidad principal** del explorador de soluciones es la **Entidad actual** en el portal.

Dependiendo de su elección verá:

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
|Escriba|Panel|
|--|--|
|**Varios a uno**|![Panel de relaciones de varios a uno](media/many-to-one-relationship-panel.png)|
|**Uno a varios**|![Panel de relaciones de uno a varios](media/one-to-many-relationship-panel.png)|

Elija la **Entidad relacionada** para la relación que desea crear entre las dos entidades. 

> [!NOTE]
> En cualquier opción, un campo de búsqueda se creará en la entidad *actual*.

Una vez que seleccione la entidad puede editar los detalles de la relación. En este ejemplo, varios registros de entidad de contacto se pueden asociar a una sola cuenta.

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
![Cuenta y contacto de relaciones de uno a varios](media/One-to-many-account-contact.png)

Puede editar los valores predeterminados proporcionados antes de guardar. Seleccione **Más opciones** para ver los valores de **Nombre de relación** y **Descripción del campo de búsqueda**

|Campo|Descripción|
|--|--|
|**Nombre para mostrar del campo de búsqueda**|El texto localizable del campo de búsqueda que se creará en la entidad relacionada.<br />Se puede editar posteriormente.|
|**Nombre de campo de búsqueda**|El nombre del campo de búsqueda que se creará en la entidad relacionada.|
|**Nombre de la relación**|El nombre para la relación que se creará.|
|**Descripción del campo de búsqueda**|Descripción del campo de búsqueda. En aplicaciones basadas en modelos esto se mostrará como información sobre herramientas cuando se mantenga el mouse sobre el campo. <br />Se puede editar posteriormente.|

Puede continuar editando la entidad. Seleccione **Guardar entidad** para crear la relación que ha configurado.

## <a name="edit-relationships"></a>Editar relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione la relación que desea editar.

> [!NOTE]
> Cada relación se puede encontrar en la entidad principal o la entidad relacionada como relación **Varios a uno** o **Uno a varios** . Aunque puede ser editada en ambos lugares, es la misma relación.
>
> El editor de una solución administrada puede evitar algunas personalizaciones de relaciones que forman parte de la solución.

Los únicos campos que puede editar son **Nombre para mostrar del campo de búsqueda** y **Descripción del campo de búsqueda**. Estos también se pueden editar en las propiedades del campo de búsqueda en la entidad relacionada. Más información: [Editar un campo](create-edit-field-portal.md#edit-a-field)

## <a name="delete-relationships"></a>Eliminar relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione la relación que desea eliminar.

![Eliminar relación entre entidades](media/delete-entity-relationship-portal.png)

Puede usar el comando **Eliminar relación** de la barra de comandos o del menú del contexto contextual de la fila al hacer clic en los puntos suspensivos (**...**).

Al eliminar la relación se eliminará el campo de búsqueda en la entidad relacionada.

> [!NOTE]
> No podrá eliminar una relación que tenga dependencias. Por ejemplo, si ha agregado el campo de búsqueda a un formulario para la entidad relacionada, debe quitar el campo del formulario antes de eliminar la relación.

### <a name="see-also"></a>Vea también

[Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)<br />
[Crear y editar relaciones 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)<br />
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones](create-edit-1n-relationships-solution-explorer.md)<br />
[Editar un campo](create-edit-field-portal.md#edit-a-field)
