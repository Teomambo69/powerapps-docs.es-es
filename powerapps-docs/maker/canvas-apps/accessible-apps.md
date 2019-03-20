---
title: Creación de aplicaciones de lienzo accesibles | Microsoft Docs
description: Cómo hacer que las aplicaciones sean accesibles para personas con discapacidades
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/03/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b6e2fc48d931ccf702dd2711bdc00a484dc51018
ms.sourcegitcommit: 4db9c763455d141a7e1dd569a50c86bd9e50ebf0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2019
ms.locfileid: "57801949"
---
# <a name="create-accessible-canvas-apps-in-powerapps"></a>Creación de aplicaciones de lienzo accesibles en PowerApps
Una aplicación de lienzo accesible permitirá a los usuarios con discapacidades visuales, auditivas y de otra índole utilizar correctamente dicha aplicación.  Además de ser un requisito para muchos gobiernos y organizaciones, si sigue las pautas que se indican a continuación aumentará la facilidad de uso para todos los usuarios, independientemente de sus capacidades.

Use el **[Comprobador de accesibilidad](accessibility-checker.md)** para ayudarle a revisar los posibles problemas de accesibilidad de la aplicación. 

## <a name="layout-and-color"></a>Diseño y color
Un diseño con sentido común y poco complicado ayuda a que las aplicaciones sean más accesibles para todos los usuarios.  Cuando realice una personalización intensa de las aplicaciones, tenga en cuenta las siguientes sugerencias.  Los temas de PowerApps son accesibles de forma predeterminada.
- Asegúrese de que todos los elementos son claramente visibles y el texto tiene un tamaño suficiente.  Todo el contenido se debe poder leer y comprender fácilmente a simple vista.
- Evite el uso de la propiedad de visibilidad de los elementos para mostrar un elemento.  Si necesita mostrar algo de manera condicional, cree el contenido en una nueva pantalla, navegue a ella y vuelva.
- Asegúrese de que los elementos de entrada están etiquetados en la pantalla. La propiedad **[AccessibilityLabel](controls/properties-accessibility.md)** define lo que el lector de pantalla anunciará.
- Si personaliza colores, asegúrese de que el contraste entre el texto y el fondo es 4.5:1 o superior.  Las herramientas de software que ayudan a este proceso están disponibles.
- Asegúrese de que el diseño sigue un flujo lógico cuando lea de arriba a abajo y de izquierda a derecha.


## <a name="keyboard-support"></a>Compatibilidad con el teclado
Cuando pruebe la accesibilidad de la aplicación, asegúrese de que esta se puede utilizar solo con el teclado, con los modos de accesibilidad de iOS y Android, y que se puede navegar por ella correctamente con el lector de pantalla habilitado.

Para la navegación con el teclado (con o sin el lector de pantalla), asegúrese de que se sigue un orden lógico cuando se utiliza la tecla TAB para navegar por los campos de entrada mediante el establecimiento de la propiedad **[TabIndex](controls/properties-accessibility.md)** de cada control:
- Etiqueta, imagen, icono, los controles de forma: si representan elementos interactivos (por ejemplo, botones) establezca TabIndex en 0. Si son elementos decorativos o texto, establezca TabIndex en -1.
- Evite establecer el índice de tabulación en un valor mayor que cero.

## <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
Las siguientes combinaciones de software son las recomendaciones admitidas para consumir PowerApps con un lector de pantalla:

- **Windows**: Microsoft Edge / Narrator
- **macOS**: Safari / VoiceOver
- **Android**: Aplicación PowerApps / Talkback
- **iOS**: Aplicación PowerApps / VoiceOver

Para garantizar una experiencia satisfactoria con el lector de pantalla, se recomienda:

- Asegurarse de que todos los controles de entrada tienen la propiedad **[AccessibilityLabel](controls/properties-accessibility.md)** establecida.
- Para las imágenes, establezca **[AccessibilityLabel](controls/properties-accessibility.md)** en una descripción adecuada.
  - Si no se utiliza una imagen como un botón o un vínculo (es decir, el icono simplemente se utiliza como decoración) y no la debe leer el lector de pantalla, asegúrese de que la propiedad **[AccessibilityLabel](controls/properties-accessibility.md)** está vacía o no está establecida.
  - Si una imagen o un icono se utiliza como un botón, establezca entonces **[TabIndex](controls/properties-accessibility.md)** en 0 y **[AccessibilityLabel](controls/properties-accessibility.md)** en la descripción del vínculo.


## <a name="multimedia"></a>Contenido multimedia
Asegúrese de todos los vídeos tienen subtítulos y una transcripción de todas las grabaciones de audio está disponible para el usuario.  **Vídeo** control admite subtítulos en formato WebVTT a través de la **ClosedCaptionsUrl** propiedad.

Tenga en cuenta que con el lector de pantalla habilitado, **Timer** no anuncia el texto del botón, sino cuánto tiempo ha transcurrido.  Los anuncios no se pueden desactivar, aunque el temporizador esté oculto con baja opacidad.

## <a name="working-with-signatures"></a>Trabajo con firmas
Si tiene un campo de firma que utiliza el control PenInput, debe habilitar un método alternativo de entrada de firma.  La manera recomendada es mostrar un control TextInput donde un usuario puede escribir su nombre.  Asegúrese de que las instrucciones para firmar se colocan en la propiedad **[AccessibilityLabel](controls/properties-accessibility.md)** y el control se pone cerca de la entrada de lápiz (a la derecha o inmediatamente debajo).



Relacionado:
- [Propiedades de accesibilidad](controls/properties-accessibility.md)
- [Usar el Comprobador de accesibilidad](accessibility-checker.md)
- [Colores accesibles en PowerApps](accessible-apps-color.md)
