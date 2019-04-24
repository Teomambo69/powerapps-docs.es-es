---
title: Anunciar cambios dinámicos con las regiones activas en las aplicaciones de lienzo | Microsoft Docs
description: Cómo usar las regiones activas para notificar a los lectores de pantalla de cambios dinámicos en las aplicaciones de lienzo
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a886b1c585f4fc07efc29bc1166ce4aca5586b5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61549959"
---
# <a name="announce-dynamic-changes-with-live-regions-for-canvas-apps"></a>Anunciar cambios dinámicos con las regiones activas para las aplicaciones de lienzo

Cambios dinámicos representan desafíos para la discapacidad visual. Los usuarios que tienen acceso a una aplicación a través de un lector de pantalla se centran en una parte de la aplicación. Si se produce un cambio en otra parte, esos usuarios no ser conscientes de ello.

Puede resolver este problema mediante la adición de las regiones activas que realizan un seguimiento de los lectores de pantalla. Si se cambia el contenido en una región activa, un lector de pantalla anunciará ese cambio.

El mecanismo subyacente para las regiones activas están [regiones aria-live](https://www.w3.org/TR/wai-aria-1.1/#dfn-live-region), por lo que se aplican las mismas directrices.

## <a name="example-uses-of-live-regions"></a>Ejemplos de usos de las regiones activas

Puede usar las regiones activas para notificar a los usuarios cuando se producen eventos como los siguientes:

* Se produce un error de validación en un formulario.
* Una acción desencadenada por un botón es correcta. Por ejemplo, un usuario puede seleccionar un botón para agregar un elemento a una colección y una región activa puede mostrar el mensaje de "Elemento agregado".
* El usuario selecciona una ficha diferente.
* Un temporizador en segundo plano actualiza un suministro de noticias.

## <a name="create-and-configure-a-live-region"></a>Crear y configurar una región activa

Puede configurar solo un **[etiqueta](controls/control-text-box.md)** control como una región activa. Su **Live** propiedad determina el tipo de región activa.

* **Off**: No es una región activa. Los lectores de pantalla no anuncian los cambios.
* **Cortés**: Los lectores de pantalla anuncian los cambios después de finalizar hablando. Use este valor para las notificaciones no críticas que no requieren atención inmediata.
* **Seguro de sí mismo**: Los lectores de pantalla de interrupción a sí mismos para anunciar los cambios inmediatamente. Utilice esto para las notificaciones críticas que requieren atención inmediata.

Si cambia el contenido de texto de una región activa, los lectores de pantalla anunciarán el contenido de texto completo, no solo la parte modificada. Si el valor de la **[texto](controls/properties-core.md)** propiedad está establecida en una cadena vacía **""**, el lector de pantalla no anuncia nada.

Para repetir un mensaje, borrar el contenido de texto estableciendo el valor de la **[texto](controls/properties-core.md)** propiedad en la cadena vacía **""** y, a continuación, establezca el valor para el mensaje.

## <a name="best-practices"></a>Procedimientos recomendados

* Establezca siempre **[Visible](controls/properties-core.md)** en true. Algunos lectores de pantalla no detectan las regiones activas que desaparecen y vuelva a aparecer.
* Evite cambiar el valor de  **[Live](controls/properties-accessibility.md)**. Algunos lectores no detectan cuando una región en vivo no se convierte en vivo de pantalla y viceversa.
* Coloque la región activa en una posición lógica en la aplicación, aunque no estén visible. Asegúrese de que su contenido es razonable en contexto con los elementos antes y después. Los usuarios pueden acceder una región activa en cualquier momento mediante la navegación normal con un lector de pantalla, no solo cuando se producen cambios.

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo [mostrar contenido únicamente a los lectores de pantalla](accessible-apps-content-visibility.md) si la región activa debe ocultarse de visión reducida a los usuarios.