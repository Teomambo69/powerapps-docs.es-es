---
title: Apertura de los datos de entidad en Excel | Microsoft Docs
description: Abra los datos de la entidad en Excel para la visualización y edición interactivas.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: 8dbf6088104270d9251b70eec9adf0642de2f879
ms.sourcegitcommit: f236364ecb06dd86244cd9a607c31e0d716912e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="open-entity-data-in-excel"></a>Abrir los datos de la entidad en Excel
Al abrir los datos de la entidad en Microsoft Excel, estos se pueden ver y editar de forma rápida y sencilla mediante el complemento de Excel de Microsoft PowerApps. Este complemento requiere Microsoft Excel 2016.

![Complemento de Excel](./media/data-platform-cds-excel-addin/ExcelAddin.png "Complemento de Excel de PowerApps")

## <a name="open-entity-data-in-excel"></a>Abrir los datos de la entidad en Excel
1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda. Se muestran todas las entidades.
2. Haga clic en los puntos suspensivos (...) que hay a la derecha de la entidad que le interesa.
3. Haga clic en **Abrir en Excel** y abra el libro que se genera. Dicho libro generado información de enlace de la entidad, un puntero a su entorno y un puntero para el complemento de Excel de PowerApps.  
4. En Excel, haga clic en **Habilitar edición** para habilitar la ejecución del complemento de Excel de PowerApps. El complemento de Excel se ejecutará en un panel de la derecha de la ventana de Excel.
5. Si es la primera vez que ejecuta el complemento, de Excel de PowerApps, haga clic en **Confiar en este complemento** para permitir que se ejecute el complemento de Excel.
6. Si se le solicita que inicie sesión, haga clic en **Inicio de sesión** y hágalo con las mismas credenciales que usó en [powerapps.com](https://web.powerapps.com). El complemento de Excel utilizará un contexto de inicio de sesión anterior e iniciará sesión automáticamente, en caso de que sea posible. Por tanto, compruebe el nombre de usuario en la parte superior derecha del complemento de Excel.

El complemento de Excel lee automáticamente los datos de la entidad que ha seleccionado. Tenga en cuenta que no habrá ningún dato en el libro hasta que el complemento de Excel los lea.

## <a name="view-and-refresh-data-in-excel"></a>Visualizar y actualizar los datos en Excel
Después de que el complemento de Excel lea los datos de la entidad en el libro, se pueden actualizar en cualquier momento, solo es preciso hacer clic en **Actualizar** en el complemento de Excel.

## <a name="edit-data-in-excel"></a>Editar datos en Excel
Para cambiar los datos de la entidad y volver a publicarlos, haga clic en **Publicar** en el complemento de Excel.

Para editar un registro, seleccione una celda en la hoja de cálculo y cambie su valor.

Para agregar un registro nuevo, siga uno de estos pasos:

* Haga clic en cualquier parte en la hoja de cálculo y, después, en **Nuevo** en el complemento de Excel.
* Haga clic en la última fila de la hoja de cálculo y presione la tecla TAB hasta que el cursor pase la última columna de la fila y se cree una fila nueva.
* Haga clic en la fila inmediatamente inferior de la hoja de cálculo y empieza a escribir datos en una celda. Cuando cambia de celda, la hoja de cálculo se expande e incluye la nueva fila.

Para eliminar un, siga uno de estos pasos:

* Haga clic con el botón derecho en el número de fila situado junto a la va a eliminar y, después, haga clic en **Eliminar**.
* Haga clic con el botón derecho en la fila de la hoja de cálculo que va a eliminar y, después, haga clic en **Eliminar** > **Filas de la tabla**.

## <a name="add-or-remove-columns"></a>Agregar o quitar columnas
Puede utilizar el diseñador para ajustar las columnas y entidades que se agregan automáticamente a la hoja de cálculo.

1. Para habilitar el diseñador de orígenes de datos del complemento de Excel, haga clic en el botón **Opciones** (el símbolo de engranaje) y active la casilla **Habilitar diseño**.
2. Haga clic en **Diseño** en el complemento de Excel. Aparecerán todos los orígenes de datos.
3. Junto al origen de datos, haga clic en el botón **Editar** (el símbolo del lápiz).
4. Ajuste la lista del campo **Campos seleccionados** como sea necesario:
   * Para agregar un campo de **Campos disponibles** a **Campos seleccionados**, haga clic en él y, después, en **Agregar**. Como alternativa, haga doble clic en el campo.
   * Para quitar un campo de **Campos seleccionados**, haga clic en él y, después, en **Quitar**. Como alternativa, haga doble clic en el campo.
   * Para cambiar el orden de los campos, haga clic en **Campos seleccionados** y, después, en **Arriba** o **Abajo**.
5. Para aplicar los cambios al origen de datos, haga clic en **Actualizar** y, después, en **Listo** para salir del diseñador. Si ha agregado un campo (columna), haga clic en **Actualizar** para recopilar un conjunto de datos actualizado.

> [!NOTE]
> Asegúrese de incluir siempre el identificador y los campos obligatorios en el libro, ya que, de lo contrario, podría recibir errores al publicar.

> [!NOTE]
> Al agregar campos de búsqueda, asegúrese de agregar tanto el identificador como los campos de visualización.

## <a name="troubleshooting"></a>Solución de problemas
Hay algunos problemas que se pueden resolver mediante algunos pasos sencillos.

* No todas las entidades admiten la edición y creación de nuevos registros, estas entidades se abrirán en Excel y le permiten ver los datos, pero la publicación estará deshabilitada.
* Los campos de búsqueda deben editarse mediante el complemento para garantizar que se hacer referencia al registro correcto; no se admite la actualización de estos campos mediante la opción de copiar y pegar o escribiendo directamente en el campo.


Si aparece algún problema que no se describe aquí, póngase en contacto con nosotros a través de las [páginas de soporte técnico](https://powerapps.microsoft.com/support/).

## <a name="next-steps"></a>Pasos siguientes
* [Administrar campos de una entidad](data-platform-manage-fields.md)
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Generación de una aplicación a partir de Common Data Service for Apps](../canvas-apps/data-platform-create-app.md)
* [Crear una aplicación desde cero mediante una base de datos de Common Data Service for Apps](../canvas-apps/data-platform-create-app-scratch.md)

