---
title: Revisión de una aplicación de lienzo para mejorar la accesibilidad | Microsoft Docs
description: Identifique maneras de hacer que una aplicación de lienzo sea más accesible para los usuarios que tienen discapacidades visuales, auditivas y de otro tipo
author: emcoope-msft
ms.service: powerapps
ms.topic: article
ms.date: 07/05/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 05ac3d3705fc56b5714d6cb704d2d3cc3dc87124
ms.sourcegitcommit: b4df7d781cda50dfe2f6609f1cc4d2b531428b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "70161293"
---
# <a name="review-a-canvas-app-for-accessibility-in-powerapps"></a>Revisar una aplicación de lienzo para mejorar la accesibilidad en PowerApps

Los usuarios con discapacidades visuales, auditivas o de otro tipo pueden usar la aplicación de lienzo con más facilidad y correctamente si tiene en cuenta la accesibilidad al diseñar el aspecto y el comportamiento de la aplicación. Si no tiene claro cómo hacer que su aplicación sea más accesible, puede ejecutar el Comprobador de accesibilidad en PowerApps Studio. Esta herramienta no solo busca posibles problemas de accesibilidad, sino que también explica por qué cada uno de ellos podría ser un posible problema para los usuarios que tienen discapacidades específicas y ofrece sugerencias sobre cómo resolver cada problema.
El Comprobador de accesibilidad detecta problemas de lector de pantalla y teclado y puede encontrar información sobre cómo solucionar los problemas de contraste de color usando [Colores accesibles](accessible-apps-color.md).

El Comprobador de accesibilidad le ayuda a identificar la configuración que puede querer cambiar, pero siempre debe tener en cuenta las sugerencias en el contexto de lo que debe hacer la aplicación. Muchas sugerencias pueden merecer la pena, pero puede omitir cualquiera que pueda ser más dañina que beneficiosa.

## <a name="find-accessibility-issues"></a>Buscar problemas de accesibilidad

1. En la esquina superior derecha de PowerApps Studio, seleccione el icono para el Comprobador de aplicaciones.

    ![Icono de Comprobador de aplicaciones](./media/accessibility-checker/app-checker-icon.png)

2. En el menú que aparece, seleccione **Accesibilidad**.

    ![Lista de opciones del panel de Comprobador de aplicaciones](./media/accessibility-checker/app-checker-menu.png)

    Aparece una lista de problemas, ordenados primero por gravedad y después por pantalla.

    ![Panel del Comprobador de accesibilidad y lista de elementos](./media/accessibility-checker/accessibility-checker-pane.png)

3. Seleccione la flecha situada junto a un elemento para mostrar sus detalles.

    ![Detalles del Comprobador de accesibilidad](./media/accessibility-checker/details-pane.png)

4. Seleccione la flecha Atrás para volver a la lista de elementos.

5. Si decide resolver un problema, selecciónelo para abrir la propiedad afectada.

6. Después de cambiar una o varias propiedades, seleccione **Volver a comprobar** para actualizar la lista de problemas.

    Los elementos resueltos desaparecerán de la lista y pueden aparecer nuevos elementos.

## <a name="severity-of-issues"></a>Gravedad de los problemas

El Comprobador de accesibilidad clasifica cada problema como un error, una advertencia o una sugerencia según la gravedad del problema.

- **Los errores** identifican problemas que hacen que la aplicación sea difícil o imposible de usar y comprender para los usuarios que tienen discapacidades.
- **Las advertencias** identifican problemas que hacen que la aplicación sea difícil de usar o entender para la mayoría de los usuarios con discapacidades, pero no para todos.
- **Las sugerencias** le ayudarán a mejorar la experiencia de los usuarios que tienen discapacidades.

## <a name="types-of-issues"></a>Tipos de problemas

| Título del problema                            | Gravedad | Descripción del problema  | Cómo corregir | Motivo de la corrección|
| ------------------------------         |:---------| -----| ------|------ |
| **Falta la etiqueta accesible**           | Error    | Cuando la propiedad de etiqueta accesible de un control interactivo no contiene texto. Un control interactivo puede ser inherentemente interactivo, como lo es un botón, o tener propiedades interactivas. Por ejemplo, es posible que estableciese la propiedad **OnSelect** de una imagen o estableciese su propiedad **TabIndex** en 0 o superior.  | Edite la propiedad de la etiqueta accesible para describir el elemento. | Si la propiedad de la etiqueta accesible no contiene texto, los usuarios que no pueden ver la pantalla no entenderán lo que aparece en las imágenes y los controles. |
| **No se muestra el foco**                | Error    | Cuando la propiedad **FocusBorderThickness** de un control se establece en 0. Es recomendable para garantizar una proporción de contraste de color adecuada entre el borde del foco y el propio control para que sea claramente visible. | Cambie la propiedad **FocusedBorderThickness** a un valor mayor que 0.  | Si el foco no está visible, los usuarios que no usen un mouse no podrán verlo cuando interactúen con la aplicación.   |
| **Faltan descripciones**                   | Advertencia  | Cuando la propiedad **ClosedCaptionsURL** de un control **Audio** o **Vídeo** está vacía. | Establezca la propiedad **ClosedCaptionsURL** para agregar la dirección URL para las descripciones. | Sin descripciones, es posible que las personas con discapacidades no puedan comprender la información de un segmento de vídeo o audio. |
| **Faltan valores de configuración de control útiles**   | Advertencia  | Cuando cualquiera de varios valores (por ejemplo, mostrar las etiquetas y los marcadores para los gráficos, así como los controles predeterminados para los controles **Audio**, **Vídeo** y **Entrada manuscrita**) están desactivados. | Seleccione la advertencia y después establezca la propiedad en **true**. | Al cambiar la configuración de esta propiedad, ofrecerá más información al usuario sobre cómo funcionan los controles de su aplicación. |
| **El archivo HTML no será accesible**           | Advertencia  | Cuando un control que no es un control de texto HTML contiene HTML. En ese caso, PowerApps no admite la accesibilidad de los elementos HTML personalizados. | Use otro método en lugar del archivo HTML o quite el archivo HTML de este elemento. | La aplicación no funcionará correctamente ni será accesible si coloca elementos HTML interactivos. |
| **Desactive el inicio automático**                 | Advertencia  | Cuando la propiedad **Autostart** de un control **Audio** o **Vídeo** está establecida en **true**. | Establezca la propiedad **Autostart** del control en **false**. | Los archivos de vídeo y audio que se reproducen automáticamente pueden distraer a los usuarios. Permítales elegir si quieren reproducir un clip. |
| **Revise el nombre de la pantalla**                 | Sugerencia      | Cuando una pantalla tiene un nombre predeterminado, que leerán los lectores de pantalla cuando el usuario navega por la aplicación. | Asigne un nombre a la pantalla que describa lo que aparece en ella o su uso.| Las personas que son ciegas, que tienen deficiencia visual o discapacidad de lectura dependen de los nombres en pantalla para navegar mediante el lector de pantalla. |
| **Agregue texto de indicación del estado**          | Sugerencia      |  Cuando un control tiene un estado, por ejemplo, un interruptor, pero las etiquetas de valor están desactivadas. | Establezca la propiedad **ShowValue** del control en **true** para mostrar su estado actual. | Los usuarios no obtendrán confirmación de sus acciones si el estado del control no se muestra. |
| **Compruebe el orden de los elementos de la pantalla**| Sugerencia      | Cuando la propiedad **TabIndex** es mayor que 0. Los creadores de aplicaciones pueden establecer órdenes de tabulación personalizadas si se establece la propiedad **TabIndex** en un valor mayor que 0, pero se desaconseja encarecidamente porque es difícil de obtener, mantener y romper los lectores de pantalla. | Establezca todas las propiedades de **TabIndex** en 0 o-1 siempre que sea posible.  En lugar de usar **TabIndex**, use el control de **Grupo mejorado** para cambiar el orden de navegación del valor predeterminado.  Si se deben usar valores de **TabIndex** mayores que 0, asegúrese de que los elementos de pantalla coincidan con el orden en el que desea realizar las tabulaciones. | El orden de navegación debe reflejar el orden en que los controles aparecen en la pantalla, que es el valor predeterminado.  Si se realizan ajustes manuales, es difícil mantener el orden correcto especialmente en la presencia de la barra de direcciones del explorador y otros controles fuera de la aplicación.  Esto puede dificultar el uso de un lector de pantalla.  Cuando el lector de pantalla lo lee, los controles deben aparecer en el mismo orden en el que aparecen en la pantalla, en lugar de un orden que sea menos intuitivo.  |
| **Agregue otro método de entrada**           | Sugerencia      | Cuando una aplicación contiene un control **Lápiz**. Esta sugerencia le recuerda que incluya un método de entrada independiente. | Agregue un control **Entrada de texto** además del control **Lápiz** para ofrecer una experiencia accesible. | Algunos usuarios no pueden usar un lápiz y necesitan otro método para indicar información como, por ejemplo, teclear una firma. |

## <a name="next-steps"></a>Pasos siguientes

- [Creación de aplicaciones accesibles](accessible-apps.md)
- [Colores accesibles](accessible-apps-color.md)
- [Propiedades de accesibilidad](controls/properties-accessibility.md)
