---
title: "Creación de listas desplegables personalizadas | Microsoft Docs"
description: Cree una lista desplegable.
services: powerapps
documentationcenter: na
author: pvillads
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/09/2017
ms.author: kfend
ms.openlocfilehash: bfb0ae0d20bb0fc10f1a8f59e97e43116b58d380
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="create-custom-picklists"></a>Crear listas desplegables personalizadas
Ahora es posible crear listas desplegables propias, además de las que están disponibles desde el principio. Las listas desplegables, que básicamente son listas con nombre de elementos que incluyen un nombre y descripciones, son un concepto simple. Cuando se representan los campos de lista desplegable, aparece un menú desplegable que contiene los nombres para mostrar de los elementos. 

Las listas desplegables se agregan mediante el elemento de menú **Listas desplegables** en la pestaña **Common Data Service**, bajo el menú **Entidades**. Haga clic en el menú para ver todas las listas desplegables que están definidas actualmente en su entorno. Ya hay definidas varias listas desplegables de uso frecuente; las puede identificar fácilmente por su tipo, **Estándar**. Las que cree personalmente son del tipo **Personalizado**.

1. Para crear una lista desplegable, en la parte superior de la página, haga clic en **Nueva lista desplegable**. En la página que se abre, defina la lista desplegable con el nombre, el nombre para mostrar y una descripción.
   **Importante:** no se puede cambiar el nombre de la lista desplegable una vez creada. Hay algunos requisitos para el nombre de la lista desplegable. Debe ser simple y no puede contener caracteres especiales. Además, solo puede tener una lista desplegable con un nombre concreto. Si intenta crear otra con el mismo nombre, recibirá un error. Estas restricciones no son aplicables al valor de **Nombre para mostrar**.
   
    En este tema, se creará una lista desplegable que sirve para elegir un modo de transporte.
2. Asigne a la lista desplegable el nombre **Transporte** y agregue la información a los campos obligatorios.
3. Haga clic en **Siguiente** y, en la siguiente página, proporcione los distintos elementos de la lista desplegable; en este ejemplo, se trata de proveedores de transporte. Cuando se abre la página, verá que ya se ha creado un solo elemento. Actualice el elemento de línea con la información adecuada para la lista desplegable que está creando. La edición se lleva a cabo en la línea. No hay ninguna página independiente para cada elemento de lista desplegable. Haga clic en el campo **Nuevo elemento** para agregar el primer elemento. Siempre que necesite un nuevo elemento de lista desplegable, haga clic en **Agregar elemento** en la parte superior derecha de la pantalla para agregar una nueva fila. 

Para eliminar un elemento, haga clic en el icono de papelera al final de cada línea de elemento. Cuando haya agregado todos los elementos necesarios, haga clic en **Crear** para crear la lista y enviarla al servidor. Verá la lista desplegable agregada a la lista de listas desplegables existentes.

Ahora puede usarla para definir campos en las entidades al agregar un tipo de campo **Lista desplegable** y después usar el valor de **Nombre para mostrar** en el panel **Propiedades** para el campo. 

