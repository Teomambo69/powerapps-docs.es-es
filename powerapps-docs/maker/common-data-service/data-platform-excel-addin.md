---
title: Abrir datos de entidad en Excel | Microsoft Docs
description: Abrir datos de entidad en Excel para la visualización y edición interactivas.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="open-entity-data-in-excel"></a>Abrir datos de entidad en Excel
Al abrir datos de entidad en Microsoft Excel, puede ver y editar datos de forma rápida y sencilla usando el complemento de Excel Microsoft PowerApps. El complemento de Excel PowerApps requiere Microsoft Excel 2016.

![Complemento de Excel](./media/data-platform-cds-excel-addin/ExcelAddin.png "Complemento de Excel PowerApps")

## <a name="open-entity-data-in-excel"></a>Abrir datos de entidad en Excel
1. En [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda. Se muestran todas las entidades.
2. Haga clic en los puntos suspensivos (...) a la derecha de la entidad que le interesa.
3. Haga clic en **Abrir en Excel** y abra el libro generado. Este libro tiene información de enlace para la entidad, un puntero al entorno y un puntero al complemento de Excel PowerApps.  
4. En Excel, haga clic en **Habilitar edición** para habilitar el complemento de Excel PowerApps para que se ejecute. El complemento de Excel se ejecuta en un panel a la derecha de la ventana de Excel.
5. Si esta es la primera vez que ha ejecutado el complemento de Excel PowerApps, haga clic en **Confiar en este complemento** para permitir que el complemento de Excel se ejecute.
6. Si se le solicita iniciar sesión, haga clic en **Iniciar sesión** y, a continuación, inicie sesión con las mismas credenciales que usó en [powerapps.com](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). El complemento de Excel usará un contexto de inicio de sesión anterior y establecerá la conexión, si puede. Por lo tanto, compruebe el nombre de usuario en la parte superior derecha del complemento de Excel.

El complemento de Excel lee automáticamente los datos de la entidad seleccionada. Tenga en cuenta que no habrá datos en el libro hasta que el complemento de Excel los lea.

## <a name="view-and-refresh-data-in-excel"></a>Visualizar y actualizar datos en Excel
Cuando el complemento de Excel lea datos de la entidad en el libro, puede actualizar los datos en cualquier momento haciendo clic en **Actualización** en el complemento de Excel.

## <a name="edit-data-in-excel"></a>Editar datos de Excel
Puede cambiar los datos de la entidad como sea necesario y después volver a publicarlos haciendo clic en **Publicar** en el complemento de Excel.

Para editar un registro, seleccione una celda en la hoja de cálculo y, a continuación, cambie el valor de la celda.

Para agregar un nuevo registro, siga estos pasos:

* Haga clic en cualquier lugar de la hoja de cálculo y después haga clic en **Nuevo** en el complemento de Excel.
* Haga clic en la última fila de la hoja de cálculo, pulse la tecla TAB hasta que el cursor salga de la última columna de esa fila y se creará una nueva fila.
* Haga clic en la fila inmediatamente que hay debajo de la hoja de cálculo y empiece a introducir datos en una celda. Cuando salga de esa celda, la hoja de cálculo se expandirá para incluir la nueva fila.

Para eliminar un registro, siga estos pasos:

* Haga clic con el botón secundario en el número de fila que hay junto a la fila de la hoja de cálculo que desea eliminar y, a continuación, haga clic en **Eliminar**.
* Haga clic con el botón secundario en la fila de la hoja de cálculo que desea eliminar y, a continuación, haga clic en **Eliminar** > **Filas de la tabla**.

## <a name="add-or-remove-columns"></a>Agregar o quitar columnas
Puede usar el diseñador para ajustar las columnas y las entidades que se agregan automáticamente a la hoja de cálculo.

1. Habilite el diseñador de origen de datos del complemento de Excel haciendo clic en el botón **Opciones** (el símbolo de engranaje) y seleccionando la casilla **Habilitar diseño**.
2. Haga clic en **Diseño** en el complemento de Excel. Se muestra una lista de todos los orígenes de datos.
3. Junto al origen de datos, haga clic en el botón **Editar** (el símbolo de lápiz).
4. Ajuste la lista en el campo **Campos seleccionados** como necesite:
   * Para agregar un campo del campo **Campos disponibles** al campo **Campos seleccionados**, haga clic en el campo y, a continuación, haga clic en **Agregar**. O bien, haga doble clic en el campo.
   * Para quitar un campo del campo **Campos seleccionados**, haga clic en el campo y, a continuación, haga clic en **Quitar**. O bien, haga doble clic en el campo.
   * Para cambiar el orden de los campos, haga clic en el campo del campo **Campos seleccionados** y, a continuación, haga clic en **Arriba** o **Abajo**.
5. Aplique los cambios al origen de datos haciendo clic en **Actualizar** y, a continuación, haga clic en **Hecho** para salir del diseñador. Si agregó un campo (columna), haga clic en **Actualizar** para obtener un conjunto de datos actualizado.

> [!NOTE]
> Asegúrese de incluir siempre el identificador y los campos necesarios en el libro, ya que podría recibir errores al publicar.

> [!NOTE]
> Al agregar campos de consulta, asegúrese de agregar el identificador y los campos de visualización.

## <a name="troubleshooting"></a>Solución de problemas
Existen algunos problemas que se pueden resolver a través de una serie de pasos sencillos.

* No todas las entidades admiten la edición y creación de nuevos registros, estas entidades se abrirán en Excel y le permitirán ver datos, aunque la publicación estará deshabilitada.
* Los campos de búsqueda deben editarse con el complemento para garantizar que se hace referencia al registro correcto, no se permite actualizar estos campos mediante la función de copiar o pegar o introduciéndolos directamente en el campo.


Si se produce un problema que no se describe aquí, póngase en contacto con nosotros mediante las [páginas de soporte](https://powerapps.microsoft.com/support/).

## <a name="next-steps"></a>Pasos siguientes
* [Administrar campos de una entidad](data-platform-manage-fields.md)
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Generar una aplicación usando Common Data Service for Apps](../canvas-apps/data-platform-create-app.md)
* [Crear una aplicación desde cero usando Common Data Service for Apps](../canvas-apps/data-platform-create-app-scratch.md)

