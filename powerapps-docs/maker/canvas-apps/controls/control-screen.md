---
title: 'Control Pantalla: referencia | Microsoft Docs'
description: Información sobre el control Pantalla, con propiedades y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 715b329f7756f35b6053199ae0c88ce2d0b967f2
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="screen-control-in-powerapps"></a>Control Pantalla en PowerApps
Elemento de la interfaz de usuario que contiene uno o más controles de una aplicación.

## <a name="description"></a>Descripción
La mayoría de las aplicaciones tienen varios controles **Pantalla** que contienen controles **[Etiqueta](control-text-box.md)**, **[Botón](control-button.md)** y otros controles que muestran los datos y son compatibles con la navegación.

## <a name="key-properties"></a>Propiedades principales
**[ImagenDeFondo](properties-visual.md)**: nombre de un archivo de imagen que aparece en el fondo de una pantalla.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

## <a name="additional-properties"></a>Propiedades adicionales
**[PosiciónDeLaImagen](properties-visual.md)**: posición (**Rellenar**, **Ajustar**, **Estirar**, **Icono** o **Centrar**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.

**AlEstarOculto**: el comportamiento de una aplicación cuando el usuario navega fuera de una pantalla.

**AlEstarVisible**: el comportamiento de una aplicación cuando el usuario navega a una pantalla.

**OnStart**: el comportamiento de la aplicación cuando el usuario la abre.

* La fórmula en la que se establece esta propiedad se ejecuta antes de que aparezca la primera pantalla de la aplicación. Llame a la función [**Navegar**](../functions/function-navigate.md) para cambiar qué pantalla aparece en primer lugar cuando se inicia la aplicación.
* No se pueden establecer [variables de contexto](../working-with-variables.md) con la función [**UpdateContext**](../functions/function-updatecontext.md) porque no ha aparecido aún ninguna pantalla. Sin embargo, puede pasar variables de contexto en la función **Navegar** y crear y rellenar una [colección](../working-with-variables.md) mediante el uso de la función [**Recopilar**](../functions/function-clear-collect-clearcollect.md).
* Cuando se actualiza una aplicación, se ejecuta la fórmula en la que se establece esta propiedad cuando la aplicación se carga en PowerApps Studio. Para ver el impacto de cambiar esta propiedad, tiene que guardar, cerrar y volver a cargar la aplicación.
* La propiedad **AlIniciar** es realmente una propiedad de la aplicación, no de la pantalla. Por comodidad a la hora de editar, se ve y se modifica como una propiedad en la primera pantalla de la aplicación. Si se quita la primera pantalla o se reorganizan las pantallas, puede ser difícil encontrar esta propiedad. En este caso, guarde, cierre y vuelva a cargar la aplicación y la propiedad volverá a aparecer como una propiedad de la primera pantalla.

## <a name="related-functions"></a>Funciones relacionadas
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **[Radio](control-radio.md)**, asígnele el nombre **ScreenFills** y establezca su propiedad **[Elementos](properties-core.md)** en este valor:<br>
   **["Red", "Green"]**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Asigne al control **Pantalla** predeterminado el nombre **Source**, agregue otro control **Pantalla** y asígnele el nombre **Target**.
3. En **Source**, agregue un control **[Forma](control-shapes-icons.md)** (como una flecha) y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:<br>
   **Navigate(Target, ScreenTransition.Fade)**
   
    ¿Desea más información sobre la función **[Navegar](../functions/function-navigate.md)** u [otras funciones](../formula-reference.md)?
4. En **Target**, agregue un control **[Forma](control-shapes-icons.md)** (como una flecha) y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:<br>
   **Navigate(Origen, ScreenTransition.Fade)**
5. Establezca la propiedad **[Fill](properties-color-border.md)** de **Target** en esta fórmula:<br>
   **If("Red" in ScreenFills.Selected.Value, RGBA(255, 0, 0, 1), RGBA(54, 176, 75, 1))**
6. Desde **Source**, presione F5, pulse o haga clic en cualquiera de las opciones del control **[Radio](control-radio.md)** y pulse o haga clic en el control **[Forma](control-shapes-icons.md)**.
   
    **Target** aparece en el color que eligiera.
7. En **Target**, pulse o haga clic en el control **[Forma](control-shapes-icons.md)** para volver a **Source**.
8. (opcional) Pulse o haga clic en la otra opción del control **[Radio](control-radio.md)** y pulse o haga clic en el control **[Forma](control-shapes-icons.md)** para confirmar que **Target** aparece en el otro color.
9. Presione Esc para volver al área de trabajo predeterminada.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Cuando la **pantalla** es de hecho el fondo del texto, debe haber un contraste de color adecuado entre:
* **[Fill](properties-color-border.md)** y el texto
* **[BackgroundImage](properties-visual.md)** y el texto (si procede)

Por ejemplo, si un control **Pantalla** contiene un control **[Etiqueta](control-text-box.md)** y esta tiene relleno transparente, la propiedad **[Fill](properties-color-border.md)** de la pantalla se convierte de hecho en el color de fondo de la etiqueta.

Además de texto, podría también comprobar el contraste de color con objetos gráficos esenciales como las imágenes de estrella de un control **[Clasificación](control-rating.md)**.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* Debe haber un nombre significativo para cada **pantalla**. El nombre de la pantalla se puede ver y editar de la misma manera que otros controles: en la vista de árbol del panel de controles o en el encabezado del panel de propiedades.
> [!NOTE]
> Cuando se carga una nueva **pantalla**, los lectores de pantalla anunciarán su nombre. 
