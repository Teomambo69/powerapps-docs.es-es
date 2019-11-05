---
title: Metadatos de formularios Web para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar metadatos de formularios Web Forms para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 63e64fe49d62be944cc040a3539b0b717f5c2f84
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552989"
---
# <a name="configure-web-form-metadata-for-portals"></a>Configuración de metadatos de formularios Web Forms para portales

Los metadatos del formulario web contienen lógica adicional de modificación del comportamiento para aumentar o invalidar la funcionalidad de los campos de formulario que, de lo contrario, no son posibles con las funciones de edición de formularios de entidad nativa.

## <a name="add-a-new-record"></a>Agregar un nuevo registro

1. En el paso de formulario web que tiene los campos que desea modificar, vaya a **metadatos** de > **relacionados** . 

2. Seleccione **nuevos metadatos de formularios Web Forms**.

## <a name="web-form-metadata-properties"></a>Propiedades de metadatos de formularios Web

Los siguientes atributos proporcionan funciones y estilos adicionales para los elementos de un formulario.

| Nombre          | Descripción                                                                                                                                                                                                                                                                                                                                          |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Paso de formulario web | Paso del formulario web asociado al registro de metadatos de formularios Web Forms.                                                                                                                                                                                                                                                                                      |
| Tipo          | Las opciones disponibles son:<ul><li>Atribui</li><li>Sección</li><li>Pestaña</li></ul>Al seleccionar atributo como el valor de tipo se muestran las opciones adecuadas para modificar los campos en el formulario actual que se representan en el paso relacionado. Al seleccionar la sección como valor de tipo se muestran las opciones disponibles para modificar una sección del formulario. Al seleccionar Tab como el valor de tipo se muestran las opciones disponibles para modificar una pestaña en un formulario.  |

## <a name="web-form-metadata-type--attribute"></a>Tipo de metadatos del formulario web = atributo

Las siguientes propiedades se muestran cuando el tipo seleccionado es ' atributo '.


|          Nombre          |                                                                                                                                                    Descripción                                                                                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre lógico del atributo |                                                                                                                              Nombre lógico del campo de atributo que se va a modificar.                                                                                                                               |
|         Etiquetas          | Reemplaza la etiqueta predeterminada asignada al atributo en la entidad con el texto especificado en esta entrada. Para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado. |

### <a name="control-style"></a>Estilo de control

Las siguientes opciones modifican el estilo y la funcionalidad del campo de un atributo.


|                      Nombre                       |                                                                                                                                                                                                                                                                                                                                       Descripción                                                                                                                                                                                                                                                                                                                                       |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      Aplicar                      | Una de las siguientes opciones:<ul><li>Opción establecida como lista de botones de radio vertical</li><li>Opción establecida como lista de botones de radio horizontal</li><li>Una sola línea de texto como validador de búsqueda de ubicación geográfica (requiere la configuración de [!INCLUDE[pn-bing](../../../includes/pn-bing.md)] Maps; aquí encontrará los detalles)</li><li>Agrupar número entero como suma constante (requiere nombre de grupo)</li><li>Agrupar número entero como orden de clasificación no hay ningún valor de escala (requiere nombre de grupo)</li><li>Agrupar número entero como escala de orden de rango permitir vínculos (requiere nombre de grupo)</li><li>Matriz de varias opciones (requiere el nombre del grupo)</li><li>Varias opciones (requiere un nombre de grupo)</li><li>Agrupar número entero como rango de la pila (requiere el nombre del grupo)</li></u> |
|                   Nombre del grupo                    |                                                                                                                                                                                                                                                                                                             Nombre que se utiliza para agrupar controles como un control compuesto.                                                                                                                                                                                                                                                                                                              |
| Recuento seleccionado mínimo necesario de varias opciones |                                                                                                                                                                                                                                                                      Estos son los valores mínimos necesarios seleccionados en la pregunta de varias opciones. Solo es necesario si se selecciona el estilo de control ' selección múltiple '.                                                                                                                                                                                                                                                                       |
|       Recuento máximo seleccionado de varias opciones        |                                                                                                                                                                                                                                                          Es el número máximo de valores que se permite seleccionar en la pregunta de selección múltiple. Solo es necesario si se selecciona el estilo de control ' selección múltiple '.                                                                                                                                                                                                                                                          |
|           Total de suma constante            |                                                                                                                                                                                                                                                             Este es el valor mínimo necesario aplicado a un campo de respuesta de suma constante. Solo es necesario si se selecciona el estilo de control ' agrupar número entero como suma constante '.                                                                                                                                                                                                                                                              |
|           Total máximo de suma constante            |                                                                                                                                                                                                                                                 Es el número máximo de valores que se permite aplicar a un campo de respuesta de suma constante. Solo es necesario si se selecciona el estilo de control ' agrupar número entero como suma constante '.                                                                                                                                                                                                                                                 |
|           Valores de conjunto de opciones RANDOMIZE           |                                                                                                                                                                                                                                                                     Si se especifica sí, se muestran las opciones ordenadas aleatoriamente para un control de conjunto de opciones. Solo se aplica a los atributos que son de tipo Option set.                                                                                                                                                                                                                                                                     |
|                    Clase CSS                    |                                                                                                                                                                                                                                                                                                                      Agrega un nombre de clase CSS personalizado al control.                                                                                                                                                                                                                                                                                                                       |

### <a name="prepopulate-field"></a>Rellenar previamente el campo

Las siguientes opciones proporcionan un valor predeterminado para los campos del formulario.


|         Nombre         |                                                                                                                                                                                                                                                                Descripción                                                                                                                                                                                                                                                                 |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Omitir valor predeterminado |                                                                              Omite el valor predeterminado del campo de atributo especificado. Resulta útil para los atributos que son dos campos de opción que se representan como sí y sin botones de radio. Dado que un valor de sí o no se asigna automáticamente de forma predeterminada, esta opción permite mostrar preguntas de sí/no sin una respuesta predefinida.                                                                               |
|         Tipo         | Una de las siguientes opciones:<ul><li>Value</li><li>Fecha de hoy</li><li>Contacto del usuario actual</li></ul>La selección de valor requiere que se especifique un valor en el campo de **valor** que se asignará al campo cuando se cargue el formulario. Al seleccionar fecha de hoy, se asignará la fecha y hora actuales al campo de atributo. La selección del contacto del usuario actual requiere un **atributo from** que sea un atributo de la entidad Contact que se recuperará del registro de contacto del usuario actual y se establecerá en el campo de atributo especificado. |
|        Value         |                                                                                                                                                                                                                                        Valor que se va a asignar al campo cuando se carga el formulario.                                                                                                                                                                                                                                        |
|    Atributo from    |                                                                                                                                                                                             Atributo de la entidad Contact que se recuperará del registro del usuario del portal actual y se asignará al campo cuando se cargue el formulario.                                                                                                                                                                                             |

### <a name="set-value-on-save"></a>Establecer valor al guardar

Las siguientes opciones especifican un valor que se establecerá cuando se guarde el formulario.

| Nombre              | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Establecer valor al guardar | Sí indica que se debe asignar un valor al atributo mediante la entrada proporcionada en el campo de **valor** . <br>**Nota**: se admiten todos los tipos de atributo excepto el siguiente: identificador único.       |
| Tipo              | Una de las siguientes opciones:<ul><li>Value</li><li>  Fecha de hoy</li><li>Contacto del usuario actual</li></ul>La selección de valor requiere que se especifique un valor en el campo de **valor** que se asignará al campo cuando se cargue el formulario. Al seleccionar fecha de hoy, se asignará la fecha y hora actuales al campo de atributo. La selección del contacto del usuario actual requiere un **atributo from** que sea un atributo de la entidad Contact que se recuperará del registro de contacto del usuario actual y se establecerá en el campo de atributo especificado.  |
| Value             | Valor asignado al atributo al guardar el formulario.<br>En el caso de dos campos de opción (booleano), use true o false.<br>En campo de conjunto de opciones, use el valor entero de la opción.<br>Para los campos de búsqueda (EntityReference), use el GUID.<br>**Nota**: Si el atributo también está en el formulario, el valor del usuario se sobrescribirá con este valor.|
| Atributo from    | Atributo de la entidad Contact que se recuperará del registro del usuario del portal actual y se asignará al campo durante el almacenamiento. |

### <a name="validation"></a>Validación

La siguiente sección contiene propiedades que modifican varios parámetros de validación y mensajes de error.

Para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado.

| Nombre                                        | Descripción                                                                                                                                                                                                                                                      |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mensaje de error de validación                    | Invalida el mensaje de error de validación predeterminado para el campo.                                                                                                                                                                                                    |
| Expresión regular                          | Expresión regular que se va a agregar para validar el campo.                                                                                                                                                                                                          |
| Mensaje de error de validación de expresión regular | Mensaje de error de validación que se va a mostrar si se produce un error en la expresión regular validada.                                                                                                                                                                               |
| El campo es obligatorio                           | Active esta casilla para que el campo de atributo requiera que contenga un valor.                                                                                                                                                                                                   |
| Mensaje de error de validación de campo obligatorio     | Invalida el mensaje de error de campo obligatorio predeterminado si el campo no contiene un valor.                                                                                                                                                                        |
| Mensaje de error de validación de intervalo              | Invalida el mensaje de error de validación de intervalo predeterminado que se muestra si el valor del campo está fuera de los valores mínimo y máximo adecuados especificados en el atributo de entidad que son de tipo número entero, número decimal, número de punto flotante o moneda. |
| Mensaje de error del validador de ubicación geográfica         | Aplicable si el atributo es una sola línea de texto y el estilo de control especificado es una sola línea de texto como validador de búsqueda de ubicación geográfica, se invalidará el mensaje de error predeterminado que se muestra si se produce un error en la validación de entrada. |
| Mensaje de error de validación de suma constante       | Aplicable si el atributo es un tipo de número entero y el estilo de control especificado es el número de grupo entero como suma constante, se invalidará el mensaje de error predeterminado que se muestra si se produce un error en la validación de entrada.                    |
| Mensaje de error de validación de varias opciones    | Aplicable si el atributo es un tipo de dos opciones y el estilo de control especificado es varias opciones, esto invalidará el mensaje de error predeterminado que se muestra si se produce un error en la validación de entrada.                                         |
| Mensaje de error de validación de orden de clasificación sin vínculos | Aplicable si el atributo es un tipo de número entero y el estilo de control especificado es el número de grupo entero como el orden de clasificación no establece ningún valor, se invalidará el mensaje de error predeterminado que se muestra si se produce un error en la validación de entrada.              |

### <a name="description-and-instructions"></a>Descripción e instrucciones

Las siguientes propiedades especifican la ubicación y el contenido de la descripción o las instrucciones personalizadas.


|                 Nombre                 |                                                                                                                                                           Descripción                                                                                                                                                           |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Agregar Descripción            |                                                                                                                        Sí da como resultado que se muestre texto personalizado en el formulario en la posición especificada.                                                                                                                        |
|               Posición               |                                                                                                             Una de las siguientes opciones:<ul><li>Encima del campo</li><li>Debajo del campo</li><li>Encima de la etiqueta</li></ul>                                                                                                              |
| Usar la propiedad Description del atributo |                                                                                       Seleccione "sí" para usar la descripción asignada a los metadatos de atributo en la entidad. Seleccione "no" para proporcionar una descripción personalizada. El valor predeterminado es "no".                                                                                       |
|             Descripción              | Texto personalizado que se va a mostrar en el formulario. Se usa en conjunción cuando la propiedad de Descripción del atributo de uso está establecida en "no". Para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado. |

## <a name="web-form-metadata-type--section"></a>Tipo de metadatos del formulario web = sección

Las siguientes propiedades se muestran cuando el tipo seleccionado es igual a ' sección '.


|     Nombre     |                                                                                                                                                   Descripción                                                                                                                                                    |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre de sección |                                                                                           Nombre de la sección del formulario de la entidad que se va a modificar.                                                                                            |
|    Etiquetas     | Reemplaza la etiqueta predeterminada asignada a la sección en la entidad con el texto especificado en esta entrada. Para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado. |

## <a name="web-form-metadata-type--tab"></a>Tipo de metadatos del formulario web = tabulación

Las siguientes propiedades se muestran cuando el tipo seleccionado es igual a ' tabulación '


|   Nombre   |                                                                                                                                                 Descripción                                                                                                                                                  |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre de la pestaña |                                                                                           Nombre de la pestaña del formulario de la entidad que se va a modificar.                                                                                            |
|  Etiquetas   | Reemplaza la etiqueta predeterminada asignada a la pestaña de la entidad con el texto especificado en esta entrada. Para cada paquete de idioma instalado y habilitado para el entorno de Common Data Service, un campo estará disponible para escribir el mensaje en el idioma asociado. |

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Propiedades de formularios Web para portales](web-form-properties.md)  
[Pasos de Web Form para portales](web-form-steps.md)  
[Configuración de subcuadrículas de formularios Web Forms para portales](configure-web-form-subgrid.md)  
[Configuración de notas para formularios Web Forms para portales](../configure-notes.md)  

