---
title: Metadatos de formularios web para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar los metadatos de un formulario web para un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 04201baf8406a6a9c9c66e1668406594334be754
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979005"
---
# <a name="configure-web-form-metadata-for-portals"></a>Configurar metadatos de formulario web para los portales

Los metadatos del formulario web contienen la lógica de modificación del comportamiento adicional para aumentar o reemplazar la funcionalidad de los campos de formulario que de otro modo no es posible conseguir con las funciones de edición de formulario de entidad nativas de .

## <a name="add-a-new-record"></a>Agregar un registro nuevo

1. En el paso del formulario web que tiene campos que desea editar, vaya a **Relacionados** > **Metadatos** 

2. Seleccione **Nuevos metadatos del formulario web**.

## <a name="web-form-metadata-properties"></a>Propiedades de metadatos del formulario web

Los siguientes atributos proporcionan funciones y estilos adicionales para elementos de un formulario.

| Nombre          | Descripción                                                                                                                                                                                                                                                                                                                                          |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Paso de formulario web | El paso de formulario web asociado al registro de metadatos del formulario web.                                                                                                                                                                                                                                                                                      |
| Tipo          | Opciones disponibles:<ul><li>Atributo</li><li>Sección</li><li>Ficha</li></ul>Si selecciona Atributo como el valor de Tipo se mostrarán las opciones correspondientes para editar campos en el formulario actual representado para el paso relacionado. Si selecciona Sección como el valor de Tipo se mostrarán las opciones disponibles para editar una sección del formulario. Si selecciona Pestaña como el valor de Tipo se mostrarán las opciones disponibles para editar una pestaña de un formulario.  |

## <a name="web-form-metadata-type--attribute"></a>Tipo de metadatos de formulario web = Atributo

Se muestran las siguientes propiedades cuando el Tipo seleccionado es 'Atributo'.


|          Nombre          |                                                                                                                                                    Descripción                                                                                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre lógico del atributo |                                                                                                                              El nombre lógico del campo de atributo que se va a modificar.                                                                                                                               |
|         Etiqueta          | Reemplaza la etiqueta predeterminada asignada al atributo en la entidad con el texto especificado en esta entrada. Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado. |

### <a name="control-style"></a>Estilo del control

Las siguientes opciones modifican el estilo y funcionalidades de un campo de atributo.


|                      Nombre                       |                                                                                                                                                                                                                                                                                                                                       Descripción                                                                                                                                                                                                                                                                                                                                       |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      Estilo                      | Uno de los siguientes:<ul><li>Conjunto de opciones como lista vertical de botones de radio</li><li>Conjunto de opciones como lista horizontal de botones de radio</li><li>Una sola línea de texto como validador de búsqueda de ubicación geográfica (requiere configuración de Mapas de [!INCLUDE[pn-bing](../../../includes/pn-bing.md)] - los detalles se encuentran aquí)</li><li>Agrupar número entero como suma constante (requiere Nombre de grupo)</li><li>Agrupar número entero como escala de orden de clasificación sin valores equivalentes (requiere Nombre de grupo)</li><li>Agrupar número entero como escala de orden de clasificación con valores equivalentes (requiere Nombre de grupo)</li><li>Matriz de opciones múltiples (requiere Nombre de grupo)</li><li>Opciones múltiples (requiere Nombre de grupo)</li><li>Agrupar número entero como orden por prioridad (requiere Nombre de grupo)</li></u> |
|                   Nombre de grupo                    |                                                                                                                                                                                                                                                                                                             Un nombre utilizado para agrupar controles como control compuesto.                                                                                                                                                                                                                                                                                                              |
| Número mínimo seleccionado necesario de opciones múltiples |                                                                                                                                                                                                                                                                      Éstos son los valores mínimos requeridos seleccionados a la pregunta de varias opciones. Solo se necesita si selecciona el estilo del control 'Opciones múltiples' está seleccionado.                                                                                                                                                                                                                                                                       |
|       Número máximo seleccionado de opciones múltiples        |                                                                                                                                                                                                                                                          Este es el número máximo de valores que se permite seleccionar en la pregunta de opciones múltiples. Solo se necesita si selecciona el estilo del control 'Opciones múltiples' está seleccionado.                                                                                                                                                                                                                                                          |
|           Total mínimo de suma constante            |                                                                                                                                                                                                                                                             Este es el valor mínimo necesario aplicado a un campo de respuesta de suma constante. Solo es necesario si el Estilo del control 'Agrupar número entero como suma constante' está seleccionado.                                                                                                                                                                                                                                                              |
|           Total máximo de suma constante            |                                                                                                                                                                                                                                                 Este es el número máximo de valor que se permite aplicar a un campo de respuesta suma constante. Solo es necesario si el Estilo del control 'Agrupar número entero como suma constante' está seleccionado.                                                                                                                                                                                                                                                 |
|           Aleatorizar valores de conjuntos de opciones           |                                                                                                                                                                                                                                                                     Si especifica Sí dará lugar a opciones ordenadas aleatoriamente mostradas para un control de conjunto de opciones. Aplicable solo a los atributos que sean de tipo Conjunto de opciones.                                                                                                                                                                                                                                                                     |
|                    Clase de CSS                    |                                                                                                                                                                                                                                                                                                                      Agrega un nombre de clase CSS personalizado al control.                                                                                                                                                                                                                                                                                                                       |

### <a name="prepopulate-field"></a>Rellenar previamente campo

Las siguientes opciones proporcionen un valor predeterminado para campos del formulario.


|         Nombre         |                                                                                                                                                                                                                                                                Descripción                                                                                                                                                                                                                                                                 |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Omitir valor predeterminado |                                                                              Omite el valor predeterminado del de campo de atributo especificado. Útil para atributos que son campos de dos opciones que se representan como botones de opción Sí y No. Dado que se asigna automáticamente un valor de Sí o No de forma predeterminada, esta opción permite mostrar preguntas Sí/No sin una respuesta predefinida.                                                                               |
|         Tipo         | Uno de los siguientes:<ul><li>Valor</li><li>Fecha de hoy</li><li>Contacto del usuario actual</li></ul>Si selecciona Valor necesitará especificar un valor en el campo **Valor** que se asignará al campo cuando el formulario se cargue. Al seleccionar la fecha de hoy se asignará la fecha y hora actuales al campo del atributo. Si selecciona el Contacto del usuario actual requerirá un **Desde atributo** que sea un atributo de la entidad de contacto que se recuperará del registro de contacto del usuario actual y esté establecido como el campo de atributo especificado. |
|        Valor         |                                                                                                                                                                                                                                        Un valor que se asignará al campo cuando el formulario se cargue.                                                                                                                                                                                                                                        |
|    Desde atributo    |                                                                                                                                                                                             Un atributo de la entidad de contacto que se recuperará del registro del usuario del portal actual y se asignará al campo cuando el formulario se cargue.                                                                                                                                                                                             |

### <a name="set-value-on-save"></a>Establecer valor al guardar

Las siguientes opciones especifican un valor que se establecerá cuando se guarde el formulario.

| Nombre              | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Establecer valor al guardar | Sí indica que un valor se debe asignar al atributo utilizando la entrada proporcionada en el campo **Valor**. <br>**Nota**: Se admiten todos los tipos de atributo excepto el siguiente: Identificador único.       |
| Tipo              | Uno de los siguientes:<ul><li>Valor</li><li>  Fecha de hoy</li><li>Contacto del usuario actual</li></ul>Si selecciona Valor necesitará especificar un valor en el campo **Valor** que se asignará al campo cuando el formulario se cargue. Al seleccionar la fecha de hoy se asignará la fecha y hora actuales al campo del atributo. Si selecciona el Contacto del usuario actual requerirá un **Desde atributo** que sea un atributo de la entidad de contacto que se recuperará del registro de contacto del usuario actual y esté establecido como el campo de atributo especificado.  |
| Valor             | Valor asignado al atributo cuando el formulario se guarde.<br>Para campos de dos opciones (booleanos), utilice true o false.<br>Para el campo Conjunto de opciones, use el valor de entero para la opción.<br>Para los campos de búsqueda (EntityReference) use el GUID.<br>**Nota**: Si el atributo también está en el formulario, el valor del usuario se sobrescribirá con este valor.|
| Desde atributo    | Un atributo de la entidad de contacto que se recuperará del registro del usuario del portal actual y se asignará al campo al guardar. |

### <a name="validation"></a>Validación

La siguiente sección contiene propiedades que modifican diferentes parámetros de validación y mensajes de error.

Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado.

| Nombre                                        | Descripción                                                                                                                                                                                                                                                      |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mensaje de error de validación                    | Reemplace el mensaje de error de validación predeterminado para el campo.                                                                                                                                                                                                    |
| Expresión regular                          | Una expresión regular que se agregará para validar el campo.                                                                                                                                                                                                          |
| Mensaje de error de validación de expresión regular | El mensaje de error de validación a mostrar si se produce un error con la expresión regular validada.                                                                                                                                                                               |
| El campo es obligatorio                           | Active esta opción para hacer que el campo de atributo necesario contenga un valor.                                                                                                                                                                                                   |
| Mensaje de error de validación de campo obligatorio     | Reemplace el mensaje de error del campo requerido predeterminado si el campo no contiene un valor.                                                                                                                                                                        |
| Mensaje de error de validación de intervalo              | Reemplaza el mensaje de error de validación del intervalo predeterminado que se muestra si el valor del campo se encuentra fuera de los valores mínimo y máximo adecuados especificados en el atributo de entidad que son de tipo Número entero, Número decimal, Número de coma flotante o Divisa. |
| Mensaje de error del validador de ubicación geográfica         | Aplicable si el atributo es una sola línea de texto y el estilo del control especificado es una sola línea de texto como validador de búsqueda de ubicación geográfica, entonces esto sobrescribirá el mensaje de error predeterminado que se muestra si se produce error de la validación de entrada. |
| Mensaje de error de validación de suma constante       | Aplicable si el atributo es un tipo de número entero y el estilo del control especificado es Agrupar número entero como suma constante, entonces esto sobrescribirá el mensaje de error predeterminado que se muestra si se produce error de la validación de entrada.                    |
| Mensaje de error de validación de opciones múltiples    | Aplicable si el atributo es un tipo de dos opciones y el estilo del control especificado es Opciones múltiples, entonces esto sobrescribirá el mensaje de error predeterminado que se muestra si se produce error de validación de entrada.                                         |
| Mensaje de error de validación de orden de clasificación sin valores equivalentes | Aplicable si el atributo es un tipo de número entero y el estilo del control especificado es Agrupar número entero como escala de orden de clasificación sin valores equivalentes, entonces esto sobrescribirá el mensaje de error predeterminado que se muestra en caso de error de la validación de entrada.              |

### <a name="description-and-instructions"></a>Descripción e instrucciones

Las siguientes propiedades especifican la ubicación y el contenido de la descripción o instrucciones personalizadas.


|                 Nombre                 |                                                                                                                                                           Descripción                                                                                                                                                           |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Agregar descripción            |                                                                                                                        Sí hace que el texto personalizado se muestre en el formulario en la ubicación especificada.                                                                                                                        |
|               Puesto               |                                                                                                             Uno de los siguientes:<ul><li>Encima del campo</li><li>Debajo del campo</li><li>Encima de la etiqueta</li></ul>                                                                                                              |
| Usar propiedad de descripción del atributo |                                                                                       Seleccione 'Sí' para usar la descripción asignada a los metadatos de atributo de la entidad. Seleccione 'No' para proporcionar una descripción personalizada. El valor predeterminado es 'No'.                                                                                       |
|             Descripción              | Texto personalizado para mostrar en el formulario. Se usa conjuntamente cuando Usar propiedad de descripción del atributo se establece en 'No'. Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado. |

## <a name="web-form-metadata-type--section"></a>Tipo de metadatos de formulario web = Sección

Se muestran las siguientes propiedades cuando el Tipo seleccionado es igual a 'Sección'.


|     Nombre     |                                                                                                                                                   Descripción                                                                                                                                                    |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre de sección |                                                                                           El nombre de la sección en el formulario de la entidad que se modificará.                                                                                            |
|    Etiqueta     | Reemplaza la etiqueta predeterminada asignada a la sección en la entidad con el texto especificado en esta entrada. Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado. |

## <a name="web-form-metadata-type--tab"></a>Tipo de metadatos de formulario web = Pestaña

Se muestran las siguientes propiedades cuando el Tipo seleccionado es igual a 'Pestaña'.


|   Nombre   |                                                                                                                                                 Descripción                                                                                                                                                  |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre de pestaña |                                                                                           El nombre de la pestaña en el formulario de la entidad que se modificará.                                                                                            |
|  Etiqueta   | Reemplaza la etiqueta predeterminada asignada a la pestaña en la entidad con el texto especificado en esta entrada. Para cada paquete de idioma instalado y activado para la organización del entorno de Common Data Service, un campo estará disponible para especificar el mensaje en el idioma asociado. |

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Propiedades del formulario web para portales](web-form-properties.md)  
[Pasos de formulario web para portales](web-form-steps.md)  
[Configuración de la subcuadrícula de formularios web para portales](configure-web-form-subgrid.md)  
[Configuración de notas para formularios web para portales](../configure-notes.md)  

