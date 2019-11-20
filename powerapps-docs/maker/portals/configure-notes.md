---
title: Configurar notas en formularios de entidad y formularios Web Forms para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar notas en formularios de entidad y formularios Web Forms en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 59ed66842874414737b7bdc04f0f4dfa51d212c8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542848"
---
# <a name="configure-notes-for-entity-forms-and-web-forms-on-portals"></a>Configurar notas para formularios de entidad y formularios Web Forms en portales

Al igual que con las subcuadrículas, agregar notas a los formularios administrados en el portal es fácil&mdash;simplemente agregue el control notas a los formularios de la aplicación Model-Drive a través del [Diseñador de formularios](../model-driven-apps/create-design-forms.md) y ya ha terminado. Puede configurar el comportamiento del control de notas mediante el uso de metadatos.

> [!Note]                                                           
> Los [permisos de entidad](configure/assign-entity-permissions.md) explícitos son necesarios para que las notas aparezcan en el portal. Para leer y editar, se deben conceder los privilegios de lectura y escritura. Para crear, deben existir dos permisos: se debe conceder un permiso con los privilegios Create y Append para la entidad Note (Annotation), el segundo permiso debe asignarse al tipo de entidad al que se va a adjuntar la nota con el privilegio anexar a concedido. La casilla **Habilitar permisos de entidad** debe estar activada en el paso de formulario de la entidad o formulario web correspondiente para que los permisos de entidad surtan efecto.

## <a name="notes-configuration-for-entity-forms"></a>Configuración de notas para formularios de entidad

1. Abra la [aplicación administración del portal](configure/configure-portal.md).
2. Vaya a **portales** > **contenido** > **formularios de entidad**. Se muestra una lista de formularios de entidad activos.
3. Seleccione el formulario de la entidad al que desea agregar la configuración de nota.
4. Vaya a los **metadatos del formulario** de la entidad mediante la lista desplegable superior o la subcuadrícula del formulario principal del registro del formulario de la entidad con el que está trabajando.
5. Seleccione **agregar nuevos metadatos del formulario** de la entidad para agregar un nuevo registro.
6. En la lista desplegable **tipo** , seleccione **notas**. Se muestra la configuración de Notes&ndash;configuración específica. La mayoría de las opciones están contraídas de forma predeterminada. Puede expandir una sección para ver la configuración adicional.
7. Escriba los valores adecuados para rellenar los campos. [!include[](../../includes/proc-more-information.md)] [atributos](#attributes), [crear opciones de cuadro](#create-dialog-options)de diálogo, [Editar opciones de cuadro](#edit-dialog-options)de diálogo y [eliminar opciones de cuadro de diálogo](#delete-dialog-options)
8. Guarde el formulario.

    ![Agregar configuración de notas para formularios de entidad](media/add-note-configuration.png "Agregar configuración de notas para formularios de entidad")  

    Después de agregar la configuración, el control nota se representará con las opciones adecuadas habilitadas en el portal.

## <a name="attributes"></a>Atributos


| Nombre                  | Descripción                                                                                                                                                  |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                              |
| Crear habilitado        | Habilita la capacidad de agregar nuevas notas a la entidad.                                                                                                          |
| Crear opciones de cuadro de diálogo | Contiene la configuración para configurar el cuadro de diálogo cuando la **opción crear habilitado** es true. Consulte crear opciones de diálogo para obtener más detalles.                                    |
| Edición habilitada          | Habilita la capacidad de editar las notas existentes en la entidad.                                                                                                    |
| Editar opciones de cuadro de diálogo   | Contiene la configuración para configurar el cuadro de diálogo cuando **EditEnabled** es true. Consulte Editar opciones de diálogo para obtener más detalles.                                         |
| Eliminación habilitada        | Habilita la capacidad de eliminar notas de la entidad.                                                                                                         |
| Eliminar opciones de cuadro de diálogo | Contiene la configuración para configurar el cuadro de diálogo cuando **DeleteEnabled** es true. Vea las opciones de cuadro de diálogo eliminar para obtener más detalles.                                     |
|Ubicación de datos adjuntos | Seleccione la ubicación de los archivos adjuntos:<ul><li>Anotar datos adjuntos</li><li>Azure Blob Storage</li></ul>|
|Aceptar tipos MIME | Permite especificar una lista de tipos MIME aceptados. |
|Restricción de tipos MIME | Seleccione si desea permitir o restringir los tipos MIME.|
|Tamaño máximo de archivo (en KB) |Permite especificar el tamaño máximo de un archivo que se puede adjuntar. |
| **Configuración avanzada** |                                                                                                                                                              |
| Título de la lista            | Invalida el título en el área de notas.                                                                                                                     |
| Agregar etiqueta de botón de nota | Invalida la etiqueta del botón Agregar notas.                                                                                                                 |
| Nota: etiqueta de privacidad    | Invalida la etiqueta que denota que una nota es privada.                                                                                                         |
| Cargando mensaje       | Invalida el mensaje mostrado mientras se está cargando la lista de notas.                                                                                              |
| Mensaje de error         | Invalida el mensaje que se muestra cuando se produce un error al intentar cargar la lista de notas.                                                                     |
| Mensaje de acceso denegado | Invalida el mensaje que se muestra cuando el usuario no tiene permisos suficientes para ver la lista de notas.                                                    |
| Mensaje vacío         | Reemplaza el mensaje mostrado cuando la entidad actual no tiene ninguna nota que se pueda ver.                                                              |
| Lista de pedidos           | Permite establecer el orden en el que se mostrarán las notas. La configuración de lista de pedidos permite establecer lo siguiente: <ul><li>Attribute: el nombre lógico de la columna por la que desea ordenar.</li><li>Alias: el alias del atributo en la consulta.</li><li>Direcciona Ascendente (de menor a mayor, o primero a último) o descendente (de mayor a menor, o último a primero).</li></ul> ![Establecer atributos para la lista de pedidos](media/set-attributes-list-orders.png "Satributos et para lista de pedidos ") Para agregar una regla de ordenación, seleccione "columna" (4) y rellene los detalles. Los pedidos de lista se procesarán en orden desde la parte superior de la lista con la prioridad más alta.|
||


## <a name="create-dialog-options"></a>Crear opciones de cuadro de diálogo

| Nombre                               | Descripción                                                                                                                                 |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**                 |                                                                                                                                             |
| Mostrar campo de opciones de privacidad      | Habilita una casilla en el cuadro de diálogo Agregar nota que permite al usuario marcar una nota como privada.                                                   |
| Valor predeterminado del campo de opción de privacidad | Especifica el valor predeterminado para la casilla Mostrar el campo de opciones de privacidad. El valor predeterminado de este campo es false.                     |
| Mostrar archivo de datos adjuntos                | Habilita un campo de carga de archivos en el cuadro de diálogo Agregar nota, lo que permite al usuario adjuntar un archivo a una nota.                                             |
| Adjuntar archivo aceptar                 | Tipo MIME aceptado por la entrada de carga de archivos.                                                                                            |
| **Configuración avanzada**              |                                                                                                                                             |
| Etiqueta de campo de nota                   | Invalida la etiqueta del campo nota en el cuadro de diálogo Agregar Nota.                                                                              |
| Columnas de campo de nota                 | Establece el valor cols de la nota &lt;TextArea&gt;                                                                                            |
| Filas de campo de nota                    | Establece el valor de las filas en la nota &lt;TextArea&gt;                                                                                            |
| Etiqueta de campo de la opción de privacidad         | Invalida la etiqueta del campo de la opción de privacidad (si está habilitado).                                                                              |
| Adjuntar etiqueta de archivo                  | Invalida la etiqueta del campo adjuntar archivo (si está habilitado)                                                                                  |
| Clase CSS de columna izquierda              | Agrega la clase o clases CSS a la columna situada más a la izquierda que contiene las etiquetas en el cuadro de diálogo Agregar Nota.                                                  |
| Clase CSS de columna derecha             | Agrega la clase o clases CSS a la columna situada más a la derecha que contiene entradas de campo en el cuadro de diálogo Agregar Nota.                                           |
| Título                              | Reemplaza el texto HTML en el encabezado del cuadro de diálogo Agregar Nota.                                                                               |
| Texto del botón primario                | Invalida el código HTML que aparece en el botón principal (agregar Nota) del cuadro de diálogo.                                                           |
| Descartar texto de SR             | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                               |
| Cerrar texto del botón                  | Invalida el código HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                               |
| Tamaño                               | Especifica el tamaño del cuadro de diálogo Agregar Nota. Las opciones son predeterminadas, grandes y pequeñas. En el cuadro de diálogo Agregar nota, el tamaño predeterminado es predeterminado. |
| Clase CSS                          | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                |
| Title CSS (clase)                    | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                    |
| Clase CSS de botón principal           | Especifique una clase o clases CSS que se aplicarán al botón principal (agregar Nota) del cuadro de diálogo.                                            |
| Botón Cerrar (clase CSS)             | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                |
|||

## <a name="edit-dialog-options"></a>Editar opciones de cuadro de diálogo

| Nombre                               | Descripción                                                                                                                                   |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**                 |                                                                                                                                               |
| Mostrar campo de opciones de privacidad      | Habilita una casilla en el cuadro de diálogo Editar nota que permite al usuario marcar una nota como privada.  |
| Valor predeterminado del campo de opción de privacidad | Especifica el valor predeterminado para la casilla Mostrar el campo de opciones de privacidad. El valor predeterminado de este campo es false.   |
| Mostrar archivo de datos adjuntos                | Habilita un campo de carga de archivos en el cuadro de diálogo Editar nota, lo que permite al usuario adjuntar un archivo a una nota.                      |
| Adjuntar archivo aceptar                 | Tipo MIME aceptado por la entrada de carga de archivos. |
| **Configuración avanzada**              |                                                                                              |
| Etiqueta de campo de nota                   | Invalida la etiqueta del campo nota en el cuadro de diálogo Editar Nota.|
| Columnas de campo de nota                 | Establece el valor cols de la nota &lt;TextArea&gt;                                                                                             |
| Filas de campo de nota                    | Establece el valor de las filas en la nota &lt;TextArea&gt;                                                                                             |
| Etiqueta de campo de la opción de privacidad         | Invalida la etiqueta del campo de la opción de privacidad (si está habilitado).                                                                                
| Adjuntar etiqueta de archivo                  | Invalida la etiqueta del campo adjuntar archivo (si está habilitado)                                                                                   |
| Clase CSS de columna izquierda              | Agrega la clase o clases CSS a la columna situada más a la izquierda que contiene las etiquetas en el cuadro de diálogo Editar Nota.                                                  |
| Clase CSS de columna derecha             | Agrega la clase o clases CSS a la columna situada más a la derecha que contiene entradas de campo en el cuadro de diálogo Editar Nota.                                           |
| Título                              | Reemplaza el texto HTML en el encabezado del cuadro de diálogo Editar Nota.                                                                               |
| Texto del botón primario                | Invalida el código HTML que aparece en el botón principal (nota de actualización) del cuadro de diálogo.                                                         |
| Descartar texto de SR             | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                                |
| Cerrar texto del botón                  | Invalida el código HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                                |
| Tamaño                               | Especifica el tamaño del cuadro de diálogo Editar Nota. Las opciones son predeterminadas, grandes y pequeñas. En el cuadro de diálogo Editar nota, el tamaño predeterminado es predeterminado.|
| Clase CSS                          | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                 |
| Title CSS (clase)                    | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                     |
| Clase CSS de botón principal           | Especifique una clase o clases CSS que se aplicarán al botón principal (nota de actualización) del cuadro de diálogo.                                          |
| Botón Cerrar (clase CSS)             | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                 |
|||

## <a name="delete-dialog-options"></a>Eliminar opciones de cuadro de diálogo

| Nombre                     | Descripción                                                                                                                                       |
|--------------------------|------------------------------|
| **Configuración básica**       |                                                                                                                                                   |
| Confirmación             | Invalide el mensaje de confirmación para eliminar la nota.                                                                                             |
| **Configuración avanzada**    |                                                                                                                                                   |
| Título                    | Reemplaza el texto HTML en el encabezado del cuadro de diálogo eliminar Nota.                                                                                  |
| Texto del botón primario      | Invalida el código HTML que aparece en el botón principal (eliminar) del cuadro de diálogo.                                                                   |
| Descartar texto de SR   | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                                     |
| Cerrar texto del botón        | Invalida el código HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                                     |
| Tamaño                     | Especifica el tamaño del cuadro de diálogo eliminar Nota. Las opciones son predeterminadas, grandes y pequeñas. En el cuadro de diálogo eliminar nota, el tamaño predeterminado es predeterminado. |
| Clase CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                      |
| Title CSS (clase)          | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                          |
| Clase CSS de botón principal | Especifique una clase o clases CSS que se aplicarán al botón principal (eliminar) del cuadro de diálogo.                                                    |
| Botón Cerrar (clase CSS)   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                      |
|||

### <a name="assign-entity-permissions"></a>Administración de permisos de entidad

Debe crear y asignar el permiso de entidad correspondiente a los registros como se indica a continuación; de lo contrario, se ocultarán los botones **Agregar**, **Editar**y **eliminar** de la Nota:

- Leer, escribir, crear, anexar y anexar a privilegios para la entidad **actividad (activitypointer)** con el ámbito como **global**. Este permiso de entidad debe estar asociado a un rol Web para el usuario.
- Leer, escribir, crear, anexar y anexar a los privilegios de la entidad que tiene habilitado el control notas. El ámbito debe establecerse en **global**. Este permiso de entidad debe estar asociado a un rol Web para el usuario.

    ![Agregar permisos de entidad](media/entity-permission.png "Agregar permisos de entidad")

    ![Agregar roles web a un permiso de entidad](media/entity-permission-web-roles.png "Agregar roles web a un permiso de entidad")

Si ha creado un formulario personalizado y le ha agregado la sección Notas, asegúrese de seleccionar **notas** como la pestaña predeterminada que desea que esté visible.

![Notas en un formulario personalizado](media/notes-activities-tab.png "Notas en un formulario personalizado")

## <a name="notes-configuration-for-web-forms"></a>Configuración de notas para formularios Web Forms

Las notas del formulario web se configuran de la misma manera que las [notas del formulario](#notes-configuration-for-entity-forms)de la entidad. Primero debe crear un registro de metadatos para el paso de formulario web que tenga notas y, a continuación, agregar los metadatos de configuración de Notes.