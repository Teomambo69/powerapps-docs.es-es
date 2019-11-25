---
title: Configurar propiedades de formulario web para un portal | MicrosoftDocs
description: Instrucciones para configurar un formulario web de un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761089"
---
# <a name="define-web-form-properties-for-portals"></a>Definir propiedades de formulario web para portales

El formulario web contiene relaciones con páginas web y un paso de inicio para controlar la inicialización del formulario dentro del portal. La relación con la página web permite la recuperación dinámica de la definición de formulario para un determinado nodo de página en el sitio web.  

Las otras opciones en el propio registro del formulario web controlan las preferencias de nivel superior para el proceso de diversos pasos en su conjunto como, por ejemplo, si desea que se muestre una barra de progreso.

Para ver formularios web existentes o crear nuevos formularios web, abra la [aplicación Administración del portal](configure-portal.md) y vaya a **Portales** > **Formularios web**.

> [!Note]
> Un **formulario web** debe estar asociado a una página web de un determinado sitio web para que el formulario sea visible desde el sitio.  

Al crear o editar una página web desde la [aplicación Administración del portal](configure-portal.md), un **formulario web** se puede especificar en el campo de búsqueda proporcionado en el formulario **Nueva página web**.

## <a name="web-form-attributes"></a>Atributos de formulario web

Los siguientes atributos y relaciones determinan la funcionalidad del formulario web.


|                Nombre                 |                                                                                                                                                                                        Descripción                                                                                                                                                                                         |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                Nombre                 |                                                                                                                                                                          Un título del formulario usado para referencia.                                                                                                                                                                           |
|             Paso de inicio              |                                                                                El primer paso del formulario. Un formulario web está compuesto por uno o varios pasos. Para obtener información acerca de estos pasos, consulte la sección titulada Paso de formulario web que se encuentra a continuación. El primer paso no puede ser de tipo "Condition".                                                                                |
|       Se requiere autenticación       |                                                                              Si está activada esta opción, cuando un usuario que no ha iniciado sesión visita la página que contiene el formulario, será redirigido a la página de inicio de sesión. Después de iniciar sesión correctamente, el usuario volverá a acceder a la página que contiene el formulario.                                                                               |
|      Iniciar nueva sesión al cargar      |              Si se selecciona **Sí**, se indica que si el usuario abre el formulario en un explorador nuevo o una nueva pestaña o cierra el explorador o la página y vuelve al paso anterior, se iniciará una sesión completamente nueva en el formulario y se reiniciará en el primer paso. En caso contrario, la sesión se mantendrá y el usuario puede cerrar el explorador o la página y reanudar más adelante exactamente donde lo dejó. Valor predeterminado: **No**.               |
| Se permiten varios registros por usuario |                                                                                                  Seleccione **Sí** para indicar que se permite a un usuario crear más de un envío. Esto ayuda al formulario a determinar qué hacer cuando un usuario revisita un formulario. Valor predeterminado: **Sí**.                                                                                                   |
|       Código de estado de editar expirado       |                                                                                                                    Si el valor entero del código de estado de la entidad de destino se combina con la razón para el estado, indica cuándo un registro existente ya no se puede editar.                                                                                                                     |
|     Razón para el estado de editar expirado      |                                                                       Si el valor entero del código de estado de la entidad de destino se combina con el código de estado, indica que cuando un registro existente tiene estos valores, el registro no debe editarse más&mdash;; es decir, cuando un registro se actualiza como completo.                                                                       |
|        Mensaje de editar expirado         | El mensaje que se muestra cuando el código de estado del registro existente y la razón para el estado coinciden con los valores especificados. Para cada paquete de idioma instalado y activado para la organización un campo estará disponible para especificar el mensaje en el idioma asociado. Mensaje predeterminado: "Ya ha completado un envío. Gracias." |
|                                     |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="progress-indicator-settings"></a>Configuración de indicador de progreso

| Nombre                              | Descripción                                                                                          |
|-----------------------------------|------------------------------------------------------------------------------------------------------|
| Habilitado                           | Active esta opción para mostrar el indicador de progreso. Valor predeterminado: **Deshabilitado**.                                      |
| Tipo                              | Uno de los siguientes: Título, Numérico (paso x de n), y barra de progreso. Valor predeterminado: **Título**                                                                                    |
| Posición                          | Uno de los siguientes: Superior, Inferior, Izquierda, Derecha. La posición es relativa al formulario. Valor predeterminado: **Superior**                                                   |
| Anteponer número de paso al título de paso | Active esta opción para agregar el número del paso al principio del título del paso. El valor predeterminado es sin activar. |
||

Ejemplo de los diferentes tipos de indicador de progreso:

**Título**

![Realizar seguimiento mediante un título](../media/track-progress-title.png "Realizar seguimiento mediante un título")  

**Título con número de paso antepuesto**

![Realizar seguimiento mediante un número de paso](../media/track-progress-step-number.png "Realizar seguimiento mediante un número de paso")  

**Numérico**

![Realizar seguimiento mediante un número](../media/track-progress-numeral.png "Realizar seguimiento mediante un número")  

**Barra de progreso**

![Realizar seguimiento mediante una barra](../media/track-progress-bar.png "Realizar seguimiento mediante una barra")  

## <a name="save-changes-warning"></a>Advertencia de "guardar cambios" 

|                 Nombre                  |                                                                                                                                Descripción                                                                                                                                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mostrar advertencia de guardar cambios al cerrar |                         Seleccione esta opción para mostrar un mensaje de advertencia si el usuario ha realizado cambios en los campos e intenta volver a cargar la página, cerrar el explorador, hacer clic en el botón Atrás del explorador, o hacer clic en el botón anterior en un formulario de varios pasos.                         |
|     Mensaje de advertencia de guardar cambios      | Para cada paquete de idioma instalado y activado para la organización un campo estará disponible para especificar el mensaje en el idioma asociado. Si no se especifica un mensaje, se utilizará el valor predeterminado del explorador. |
|                                       |                                                                                                                                                                                                                                                                           |

Ejemplo:

![Advertencia de guardar cambios](../media/save-changes-warning.png "Advertencia de guardar cambios")  

>[!Note]
> Firefox no ofrece la posibilidad de especificar un mensaje personalizado.

## <a name="geolocation-configuration-for-web-form"></a>Configuración de ubicación geográfica para formulario web.

Un formulario administrado se puede configurar para mostrar un control de mapa para que se muestre una ubicación existente como una chincheta en un mapa o proporcionar la capacidad de que el usuario especifique una ubicación. Vea [Agregar ubicación geográfica](add-geolocation.md).

El control de mapa del formulario requiere configuración adicional para indicarle cuáles son los id. de los diferentes campos de ubicación para poder asignar o recuperar valores. El registro del paso de formulario web tiene una sección que define estas asignaciones de campo a las que debe asignar valores. Los nombres de campo variarán en función del esquema que ha elegido.

![Datos de ubicación geográfica en formulario web](../media/geolocation-managed-form.png "Datos de ubicación geográfica en formulario web")

> [!Note]
> La sección de ubicación geográfica no podrá verse en el entorno de la nube soberana alemana. Si un usuario ha habilitado la ubicación geográfica con otro formulario, no se mostrarán durante la representación en portal.

### <a name="see-also"></a>Vea también

[Configurar un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Pasos de formulario web para portales](web-form-steps.md)  
[Metadatos de formularios web para portales](configure-web-form-metadata.md)  
[Configuración de la subcuadrícula de formularios web para portales](configure-web-form-subgrid.md)  
[Configuración de notas para formularios web para portales](../configure-notes.md)  
