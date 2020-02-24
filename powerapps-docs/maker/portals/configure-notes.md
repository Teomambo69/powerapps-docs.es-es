---
title: Configurar notas en formularios de entidad y formularios web para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar notas en los formularios de entidades y formularios web en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d1e8048f4cc4dbb2023788fcc3d3cf28fdfb7f7b
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979709"
---
# <a name="configure-notes-for-entity-forms-and-web-forms-on-portals"></a>Configurar notas para formularios de entidad y formularios web en portales

Como con las subcuadrículas, agregar notas a los formularios administrados en el portal es sencillo&mdash;simplemente agregue el control de notas a formularios de aplicaciones basadas en modelo a través del [diseñador de formularios](../model-driven-apps/create-design-forms.md) y ya está. Puede configurar el comportamiento del control de notas utilizando metadatos.

> [!Note]                                                           
> Se requieren [permisos de entidad](configure/assign-entity-permissions.md) explícitos para cualquier nota que aparece en el portal. Para leer y editar, deben ser concedidos los privilegios de la lectura y escritura. Para crear, deben existir dos permisos: un permiso con los privilegios crear y anexar debe concederse para la entidad de nota (anotación), el segundo permiso debe asignarse al tipo de entidad al que se anexa la nota con el privilegio de Anexar a concedido. La casilla de verificación **Habilitar los permisos de la entidad** debe estar seleccionado en el formulario correspondiente de la entidad o el paso web de formulario para que los permisos de la entidad surtan efecto.

## <a name="notes-configuration-for-entity-forms"></a>Configuración de notas para formularios de entidad

1. Abra la aplicación [Administración del portal](configure/configure-portal.md).
2. Vaya a **Portales** > **Contenido** > **Formularios de entidad**. Aparece una lista de formularios de entidad activos.
3. Seleccione el formulario de entidad al que desee agregar una configuración de notas.
4. Vaya a **Metadatos del formulario de entidad** con la lista desplegable superior o la subcuadrícula en el formulario principal del registro del formulario de entidad con el que trabaja.
5. Seleccione **Agregar nuevos metadatos del formulario de entidad** para agregar un nuevo registro.
6. De la lista desplegable **Tipo**, seleccione **Notas**. Se muestran los valores específicos de la&ndash;configuración de notas La mayoría de los valores están contraídos de forma predeterminada. Puede expandir una sección para ver la configuración adicional.
7. Complete los campos con los valores apropiados. [!include[](../../includes/proc-more-information.md)] [Atributos](#attributes), [Crear opciones de diálogo](#create-dialog-options), [Editar opciones de diálogo](#edit-dialog-options), y [Eliminar opciones de diálogo](#delete-dialog-options)
8. Guarde el formulario.

    ![Agregar configuración de notas para formularios de entidad](media/add-note-configuration.png "Agregar configuración de notas para formularios de entidad")  

    Después de agregar la configuración, el control de nota se representará con las opciones adecuadas habilitadas en el portal.

## <a name="attributes"></a>Atributos


| Nombre                  | Descripción                                                                                                                                                  |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                              |
| Creación habilitada        | Habilita la capacidad de agregar nuevas notas a la entidad.                                                                                                          |
| Opciones del diálogo de creación | Contiene la configuración para configurar el cuadro de diálogo cuando **Creación habilitada** es true. Consulte Opciones del diálogo de creación para obtener más detalles.                                    |
| Edición habilitada          | Habilita la capacidad de editar notas existentes en la entidad.                                                                                                    |
| Opciones del diálogo de edición   | Contiene la configuración para configurar el cuadro de diálogo cuando **EditEnabled** es true. Consulte Opciones del diálogo de edición para obtener más detalles.                                         |
| Eliminación habilitada        | Habilita la capacidad de eliminar notas de la entidad.                                                                                                         |
| Opciones del diálogo de eliminación | Contiene la configuración para configurar el cuadro de diálogo cuando **DeleteEnabled** es true. Consulte Opciones del diálogo de eliminación para obtener más detalles.                                     |
|Ubicación de archivo adjunto | Seleccione la ubicación del archivo adjunto:<ul><li>Datos adjuntos de nota</li><li>Azure Blob Storage</li></ul>|
|Aceptar tipos MIME | Permite especificar una lista de tipos MIME aceptados. |
|Restringir tipos MIME | Seleccione si permite o restringe los tipos MIME.|
|Tamaño máximo de archivo (en kB) |Permite especificar el tamaño máximo de archivo que se puede adjuntar. |
| **Configuración avanzada** |                                                                                                                                                              |
| Mostrar título            | Reemplaza el título sobre el área Notas.                                                                                                                     |
| Etiqueta del botón Agregar nota | Reemplaza la etiqueta en el botón Agregar notas.                                                                                                                 |
| Etiqueta de privacidad de nota    | Reemplaza la etiqueta que denota que una nota es privada.                                                                                                         |
| Cargando mensaje       | Reemplaza el mensaje que se muestra mientras la lista de notas se carga.                                                                                              |
| Mensaje de error         | Reemplaza el mensaje que se muestra cuando se produce un error al intentar cargar la lista de notas.                                                                     |
| Mensaje de acceso denegado | Reemplaza el mensaje que se muestra cuando el usuario no tiene permisos suficientes para ver la lista de notas.                                                    |
| Mensaje vacío         | Reemplaza el mensaje que se muestra cuando la entidad actual no tiene notas que pueden ser vistas.                                                              |
| Mostrar órdenes           | Permite establecer el orden en que las notas se mostrarán. Los configuración de lista de órdenes le permite establecer lo siguiente: <ul><li>Atributo: el nombre lógico de la columna por la que desea ordenar</li><li>Alias: el alias para el atributo en la consulta</li><li>Dirección: Ascendente (menor a mayor, o primera a última), o descendente (mayor a menor, o última a primera).</li></ul>  ![Establecer atributos para Mostrar órdenes](media/set-attributes-list-orders.png "Establecer atributos para órdenes de lista")   Para agregar una regla de ordenación, seleccione "Columna" (4) y rellene los detalles. Mostrar órdenes se procesará en orden de arriba de la lista que tenga la prioridad máxima.|
||


## <a name="create-dialog-options"></a>Opciones del diálogo de creación

| Nombre                               | Descripción                                                                                                                                 |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**                 |                                                                                                                                             |
| Mostrar campo de opciones de privacidad      | Activa una casilla en el cuadro de diálogo Agregar nota que permite al usuario marcar una nota como privada.                                                   |
| Valor predeterminado del campo de opción de privacidad | Especifica el valor predeterminado para la casilla del campo Mostrar opciones de privacidad. El valor predeterminado de este campo es "false".                     |
| Mostrar adjuntar archivo                | Habilita un campo de carga de archivos en el cuadro de diálogo Agregar nota, lo que permite a un usuario adjuntar un archivo a una nota.                                             |
| Aceptar archivo adjunto                 | El tipo MIME aceptado por la entrada de carga de archivos.                                                                                            |
| **Configuración avanzada**              |                                                                                                                                             |
| Etiqueta de campo de nota                   | Reemplaza la etiqueta del campo Nota en el cuadro de diálogo Agregar nota.                                                                              |
| Columnas de campo de nota                 | Establece el valor de cols en la Nota &lt;textarea&gt;                                                                                            |
| Filas de campo de nota                    | Establece el valor de rows en la Nota &lt;textarea&gt;                                                                                            |
| Etiqueta de campo de opción de privacidad         | Reemplaza la etiqueta del campo Opción de privacidad (si está habilitado).                                                                              |
| Etiqueta de archivo adjunto                  | Reemplaza la etiqueta del campo Adjuntar archivo privacidad (si está habilitado)                                                                                  |
| Clase CSS de columna izquierda              | Agrega la clase o clases CSS a la columna izquierda que contiene etiquetas en cuadro de diálogo Agregar nota.                                                  |
| Clase CSS de columna derecha             | Agrega la clase o clases CSS a la columna derecha que contiene entradas de campo en el cuadro de diálogo Agregar nota.                                           |
| Título                              | Reemplaza el texto HTML en el encabezado del cuadro de diálogo Agregar nota.                                                                               |
| Texto del botón primario                | Reemplaza el HTML que aparece en el botón Principal (Agregar nota) en el cuadro de diálogo.                                                           |
| Texto del lector de pantalla del botón Descartar             | Reemplaza el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                               |
| Texto del botón Cerrar                  | Reemplaza el HTML que aparece en el botón Cerrar (Cancelar) en el cuadro de diálogo.                                                               |
| Tamaño                               | Especifica el tamaño del cuadro de diálogo Agregar nota. Las opciones son: Predeterminado, Grande y Pequeño. Para el cuadro de diálogo Agregar nota, el tamaño predeterminado es Predeterminado. |
| Clase de CSS                          | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                |
| Clase CSS de título                    | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                    |
| Clase CSS del botón primario           | Especifique una clase o clases CSS que se aplicará al botón Principal (Agregar nota) del cuadro de diálogo.                                            |
| Clase CSS del botón Cerrar             | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                |
|||

## <a name="edit-dialog-options"></a>Opciones del diálogo de edición

| Nombre                               | Descripción                                                                                                                                   |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**                 |                                                                                                                                               |
| Mostrar campo de opciones de privacidad      | Activa una casilla en el cuadro de diálogo Editar nota que permite al usuario marcar una nota como privada.  |
| Valor predeterminado del campo de opción de privacidad | Especifica el valor predeterminado para la casilla del campo Mostrar opciones de privacidad. El valor predeterminado de este campo es "false".   |
| Mostrar adjuntar archivo                | Habilita un campo de carga de archivos en el cuadro de diálogo Editar nota, lo que permite a un usuario adjuntar un archivo a una nota.                      |
| Aceptar archivo adjunto                 | El tipo MIME aceptado por la entrada de carga de archivos. |
| **Configuración avanzada**              |                                                                                              |
| Etiqueta de campo de nota                   | Reemplaza la etiqueta del campo Nota en el cuadro de diálogo Editar nota.|
| Columnas de campo de nota                 | Establece el valor de cols en la Nota &lt;textarea&gt;                                                                                             |
| Filas de campo de nota                    | Establece el valor de rows en la Nota &lt;textarea&gt;                                                                                             |
| Etiqueta de campo de opción de privacidad         | Reemplaza la etiqueta del campo Opción de privacidad (si está habilitado).                                                                                
| Etiqueta de archivo adjunto                  | Reemplaza la etiqueta del campo Adjuntar archivo privacidad (si está habilitado)                                                                                   |
| Clase CSS de columna izquierda              | Agrega la clase o clases CSS a la columna izquierda que contiene etiquetas en cuadro de diálogo Editar nota.                                                  |
| Clase CSS de columna derecha             | Agrega la clase o clases CSS a la columna derecha que contiene entradas de campo en el cuadro de diálogo Ediar nota.                                           |
| Título                              | Reemplaza el texto HTML en el encabezado del cuadro de diálogo Editar nota.                                                                               |
| Texto del botón primario                | Reemplaza el HTML que aparece en el botón Principal (Actualizar nota) en el cuadro de diálogo.                                                         |
| Texto del lector de pantalla del botón Descartar             | Reemplaza el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                                |
| Texto del botón Cerrar                  | Reemplaza el HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                                |
| Tamaño                               | Especifica el tamaño del cuador de diálogo Editar nota. Las opciones son: Predeterminado, Grande y Pequeño. Para el cuadro de diálogo Editar nota, el tamaño predeterminado es Predeterminado.|
| Clase de CSS                          | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                 |
| Clase CSS de título                    | Especifique una clase o clases CSS que se aplicará a la barra de título del diálogo resultante.                                                     |
| Clase CSS del botón primario           | Especifique una clase o clases CSS que se aplicará al botón Principal (Actualizar nota) del cuadro de diálogo.                                          |
| Clase CSS del botón Cerrar             | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                 |
|||

## <a name="delete-dialog-options"></a>Opciones del diálogo de eliminación

| Nombre                     | Descripción                                                                                                                                       |
|--------------------------|------------------------------|
| **Configuración básica**       |                                                                                                                                                   |
| Confirmación             | Reemplace el mensaje de confirmación para eliminar la nota.                                                                                             |
| **Configuración avanzada**    |                                                                                                                                                   |
| Título                    | Reemplaza el texto HTML en el encabezado del cuadro de diálogo Eliminar nota.                                                                                  |
| Texto del botón primario      | Reemplaza el HTML que aparece en el botón Principal (Eliminar) en el cuadro de diálogo.                                                                   |
| Texto del lector de pantalla del botón Descartar   | Reemplaza el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                                     |
| Texto del botón Cerrar        | Reemplaza el HTML que aparece en el botón Cerrar (Cancelar) en el cuadro de diálogo.                                                                     |
| Tamaño                     | Especifica el tamaño del cuadro de diálogo Eliminar nota. Las opciones son: Predeterminado, Grande y Pequeño. Para el cuadro de diálogo Eliminar nota, el tamaño predeterminado es Predeterminado. |
| Clase de CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                      |
| Clase CSS de título          | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                          |
| Clase CSS del botón primario | Especifique una clase o clases CSS que se aplicarán al botón Principal (Eliminar) del cuadro de diálogo.                                                    |
| Clase CSS del botón Cerrar   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                      |
|||

### <a name="assign-entity-permissions"></a>Asignar permisos de entidad

Debe crear y asignar el permiso de entidad adecuado a los registros como sigue; de lo contrario, los botones **Agregar**, **Editar** y **Eliminar** para la nota estarán ocultos:

- Privilegios Leer, Escribir, Crear, Anexar y Anexar a para la entidad **Actividad (activitypointer)** con el ámbito como **Global**. Este permiso de entidad debe estar asociado a un rol web para el usuario.
- Privilegios Leer, Escribir, Crear, Anexar y Anexar a para la entidad que tiene el control Notas habilitado. El ámbito debe establecerse en **Global**. Este permiso de entidad debe estar asociado a un rol web para el usuario.

    ![Agregar permisos de entidad](media/entity-permission.png "Agregar permisos de entidad")

    ![Agregar roles web a un permiso de entidad](media/entity-permission-web-roles.png "Agregar roles web a un permiso de entidad")

Si ha creado un formulario personalizado y ha agregado la sección notas, asegúrese de seleccionar **Notas** como la pestaña predeterminada que quiere que esté visible.

![Notas en un formulario personalizado](media/notes-activities-tab.png "Notas en un formulario personalizado")

## <a name="notes-configuration-for-web-forms"></a>Configuración de notas para formularios web

Las notas de formulario web se configuran de la misma forma que las [notas de formulario de entidad](#notes-configuration-for-entity-forms). Primero debe crear un registro de metadatos para el paso del formulario web que tiene notas, y luego agregue los metadatos de configuración de notas.
