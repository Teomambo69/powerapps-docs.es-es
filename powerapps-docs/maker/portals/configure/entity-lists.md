---
title: Agregar una página web para presentar una lista de registros en un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar las listas de entidades para presentar una lista de registros en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 1ab175f69fdcf292185fd96cb176045dccc3a70b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552851"
---
# <a name="about-entity-lists"></a>Acerca de las listas de entidades

Una lista de entidades es una configuración controlada por datos que se usa para agregar una página web que representará una lista de registros sin necesidad de que un desarrollador muestre la cuadrícula en el portal. Mediante el uso de listas de entidades, puede exponer registros para su presentación en portales.

La cuadrícula admite la ordenación y se paginará si el número de registros es mayor que el tamaño de página especificado. Si se ha especificado una **Página Web para la vista de detalles** , cada registro contendrá un vínculo a la página y el identificador del registro se anexará a la cadena de consulta junto con el nombre del parámetro de cadena de consulta de identificador. La lista de entidades también admite varias vistas. Si se especifica más de una vista, se representará una lista desplegable para permitir que el usuario cambie entre las distintas vistas.

Los datos también se pueden filtrar por el usuario actual del portal, la cuenta de cliente primaria del usuario del portal actual y el sitio web del portal actual. Si existe un valor para el atributo de **usuario del portal** de condiciones de filtro y el **atributo de cuenta**, el portal presentará una lista desplegable para permitir al usuario ver sus propios datos (mis) o los datos de su cuenta de cliente primaria.

## <a name="add-an-entity-list-to-your-portal"></a>Agregar una lista de entidades al portal

La lista de entidades contiene relaciones con las páginas web y distintas propiedades para controlar la inicialización de la lista de registros dentro del portal. La relación con la página web permite la recuperación dinámica de la definición de lista para un nodo de página determinado dentro del sitio Web. Para ver las vistas de entidad existentes o crear nuevas vistas de entidad, vaya a **portales** > **listas de entidades**.

> [!Note]
> - Una lista de entidades debe estar asociada a una página web en un sitio Web determinado para que la lista se pueda ver en el sitio.
> - No se admite el conjunto de opciones de selección múltiple en las listas de entidades.

Las páginas web asociadas a la lista de entidades se pueden ver seleccionando el vínculo **páginas web** que se muestra en los vínculos de navegación **relacionados** en el menú de la izquierda. Al crear la lista de entidades, el primer paso es elegir la entidad para la que desea representar una lista en el portal. A continuación, elegirá una o varias vistas de aplicaciones controladas por modelos para representarlas.

Al crear o editar una página web, puede especificar una lista de entidades en el campo de búsqueda proporcionado en el formulario de la Página Web. La plantilla de página normalmente será la plantilla de página, pero puede ser una de las otras plantillas diseñadas para el contenido, ya que las plantillas maestras contienen la lógica necesaria para determinar si se debe representar una lista de entidades.

## <a name="entity-list-attributes-and-relationships"></a>Atributos y relaciones de la lista de entidades

|              Nombre              |                                                                                                                                                                                        Descripción                                                                                                                                                                                         |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Nombre              |                                                                                                                                                                Nombre descriptivo del registro. Este campo es obligatorio.                                                                                                                                                                 |
|          Nombre de entidad           |                                                                                                                                               Nombre de la entidad desde la que se cargará la vista de consulta guardada. Este campo es obligatorio.                                                                                                                                               |
|              Visores              |                                                                          Vistas de consulta guardadas de la entidad de destino que se van a representar. Este campo es obligatorio. Si se ha especificado más de una vista, la página web contendrá una lista desplegable para permitir que el usuario cambie entre las distintas vistas.                                                                           |
|           Tamaño de página            |                                                                                                                                            Valor entero que especifica el número de registros por página. Este campo es obligatorio. Valor predeterminado: 10                                                                                                                                             |
|   Página Web para la vista de detalles    |                                                                                                        Una página web opcional que se puede vincular a para cada registro. El nombre del parámetro de cadena de consulta de identificador y el ID. de registro se anexarán a la cadena de consulta de la dirección URL a esta página web.                                                                                                        |
|      Etiqueta del botón detalles      |                     Texto que se muestra para el botón vista de detalles si se ha especificado la **Página Web para la vista de detalles** . Valor predeterminado: ver detalles <br>**Nota**: para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado.                      |
|      Página Web para crear       |                                                                                                                                                             Una página web opcional que será el destino del botón crear.                                                                                                                                                              |
|      Crear etiqueta del botón       |                              Texto que se muestra para el botón crear si se ha especificado la **Página Web para crear** . Valor predeterminado: crear <br>**Nota**: para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado.                              |
| Nombre de parámetro de cadena de consulta de identificador |                                                                                                                                           Un nombre de parámetro proporcionado en la cadena de consulta de la dirección URL de la página web para la vista de detalles. Valor predeterminado: ID.                                                                                                                                           |
|        Texto de lista vacío         |  En **desuso**.  Mensaje que se muestra cuando no hay registros.<br>**Nota**: para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado.                                                           |
|     Atributo de usuario del portal      |                                                                                      Atributo de búsqueda opcional en la entidad principal que representa el registro de usuario del portal, ya sea contacto o usuario del sistema, al que se puede aplicar el identificador del usuario actual para filtrar los datos representados en la lista.                                                                                      |
|       Atributo de cuenta        |                                                                                       Atributo de búsqueda opcional en la entidad principal que representa un registro de cuenta en el que se puede aplicar el valor de la cuenta de cliente primaria del contacto del usuario actual para filtrar los datos representados en la lista.                                                                                       |
|       Atributo de sitio web        |                                                                                                          Atributo de búsqueda opcional en la entidad principal que representa el sitio web al que se puede aplicar el identificador del sitio web actual para filtrar los datos representados en la lista.                                                                                                          |
|         Búsqueda habilitada         | Un valor booleano opcional que indica si la búsqueda debe estar habilitada. Se representará un cuadro de texto para permitir que los usuarios realicen una búsqueda rápida de registros. Use el carácter comodín de asterisco (\*) para buscar texto parcial. La búsqueda anexa los filtros de condición o para cada columna de la vista a las condiciones de filtro predefinidas existentes de la vista para consultar y devolver los registros resultantes. |
|    Buscar texto de marcador de posición     |                                                                                                                                                      Cadena opcional utilizada como etiqueta mostrada en el cuadro de texto de la carga inicial.                                                                                                                                                       |
|      Buscar texto de información sobre herramientas       |                                                                                                                                             Cadena opcional utilizada como información sobre herramientas que se muestra cuando el usuario apunta al cuadro de texto de **búsqueda** .                                                                                                                                              |
|                                |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="add-custom-javascript"></a>Agregar JavaScript personalizado

La pestaña Opciones del formulario contiene un área de texto en la que puede escribir [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)]personalizado; Si la página incluye la biblioteca de jQuery, puede usarla aquí también. El bloque de script se agregará en la parte inferior de la página web justo antes de la etiqueta del formulario de cierre de la página.

![Ejemplo de JavaScript personalizado](../media/custom-javascript-example.png "Ejemplo de JavaScript personalizado")  

La lista obtiene sus datos de forma asincrónica y, cuando se completa, desencadenará un evento `loaded` que el [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] personalizado pueda escuchar y hacer algo con los elementos de la cuadrícula. El código siguiente es un ejemplo trivial:
```
$(document).ready(function (){
$(".entitylist.entity-grid").on("loaded", function () {
$(this).children(".view-grid").find("tr").each(function (){
// do something with each row
$(this).css("background-color", "yellow");
});
});
}); 
```

Busque un campo de atributo determinado y obtenga su valor para modificar posiblemente la representación del valor. El código siguiente obtiene cada celda de la tabla que contiene el valor del atributo `accountnumber`. Reemplace `accountnumber` por un atributo adecuado para su entidad y vista.
```
$(document).ready(function (){
   $(".entitylist.entity-grid").on("loaded", function () {
      $(this).children(".view-grid").find("td[data-attribute='accountnumber']").each(function (i, e){
         var value = $(this).data(value);
         // now that you have the value you can do something to the value
      });
   });
});
```
## <a name="entity-list-configuration"></a>Configuración de la lista de entidades

Puede habilitar y configurar fácilmente las acciones (crear, editar, eliminar, etc.) para los registros de una lista de entidades. También es posible invalidar etiquetas, tamaños y otros atributos predeterminados para que la lista de entidades se muestre exactamente como se desea.

Esta configuración se encuentra en la sección configuración del formulario lista de entidades. De forma predeterminada, solo se muestra la **configuración básica** . Seleccione **Configuración avanzada** para ver la configuración adicional.

![Configurar una lista de entidades](../media/configure-entitylist.png "Configurar una lista de entidades")  

**Sus**

|Nombre                   |Descripción|
|---------------------------|-----------|
|**Configuración básica**         |   |
| Ver acciones              |Use para agregar botones de acción para las acciones que se aplican al conjunto de entidades y que aparecerán encima de la cuadrícula. Las acciones disponibles son: <ul><li>A</li> <li>Download</li></ul> Al seleccionar una de estas opciones se muestra un área de configuración para esa acción.|
| Acciones de elementos             |Use para agregar botones de acción para las acciones que se aplican a un registro individual y que aparecerán para cada fila de la cuadrícula, siempre que los permisos de entidad hayan concedido el privilegio adecuado. Las acciones que están disponibles con carácter general son:<ul><li>Detalles</li><li>Editar</li><li>Elimínelos</li><li>Flujo</li><li>Activación</li><li>Desactivar</li></ul> Al seleccionar una de estas opciones se muestra un área de configuración para esa acción. Consulte a continuación los detalles de cada acción. Además, algunas entidades tienen acciones especiales que están disponibles para cada entidad:<ul><li>Calcular el valor de la oportunidad (oportunidad)</li><li>Cancelar acción de caso (incidente)</li><li>Cerrar (resolver) acción de caso (incidente)</li><li>Convertir comillas en pedido (comillas)</li><li>Convertir el orden en factura (SalesOrder)</li><li>Generar oferta a partir de la oportunidad (oportunidad)</li><li>Acción de la oportunidad de pérdida (oportunidad)</li><li>Acción de la oportunidad de ganar (oportunidad)</li><li>Volver a abrir acción de caso (incidente)</li><li>Establecimiento de la oportunidad en espera (oportunidad)</li></ul>|
| Reemplazar atributos de columna|Se usa para invalidar la configuración de presentación de columnas individuales en la cuadrícula.<ul><li>Attribute: nombre lógico de la columna que desea invalidar</li><li>Nombre para mostrar: nuevo título de columna para invalidar el valor predeterminado</li><li>Width: ancho (en porcentaje o píxeles) de la columna para reemplazar el valor predeterminado. Vea también estilo de ancho de columna de cuadrícula</li></ul> Para invalidar la configuración de una columna, seleccione **+ columna** y rellene los detalles.|
|**Configuración avanzada**      |  |
| Cargando mensaje           |Invalida el mensaje HTML predeterminado que aparece mientras se carga la cuadrícula.|
| Mensaje de error             |Invalida el mensaje HTML predeterminado que aparece cuando se produce un error al cargar la cuadrícula.|
| Mensaje de acceso denegado     |Invalida el mensaje HTML predeterminado que aparece cuando un usuario no tiene suficientes permisos de entidad para ver la lista de entidades.|
| Mensaje vacío             |Invalida el mensaje HTML que aparece cuando la cuadrícula no contiene datos.|
| Cuadro de diálogo formulario de detalles       |Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de detalles.|
| Cuadro de diálogo Editar formulario          |Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de edición.|
| Cuadro de diálogo Crear formulario        |Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de creación.|
| Cuadro de diálogo eliminar             |Controla la configuración del cuadro de diálogo que aparece cuando un usuario activa la acción de eliminación.|
| Cuadro de diálogo de error              |Controla la configuración del cuadro de diálogo que aparece cuando se produce un error durante cualquier acción.|
| Clase CSS                 |Especifique una clase o clases CSS que se aplicarán al elemento HTML que contiene el área de cuadrícula completa, incluidos los botones de acción y cuadrícula.|
| Grid CSS (clase)            |Especifique una clase o clases CSS que se aplicarán al elemento\> de la tabla de \<HTML de la lista de entidades.|
| Estilo de ancho de columna de cuadrícula   |Configura si los valores de **ancho** de los atributos de columna de invalidación se especifican en **píxeles** o como **porcentaje**.|

**Configuración de acción general**

En general, las acciones de entidad tienen opciones de configuración que se pueden configurar. En todos los casos, esto es para proporcionar más opciones en términos de personalización, y los campos no son necesarios. Basta con agregar la acción para que se realice la acción en el portal, siempre que los permisos de entidad hayan concedido el privilegio adecuado.

Por lo general, puede configurar el cuadro de diálogo correspondiente para cada acción, que solo aparecerá si selecciona **confirmación requerida**.


| Nombre                   | Descripción                                                                                                                                                                                                                   |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**         |                                                                                                                                                                                                                               |
| ¿Se requiere confirmación? | Determina si una confirmación solicitará al usuario que confirme cuando se selecciona la acción.                                                                                                                                 |
| **Configuración avanzada**      |                                                                                                                                                                                                                               |
| Confirmación           | Invalida el mensaje HTML de confirmación que se muestra cuando el usuario activa la acción.                                                                                                                                         |
| Etiqueta del botón           | Invalida la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                    |
| Información sobre herramientas del botón         | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la lista de entidades.                                                                                           |
| Button (clase CSS)       | Agrega una clase CSS al botón.                                                                                                                                                      |
| Redirigir a la página web    | Algunas acciones (no todas) permiten un redireccionamiento al completarse la acción. Muy recomendable para la acción de eliminación, opcional en la mayoría de los demás casos, puede elegir una página web a la que redirigirse cuando se complete la acción. |
| URL de redireccionamiento           | Una alternativa a la opción **redirigir a la página web**&mdash;permite redirigir a una dirección URL específica.                                                                                                                                   |

**Configuración avanzada del cuadro de diálogo general**

|**Nombre**                 |**Description**                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Título                    | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.|                                                                         
| Texto del botón primario      | Invalida el código HTML que aparece en el botón principal (eliminar) del cuadro de diálogo.                                                         |
| Cerrar texto del botón        | Invalida el código HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                           |
| Descartar texto de Sr   | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                           |
| Tamaño                     | Especifica el tamaño del cuadro de diálogo eliminar. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es default. |
| Clase CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Tile (clase CSS)           | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |
| Clase CSS de botón principal | Especifique una clase o clases CSS que se aplicarán al botón principal (eliminar) del cuadro de diálogo.                                          |
| Botón Cerrar (clase CSS)   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                            |

**Crear configuración de acción**

La habilitación de una **acción de creación** representa un botón encima de la lista de entidades que, cuando se selecciona, abre un cuadro de diálogo con un formulario de entidad que el usuario puede usar para crear un nuevo registro, siempre que los permisos de entidad hayan concedido el privilegio de creación.

| Nombre               | Descripción                          |
|--------------------|--------------------------------------|
| **Configuración básica**     |                                                                                                                                                                       |
| Formulario de la entidad     | Especifica el formulario de la entidad que se usará para crear el nuevo registro. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la lista de entidades. <br>**Nota**: Si el tipo de entidad de la lista de entidades no tiene ningún formulario de entidad, la lista desplegable aparecerá vacía. Si no se proporciona ningún formulario de entidad para la acción de creación, se omitirá y el botón no se representará en la lista de entidades. |
| **Configuración avanzada**          |                                                                                                                                                                       |
| Etiqueta del botón                                                                                                                                                                                                                 | Invalida la etiqueta HTML que se muestra en el botón crear acción situado encima de la lista.                                                                                        |
| Información sobre herramientas del botón                                                                                                                                                                                                               | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón crear acción.                                                                         |

**Cuadro de diálogo Crear formulario de la configuración de avance**

|**Nombre**               |**Description**                                                                                                                                 |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Invalida el mensaje que aparece mientras se está cargando el cuadro de diálogo.                                                                                  |
| Título                  | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                                  |
| Descartar texto de Sr | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                                   |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Crear formulario. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es grande. |
| Clase CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                    |
| Title CSS (clase)        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                        |

**Descargar configuración de acción**

Al habilitar una **acción de descarga** se representa un botón encima de la lista de entidades que, cuando se selecciona, descarga los datos de la lista en un archivo [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)] (. xlsx).

| Nombre              | Descripción                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                    |
| Ninguna              |                                                                                                    |
| **Configuración avanzada** |                                                                                                    |
| Etiqueta del botón      | Invalida la etiqueta HTML que se muestra en el botón Descargar acción situado encima de la lista de entidades.            |
| Información sobre herramientas del botón    | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón Descargar acción. |

**Configuración de la acción de detalles**

Al habilitar una **acción de detalles** , un usuario puede ver un formulario de entidad de solo lectura de una fila seleccionada en la lista de entidades.


|                 Nombre                  |                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                      |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Configuración básica**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              Formulario de la entidad              | Especifica el formulario de la entidad que se usará para ver los detalles de la entidad seleccionada. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la lista de entidades. <br> **Nota**: Si el tipo de entidad de la lista de entidades no tiene ningún formulario de entidad, la lista desplegable aparecerá vacía. Si no se proporciona ningún formulario de entidad para la acción de detalles, se omitirá y el botón no se representará en la lista de entidades. |
|         **Configuración avanzada**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Nombre de parámetro de cadena de consulta de ID. de registro |                                                                    Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad que se va a ver en el formulario de la entidad seleccionada. Debe coincidir con el valor del nombre de parámetro de la cadena de consulta de ID. de registro del formulario de la entidad. El valor predeterminado de este campo, tanto aquí como en configuración de formulario de la entidad, es **ID**.                                                                     |
|             Etiqueta del botón              |                                                                                                                                                                                      Invalida la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                                                       |
|            Información sobre herramientas del botón             |                                                                                                                                                             Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la lista de entidades.                                                                                                                                                              |

**Detalles configuración avanzada del cuadro de diálogo**

|**Nombre**               |**Description**                                                                                                                         |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Invalida el código HTML que aparece cuando se carga el cuadro de diálogo.                                                                             |
| Título                  | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                         |
| Descartar texto de Sr | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                           |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Detalles. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es grande. |
| Clase CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Title CSS (clase)        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |

**Editar configuración de acción**

Habilitar una **acción de edición** permite a un usuario ver un formulario de entidad editable que está enlazado a datos con el registro de la fila seleccionada de la lista de entidades, siempre que los permisos de entidad hayan concedido el privilegio de escritura.


|                 Nombre                  |                                                                                                                                                                                                             Descripción                                                                                                                                                                                                             |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Configuración básica**           |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|              Formulario de la entidad              | Especifica el formulario de la entidad que se usará para editar la entidad seleccionada. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la lista de entidades. <br> **Nota**: Si el tipo de entidad de la lista de entidades no tiene ningún formulario de entidad, la lista desplegable aparecerá vacía. Si no se proporciona ningún formulario de entidad para la acción de edición, se omitirá y el botón no se representará en la lista de entidades. |
|         **Configuración avanzada**         |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Nombre de parámetro de cadena de consulta de ID. de registro |                                                           Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad que se va a editar en el formulario de la entidad seleccionada. Debe coincidir con el valor del nombre de parámetro de la cadena de consulta de ID. de registro del formulario de la entidad. El valor predeterminado de este campo, tanto aquí como en configuración de formulario de la entidad, es **ID**.                                                            |
|             Etiqueta del botón              |                                                                                                                                                                             Invalida la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                                              |
|            Información sobre herramientas del botón             |                                                                                                                                                    Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la lista de entidades.                                                                                                                                                     |

**Cuadro de diálogo Editar formulario Configuración avanzada**

|**Nombre**               |**Description**                                                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Invalida el código HTML que aparece cuando se carga el cuadro de diálogo.                                                                       |
| Título                  | Invalida el código HTML que aparece en la barra de título del cuadro de diálogo.                                                                   |
| Descartar texto de Sr | Invalida el texto del lector de pantalla asociado al botón descartar del cuadro de diálogo.                                                     |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo de edición. Las opciones son predeterminadas, grandes y pequeñas. El tamaño predeterminado es grande. |
| Clase CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                      |
| Title CSS (clase)        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                          |

**Eliminar configuración de acción**

Al habilitar una **acción de eliminación** , el usuario puede eliminar de forma permanente el registro de la fila seleccionada de la lista de entidades, siempre que los permisos de entidad hayan concedido el privilegio de eliminación.

| Nombre              | Descripción                                                                                                                         |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                     |
| Ninguna              |                                                                                                                                     |
| **Configuración avanzada** |                                                                                                                                     |
| Confirmación      | Invalida el mensaje HTML de confirmación que se muestra cuando el usuario activa la acción de eliminación.                                        |
| Etiqueta del botón      | Invalida la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                          |
| Información sobre herramientas del botón    | Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la lista de entidades. |

**Eliminar configuración del cuadro de diálogo (avanzado)**

|**Nombre**                 |**Description**                                                                                                                         |
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

**Configuración de la acción de flujo de trabajo**

La habilitación de una **acción de flujo de trabajo** permite a un usuario ejecutar un flujo de trabajo a petición en el registro de la fila seleccionada de la lista de entidades. Puede agregar cualquier número de acciones de flujo de trabajo a la lista de entidades.


|         Nombre          |                                                                                                                                                           Descripción                                                                                                                                                           |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Configuración básica**   |                                                                                                                                                                                                                                                                                                                                 |
|       Flujo        | Especifica el flujo de trabajo a petición que se ejecutará cuando el usuario Active esta acción. <br> **Nota**: Si el tipo de entidad de la lista de entidades no tiene ningún flujo de trabajo, la lista desplegable aparecerá vacía. Si no se proporciona ningún flujo de trabajo para la acción de flujo de trabajo, se omitirá y el botón no se representará en la lista de entidades. |
|     Etiqueta del botón      |                                                                                                                 Establece la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades. Esta configuración es obligatoria.                                                                                                                 |
| **Configuración avanzada** |                                                                                                                                                                                                                                                                                                                                 |
|    Información sobre herramientas del botón     |                                                                                                  Invalida el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción que se muestra en la fila de la lista de entidades.                                                                                                   |

## <a name="securing-entity-lists"></a>Proteger listas de entidades

Para proteger una lista de entidades, debe configurar los permisos de entidad para la entidad para la que se muestran los registros y también establecer el valor booleano de **Habilitar permisos de entidad** en el registro de la lista de entidades en true.

La acción de proteger una lista de entidades garantizará que, para cualquier usuario que tenga acceso a la página, solo se muestren los registros a los que se les ha concedido permiso. Esto se logra mediante un filtro adicional que se agrega a las vistas de aplicaciones controladas por modelos que se muestran a través de la lista. Este filtro solo filtrará los registros que son accesibles para el usuario, mediante el permiso de **lectura** .

Además, las acciones que se hayan definido para la lista respetarán los permisos correspondientes para esa acción por registro. Es decir, si tiene permiso de edición para un registro, la acción de edición se habilitará para ese registro. Lo mismo se aplica a Delete, Create, etc. Tenga en cuenta que si no hay ningún registro disponible, se mostrará un mensaje que lo indicará cuando se cargue la lista.

Sin embargo, un buen diseño del sitio web requiere que, si un usuario no está en un rol que tenga permisos para la entidad (es decir, nunca habrá una situación en la que debería ver cualquier registro), no debería tener acceso a la página. Idealmente, la página debe protegerse mediante los permisos de acceso de la Página Web.

## <a name="adding-a-view-details-page"></a>Agregar una página de detalles de la vista

Al establecer la página web para la búsqueda de detalles de la vista en una página web, los detalles de un registro que aparece en la cuadrícula se pueden ver como de solo lectura o de edición, dependiendo de la configuración del formulario o la página asociados.

Esta página puede ser una plantilla de página completamente personalizada, tal vez creada con Liquid. Probablemente, el escenario más común es que la página de detalles sea una página web que contenga un formulario de entidad o un formulario Web Forms.

Lo importante que hay que tener en cuenta es que cada registro que aparece en la cuadrícula tendrá un hipervínculo a la página de detalles y el vínculo contendrá un parámetro de cadena de consulta con nombre con el identificador del registro. El nombre del parámetro de cadena de consulta depende del nombre del parámetro de cadena de consulta de identificador especificado en la lista de entidades. Lo último que hay que tener en cuenta es que la Página Web de detalles de destino también debe tener en cuenta el nombre de este parámetro de cadena de consulta para obtener el identificador del registro que necesita para consultar y cargar sus datos.

![Agregar página de detalles de la vista](../media/add-view-details-page.png "Agregar página de detalles de la vista")  

**Usar un formulario de entidad para mostrar detalles**

Para crear un formulario de entidad, consulte las instrucciones que se encuentran en la página formulario de la [entidad](entity-forms.md) .

A continuación se muestran los valores importantes que se deben tener en cuenta para asegurarse de que el registro de la lista de entidades se carga en el formulario de la entidad.

El nombre del parámetro de cadena de consulta de ID. de registro en el formulario de la entidad debe coincidir con el nombre del parámetro de cadena de consulta de ID.

El modo puede ser Edit o ReadOnly, dependiendo de sus necesidades.

**Usar un formulario web para mostrar detalles**

A continuación se muestran los valores importantes que se deben tener en cuenta para asegurarse de que el registro de la lista de entidades se carga en el formulario Web.

El nombre del parámetro de la cadena de consulta de la clave principal en el paso de Web Forms debe coincidir con el nombre del parámetro de cadena de consulta de ID.

El modo puede ser Edit o ReadOnly, dependiendo de sus necesidades.

**Usar una página de detalles para la función Create**

Puede usar una página personalizada, un formulario de entidad o un formulario Web Forms de la misma manera para la función Create. Se trata de una alternativa a la definición de una acción de creación en el formulario. No se puede definir una acción de creación *y* una página personalizada para crear: la definición de una acción personalizada tiene prioridad.

Si asigna una página web a la búsqueda de creación en la lista de entidades y no especifica una acción de creación mediante la configuración, se representará un botón crear en la lista. Este botón vinculará al usuario a la página personalizada que ha designado para crear.

## <a name="entity-list-filter-configuration"></a>Configuración del filtro de la lista de entidades

Agregar la capacidad de filtrar registros en una lista de entidades es fácil: simplemente habilite la opción de filtrado y, a continuación, elija uno o varios tipos de filtro para mostrar a los usuarios. Es posible filtrar por un atributo que coincida con el texto proporcionado por el usuario o seleccionar entre una serie de opciones. Incluso puede diseñar prácticamente cualquier tipo de filtro que pueda imaginar mediante la búsqueda avanzada.

**Habilitación del filtro de la lista de entidades**

En la sección filtro de metadatos, active la casilla habilitado. Esto agregará el área de filtro a la lista de entidades cuando se muestre. Hasta que haya definido al menos un tipo de filtro, el cuadro aparecerá vacío.

Puede definir cómo se representará el área de filtro en la lista de entidades mediante la configuración de orientación. El valor predeterminado, horizontal, representa el área de filtro por encima de la lista de entidades. Orientación vertical: representa el área de filtro como un cuadro a la izquierda de la lista de entidades.

![Configuración del filtro de metadatos](../media/metadata-filter-settings.png "Configuración del filtro de metadatos")  

**Tipos de filtro**

|**Tipo de filtro**      |**Description**                                                                                                                                                                                                                               |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Filtro de texto          | Filtre la lista de entidades mediante un cuadro de texto para buscar texto coincidente en un atributo seleccionado de la entidad determinada.                                                                                                                               |
| Conjunto de filtros de atributos | Filtre la lista de entidades mediante una serie de casillas, cada una de las cuales intenta coincidir su condición con un atributo determinado de la entidad determinada.                                                                                           |
| Conjunto de búsqueda           | Filtre la lista de entidades mediante una serie de casillas, cada una de las cuales representa una relación entre un registro de la entidad determinada y un registro para una entidad relacionada.                                                                         |
| Conjunto de filtros de intervalo     | Similar al conjunto de filtros de atributos, con la excepción de que cada casilla puede representar dos condiciones en lugar de una (por ejemplo, mayor o igual que 0 y menor que 100).                                                                    |
| Conjunto de listas desplegables dinámicas | Similar a elegir un valor de lista desplegable en un conjunto de filtros de atributos. No es necesario que especifique las opciones de lista desplegable por las que filtrar el conjunto de listas desplegables dinámicas. en su lugar, genera la lista completa de opciones cuando se carga la lista de entidades. |
| Conjunto de búsqueda dinámica   | Similar al conjunto de búsqueda. El conjunto de búsqueda dinámica no requiere que especifique las opciones de búsqueda por las que filtrar; en su lugar, genera la lista completa de opciones cuando se carga la lista de entidades.                                           |
| Filtro de FetchXML      | Filtre la lista de entidades mediante una condición de filtro FetchXML.                                                                                                                                                                                     |

**Filtro de texto**

El filtro de texto agrega un cuadro de texto al área de filtro de la lista de entidades que está asociada a un atributo del tipo de entidad de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades solo muestra los registros cuyo atributo seleccionado contiene el valor.

Para agregar un filtro de texto, seleccione **+ filtro de texto**.

![Agregar un filtro de texto](../media/add-text-filter.png "Agregar un filtro de texto")  

El filtro de texto usa los siguientes atributos:

|**Nombre**     |**Description**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atribui    | Nombre del atributo en el tipo de entidad seleccionado de la lista de entidades que se va a filtrar. *Solo los atributos con la cadena de tipo son válidos para un filtro de texto.*                                                                                   |
| Nombre para mostrar | Invalide la etiqueta del filtro cuando se muestre la lista de entidades. De forma predeterminada, se establecerá automáticamente en el nombre del atributo seleccionado. |

**Conjunto de filtros de atributos**

El conjunto de filtros de atributos agrega una serie de opciones para filtrar la lista de entidades, vinculada a un solo atributo del tipo de entidad seleccionado de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades solo muestra los registros que coinciden exactamente con al menos una de las opciones seleccionadas.

![Configuración de filtro de atributos](../media/set-attribute-filter.png "Configuración de filtro de atributos")

El conjunto de filtros de atributos usa los siguientes atributos:

|**Nombre**     |**Description**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atribui    | Nombre del atributo en el tipo de entidad seleccionado de la lista de entidades que se va a filtrar. Solo los atributos con los siguientes tipos son válidos para un filtro de texto: String, BigInt, decimal, Double, integer, Money, lista desplegable, DateTime y Boolean.
|Nombre para mostrar | Invalide la etiqueta del filtro cuando se muestre la lista de entidades. De forma predeterminada, se establecerá automáticamente en el nombre del atributo seleccionado.
| Opciones |      Colección de valores posibles por los que filtrar. Consulte a continuación para obtener más detalles.                                                                              |

**Opciones set de filtro de atributos**

Un conjunto de filtros de atributos normalmente puede tener cualquier número de opciones, con las excepciones de los atributos de lista desplegable y booleano. Un conjunto de filtros de atributo booleano solo puede tener una o dos opciones&mdash;una opción true y una opción false. Un conjunto de filtros de atributos de lista desplegable puede tener como máximo una opción para cada valor posible de la lista desplegable.

Las opciones tienen los siguientes atributos:

|**Nombre**     |**Description**                                                                                                                                                                                  |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator     | El operador de comparación utilizado para filtrar los resultados, por ejemplo, es igual a, menor que, etc. La lista de operadores de la opción dependerá del tipo de atributo seleccionado para el filtro. Por ejemplo, los tipos numéricos (decimal) tendrán operadores como menor que o mayor que, mientras que los atributos de cadena usarán operadores como Begins with o Contains. Los operadores de lista desplegable y booleano siempre son iguales.                                                                                                                                               |
| Value        | Valor real que se usa para esta condición de filtro.                                                                                                                                                 |
| Nombre para mostrar | Invalida el nombre para mostrar de esta opción en el cuadro de filtro. De forma predeterminada, se establecerá en el mismo valor que el atributo value.                                                             |

**Conjunto de búsqueda**

El conjunto de búsqueda agrega una serie de opciones para filtrar la lista de entidades, vinculada a una entidad relacionada con el tipo de entidad seleccionado de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades solo muestra los registros que coinciden exactamente con al menos uno de los registros relacionados seleccionados.

![Conjunto de búsqueda](../media/lookup-set.png "Conjunto de búsqueda")  

El conjunto de búsqueda utiliza los siguientes atributos:

|**Nombre**     |**Description**                                                                                                                                           |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Relación | Nombre de la entidad relacionada con el tipo de entidad seleccionado de la lista de entidades que se va a filtrar. Solo las entidades con una relación de uno a varios o de varios a varios con el tipo de entidad seleccionado de la lista de entidades aparecen como opciones para este tipo de filtro.          |
| Nombre para mostrar | Invalide la etiqueta del filtro cuando se muestre la lista de entidades. De forma predeterminada, se establecerá automáticamente en el nombre de la relación seleccionada. |
| Opciones      | Colección de valores posibles por los que filtrar. Consulte a continuación para obtener más detalles.                                                                                 |

**Opciones del conjunto de búsquedas**

Un conjunto de búsqueda normalmente puede tener cualquier número de opciones, y el único límite es el número de registros relacionados del tipo relacionado seleccionado.

Las opciones tienen los siguientes atributos:

|**Nombre**     |**Description**                                                                                                                      |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Value        | Registro del tipo relacionado seleccionado por el que se va a filtrar.                                                                                |
| Nombre para mostrar | Invalida el nombre para mostrar de esta opción en el cuadro de filtro. De forma predeterminada, se establecerá en el mismo valor que el atributo value. |

**Conjunto de filtros de intervalo**

El conjunto de filtros de intervalo agrega una serie de opciones, cada una con una o dos condiciones, al área de filtro. Cuando un usuario aplica el filtro, la lista de entidades solo muestra los registros que coinciden exactamente con todas las condiciones de al menos una de las opciones seleccionadas.

![Configuración del filtro de intervalo](../media/set-range-filter.png "Configuración del filtro de intervalo")  

El conjunto de filtros de intervalo usa los siguientes atributos:

|**Nombre**     |**Description**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atribui    | Nombre del atributo en el tipo de entidad seleccionado de la lista de entidades que se va a filtrar. Solo los atributos con los siguientes tipos son válidos para un filtro de texto: String, BigInt, decimal, Double, integer, Money, DateTime.                       |
| Nombre para mostrar | Invalide la etiqueta del filtro cuando se muestre la lista de entidades. De forma predeterminada, se establecerá automáticamente en el nombre del atributo seleccionado. |
| Opciones      | Colección de valores posibles por los que filtrar. Consulte a continuación para obtener más detalles.                                                                              |

**Opciones de conjunto de filtros de intervalo**

Un conjunto de filtros de intervalo puede tener cualquier número de opciones. Cada opción generará una condición de filtro con una o dos subcondiciones, ambas deben cumplirse para que la condición sea verdadera.

Las opciones tienen los siguientes atributos:

|**Nombre**              |**Description**                                                                                                                                                                                |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operador 1            | El primer operador de comparación utilizado para filtrar los resultados, por ejemplo, es igual a y menor que. La lista de operadores de la opción dependerá del tipo de atributo seleccionado para el filtro. Por ejemplo, los tipos numéricos (decimal) tendrán operadores como menor que o mayor que, mientras que los atributos de cadena usarán operadores como Begins with o Contains. Los operadores de lista desplegable y booleano siempre son iguales.                                                                                                                                             |
| Valor 1               | Primer valor que se usa para esta condición de filtro.                                                                                                                                                |
| Operador 2 (opcional) | Segundo operador de comparación utilizado para filtrar los resultados, por ejemplo, es igual a y menor que. La lista de operadores de la opción dependerá del tipo de atributo seleccionado para el filtro. Por ejemplo, los tipos numéricos (decimal) tendrán operadores como menor que o mayor que, mientras que los atributos de cadena usarán operadores como Begins with o Contains. Los operadores de lista desplegable y booleano siempre son iguales.                                                                                                                                             |
| Valor 2 (opcional)    | Segundo valor utilizado para esta condición de filtro.                                                                                                                                               |
| Nombre para mostrar          | Invalida el nombre para mostrar de esta opción en el cuadro de filtro. De forma predeterminada, se establecerá de manera dinámica, en función de los operadores y valores seleccionados.                                         |

**Conjunto de listas desplegables dinámicas**

El conjunto de listas desplegables dinámicas agrega una serie de opciones para filtrar por que representan todos los valores de un campo de lista desplegable especificado. Esto no es lo mismo que seleccionar una lista desplegable en el conjunto de filtros de atributos. En el conjunto de filtros de atributo, debe especificar un conjunto de opciones que se pondrá a disposición del usuario para filtrar; en el conjunto de listas desplegables dinámicas, solo es necesario especificar el campo de lista desplegable y el conjunto completo de opciones se proporcionará automáticamente. Si necesita un mayor control, se recomienda usar el conjunto de filtros de atributos.

![Configuración dinámica de la lista desplegable](../media/set-dynamic-picklist.png "Configuración dinámica de la lista desplegable")  

El conjunto de listas desplegables dinámicas usa las siguientes opciones:

|**Nombre**     |**Description**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atribui    | Nombre del atributo de lista desplegable en el tipo de entidad seleccionado de la lista de entidades que se va a filtrar.                                                             |
| Nombre para mostrar | Invalide la etiqueta del filtro cuando se muestre la lista de entidades. De forma predeterminada, se establecerá automáticamente en el nombre del atributo seleccionado. |

**Conjunto de búsqueda dinámica**

El conjunto de búsqueda dinámica agrega una serie dinámica de opciones para filtrar la lista de entidades por, vinculada a una entidad relacionada con el tipo de entidad seleccionado de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades solo muestra los registros que coinciden exactamente con al menos uno de los registros relacionados seleccionados.

Esto es diferente de un conjunto de búsqueda. En el conjunto de búsqueda, debe especificar manualmente las entidades relacionadas por las que filtrar. En el conjunto de búsqueda dinámica, solo es necesario especificar la relación en la que se va a filtrar y se generará una lista de opciones en función de la vista especificada de las entidades relacionadas.

![Configuración de búsqueda dinámica](../media/set-dynamic-lookup.png "Configuración de búsqueda dinámica")  

El conjunto de búsqueda dinámica utiliza las siguientes opciones:

|**Nombre**                      |**Description**                                                                                                                                                                      |
|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Relación                  | Nombre de la entidad relacionada con el tipo de entidad seleccionado de la lista de entidades que se va a filtrar. Solo las entidades con una relación de uno a varios o de varios a varios con el tipo de entidad seleccionado de la lista de entidades aparecen como opciones para este tipo de filtro.                                     |
| Visores                          | Vista (consulta guardada) que se va a usar como origen de la lista dinámica de entidades por las que filtrar.                                                                                              |
| Columna de etiqueta                  | Campo de la vista que proporciona el valor de nombre de cada entidad.                                                                                                                    |
| Filtrar la búsqueda en relación | Especifica una relación entre la entidad especificada por el campo de relación y el usuario con sesión iniciada. Si la entidad especificada por el campo de relación también tiene una relación con un contacto, puede restringir la lista de opciones de filtro a las relacionadas con el usuario que ha iniciado sesión.  |
| Nombre para mostrar                  | Invalide la etiqueta del filtro cuando se muestre la lista de entidades. De forma predeterminada, se establecerá automáticamente en el nombre de la relación seleccionada.                            |

**Filtro de FetchXML**

El filtro de intervalo puede crear un filtro de cuadro de texto simple, como el filtro de texto o un conjunto de opciones, como los demás tipos de filtro. Permite crear manualmente prácticamente cualquier tipo de filtro para la lista de entidades mediante FetchXML.

![Configuración del filtro de FetchXML](../media/set-fetchxml-filter.png "Configuración del filtro de FetchXML")

El filtro FetchXML solo usa un atributo:

|**Nombre** |**Description**                            |
|----------|--------------------------------------------|
| FetchXML | Instrucción XML que representa el filtro. |

## <a name="entity-list-map-view"></a>Vista de mapa de lista de entidades

Con las listas de entidades, es posible habilitar y configurar una vista de mapa de los datos, con la tecnología de [!INCLUDE[pn-bing](../../../includes/pn-bing.md)] Maps con funcionalidad de búsqueda para buscar ubicaciones cerca de una dirección. Al rellenar los registros con los valores de las coordenadas de latitud y longitud, y especificar las opciones de configuración necesarias enumeradas en esta sección, los registros se pueden representar como marcadores en un mapa. Los registros que no tengan un valor de latitud o longitud se excluirán de la búsqueda. La carga inicial de la página mostrará todos los registros dentro del valor inicial del campo Distance Values (en millas o km, en función de las unidades de distancia especificadas) de las coordenadas de la latitud predeterminada del centro y la longitud predeterminada del centro. La vista especificada se omite cuando se usa la vista de mapa y se aplica una consulta de distancia al conjunto de valores para devolver los resultados asignables.
>[!Note] 
>Esta opción no se admite en el entorno de nube soberano. La sección de la vista del mapa no será visible en este entorno.


## <a name="entity-list-calendar-view"></a>Vista de calendario de la lista de entidades

Use la vista de calendario de la lista de entidades para representar una lista de entidades como un calendario, con cada registro individual configurado para que actúe como un evento único.

Para mostrar los registros mediante un calendario, dichos registros deben incluirse en un campo de fecha como mínimo. Para que los eventos tengan horas de inicio y finalización exactas, los campos adecuados deben estar en su lugar, etc. Suponiendo que estos campos estén configurados, aparecerá una vista de calendario de la lista de entidades en el portal.

## <a name="enhanced-view-filter-for-entity-lists"></a>Filtro de vista mejorada para listas de entidades

Si está habilitada, se puede publicar una entidad en una fuente de OData. El protocolo OData es un protocolo de nivel de aplicación para interactuar con los datos a través de los servicios web RESTful. Los datos de esta fuente se pueden ver en un explorador Web, usar una aplicación web del lado cliente o importarse en [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)].

## <a name="entity-list-odata-feeds"></a>Fuentes OData de la lista de entidades

Puede usar permisos de entidad si desea proteger registros, pero si desea simplemente proporcionar un filtro como parte del conjunto de opciones de filtro que es relevante para el usuario actual del portal, puede usar la característica de lista de entidades. Esta característica permite filtrar el usuario actual, la cuenta primaria del usuario o el sitio web con cualquier nivel. Simplemente cree el filtro de vista para que coincida con cualquier registro de contacto único y el código reemplace su valor por el valor real en tiempo de ejecución&mdash;no es necesario asignar valores a los campos de la sección condiciones de filtro.

> [!Note]
> La fuente de OData que se publica es anónima y no tiene ninguna comprobación de autorización; por lo tanto, es importante no habilitar las fuentes de oData para los datos que no son adecuados para el acceso anónimo al portal.

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Redirigir a una nueva dirección URL en un portal](add-redirect-url.md)  
