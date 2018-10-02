---
title: Crear relaciones entre entidades de varios a varios en Common Data Service para aplicaciones mediante el portal PowerApps | MicrosoftDocs
description: Aprender a crear relaciones de varios a varios
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
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-many-to-many-entity-relationships-in-common-data-service-for-apps-using-powerapps-portal"></a>Crear relaciones entre entidades de varios a varios en Common Data Service para aplicaciones mediante el portal PowerApps

El [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) proporciona una forma de crear y editar relaciones entre entidades de varios a varios para Common Data Service para aplicaciones.

El portal permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. Más información: 
- [Crear relaciones entre entidades N:N (varios a varios)](create-edit-nn-relationships.md)
- [Crear relaciones entre entidades N:N (varios a varios) en Common Data Service para aplicaciones mediante el explorador de soluciones](create-edit-nn-relationships-solution-explorer.md)

## <a name="view-many-to-many-entity-relationships"></a>Ver relaciones entre entidades de varios a varios

1. En el [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione el modo de diseño **Basadas en modelos** o **Lienzo**.
2. Seleccione **Datos** > **Entidades** y seleccione la entidad que tiene las relaciones que desea ver.
3. Con la pestaña **Relaciones** seleccionada, seleccione las vistas siguientes: 

 |Vista|Descripción|
 |--|--|
 |**Todo**| Muestra todas las relaciones para la entidad|
 |**Personalizada**|Muestra solo relaciones personalizadas para la entidad|
 |**Predeterminado**|Muestra solo relaciones estándar para la entidad|
<!-- TODO: What is the actual difference between All and Default? -->

![Relaciones entre entidades de cuenta](media/view-account-relationships-portal.png)

Las relaciones de varios a varios tendrán un **Tipo de relación** de **Varios a varios**.

> [!NOTE]
> La entidad que ve puede no tener ninguna relación de **Varios a varios**.

## <a name="create-relationships"></a>Crear relaciones

Mientras ve [relaciones entre entidades](#view-many-to-many-entity-relationships), en la barra de comandos, seleccione **Agregar relación** y elija **Varios a varios**.

![Seleccione el tipo de relación](media/add-relationship-menu-portal.png)

En el panel **Varios a varios**, elija la entidad que desea relacionar con la entidad actual.

![Panel de varios a varios con la entidad de cuenta seleccionada](media/many-to-many-panel-1.png)

Seleccione **Más opciones** para ver los campos **Nombre de relación** y **Nombre de entidad de relación**.

![Panel de varios a varios con Más opciones seleccionado](media/many-to-many-panel-2.png)

Los valores de estos campos se generan en función de las entidades elegidas.

> [!NOTE]
> Si crea más de una relación de **Varios a varios** con las mismas dos entidades, tendrá que editar los campos **Nombre de la relación** y **Nombre de entidad de relación** generados de modo que sean únicos.

Seleccione **Aceptar** para cerrar el panel **Varios a varios**. Se creará la relación al guardar los cambios en la entidad. 

Una vez guardados, no se puede cambiar nada mediante el [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). Para editar las propiedades de la relación para aplicaciones basadas en modelos, utilice el [explorador de soluciones](create-edit-nn-relationships-solution-explorer.md).

## <a name="delete-relationships"></a>Eliminar relaciones

Mientras [ve relaciones entre entidades](#view-many-to-many-entity-relationships), seleccione la relación que desea eliminar.

![Eliminar relación entre entidades](media/delete-entity-relationship-portal.png)

Puede usar el comando **Eliminar relación** de la barra de comandos o del menú del contexto contextual de la fila al seleccionar los puntos suspensivos (**...**).

Al eliminar la relación de varios a varios se eliminará la entidad de relación creada. Se perderán a todas las entidades de conexión de datos que usen la relación.

### <a name="see-also"></a>Vea también

[Crear relaciones entre entidades N:N (varios a varios)](create-edit-nn-relationships.md)<br />
[Crear relaciones entre entidades N:N (varios a varios) en Common Data Service para aplicaciones mediante el explorador de soluciones](create-edit-nn-relationships-solution-explorer.md)
