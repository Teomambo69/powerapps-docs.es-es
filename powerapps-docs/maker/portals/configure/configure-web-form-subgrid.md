---
title: Configuración de subcuadrícula de formulario web para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar las subcuadrículas de un formulario web para un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761115"
---
# <a name="configure-web-form-subgrids-for-portals"></a>Configurar subcuadrículas de formulario web para los portales

Los subcuadrículas de formularios web se configuran en modo idéntico a las subcuadrículas de formularios de entidad: primero, cree un registro de los metadatos para el paso de formulario web que tiene un subcuadrícula y luego agregue los metadatos de configuración.

Agregar subcuadrículas a los formularios administrados en el portal es sencillo: simplemente agregue la subcuadrícula al formulario que está administrando a través del diseñador de formularios y ya está. La cuadrícula usará la vista que se especifica en el diseñador de formularios de Common Data Service, mostrará solo los registros relacionados si esa opción se eligió en , opcionalmente mostrará una barra de búsqueda, e incluso concederá [permisos de entidad para portales](assign-entity-permissions.md). No puede ser más sencillo mostrar una lista de solo lectura de registros. Para habilitar acciones para la cuadrícula —Crear, Actualizar, Eliminar, etc.—, debe configurar esas acciones mediante las configuraciones de metadatos.

## <a name="add-subgrid-metadata-to-your-form"></a>Agregar metadatos de subcuadrícula al formulario

Para agregar metadatos de subcuadrícula a un formulario de entidad, vaya a **Metadatos del formulario de entidad** con la lista desplegable superior o la subcuadrícula en el formulario principal del registro con el que trabaja. Más información: [Definir formularios de entidad](entity-forms.md).

Seleccione **Agregar nuevos metadatos del formulario de entidad** para agregar un nuevo registro.

Para editar un registro existente, seleccione el registro en la cuadrícula. La selección de **Subcuadrícula** como el valor de **Tipo** muestra otro atributo, **Nombre de subcuadrícula**.


|     Nombre     |                                                       Descripción                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------|
| Nombre de subcuadrícula | El nombre único de la subcuadrícula en el formulario relacionado de la entidad. |
|              |                                                                                                                          |

Al seleccionar la subcuadrícula en el editor de formularios se mostrará una ventana de propiedades. Esta contiene un campo **Nombre** que debe usarse para asignar al campo **Nombre de subcuadrícula** en el registro de metadatos del formulario de entidad.

![Agregar metadatos de subcuadrícula](../media/add-subgrid-metadata.png "Agregar metadatos de subcuadrícula")  

Al especificar un nombre de subcuadrícula válido se mostrará la configuración de subcuadrícula. De forma predeterminada, sólo aparece **Configuración básica**. Seleccione **Configuración avanzada** para mostrar configuración adicional.

La mayoría de los valores se muestran contraídos para ahorrar espacio de forma predeterminada. Haga clic en **** para expandir una sección y ver opciones adicionales. Seleccione **** para contraer la sección.

## <a name="attributes"></a>Atributos

| Nombre                       | Descripción                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**         |                                                                                                                                                                                                                                                                                                                                                                           |
| Acciones de vista               | Úselo para agregar botones de acción para las acciones que son aplicables al conjunto de entidades y aparecerán encima de la subcuadrícula. Las acciones disponibles son: <ul><li>Crear</li><li>Descargar</li><li>Asociar</li></ul> Seleccione una de estas opciones para mostrar un área de configuración para dicha acción. Consulte a continuación para obtener más información acerca de cada acción.                                                                                                                                                                                                                                                   |
| Acciones de elemento               | Úselo para agregar los botones de acción para las acciones que son aplicables a un registro individual y aparecerán para cada fila de la subcuadrícula siempre que el privilegio asociado haya sido otorgado por [permisos de entidad](assign-entity-permissions.md). Las acciones disponibles son: <ul><li>Detalles</li><li>Edición</li><li>Eliminar</li><li>Flujo de trabajo</li><li>Desasociar</li></ul> Seleccione una de estas opciones para mostrar un área de configuración para dicha acción. Consulte a continuación para obtener más información acerca de cada acción.                                                                                                                                                                                                                                                   |
| Reemplazar atributos de columna | Úselo para reemplazar la configuración de presentación de las columnas individuales de la cuadrícula. <ul><li>Atributo: Nombre lógico de la columna que desea reemplazar.</li><li>Nombre para mostrar: Nuevo título de columna para reemplazar el predeterminado</li><li>Ancho: Ancho (en porcentaje o píxeles) de la columna para reemplazar el valor predeterminado. Vea también Estilo de ancho de columnas de cuadrícula. Para reemplazar los valores de una columna, seleccione **Columna** y rellene los detalles.                                                                                                                                                                                                                                                                                             |
| **Configuración avanzada**      |                                                                                                                                                                                                                                                                                                                                                                           |
| Cargando mensaje            | Reemplaza el mensaje HTML predeterminado que aparece mientras se carga la subcuadrícula.                                                                                                                                                                                                                                                                                             |
| Mensaje de error              | Reemplaza el mensaje HTML predeterminado que aparece cuando se produce un error mientras la subcuadrícula se carga.                                                                                                                                                                                                                                                                           |
| Mensaje de acceso denegado      | Reemplaza el mensaje HTML predeterminado que aparece cuando un usuario no tiene suficientes [permisos](assign-entity-permissions.md) para leer el tipo de entidad asociado a la subcuadrícula.                       |
| Mensaje vacío              | Reemplaza el mensaje HTML que aparece cuando la subcuadrícula asociada no contiene datos.                                                                                                                                                                                                                                                                                     |
| Diálogo de búsqueda              | Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Asociar.                                                                                                                                                                                                                                                                             |
| Diálogo de formulario de detalles        | Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Detalles                                                                                                                                                                                                                                                                                |
| Diálogo de editar formulario           | Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Editar                                                                                                                                                                                                                                                                                   |
| Diálogo de crear formulario         | Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Crear                                                                                                                                                                                                                                                                                 |
| Diálogo de eliminar              | Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Eliminar                                                                                                                                                                                                                                                                                 |
| Diálogo de error               | Controla los valores del cuadro de diálogo que aparece cuando se produce un error durante cualquier acción.                                                                                                                                                                                                                                                                                 |
| Clase de CSS                  | Especifique una clase o clases CSS que se aplicarán al elemento HTML que contiene el área completa de subcuadrícula, incluida la cuadrícula y los botones de acción.                                                                                                                                                                                                                     |
| Clase CSS de cuadrícula             | Especifique una clase o clases CSS que se aplicarán al elemento HTML &lt;table&gt; de la subcuadrícula.                                                                                                                                                                                                                                                                          |
| Estilo de ancho de columnas de cuadrícula    | Configura si los valores **Ancho** en Reemplazar atributos de columna están especificados en **Píxeles** o **Porcentaje**.                                                                                                                                                                                                                                                             |
||

## <a name="create-action"></a>Acción Crear

Habilitar una **Acción Crear** representa un botón encima de la subcuadrícula que, cuando se selecciona, abre un cuadro de diálogo con un [formulario de entidad](entity-forms.md) que permite al usuario crear un nuevo registro.  

### <a name="create-action-settings"></a>Configuración de la Acción Crear

| Nombre                  | Descripción                                                                                                                                                                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                                                                                                                             |
| Formulario de entidad           | Especifica los [formularios de entidad y la lógica personalizada](entity-forms.md) que se usarán para crear el nuevo registro. La lista desplegable incluye todos los formularios de entidad que se configuraron para el tipo de entidad de la subcuadrícula.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene formularios de entidad, la lista desplegable aparecerá vacía. Si no se proporciona un formulario de entidad para la acción Crear, se ignorará y el botón no se representará en el formulario de entidad de la subcuadrícula.                                |
| **Configuración avanzada** |                                                                                                                                                                                                                                                             |
| Etiqueta de botón          | Reemplaza la etiqueta HTML mostrada en el botón Acción Crear encima de la subcuadrícula.                                                                                                                                                                           |
| Información sobre herramientas de botón        | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón de acción Crear.                                                                                                                                                            |

### <a name="create-form-dialog-box-advanced-settings"></a>Configuración avanzada del cuadro de diálogo Crear formulario

| Nombre                   | Descripción                                                                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Reemplaza el mensaje que aparece mientras el diálogo se carga.                                                                                  |
| Cargo                  | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                                 |
| Texto del lector de pantalla del botón Descartar | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                                   |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Crear formulario. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Grande. |
| Clase de CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                    |
| Clase CSS de título        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                        |
||

## <a name="download-action"></a>Acción Descargar

Habilitar una **Acción Descargar** representa un botón encima de la subcuadrícula que, cuando se selecciona, descarga los datos de la subcuadrícula en un archivo de [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)] (.xlsx).

### <a name="download-action-settings"></a>Configuración de la Acción Descargar

| Nombre                  | Descripción                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                    |
| Ninguna                  |                                                                                                    |
| **Configuración avanzada** |                                                                                                    |
| Etiqueta de botón          | Reemplaza la etiqueta HTML mostrada en el botón Acción Descargar encima de la subcuadrícula.                |
| Información sobre herramientas de botón        | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón de acción Descargar. |
||

## <a name="associate-action"></a>Acción Asociar

Habilitar una **Acción Asociar** muestra un botón encima de la subcuadrícula que, cuando se selecciona, abre una tabla de entidades que el usuario puede elegir para asociar al registro de la entidad que está mostrando el [formulario de entidad](entity-forms.md), siempre que [Permisos de entidad](assign-entity-permissions.md) hayan concedido los privilegios Append y AppendTo para los tipos de entidad aplicables.  

### <a name="associate-action-settings"></a>Configuración de la Acción Asociar

| Nombre                  | Descripción                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                                                                                            |
| Vista                  | Especifica la vista (consulta guardada) que se usará para buscar y mostrar la lista de entidades elegibles.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene consultas guardadas, la lista desplegable aparecerá vacía. Si no se proporciona una vista para la acción Asociar, se ignorará y el botón no se representará en el formulario de entidad de la subcuadrícula.  |
| **Configuración avanzada** |                                                                                                                                                                                                                            |
| Etiqueta de botón          | Reemplaza la etiqueta HTML mostrada en el botón acción Asociar encima de la subcuadrícula.                                                                                                                                       |
| Información sobre herramientas de botón        | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón de acción Asociar.                                                                                                                        |
||

### <a name="lookup-dialog-box-advanced-settings"></a>Configuración avanzada del cuadro de diálogo Búsqueda

| Nombre                     | Descripción                                                                                                                                 |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Cargo                    | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                             |
| Texto del botón primario      | Reemplaza el HTML que aparece en el botón Principal (Agregar) del cuadro de diálogo.                                                                |
| Texto del botón Cerrar        | Reemplaza el HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                               |
| Texto del lector de pantalla del botón Descartar   | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                               |
| Tamaño                     | Especifica el tamaño del cuadro de diálogo Asociar. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Grande. |
| Clase de CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                |
| Clase CSS de título          | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                    |
| Clase CSS del botón primario | Especifique una clase o clases CSS que se aplicarán al botón Principal (Agregar) del cuadro de diálogo.                                                 |
| Clase CSS del botón Cerrar   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                                |
| Seleccionar título de registros     | Reemplaza el HTML que aparece en el título del área Selección de registro.                                                                  |
| Mensaje de error predeterminado    | Reemplaza el mensaje que aparece cuando se produce un error al asociar la entidad o entidades seleccionadas.                                  |
| Opciones de cuadrícula             | Especifique la configuración del aspecto de la cuadrícula de entidad. Vea a continuación las opciones.                                                              |
||

### <a name="lookup-dialog-box-advanced-grid-options-settings"></a>Configuración avanzada de opciones de cuadrícula del cuadro de diálogo Búsqueda

| Nombre                  | Descripción                                                                                                              |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje       | Reemplaza el mensaje que aparece mientras se carga la cuadrícula de entidades.                                                |
| Mensaje de error         | Reemplaza el mensaje que aparece cuando se produce un error mientras se carga la cuadrícula de entidades.                               |
| Mensaje de acceso denegado | Reemplaza el mensaje que aparece cuando el usuario no tiene permisos de entidad suficientes para ver la cuadrícula de entidades. |
| Mensaje vacío         | Reemplaza el mensaje que aparece cuando no hay entidades que se puedan asociar con el formulario de entidad actual.       |
| Clase de CSS             | Especifique una clase o clases CSS que se aplicará al área de cuadrícula asociada.                                          |
| Clase CSS de cuadrícula        | Especifique una clase o clases CSS que se aplicarán al elemento &lt;table&gt; de la cuadrícula asociada.                       |
||

## <a name="details-action"></a>Acción Detalles

Habilitar **Acción Detalles** permite al usuario ver un [formulario de entidad](entity-forms.md) de solo lectura que esté enlazado a datos al registro de la fila seleccionada de la subcuadrícula.  

### <a name="details-action-settings"></a>Configuración de la Acción Detalles

|                 Nombre                  |                                                                                                                                                                                                                        Descripción                                                                                                                                                                                                                        |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Configuración básica**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|              Formulario de entidad              | Especifica el [formulario de entidad](entity-forms.md) que se usará para ver los detalles del registro seleccionado. La lista desplegable incluirá todos los formularios de entidad que se configuren para el tipo de entidad de la subcuadrícula. <br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene formularios de entidad, el desplegable aparecerá vacío. Si no se proporciona una formulario de entidad para la acción Detalles, se ignorará y el botón no se representará en la subcuadrícula. |
|         **Configuración avanzada**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Nombre del parámetro de cadena de consulta de id. de registro |                                                                      Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad para ver en el formulario de entidad seleccionado. Este debe coincidir con el valor de Nombre del parámetro de cadena de consulta de id. de registro de ese formulario de entidad. El valor predeterminado de este campo, aquí y en la configuración del formulario de entidad, es **id**.                                                                       |
|             Etiqueta de botón              |                                                                                                                                                                                          Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                                                                                                                                                           |
|            Información sobre herramientas de botón             |                                                                                                                                                                 Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la subcuadrícula.                                                                                                                                                                  |
|                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### <a name="details-form-dialog-box-advanced-settings"></a>Configuración avanzada del cuadro de diálogo Formulario de detalles

| Nombre                   | Descripción                                                                                                                             |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Reemplaza el HTML que aparece cuando el cuadro de diálogo se carga.                                                                             |
| Cargo                  | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                         |
| Texto del lector de pantalla del botón Descartar | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                           |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Detalles. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Grande. |
| Clase de CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Clase CSS de título        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |
||

## <a name="edit-action"></a>Acción Editar

Habilitar una **Acción Editar** permite al usuario ver un [formulario de entidad](entity-forms.md) editable que está enlazado a datos al registro de la fila seleccionada de la subcuadrícula, si el privilegio Write ha sido concedido por [Permisos de entidad](assign-entity-permissions.md).  

### <a name="edit-action-settings"></a>Configuración de la Acción Editar

| Nombre                                  | Descripción                                                                                                                                                                                                                                                                                                  |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**                    |                                                                                                                                                                                                                                                                                                              |
| Formulario de entidad                           | Especifica el [formulario de entidad](entity-forms.md) que se usará para editar el registro seleccionado. La lista desplegable incluirá todos los formularios de entidad que se configuren para el tipo de entidad de la subcuadrícula.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene formularios de entidad, la lista desplegable aparecerá vacía. Si no se proporciona una formulario de entidad para la acción Editar, se ignorará y el botón no se representará en la subcuadrícula.                                                                                                 |
| **Configuración avanzada**                 |                                                                                                                                                                                                                                                                                                              |
| Nombre del parámetro de cadena de consulta de id. de registro | Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad para editar en el formulario de entidad seleccionado. Este debe coincidir con el valor de Nombre del parámetro de cadena de consulta de id. de registro de ese formulario de entidad. El valor predeterminado de este campo, aquí y en la configuración del formulario de entidad, es **id**. |
| Etiqueta de botón                          | Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                                                                                                                                                                                                       |
| Información sobre herramientas de botón                        | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la subcuadrícula.                                                                                                                                                                              |
||

### <a name="edit-form-dialog-box-advanced-settings"></a>Configuración avanzada del cuadro de diálogo Editar formulario

| Nombre                   | Descripción                                                                                                                       |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Reemplaza el HTML que aparece cuando el cuadro de diálogo se carga.                                                                       |
| Cargo                  | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                   |
| Texto del lector de pantalla del botón Descartar | Reemplaza el texto del lector de pantalla asociado al botón Descartar del diálogo.                                                     |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Editar. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Grande. |
| Clase de CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                      |
| Clase CSS de título        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                          |
||

## <a name="delete-action"></a>Acción Eliminar

Habilitar una **Acción Eliminar** permite al usuario eliminar permanentemente la entidad representada por una fila en la subcuadrícula, si el privilegio Delete haya sido concedido por [Permisos de entidad](assign-entity-permissions.md).  

### <a name="delete-action-settings"></a>Configuración de la Acción Eliminar

| Nombre                  | Descripción                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                 |
| Ninguna                  |                                                                                                                                 |
| **Configuración avanzada** |                                                                                                                                 |
| Confirmación          | Reemplaza el mensaje HTML de confirmación que se muestra cuando el usuario activa la acción Eliminar.                                    |
| Etiqueta de botón          | Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                          |
| Información sobre herramientas de botón        | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la subcuadrícula. |
||

### <a name="delete-dialog-box-advanced-settings"></a>Configuración avanzada del cuadro de diálogo Eliminar

| Nombre                     | Descripción                                                                                                                             |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Cargo                    | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                         |
| Texto del botón primario      | Reemplaza el HTML que aparece en el botón Principal (Eliminar) del cuadro de diálogo.                                                         |
| Texto del botón Cerrar        | Reemplaza el HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                           |
| Texto del lector de pantalla del botón Descartar   | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                           |
| Tamaño                     | Especifica el tamaño de cuadro de diálogo Eliminar. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Predeterminado. |
| Clase de CSS                | Especifique una clase o clases CSS que se aplicará al diálogo resultante.                                                            |
| Clase CSS de título          | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |
| Clase CSS del botón primario | Especifique una clase o clases CSS que se aplicarán al botón Principal (Eliminar) del cuadro de diálogo.                                          |
| Clase CSS del botón Cerrar   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                            |
||

## <a name="workflow-action"></a>Acción flujo de trabajo

Habilitar **Acción de flujo de trabajo** permite al usuario ejecutar un flujo de trabajo a petición para el registro seleccionado en la subcuadrícula. Puede agregar cualquier número de acciones Flujo de trabajo a los metadatos de la subcuadrícula.

### <a name="workflow-action-settings"></a>Configuración de la Acción de flujo de trabajo

| Nombre                  | Descripción                                                                                                                                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                                                                                                 |
| Flujo de trabajo              | Especifica el flujo de trabajo a petición que se ejecutará cuando el usuario active esta acción.<br>**Nota**: Si el tipo de entidad de la subcuadrícula no tiene flujos de trabajo, la lista desplegable aparecerá vacía. Si no se proporciona un flujo de trabajo para la acción Flujo de trabajo, se ignorará y el botón no se representará en la subcuadrícula.  |
| Etiqueta de botón          | Establece la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula. Este ajuste es obligatorio.                                                                                                                     |
| **Configuración avanzada** |                                                                                                                                                                                                                 |
| Información sobre herramientas de botón        | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la subcuadrícula.                                                                                 |
||

## <a name="disassociate-action"></a>Acción Desasociar

Habilitar una **Acción Desasociar** permite que un usuario quite el vínculo entre el registro representado por el [formulario de entidad](entity-forms.md) mostrado actualmente y el registro representado por la fila seleccionada en la subcuadrícula, siempre que se hayan sido concedidos privilegios Append y AppendTo por [Permisos de entidad](assign-entity-permissions.md) para los tipos de entidad aplicables.

### <a name="disassociate-action-settings"></a>Configuración de la acción Desasociar

| Nombre                  | Descripción                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                 |
| Ninguna                  |                                                                                                                                 |
| **Configuración avanzada** |                                                                                                                                 |
| Etiqueta de botón          | Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la subcuadrícula.                                                          |
| Información sobre herramientas de botón        | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la subcuadrícula. |
||

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Propiedades del formulario web para portales](web-form-properties.md)  
[Pasos de formulario web para portales](web-form-steps.md)  
[Metadatos de formularios web para portales](configure-web-form-metadata.md)  
[Configuración de notas para formularios web para portales](../configure-notes.md)  

