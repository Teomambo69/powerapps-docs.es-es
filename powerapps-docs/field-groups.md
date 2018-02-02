---
title: "Uso de grupos de campos para la creación de aplicaciones | Microsoft Docs"
description: "Use grupos de campos para estandarizar la creación de aplicaciones en la base de datos."
services: powerapps
documentationcenter: na
author: aneesmsft
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/11/2017
ms.author: aneesa
ms.openlocfilehash: d791d04965873c133be85013feb181dc5a1e1bad
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="use-field-groups"></a>Usar grupos de campos
Los grupos de campos proporcionan una manera de agrupar uno o más campos de una entidad. Los grupos de campos pueden acelerar y simplificar la creación y mantenimiento de aplicaciones. Un grupo de campos puede contener uno o varios campos, y un mismo campo puede aparecer en varios grupos de campos. Un campo no puede aparecer más de una vez en un mismo grupo de campos.

Los grupos de campos se almacenan en una entidad y se comparten entre todas las aplicaciones que usan la misma entidad. En cualquier momento dado, varias aplicaciones diferentes pueden usar la misma entidad y grupos de campos de esa entidad. Esta centralización y uso compartido de grupos de campo le ayuda a garantizar la coherencia, ya que un grupo de campos mostrará siempre los mismos campos independientemente de dónde se use. Esto facilita el mantenimiento ya que cualquier cambio en un grupo de campos se reflejará automáticamente en todos los lugares que usan ese grupo de campos. Los grupos de campos ayudan a acelerar el proceso de creación y personalización de aplicaciones ya que el autor de una aplicación trabaja con grupos de campos en lugar de con campos individuales.

## <a name="default-field-groups"></a>Grupos de campos predeterminados
Common Data Service incluye varios grupos de campos predeterminados en entidades. Estos grupos de campos se utilizan en varios lugares para acelerar y facilitar la personalización y creación de aplicaciones.

| Nombre del grupo de campos predeterminado | Descripción |
| --- | --- |
| DefaultList |Se utiliza para mostrar una lista de registros en un formato tabular. |
| DefaultCard |Se utiliza para mostrar una lista de registros en un formato de tarjeta. |
| DefaultDetails |Se utiliza para mostrar los detalles de un registro único en modo vista y edición. |
| DefaultLookup |Se usa para mostrar una búsqueda para seleccionar un registro. |

## <a name="view-a-field-group"></a>Visualización de un grupo de campos
1. Inicie sesión en [powerapps.com](https://web.powerapps.com).
2. Si tiene acceso a más de un entorno, asegúrese de que tiene seleccionado el entorno correcto mediante el selector de entornos de la barra superior.
3. Expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo.
4. En la lista de entidades, haga clic o pulse en la entidad de la que desea ver el grupo de campos.
5. En el encabezado situado por encima de la lista de campos, haga clic o pulse en **Grupos de campos**. Ahora verá todos los grupos de campos que existen actualmente para la entidad.
6. En la lista de grupos de campos, haga clic o pulse en el grupo de campos del que desea ver los detalles.
7. En los detalles del grupo de campos, hay dos listas en paralelo. Una se titula **Campos de entidad** y enumera todos los campos de la entidad. La otra se denomina **Campos del grupo de campos** y enumera los campos incluidos en el grupo de campos.

## <a name="modify-a-field-group"></a>Modificación de un grupo de campos
1. Vea el grupo de campos que desea modificar.
2. Para agregar un campo, haga doble clic en un nombre de campo de la lista **Campos de entidad**. También puede arrastrar y soltar campos de la lista **Campos de entidad** en la lista **Campos del grupo de campos**.
3. Para quitar un grupo de campos, haga clic en la **X** situada junto al nombre de campo de la lista **Campos del grupo de campos**.
4. Pulse o haga clic en el botón **Guardar**.

> [!NOTE]
> La modificación de grupos de campos para [entidades estándar](guided-learning/manage-data.yml#step-2) no se admite actualmente, pero se pueden modificar los grupos de campos para las entidades personalizadas.*

## <a name="creating-a-field-group"></a>Creación de un grupo de campos
Los grupos de campos predeterminados se crean automáticamente cuando se crea una entidad. La creación de grupos de campos adicionales no se admite actualmente.

## <a name="delete-a-field-group"></a>Eliminación de un grupo de campos
La eliminación de un grupo de campos no se admite actualmente.

## <a name="view-and-edit-field-group-data-in-microsoft-excel"></a>Visualización y edición de los datos de un grupo de campos en Microsoft Excel
1. Vea los grupos de campos de la entidad de la que desea examinar los datos.
2. Hay un icono de Excel junto a cada grupo de campos. El icono de Excel solo se habilita si el grupo de campos tiene campos.
3. Haga clic en el icono de Excel para el grupo de campos que desea abrir en Excel. Se genera un libro que contiene la lista de campos de entidad, el complemento de Excel y un puntero a su entorno.
4. Abra el libro generado que proporciona el explorador.
5. Después de abrir el libro, habilite la edición. El complemento de Excel leerá, a continuación, los datos del libro. Para más información, consulte [Abrir los datos de la entidad en Excel](data-platform-interactive-excel.md).

## <a name="field-group-usage"></a>Uso de los grupos de campos
Los grupos de campos predeterminados ayudan a acelerar la creación y personalización de aplicaciones. Algunos lugares donde puede ver actualmente los grupos de campos en acción son:

* **Control de formulario de la entidad**: el control de formulario de la entidad usa los grupos de campos predeterminados para mostrar formularios dinámicos que le ayudan a acelerar el proceso de creación de aplicaciones, a garantizar la coherencia y a facilitar el mantenimiento. Para más información, consulte [Uso del control de formulario de entidad](entity-form-control.md).
* **Control de búsqueda**: si uno de los campos que agregue en la pantalla es una referencia a otra entidad vinculada, el campo se representará como un control de búsqueda (lista desplegable). Cuando un usuario hace clic en el control de búsqueda para seleccionar un registro de la entidad vinculada, los campos que se muestran vienen determinados por el grupo de campos **DefaultLookup** de la entidad vinculada. Solo se utilizan los primeros dos campos del grupo de campos **DefaultLookup**.
* **Creación de una aplicación**: si genera una aplicación eligiendo la opción para crear una aplicación a partir de datos, se crearán automáticamente las pantallas de la entidad que seleccione. El control **Mostrar formulario** de la pantalla **Mostrar** y el control **Editar formulario** de la pantalla **Editar** usan el grupo de campos **DefaultDetails** para determinar qué campos se agregarán de forma predeterminada a esas pantallas.

