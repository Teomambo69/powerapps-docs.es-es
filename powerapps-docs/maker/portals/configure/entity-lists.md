---
title: Agregar una página web para representar una lista de registros en un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar listas de entidades para representar una lista de registros en un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761109"
---
# <a name="about-entity-lists"></a>Acerca de listas de entidades

Una lista de entidades es una configuración basada en datos que usa para agregar una página web que representará una lista de registros sin necesidad de que un programador muestre la cuadrícula en el portal. Al usar listas de entidades, puede exponer registros para mostrar en portales.

La cuadrícula admite la ordenación y se paginará si el número de registros es mayor que el tamaño de página especificado. Si la **página web para la vista de detalles** se ha especificado, cada registro contendrá un vínculo a la página y el identificador del registro se anexará a la cadena de consulta junto al nombre de parámetro de la cadena de consulta de Id. La lista de entidades también admite varias vistas. Si se ha especificado más de una vista, se representará una lista desplegable para permitir que el usuario cambie en las distintas vistas.

Los datos también se pueden filtrar por el usuario del portal actual, la cuenta del cliente principal del usuario del portal actual y el sitio web del portal actual. Si existe un valor para las condiciones de filtro **Atributo de usuario del portal** y **Atributo de cuenta**, el portal representará una lista desplegable para permitir que el usuario vea sus propios datos (Mis) o los datos de su cuenta de cliente principal.

## <a name="add-an-entity-list-to-your-portal"></a>Agregar una lista de entidades al portal

La lista de entidades contiene relaciones con páginas web y distintas propiedades para controlar la inicialización de la lista de registros dentro del portal. La relación con la página web permite la recuperación dinámica de la definición de lista para un determinado nodo de página en el sitio web. Para ver las vistas de entidad existentes o para crear nuevas vistas de entidad, vaya a **Portales** > **Listas de entidades**.

> [!Note]
> - Una lista de entidades debe estar asociada con una página web para un determinado sitio web para que la lista sea visible en el sitio.
> - El conjunto de opciones de selección múltiple no es compatible en listas de entidades.

Las páginas web asociadas a la lista de entidades se pueden ver al seleccionar el vínculo **Páginas web** mostrado en los vínculos de navegación **Relacionados** en el menú de la izquierda. Al crear la lista de entidades, el primer paso es elegir la entidad para la que desea representar una lista del portal. Después elegirá una o varias vistas de aplicación basada en modelo para representar.

Al crear o editar una página web, puede especificar una lista de entidades en el campo de búsqueda proporcionado en el formulario de la página web. La plantilla de página será normalmente la plantilla de "página", pero puede suele ser una de las otras plantillas diseñadas para contenido, ya que las plantillas maestras contienen la lógica necesaria para determinar si se debe representar una lista de entidades.

## <a name="entity-list-attributes-and-relationships"></a>Atributos y relaciones de la lista de entidades

|              Nombre              |                                                                                                                                                                                        Descripción                                                                                                                                                                                         |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Nombre              |                                                                                                                                                                Nombre descriptivo del registro. Este campo es obligatorio.                                                                                                                                                                 |
|          Nombre de entidad           |                                                                                                                                               El nombre de la entidad desde la que se cargará la vista de Búsqueda rápida. Este campo es obligatorio.                                                                                                                                               |
|              Vista              |                                                                          Las vistas de Búsqueda rápida de la entidad de destino que se va a representar. Este campo es obligatorio. Si se ha especificado más de una vista, la página web contendrá una lista desplegable para permitir que el usuario cambie en las distintas vistas.                                                                           |
|           Tamaño de página            |                                                                                                                                            Un valor entero que especifica el número de registros por página. Este campo es obligatorio. Valor predeterminado: 10                                                                                                                                             |
|   Página web para vista de detalles    |                                                                                                        Una página web opcional que se puede vincular para cada registro. El nombre de parámetro de cadena de consulta de id. y el identificador de registro se anexarán a la cadena de consulta de la dirección URL de esta página web.                                                                                                        |
|      Etiqueta del botón Detalles      |                     El texto que aparece para el botón de vista de detalles si se ha especificado la **página web para la vista de detalles**. Valor predeterminado: Ver detalles <br>**Nota**: Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado.                      |
|      Página web para crear       |                                                                                                                                                             Una página web opcional que será el destino del botón Crear.                                                                                                                                                              |
|      Etiqueta del botón Crear       |                              El texto que aparece para el botón Crear si se ha especificado **Página web para crear**. Valor predeterminado: Crear <br>**Nota**: Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado.                              |
| Nombre de parámetro de cadena de consulta de id. |                                                                                                                                           Un nombre de parámetro proporcionado en la cadena de consulta de la dirección URL de la Página web para vista de detalles. Valor predeterminado: id                                                                                                                                           |
|        Texto de lista vacía         |  **Obsoleto**.  El mensaje que se muestra cuando no hay registros.<br>**Nota**: Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado.                                                           |
|     Atributo de usuario del portal      |                                                                                      Un atributo de búsqueda opcional en la entidad principal que representa el registro de usuario del portal, contacto o usuario del sistema, al que se puede aplicar el identificador del usuario actual para filtrar los datos representados en la lista.                                                                                      |
|       Atributo de cuenta        |                                                                                       Un atributo de búsqueda opcional en la entidad principal que representa el registro de cuenta al que se puede aplicar el valor de cuenta de Cliente primario del contacto del usuario actual para filtrar los datos representados en la lista.                                                                                       |
|       Atributo de sitio web        |                                                                                                          Un atributo de búsqueda opcional en la entidad principal que representa el sitio web al que se puede aplicar el ID del sitio web actual para filtrar los datos representados en la lista.                                                                                                          |
|         Búsqueda habilitada         | Un valor booleano opcional que indica si se debe habilitar la búsqueda. Un cuadro de texto se generará para permitir a los usuarios realizar una búsqueda rápida de registros. Para realizar búsquedas de texto parcial, use el carácter comodín asterisco (\*). La búsqueda anexa filtros de condición 'or' para cada columna en la vista a las condiciones de filtro predefinidas existentes de la vista para consultar y devolver los registros resultantes. |
|    Texto de marcador de posición de búsqueda     |                                                                                                                                                      Una cadena opcional usada como la etiqueta que se muestra en el cuadro de texto en la carga inicial.                                                                                                                                                       |
|      Texto de información sobre herramientas de búsqueda       |                                                                                                                                             Una cadena opcional usada como información sobre herramientas que se muestra cuando el usuario apunta al cuadro de texto **Buscar**.                                                                                                                                              |
|                                |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="add-custom-javascript"></a>Agregar JavaScript personalizado

La pestaña Opciones del formulario contiene un área de texto en la que puede introducir [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] personalizado. Si la página incluye biblioteca de jQuery, puede usarla aquí también. El bloque de script se agregará en la parte inferior de la página web justo delante de la etiqueta de formulario de cierre de la página.

![Ejemplo de JavaScript personalizado](../media/custom-javascript-example.png "Ejemplo de JavaScript personalizado")  

La lista obtiene sus datos de forma asincrónica y, cuando está competa, desencadena un evento `loaded` que su [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] personalizado pueda escuchar y hacer algo con los elementos de la cuadrícula. El siguiente código es un ejemplo trivial:
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

Busque un campo de atributo particular y obtenga su valor para modificar posiblemente la representación del valor. El siguiente código obtiene cada celda de la tabla que contenga el valor del atributo `accountnumber`. Reemplace `accountnumber` con un atributo adecuado para la entidad y vista.
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
## <a name="entity-list-configuration"></a>Configuración de listas de entidades

Puede fácilmente habilitar y configurar acciones (crear, editar, eliminar, etc.) para registros en una lista de entidades. También es posible reemplazar etiquetas predeterminadas, tamaños y otro atributos para que la lista de entidades se muestre exactamente de la manera que desea.

Estos valores se encuentran en la sección Configuración del formulario de lista de entidades. De forma predeterminada, sólo aparece **Configuración básica**. Seleccione **Configuración avanzada** para ver configuración adicional.

![Configurar una lista de entidades](../media/configure-entitylist.png "Configurar una lista de entidades")  

**Atributos**

|Nombre                   |Descripción|
|---------------------------|-----------|
|**Configuración básica**         |   |
| Acciones de vista              |Úselo para agregar botones de acción para las acciones que son aplicables al conjunto de entidades y aparecerán encima de la cuadrícula. Las acciones disponibles son: <ul><li>Crear</li> <li>Descargar</li></ul> Seleccione una de estas opciones para mostrar un área de configuración para dicha acción.|
| Acciones de elementos             |Úselo para agregar los botones de acción para las acciones que son aplicables a un registro individual y aparecerán para cada fila de la cuadrícula siempre que el privilegio apropiado haya sido otorgado por permisos de entidad. Las acciones disponibles generalmente son:<ul><li>Detalles</li><li>Edición</li><li>Eliminar</li><li>Flujo de trabajo</li><li>Activar</li><li>Desactivar</li></ul> Seleccione una de estas opciones para mostrar un área de configuración para dicha acción. Consulte a continuación para obtener más información acerca de cada acción. Además, determinadas entidades tienen acciones específicas que están disponibles para estos por entidad:<ul><li>Calcular valor de oportunidad (oportunidad)</li><li>Cancelar acción del caso (incidente)</li><li>Cerrar (resolver) acción de caso (incidente)</li><li>Convierta oferta en pedido (oferta)</li><li>Convertir pedido en factura (salesorder)</li><li>Generar oferta a partir de oportunidad (oportunidad)</li><li>Perder acción de oportunidad (oportunidad)</li><li>Ganar acción de oportunidad (oportunidad)</li><li>Reabrir acción del caso (incidente)</li><li>Establecer oportunidad en espera (oportunidad)</li></ul>|
| Reemplazar atributos de columna|Úselo para reemplazar la configuración de presentación de las columnas individuales de la cuadrícula.<ul><li>Atributo: Nombre lógico de la columna que desea reemplazar.</li><li>Nombre para mostrar: Nuevo título de columna para reemplazar el predeterminado</li><li>Ancho: Ancho (en porcentaje o píxeles) de la columna para reemplazar el valor predeterminado. Vea también Estilo de ancho de columnas de cuadrícula</li></ul> Para reemplazar los valores de una columna, seleccione **+ Columna** y rellene los detalles.|
|**Configuración avanzada**      |  |
| Cargando mensaje           |Reemplaza el mensaje HTML predeterminado que aparece mientras se carga la cuadrícula.|
| Mensaje de error             |Reemplaza el mensaje HTML predeterminado que aparece cuando se produce un error mientras la cuadrícula se carga.|
| Mensaje de acceso denegado     |Reemplaza el mensaje HTML predeterminado que aparece cuando el usuario no tiene permisos de entidad suficientes para ver la lista de entidades.|
| Mensaje vacío             |Reemplaza el mensaje HTML que aparece cuando la cuadrícula no contiene datos.|
| Diálogo de formulario de detalles       |Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Detalles|
| Diálogo de editar formulario          |Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Editar|
| Diálogo de crear formulario        |Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Crear|
| Diálogo de eliminar             |Controla los valores del cuadro de diálogo que aparece cuando un usuario activa la acción Eliminar|
| Diálogo de error              |Controla los valores del cuadro de diálogo que aparece cuando se produce un error durante cualquier acción.|
| Clase de CSS                 |Especifique una clase o clases CSS que se aplicarán al elemento HTML que contiene el área completa de cuadrícula, incluida la cuadrícula y los botones de acción.|
| Clase CSS de cuadrícula            |Especifique una o varias clases CSS que se aplicarán al elemento \<table\> HTML de la lista de entidades.|
| Estilo de ancho de columnas de cuadrícula   |Configura si los valores **Ancho** en Reemplazar atributos de columna están especificados en **Píxeles** o **Porcentaje**.|

**Configuración general de acciones**

En general, las acciones de la entidad tienen valores que se pueden configurar. En todos los casos, este para ofrecerle más opciones en relación con la personalización, y los campos no son necesarios. Al agregar la acción simplemente podrá realizarse la acción en el portal, siempre que los permisos de la entidad hayan concedido el privilegio adecuado.

Generalmente, puede configurar el cuadro de diálogo correspondiente para cada acción, que aparecerá solo si se selecciona **Confirmación necesaria**.


| Nombre                   | Descripción                                                                                                                                                                                                                   |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**         |                                                                                                                                                                                                                               |
| ¿Se requiere confirmación? | Determina si una confirmación pedirá al usuario que confirme cuando se selecciona la acción.                                                                                                                                 |
| **Configuración avanzada**      |                                                                                                                                                                                                                               |
| Confirmación           | Reemplaza el mensaje HTML de confirmación que se muestra cuando el usuario activa la acción.                                                                                                                                         |
| Etiqueta de botón           | Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                    |
| Información sobre herramientas de botón         | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la lista de entidades.                                                                                           |
| Clase CSS del botón       | Agrega una clase CSS al botón.                                                                                                                                                      |
| Redireccionar a página web    | Algunas acciones (no todas) permiten un redireccionamiento al finalizar la acción. Sumamente recomendado para la acción Eliminar, opcional en la mayoría de los otros casos, puede elegir una página web a la que redirigir cuando se completa la acción. |
| URL de redireccionamiento           | Una alternativa a la opción **Redireccionar a página web**&mdash;permite redirigir a una dirección URL específica.                                                                                                                                   |

**Configuración avanzada del cuadro de diálogo General**

|**Nombre**                 |**Descripción**                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Cargo                    | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.|                                                                         
| Texto del botón primario      | Reemplaza el HTML que aparece en el botón Principal (Eliminar) del cuadro de diálogo.                                                         |
| Texto del botón Cerrar        | Reemplaza el HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                           |
| Texto del lector de pantalla del botón Descartar   | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                           |
| Tamaño                     | Especifica el tamaño de cuadro de diálogo Eliminar. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Predeterminado. |
| Clase de CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Clase CSS de título           | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |
| Clase CSS del botón primario | Especifique una clase o clases CSS que se aplicarán al botón Principal (Eliminar) del cuadro de diálogo.                                          |
| Clase CSS del botón Cerrar   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                            |

**Configuración de la Acción Crear**

Habilitar una **Acción Crear** representa un botón sobre la lista de entidades, cuando se selecciona, abre un cuadro de diálogo con un formulario de entidad que permite al usuario crear un nuevo registro, siempre que los permisos de la entidad hayan concedido el privilegio "Crear".

| Nombre               | Descripción                          |
|--------------------|--------------------------------------|
| **Configuración básica**     |                                                                                                                                                                       |
| Formulario de entidad     | Especifica el formulario de entidad que se usará para crear el nuevo registro. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la lista de entidades. <br>**Nota**: Si el tipo de entidad de la lista de entidades no tiene formularios de entidad, la lista desplegable aparecerá vacía. Si no se proporciona un formulario de entidad para la acción Crear, se ignorará y el botón no se representará en la lista de entidades. |
| **Configuración avanzada**          |                                                                                                                                                                       |
| Etiqueta de botón                                                                                                                                                                                                                 | Reemplaza la etiqueta HTML mostrada en el botón de acción Crear encima de la lista.                                                                                        |
| Información sobre herramientas de botón                                                                                                                                                                                                               | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón de acción Crear.                                                                         |

**Configuración avanzada del cuadro de diálogo Crear formulario**

|**Nombre**               |**Descripción**                                                                                                                                 |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Reemplaza el mensaje que aparece mientras el cuadro de diálogo se carga.                                                                                  |
| Cargo                  | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                                  |
| Texto del lector de pantalla del botón Descartar | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                                   |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Crear formulario. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Grande. |
| Clase de CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                                    |
| Clase CSS de título        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                        |

**Configuración de la Acción Descargar**

Habilitar una **Acción Descargar** representa un botón encima de la lista de entidades que, cuando se selecciona, descarga los datos de la lista en un archivo [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)] (.xlsx).

| Nombre              | Descripción                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                    |
| Ninguna              |                                                                                                    |
| **Configuración avanzada** |                                                                                                    |
| Etiqueta de botón      | Reemplaza la etiqueta HTML mostrada en el botón de acción Descargar encima de la lista de entidades.            |
| Información sobre herramientas de botón    | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón de acción Descargar. |

**Configuración de la Acción Detalles**

Habilitar una **Acción Detalles** permite al usuario ver un formulario de entidad de solo lectura de una fila seleccionada en la lista de entidades.


|                 Nombre                  |                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                      |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Configuración básica**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              Formulario de entidad              | Especifica el formulario de entidad que se usará para ver los detalles de la entidad seleccionada. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la lista de entidades. <br> **Nota**: Si el tipo de entidad de la lista de entidades no tiene formularios de entidad, la lista desplegable aparecerá vacía. Si no se proporciona un formulario de entidad para la acción Detalles, se ignorará y el botón no se representará en la lista de entidades. |
|         **Configuración avanzada**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Nombre del parámetro de cadena de consulta de id. de registro |                                                                    Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad para ver en el formulario de entidad seleccionado. Este debe coincidir con el valor de Nombre del parámetro de cadena de consulta de id. de registro de ese formulario de entidad. El valor predeterminado de este campo, aquí y en la configuración del formulario de entidad, es **id**.                                                                     |
|             Etiqueta de botón              |                                                                                                                                                                                      Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                                                       |
|            Información sobre herramientas de botón             |                                                                                                                                                             Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                              |

**Configuración avanzada del cuadro de diálogo Detalles**

|**Nombre**               |**Descripción**                                                                                                                         |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Reemplaza el HTML que aparece cuando el cuadro de diálogo se carga.                                                                             |
| Cargo                  | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                         |
| Texto del lector de pantalla del botón Descartar | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                           |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Detalles. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Grande. |
| Clase de CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Clase CSS de título        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |

**Configuración de la Acción Editar**

Habilitar una **Acción Editar** permite al usuario ver un formulario de entidad editable que está enlazado a datos al registro de la fila seleccionada de la lista de entidades siempre que los permisos de entidad hayan concedido el privilegio de 'Escritura'.


|                 Nombre                  |                                                                                                                                                                                                             Descripción                                                                                                                                                                                                             |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Configuración básica**           |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|              Formulario de entidad              | Especifica el formulario de entidad que se usará para editar la entidad seleccionada. La lista desplegable incluirá todos los formularios de entidad que estén configurados para el tipo de entidad de la lista de entidades. <br> **Nota**: Si el tipo de entidad de la lista de entidades no tiene formularios de entidad, la lista desplegable aparecerá vacía. Si no se proporciona un formulario de entidad para la acción Editar, se ignorará y el botón no se representará en la lista de entidades. |
|         **Configuración avanzada**         |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Nombre del parámetro de cadena de consulta de id. de registro |                                                           Especifica el nombre del parámetro de cadena de consulta que se usará para seleccionar la entidad para editar en el formulario de entidad seleccionado. Este debe coincidir con el valor de Nombre del parámetro de cadena de consulta de id. de registro de ese formulario de entidad. El valor predeterminado de este campo, aquí y en la configuración del formulario de entidad, es **id**.                                                            |
|             Etiqueta de botón              |                                                                                                                                                                             Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                                              |
|            Información sobre herramientas de botón             |                                                                                                                                                    Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la lista de entidades.                                                                                                                                                     |

**Configuración avanzada del cuadro de diálogo Editar formulario**

|**Nombre**               |**Descripción**                                                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Cargando mensaje        | Reemplaza el HTML que aparece cuando el cuadro de diálogo se carga.                                                                       |
| Cargo                  | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                   |
| Texto del lector de pantalla del botón Descartar | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                     |
| Tamaño                   | Especifica el tamaño del cuadro de diálogo Editar. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Grande. |
| Clase de CSS              | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                      |
| Clase CSS de título        | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                          |

**Configuración de la Acción Eliminar**

Habilitar **Acción Eliminar** permite al usuario eliminar permanentemente el registro de la fila seleccionada de la lista de entidades, siempre que permisos de entidad haya concedido el privilegio 'Eliminar'.

| Nombre              | Descripción                                                                                                                         |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| **Configuración básica**    |                                                                                                                                     |
| ninguna              |                                                                                                                                     |
| **Configuración avanzada** |                                                                                                                                     |
| Confirmación      | Reemplaza el mensaje HTML de confirmación que se muestra cuando el usuario activa la acción Eliminar.                                        |
| Etiqueta de botón      | Reemplaza la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades.                                                          |
| Información sobre herramientas de botón    | Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la lista de entidades. |

**Configuración avanzada del cuadro de diálogo Eliminar**

|**Nombre**                 |**Descripción**                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Cargo                    | Reemplaza el HTML que aparece en la barra de título del cuadro de diálogo.                                                                         |
| Texto del botón primario      | Reemplaza el HTML que aparece en el botón Principal (Eliminar) del cuadro de diálogo.                                                         |
| Texto del botón Cerrar        | Reemplaza el HTML que aparece en el botón Cerrar (Cancelar) del cuadro de diálogo.                                                           |
| Texto del lector de pantalla del botón Descartar   | Reemplaza el texto del lector de pantalla asociado al botón Descartar del cuadro de diálogo.                                                           |
| Tamaño                     | Especifica el tamaño de cuadro de diálogo Eliminar. Las opciones son: Predeterminado, Grande y Pequeño. El tamaño predeterminado es Predeterminado. |
| Clase de CSS                | Especifique una clase o clases CSS que se aplicarán al cuadro de diálogo resultante.                                                            |
| Clase CSS de título          | Especifique una clase o clases CSS que se aplicarán a la barra de título del cuadro de diálogo resultante.                                                |
| Clase CSS del botón primario | Especifique una clase o clases CSS que se aplicarán al botón Principal (Eliminar) del cuadro de diálogo.                                          |
| Clase CSS del botón Cerrar   | Especifique una clase o clases CSS que se aplicarán al botón Cerrar (Cancelar) del cuadro de diálogo.                                            |

**Configuración de la Acción de flujo de trabajo**

Habilitar una **Acción de flujo de trabajo** permite al usuario ejecutar un flujo de trabajo a petición para el registro de la fila seleccionada de la lista de entidades. Puede agregar cualquier número de acciones de flujo de trabajo a la lista de entidades.


|         Nombre          |                                                                                                                                                           Descripción                                                                                                                                                           |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Configuración básica**   |                                                                                                                                                                                                                                                                                                                                 |
|       Flujo de trabajo        | Especifica el flujo de trabajo a petición que se ejecutará cuando el usuario active esta acción. <br> **Nota**: Si el tipo de entidad de la lista de entidades no tiene flujos de trabajo, la lista desplegable aparecerá vacía. Si no se proporciona un flujo de trabajo para la acción Flujo de trabajo, se ignorará y el botón no se representará en la lista de entidades. |
|     Etiqueta de botón      |                                                                                                                 Establece la etiqueta HTML para esta acción mostrada en la fila de la lista de entidades. Este ajuste es obligatorio.                                                                                                                 |
| **Configuración avanzada** |                                                                                                                                                                                                                                                                                                                                 |
|    Información sobre herramientas de botón     |                                                                                                  Reemplaza el texto de información sobre herramientas que aparece cuando el usuario apunta al botón para esta acción mostrada en la fila de la lista de entidades.                                                                                                   |

## <a name="securing-entity-lists"></a>Protección de listas de entidades

Para realizar una lista de entidades, debe configurar los permisos de entidad para la entidad para la que se muestran registros y también establecer el valor booleano **Habilitar permisos de entidad** en el registro de la lista de entidades en True.

El acto de proteger una lista de entidades asegurará que para cualquier usuario que tenga acceso a la página solo se muestran los registros para los que se ha concedido permiso. Esto se consigue mediante un filtro adicional que se agrega a las vistas de la aplicación basada en modelo que emergen a través de la lista. Este filtro filtrará solo los registros que son accesibles al usuario, mediante el permiso **Leer**.

Además, las acciones se definan para la lista respetarán los permisos correspondientes para dicha acción, registro a registro. Es decir, si tiene el permiso Editar para un registro, la acción Editar se habilitará para ese registro. Lo mismo se aplica a Eliminar, Crear, etc. Tenga en cuenta que si no hay ningún registro disponible, un mensaje que indica esto aparecerá cuando la lista se cargue.

Sin embargo, un buen diseño de la página web requiere que, si el usuario no tiene un rol con permisos para la entidad (es decir, nunca habrá una situación en la que no vea ningún registro), no debe obtener acceso a la página en absoluto. Idealmente, la página debe protegerse con permisos de acceso de página web.

## <a name="adding-a-view-details-page"></a>Agregar una página de detalles de vista

Al establecer la búsqueda de Página web para vista de detalles en una página web, los detalles de un registro enumerado en la cuadrícula pueden verse como de solo lectura o editados, en función de la configuración del formulario o de la página asociada.

Esta página puede ser una plantilla de página completamente personalizada, quizás creada con Liquid. El escenario más común es probablemente tener la página de detalles como una página web que contiene un formulario de entidad o un formulario web.

Lo importante es conocer que cada registro enumerado en la cuadrícula tendrá un hipervínculo a la página de detalles, y el vínculo contendrá un parámetro Cadena de consulta con nombre con el identificador del registro. El nombre de parámetro Cadena de consulta depende del Nombre de parámetro de cadena de consulta de id. especificado en la lista de entidades. La tarea final a tener en cuenta es que la página web de detalles de destino también debe conocer el nombre de este parámetro de Cadena de consulta para obtener el identificador del registro que debe consultar y cargar sus datos.

![Agregar una página de detalles de vista](../media/add-view-details-page.png "Agregar una página de detalles de vista")  

**Uso de un formulario de entidad para mostrar detalles**

Para crear un formulario de entidad consulte las instrucciones que se encuentran en la página [Formulario de entidad](entity-forms.md).

A continuación se describen los valores importantes que debe conocer para asegurarse de que el registro de la lista de entidades se carga en el formulario de entidad.

El Nombre del parámetro de cadena de consulta de id. de registro en el Formulario de entidad debe coincidir con Nombre de parámetro de cadena de consulta de id. en la lista de entidades.

El Modo puede ser Editar o Solo lectura según sus necesidades.

**Uso de un formulario web para mostrar detalles**

A continuación se describen los valores importantes que debe conocer para asegurarse de que el registro de la lista de entidades se carga en el formulario web.

El Nombre del parámetro de cadena de consulta de clave principal en Paso de formulario web debe coincidir con Nombre de parámetro de cadena de consulta de id. en la lista de entidades.

El Modo puede ser Editar o Solo lectura según sus necesidades.

**Uso de una página de detalles para la función Crear**

Puede usar una página personalizada, un formulario de entidad o un formulario web en el mismo modo para la función Crear. Esto es una alternativa a definir una acción Crear en el formulario. No puede definir una acción Crear *y* una página personalizada para Crear: definir una acción personalizada tiene prioridad.

Si asigna una página web a la búsqueda Crear en la lista de entidades, y no especifica una acción Crear mediante la Configuración, se representará un botón Crear en la lista; este botón vinculará al usuario a la página personalizada que se ha designado para Crear.

## <a name="entity-list-filter-configuration"></a>Configuración de filtro de listas de entidades

Agregar la capacidad de filtrar registros de una lista de entidad es fácil: habilite simplemente la opción de filtrado y luego seleccione uno o más tipos de filtro para mostrar a los usuarios. Es posible filtrar por un atributo que coincida con algo de texto proporcionado por el usuario, o seleccionar de una serie de opciones. Incluso puede diseñar prácticamente cualquier tipo de filtro que pueda imaginarse mediante Búsqueda avanzada.

**Habilitar el filtro de lista de entidades**

En la sección Filtro de metadatos, seleccione la casilla Habilitado. Esto agregará el área Filtro a la lista de entidades cuando se muestran. Hasta que haya definido por lo menos un tipo de filtro, aparecerá el cuadro vacío.

Puede definir cómo el área Filtro en la lista de entidades se representará con la opción Orientación. El valor predeterminado, Horizontal, representa el área Filtro por encima de la lista de entidades. Orientación vertical representa el área Filtro como un cuadro a la izquierda de la lista de entidades.

![Configuración de filtro de metadatos](../media/metadata-filter-settings.png "Configuración de filtro de metadatos")  

**Tipos de filtro**

|**Tipo de filtro**      |**Descripción**                                                                                                                                                                                                                               |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Filtro de texto          | Filtre la lista de entidades mediante un cuadro de texto para buscar texto coincidente en un atributo seleccionado de la entidad dada.                                                                                                                               |
| Conjunto de filtros de atributo | Filtre la lista de entidades mediante una serie de casillas, cada de las cuales intenta que su condición coincida con un atributo específico de la entidad dada.                                                                                           |
| Conjunto de búsquedas           | Filtre la lista de entidades mediante una serie de casillas, cada una de las cuales que representa una relación entre un registro para la entidad dada y un registro para una entidad relacionada.                                                                         |
| Conjunto de filtros de intervalo     | Es similar al conjunto de filtros de atributo, salvo que cada casilla puede representar dos condiciones en lugar de una (por ejemplo, mayor o igual que 0 AND menor que 100).                                                                    |
| Conjunto de listas desplegables dinámicas | Es similar a elegir un valor de una lista desplegable en un conjunto de filtros de atributo. El Conjunto de listas desplegables dinámicas no requiere que especifique las opciones de lista desplegable por las que filtrar; en su lugar, genera la lista completa de opciones cuando la lista de entidades se carga. |
| Conjunto de búsquedas dinámicas   | Es similar al conjunto de búsquedas. El Conjunto de búsquedas dinámicas no requiere que especifique las opciones de búsqueda por las que filtrar; en su lugar, genera la lista completa de opciones cuando la lista de entidades se carga.                                           |
| Filtro FetchXML      | Filtre la lista de entidades mediante una condición de filtro FetchXML.                                                                                                                                                                                     |

**Filtro de texto**

El Filtro de texto agrega un cuadro de texto al área Filtro de listas de entidades que está ligado a un atributo de tipo entidad de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades muestra solo aquellos registros cuyo atributo seleccionado contenga el valor.

Para agregar un filtro de texto, seleccione **+ Filtro de texto**.

![Agregar un filtro de texto](../media/add-text-filter.png "Agregar un filtro de texto")  

El filtro de texto usa los siguientes atributos:

|**Nombre**     |**Descripción**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atributo    | El nombre del atributo en el tipo de entidad seleccionado de la lista de entidades por el que filtrar. *Solo los atributos con el tipo Cadena son válidos para un filtro de texto.*                                                                                   |
| Nombre para mostrar | Reemplace la etiqueta para el filtro cuando se muestre la lista de entidades. De forma predeterminada, esto se establecerá automáticamente con el nombre del atributo seleccionado. |

**Conjunto de filtros de atributo**

El Conjunto de filtros de atributo agrega una serie de opciones por las que filtrar la lista de entidades, ligadas a un solo atributo de tipo de la entidad seleccionada de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades muestra solo aquellos registros que coinciden exactamente con al menos una de las opciones seleccionadas.

![Cofiguración de filtros de atributo](../media/set-attribute-filter.png "Cofiguración de filtros de atributo")

El Conjunto de filtros de atributo usa los siguientes atributos:

|**Nombre**     |**Descripción**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atributo    | El nombre del atributo en el tipo de entidad seleccionado de la lista de entidades por el que filtrar. Solo los atributos con los siguientes tipos son válidos para un filtro de texto: String, BigInt, Decimal, Double, Integer, Money, Picklist, DateTime y Boolean.
|Nombre | Reemplace la etiqueta para el filtro cuando se muestre la lista de entidades. De forma predeterminada, esto se establecerá automáticamente con el nombre del atributo seleccionado.
| Opciones |      Una colección de valores posibles por la que filtrar. Consulte más adelante para obtener más información.                                                                              |

**Opciones Conjunto de filtros de atributo**

Un Conjunto de filtros de atributo puede tener normalmente cualquier número de opciones, con las excepciones de lista desplegable y atributos booleanos. Un Conjunto de filtros de atributo booleano puede tener solo una o dos opciones&mdash;una opción True y una opción False. Un Conjunto de filtros de atributo de lista desplegable puede tener una opción para cada valor posible en la lista desplegable.

Las opciones tienen los siguientes atributos:

|**Nombre**     |**Descripción**                                                                                                                                                                                  |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operador     | El operador de comparación usado para filtrar resultados, por ejemplo, iguales, menos que, etc. La lista de operadores de la opción dependerá del tipo de atributo seleccionado para el filtro. Por ejemplo, los tipos numéricos (Decimal) tendrán operadores como Menor que o Mayor que, donde los atributos de Cadena utilizarán Operadores como Empieza por o Contiene. Los operadores de lista desplegable y booleanos siempre son Es igual a.                                                                                                                                               |
| Valor        | El valor real usado para esta condición de filtro.                                                                                                                                                 |
| Nombre | Reemplaza el nombre para mostrar para esta opción en el cuadro Filtro. De forma predeterminada, esto se establecerá con el mismo valor que el atributo Valor.                                                             |

**Conjunto de búsquedas**

El Conjunto de búsquedas agrega una serie de opciones por las que filtrar la lista de entidades, ligadas a una entidad relacionada con el tipo de la entidad seleccionada de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades muestra solo aquellos registros que coinciden exactamente con al menos uno de los registros seleccionados.

![Conjunto de búsquedas](../media/lookup-set.png "Conjunto de búsquedas")  

El Conjunto de búsquedas usa los siguientes atributos:

|**Nombre**     |**Descripción**                                                                                                                                           |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Relación | El nombre de la entidad relacionada con el tipo de entidad seleccionado de la lista de entidades por el que filtrar. Solo las entidades con relaciones de uno a varios o de varios a varios con el tipo de entidad seleccionado de la lista de entidades aparecen como opciones para este tipo de filtro.          |
| Nombre | Reemplace la etiqueta para el filtro cuando se muestre la lista de entidades. De forma predeterminada, esto se establecerá automáticamente con el nombre de la relación seleccionada. |
| Opciones      | Una colección de valores posibles por la que filtrar. Consulte más adelante para obtener más información.                                                                                 |

**Opciones de conjunto de búsqueda**

Un conjunto de la búsqueda tiene normalmente varias opciones, con el único límite en el número de registros relacionados de tipo relacionado seleccionado.

Las opciones tienen los siguientes atributos:

|**Nombre**     |**Descripción**                                                                                                                      |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Valor        | El registro de tipo relacionado seleccionado por el que filtrar.                                                                                |
| Nombre | Reemplaza el nombre para mostrar para esta opción en el cuadro Filtro. De forma predeterminada, esto se establecerá con el mismo valor que el atributo Valor. |

**Conjunto de filtros de intervalo**

El Conjunto de filtros de intervalo agrega una serie de opciones, cada una con una o dos condiciones, al área Filtro. Cuando un usuario aplica el filtro, la lista de entidades muestra solo aquellos registros que coinciden exactamente con todas las condiciones en al menos una de las opciones seleccionadas.

![Configuración de filtros de intervalo](../media/set-range-filter.png "Configuración de filtros de intervalo")  

El conjunto de filtros de intervalo usa los siguientes atributos:

|**Nombre**     |**Descripción**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atributo    | El nombre del atributo en el tipo de entidad seleccionado de la lista de entidades por el que filtrar. Solo los atributos con los siguientes tipos son válidos para un filtro de texto: String, BigInt, Decimal, Double, Integer, Money y DateTime.                       |
| Nombre | Reemplace la etiqueta para el filtro cuando se muestre la lista de entidades. De forma predeterminada, esto se establecerá automáticamente con el nombre del atributo seleccionado. |
| Opciones      | Una colección de valores posibles por la que filtrar. Consulte más adelante para obtener más información.                                                                              |

**Opciones del Conjunto de filtros de intervalo**

Un Conjunto de filtros de intervalo puede tener varias opciones. Cada opción generará una condición de filtro con una o dos subcondiciones, que deben cumplirse para que la condición sea True.

Las opciones tienen los siguientes atributos:

|**Nombre**              |**Descripción**                                                                                                                                                                                |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operador 1            | El primer operador de comparación usado para filtrar resultados, por ejemplo, Es igual a y Es menor que. La lista de operadores de la opción dependerá del tipo de atributo seleccionado para el filtro. Por ejemplo, los tipos numéricos (Decimal) tendrán operadores como Menor que o Mayor que, donde los atributos de Cadena utilizarán Operadores como Empieza por o Contiene. Los operadores de lista desplegable y booleanos siempre son Es igual a.                                                                                                                                             |
| Valor 1               | El primer valor usado para esta condición de filtro.                                                                                                                                                |
| Operador 2 (opcional) | El segundo operador de comparación usado para filtrar resultados, por ejemplo, Es igual a y Es menor que. La lista de operadores de la opción dependerá del tipo de atributo seleccionado para el filtro. Por ejemplo, los tipos numéricos (Decimal) tendrán operadores como Menor que o Mayor que, donde los atributos de Cadena utilizarán Operadores como Empieza por o Contiene. Los operadores de lista desplegable y booleanos siempre son Es igual a.                                                                                                                                             |
| Valor 2 (opcional)    | El segundo valor usado para esta condición de filtro.                                                                                                                                               |
| Nombre          | Reemplaza el nombre para mostrar para esta opción en el cuadro Filtro. De forma predeterminada, se establecerá dinámicamente en función de los operadores y los valores seleccionados.                                         |

**Conjunto de listas desplegables dinámicas**

El Conjunto de listas desplegables dinámicas agrega una serie de opciones por las que filtrar que representan todos los valores de un campo de lista desplegable específico. Esto es diferente de seleccionar una lista desplegable en el Conjunto de filtros de atributo. En el Conjunto de filtros de atributo debe especificar un conjunto de opciones que estarán disponibles para el usuario para filtrar; en el Conjunto de lisas desplegables dinámicas solo debe especificar el campo de lista desplegable y el conjunto completo de opciones se proporcionará automáticamente. Si necesita mayor control, se recomienda usar el Conjunto de filtros de atributo.

![Configuración de listas desplegables dinámicas](../media/set-dynamic-picklist.png "Configuración de listas desplegables dinámicas")  

El Conjunto de listas desplegables dinámicas usa las siguientes opciones:

|**Nombre**     |**Descripción**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atributo    | El nombre del atributo de lista desplegable en el tipo de entidad seleccionado de la lista de entidades por el que filtrar.                                                             |
| Nombre | Reemplace la etiqueta para el filtro cuando se muestre la lista de entidades. De forma predeterminada, esto se establecerá automáticamente con el nombre del atributo seleccionado. |

**Conjunto de búsquedas dinámicas**

El Conjunto de búsquedas dinámicas agrega una serie de opciones por las que filtrar la lista de entidades, ligadas a una entidad relacionada con el tipo de la entidad seleccionada de la lista de entidades. Cuando un usuario aplica el filtro, la lista de entidades muestra solo aquellos registros que coinciden exactamente con al menos uno de los registros seleccionados.

Esto es diferente de un Conjunto de búsquedas. En el Conjunto de búsqueda, debe especificar manualmente las entidades relacionadas por las que filtrar. En el Conjunto de búsquedas dinámicas, debe especificar solo la relación por la que se va a filtrar, y una lista de opciones se generará en función de la vista especificada de entidades relacionadas.

![Configuración de búsquedas dinámicas](../media/set-dynamic-lookup.png "Configuración de búsquedas dinámicas")  

El Conjunto de búsquedas dinámicas usa las siguientes opciones:

|**Nombre**                      |**Descripción**                                                                                                                                                                      |
|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Relación                  | El nombre de la entidad relacionada con el tipo de entidad seleccionado de la lista de entidades por el que filtrar. Solo las entidades con relaciones de uno a varios o de varios a varios con el tipo de entidad seleccionado de la lista de entidades aparecen como opciones para este tipo de filtro.                                     |
| Vista                          | La Vista (consulta guardada) para usar como origen para la lista dinámica de entidades por la que filtrar.                                                                                              |
| Columna de etiqueta                  | El campo de la vista que proporciona el valor de Nombre de cada entidad.                                                                                                                    |
| Filtrar búsqueda por relación | Especifica una relación entre la entidad especificada por el campo Relación y el usuario que inició sesión. Si la entidad especificada por campo Relación también tiene una relación con un contacto, puede reducir la lista de opciones de filtro a los usuarios relacionados con el usuario que inició sesión.  |
| Nombre                  | Reemplace la etiqueta para el filtro cuando se muestre la lista de entidades. De forma predeterminada, esto se establecerá automáticamente con el nombre de la relación seleccionada.                            |

**Filtro FetchXML**

El filtro de intervalo puede crear un filtro de cuadro de texto básico como el filtro de texto, o un conjunto de opciones como otros tipos de filtro. Permite crear manualmente prácticamente cualquier tipo de filtro para la entidad de entidades mediante FetchXML.

![Configuración de filtros FetchXML](../media/set-fetchxml-filter.png "Configuración de filtros FetchXML")

El filtro FetchXML solo usa un atributo:

|**Nombre** |**Descripción**                            |
|----------|--------------------------------------------|
| FetchXML | La instrucción XML que representa el filtro. |

## <a name="entity-list-map-view"></a>Vista de mapa de listas de entidades

Con las listas de entidades es posible habilitar y configurar una vista de mapa de los datos, con tecnología de mapas de [!INCLUDE[pn-bing](../../../includes/pn-bing.md)] con la funcionalidad de búsqueda para buscar ubicaciones cerca de una dirección. Al rellenar los registros con valores de coordenadas de latitud y longitud y especificar las opciones de configuración necesarias enumeradas en esta sección, los registros se pueden representar como marcadores en un mapa. Cualquier registro que no tenga un valor de latitud o longitud quedará excluido de la búsqueda. La carga inicial de la página mostrará todos los registros en el valor inicial del campo Valores de distancia (en millas o kilómetros, según las unidades de distancia especificadas) de las coordenadas de Latitud del centro predeterminada y Longitud del centro predeterminada. La vista especificada se omite cuando se usa la vista de mapa, y una consulta de distancia se aplica al conjunto de datos para devolver resultados de mapa.
>[!Note] 
>Esta opción no se admite en el entorno de la nube soberana alemana. La sección de la vista de mapa no estará visible en este entorno.


## <a name="entity-list-calendar-view"></a>Vista de calendario de lista de entidades

Use la Vista de calendario de lista de entidades para representar una lista de entidades como calendario, con cada registro individual configurado para actuar como un solo evento.

Para mostrar los registros mediante un calendario, esos registros deben incluir como mínimo un campo de fecha. Para que los eventos tengan horas de inicio y finalización exactos, los campos correspondientes deben existir, etc. Si se supone que estos campos estén configurados, una vista de calendario de lista de entidades aparecerá en el portal.

## <a name="enhanced-view-filter-for-entity-lists"></a>Filtro de vista mejorado para listas de entidades

Si está habilitada, una entidad se puede publicar a una fuente de OData. El protocolo OData es un protocolo a nivel de aplicación para interactuar con datos a través de servicios web RESTful. Los datos de esta fuente se pueden ver en un explorador web, consumir por una aplicación web del lado del cliente, o importar a [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)].

## <a name="entity-list-odata-feeds"></a>Fuentes de OData de la lista de entidades

Puede usar permisos de la entidad si desea proteger los registros, pero si desea proporcionar simplemente un filtro como parte del conjunto de opciones de filtro que corresponde al usuario del portal actual, puede usar la función lista de entidades. Esta característica admite el filtro de usuario actual, de la cuenta primaria del usuario, o una página web en cualquier profundidad. Simplemente cree el filtro de la vista para que coincida con cualquier registro de contacto único, y el código reemplazará la configuración con el valor real en tiempo de ejecución, sin la necesidad de asignar valores a los campos de la sección Condiciones de filtro.

> [!Note]
> La fuente OData que se publica es anónima y no tiene comprobaciones de autorización; por tanto, es importante no habilitar las fuentes OData para los datos que son inadecuados para el acceso anónimo al portal.

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Redireccionar a una nueva dirección URL en un portal](add-redirect-url.md)  
