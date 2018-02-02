---
title: "Relaciones de entidad mediante un campo de búsqueda | Microsoft Docs"
description: "Cree una relación entre entidades mediante un campo de búsqueda."
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: kfend
ms.openlocfilehash: 21f33f8810b545b11f611b86261227c9443be5de
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="build-a-relationship-between-entities"></a>Crear una relación entre entidades
A menudo, los datos de una entidad se relacionan con los datos de otra entidad. Por ejemplo, podría tener una entidad **Clientes** y otra **Pedidos**, y la entidad **Pedidos** podría tener una relación de búsqueda con la entidad **Clientes** para mostrar qué cliente realizó el pedido. Puede usar un campo de búsqueda para mostrar los datos de la entidad **Clientes** para el cliente que realizó el pedido. Para más información, consulte [Entity relationships and lookup fields](https://docs.microsoft.com/en-us/common-data-service/entity-reference/relationships) (Relaciones de entidad y campos de búsqueda).

## <a name="define-a-relationship"></a>Definir una relación
Puede crear varios tipos de relaciones de una entidad a otra (o entre una entidad y ella misma). Cada entidad puede tener una relación con más de una entidad, y cada entidad puede tener más de una relación con otra entidad. Algunos tipos de relación comunes son:

* **Normal**: este tipo de relación existe entre dos entidades.
* **Auto**: este tipo de relación existe entre una entidad y ella misma.
* **Uno a uno**: en este tipo de relación, cada registro de la entidad A se corresponde solo con un registro de la entidad B y viceversa. La versión actual de Common Data Service no admite este tipo de relación para las entidades personalizadas.
* **Uno a varios**: en este tipo de relación, cada registro de la entidad A se corresponde con más de un registro en la entidad B, pero cada registro de la entidad B solo se corresponde con un registro de la entidad A.
* **Varios a varios**: en este tipo de relación, cada registro de la entidad A se corresponde con más de un registro de la entidad B y viceversa. La versión actual de Common Data Service no admite este tipo de relación.

## <a name="add-a-lookup-relation"></a>Agregar una relación de búsqueda
Para agregar una relación de búsqueda a una entidad, cree una relación en la pestaña **Relaciones** y especifique la entidad con la que desea crear una relación.

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo.
2. En la lista de entidades, haga clic o pulse en una entidad para mostrar sus campos. Para filtrar la lista, escriba uno o varios caracteres en la barra de búsqueda, encima de la lista.
3. Cerca de la parte superior de la pantalla, pulse o haga clic en **Relaciones**. En esta pestaña se muestran todas las relaciones de la entidad. Haga clic en **Nueva relación**.
4. En la página **Crear relación**, especifique la entidad relacionada con la que desea crear una relación y especifique el nombre y el nombre para mostrar de la relación.
5. Haga clic o pulse en **Guardar** para confirmar los cambios. Se creará automáticamente un campo de búsqueda con el mismo nombre.

## <a name="use-a-lookup-field-in-an-app"></a>Usar un campo de búsqueda en una aplicación
Si [crea una aplicación automáticamente](data-platform-create-app.md) a partir de una entidad que contiene un campo de búsqueda, aparece como control **Lista desplegable** que contiene los datos del campo **Clave principal** de la entidad a la que se hace referencia en estado contraído. Para ver dos campos en la lista desplegable cuando se expanda, debe agregar el campo PrimaryId y un segundo campo de su elección al grupo de campos **Búsqueda predeterminada** de la entidad relacionada de la relación de búsqueda.

## <a name="delete-a-record-with-a-lookup-relation"></a>Eliminar un registro con una relación de búsqueda
Si la entidad A tiene una relación de búsqueda con la entidad B:

* Puede eliminar cualquier registro de la entidad A sin restricciones.
* Si un registro de la entidad B se corresponde con uno o más registros de la entidad A, debe eliminar todos los registros correspondientes en la entidad A antes de poder eliminar el registro de la entidad B.

> [!NOTE]
> Si la entidad B es estándar con una relación principal con la entidad A y elimina un registro de la entidad A, también se eliminan todos los registros correspondientes de la entidad B.

Para obtener información acerca de cómo eliminar un campo, consulte [Administrar campos](data-platform-manage-fields.md).

## <a name="next-steps"></a>Pasos siguientes
* [Generate an app by using a Common Data Service database](data-platform-create-app.md) (Generar una aplicación mediante una base de datos de Common Data Service)
* [Create an app from scratch using a Common Data Service database](data-platform-create-app-scratch.md) (Crear una aplicación desde cero mediante una base de datos de Common Data Service)

