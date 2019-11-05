---
title: Configuración de subcuadrículas de formularios Web Forms para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar subcuadrículas de formularios Web Forms para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 210300d40742cbf2ca83f9d6c3b07cd580167eaa
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552966"
---
# <a name="configure-web-form-subgrids-for-portals"></a>Configurar subcuadrículas de formularios Web Forms para portales

Las subcuadrículas del formulario web se configuran de una manera idéntica a las subcuadrículas del formulario de la entidad: en primer lugar, cree un registro de metadatos para el paso de formulario web que tenga una subcuadrícula y, a continuación, agregue metadatos de configuración.

Agregar subcuadrículas a los formularios administrados en el portal es fácil: solo tiene que agregar la subcuadrícula al formulario que está administrando mediante el diseñador de formularios listo para usar y ya ha terminado. La cuadrícula usará la vista que se especifica en Common Data Service diseñador de formularios, mostrar solo los registros relacionados si se eligió esa opción, Mostrar opcionalmente una barra de búsqueda e incluso respetar [los permisos de entidad para los portales](assign-entity-permissions.md). No es más fácil mostrar una lista de registros de solo lectura. Para habilitar las acciones de la cuadrícula (crear, actualizar, eliminar, etc.), debe configurar esas acciones mediante la configuración de metadatos.

## <a name="add-subgrid-metadata-to-your-form"></a>Agregar metadatos de subcuadrícula al formulario

Para agregar metadatos de subcuadrícula a un formulario de entidad, vaya a **metadatos del formulario** de la entidad mediante la lista desplegable superior o la subcuadrícula del formulario principal del registro con el que está trabajando. Más información: [definir formularios de entidad](entity-forms.md).

Para agregar un nuevo registro, seleccione **agregar nuevos metadatos del formulario**de la entidad.

Para editar un registro existente, seleccione el registro en la cuadrícula. Al seleccionar **subcuadrícula** como el valor de **tipo** se muestra otro atributo, **nombre de subcuadrícula**.


|     Nombre     |                                                       Descripción                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------|
| Nombre de la subcuadrícula | Nombre único de la subcuadrícula del formulario relacionado de la entidad. |
|              |                                                                                                                          |

Si selecciona la subcuadrícula en el editor de formularios, se mostrará una ventana Propiedades. Contiene un campo de **nombre** que se debe usar para asignar al campo **nombre de la subcuadrícula** en el registro de metadatos del formulario de la entidad.

![Agregar metadatos de subcuadrícula](../media/add-subgrid-metadata.png "Agregar metadatos de subcuadrícula")  

Si se especifica un nombre de subcuadrícula válido, se mostrarán los valores de configuración de la subcuadrícula. De forma predeterminada, solo se muestra la **configuración básica** . Seleccione **Configuración avanzada** para mostrar la configuración adicional.

De forma predeterminada, la mayoría de las configuraciones se muestran contraídas para ahorrar espacio. Seleccione * * * * para expandir una sección y ver opciones adicionales. Seleccione * * * * para contraer la sección.

## <a name="attributes"></a>Atributos

| Nombre                       | Descripción                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**         |                                                                                                                                                                                                                                                                                                                                                                           |
| Ver acciones               | Use para agregar botones de acción para las acciones que se aplican al conjunto de entidades y que aparecerán encima de la subcuadrícula. Las acciones disponibles son: <ul><li>A</li><li>Download</li><li>Asócielos</li></ul> Al seleccionar una de estas opciones se muestra un área de configuración para esa acción. Consulte a continuación los detalles de cada acción.                                                                                                                                                                                                                                                   |
| Acciones de elemento               | Use para agregar botones de acción para las acciones que se pueden aplicar a un registro individual y que aparecerán en cada fila de la subcuadrícula, siempre que los permisos de [entidad](assign-entity-permissions.md)hayan concedido el privilegio asociado. Las acciones disponibles son: <ul><li>Detalles</li><li>Editar</li><li>Elimínelos</li><li>Flujo</li><li>Desasociar</li></ul> Al seleccionar una de estas opciones, se muestra un área de configuración para esa acción. Consulte a continuación los detalles de cada acción.                                                                                                                                                                                                                                                   |
| Reemplazar atributos de columna | Se usa para invalidar la configuración de presentación de columnas individuales en la cuadrícula. <ul><li>Attribute: nombre lógico de la columna que desea invalidar.</li><li>Nombre para mostrar: nuevo título de columna para invalidar el valor predeterminado</li><li>Width: ancho (en porcentaje o píxeles) de la columna para reemplazar el valor predeterminado. Vea también estilo de ancho de columna de cuadrícula. Para invalidar la configuración de una columna, seleccione **columna** y rellene los detalles.                                                                                                                                                                                                                                                                                             |
| **Configuración avanzada**      |                                                                                                                                                                                                                                                                                                                                                                           |
| Cargando mensaje            | Invalida el mensaje HTML predeterminado que aparece mientras se está cargando la subcuadrícula.                                                                                                                                                                                                                                                                                             |
| Mensaje de error              | Invalida el mensaje HTML predeterminado que aparece cuando se produce un error mientras se carga la subcuadrícula.                                                                                                                                                                                                                                                                           |
| Mensaje de acceso denegado      | Invalida el mensaje HTML predeterminado que aparece cuando un usuario no tiene [permisos](assign-entity-permissions.md) suficientes para leer el tipo de entidad asociado a la subcuadrícula.                       |
| Mensaje vacío              | Invalida el mensaje HTML que aparece cuando la subcuadrícula asociada no contiene datos.                                                                                                                                                                                                                                                                                     |
| Cuadro de diálogo de búsqueda              | Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción asociar.                                                                                                                                                                                                                                                                             |
| Cuadro de diálogo formulario de detalles        | Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de detalles.                                                                                                                                                                                                                                                                                |
| Cuadro de diálogo Editar formulario           | Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de edición.                                                                                                                                                                                                                                                                                   |
| Cuadro de diálogo Crear formulario         | Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de creación.                                                                                                                                                                                                                                                                                 |
| Cuadro de diálogo eliminar              | Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de eliminación.                                                                                                                                                                                                                                                                                 |
| Cuadro de diálogo de error               | Controla la configuración del cuadro de diálogo que aparece cuando se produce un error durante cualquier acción.                                                                                                                                                                                                                                                                                 |
| Clase CSS                  | Especifique una clase o clases CSS que se aplicarán al elemento HTML que contiene la totalidad del área de la subcuadrícula, incluidos los botones de acción y cuadrícula.                                                                                                                                                                                                                     |
| Grid CSS (clase)             | Especifique una clase o clases CSS que se aplicarán al elemento&gt; de la tabla &lt;HTML de la subcuadrícula.                                                                                                                                                                                                                                                                          |
| Estilo de ancho de columna de cuadrícula    | Configura si los valores de **ancho** de los atributos de columna de invalidación se especifican en **píxeles** o como **porcentaje**.                                                                                                                                                                                                                                                             |
||

## <a name="create-action"></a>Crear acción

La habilitación de una **acción de creación** representa un botón encima de la cuadrícula que, cuando se selecciona, abre un cuadro de diálogo con un [formulario de entidad](entity-forms.md) que permite a un usuario crear un nuevo registro.  

### <a name="create-action-settings"></a>Crear configuración de acción

| Nombre                  | Descripción                                                                                                                                                                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                                                                                                                             |
| Formulario de la entidad           | Especifica los [formularios de entidad y la lógica personalizada](entity-forms.md) que se usará para crear el nuevo registro. La lista desplegable incluye todos los formularios de entidad que están configurados para el tipo de entidad de subcuadrícula.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene ningún formulario de entidad, la lista desplegable aparecerá vacía. Si no se proporciona ningún formulario de entidad para la acción de creación, se omitirá y el botón no se representará en el formulario de la entidad de la subcuadrícula.                                |
| **Configuración avanzada** |                                                                                                                                                                                                                                                             |
| Etiqueta del botón          | Invalida la etiqueta HTML que se muestra en el botón crear acción situado encima de la subcuadrícula.                                                                                                                                                                           |
| Información sobre herramientas del botón        | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón crear acción.                                                                                                                                                            |

### <a name="create-form-dialog-box-advanced-settings"></a>Cuadro de diálogo Crear formulario Configuración avanzada

| Nombre                   | Descripción                                                                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Invalida el mensaje que aparece mientras se carga el cuadro de diálogo.                                                                                  |
| Título                  | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                                 |
| Descartar texto de Sr | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                                   |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Crear formulario. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es grande. |
| Clase CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                    |
| Title CSS (clase)        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                        |
||

## <a name="download-action"></a>Acción de descarga

Al habilitar una **acción de descarga** , se presenta un botón encima de la cuadrícula que, cuando se selecciona, descarga los datos de la subcuadrícula en un archivo [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)] (. xlsx).

### <a name="download-action-settings"></a>Descargar configuración de acción

| Nombre                  | Descripción                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                    |
| Ninguna                  |                                                                                                    |
| **Configuración avanzada** |                                                                                                    |
| Etiqueta del botón          | Invalida la etiqueta HTML que se muestra en el botón Descargar acción situado encima de la subcuadrícula.                |
| Información sobre herramientas del botón        | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón Descargar acción. |
||

## <a name="associate-action"></a>Asociar acción

Al habilitar una **acción de asociación** , se muestra un botón encima de la cuadrícula que, cuando se selecciona, abre una tabla de entidades que el usuario puede asociar al registro de la entidad que se muestra actualmente en el formulario de la [entidad](entity-forms.md), siempre que los datos anexados y [Los permisos de entidad](assign-entity-permissions.md) se han concedido a los privilegios appendto para los tipos de entidad aplicables.  

### <a name="associate-action-settings"></a>Asociar configuración de acción

| Nombre                  | Descripción                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                                                                                            |
| Visores                  | Especifica la vista (consulta guardada) que se utilizará para buscar y mostrar la lista de entidades válidas.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene ninguna consulta guardada, la lista desplegable aparecerá vacía. Si no se proporciona ninguna vista para la acción de asociación, se omitirá y el botón no se representará en el formulario de la entidad de la subcuadrícula.  |
| **Configuración avanzada** |                                                                                                                                                                                                                            |
| Etiqueta del botón          | Invalida la etiqueta HTML que se muestra en el botón asociar acción situado encima de la subcuadrícula.                                                                                                                                       |
| Información sobre herramientas del botón        | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón asociar acción.                                                                                                                        |
||

### <a name="lookup-dialog-box-advanced-settings"></a>Configuración avanzada del cuadro de diálogo de búsqueda

| Nombre                     | Descripción                                                                                                                                 |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Título                    | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                             |
| Texto del botón primario      | Invalida el código HTML que aparece en el botón principal (agregar) del cuadro de diálogo.                                                                |
| Cerrar texto del botón        | Invalida el código HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                               |
| Descartar texto de Sr   | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                               |
| Tamaño                     | Especifica el tamaño del cuadro de diálogo asociar. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es grande. |
| Clase CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                |
| Title CSS (clase)          | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                    |
| Clase CSS de botón principal | Especifique una clase o clases CSS que se aplicarán al botón principal (agregar) del cuadro de diálogo.                                                 |
| Botón Cerrar (clase CSS)   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                |
| Seleccionar el título de los registros     | Invalida el código HTML que aparece en el título del área de selección de registros.                                                                  |
| Mensaje de error predeterminado    | Reemplaza el mensaje que aparece cuando se produce un error al asociar la entidad o entidades seleccionadas.                                  |
| Opciones de cuadrícula             | Especifique la configuración de la apariencia de la cuadrícula de entidades. Consulte a continuación las opciones.                                                              |
||

### <a name="lookup-dialog-box-advanced-grid-options-settings"></a>Cuadro de diálogo de búsqueda configuración avanzada de opciones de cuadrícula

| Nombre                  | Descripción                                                                                                              |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje       | Invalida el mensaje que aparece mientras se carga la cuadrícula de entidades.                                                |
| Mensaje de error         | Invalida el mensaje que aparece cuando se produce un error al cargar la cuadrícula de entidades.                               |
| Mensaje de acceso denegado | Invalida el mensaje que aparece cuando un usuario no tiene suficientes permisos de entidad para ver la cuadrícula de entidades. |
| Mensaje vacío         | Invalida el mensaje que aparece cuando no hay entidades que se puedan asociar al formulario de la entidad actual.       |
| Clase CSS             | Especifique una clase o clases CSS que se aplicarán al área de cuadrícula asociada.                                          |
| Grid CSS (clase)        | Especifique una clase o clases CSS que se aplicarán a la tabla &lt;&gt; elemento de la cuadrícula asociada.                       |
||

## <a name="details-action"></a>Acción de detalles

La habilitación de una **acción de detalles** permite al usuario ver un [formulario de entidad](entity-forms.md) de solo lectura que está enlazado a datos con el registro de la fila seleccionada de la subcuadrícula.  

### <a name="details-action-settings"></a>Configuración de la acción de detalles

|                 Nombre                  |                                                                                                                                                                                                                        Descripción                                                                                                                                                                                                                        |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Configuración básica**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|              Formulario de la entidad              | Especifica el [formulario](entity-forms.md) de la entidad que se utilizará para ver los detalles del registro seleccionado. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la subcuadrícula. <br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene ningún formulario de entidad, la lista desplegable aparecerá vacía. Si no se proporciona ningún formulario de entidad para la acción de detalles, se omitirá y el botón no se representará en la subcuadrícula. |
|         **Configuración avanzada**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Nombre de parámetro de cadena de consulta de ID. de registro |                                                                      Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad que se va a ver en el formulario de la entidad seleccionada. Debe coincidir con el valor del nombre de parámetro de la cadena de consulta de ID. de registro del formulario de la entidad. El valor predeterminado de este campo, tanto aquí como en configuración de formulario de la entidad, es **ID**.                                                                       |
|             Etiqueta del botón              |                                                                                                                                                                                          Invalida la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                                                                                                                                                           |
|            Información sobre herramientas del botón             |                                                                                                                                                                 Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la subcuadrícula.                                                                                                                                                                  |
|                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### <a name="details-form-dialog-box-advanced-settings"></a>Cuadro de diálogo formulario de detalles configuración avanzada

| Nombre                   | Descripción                                                                                                                             |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Invalida el código HTML que aparece cuando se carga el cuadro de diálogo.                                                                             |
| Título                  | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                         |
| Descartar texto de Sr | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                           |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Detalles. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es grande. |
| Clase CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Title CSS (clase)        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |
||

## <a name="edit-action"></a>Editar acción

La habilitación de una **acción de edición** permite a un usuario ver un [formulario de entidad](entity-forms.md) editable que está enlazado a datos con el registro de la fila seleccionada de la subcuadrícula, si los permisos de la [entidad](assign-entity-permissions.md)han concedido el privilegio de escritura.  

### <a name="edit-action-settings"></a>Editar configuración de acción

| Nombre                                  | Descripción                                                                                                                                                                                                                                                                                                  |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**                    |                                                                                                                                                                                                                                                                                                              |
| Formulario de la entidad                           | Especifica el [formulario](entity-forms.md) de la entidad que se usará para editar el registro seleccionado. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la subcuadrícula.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene ningún formulario de entidad, la lista desplegable aparecerá vacía. Si no se proporciona ningún formulario de entidad para la acción de edición, se omitirá y el botón no se representará en la subcuadrícula.                                                                                                 |
| **Configuración avanzada**                 |                                                                                                                                                                                                                                                                                                              |
| Nombre de parámetro de cadena de consulta de ID. de registro | Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad que se va a editar en el formulario de la entidad seleccionada. Debe coincidir con el valor del nombre de parámetro de la cadena de consulta de ID. de registro del formulario de la entidad. El valor predeterminado de este campo, tanto aquí como en configuración de formulario de la entidad, es **ID**. |
| Etiqueta del botón                          | Invalida la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                                                                                                                                                                                                       |
| Información sobre herramientas del botón                        | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la subcuadrícula.                                                                                                                                                                              |
||

### <a name="edit-form-dialog-box-advanced-settings"></a>Cuadro de diálogo Editar formulario Configuración avanzada

| Nombre                   | Descripción                                                                                                                       |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Invalida el código HTML que aparece cuando se carga el cuadro de diálogo.                                                                       |
| Título                  | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                   |
| Descartar texto de Sr | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                     |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo de edición. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es grande. |
| Clase CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                      |
| Title CSS (clase)        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                          |
||

## <a name="delete-action"></a>Eliminar acción

La habilitación de una **acción de eliminación** permite al usuario eliminar permanentemente la entidad representada por una fila en la subcuadrícula, si los permisos de la [entidad](assign-entity-permissions.md)han concedido el privilegio de eliminación.  

### <a name="delete-action-settings"></a>Eliminar configuración de acción

| Nombre                  | Descripción                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                 |
| Ninguna                  |                                                                                                                                 |
| **Configuración avanzada** |                                                                                                                                 |
| Confirmación          | Invalida el mensaje HTML de confirmación que se muestra cuando el usuario activa la acción de eliminación.                                    |
| Etiqueta del botón          | Invalida la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                          |
| Información sobre herramientas del botón        | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la subcuadrícula. |
||

### <a name="delete-dialog-box-advanced-settings"></a>Eliminar configuración avanzada del cuadro de diálogo

| Nombre                     | Descripción                                                                                                                             |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Título                    | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                         |
| Texto del botón primario      | Invalida el código HTML que aparece en el botón principal (eliminar) del cuadro de diálogo.                                                         |
| Cerrar texto del botón        | Invalida el código HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                           |
| Descartar texto de Sr   | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                           |
| Tamaño                     | Especifica el tamaño del cuadro de diálogo eliminar. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es default. |
| Clase CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Title CSS (clase)          | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |
| Clase CSS de botón principal | Especifique una clase o clases CSS que se aplicarán al botón principal (eliminar) del cuadro de diálogo.                                          |
| Botón Cerrar (clase CSS)   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                            |
||

## <a name="workflow-action"></a>Acción de flujo de trabajo

La habilitación de una **acción de flujo de trabajo** permite a un usuario ejecutar un flujo de trabajo a petición en el registro seleccionado en la subcuadrícula. Puede agregar cualquier número de acciones de flujo de trabajo a los metadatos de la subcuadrícula.

### <a name="workflow-action-settings"></a>Configuración de la acción de flujo de trabajo

| Nombre                  | Descripción                                                                                                                                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                                                                                 |
| Flujo              | Especifica el flujo de trabajo a petición que se ejecutará cuando el usuario Active esta acción.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene ningún flujo de trabajo, la lista desplegable aparecerá vacía. Si no se proporciona ningún flujo de trabajo para la acción de flujo de trabajo, se omitirá y el botón no se representará en la subcuadrícula.  |
| Etiqueta del botón          | Establece la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula. Esta configuración es obligatoria.                                                                                                                     |
| **Configuración avanzada** |                                                                                                                                                                                                                 |
| Información sobre herramientas del botón        | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la subcuadrícula.                                                                                 |
||

## <a name="disassociate-action"></a>Acción de desasociación

Habilitar una **acción de desasociación** permite al usuario quitar el vínculo entre el registro representado por el formulario de la [entidad](entity-forms.md) que se está viendo actualmente y el registro representado por la fila seleccionada en la subcuadrícula, siempre y cuando los privilegios anexar y anexar tengan se han concedido por [los permisos de entidad](assign-entity-permissions.md) para los tipos de entidad aplicables.

### <a name="disassociate-action-settings"></a>Configuración de la acción de desasociación

| Nombre                  | Descripción                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                 |
| Ninguna                  |                                                                                                                                 |
| **Configuración avanzada** |                                                                                                                                 |
| Etiqueta del botón          | Invalida la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                          |
| Información sobre herramientas del botón        | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la subcuadrícula. |
||

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Propiedades de formularios Web para portales](web-form-properties.md)  
[Pasos de Web Form para portales](web-form-steps.md)  
[Metadatos de formularios Web Forms para portales](configure-web-form-metadata.md)  
[Configuración de notas para formularios Web Forms para portales](../configure-notes.md)  

