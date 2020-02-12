---
title: Métodos abreviados de teclado para aplicaciones de Canvas | Microsoft Docs
description: Métodos abreviados de teclado para aplicaciones de Canvas
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/09/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6c6f033027fb9ce29ba443efab2b5c14ec5ea013
ms.sourcegitcommit: ee1960fe32136a621e653d6ff2f13d87017830a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77145342"
---
# <a name="keyboard-shortcuts-for-canvas-apps"></a>Métodos abreviados de teclado para aplicaciones de Canvas

> [!NOTE]
> Los métodos abreviados pueden variar en función de la distribución del teclado.

## <a name="file"></a>Archivo

| Método abreviado | Acción |
|--|--|
| Ctrl + O (o Alt + F) | Abra un archivo. |
| Ctrl + Mayús + S (o Alt + P) | Guarde la aplicación con un nombre diferente. |
| Ctrl+S | Guarde la aplicación con el mismo nombre o por primera vez. |
| F12 | Descargue el archivo de aplicación (. msapp). |
| Alt+F | Abra el menú **archivo** . |

## <a name="ribbon"></a>cinta de opciones

| Método abreviado | Acción |
|--|--|
| Escribir | Ejecutar el comando seleccionado. |
| Tabulador | Desplazarse entre los comandos de la pestaña seleccionada y, a continuación, a la pestaña siguiente. |
| Ctrl+F6 | Navegue hasta el punto de referencia siguiente. |
| Ctrl + Mayús + F6 | Navegue hasta el punto de referencia anterior. |
| Alt+I | Seleccione la pestaña **Insertar** . |

## <a name="editing"></a>Editar

| Método abreviado | Acción |
|--|--|
| Ctrl+A | Seleccionar todo. |
| Ctrl+X | Límite. |
| Ctrl+C | Copiar. |
| Ctrl+V | Pegar. |
| Ctrl+Z | Comando Deshacer. |
| Ctrl+Y | Comando Redo. |
| Ctrl+M | Agregar una pantalla. |
| Ctrl + = o Ctrl + Mayús + = | Acercar. |
| Ctrl +-o Ctrl + Mayús +- | Alejar. |
| Ctrl + 0 | Ajustar el lienzo a la página. |
| Mayús+ENTRAR | Dividir una línea en una fórmula. |

## <a name="preview"></a>Vista previa

| Método abreviado | Acción |
|--|--|
| F5 | Abra el modo de vista previa. |
| Esc | Cerrar el modo de vista previa, un cuadro de diálogo o un panel flotante.|

## <a name="canvas"></a>Canvas

| Método abreviado | Acción |
|--|--|
| Tabulador | Seleccione el control siguiente. |
| Ctrl + clic o Mayús + clic | Seleccionar varios objetos a la vez. |
| Flecha hacia la derecha | Desplazar el control seleccionado a la derecha. |
| Flecha izquierda | Desplazar el control seleccionado a la izquierda. |
| Flecha arriba | Desplazar hacia arriba el control seleccionado. |
| Flecha abajo | Desplazar el control seleccionado hacia abajo. |

## <a name="tree-view"></a>Vista de árbol

> [!NOTE]
> Estos métodos abreviados requieren que el panel de **vista de árbol** tenga el foco.

| Método abreviado | Acción |
|--|--|
| F2 | Cambiar el nombre de un control. |
| Esc | Cancelar cambiar el nombre de un control. |
| Ctrl+G | Agrupar/desagrupar controles. |
| Ctrl +] | Traer un control hacia delante. |
| Ctrl + [ | Enviar un control hacia atrás. |
| Ctrl + Mayús +] | Traer al frente. |
| Ctrl + Mayús + [ | Enviar al fondo. |

## <a name="resize"></a>Cambiar tamaño

| Método abreviado | Acción |
|--|--|
| Mayús + Flecha izquierda | Reducir ancho. |
| Ctrl + Mayús + Flecha izquierda | Reducir ligeramente el ancho. |
| Mayús + Flecha abajo | Reducir el alto. |
| Ctrl + Mayús + Flecha abajo | Reduce ligeramente el alto. |
| Mayús + Flecha derecha | Aumentar ancho. |
| Ctrl + Mayús + Flecha derecha | Aumentar ligeramente el ancho. |
| Mayús + Flecha arriba | Aumentar el alto. |
| Ctrl + Mayús + Flecha arriba | Aumentar ligeramente el alto. |

## <a name="text-format"></a>Formato de texto

| Método abreviado | Acción |
|--|--|
| CTRL + B  | Desplazarse por los niveles de negrita. |
| Ctrl+I | Activar o desactivar cursiva. |
| Ctrl+U | Agrega o quita el subrayado. |

## <a name="alternate-behavior"></a>Comportamiento alternativo

| Método abreviado | Acción |
|--|--|
| Alt o Ctrl + Mayús | 1. antes de seleccionar un control, oculte los elementos de diseño para que pueda interactuar con los controles como lo haría el usuario de la aplicación.<br>2. una vez que se inicia un reinicio o una reposición de un control, si se mantienen estas claves, se invalidan los puntos de acoplamiento. |

Al igual que una hoja de cálculo de Excel, las aplicaciones de canvas están activas y funcionan incluso cuando se editan.  No es necesario cambiar al modo de vista previa para ejecutar la aplicación, de forma que el ciclo de edición y prueba sea mucho más rápido.  Pero esto plantea un problema: ¿cómo se diferencia la selección de un control de botón para que se pueda cambiar el tamaño de la selección de un control de botón para que se ejecute la lógica en nuestra aplicación?

En el modo de diseño, la selección predeterminada de un objeto es para su edición: mover, cambiar de tamaño, cambiar propiedades y, de lo contrario, configurar el objeto.  Este valor predeterminado se puede invalidar manteniendo presionadas las teclas Alt o Ctrl + Mayús *antes* de iniciar la selección que trata la selección como si un usuario de la aplicación lo hubiera hecho.  

En la animación siguiente, primero se selecciona un control de botón para su edición.  Los adornos aparecen alrededor del control y la barra de fórmulas muestra la propiedad **alseleccionar** , lista para su edición.  A continuación, se libera el botón.  *Con la tecla Alt presionada por primera*vez, el control de botón se vuelve a seleccionar, pero esta vez se evalúa la propiedad **alseleccionar** y se muestra la notificación, como si el botón estuviera seleccionado en una aplicación en ejecución.  

![Animación en la que se muestra el efecto de comenzar manteniendo presionada la tecla Alt, seleccione un control de botón](media/keyboard-shortcuts/alt-select.gif)

También se puede utilizar la tecla Alt *después* de haber seleccionado un control para invalidar los puntos de acoplamiento y cambiar su tamaño.  La animación siguiente muestra el tamaño de una tarjeta de datos dentro de un control [**Editar formulario**](controls/control-form-detail.md) .  Inicialmente, el cambio de tamaño se restringe a puntos de ajuste específicos.  Más adelante, *sin soltar el botón del mouse*, se presiona la tecla Alt junto con el botón del mouse. La adición de la tecla Alt invalida los puntos de ajuste y se puede obtener cualquier ancho con el mouse. 

![Animación en la que se muestra el efecto de agregar la tecla Alt al cambiar el tamaño de una tarjeta de datos](media/keyboard-shortcuts/alt-fine-control.gif)

## <a name="other"></a>Otro

| Método abreviado | Acción |
|--|--|
| F1 | Abra la documentación de. |
| Mayús+F10 | Abra un menú contextual en, por ejemplo, la **vista de árbol**. |


 