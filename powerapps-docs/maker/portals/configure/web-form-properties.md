---
title: Configurar propiedades de formularios Web para un portal | MicrosoftDocs
description: Instrucciones para configurar las propiedades de un formulario Web Forms para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 904734c2143eae8e687be339b1bc5b30b47cff46
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551218"
---
# <a name="define-web-form-properties-for-portals"></a>Definir propiedades de formularios Web para portales

El formulario web contiene relaciones con las páginas web y un paso de inicio para controlar la inicialización del formulario en el portal. La relación con la página web permite la recuperación dinámica de la definición del formulario para un nodo de página determinado dentro del sitio Web.  

Las demás opciones del formulario Web Forms se registran en su totalidad las preferencias de nivel superior del proceso de varios pasos, por ejemplo, si desea mostrar una barra de progreso.

Para ver formularios Web Forms existentes o crear nuevos formularios Web Forms, abra la [aplicación de administración del portal](configure-portal.md) y vaya a portales > **formularios Web Forms**.

> [!Note]
> Un **formulario web** debe estar asociado a una página web para un sitio Web determinado para que el formulario sea visible en el sitio.  

Al crear o editar una página web desde la [aplicación de administración del portal](configure-portal.md), se puede especificar un **formulario web** en el campo de búsqueda proporcionado en el formulario de **nueva página web** .

## <a name="web-form-attributes"></a>Atributos de formularios Web Forms

Los siguientes atributos y relaciones determinan la funcionalidad del formulario Web Forms.


|                Nombre                 |                                                                                                                                                                                        Descripción                                                                                                                                                                                         |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                Nombre                 |                                                                                                                                                                          Título del formulario utilizado como referencia.                                                                                                                                                                           |
|             Iniciar paso              |                                                                                Primer paso del formulario. Un formulario Web Forms estará compuesto por uno o varios pasos. Para obtener más información acerca de estos pasos, consulte la sección titulada Web Form Step que se encuentra a continuación. El primer paso no puede ser de tipo condition.                                                                                |
|       Autenticación necesaria       |                                                                              Si está activada, cuando un usuario que no ha iniciado sesión visita la página que contiene el formulario, se le redirigirá a la página de inicio de sesión. Una vez que el inicio de sesión se realiza correctamente, se redirigirá al usuario a la página que contiene el formulario.                                                                               |
|      Iniciar nueva sesión al cargar      |              Si selecciona **sí** , se indica que si el usuario abre el formulario en un nuevo explorador o en una nueva pestaña, o bien cierra el explorador o la página y devuelve, el formulario iniciará una sesión completamente nueva y comenzará en el primer paso. En caso contrario, la sesión se conservará y el usuario puede cerrar el explorador o la página y reanudar más adelante exactamente donde se dejaron. Valor predeterminado: **no**.               |
| Se permiten varios registros por usuario |                                                                                                  Si selecciona **sí** , se indica que un usuario puede crear más de un envío. Esto ayuda al formulario a determinar qué hacer cuando un usuario vuelve a visitar un formulario. Valor predeterminado: **sí**.                                                                                                   |
|       Editar código de estado expirado       |                                                                                                                    Valor entero del código de estado de la entidad de destino que, cuando se combina con la razón del estado, indica que ya no se puede editar un registro existente.                                                                                                                     |
|     Editar motivo de estado expirado      |                                                                       Valor entero del código de estado de la entidad de destino que, cuando se combina con el código de estado, indica que, cuando un registro existente tiene estos valores, el registro ya no se&mdash;por ejemplo, cuando se actualiza un registro como completo.                                                                       |
|        Editar mensaje expirado         | El mensaje que se muestra cuando el código de estado y el motivo del estado del registro existente coinciden con los valores especificados. Para cada paquete de idioma instalado y habilitado para la organización, un campo estará disponible para escribir el mensaje en el idioma asociado. Mensaje predeterminado; Ya ha completado un envío. ¡Gracias! |
|                                     |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="progress-indicator-settings"></a>Configuración del indicador de progreso

| Nombre                              | Descripción                                                                                          |
|-----------------------------------|------------------------------------------------------------------------------------------------------|
| Activó                           | Active esta casilla para mostrar el indicador de progreso. Valor predeterminado: **deshabilitado**.                                      |
| Tipo                              | Uno de los siguientes: título, numérico (paso x de n) y barra de progreso. Valor predeterminado: **título**                                                                                    |
| Posición                          | Uno de los siguientes: superior, inferior, izquierda, derecha. La posición es relativa al formulario. Valor predeterminado: **Top**.                                                   |
| Anteponer el número de paso al título del paso | Active esta casilla para agregar el número de pasos al principio del título del paso. El valor predeterminado es desactivado. |
||

Ejemplo de varios tipos de indicadores de progreso:

**Title**

![Seguimiento del progreso mediante un título](../media/track-progress-title.png "Realizar un seguimiento del progreso mediante un título")  

**Título con el número de paso antepuesto**

![Seguimiento del progreso mediante un número de paso](../media/track-progress-step-number.png "Realizar un seguimiento del progreso mediante un número de paso")  

**Alfanumérico**

![Seguimiento del progreso mediante un número](../media/track-progress-numeral.png "Realizar un seguimiento del progreso mediante un número")  

**Barra de progreso**

![Seguimiento del progreso mediante una barra](../media/track-progress-bar.png "Realizar un seguimiento del progreso mediante una barra")  

## <a name="save-changes-warning"></a>ADVERTENCIA "Guardar cambios" 

|                 Nombre                  |                                                                                                                                Descripción                                                                                                                                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mostrar ADVERTENCIA de guardado de cambios al cerrar |                         Seleccione para mostrar un mensaje de advertencia si el usuario ha realizado cambios en los campos e intente recargar la página, cierre el explorador, seleccione el botón atrás del explorador o seleccione el botón anterior en un formulario de varios pasos.                         |
|     Mensaje de advertencia al guardar cambios      | Para cada paquete de idioma instalado y habilitado para la organización, un campo estará disponible para escribir el mensaje en el idioma asociado. Si no se especifica ningún mensaje, se usará el valor predeterminado del explorador. |
|                                       |                                                                                                                                                                                                                                                                           |

Ejemplo:

![ADVERTENCIA de guardado de cambios](../media/save-changes-warning.png "ADVERTENCIA de guardado de cambios")  

>[!Note]
> Firefox no proporciona la capacidad de especificar un mensaje personalizado.

## <a name="geolocation-configuration-for-web-form"></a>Configuración de geolocalización para Web Forms

Un formulario administrado puede configurarse para mostrar un control de mapa con el fin de mostrar una ubicación existente como un PIN en un mapa o para proporcionar a los usuarios la posibilidad de especificar una ubicación. Consulte [Agregar geolocation](add-geolocation.md).

El control de mapa del formulario requiere una configuración adicional para indicarle los identificadores de los distintos campos de ubicación, para asignarles valores o recuperar valores de ellos. El registro paso de formulario Web Forms tiene una sección que define estas asignaciones de campos para las que debe asignar valores. Los nombres de campo variarán en función del esquema que se haya creado.

![Datos de geolocalización en el formulario Web Forms](../media/geolocation-managed-form.png "Datos de geolocalización en el formulario Web Forms")

> [!Note]
> La sección geolocation no es visible en el entorno de nube soberano. Si un usuario ha habilitado la geolocalización con un formato diferente, no se mostrará durante la representación en el portal.

### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Pasos de Web Form para portales](web-form-steps.md)  
[Metadatos de formularios Web Forms para portales](configure-web-form-metadata.md)  
[Configuración de subcuadrículas de formularios Web Forms para portales](configure-web-form-subgrid.md)  
[Configuración de notas para formularios Web Forms para portales](../configure-notes.md)  
