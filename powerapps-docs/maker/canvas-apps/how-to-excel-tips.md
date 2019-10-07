---
title: Formato de tablas en Excel | Microsoft Docs
description: Para utilizar datos de Excel en PowerApps, debe dar formato de tabla a los datos. Agregar palabra clave "imagen" en los nombres de columna
author: yifwang
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 164de5c1b2534901563ab888cfd83641dbe5a9c5
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71990031"
---
# <a name="format-a-table-in-excel-and-naming-tips"></a>Dar formato a una tabla en Excel y sugerencias de nomenclatura
En PowerApps, solo puede crear una aplicación de lienzo basada en datos de Excel si tienen formato de tabla. En este artículo se muestra cómo dar formato a una tabla en Excel y se ofrecen algunas sugerencias de asignación de nombres de columnas de Excel.

## <a name="how-to-format-a-table-in-excel"></a>Cómo dar formato a una tabla de Excel
Para convertir los datos en una tabla, seleccione **Dar formato como tabla** en la pestaña **Inicio** de Excel.

![Formato de una tabla de Excel](./media/how-to-excel-tips/format-table.png)

También puede crear una tabla seleccionando **Tabla** en la pestaña **Insertar**.

![Insertar una tabla en Excel](./media/how-to-excel-tips/insert-table.png)

Para que le resulte fácil encontrar la tabla, vaya a **Diseño** en **Herramientas de tabla** y cambie el nombre de la tabla. Resulta práctico asignarle a la tabla un nombre descriptivo, sobre todo si un mismo archivo de Excel contiene varias tablas.

![Cambio de nombre de una tabla en Excel](./media/how-to-excel-tips/rename-table.png)

## <a name="naming-tips-in-excel"></a>Sugerencias de nomenclatura en Excel
Si una columna de la tabla contiene imágenes, incluya "imagen" en el nombre de esa columna. Esta palabra clave enlazará esa columna a un control de imagen en una galería.

![Conectar la tabla de Excel con imágenes](./media/how-to-excel-tips/connect-gallery.png)

## <a name="next-steps"></a>Pasos siguientes
* [Generar una aplicación desde Excel en PowerApps](get-started-create-from-data.md) según una tabla especificada. La aplicación tendrá tres pantallas de forma predeterminada: una para examinar registros, para mostrar detalles acerca de un registro y crear o actualizar un registro.
* [Crear una aplicación desde el principio](get-started-create-from-blank.md) mediante la tabla a la que ha aplicado formato de Excel. Puede crear y personalizar manualmente la aplicación para mostrar, examinar o modificar los datos de la tabla.
